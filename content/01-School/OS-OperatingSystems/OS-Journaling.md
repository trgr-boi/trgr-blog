---
title: OS-Journaling
aliases:
  - Journaling
tags:
  - school
  - OS
reference: "[[OS-H04-FileSystems]]"
related notes:
---

## Overzicht

> [!question] Wat is een Journal?
> Een beschrijving van wat er aan het gebeuren was/is gebeurt. Als iets crashed of fout loopt kan dit als referentie dienen.

- Schrijfbewerking = meerdere stappen
- Onderbreking: ongeldige bestandssysteemtoestand

**Werking:**
1. Bewerking eerst in logboek geschreven
 2. Bewerking uitgevoerd
 3. Bewerking gemarkeerd als voltooid in logboek
- **Detectie crash:** onvoltooide bewerking in logboek31.
- **Herstel:** onvoltooide bewerking voltooien o.b.v. logboek31.

