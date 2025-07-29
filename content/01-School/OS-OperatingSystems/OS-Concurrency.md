---
tags:
  - school
  - OS
reference: "[[OS-H06-Concurrency]]"
title: OS-Concurrency
---

## Overzicht

> [!important] Processen zijn meestal niet onafhankelijk, processen zijn concurrent

- [[OS-Process|Processen]] die tegelijk uitvoeren
- multiprocessen
- snel schakelen tussen taken (timesharing)
	- illusie van gelijktijdigheid
- verhoogt productiviteit
	- **maar** zorgt voor uitdaging
		- communicatie tussen [[OS-Process|Processen]]
		- delen van [[OS-Hardware-Resources|resources]]
		- synchronisatie
	- wanneer gedeelde bronnen -> conflicten
	- [[OS-Deadlock|deadlock]]