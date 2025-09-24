---
tags:
  - school
  - OS
reference: "[[OS-Operating Systems]]"
title: OpSys-Brief
aliases:
---
**Briefing Document: Besturingssystemen, Virtualisatie en Opslag**

**1. Hoofdthema: Besturingssystemen (OS) - Functies en Structuur**

- **Kernrol van een [[OS-OS|Besturingssysteem]]:** Een besturingssysteem is essentieel om conflicten en verwarring te voorkomen wanneer "Veel mensen willen van systeembronnen ([[OS-Hardware-Resources|Resources]]) gebruik maken." Het hoofddoel is om "zoveel mogelijk gebruikers gelukkig te maken."
- **[[OS-OS#Taken|Taken van een Besturingssysteem]]:** De bronnen benadrukken verschillende taken:
- Opslaan en ophalen van informatie voor programma's.
- Afschermen van programma's van specifieke hardware.
- Regelen van de gegevensstroom door de computercomponenten.
- Zorgen dat programma's werken zonder onderbrekingen door andere programma's.
- Onafhankelijke programma's in staat stellen samen te werken en informatie te delen.
- Reageren op fouten en gebruikersaanvragen.
- "een tijdsplanning maken voor programma's die resources willen gebruiken." ([[OS-Scheduling|Scheduling]])
- **[[OS-OS#Lagen|Structuur van een Besturingssysteem]] (gelaagd):** De bronnen beschrijven een gelaagde structuur:
- **[[OS-OS#Shell of Command Interpreter|Shell]]:** De interface voor de gebruiker.
- **[[OS-OS#Utilities-laag|Utilities-laag]]:** Bevat routines die "voor deze dingen zorg dragen" wanneer de shell een opdracht ontvangt. Veel opdrachten zijn ingewikkeld en vereisen voorbereiding en controle door de utilities.
- **[[OS-OS#Kernel|Kernel]]:** Het "hart van het besturingssysteem". Deze laag bevat de "routines die het vaakst worden gebruikt en waar het meest op aan komt." De utilities verzorgen het grootste deel van de controle en voorbereiding, maar de kernel voert de kernroutines uit.
- **Beheer van [[OS-Hardware-Resources|Resources]]:** Een cruciale taak van het OS is het efficiënt en eerlijk beheren van systeembronnen:
- **Geheugen:** Het OS moet ervoor zorgen dat processen voldoende geheugen krijgen, maar "mag niet toelaten dat een proces zoveel geheugen heeft dat de andere processen niet kunnen uitgevoerd worden." Bovendien moet het OS de toegang tot geheugen regelen voor privacy en beveiliging, zodat een proces "niet in staat mag zijn zich eigenmachtig toegang tot het geheugen van een ander proces te verschaffen."
- **CPU:** Aangezien er meestal meer processen dan CPU's zijn, moet het OS het gebruik van de CPU regelen. Dit moet "wel eerlijk gebeuren." Belangrijke processen moeten snel de CPU krijgen, terwijl minder belangrijke processen "de CPU niet mogen gebruiken ten koste van andere."
- **Randapparatuur (Devices):** Het OS moet bepalen "wie tot wat toegang heeft" wanneer meerdere processen dezelfde randapparatuur willen gebruiken (bijv. printers, tapedrives). Het moet ook de gegevensstroom regelen bij lezen en schrijven van devices.
- **Bestanden:** Het OS is verantwoordelijk voor het snel kunnen lokaliseren van "een bepaalde file" en "een bepaald record in die file". Dit is een "ingewikkelde taak" gezien de grote hoeveelheid bestanden en records op opslagmedia.

**2. Hoofdthema: Virtualisatie**

- **[[OS-Virtualisatie|Virtuele Machine]] (VM):** Een VM is "een computerprogramma dat een volledige computer nabootst, waar andere (besturings-)programma's op kunnen worden uitgevoerd." Binnen een VM kunnen virtuele hardwarebronnen worden geconfigureerd en een besturingssysteem en programma's worden geïnstalleerd, net als op een fysieke machine.
- **[[OS-Virtualisatie#Soorten VM's|Soorten Virtualisatie]] (Virtuele Machines):Programmeertaal-specifiek:** Biedt een abstractielaag voor de werkelijke computer, functioneert als besturingssysteem voor programma's in die taal. De VM zelf is vaak een programma dat op een bestaand besturingssysteem draait. Code spreekt alleen de functies van de VM aan, niet direct de hardware. Voorbeeld: Java Virtual Machine (JVM). Dit maakt "platform-onafhankelijkheid" mogelijk.
- **Emulatie:** Bootst hardware na (processor, etc.) zodat een bestaand besturingssysteem erop kan draaien als ware het een fysieke computer. Voorbeeld: Windows emuleren in een GNU/Linux omgeving.
- **Applicatie-specifiek:** Bootst meestal geen volledige computer na. Toepassingen draaien in een "container". Voorbeeld: Docker, waarbij containers de Linux kernel delen en direct aanspreken.
- **[[OS-Hypervisor|Hypervisor]] (Virtual Machine Monitor - VMM):** De software die "gebruikt wordt om virtuele machines aan te maken en op te starten." Een hypervisor "regelt de virtualisatie" en maakt het mogelijk voor "één hostcomputer meerdere VM's gelijktijdig te laten draaien door de (hardware) bronnen virtueel te delen."
- **Soorten Hypervisors:Type 1:** Direct op de hardware geïnstalleerd (bare metal). Draait als een lichtgewicht besturingssysteem waarop VM's worden aangemaakt.
- **Type 2:** Draait als een programma binnen een bestaand besturingssysteem.
- **Multi-tenancy:** Een concept waarbij bronnen (hardware, software) worden gedeeld door meerdere "tenants" (individuele gebruikers of groepen). In IT kan dit variëren van het delen van fysieke servers (via VM's) tot het delen van online applicaties.
- **Kenmerken:** Hoger gebruik van beschikbare ruimte, vaak goedkoper.
- **Risico's:** Beveiliging (compromitteren van een gedeelde server kan meerdere tenants beïnvloeden), prestatie-impact (zware belasting door één tenant kan andere beïnvloeden).
- **[[OS-CloudComputing|Cloud Computing]]:** Vaak geassocieerd met multi-tenancy en virtualisatie. "bronnen op aanvraag beschikbaar worden gesteld aan de eindgebruikers." Resources worden vaak automatisch geprovisioneerd. Vaak via een "pay-as-you-go pricing model". Kenmerkend is "[[OS-Elasticiteit|Elasticiteit]]": het automatisch aanpassen van het aantal bronnen aan de vraag.
- **Deployment Modellen:Private Cloud:** Werkt op een (virtueel) private ICT-infrastructuur. Gebruiker heeft volledige controle over data, beveiliging en kwaliteit. Infrastructuurcomponenten worden gedeeld door meerdere afnemers (bijv. afdelingen van een bedrijf), maar de applicaties zelf worden niet gedeeld met externe klanten.
- **Hybride Cloud:** Combinatie van meerdere interne en/of externe Cloud omgevingen, vaak om voor- en nadelen van private en publieke cloud te combineren (bijv. gevoelige data lokaal bewaren, zwaar rekenwerk in publieke cloud).
- **Provisioning:** Het toewijzen van middelen. "Over-provisioning" betekent dat er meer middelen zijn toegewezen dan nodig, wat onnodige kosten met zich meebrengt omdat cloud providers vaak het aantal _voorziene_ bronnen aanrekenen.

**3. Hoofdthema: Containers ([[OS-Docker|Docker]])**

- **Evolutie van VM's naar [[OS-Docker#Containers|containers]]:** Hoewel VM's belangrijk blijven, hebben containers de afgelopen tien jaar aan populariteit gewonnen, mede door Docker. Containers worden gezien als een oplossing voor de complexiteit van het beheren van veel systemen of geïsoleerde services met VM's.
- **Containers vs. VM's:** In tegenstelling tot VM's die een volledige computer nabootsen en virtuele disks gebruiken, "heeft een Docker container geen virtuele disk." Bestanden worden opgeslagen in een "writable container layer" beheerd door een "storage driver".
- **Doel van Containers:** Vaak gebruikt om "een enkele service of applicatie te isoleren en uit te voeren op verschillende Windows- en Linux-versies."
- **Docker [[OS-Docker#Images|Images]]:** Een bestand dat "alles bevat wat nodig is om een applicatie te draaien". Wordt gezien als een "sjabloon", "blauwdruk", of "template". Gedefinieerd door een Dockerfile. Images zijn "Onveranderlijk ('immutable')" en bestaan uit verschillende lagen. Images maken het verspreiden en uitvoeren van applicaties eenvoudiger door benodigde bibliotheken, hulpprogramma's en afhankelijkheden te bundelen.
- **Data Persistence in Docker:** Omdat de container layer verwijderd wordt bij het verwijderen van een container, zijn "volumes en bind mounts" beter voor persistente opslag.
- **[[OS-Docker#Named volume|Named Volumes]]:** Beheerd door Docker, opgeslagen in de Docker storage directory op de host. Nuttig voor "data delen tussen verschillende containers."
- **[[OS-Docker#Bind mount|Bind Mounts]]:** Koppelen een specifieke map op de host aan een map in de container. Handig voor "vanaf de host ook toegang tot de data" en het delen van bestanden en directories tussen host en container.
- **Beveiliging ([[OS-DockerCompose|Port Mapping]]):** Het is een "slechte gewoonte om de database toegankelijk te maken voor buitenaf." Poort mapping is nodig om dit te voorkomen. "Alleen de website heeft toegang nodig tot de database."

**4. Hoofdthema: Opslagmedia en Bestandssystemen**

- **[[OS-PersistenteOpslag|Persistente Opslag]]:** Nodig om data te bewaren wanneer een proces afsluit of RAM beperkt is. Ook voor processen om data te delen, aangezien ze in hun eigen virtuele adresruimte werken en van elkaar zijn afgeschermd.
- **[[OS-PersistenteOpslag|soorten opslag]]:Hard Disk Drive (HDD):** Magnetisch opslagmedium. Bevat draaiende schijven, wat zorgt voor "seek time" vertraging. Biedt "Grote capaciteit" voor een "Lage kost".
- **Solid-State Drive (SSD):** Geen bewegende onderdelen. Opslag in geïntegreerde circuits (ICs). "Sneller dan HDD". Heeft een "Hogere kost per GB". Robuuster dan HDD.
- **CD/DVD:** Optisch opslagmedium. "Beperkte capaciteit en performantie". Vaak "read-only". Geschikt voor "distributie of backup".
- **USB Stick:** Extern opslagmedium via USB. Opslag in ICs (zoals SSD). "Beperkte capaciteit en performantie".
- **[[OS-Files|files]] (Bestand):** Een abstracte eenheid die data uit één of meer blokken op een fysiek opslagmedium groepeert. Verbergt de complexiteit van de fysieke opslag.
- **[[OS-FileSystems|File Systems]] (Bestandssysteem):** Implementeert het beheer van files en het toekennen van blokken. Verbergt de complexiteit van de fysieke opslag voor gebruikers.
- **Eigenschappen van een File:** Naam (met optionele extensie), huidige en maximale grootte, "Toegangsrechten", datum van aanmaak en laatste aanpassing, "Verwijzing naar de datablokken", etc. Deze eigenschappen zijn afhankelijk van het bestandssysteem.
- **[[OS-Files|Sequentieel]]:** Bytes moeten in volgorde worden uitgelezen.
- **[[OS-Files#Bytes uitlezen|Random access]]**: Bytes kunnen in willekeurige volgorde worden uitgelezen.
- **[[OS-Directories|Directory]] (Map):** Groepeert bestanden en kan zelf andere directories bevatten, wat een "hiërarchische structuur" creëert. De implementatie is een taak van het bestandssysteem. Kan worden opgeslagen als een bestand met een inhoudstabel.
- **[[OS-Directories|Absoluut pad]]:** Start bij de root directory en beschrijft de volledige weg (bijv. /home/hogent/os of C:\Users\hogent\os).
- **[[OS-Directories|Relatief pad]]:** Start vanuit een bestaande directory en kan speciale verwijzingen . (huidige directory) en .. (parent directory) gebruiken.
- **[[OS-Mappenstructuur|Mappenstructuur]] per Besturingssysteem:Windows:** Opslagmedia gekoppeld via aparte schijfletters (C:, D:, ...). Beheer van apparaten via Device Manager. Opstartbestanden op aparte bootpartitie.
- **Linux:** Root-directory / bevat alles. Apparaten onder /dev, I/O-apparaten onder /mnt of /media, opstartbestanden onder /boot, configuratiebestanden onder /etc, uitvoerbare bestanden onder /bin, /sbin, /usr/(s)bin, /opt, variabele bestanden onder /var.
- **[[OS-VirtualFileSystem|Virtual File System]] (VFS):** Op Linux en macOS brengt een VFS alle actieve bestandssystemen samen onder "één hiërarchische structuur". Voor de gebruiker lijkt het alsof er slechts één bestandssysteem is. Verbergt de verschillen tussen bestandssystemen. Processen gebruiken algemene OS-functies die de VFS aanspreken, die dit vertaalt naar drivers voor elk bestandssysteem.
- **Mount:** Het inladen van de root directory van een bestandssysteem in een directory van de virtuele hiërarchie.
- **Unmount:** Het ontkoppelen van een reeds ingeladen bestandssysteem van het virtuele bestandssysteem.
- **Partities:** Een fysiek opslagmedium kan worden onderverdeeld in partities. Elke partitie heeft een eigen bestandssysteem. Een "partitietabel" (bijv. MBR of GPT) beschrijft de partities en hun bestandssystemen.
- **MBR (Master Boot Record):** Oudere methode. Beperkingen: max 2TB schijfgrootte, max 4 primaire partities (workaround: extended partities).
- **GPT (GUID Partition Table):** Opvolger van MBR. Onderdeel van UEFI. Ondersteunt schijven > 2TB. Theoretisch onbeperkt aantal partities. Elke partitie heeft unieke GUID. Windows boot support op GPT vereist 64-bit systemen met UEFI (meestal). Linux kan booten van GPT met BIOS firmware.
- **Bootloader:** Verantwoordelijk voor het opstarten van het systeem. Zoekt naar een partitie met een besturingssysteem en schakelt over naar de code in het boot block van die partitie. Opstartbestanden (kernel, root file system) bevinden zich vaak in een aparte bootpartitie en zijn gecomprimeerd.
- **Multi-boot:** Installeren van meer dan één OS op een systeem. Vereist een bootloader die elk OS kan starten. "Chain loading" van bootloaders: een bootloader (bijv. Linux GRUB) verwijst naar de bootloader van een ander OS (bijv. Windows).
- **Voorbeelden van Bestandssystemen:NTFS:** Standaard op Windows. Gebruikt journaling. Vervangt FAT32. Proprietary. Beperkte ondersteuning op macOS en Linux (via NTFS-3G).
- **FAT32:** Ouder, ontwikkeld door Microsoft. Werkt op verschillende OS. Gebruikt 32 bits voor adressering. Beperkingen: max 4GB bestandsgrootte, max 2TB bestandssysteemgrootte. Weinig gebruikt vandaag, vervangen door exFAT.
- **exFAT:** Ontwikkeld door Microsoft. Gericht op USB-sticks en SD-kaarten. Vervangt FAT32 voor deze toepassingen. Gebruikt file allocation table, geen journaling. Proprietary. Goede ondersteuning op macOS en Linux.
- **APFS:** Standaard op macOS. Focus op SSD's en encryptie. Gebruikt GPT partitionering met containers en volumes. Beperkte ondersteuning op Windows en Linux (via third-party drivers).
- **ZFS:** Ontwikkeld door Sun Microsystems. Populair op Linux en FreeBSD. Geavanceerd (volume management, snapshots, etc.). Sterk tegen bitrot en data corruptie.
- **Btrfs:** Ontwikkeld door Oracle. Antwoord op ZFS. Standaard op Fedora. Sterk tegen bitrot en data corruptie. Meer features dan ext4.
- **ISO 9660 / UDF:** Bestandssystemen voor optische schijven (CD/DVD). Gericht op read-only/write-once media. Ondersteund op gangbare platformen.
- **[[OS-OpslagDocker|Opslag in Docker]] vs VM's:** Een VM heeft virtuele disks (bestanden op host). Een Docker container heeft geen virtuele disk, maar een writable container layer.

**5. Hoofdthema: [[OS-Process|Processen]] en [[OS-Threads|Threads]]**

- **[[OS-Process|Process]]:** Een "instantie van een programma dat uitgevoerd wordt op het systeem." Een proces is een soort "container die alles bevat om een programma uit te voeren." [[OS-OS|OS]] gebruikt processen om programma's te beheren en meerdere programma's tegelijk uit te voeren.
- **Programma vs. Proces:** Een programma (binary) is een passief bestand op schijf. Een proces is een actieve instantie in RAM.
- **Address Space:** Een proces heeft een eigen (virtuele) address space in RAM waar het zijn instructies en data opslaat en leest/schrijft.
- **Process Image:** Een momentopname van de address space van een proces in RAM, met:
- **Text:** Uit te voeren instructies.
- **Data:** Globale variabelen.
- **Stack:** Tijdelijke opslag voor variabelen, functie parameters, return-adressen. Beperkt in grootte (stack overflow).
- **Heap:** Dynamisch gealloceerd geheugen (voor objecten, etc.). Blijft beschikbaar tot het wordt opgeruimd.
- **PID (Process Identifier):** Op Linux heeft elk proces een uniek ID. PID 1 is het eerste proces dat opstart (systemd of init). Processen vormen een boomstructuur (ouder-kind relatie).
- **Ontstaan van een Proces (Linux):** Gebruikt de functies fork() en exec(). fork() maakt een kopie van het proces (inclusief address space). exec() overschrijft het nieuwe proces met de inhoud van het gewenste programma.
- **Process States (Scheduling Model):** Beschrijft de verschillende toestanden waarin een proces zich kan bevinden:
- **New:** Nieuw proces, PCB toegevoegd aan process table, nog niet volledig in geheugen geladen.
- **Ready:** Proces wacht om op de CPU te worden uitgevoerd (in de wachtrij).
- **Running:** Proces wordt uitgevoerd op de CPU.
- **Blocked:** Proces wacht op iets (I/O, resource, etc.).
- **Exit:** Proces is afgewerkt (correct of met fout).
- **Suspend:** Proces is uit het RAM verplaatst naar schijf (swapping) om RAM vrij te maken.
- Kan verder onderverdeeld worden in Ready/Suspend en Blocked/Suspend.
- **Overgangen tussen Process States:**Ready -> Running: Scheduler selecteert het volgende proces voor de CPU.
- Running -> Ready: Pre-emption (onderbreking na verstrijken van een tijdslimiet - quantum/time slice) of vrijwillig de CPU vrijgeven.
- Running -> Blocked: Proces wacht op een gebeurtenis (bijv. I/O).
- Blocked -> Ready: Gebeurtenis waarop het proces wachtte heeft plaatsgevonden.
- Overgangen van/naar Suspend (swapping).
- **Threads:** Het "Uitvoeringsgedeelte proces = thread". De kleinste eenheid van geprogrammeerde instructies die onafhankelijk kunnen worden beheerd door een scheduler.
- **Single-threaded:** Proces met één thread.
- **Multi-threaded:** Proces met meerdere threads. Threads kunnen parallel worden uitgevoerd.
- **Delen van Bronnen:** Threads binnen een proces delen instructies, data, toegewezen bronnen (bijv. bestandstoegang). "Elke thread van een proces heeft dus toegang tot alle bronnen toegewezen aan dat proces."
- **Eigen Resources van Threads:** Elke thread heeft zijn eigen registers (inclusief Program Counter), stack en toestand.
- **Afscherming:** Er is "geen afscherming tussen threads binnen eenzelfde proces." Threads kunnen elkaars gegevens lezen, schrijven, verwijderen. Dit is een "groot verschil met processen waar het besturingssysteem processen van elkaar afschermt."
- **Context Switch:** Wisselen tussen threads binnen een proces is "goedkoper" dan een context switch tussen processen, omdat een thread minder data bevat (instructies, data, bronnen worden gedeeld).
- **Soorten Threads:User-Level Threads (ULT):** Beheerd door een bibliotheek in het programma, onafhankelijk van het OS. OS ziet het als single-threaded.
- _Voordelen:_ Sneller (geen system calls), proces heeft controle over scheduling, onafhankelijk van OS.
- _Nadelen:_ Blokkeren van één thread kan het hele proces blokkeren, geen multiprocessing mogelijk.
- **Kernel-Level Threads (KLT):** Beheerd door het besturingssysteem.
- _Voordelen:_ Scheduling op threadniveau mogelijk, blokkeren van één thread beïnvloedt andere niet, multiprocessing mogelijk, OS gebruikt zelf vaak threads.
- _Nadelen:_ Trager (wisselen tussen programma en OS).
- **Combinatie ULT en KLT:** Mogelijk om de voordelen van beide te combineren.

**6. Hoofdthema: [[Parallelisme]] en Synchronisatie**

- **Parallelle Uitvoering:** Treedt op in systemen met meer dan één CPU of kern. Meer dan één taak wordt "gelijktijdig (parallel)" uitgevoerd. Dit is niet hetzelfde als parallelisme.
- **Kritieke Secties:** Delen van programma's waar parallelle processen toegang krijgen tot gemeenschappelijk geheugen of andere gedeelde bronnen. Het OS moet hier "wederzijdse uitsluiting garanderen." Dit betekent dat wanneer een proces in zijn kritieke sectie is, "elk ander proces zijn eigen kritieke sectie niet betreedt."
- **Wederzijdse Uitsluiting (Mutual Exclusion):** Kan ook worden toegepast op de toegang tot bestanden (voorkomen dat 2 processen tegelijk schrijven) en hardware bronnen (bijv. printertaken in wachtrij plaatsen).
- **Het Filosofen Diner Probleem:** Een klassiek voorbeeld dat het probleem van synchronisatie en het voorkomen van deadlocks en starvation illustreert bij het delen van gedeelde bronnen (vorken).
- **Deadlock:** Een situatie waarin "elk proces wacht op een bron die reeds in gebruik is door een ander proces in de verzameling."
- **Voorwaarden voor Deadlock (moeten tegelijkertijd voldaan zijn):Wederzijdse Uitsluiting (Mutual Exclusion):** Gemeenschappelijk gebruik van bronnen moet met uitsluiting plaatsvinden.
- **Bezet Houden en Wachten (Hold and Wait):** Een proces houdt ten minste één bron bezet en wacht op andere bronnen.
- **Geen Voortijdig Ontnemen (No preemption):** Bronnen kunnen alleen vrijwillig worden vrijgegeven door het proces dat ze bezit.
- **Wachten in een Kring (Circular Wait):** Er is een verzameling processen waarbij elk proces wacht op een bron die in het bezit is van het volgende proces in de kring, en het laatste proces wacht op een bron van het eerste.
- **Oplossingen/Preventie van Deadlock:** Door één van de voorwaarden (behalve Mutual Exclusion) te doorbreken. Bijv.: alle bronnen tegelijkertijd aanvragen of bronnen vrijgeven als een aangevraagde bron niet direct beschikbaar is.
- **Deadlock Signaleren:** Het OS kan deadlock opsporen door een "Resource Allocation Graph (RAG)" te bekijken. Een deadlock is een "cyclus in RAG". Algoritmes kunnen cycli in de graaf opsporen.
- **Starvation:** Een situatie waarbij een proces oneindig moet wachten omdat er steeds andere processen voorrang krijgen (geïllustreerd in het filosofen diner probleem met oneerlijke planning).

**7. Overige Belangrijke Concepten**

- **[[OS-Scheduling|Scheduling]]:** Het maken van een tijdsplanning voor programma's/processen die resources willen gebruiken.
- **Instructiecyclus (Fetch-Execute):** De basiscyclus waarin een CPU instructies ophaalt (fetch) en uitvoert (execute).
- **Interrupts:** Gebeurtenissen (nieuwe apparaten, gebruikersactie, fouten, timers) waarop de computer moet reageren. Een extra stap in de fetch-execute cyclus controleert op interrupts.
- **Binaries/Executables:** Bestanden gegenereerd door een compiler. Formaat is OS-specifiek (bijv. PE voor Windows, ELF voor Linux, Mach-O voor Mac). Dit maakt programma's gecompileerd op het ene OS meestal niet uitvoerbaar op een ander OS.
- **[[OS-Scheduling|Context Switch]]:** Het proces waarbij de CPU wisselt van het ene proces/thread naar het andere. De context (inhoud van registers, stack, toestand) van het huidige proces/thread wordt opgeslagen en de context van het volgende wordt geladen.
- **Swapping (Suspend):** Het verplaatsen van processen uit RAM naar schijf om RAM vrij te maken wanneer het geheugen vol raakt.
- **Multi-processor / Multi-core CPU:** Systemen met meer dan één CPU of CPU-kern, die parallelle uitvoering mogelijk maken.
- **Data Parallelisme:** Een vorm van parallelisme waarbij de te verwerken data wordt opgesplitst en dezelfde operatie op elk deel wordt uitgevoerd door verschillende threads. De data wordt verdeeld over de threads.

**8. Voorbeeld Vragen (Examen OS)**

- **Meerkeuze:** Identificeren wat géén voorbeeld is van een besturingssysteem (Office 365).
- **Juist/Fout:** Beoordelen van uitspraken over processen (bijv. eenvoudig aan data van ander proces - fout, slechts één actief op multiprocessor - fout, unieke PID op UNIX - juist, proces blijft bestaan na herstart - fout).
- **Open Vraag:** Kort uitleggen waarom een context switch tussen threads goedkoper is dan tussen processen (threads delen meer bronnen, waardoor minder contextinformatie (PCB) hoeft te worden opgeslagen/geladen).

Dit document biedt een samenvatting van de belangrijkste concepten en feiten die in de verstrekte bronnen worden behandeld, met inbegrip van citaten om de oorspronkelijke formulering te behouden.
