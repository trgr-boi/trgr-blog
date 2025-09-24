---
title: OS-vragen H01-03
aliases:
  - vragen H01-03
tags:
  - school
  - OS
  - oefeningen
reference: "[[OS-Operating Systems]]"
related notes:
---

Hier zijn voorbeeldvragen die samenhangen met de geselecteerde bronnen, opgesteld volgens het gevraagde formaat:

# theorie vragen

## 10 Vragen voor met 2-3 zinnen op te antwoorden

1. Wat is de primaire rol van een besturingssysteem en waarom is het essentieel voor het gebruik van een computer?
2. Noem twee belangrijke taken van een besturingssysteem en licht kort toe wat ze inhouden.
3. Leg het verschil uit tussen een Type 1 en een Type 2 hypervisor, inclusief een voordeel en een nadeel van elk.
4. Wat wordt bedoeld met "elasticiteit" in de context van Cloud computing, en waarom is dit een belangrijk kenmerk?
5. Beschrijf kort het concept van "multi-tenancy" en noem één voordeel en één nadeel hiervan in een IT-omgeving.
6. Hoe verschillen Docker containers fundamenteel van virtuele machines (VM's) op het gebied van resourcegebruik en opstarttijden?
7. Wat is een Docker image en hoe verhoudt het zich tot een Docker container?
8. Waarom is het gebruik van "port bindings" essentieel bij het draaien van netwerkdiensten in Docker containers?
9. Leg uit waarom "volumes" belangrijk zijn in Docker en noem twee types volumes.
10. Wat is het doel van Docker Compose en hoe vereenvoudigt het het beheer van Docker-applicaties?

## de antwoorden op de 10 vragen

1. De primaire rol van een besturingssysteem is het fungeren als de link tussen hardware en gebruiker, waardoor mensen de hardware van een computer kunnen gebruiken. Zonder een besturingssysteem zou het bijna onmogelijk zijn om een computer te gebruiken, omdat gebruikers dan rechtstreeks de hardware zouden moeten aansturen en zelf zouden moeten zorgen voor samenwerking tussen hardwarecomponenten.
2. Een belangrijke taak is het **opslaan en ophalen van informatie**, waarbij programma's de mogelijkheid krijgen om gegevens te bewaren en terug te halen. Een andere taak is het **beheer en delen van bronnen** (resources) zoals CPU en geheugen, om conflicten te voorkomen wanneer meerdere gebruikers of programma's hiervan gebruik willen maken.
3. Een Type 1 hypervisor (bare metal) wordt rechtstreeks op de hardware geïnstalleerd zonder onderliggend besturingssysteem, wat deze efficiënter maakt maar complexer in gebruik. Een Type 2 hypervisor (gehost) draait als een programma bovenop een bestaand besturingssysteem, waardoor deze eenvoudiger te installeren is, maar minder krachtig en efficiënt is dan een Type 1 hypervisor.
4. Elasticiteit in Cloud computing verwijst naar de mate waarin het aanbod van computerbronnen automatisch wordt afgestemd op een stijgende of dalende vraag. Dit is belangrijk omdat het zorgt voor optimale benutting van resources, door automatisch meer (virtuele) bronnen in te zetten bij piekbelasting en deze vrij te geven bij dalende vraag, wat over- of under-provisioning helpt voorkomen.
5. Multi-tenancy is een concept waarbij computerbronnen (hardware of software) gedeeld worden over verschillende tenants (gebruikers of groepen gebruikers). Een voordeel is efficiënter gebruik van beschikbare bronnen en lagere operationele kosten. Een nadeel is minder isolatie en verhoogde beveiligingsrisico's, evenals een potentieel negatieve beïnvloeding van prestaties tussen tenants.
6. Docker containers zijn lichter en efficiënter dan VM's omdat ze de kernel van het besturingssysteem van de hostmachine delen, in plaats van een volledig gesimuleerd besturingssysteem te omvatten. Dit resulteert in snellere opstarttijden en minder overhead, aangezien er geen apart OS binnen de container hoeft te booten.
7. Een Docker image is een onveranderlijke "sjabloon" of "blauwdruk" die alles bevat wat nodig is om een applicatie te draaien, inclusief code en afhankelijkheden. Een Docker container is een draaiend, geïsoleerd exemplaar van een image, vergelijkbaar met een actieve instantie van een programma in het RAM-geheugen, waar gegevens bewerkt kunnen worden zonder de originele image aan te passen.
8. Port bindings zijn essentieel omdat Docker containers standaard geïsoleerd zijn en geen directe toegang hebben tot het netwerk van de host. Door een poort van de container te binden aan een poort op de host, wordt het mogelijk om vanaf de buitenwereld (host of netwerk) toegang te krijgen tot de applicatie of dienst die binnen de container draait.
9. Volumes zijn belangrijk in Docker om gegevens persistent op te slaan buiten de levenscyclus van een container, zodat wijzigingen niet verloren gaan wanneer een container wordt verwijderd. Twee typen volumes zijn "named volumes", die door Docker worden beheerd in een specifieke opslagdirectory op de host, en "bind mounts", die een specifieke map op de host koppelen aan een map in de container voor directe toegang.
10. Docker Compose is een tool die het beheer van multi-container Docker-applicaties vereenvoudigt door alle services in één `docker-compose.yml` bestand te definiëren. Het stroomlijnt het proces van het bouwen, netwerken en beheren van meerdere containers die samen een applicatie vormen, waardoor complexe Docker-commando's vermeden worden en consistentie in omgevingen gewaarborgd wordt.

## 10 meerkeuze vragen

1. Welke van de volgende is **geen** taak van een besturingssysteem? 
	1. a) Opslaan en ophalen van informatie 
	2. b) Programma's afschermen van specifieke hardware 
	3. c) Hardware produceren 
	4. d) Een tijdsplanning maken voor programma's die resources willen gebruiken
    
