---
title: OS-Virtualisatie
aliases:
  - Virtualisatie
  - virtualisatie
  - VM
  - vm
tags:
  - school
  - OS
reference: "[[OS-H02-Virtualisatie&cloud]]"
---

## Overzicht

> [!summary] Definitie
> creëren van een virtuele versie van iets
> > computer hardware platformen
> > opslagaperatuur
> > netwerkbronnen

> [!question] traditioneel vs virtualisatie?
> **Traditioneel:** 1 besturingssysteem. Kunnen meerdere OS'en maar niet tegelijk
> **Virtualisatie:** laat toe voor meerdere OS'en tegelijk, maar delen dezelfde hardware

> [!info] Belangrijkste doel
> > Effectief gebruiken van beschikbare [[OS-Hardware-Resources|Hardware]]
> > Vooral voor krachtige systemen (servers, datacentra,...)

- [[OS-Hypervisor|Hypervisor]]
	- [[OS-Hypervisor#Type 1 (Bare Metal)|Type 1 (Bare Metal)]]
	- [[OS-Hypervisor#Type 2|Type 2]]
- Voor- en nadelen
- soorten VM's

- Werken als afzonderlijke computers
	- [[OS-Hardware-Resources|Hardware]] wordt verdeelt via [[OS-Scheduling|Scheduling]]
- Container virtualisatie zoals [[OS-Docker|Docker]]
	- Speciale vorm
	- Enkel isoleren van app
	- Kernel is gedeelt


## Traditional deployment

- een klant kreeg 1 computer

### Nadelen

- moeilijk om verschillende versies te draaien
- Potentiële crashes van het besturingssysteem of programma die de hele server offline konden brengen
- Inefficiënt gebruik [[OS-Hardware-Resources|hardwarebronnen]] -> server vaak onderbenut bleef als voor één klant werd gebruikt
- Moeilijkheden met dynamisch schalen en verhuizen

## [[OS-Hypervisor|Hypervisor]]

![[OS-Hypervisor#Overzicht]]

## Voordelen

- Efficiënter gebruik van hardware
- Goedkoper
- Lagere ecologische afdruk

## Nadelen

- Niet alle software is geschikt
- Minder prestatie (bv. gamen moeilijker)
- Complexer om op te zetten of onderhouden
	- Kan '[[OS-VM sprawl|VM sprawl]] veroorzaken'

## Soorten VM's

1. Programeertaal gericht (JVM)
2. Emulatie (Virtualbox)
3. application gericht (Docker)