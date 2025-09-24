---
title: OS-OpslagDocker
aliases:
  - Opslag in Docker
tags:
  - school
  - OS
reference: "[[OS-H04-FileSystems]]"
related notes:
---

## Overzicht

- VM vs container
- Storage driver en layers
- Persistente opslag in Docker

## **VM vs container**

- **Virtuele machine (VM):**
	- Eén of meerdere virtuele disks.
	- Bestand op fysieke schijf host (bv. Virtualbox .vdi).
	- Virtuele disk: virtueel blokapparaat.
	- Eigen partitietabel, elke partitie eigen file system.
	
- **Docker container:**
	- Geen virtuele disks.
	- Bestanden opgeslagen in "writable container layer".
	- Beheer layer: via "storage driver".
## **Storage driver en layers**

- Docker container bestaat uit:
	- Meerdere "image layers" (readonly).
	- Eén "schrijfbare container layer" (writeable).
- Onderste image layer: basis image.
- Elke layer: houdt wijzigingen bij t.o.v. onderliggende layer.
- Nieuwe container: nieuwe writable layer (container layer).
- Storage driver: beheert layers.
- Container layer: enige aanpasbare layer tijdens uitvoering container.
- Image layers: readonly (container kan alleen lezen).
- Container verwijderen: container layer verwijderd.
- Image layers: niet verwijderd (andere containers gebruiken ze).
- Image verwijderen: image layers verwijderd.
- Meerdere containers: zelfde onderliggende image layers.
## **Persistente opslag in Docker**

- Container layer: verwijderd bij verwijderen container (niet optimaal voor persistentie).
- Layers "ergens" op fysiek filesystem host (afh. storage driver).
- Niet handmatig wijzigen (risico corruptie).
- Beter: volumes en "bind mounts".
	- Volumes: data delen tussen containers.
	- Bind mounts: host toegang tot data.
		- Soort volumes, gemount op VFS Linux host.