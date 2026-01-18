---
title: Calendar
date: 2026-01-18
tags:
    - homelab
    - wiki
---

- calcurse
- rsync to sync to and from server
- git for version history
- converts my calendar to multiple pdf's for phone.

## About

First I tried a CalDAV Calendar using Baïkal. It was good and simple. But after trying Calcurse
I found some difficalties with it. The simplicity of Calcurse really made me like it. Just some
tiny textfiles that are still readable even if you just read the textfile.

All I needed was a way to sync this via my thinkpad and pc. Both running Fedora Linux with i3wm.
So a cli first interface is good for this.

I am using a 'pre-load' and 'post-load' script that I am proud of. I run this script via `zsh`.
but you could also use this as a normal bash script.

Both online and ofline available. The online calendar is synced locally. It is
imported in the `apts` file when Calcurse is loaded, and removed using `sed` and
the name of the online calendar.  
This is so you don't tranfer to server everytime you close because the online
calendar got `curl`ed again, and the git log is not filled with sync changes.  
Only the changes you make on the local calendar

## Calcurse script

<details>

  <summary>Full code</summary>

```bash
calcurse() {
    REMOTE_NAME="serv-rem"
    REMOTE_IP="100.85.244.105"
    REMOTE_CALENDAR="/mnt/storage/data/files/calendar/"
    LOCAL_CALENDAR="$HOME/.local/share/calcurse/"
    APTS_FILE="$HOME/.local/share/calcurse/apts"
    SCHOOL_CACHE="$HOME/.calendars/school_tagged.ics"

    mkdir -p "$HOME/.calendars"

    # --- CONNECTIVITY CHECK ---
    if ping -c 1 -W 1 "$REMOTE_IP" > /dev/null 2>&1; then
        ONLINE=true
    else
        ONLINE=false
        echo "Offline mode: Skipping server sync and school update."
    fi

    # --- PULL (if online) ---
    if [ "$ONLINE" = true ]; then
        echo "Pulling latest from server..."
        rsync -aq --checksum "$REMOTE_NAME:$REMOTE_CALENDAR" "$LOCAL_CALENDAR"

        echo "Updating school calendar..."
        curl -s "https://online.calendar.com"
            | sed 's/^SUMMARY:/SUMMARY:[SCHOOL] /' > "$SCHOOL_CACHE"
    fi

    # --- IMPORT (always use the cache, even if offline) ---
    if [ -f "$SCHOOL_CACHE" ]; then
        command calcurse -i "$SCHOOL_CACHE" > /dev/null
    fi

    # --- START APP ---
    command calcurse "$@"

    # --- PDF CALENDAR CREATION ---
    echo "Generating PDF report..." >&2
    command /usr/bin/calcurse -xpcal > /tmp/cal_export.txt
    command python3 /home/trgr/.local/bin/cal_to_pdf.py /tmp/cal_export.txt
    command python3 /home/trgr/.local/bin/cal_to_pdf_school.py $SCHOOL_CACHE

    # --- CLEANUP SCHOOL ENTRIES ---
    if [ -f "$APTS_FILE" ]; then
        grep -v "\[SCHOOL\]" "$APTS_FILE" > "${APTS_FILE}.tmp"
        mv "${APTS_FILE}.tmp" "$APTS_FILE"
    fi

    # --- GIT SUBSHELL (always runs to track local history) ---
    (
        cd "$LOCAL_CALENDAR" || exit
        if [[ -n $(git status --short) ]]; then
            echo "Committing changes..."
            git add .
            git commit -m "Auto-sync: $(date +'%Y-%m-%d %H:%M:%S')"
        fi
    ) > /dev/null 2>&1

    # --- PUSH (if online) ---
    if [ "$ONLINE" = true ]; then
        echo "Pushing changes to server..."
        rsync -aqi --checksum "$LOCAL_CALENDAR" "$REMOTE_NAME:$REMOTE_CALENDAR"
        echo "Sync complete!"
    else
        echo "Changes saved locally. Will sync next time you're online."
    fi
}
```

</details>

## conversion scripts

I use 2 scripts to convert:

- for the `~/.local/share/calcurse/apts` & `~/.local/share/calcurse/todo` of calcurse itself
- for my imported ics calendar in `~/.calendars/school_tagged.ics`
    - because it was difficult to extract the notes linked to the apointments
    - this was needed to get the classroom number for classes.

