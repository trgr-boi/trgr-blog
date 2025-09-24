# databases-H07>H12-SQL
2025-01-19 - 20:59
Tags: [[Databases-1]]
***
## Hoofdstuk 7: Werken met één tabel

### SQL-inleiding
- Ontwikkeld in de jaren 1970 door IBM; oorspronkelijk "SEQUEL", later "SQL".
- ANSI-standaard, maar implementaties kunnen verschillen (bv. Oracle, MySQL).

### Basisprincipes
- SQL is *niet* hoofdlettergevoelig.
- SELECT kan hele tabellen, subsets van rijen/kolommen, of gecombineerde subsets ophalen.

### Selectie en projectie
- **Alle gegevens:** `SELECT * FROM tabelnaam`.
- **Subset rijen:** Voeg een `WHERE`-clausule toe voor filteren.
- **Subset kolommen:** Specificeer de kolomnamen in `SELECT`.

### Voorwaarden en operators
- **Vergelijkingen:** Gebruik `=`, `>`, `<`, `<=`, etc.
- **LIKE:** Voor patroonmatching (`%` voor willekeurige tekens).
- **BETWEEN:** Filter binnen een bereik.
- **IN:** Vergelijk een veld met een lijst van waarden.
- **NULL-waarden:** Controleer met `IS NULL` of `IS NOT NULL`.
- **Logische operators:** Combineer voorwaarden met `AND`, `OR`, en `NOT`.

### Formatteren van resultaten
- **Sorteren:** Gebruik `ORDER BY [ASC|DESC]`.
- **Unieke waarden:** Voeg `DISTINCT` toe na `SELECT`.
- **Aliassen:** Gebruik `AS` voor leesbare kolomnamen.
- **Berekende kolommen:** Maak nieuwe waarden met berekeningen of concatenatie.

### Aggregatiefuncties
- **Basisfuncties:** `AVG`, `SUM`, `MIN`, `MAX`, en `COUNT`.
- **Groeperen:** Gebruik `GROUP BY` voor resultaten per groep.
- **Filter op groepen:** Voeg een `HAVING`-clausule toe.

---
## Hoofdstuk 8: Werken met meerdere tabellen

### Joins
- **INNER JOIN:** Combineert rijen op basis van een match in beide tabellen.
- **OUTER JOIN:** Geeft ook niet-overeenkomende rijen uit een van de tabellen.
    - LEFT, RIGHT, en FULL varianten.
- **CROSS JOIN:** Cartesian product, zelden gebruikt.
- **Tabel met zichzelf joinen:** Gebruik aliasnamen om dezelfde tabel te koppelen.

### UNION
- Combineert resultaten van meerdere queries in één tabel.
- Regels:
    - Kolommen moeten gelijk zijn in aantal en datatypes.
    - Resultaat bevat unieke rijen tenzij `UNION ALL` wordt gebruikt.

---

## Hoofdstuk 9: Wijzigen van inhoud in tabellen
### INSERT
- **Één rij:** Voeg data toe met `INSERT INTO`.
- **Meerdere rijen:** Gebruik een `SELECT`-query voor data-invoer.

### UPDATE
- Wijzig bestaande data met `UPDATE ... SET ... WHERE ...`.
- Zonder `WHERE` worden alle rijen aangepast.

### DELETE
- Verwijder rijen met `DELETE FROM ... WHERE ...`.
- Zonder `WHERE` verwijdert alle rijen.

---

## Hoofdstuk 10: Aanmaken, wijzigen en verwijderen van tabellen
### CREATE TABLE
- Definieer kolommen, datatypes, en constraints.
- Constraints zoals `NOT NULL`, `PRIMARY KEY`, en `FOREIGN KEY` zijn mogelijk.

### ALTER TABLE
- **Kolom toevoegen:** Voeg een nieuwe kolom toe met `ADD`.
- **Kolom wijzigen:** Pas datatype of eigenschappen aan met `ALTER`.
- **Kolom verwijderen:** Gebruik `DROP COLUMN`.

### DROP TABLE
- Verwijdert de hele tabel, inclusief data en structuur.

---

## Hoofdstuk 11: Sleutels
- **Primaire sleutel:** Zorgt voor unieke identificatie van rijen.
- **Vreemde sleutel:** Verwijst naar een primaire sleutel in een andere tabel.
- **Entiteitsintegriteit:** Primaire sleutel mag geen `NULL` bevatten.

---

## Hoofdstuk 12: Views
- **Doel:** Complexe queries vereenvoudigen en data beveiligen.
- **Syntax:** `CREATE VIEW viewnaam AS SELECT ...`.
- Views kunnen gebruikt worden alsof het tabellen zijn.