2. Welk besturingssysteem wordt genoemd als een voorbeeld van een "single-tasking" besturingssysteem? 
	1. a) Windows 11 
	2. b) macOS 14 Sonoma 
	3. c) MS-DOS 
	4. d) Ubuntu 24.04.1 LTS
    
3. Welke term wordt gebruikt voor het hart van het besturingssysteem, dat de meest frequent gebruikte en cruciale routines bevat? 
	1. a) Shell 
	2. b) Utilities 
	3. c) Kernel 
	4. d) Command interpreter
    
4. Wat is het belangrijkste voordeel van virtualisatie? 
	1. a) Het maakt computers trager door overhead. 
	2. b) Het zorgt voor een grotere ecologische voetafdruk. 
	3. c) Efficiënter gebruik van de beschikbare hardware. 
	4. d) Het vereist meer fysieke computers.
    
5. Welke type hypervisor wordt rechtstreeks op de hardware geïnstalleerd zonder onderliggend besturingssysteem? 
	1. a) Type 1 hypervisor 
	2. b) Type 2 hypervisor 
	3. c) Programmeertaal-specifieke VM 
	4. d) Applicatie-specifieke VM
    
6. Wat is een kenmerk van "pay-as-you-go" pricing in Cloud computing? 
	1. a) Een vaste prijs, ongeacht het gebruik. 
	2. b) Kosten zijn afhankelijk van de effectief gebruikte bronnen. 
	3. c) Alleen van toepassing op private Cloud-omgevingen. 
	4. d) De prijs blijft constant, zelfs bij schommelingen in de vraag.
    
7. Welk Cloud service model geeft de gebruiker de meeste controle over het besturingssysteem en de (virtuele) hardware? 
	1. a) Software as a Service (SaaS) 
	2. b) Platform as a Service (PaaS) 
	3. c) Infrastructure as a Service (IaaS) 
	4. d) Everything as a Service (EaaS)
    
8. Waarom is het gebruik van de `latest` tag voor Docker images in productieomgevingen over het algemeen een slecht idee? 
	1. a) Het maakt de image onveranderlijk. 
	2. b) Het is onduidelijk welke versie van de image daadwerkelijk wordt gebruikt, wat tot onverwachte problemen kan leiden. 
	3. c) Het vereist extra schijfruimte. 
	4. d) Het verhindert het gebruik van port bindings.
    
9. Welke van de volgende Docker-concepten is vergelijkbaar met een "draaiend exemplaar" van een programma, met een beschrijfbare laag erbovenop? 
	1. a) Image
	2. b) Dockerfile 
	3. c) Volume 
	4. d) Container
    