> I could do this in one, but these scripts are largely vibe coded, will do this in the future

### calcurse conversion script

<details>

  <summary>Full code</summary>

```python
# PREREQUIREMENTS
# $ pip install reportlab

import re
import calendar
import sys
import os
import argparse
from datetime import datetime
from reportlab.lib import colors
from reportlab.lib.pagesizes import landscape, portrait, A4
from reportlab.platypus import SimpleDocTemplate, Table, TableStyle, Paragraph, PageBreak, Spacer
from reportlab.lib.styles import getSampleStyleSheet, ParagraphStyle

# ================= CONFIGURATION =================
YEAR           = 2026
GRID_OUT       = "/home/trgr/.local/share/calcurse/pdf/Agenda_Grid_2026.pdf"
MOBILE_OUT     = "/home/trgr/.local/share/calcurse/pdf/Agenda_Mobile_2026.pdf"
TODO_OUT       = "/home/trgr/.local/share/calcurse/pdf/Agenda_Todos.pdf"
# =================================================

def clean_description(desc):
    """Removes unwanted prefixes and cleans up the text."""
    # List of exact strings to remove
    to_remove = [
        "PBA-TIN/",
        "INT-IT/",
    ]

    for prefix in to_remove:
        desc = desc.replace(prefix, "")

    # Standardize tags
    desc = desc.replace("[SCHOOL]", "S:")

    return desc.strip()

def parse_pcal(filename):
    events = {}
    todos = []
    event_pattern = re.compile(r'^([A-Z][a-z]{2})\s(\d{2})\s+(?:\((\d{2}:\d{2})\s->\s(\d{2}:\d{2})\)\s)?(.*)')
    todo_pattern = re.compile(r'^note all\s+(.*)')

    if not os.path.exists(filename):
        sys.exit(1)

    with open(filename, 'r') as f:
        for line in f:
            line = line.strip()
            todo_match = todo_pattern.match(line)
            if todo_match:
                # Clean todos as well using the same rules
                todos.append(clean_description(todo_match.group(1)))
                continue

            match = event_pattern.match(line)
            if match:
                month_str, day, start_t, end_t, desc = match.groups()
                try:
                    month = datetime.strptime(month_str, '%b').month
                    date_obj = datetime(YEAR, month, int(day))
                    date_key = date_obj.strftime("%Y-%m-%d")

                    entry = {
                        'time': f"{start_t} - {end_t}" if start_t else None,
                        'desc': clean_description(desc),
                        'display_date': date_obj.strftime("%A, %b %d")
                    }
                    if date_key not in events: events[date_key] = []
                    events[date_key].append(entry)
                except ValueError: continue
    return events, todos

def build_todo_pdf(filename, todos):
    doc = SimpleDocTemplate(filename, pagesize=portrait(A4), topMargin=40)
    styles = getSampleStyleSheet()
    title_style = ParagraphStyle('TodoTitle', parent=styles['Title'], spaceAfter=20)
    item_style = ParagraphStyle('TodoItem', parent=styles['Normal'], fontSize=12, leading=18, spaceBefore=6)

    elements = []
    elements.append(Paragraph("Task List (To-do)", title_style))

    if todos:
        todo_data = []
        for todo in sorted(todos):
            color = "#d93025" if todo.startswith(('1.', '2.')) else "#202124"
            checkbox = "❏"
            text = f"<font color='{color}'>{todo}</font>"
            todo_data.append([Paragraph(checkbox, item_style), Paragraph(text, item_style)])

        t = Table(todo_data, colWidths=[30, 420])
        t.setStyle(TableStyle([
            ('VALIGN', (0,0), (-1,-1), 'TOP'),
            ('BOTTOMPADDING', (0,0), (-1,-1), 10),
            ('LINEBELOW', (1,0), (1,-1), 0.5, colors.lightgrey),
        ]))
        elements.append(t)
    doc.build(elements)

def build_grid_pdf(filename, data, months):
    doc = SimpleDocTemplate(filename, pagesize=landscape(A4),
                            topMargin=20, bottomMargin=20,
                            leftMargin=30, rightMargin=30)
    styles = getSampleStyleSheet()
    elements = []

    # Constants to ensure it fits one page
    TOTAL_AVAILABLE_HEIGHT = 510
    HEADER_ROW_HEIGHT = 20

    for month in months:
        elements.append(Paragraph(f"<b>{calendar.month_name[month]} {YEAR}</b>", styles['Title']))

        cal = calendar.Calendar(firstweekday=0)
        weeks = cal.monthdayscalendar(YEAR, month)
        num_weeks = len(weeks)

        # Dynamic height calculation
        row_height = (TOTAL_AVAILABLE_HEIGHT - HEADER_ROW_HEIGHT) / num_weeks

        table_data = [[calendar.day_name[i] for i in range(7)]]
        for week in weeks:
            row = []
            for day in week:
                if day == 0:
                    row.append("")
                else:
                    date_str = f"{YEAR}-{month:02d}-{day:02d}"
                    day_events = data.get(date_str, [])
                    cell = [f"<b>{day}</b>"]
                    for ev in day_events:
                        t_str = f"<font size='5'><b>{ev['time']}</b></font><br/>" if ev['time'] else ""
                        # Use already cleaned description
                        cell.append(f"{t_str}<font size='6'>• {ev['desc'][:35]}</font>")
                    row.append(Paragraph("<br/>".join(cell), styles['Normal']))
            table_data.append(row)

        t = Table(table_data, colWidths=[105]*7, rowHeights=[HEADER_ROW_HEIGHT] + [row_height]*num_weeks)
        t.setStyle(TableStyle([
            ('GRID', (0,0), (-1,-1), 0.5, colors.grey),
            ('BACKGROUND', (0,0), (-1,0), colors.whitesmoke),
            ('VALIGN', (0,0), (-1,-1), 'TOP'),
            ('TOPPADDING', (0,0), (-1,-1), 2),
            ('BOTTOMPADDING', (0,0), (-1,-1), 2),
        ]))
        elements.append(t)
        elements.append(PageBreak())

    doc.build(elements)

def build_mobile_pdf(filename, data):
    doc = SimpleDocTemplate(filename, pagesize=portrait(A4), leftMargin=30, rightMargin=30)
    styles = getSampleStyleSheet()
    date_style = ParagraphStyle('DateH', parent=styles['Heading2'], fontSize=12, spaceBefore=10)
    time_style = ParagraphStyle('TimeS', fontSize=9, textColor=colors.HexColor("#1a73e8"), fontName='Helvetica-Bold')
    desc_style = ParagraphStyle('DescS', fontSize=10, leading=12)
    elements = []
    curr_month = ""
    for date_key in sorted(data.keys()):
        m_name = datetime.strptime(date_key, "%Y-%m-%d").strftime("%B %Y")
        if m_name != curr_month:
            elements.append(Spacer(1, 20)); elements.append(Paragraph(m_name, styles['Title'])); curr_month = m_name
        elements.append(Paragraph(data[date_key][0]['display_date'], date_style))
        table_rows = []
        for ev in data[date_key]:
            table_rows.append([Paragraph(ev['time'] or "All Day", time_style), Paragraph(ev['desc'], desc_style)])
        t = Table(table_rows, colWidths=[80, 380])
        t.setStyle(TableStyle([('VALIGN',(0,0),(-1,-1),'TOP'),('LINEBELOW',(1,0),(1,-1),0.5,colors.lightgrey)]))
        elements.append(t)
    doc.build(elements)

if __name__ == "__main__":
    parser = argparse.ArgumentParser(description="Convert pcal to PDF.")
    parser.add_argument("input", help="Input text file")
    parser.add_argument("-v", "--verbose", action="store_true", help="Display output logs")
    args = parser.parse_args()

    cal_data, todo_list = parse_pcal(args.input)
    active_months = sorted(list(set(int(d.split('-')[1]) for d in cal_data.keys())))

    if cal_data:
        build_grid_pdf(GRID_OUT, cal_data, active_months)
        build_mobile_pdf(MOBILE_OUT, cal_data)

    build_todo_pdf(TODO_OUT, todo_list)

    if args.verbose:
        print(f"Success! Generated:")
        print(f"1. {GRID_OUT}")
        print(f"2. {MOBILE_OUT}")
        print(f"3. {TODO_OUT}")
```

