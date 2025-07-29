# cybersecurity-H01
2025-01-22 - 22:03
Tags: [[Cybersecurity]]
***
## 1.1 Data, het virtuele goud

- Data wordt tegenwoordig beschouwd als het **virtuele goud** en is net zo waardevol als goud ooit was. Het wordt gestolen, misbruikt en gehackt door zowel bedrijven als individuen.

### Inleiding

- **Goud**: In het verleden was goud het doelwit van rovers en overvallen, net als hoe **data** nu het doelwit is van cybercriminelen.
    - **Goudtransporten** werden aangevallen.
    - **Mensen** werden overvallen voor hun bezittingen.
- **Data**: Tegenwoordig draait het internet om data, die steeds vaker het doelwit is van aanvallen zoals databreaches en phishing.
    - **Bedrijven** worden gehackt.
    - **Netwerken** worden afgeluisterd en besmet met malware.
    - **Mensen** worden slachtoffer van phishing of verliezen persoonlijke gegevens via gestolen laptops.

### Jouw Data

- **Persoonlijke data** wordt door bedrijven opgeslagen, zoals:
    - **Private gegevens** (chat, e-mail, foto's, ...).
    - **Financiën** (bankrekeningen, overschrijvingen, ...).
    - **Medisch** (aandoeningen, ziektegeschiedenis, medicatie, ...).
    - **School** (punten, verslagen, feedback, ...).
    - **Werk** (loon, HR, werkbestanden, ...).
    - **Overheid** (rechtszaken, boetes, eigendom, ...).

### Bedrijven en Data

- Bedrijven moeten zorgen voor de **beveiliging** van deze gegevens:
    - Bescherming tegen misbruik.
    - Bescherming tegen ongeoorloofde toegang.
- Gevoelige gegevens kunnen ernstige gevolgen hebben als ze verloren gaan of gehackt worden.

### Meer dan Persoonlijke Data

- **Industriële data** is ook waardevol voor hackers, vaak voor **losgeld** of **spionage**:
    - Industriële netwerken zoals **SCADA** zijn doelwit voor aanvallen die grote gevolgen kunnen hebben voor sectoren zoals energieproductie en transportsystemen.
    - Cyberaanvallen op deze systemen kunnen ernstige verstoringen veroorzaken.

### Omgaan met Data

- **Verantwoordelijkheid van bedrijven**: Bedrijven hebben de plicht om gegevens te beschermen en de risico's van dataverlies of -misbruik te beperken.
- Er is **groei in gegevensverzameling en -analyse**, wat nieuwe **risico's** met zich meebrengt.
- Er zijn **voorzorgsmaatregelen** nodig om gevoelige gegevens te beschermen tegen criminelen en schade te voorkomen.

## 1.2 Staten van data

- Alles in de cyberwereld draait rond data. Cybersecurity specialisten focussen zich op het beveiligen van die data.
- Data heeft 3 mogelijke staten:
    - Data in **rust**/opslag
    - Data tijdens het **verzenden**
    - Data tijdens het **verwerken**

---

### Data in rust

- Data opgeslagen op **opslagapparaten** die niet wordt gebruikt door personen of processen.
- Opslagapparaten kunnen **lokaal** (harde schijf, USB-stick, ...) of gecentraliseerd **op afstand** aangesloten zijn (Dropbox, Google drive, NAS, ...).
- Data kan zo **verloren** of **gestolen** worden:
    - Harde schijf kapot
    - Laptop vergeten op trein
    - Smartphone gestolen

---

### Data tijdens verzenden

- Verschillende manieren:
    - **Sneaker net**: gebruikt opslagapparaten om data tussen computers over te zetten (USB-stick, draagbare harde schijf, ...).
    - **Bedraad** netwerk: gebruikt koper- of fiberkabels.
    - **Draadloos** netwerk: gebruikt elektromagnetische golven (kan door iedereen in de buurt "gehoord" worden).
- Een van de grootste uitdagingen voor cybersecurity personeel om te beveiligen.
- Enkele uitdagingen: cybercriminelen kunnen data tijdens het verzenden ...
    - afluisteren, kopiëren of stelen (vertrouwelijkheid),
    - aanpassen (integriteit),
    - verhinderen of verstoren (beschikbaarheid).

---

### Data tijdens het verwerken

- Dit omvat data tijdens de **invoer**, **aanpassing**, **berekening** of **uitvoer**.
- Organisaties gebruiken verschillende methodes om data te verzamelen:
    - Manuele invoer, het uploaden van bestanden, dataverzameling van sensoren, ... .
    - Elk van deze input-methode is een mogelijke bedreiging voor integriteit.
- Data kan aangepast worden door manuele verandering door gebruikers, programma's die de data wijzigen, defecte apparaten, ... .
    - Voorbeelden van data-aanpassingen: encoderen/decoderen, compressie/decompressie, encryptie/decryptie, ... .
- Data die zodanig wordt aangepast dat het fouten bevat of onbruikbaar wordt, noemt men **corrupte** data.


---

## 1.3 The CIA Triangle

- Not _that_ CIA...
- 3 principles:
    - Confidentiality
    - Integrity
    - Availability

---

#### Confidentiality

- **Question:** Who can see this?
- **Examples:** Chat messages, company secrets, medical information.

#### Integrity

- **Question:** Is this information accurate? Is it from the right source?
- **Examples:** Financial transactions, contracts.

#### Availability

- **Question:** Can I access this when I need it?
- **Examples:** Emergency services, online exams, email servers, internet access.

---

### Confidentiality

- Prevents unauthorized disclosure of information.
- Organizations must train staff to protect sensitive data.
- Can be achieved through **encryption**, **authentication**, and **access control**.
    - This is covered in **H4**.

---

### Integrity

- Integrity is the accuracy, consistency, and **reliability** of data.
- The need for integrity depends on the data's nature:
    - E.g., Facebook does not verify user post data.
    - E.g., Bank transactions must be 100% accurate.

- Loss of integrity can cause massive damage and render data unreliable.
- Integrity checks often use a **hash function**.
- Covered in **H5**.

---

### Availability

- Information systems must be accessible at all times.
- Attacks and failures can compromise system access.


- Measures for availability:
    - Redundancy, backups, resistance, maintenance, up-to-date software, disaster recovery plans, and more.
- Covered in **H6**.

---

## 1.5: De Cybersecurity Kubus (Samenvatting)

De **Cybersecurity Kubus** helpt bij het beschermen van data in verschillende staten (rust, verzending, verwerking) volgens de **CIA-driehoek** (Confidentiality, Integrity, Availability). Dit wordt gevisualiseerd als een kubus met drie dimensies:

1. **Beveiligingsprincipes** (CIA-driehoek)
2. **Staten van data** (rust, verzending, verwerking)
3. **Beveiligingsmaatregelen** (technologie, beleid, personeel)

Het ontwerp van een beveiligingsplan houdt rekening met al deze aspecten om te zorgen voor een robuuste beveiliging van gegevens.

---

## Extra: Wachtwoorden

- **Een goed [[wachtwoord]]** moet lang, complex en uniek zijn. Veelvoorkomende wachtwoorden zoals "Musti2012" of "SchoonmeersenHOGENT" zijn gemakkelijk te raden.
- Gebruik **twee-factor authenticatie (2FA)** om je accounts extra te beveiligen.
- **Password managers** helpen bij het beheren van wachtwoorden door ze versleuteld op te slaan en automatisch in te vullen, maar wees voorzichtig met je **master password**.

**Belangrijke tips:**

- Gebruik **verschillende wachtwoorden** voor elke website om te voorkomen dat, bij een datalek, meerdere accounts in gevaar komen.
- Vermijd het gebruik van voor de hand liggende patronen, zoals geboortedata of simpele woorden.
- Gebruik **passphrases** (lange, willekeurige zinnen) in plaats van traditionele wachtwoorden.

**Wachtwoordbeleid**:

- Bedrijven moeten geen te frequente wachtwoordwijzigingen afdwingen, aangezien dit vaak leidt tot zwakkere wachtwoorden. Het is beter om gebruikers **sterkere wachtwoorden** en 2FA aan te moedigen.

**Tips voor programmeurs**:

- Voeg een **time-delay** toe bij inlogpogingen om brute-force aanvallen tegen te gaan.
- **Systeembeheerders** moeten programma's gebruiken zoals **fail2ban** om herhaalde inlogpogingen na een bepaald aantal mislukkingen te blokkeren.