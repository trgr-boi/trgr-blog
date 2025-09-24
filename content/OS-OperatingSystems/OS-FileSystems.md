---
title: OS-FileSystems
aliases:
  - File Systems
tags:
  - school
  - OS
reference: "[[OS-Operating Systems]]"
related notes:
  - "[[MOC-Linux]]"
---

## Overzicht

>[!note] Definitie
> Onderdeel in [[OS-OS|OS]] die fysieke opslagruimte beheert en dit als files en dir's implementeert.
> OS ondersteunt meerdere (tegelijk)

- Contiguous storage
- Linked lists
- File allocation table (FAT)
- Index nodes (inodes)

## Contiguous storage

- In aansluitende blokken opgeslagen
- **Voordelen:** Eenvoudig, goede leessnelheid, random access
- **Nadelen:** Bestand groeit (verplaatsen nodig), fragmentatie (kleine ruimtes)
- Regelmatig defragmenteren nodig
- Geschikt voor "read-only" of "write-once" media ([[OS-PersistenteOpslag|CDs]], [[OS-PersistenteOpslag|DVDs]])

## Linked lists

- Datablokken hoeven niet aan te sluiten
- Elk blok: verwijzing naar volgend blok
- **Voordelen:** Geen fragmentatie
- **Nadelen:** Slechte leessnelheid, geen random access

## File allocation table (FAT)

- Verbetering linked list
- Verwijzingen: samengebracht in één tabel
- Tabel in [[OS-Hardware-Resources|RAM]]: snelle lijst van blokken, random access
- **Voordelen:** Betere leessnelheid dan linked lists, random access
- **Nadeel:** Hoog RAM-verbruik (bv. 1GB voor 1TB schijf)

## Index nodes (inodes)

- Datastructuur: metadata bestand + verwijzingen datablokken
- Enkel inodes van geopende bestanden in RAM
- **Voordelen:** Goede leessnelheid, random access, beperkt RAM-verbruik