10. Wat is het belangrijkste voordeel van het gebruik van een geïsoleerd netwerk in Docker Compose voor multi-container applicaties? 
	1. a) Containers kunnen niet met elkaar communiceren. 
	2. b) Het maakt de applicatie minder complex. 
	3. c) Containers kunnen gemakkelijk met elkaar communiceren zonder interferentie van andere containers op de host. 
	4. d) Het verhoogt de beveiligingsrisico's.
    

## antwoorden op meerkeuze vragen

1. c) Hardware produceren
2. c) MS-DOS
3. c) Kernel
4. c) Efficiënter gebruik van de beschikbare hardware.
5. a) Type 1 hypervisor
6. b) Kosten zijn afhankelijk van de effectief gebruikte bronnen.
7. c) Infrastructure as a Service (IaaS)
8. b) Het is onduidelijk welke versie van de image daadwerkelijk wordt gebruikt, wat tot onverwachte problemen kan leiden.
9. d) Container
10. c) Containers kunnen gemakkelijk met elkaar communiceren zonder interferentie van andere containers op de host.

# termen

## geef 20 termen

1. Besturingssysteem (OS)
2. Hardware
3. Resources
4. Proces
5. Kernel
6. Scheduling
7. Virtualisatie
8. Virtuele machine (VM)
9. Hypervisor
10. Type 1 Hypervisor
11. Multi-tenancy
12. Cloud Computing
13. Elasticiteit
14. Infrastructure as a Service (IaaS)
15. Software as a Service (SaaS)
16. Docker
17. Image
18. Container
19. Port binding
20. Docker Compose

## antwoorden van termen

1. **Besturingssysteem (OS):** Een programma dat de link vormt tussen computerhardware en de gebruiker, waardoor het mogelijk wordt om de hardware te gebruiken en gewenste taken uit te voeren.
2. **Hardware:** De fysieke componenten van een computer, zoals de CPU, geheugen, secundaire opslagapparatuur en randapparatuur.
3. **Resources (bronnen):** Elementen van een computersysteem, zoals persistente opslag (bestanden), RAM-geheugen, CPU-uitvoeringstijd en randapparatuur, die door processen worden aangesproken en beheerd door het besturingssysteem.
4. **Proces:** Eén of meer reeksen van opdrachten die door een besturingssysteem als een werkeenheid worden beschouwd; het is een onafhankelijk uitgevoerde entiteit die meedingt naar het gebruik van bronnen.
5. **Kernel:** Het hart van het besturingssysteem, dat de routines bevat die het vaakst worden gebruikt en waar het meest op aankomt.
6. **Scheduling:** De manier waarop het besturingssysteem prioriteiten toekent aan processen en beslist welk programma wat krijgt en wanneer, vaak in combinatie met een prioriteitenwachtrij.
7. **Virtualisatie:** Het creëren van een virtuele (in plaats van daadwerkelijke) versie van iets, zoals virtuele computerhardwareplatforms, opslagapparaten of netwerkbronnen.
8. **Virtuele machine (VM):** Een computerprogramma dat een volledige computer nabootst, waarop andere (besturings-)programma's kunnen worden uitgevoerd alsof het een fysieke machine betreft.
9. **Hypervisor:** De software die wordt gebruikt om virtuele machines aan te maken en op te starten, en die ervoor zorgt dat de fysieke hardware gedeeld wordt over de verschillende virtuele machines.
10. **Type 1 Hypervisor:** Een hypervisor die rechtstreeks op de hardware ligt (bare metal), zonder onderliggend besturingssysteem, en die daardoor zeer efficiënt is, voornamelijk gebruikt op servers.
11. **Multi-tenancy:** Een concept waarbij computerbronnen mogelijks gedeeld worden over verschillende "tenants" (individuele gebruikers of groepen gebruikers met gemeenschappelijke toegang), in tegenstelling tot een dedicated omgeving.
12. **Cloud Computing:** Het via een netwerk (vaak het internet) op aanvraag beschikbaar stellen van hardware, software en gegevens.
13. **Elasticiteit:** De mate waarin het aanbod van (virtuele) bronnen zich automatisch afstemt op een stijgende of dalende vraag in een Cloud-omgeving.
14. **Infrastructure as a Service (IaaS):** Een Cloud service model waarbij de gebruiker infrastructuur (meestal virtuele machines) aangeboden krijgt en volledige controle heeft over het besturingssysteem, de software en (virtuele) hardware.
15. **Software as a Service (SaaS):** Een Cloud service model waarbij de aanbieder eindapplicaties aanbiedt "via de Cloud" (bijvoorbeeld e-mail of klantenbeheer), die vaak via een webbrowser te gebruiken zijn, waarbij de aanbieder volledige controle heeft over de applicaties.
16. **Docker:** Een containertechnologie die een lichtere, snellere en flexibelere manier biedt om applicaties te draaien door ze te isoleren in containers die de kernel van de hostmachine delen.
17. **Image:** Een onveranderlijk "sjabloon" of "blauwdruk" van een gevirtualiseerde omgeving die een programma en al zijn benodigde afhankelijkheden bevat, gedefinieerd door een Dockerfile.
18. **Container:** Een draaiend, geïsoleerd exemplaar van een Docker image met een beschrijfbare laag erbovenop, waarin een programma wordt uitgevoerd zonder directe kennis van de host.
19. **Port binding:** Het proces waarbij een poort van een Docker container wordt gekoppeld aan een poort op de host, om toegang te krijgen tot de services die binnen de container draaien vanaf de buitenwereld.
20. **Docker Compose:** Een tool die het beheer van multi-container Docker-applicaties vereenvoudigt door alle services en hun configuratie in een enkel `docker-compose.yml` bestand te definiëren.

