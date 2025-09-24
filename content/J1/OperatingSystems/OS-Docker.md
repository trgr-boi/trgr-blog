---
title: OS-Docker
aliases:
  - Docker
  - docker
  - images
  - containers
  - Port bindings
  - Volumes
  - named volumes
  - Bind mounts
  - Tags
  - Environment variable
tags:
  - school
  - OS
  - docker
  - server
reference: "[[OS-H03-Docker]]"
related notes:
  - "[[DOCKER Reference Sheet]]"
  - "[[OS-DockerCompose]]"
---

## Overzicht

> [!note] Definitie
> Speciale vorm van virtualisatie.
> Maakt gebruik van containers in plaats van [[OS-Virtualisatie|VM]]'s

- in plaats van volledige computer visualiseren
	- deelt [[OS-OS|Kernel]] van host -> **efficiënter**
- enkel benodigde afhankelijkheden geïsoleerd

![[OS-Docker.png]]
### Voordelen

- snellere opstarttijd
- efficiënter gebruik van [[OS-Hardware-Resources|Resources]]
- **app-specifieke virtualisatie**

## Kernconcepten

- images
- containers

### Images

> [!note] Definitie
> 'Blauwdruk' van applicatie

- wordt gedefinieerd in een **dockerfile**
- devs maken images van apps om makkelijker rond te versprijden
- [Docker Hub](https://hub.docker.com/) = centrale repo voor images

### Containers

> [!note] Definitie
> Draaiend exemplaar van een image

- geïsoleerde omgeving voor code
	- geen kennis van host
	- denkt dat het gewoon op hoost draait
- copy van image met extra **schrijfbare laag**
	- kan wijzigingen hierin opslaan
- meerdere containers kunnen zelfde image draaien

## Belangrijke concepten

### Port bindings


- linkt poort van host van poort van container
- container heeft standaard geen toegang vanuit host

```bash
# in **docker run commando**
-p <hostpoort>:<containerpoort>
```

### Volumes

- maakt link tussen host directory en container directory
- data in container gaat weg als container afsluit

#### Named volume

- beheert door docker
- in Docker Storage Directory: `/var/lib/docker/volumes/`

```bash
# volume aanmaken
docker volume create <naam_volume>

# volume toevoegen in **docker run commando**
-v <naam_volume>:/data
```

#### Bind mount

- koppelt dir van host aan directory in container

```bash
# in **docker run commando**
-v <dir-host>:<dir-container>
```

## Tags

- voor specifieke versie van app
- geen = `latest`

```bash
# in **docker run commando**
<naam_image>:stable(of andere versie)
```

## Environment variable

- config instellingen (URL's, wachtwoorden,...)
- maakt images herbruikbaar

## Voorbeeld

```bash
docker run -d \
nextcloud \
-p 8080:80 \
-v /home/admin/containers/nextcloud/html:/var/www/html \
-v /home/admin/containers/nextcloud/config:/var/www/html/config \
-v /home/admin/documents/documents/data:/var/www/html/data \
-e DATABASE_NAME=test
-e DATABASE_PASSWORD=test123
```