</details>

### ics conversion script

<details>

  <summary>Full code</summary>

```python
import re
import sys
import os
import argparse
from datetime import datetime
from reportlab.lib import colors
from reportlab.lib.pagesizes import portrait, A4
from reportlab.platypus import SimpleDocTemplate, Table, TableStyle, Paragraph, Spacer
from reportlab.lib.styles import getSampleStyleSheet, ParagraphStyle

# ================= CONFIGURATION =================

YEAR = 2026
HOME_DIR = os.path.expanduser("~")
BASE_PATH = os.path.join(HOME_DIR, ".local/share/calcurse/pdf")

# Single output file for the list view

OUT_FILE = os.path.join(BASE_PATH, "School_List_2026.pdf")

# =================================================

def clean_text(text):
"""Cleans ICS specific escaping and prefixes."""
if not text: return ""
text = text.replace(r'\,', ',').replace(r'\n', ' ')
to_remove = ["PBA-TIN/", "INT-IT/"]
for prefix in to_remove:
text = text.replace(prefix, "")
text = text.replace("[SCHOOL]", "S:")
return re.sub(r'\s+', ' ', text).strip()

def parse_ics(filename):
"""Parses .ics format for the list builder."""
events = {}
if not os.path.exists(filename):
print(f"Error: {filename} not found.")
sys.exit(1)

    with open(filename, 'r', encoding='utf-8') as f:
        content = f.read()

    # Unfold ICS lines
    content = re.sub(r'\r?\n[ \t]', '', content)
    vevent_pattern = re.compile(r'BEGIN:VEVENT(.*?)END:VEVENT', re.DOTALL)

    for block in vevent_pattern.findall(content):
        summary = re.search(r'SUMMARY:(.*)', block)
        location = re.search(r'LOCATION:(.*)', block)
        dtstart = re.search(r'DTSTART(?:;VALUE=DATE)?:(\d{8})(?:T(\d{6})Z)?', block)
        dtend = re.search(r'DTEND(?:;VALUE=DATE)?:(\d{8})(?:T(\d{6})Z)?', block)

        if summary and dtstart:
            date_str = dtstart.group(1)
            time_start = dtstart.group(2)
            time_end = dtend.group(2) if dtend else None

            try:
                date_obj = datetime.strptime(date_str, '%Y%m%d')
                date_key = date_obj.strftime("%Y-%m-%d")

                time_disp = f"{time_start[:2]}:{time_start[2:4]} - {time_end[:2]}:{time_end[2:4]}" if time_start and time_end else None

                entry = {
                    'time': time_disp,
                    'desc': clean_text(summary.group(1)),
                    'loc': clean_text(location.group(1)) if location else "",
                    'display_date': date_obj.strftime("%A, %b %d")
                }
                events.setdefault(date_key, []).append(entry)
            except ValueError:
                continue
    return events

def build_list_pdf(filename, data):
"""Generates a clean list-style PDF of all school events."""
doc = SimpleDocTemplate(filename, pagesize=portrait(A4), leftMargin=30, rightMargin=30, topMargin=30)
styles = getSampleStyleSheet()

    # Styles
    title_style = ParagraphStyle('SchoolTitle', parent=styles['Title'], spaceAfter=20)
    date_style = ParagraphStyle('DateH', parent=styles['Heading2'], fontSize=11, spaceBefore=8, textColor=colors.black)
    time_style = ParagraphStyle('TimeS', fontSize=9, textColor=colors.HexColor("#1a73e8"), fontName='Helvetica-Bold')
    desc_style = ParagraphStyle('DescS', fontSize=9, leading=11)
    loc_style = ParagraphStyle('LocS', fontSize=8, textColor=colors.grey, leading=10)

    elements = []
    elements.append(Paragraph(f"School Schedule {YEAR}", title_style))

    curr_month = ""
    for date_key in sorted(data.keys()):
        # Month Header
        m_name = datetime.strptime(date_key, "%Y-%m-%d").strftime("%B %Y")
        if m_name != curr_month:
            elements.append(Spacer(1, 20)); elements.append(Paragraph(m_name, styles['Title'])); curr_month = m_name
            curr_month = m_name

        # Date Header
        elements.append(Paragraph(data[date_key][0]['display_date'], date_style))

        # Events Table
        table_rows = []
        for ev in data[date_key]:
            info = [Paragraph(ev['desc'], desc_style)]
            if ev['loc']:
                info.append(Paragraph(f"Location: {ev['loc']}", loc_style))
            table_rows.append([Paragraph(ev['time'] or "All Day", time_style), info])

        t = Table(table_rows, colWidths=[80, 380])
        t.setStyle(TableStyle([
            ('VALIGN',(0,0),(-1,-1),'TOP'),
            ('LINEBELOW',(1,0),(1,-1),0.5,colors.lightgrey),
            ('BOTTOMPADDING', (0,0), (-1,-1), 5),
            ('TOPPADDING', (0,0), (-1,-1), 5),
        ]))
        elements.append(t)

    doc.build(elements)

if **name** == "**main**":
parser = argparse.ArgumentParser(description="Convert school ICS to a list-view PDF.")
parser.add_argument("input", help="Input .ics file")
parser.add_argument("-v", "--verbose", action="store_true")
args = parser.parse_args()

    cal_data = parse_ics(args.input)
    if cal_data:
        os.makedirs(os.path.dirname(OUT_FILE), exist_ok=True)
        build_list_pdf(OUT_FILE, cal_data)

        if args.verbose:
            print(f"Success! Generated School List View:")
            print(f"-> {OUT_FILE}")
    else:
        print("No event data found in ICS.")
```

