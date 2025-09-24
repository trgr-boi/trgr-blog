---
title: OS-Directories
aliases:
  - Directories
  - dir
  - Directory
  - Absoluut
  - Absoluut pad
  - Relatief
  - Relatief pad
tags:
  - school
  - OS
reference: "[[OS-H04-FileSystems]]"
related notes:
  - "[[MOC-Linux]]"
---

## Overzicht

> [!note] Definitie
> Groepeert bestanden
> Kan andere dirs bevatten
> Creërd hiërarchische structuur
> **Implementatie:** door bestandssysteem (bv. als bestand met inhoudstafel)

> [!question] Hoe ziet de [[OS-H04-FileSystems|file system]] dit? (unix-based)
> Opgeslagen als bestand
> Bevat "directory entry" per file/subdirectory
> Entry: verwijzing naar eerste datablok of inode
> Opslag naam: deel van entry (variabele grootte, fragmentatie) of apart in heap (heapbeheer nodig)

- Hiërarchie
- Padnamen

## Hiërarchie

- File system vormt een boomstructuur
![[OS-Directories.png]]

## Padnamen

- **Absoluut** 
	- Vanuit root (`/`)
	- Doorloopt hiërarchie
	- Voorbeelden
		- UNIX: `/home/hogent/os` (slash als scheidingsteken)
		- Windows: `C:\Users\hogent\os` (backslash, start met drive letter)
- **Relatief**
	- Vanuit huidige positie
	- `.` : huidige dir
	- `..` : parent (vorige) dir
	- Voorbeeld: `../home/hogent/os`