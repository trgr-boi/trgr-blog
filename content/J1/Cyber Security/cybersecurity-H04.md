# cybersecurity-H04
2025-01-22 - 22:08
Tags: [[Cybersecurity]]
***

> [!important] AI gegenereerd!
> Check of dit volledig klopt.

## 4.1 Cryptografie
### Kernconcepten
- Cryptografie is een manier om gegevens op te slaan en te verzenden zodat alleen beoogde ontvangers deze kunnen lezen
- Cryptologie is de wetenschap van het maken en breken van geheime codes
- Basis proces bestaat uit:
  - Encryptie: Omzetten van platte tekst naar versleutelde tekst met behulp van een algoritme (cipher) en sleutel
  - Decryptie: Omzetten van versleutelde tekst terug naar platte tekst met behulp van sleutel
### Encryptiemethoden
- Transpositie: Herschikken van tekenvolgorde
- Substitutie: Vervangen van tekens door andere tekens
- One-time pad: Gebruik van willekeurige sleutel om bericht te versleutelen
### Soorten Encryptie
1. Symmetrische Encryptie:
   - Gebruikt dezelfde sleutel voor encryptie en decryptie
   - Snel en efficiënt
   - Voorbeelden: DES, 3DES, IDEA, AES
   - Uitdaging: Veilige sleuteluitwisseling
2. Asymmetrische Encryptie:
   - Gebruikt publieke/private sleutelpaar
   - Langzamer maar veiliger voor sleuteluitwisseling
   - Voorbeelden: RSA, ECC, Diffie-Hellman, ElGamal
   - Geen noodzaak om vooraf geheime sleutel te delen
### Praktische Implementatie
- Gebruikt combinatie van beide types:
  1. Asymmetrische encryptie om veilige tunnel op te zetten
  2. Diffie-Hellman om gedeelde sessiesleutel te genereren
  3. Symmetrische encryptie voor doorlopende communicatie
## 4.2 Cryptanalyse
### Encryptie Breken
- Doelen: Versleutelde tekst omzetten naar platte tekst zonder sleutel
- Belangrijkste aanvalsmethoden:
  - Woordenboekaanvallen: Gebruik van voorgedefinieerde woordenlijsten
  - Brute-force aanvallen: Alle mogelijke sleutels proberen
  - Rainbow tables: Gebruik van vooraf berekende hash tabellen
- Tools zijn onder andere John The Ripper en Hashcat
## 4.3 Gegevensverduistering
### Methoden
1. Gegevensmaskering:
   - Vervangen van gevoelige gegevens door niet-gevoelige equivalenten
   - Behoudt bruikbaarheid van gegevens met bescherming van privacy
   - Gebruikt voor testen en analyse
2. Steganografie:
   - Verbergen van gegevens binnen andere bestanden (afbeeldingen, audio, tekst)
   - Maakt geheim bericht onopvallend
   - Gebruikt dragerbestand, verborgen gegevens en stego-sleutel
3. Gegevensverduistering:
   - Gegevens verwarrend of dubbelzinnig maken
   - Combineert maskerings- en steganografietechnieken
   - Gebruikt in cyberbeveiliging om gevoelige informatie te beschermen