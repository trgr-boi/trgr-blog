# databases-H04
2025-01-19 - 20:57
Tags: [[Databases-1]]
***
## H04 Enhanced Entity-Relationship Diagram (EERD)

### 4.1 Inleiding

Het Enhanced Entity-Relationship Model (EERM) is een uitbreiding van het traditionele ER-model om complexere datastructuren te modelleren. Het voegt het concept van _specialisatie/generalisatie_ toe, terwijl de basiselementen zoals entiteittypen, attributen en relaties behouden blijven.

---

### 4.2 Specialisatie en Generalisatie

- **Specialisatie**: Een _top-down_ proces waarbij een supertype wordt opgesplitst in specifieke subtypen op basis van unieke kenmerken. Voorbeeld: Een ARTIEST kan gespecialiseerd worden in ZANGER of ACTEUR.
    
    - Specifieke attributen of relaties worden toegewezen aan subtypen.
    - **Constraints**:
        - **Disjoint (OR)**: Een entiteit kan maar tot één subtype behoren.
        - **Overlapping (AND)**: Een entiteit kan tot meerdere subtypen behoren.
        - **Participatie**:
            - **Mandatory**: Elke entiteit van het supertype behoort tot minstens één subtype.
            - **Optional**: Een entiteit van het supertype hoeft niet tot een subtype te behoren.
- **Generalisatie**: Een _bottom-up_ proces waarbij gemeenschappelijke kenmerken van subtypen worden gecombineerd in een supertype. Voorbeeld: Subtypen PIANO, VIOOL en GITAAR kunnen gegeneraliseerd worden in STRIJKINSTRUMENT.
    
- Specialisatie kan hiërarchisch zijn, waarbij subtypen zelf weer supertypen kunnen zijn.
    

---

### 4.3 Beperkingen van het ER-model

- Het ER-model biedt slechts een momentopname van gegevensvereisten en kan geen temporele of complexe bedrijfsregels afhandelen. Voorbeelden:
    - Tijdelijke restricties zoals deadlines of verbod op terugkeer naar eerdere rollen.
    - Consistentie over meerdere relatietypes.
    - Domeinrestricties (bijv. positieve waarden voor gewerkte uren).
    - Definities van functies (zoals salarisberekeningen) worden niet ondersteund.
---

### 4.3.1 Fan Trap
Een _fan trap_ ontstaat wanneer één entiteitstype meerdere 1:N-relaties heeft, wat leidt tot dubbelzinnigheid in associaties. Voorbeeld:

- Het is onduidelijk aan welk PROJECT een WERKNEMER werkt als de juiste associaties ontbreken. Oplossing: Voeg duidelijke relaties toe.

### 4.3.2 Chasm Trap
Een _chasm trap_ ontstaat wanneer een relatie met minimumcardinaliteit 0 het onmogelijk maakt om een associatie te maken. Voorbeeld:

- Een PROJECT kan niet toegewezen worden aan een DEPARTEMENT als er geen WERKNEMER is die het superviseert. Oplossing: Voeg een directe relatie toe tussen DEPARTEMENT en PROJECT.