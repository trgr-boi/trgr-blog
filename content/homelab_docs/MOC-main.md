---
title: MOC-main
date: 2026-01-10
tags:
    - homelab
    - wiki
---

## Servers

- srv01
    - old thinkpad l380

## Tools I setup

### calendar

- calcurse
- rsync to sync to and from server
- git for version history

First I tried a CalDAV Calendar using Baïkal. It was good and simple. But after trying Calcurse
I found some difficalties with it. The simplicity of Calcurse really made me like it. Just some
tiny textfiles that are still readable even if you just read the textfile.

All I needed was a way to sync this via my thinkpad and pc. Both running Fedora Linux with i3wm.
So a cli first interface is good for this.

I am using a 'pre-load' and 'post-load' script that I am proud of. I run this script via `zsh`.
but you could also use this as a normal bash script.

```bash
calcurse() {
    REMOTE_NAME="srv01"
    REMOTE_IP="ts.ip.for.ping"
    REMOTE_CALENDAR="/path/to/remote/calendar" # directory on server (no tailing '/')
    LOCAL_CALENDAR="$HOME/.local/share/calcurse/" # default calcurse calendar (yes tailing '/')
    APTS_FILE="$LOCAL_CALENDAR/apts"
    SCHOOL_CACHE="$HOME/.calendars/school_tagged.ics" # online calendar cache location

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
        curl -s "https://linktomyschoolcalendar.com/..." \
            | sed 's/^SUMMARY:/SUMMARY:[SCHOOL] /' > "$SCHOOL_CACHE"
    fi

    # --- IMPORT (always use the cache, even if offline) ---
    if [ -f "$SCHOOL_CACHE" ]; then
        command calcurse -i "$SCHOOL_CACHE" > /dev/null
    fi

    # --- START APP ---
    command calcurse "$@"

    # --- CLEANUP SCHOOL ENTRIES ---
    if [ -f "$APTS_FILE" ]; then
        # NOTE: change name of online calendar
        grep -v "\[SCHOOL\]" "$APTS_FILE" > "${APTS_FILE}.tmp"
        mv "${APTS_FILE}.tmp" "$APTS_FILE"
    fi

    # --- GIT SUBSHELL (always runs to track local history) ---
    (
        cd "$LOCAL_CALENDAR" || exit
        # TODO: add check if git repo
        if [[ -n $(git status --short) ]]; then
            echo "Committing changes..."
            git add .
            git commit -m "Auto-sync: $(date +'%Y-%m-%d %H:%M:%S')"
        fi
    ) > /dev/null 2>&1

    # --- PUSH (If Online) ---
    if [ "$ONLINE" = true ]; then
        echo "Pushing changes to server..."
        rsync -aqi --checksum "$LOCAL_CALENDAR" "$REMOTE_NAME:$REMOTE_CALENDAR"
        echo "Sync complete!"
    else
        echo "Changes saved locally. Will sync next time you're online."
    fi
}
```

Both online and ofline available. The online calendar is synced locally. It is
imported in the `apts` file when Calcurse is loaded, and removed using `sed` and
the name of the online calendar.  
This is so you don't tranfer to server everytime you close because the online
calendar got `curl`ed again, and the git log is not filled with sync changes.  
Only the changes you make on the local calendar
