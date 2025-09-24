# databases-H01
2025-01-19 - 20:54
Tags: [[Databases-1]]
***
vershillende applicaties
	- Traditionele bedrijfsapplicaties (loonberekening, tijdsregistratie,...)
	- Biometrische applicaties (vingerafdrukken, resultaten scans)
	- Sensor-applicaties (in kerncentrales, ...)
	- GIS applicaties (geografische informatiesystemen (Google Maps, ...)
	- Big Data applicaties (Walmart, ...)
	- ‘Internet of Things (IoT)’ applicaties(Telematics, ...)
	-> opslagenterugophalenvan informatie(data)
- Nadelen gegevensmanagement via bestanden
	- Nadeel 1: Verspreiding en isolatie van gegevens
	- Nadeel 2: Gegevens**redundantie** (dubbele/niet nodige info)
	- Nadeel 3: Data afhankelijkheid
### Basisdefinities:
- databanken
	- Een **gedeelde** verzameling van **logisch met elkaar verbonden** gegevens en hun **beschrijving**, ontworpen om aan de **informatienoden** van een organisatie te voldoen.(T. Connolly).
		- digitaal opgeslagen
		- specifiek bedrijfsproces
		- specifieke groep (gebruikers & applicaties)
- DBMS
	- Een Database Management System (DBMS):
		- **verzameling** computerprogramma's
		- nodig om databanken te
			- definiëren
			- creëren
			- wijzigen
			- beheren
			- gebruiken
	**Databanksysteem: databank + DBMS**
- gebruikers
	- De **data-administrators** (DA) zijn in een onderneming centraal verantwoordelijk zijn voor de data
	- **Dbontwerper** vertaalt conceptueel model naar logisch en intern mode
	- DBA (**databankbeheerder** of database administrator) implementeert en monitort DB
	- Applicatieontwikkelaar schrijft databankprogramma’s/databankapplicaties
	- Eindgebruikers gebruikt databankapplicaties en voert op die manier databankacties uit
		- Sommige eindgebruikers zijn zich niet bewust van de databank
		- Sommige geavanceerde eindgebruikers kennen de structuur van de databank
### Elementen van een databank
- datamodels versus instances
	- databankmidel = databankscheme
		- bevat 
			- beschrijving van de databankstructuur
			- specificaties v/d elementen, hun eigenschappen, relaties,...
		- opgesteld tijdens databankontwerp
		- Wijzigt niet om de haverklap
		- Opgeslagen in de cataloog
	- toestand van een databank
		- Op dat ogenblik aanwezige data
		- Wijzigt voortdurend
- cataloog
- datamodel
	- Conceptueel datamodel :
		- perfecte weergave van de gegevensvereisten van de ‘business’
		- algemene beschrijving gegevenselementen, kenmerken en relaties
			- gebruikt door 'IT' & 'buisiness'
				- *'IT' gebruikt andere taal dan 'business'*
			- weergave hoe de 'business' de gegevens zien
			- voorstelling: (E)ERD diagram
	- Logisch datamodel
		- vertaling conceptueel gegevensmodel naar het type databankmodel
			- Relationeel, hiërarchisch, OO, XML, NoSQL
		- nog altijd verstaanbaar voor niet IT-ers, maar leunt al dichter aan bij hoe de data fysiek zal opgeslagen worden
	- Fysiek datamodel
		- Geeft informatie over fysieke opslag:
			- waar worden welke gegevens opgeslagen
			- Wat is de grootte van de datavelden
			- Indexen die het ophalen versnellen
- 3-lagen architectuur
	- **doel:** data onafhankelijkheid
		- wijzigen in ene laag -> minimale wijzigingen in andere
		- externe laag -> views
		- middelste laag -> conceptuele/logische laag
		- onderste laag -> interne datamodel, hoe data fysisch georganiseerd en opgeslagen wordt