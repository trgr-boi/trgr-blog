---
title: OS-DockerCompose
aliases:
  - docker compose
  - compose
tags:
  - school
  - OS
  - docker
  - server
reference: "[[OS-H03-Docker]]"
related notes:
  - "[[OS-Docker]]"
---

## Overzicht

> [!question] Waarom een extra tool?
> Voor meerdere [[OS-Docker#Containers|containers]] tegelijk te kunne opstarten en stoppen
> Voor containers in [[yml]] te kunnen configureren

- kan alles wat [[OS-Docker|Docker]] kan (port bindings, volumes,...)
- gewoon docker kan leiden tot **complexe commando's**
- beheert eenvoudiger meerdere containers
- alles in 1 [[yml]] file

### Voordelen

- eenvoudige config
- beheer van **multi-container** apps
	- bv. web-server en database server
- **Geïsoleerd netwerk**/**Port mapping**
	- containers kunnen communiceren via service naam (ingebouwde DNS) in plaats van ip
		- hierdoor moet bv. databank niet publiek toegankelijk zijn via het internet
- Infrastructure as Code (IaC)
	- door in code -> beter overzicht, onderhoud
- herhaalbare code
- gemakkelijk starten en stoppen