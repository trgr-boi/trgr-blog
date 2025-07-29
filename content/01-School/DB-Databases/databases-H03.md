# databases-H03
2025-01-19 - 20:56
Tags: [[Databases-1]]
***
## H03 Zwakke entiteiten
- Zwakke entiteiten worden gebruikt wanneer een entiteit:
    - Bestaansafhankelijk is van een andere entiteit.
    - Niet uniek kan worden geïdentificeerd met zijn eigen attributen.

### 3.1 Inleiding

- Voorbeeld: een website voor recreatieve lopers.
    - Entiteittype **GEBRUIKER**: identificeerbaar via e-mailadres.
    - Entiteittype **TRAINING**: bestaansafhankelijk van gebruiker en niet uniek identificeerbaar (bijvoorbeeld trainingen met dezelfde data en tijdstippen).

### 3.2 Eigenschappen van zwakke entiteiten

- **Weergave in ERD**: stippellijn.
- **Identificatie**:
    - Gebeurt via een partiële kandidaatsleutel in combinatie met de kandidaatsleutel van de identificerende entiteit.
    - Partiële kandidaatsleutel = attribuuttypes die geen volledige kandidaatsleutel vormen.
- Voorbeeld: **TRAINING** is identificeerbaar door begintijdstip én de relatie met **GEBRUIKER**.

### 3.3 Zwak entiteittype versus bestaansafhankelijk

- Enkel bestaansafhankelijkheid is niet voldoende om een entiteittype als zwak te beschouwen.
    - Voorbeeld: Als **TRAINING** een uniek trainingsnummer krijgt, wordt het geen zwak entiteittype meer, ondanks bestaansafhankelijkheid.

### 3.4 Historiek

- Historiek bewaart gegevens over het verleden.
    - Voorbeeld: Het uitleenproces in een bibliotheek.
        - Entiteittype **EXEMPLAAR**: zwak omdat het bestaansafhankelijk is van **BOEK**.
        - Historiek toevoegen: een apart zwak entiteittype **ONTLENING** met een datumattribuut.

### 3.5 Ternaire relaties met zwakke entiteiten

- Complexe relaties (zoals tussen **PATIËNT**, **DOKTER**, en **MEDICIJN**) worden vaak gemodelleerd met zwakke entiteiten om duidelijkheid te bewaren.
    - Voorbeeld: Een zwakke entiteit kan aangeven welk medicijn door welke dokter aan welke patiënt werd voorgeschreven, inclusief extra relatieattributen zoals voorschrijfdatum.

### 3.6 Bronnen

- Principles of DATABASE MANAGEMENT —— Wilfried Lemahieu / Seppe Vanden Broucke / Bart Baesens
- Principes van databases —— Guy De Tré
- DATABASE SYSTEMS Design, Implementation, and Management —— Carlos Coronel / Steven Morris