# commando's

## geef 10 voorbeelden van commando's waar ik elk onderdeel van moet uitleggen

1. `sudo docker run hello-world`
2. `sudo docker run -p 8123:80 nginx`
3. `sudo docker run -p 8123:80 -v ./website/:/usr/share/nginx/html nginx`
4. `sudo docker run -p 8123:80 -v ./website/:/usr/share/nginx/html:ro nginx:1.24.0`
5. `sudo docker run -d --name webapp -e DATABASE_URL=mysql://user:password@host:3306/dbname -e DATABASE_PASSWORD=my-secret-password myapp:latest`
6. `docker volume create mijn-volume`
7. `docker compose up`
8. `docker compose up --detach`
9. `docker compose down`
10. `docker compose logs wordpress`

## antwoorden van de commando's

1. `sudo docker run hello-world`
    
    - `sudo`: Staat voor "superuser do" en wordt gebruikt om een opdracht met root-rechten uit te voeren, vaak vereist voor Docker-commando's om systeemwijzigingen toe te staan.
    - `docker`: Het hoofdcommando voor het interactief beheren van Docker-containers en -images.
    - `run`: Een subcommando van `docker` dat gebruikt wordt om een nieuwe container te maken en deze te starten op basis van een gespecificeerde image.
    - `hello-world`: De naam van de Docker image die gebruikt moet worden om de container te creëren en te starten. Deze image is een basisvoorbeeld dat een eenvoudig bericht afdrukt om te bevestigen dat Docker correct werkt.
2. `sudo docker run -p 8123:80 nginx`
    
    - `sudo docker run`: Zoals hierboven, om een container met root-rechten te maken en te starten.
    - `-p 8123:80`: Dit is de "port binding" optie.
        - `-p`: Vlag die aangeeft dat een poortbinding moet worden geconfigureerd.
        - `8123`: De poort op de **hostmachine** (bijv. je laptop) die toegankelijk wordt gemaakt.
        - `:`: Scheidingsteken tussen hostpoort en containerpoort.
        - `80`: De poort **binnen de container** waarop de service (in dit geval de Nginx webserver) luistert. Verkeer naar poort 8123 op de host wordt doorgestuurd naar poort 80 in de container.
    - `nginx`: De naam van de Docker image die gebruikt moet worden, in dit geval de officiële Nginx webserver image.
3. `sudo docker run -p 8123:80 -v ./website/:/usr/share/nginx/html nginx`
    
    - `sudo docker run -p 8123:80`: Zoals hierboven.
    - `-v ./website/:/usr/share/nginx/html`: Dit is de "bind mount" optie, een type volume.
        - `-v`: Vlag die aangeeft dat een volume moet worden gekoppeld.
        - `./website/`: Het **absolute of relatieve pad op de hostmachine** (vanaf de directory waar het commando wordt uitgevoerd) dat gekoppeld moet worden.
        - `:`: Scheidingsteken tussen hostpad en containerpad.
        - `/usr/share/nginx/html`: Het **pad binnen de container** waar de hostmap gekoppeld wordt. In dit geval is het de standaardmap waar Nginx webbestanden zoekt.
    - `nginx`: De naam van de Docker image die gebruikt moet worden.