</details>

## Mobile frontend

This is a simple single webfront hosted with a `apache` container.

### Htlm website

<details>

<summary>Full code</summary>

```html
<!doctype html>
<html lang="en">
    <head>
        <meta charset="UTF-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0" />
        <title>Calendars</title>
        <style>
            body {
                font-family:
                    -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial,
                    sans-serif;
                background: #121212;
                /* Deep Dark Background */
                color: #e0e0e0;
                padding: 20px;
                display: flex;
                flex-direction: column;
                align-items: center;
                min-height: 100vh;
                margin: 0;
            }

            h1 {
                color: #ffffff;
                margin-bottom: 10px;
                font-weight: 700;
            }

            h2 {
                width: 100%;
                max-width: 800px;
                font-size: 0.85rem;
                color: #757575;
                /* Subdued Grey */
                text-transform: uppercase;
                letter-spacing: 1.5px;
                margin: 40px 0 15px 0;
                border-bottom: 1px solid #2c2c2c;
                padding-bottom: 8px;
            }

            .grid {
                display: grid;
                grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
                gap: 20px;
                width: 100%;
                max-width: 800px;
            }

            .card {
                background: #1e1e1e;
                /* Elevated surface color */
                padding: 25px;
                border-radius: 16px;
                box-shadow: 0 4px 20px rgba(0, 0, 0, 0.4);
                text-align: center;
                text-decoration: none;
                color: inherit;
                transition: all 0.2s ease;
                border: 1px solid #333;
            }

            .card:hover {
                border-color: #444;
                background: #252525;
                transform: translateY(-2px);
            }

            .card:active {
                transform: scale(0.96);
                background: #1a1a1a;
            }

            .icon {
                font-size: 40px;
                margin-bottom: 12px;
                display: block;
            }

            .title {
                font-size: 1.15rem;
                font-weight: 600;
                display: block;
                margin-bottom: 6px;
                color: #ffffff;
            }

            .desc {
                font-size: 0.85rem;
                color: #b0b0b0;
            }

            #time-container {
                color: #666;
                margin-top: 50px;
                font-size: 0.75rem;
                text-align: center;
            }

            #time {
                color: #888;
            }
        </style>
    </head>

    <body>
        <h1>Calendars</h1>

        <h2>Personal Agenda</h2>
        <div class="grid">
            <a href="pdf/Agenda_Grid_2026.pdf" class="card">
                <span class="icon">🗓️</span>
                <span class="title">Desktop Grid</span>
                <span class="desc">Printable Monthly View</span>
            </a>
            <a href="pdf/Agenda_Mobile_2026.pdf" class="card">
                <span class="icon">📋</span>
                <span class="title">Mobile Agenda</span>
                <span class="desc">Vertical Scrolling List</span>
            </a>
            <a href="pdf/Agenda_Todos.pdf" class="card">
                <span class="icon">✅</span>
                <span class="title">Task List</span>
                <span class="desc">To-dos & Priorities</span>
            </a>
        </div>

        <h2>School Schedule</h2>
        <div class="grid">
            <a href="pdf/School_List_2026.pdf" class="card">
                <span class="icon">🎓</span>
                <span class="title">School List</span>
                <span class="desc">Courses & Exam Schedule</span>
            </a>
        </div>

        <div id="time-container">Last updated: <span id="time"></span></div>

        <script>
            document.getElementById("time").innerText = new Date().toLocaleString()
        </script>
    </body>
</html>
````

</details>
