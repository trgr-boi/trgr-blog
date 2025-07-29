---
title: OS-Hypervisor
aliases:
  - Hypervisor
  - hypervisor
  - type 1
  - bare metal
  - type 2
tags:
  - school
  - OS
reference: "[[OS-Virtualisatie]]"
---

## Overzicht

> [!summary] Definitie
> Software die gebruikt wordt om VM's aan te maken en te beheren

- **Virtual Machine Manager** (VMM)
- zorgt voor verdeling fysieke [[OS-Hardware-Resources|hardware]]
- 2 types
	- type 1, type 2

## Type 1 (Bare Metal)

- ook **Native hypervisor** genoemd
- rechtstreeks op [[OS-Hardware-Resources|hardware]] geïnstalleerd
	- geen onderliggende [[OS-OS|OS]] nodig
	- is zelf een *light-weight* OS
- voornamelijk op servers
- voorbeelden:
	- VMWare ESXi
	- Citrix Xen
	- Microsoft Hyper-V
	- Proxmox

### Nadelen

- veel complexer om op te zetten

## Type 2

- programma bovenop [[OS-OS|OS]]
- eenvoudigere installatie
	- vaak zoals andere applicaties
- vooral op persoonlijke computers
- voorbeelden:
	- VirtualBox
	- VMWare Workstation
	- Parallels Desktop

## Nadelen

- minder krachtig dan Type 1
