# databases-H06
2025-01-19 - 20:58
Tags: [[Databases-1]]
***
## H06 Normalisatie

### 6.1 Inleiding
Normalisatie is een proces om de structuur van tabellen te evalueren en te corrigeren. Het doel is het elimineren van gegevensredundantie en anomalieën, terwijl de databank schaalbaar, onderhoudbaar en consistent blijft.

- Normalisatie werkt via normaalvormen: **0NF**, **1NF**, **2NF**, **3NF**, en hogere vormen zoals **BCNF**, **4NF**, en **5NF**.
- **Praktijk**: Normalisatie tot 3NF is meestal voldoende. Hogere normaalvormen kunnen leiden tot complexe JOIN-operaties.

---

### 6.2 Nut van Normalisatie

1. **Verminderen van gegevensredundantie**: Vermijdt herhaling van gegevens in meerdere tabellen.
2. **Voorkomen van anomalieën**:
    - **Invoeganomalie**: Moeite met het toevoegen van nieuwe gegevens.
    - **Verwijderanomalie**: Onbedoeld verwijderen van relevante gegevens.
    - **Modificatie-anomalie**: Fouten door handmatige updates op meerdere plaatsen.
3. **Verhogen van gegevensconsistentie**: Minimaliseert het risico op inconsistente gegevens.
4. **Betere gegevensintegriteit**: Ondersteunt validiteit en betrouwbaarheid van gegevens.
5. **Eenvoudiger onderhoud**: Makkelijker om wijzigingen door te voeren zonder fouten.

---

### 6.3 Functionele Afhankelijkheid
- **Definitie**: Attribuut B is afhankelijk van attribuut A als de waarde van A de waarde van B bepaalt (notatie: `A → B`).
- **Partiële afhankelijkheid**: B hangt af van slechts een deel van een samengestelde sleutel.
- **Transitieve afhankelijkheid**: Niet-sleutelattributen zijn indirect afhankelijk van de primaire sleutel via andere niet-sleutelattributen.

---

### 6.4 Normalisatieproces
1. **0NF (nulde normaalvorm)**: Alle gegevens in één tabel, inclusief herhalende groepen.
    - Voorbereiding: Identificeer herhalende gegevens en bepaal functionele afhankelijkheden.
2. **1NF (eerste normaalvorm)**:
    - **Elimineer herhalende groepen**.
    - **Zet samengestelde en meerwaardige attributen om in afzonderlijke relaties.**
3. **2NF (tweede normaalvorm)**:
    - **Voldoet aan 1NF.**
    - **Geen partiële afhankelijkheden**: Niet-sleutelattributen moeten afhankelijk zijn van de volledige primaire sleutel.
4. **3NF (derde normaalvorm)**:
    - **Voldoet aan 2NF.**
    - **Geen transitieve afhankelijkheden**: Niet-sleutelattributen mogen niet afhankelijk zijn van andere niet-sleutelattributen.

---

### 6.5 Het relationele model
Na normalisatie tot 3NF worden tabellen gestructureerd en benoemd, met duidelijk gedefinieerde integriteitsregels:

- **Klant**: (KlantNummer, KlantNaam, KlantAdres, Postcode)
- **Artikel**: (Artikelcode, Omschrijving, Eenheidsprijs, BTWCode)
- **Factuur**: (FactuurNummer, FactuurDatum, KlantNummer)
- **Plaats**: (Postcode, Woonplaats)
- **BTW**: (BTWCode, BTWPercentage)

---

### 6.6 Integratie
Gegevens uit verschillende bronnen worden geïntegreerd in een genormaliseerd model, wat verdere consistentie en onderhoudbaarheid garandeert.