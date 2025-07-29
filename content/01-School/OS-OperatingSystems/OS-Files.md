---
title: OS-Files
aliases:
  - files
  - Sequentieel
  - Random access
tags:
  - school
  - OS
reference: "[[OS-H04-FileSystems]]"
related notes:
  - "[[MOC-Linux]]"
---

## Overzicht

> [!question] Wat is een file?
> Fysiek opslagmedium: onderverdeeld in blokken
> File: groepeert data uit één of meer blokken
> Abstracte eenheid: verbergt complexiteit fysieke opslag
> Implementatie: door bestandssysteem

- Voorstelling
- Eigenschappen
- Soorten (UNIX)
	- Commando's
	- Bytes uitlezen

## Voorstelling

- Voorgesteld als opeenvolging van bytes
- Abstractie: bytes kunnen verspreid zijn over opslagmedium

## Eigenschappen

- Naam, visueel extensie (`README.MD`)
- Huidige grootte
- Toegangsrechten
- Datum laatste aanpassing
- Verwijzing naar datablokken
- Afhankelijk van bestandssysteem

## Soorten (UNIX)

> [!quote] *"Everything is a file"*

- **Gewone bestanden:** data
- **[[OS-Directories|Directories]]:** bevatten andere bestanden/directories (hiërarchie)
- **Links:** bestanden op meerdere plaatsen zichtbaar
- **Speciale bestanden (block/character special):** toegang tot hardware
- **Sockets:** netwerkcommunicatie
- **Pipes (FIFO):** output proces verbindt met input ander [[OS-Process|proces]]

### Commando's

- `ls -l` : toont type van bestand
- `ls-F` : toont type van suffix
	- `/` : dir
	- `*` : uitvoerbaar bestand
	- `@` : link
	- `=` : socket
	- `|` : named pipe

```bash
drwx------@   9 Tuur  staff     288 May 30 23:18 Pictures/
-rwxr-xr-x@ 1 Tuur  staff  2067 Mar 11 16:18 syncGit-server.sh*
lrwxr-xr-x@   1 Tuur  staff      27 May 30 23:18 git-tools@ -> .dotfiles/scripts/git-tools
```
### Bytes uitlezen

- **Sequentieel:** bytes in volgorde uitlezen
- **"Random access":** bytes in willekeurige volgorde uitlezen
