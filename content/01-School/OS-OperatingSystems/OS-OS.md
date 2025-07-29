---
tags:
  - school
  - OS
reference: "[[OS-H01-besturingssystemen]]"
title: OS-OS
aliases:
  - operating system
  - Single-task
  - multi-task
  - multi-User
  - OS taken
  - OS lagen
  - Shell
  - Utilities-laag
  - Kernel
  - os
  - OS
  - Besturingssysteem
---

## Overzicht

> [!summary] Definitie
> **OS** = een programma die hardware bestuurd

> [!info] link tussen **gebruiken** en **hardware**
> anders rechtstreeks moeten aanspreken
> opdracht gebruiker > OS > hardware

- taken
- soorten
- lagen
- Evolutie

## Taken

- geeft mogelijkheid aan programma's om data op te slaan
- gegevenstroon regelen
- prioriteiten regelen ([[OS-Scheduling|scheduling]])
- beheren & delen van [[OS-Hardware-Resources|resources]]
	- veel programma's willen (dezelfde) bronnen tegelijk ([[OS-Concurrency|Concurrency]])
	- moet zorgen voor voldoende [[OS-Hardware-Resources|resources]] per [[OS-Process|process]]
- tijdelijke samenwerken mogelijk maken
- reageren op fouten (bv [[OS-Deadlock|deadlock]])
- tijdsplanning maken voor programma's die resources willen ([[OS-Scheduling|scheduling]])

## Soorten
1. single-task
2. multi-task
3. multi-User
	- meerdere gebruikers tegelijk die meerdere programma's kunnen runnen
	- of multiprogrammering

### Single-task

- één programma tegelijk
- bv. MS-DOS

![[OS-OS.png]]

### multi-task
- meerdere programma's tegelijk
- meeste moderne OSen

![[OS-OS-1.png]]

### multi-User
- meerdere gebruikers tegelijk die meerdere programma's kunnen runnen
- of multiprogrammering

![[OS-OS-2.png]]

## Lagen

> [!question] waarom lagen?
> lagen helpen bij het organiseren van de functie van een OS. Deze kan heel complex zijn, maar door opsplitsen komt er meet begrip

1. Shell of Command Interpreter
2. utilities-laag
3. kernel

![[OS-OS-3.png]]

### Shell of Command Interpreter

- toplaag
- laag waarmee gebruiker communiceert (in commands)
- reageert op opdrachten van gebruiker
- roept routines aan in utilities-laag

### Utilities-laag

- bevat routines die zorgen voor complexere taken & controle

### Kernel

- onderste laag
- hart van OS
- bevat kritieke routines voor uitvoering
- geeft taken aan hardware

## [[OS-Evolutie|Evolutie]]

![[OS-Evolutie#Evolutie]]

## Zie ook

- [[OS-Process|Process]]
- [[OS-Scheduling|Scheduling]]
- [[OS-Concurrency|Concurrency]]
- [[OS-Threads|Threads]]