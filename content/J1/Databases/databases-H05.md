# databases-H05
2025-01-19 - 20:58
Tags: [[Databases-1]]
***
## H05 Van het conceptueel naar het logisch model
### 5.1 Inleiding
Het omzetten van een ERD naar een relationele databank is een belangrijke stap in het databankontwerpproces. Deze omzetting resulteert in een relationeel model bestaande uit tabellen en kolommen. Hoewel er tools bestaan om dit proces te automatiseren, biedt het manueel toepassen van de regels waardevolle inzichten in databankontwerp. Dit hoofdstuk bespreekt de vertaling van een conceptueel ERD naar een relationeel model.

### 5.2 Bouwstenen voor het relationeel model
#### 5.2.1 Tupel
- Een **tupel** is een geordende lijst van waarden die een object beschrijven, en is steeds uniek.
- Voorbeeld: `(100, ‘Pringles’, ‘Classic Paprika’, ‘175g’, 2.5)`.

#### 5.2.2 Attribuut
- Een **attribuut** is een kenmerk van een tupel en heeft slechts één waarde.
- Voorbeeld: Het attribuut `merk` uit de tupel bevat de waarde `'Pringles'`.

#### 5.2.3 Domein
- Een **domein** is de verzameling van toegelaten waarden voor een attribuut.
- Voorbeeld: Het domein van `prijs` zijn alle toegestane productprijzen.

#### 5.2.4 Relatie
- Een **relatie** is een verzameling van tupels die gelijkaardige objecten beschrijven.
- Voorbeeld: De relatie van producten bevat tupels zoals `{(100, ‘Pringles’, ...), (101, ‘Lays’, ...), ...}`.

#### 5.2.5 Sleutels
- **Kandidaatsleutel**: Een unieke combinatie van attributen die een tupel identificeert.
- **Primaire sleutel**: De gekozen kandidaatsleutel, mag geen NULL-waarden bevatten.
- **Alternatieve sleutel**: Een kandidaatsleutel die niet als primaire sleutel is gekozen, NULL-waarden mogelijk.
- **Vreemde sleutel**: Verwijst naar een andere relatie en legt verbanden tussen tabellen.

### 5.3 Vergelijking met het ER-model
- **Entiteittypes en attribuuttypes**: In het ER-model zijn dit entiteittypes en hun attributen; in het relationele model worden dit tabellen en kolommen.
- **Relatietypes**: In het ER-model worden relaties visueel weergegeven; in het relationele model worden deze geïmplementeerd met primaire en vreemde sleutels.

### 5.4 Regels van een relationeel model
1. Elke tupel in een relatie is uniek.
2. Elk attribuut heeft enkelvoudige en enkelwaardige waarden.
3. Verbanden tussen relaties worden gelegd via vreemde sleutels.

### 5.5 Mapping
Het proces van **mapping** vertaalt een conceptueel model naar een logisch model volgens gestructureerde stappen en regels. Deze regels zorgen ervoor dat het proces nauwkeurig en efficiënt verloopt. De kernstappen zijn:

1. **Entiteittypes omzetten naar relaties**:
    
    - Elk entiteittype wordt een relatie. Bij specialisaties kunnen entiteittypes verdwijnen.
    - Enkelvoudige attributen worden kolommen; samengestelde attributen splitsen in enkelvoudige attributen.
    - Meerwaardige attributen worden in een nieuwe relatie geplaatst.
    - Een van de kandidaatsleutels wordt de primaire sleutel van de relatie.
2. **Relatietypes verwerken**:
    
    - Vreemde sleutels worden bepaald afhankelijk van de relatiecardinaliteit:
        - **1-op-1 relatie**: Vreemde sleutel in een van de relaties, afhankelijk van minimumcardinaliteit.
        - **1-op-N relatie**: Vreemde sleutel aan de N-zijde.
        - **M-op-N relatie**: Nieuwe relatie met beide vreemde sleutels als samengestelde primaire sleutel.
        - **Unaire relatie**: Vreemde sleutel in dezelfde relatie.
    - Integriteitsregels vastleggen: verwijzing, verplichtheid, en uniciteit van de vreemde sleutel.

#### Voorbeeld: WERKNEMER en BEDRIJFSWAGEN
- **1-op-1 relatie** met minimumcardinaliteit = 1:
    
    - **Mogelijkheid 1**: Voeg kolom `nummerplaat` toe aan WERKNEMER. Kan NULL-waarden bevatten (optioneel).
    - **Mogelijkheid 2**: Voeg kolom `wncode` toe aan BEDRIJFSWAGEN. Geen NULL-waarden (verplicht).  
        **Voorkeur**: Mogelijkheid 2, omdat er geen NULL-waarden zijn.
- **1-op-1 relatie** met minimumcardinaliteit = 0:
    
    - Zelfde mogelijkheden als hierboven, maar optionele waarden worden belangrijker.

Door het volgen van deze methodologie kunnen conceptuele modellen systematisch omgezet worden naar relationele databasemodellen.