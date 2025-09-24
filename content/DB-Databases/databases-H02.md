# databases-H02
2025-01-19 - 20:55
Tags: [[Databases-1]] 
***
### fases in databank ontwerp
- 4 fases
	- fase 1 = verzamelen en analyseren van de funtionele/inhoudelijke vereisten
	- fase 2 = coneptueel ontwerp
	- logisch ontwerp
	- fysiek ontwerp
### EntityRelationshipDiagram (ERD)
- éénvan de populairste voorstellingswijzen voor het conceptueel gegevensmodel
- Een ERD de volgende bouwstenen:
	- Entiteittypes
	- Attribuuttypes
	- Relatietypes
### ModelEntiteittype
- Een entiteittype
	- bestaat in de reële wereld
	- kan zowel abstract (een tentoonstelling, firma, cursus, job, ...) als fysiek (schilderij, persoon, auto, huis, ...) zijn
	- ondubbelzinnig gedefinieerd voor een bepaalde groep gebruikers
	- karakteriseert een collectie van entiteiten
	- heeft een naam en inhoud en is identificeerbaar
- Een entiteit is een instantie van een entiteittype
- In het conceptueel model nemen we entiteittypes op (geen individuele entiteiten)
versil entiteittype en entiteit:
- *boek: rich dad poor dad*
- *boek: why we sleep*
	- het entiteittype is **Boek**
	- de entiteit is welk boek het is
		- vb van bieb: meerdere exemplaren gaan als de zelfde entiteit gezien worden
			- `entiteittype boek: title, aantal ex., ...`
		- vb van 2de hand boeken: meerdere exemplaren gaan als een andere entiteit gezien worden
			- `entiteittype boek: title, eigenaar, prijs, ...`
	- 