4. `sudo docker run -p 8123:80 -v ./website/:/usr/share/nginx/html:ro nginx:1.24.0`
    
    - `sudo docker run -p 8123:80 -v ./website/:/usr/share/nginx/html`: Zoals hierboven.
    - `:ro`: Staat voor "read-only". Dit betekent dat de container alleen leesrechten heeft op de gekoppelde map van de host. De container kan bestanden in `./website/` lezen, maar niet wijzigen of nieuwe bestanden maken.
    - `nginx:1.24.0`: De naam van de Docker image met een specifieke "tag".
        - `nginx`: De naam van de image.
        - `:`: Scheidingsteken tussen image naam en tag.
        - `1.24.0`: De specifieke versie (tag) van de Nginx image die gebruikt moet worden. Het expliciet opgeven van een tag voorkomt dat `latest` wordt gebruikt, wat onverwachte problemen kan veroorzaken bij updates.
5. `sudo docker run -d --name webapp -e DATABASE_URL=mysql://user:password@host:3306/dbname -e DATABASE_PASSWORD=my-secret-password myapp:latest`
    
    - `sudo docker run`: Zoals hierboven.
    - `-d`: Staat voor "detach". Hiermee wordt de container op de achtergrond gestart en wordt de terminal vrijgegeven.
    - `--name webapp`: Geeft een specifieke naam aan de container.
        - `--name`: Vlag die een naam toekent aan de container.
        - `webapp`: De gewenste naam voor de container. Dit maakt het gemakkelijker om de container later te identificeren en te beheren.
    - `-e DATABASE_URL=mysql://user:password@host:3306/dbname`: Stelt een "environment variable" in voor de container.
        - `-e`: Vlag die aangeeft dat een omgevingsvariabele moet worden ingesteld.
        - `DATABASE_URL`: De naam van de omgevingsvariabele.
        - `=mysql://user:password@host:3306/dbname`: De waarde die aan de omgevingsvariabele wordt toegekend. Dit wordt door de applicatie binnen de container gebruikt om verbinding te maken met een database.
    - `-e DATABASE_PASSWORD=my-secret-password`: Stelt nog een omgevingsvariabele in, specifiek voor het databasewachtwoord.
    - `myapp:latest`: De naam en tag van de image die moet worden gebruikt om deze specifieke applicatiecontainer te starten.
6. `docker volume create mijn-volume`
    
    - `docker`: Het hoofdcommando voor Docker.
    - `volume`: Een subcommando van `docker` dat wordt gebruikt voor het beheren van Docker volumes.
    - `create`: Een subcommando van `docker volume` om een nieuw named volume aan te maken.
    - `mijn-volume`: De naam die aan het nieuw te creëren named volume wordt gegeven. Dit volume wordt door Docker zelf beheerd op de host.
7. `docker compose up`
    
    - `docker`: Het hoofdcommando voor Docker.
    - `compose`: Een subcommando voor het beheren van multi-container Docker-applicaties gedefinieerd in een `docker-compose.yml` bestand.
    - `up`: Dit commando bouwt (indien nodig) de services die in het `docker-compose.yml` bestand zijn gedefinieerd, creëert de bijbehorende containers, en start deze. Het creëert ook een geïsoleerd netwerk voor deze services. Standaard draait dit op de voorgrond.
8. `docker compose up --detach`
    
    - `docker compose up`: Zoals hierboven, bouwt en start de services.
    - `--detach` (of `-d`): Een optie die ervoor zorgt dat de containers op de achtergrond draaien, waardoor de terminal vrijkomt na het starten van de services.
9. `docker compose down`
    
    - `docker`: Het hoofdcommando voor Docker.
    - `compose`: Subcommando voor Docker Compose.
    - `down`: Dit commando stopt en verwijdert alle containers, netwerken en volumes (tenzij expliciet persistentie is geconfigureerd) die zijn aangemaakt door `docker compose up` voor het huidige project.
10. `docker compose logs wordpress`
    
    - `docker`: Het hoofdcommando voor Docker.
    - `compose`: Subcommando voor Docker Compose.
    - `logs`: Een subcommando dat de logs van de services in een Docker Compose-project weergeeft.
    - `wordpress`: De naam van de specifieke service (container) waarvan de logs moeten worden weergegeven, zoals gedefinieerd in het `docker-compose.yml` bestand.