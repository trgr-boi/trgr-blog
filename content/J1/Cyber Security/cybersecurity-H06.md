# cybersecurity-H06
2025-01-22 - 22:10
Tags: [[Cybersecurity]]
***

> [!important] AI gegenereerd!
> Check of dit volledig klopt.

## 6.1 Onvoorziene problemen

- Disaster Recovery Planning is essentieel om een organisatie draaiende te houden tijdens rampen
- Rampen omvatten zowel natuurlijke als door de mens veroorzaakte gebeurtenissen
- Natuurrampen: geologisch (aardbevingen), meteorologisch (bliksem, hagel, tornado’s), gezondheidsgerelateerd (pandemieën)
- Menselijke rampen: werkplekgebeurtenissen (stakingen), sociaal-politieke gebeurtenissen (vandalisme, terrorisme), onderbrekingen van nutsvoorzieningen

## 6.2 Hoge beschikbaarheid (High Availability)

- Het Five Nines (5x9) principe: 99,999% uptime (maximaal 5m 15,36s downtime per jaar)
- Kritieke sectoren die hoge beschikbaarheid vereisen:
    - Financiële sector
    - Gezondheidszorg
    - Industrie
    - Vervoer
    - Openbare veiligheid
    - Nutsvoorzieningen
    - Telecommunicatie
    - Detailhandel
- Bedreigingen voor beschikbaarheid omvatten systeemstoringen, ongevallen, opzettelijke aanvallen en natuurrampen
- Hoge beschikbaarheid wordt bereikt door:
    - Maximale uptime
    - Redundantie (vermijden van enkele punten van falen)
    - Robuuste systemen
    - Monitoring
    - Back-ups
- N+1 redundantie zorgt ervoor dat systemen beschikbaar blijven als één component uitvalt

## 6.3 Back-ups

- 3-2-1 regel:
    - Ten minste 3 kopieën
    - Op ten minste 2 verschillende media
    - Ten minste 1 kopie op een andere locatie
- Varianten zijn 3-2-1-1-0 en 4-3-2
- Opties voor opslagmedia:
    - HDD’s (gemiddelde levensduur 6-7 jaar)
    - SSD’s (vereist jaarlijkse verbinding om bit rot te voorkomen)
    - NAS
    - Cloudopslag
    - Tapes, USB, optische media
- Belangrijke overwegingen:
    - Test back-ups regelmatig
    - Automatiseer back-upprocessen
    - Gebruik incrementele back-ups om ruimte en tijd te besparen
    - Vergeet niet alle apparaten en gegevensbronnen te back-uppen
    - Synchronisatie is geen back-up
    - Houd rekening met privacy- en kostenimplicaties voor cloudopslag