---
title: OS-Mappenstructuur
aliases:
  - Mappenstructuur
  - mappenstructuur
tags:
  - school
  - OS
reference: "[[OS-H04-FileSystems]]"
related notes:
  - "[[MOC-Linux]]"
---

## Overzicht

> [!note] Elke soort heeft eigen systeem

- Windows
- Linux
- MacOS

## Windows

- gekoppeld via aparte schijfletters (C:, D:, ...)
- **Program files:** uitvoerbare bestanden, applicaties
- **Windows\System32:** systeembestanden
- **Users`<gebruikersnaam>`:** home directories
- **Users\AppData:** configuratiebestanden (verborgen)
- **Beheer apparaten:** Device manager
- **Opstartbestanden:** aparte bootpartitie (standaard zonder schijfletter)

## Linux

- **Root-directory `/`:** bevat alles
	- elk bestand zit onder root
- **`/home/<gebruiker>`:** gebruikersbestanden
- **`/dev`:** apparaten
- **`/mnt` of `/media`:** I/O-apparaten
- **`/boot`:** opstartbestanden
- **`/etc`:** configuratiebestanden
- **`/(s)bin`, `/usr/(s)bin` of `/opt`:** uitvoerbare bestanden
	- **`/sbin`:** vereist systeemprivileges
	- **`/bin`:** geen systeemprivileges
- **`/var`:** variabele bestanden (bv. logs)

## MacOS

- **"Main Disk"** (vergelijkbaar met Windows C-schijf)
- **Applications:** geïnstalleerde applicaties
- **Library:** fonts, bestanden gebruikt door apps (gedeeld)
- **System:** macOS besturingssysteem (niet wijzigbaar)
- **Users:** home directories per gebruiker, Shared map
- **Fysiek:** gelijkaardige mappenstructuur als Linux (verborgen in UI)
- **`Volumes` map:** bevat gekoppelde volumes (verborgen in UI, zichtbaar via CLI)