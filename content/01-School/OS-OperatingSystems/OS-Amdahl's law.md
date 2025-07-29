---
title: OS-Amdahl's law
aliases:
  - Amdahl's law
tags:
  - school
  - OS
reference: "[[OS-H06-Concurrency]]"
related notes:
---


[wiki](https://en.wikipedia.org/wiki/Amdahl%27s_law)

- $S$: % van het programma dat niet versneld kan worden met meer CPU cores
- $N$: aantal CPU cores
$$
snelheidswinst = \frac{1}{S-\frac{1-S}{N}}
$$
