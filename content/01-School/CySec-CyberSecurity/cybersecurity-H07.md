# cybersecurity-H07
2025-01-22 - 22:10
Tags: [[Cybersecurity]]
***
## 7.1 Waarom certificaten nodig?

- Problemen met symmetrische encryptie: fysieke sleuteloverdracht is vereist
- Problemen met asymmetrische encryptie: de juiste openbare sleutel moet worden verkregen
- Risico op Man-in-the-Middle (MitM) aanvallen waarbij hackers openbare sleutels kunnen onderscheppen en vervangen
- Noodzaak om te garanderen dat openbare sleutels behoren tot specifieke personen/organisaties

## 7.2 De oplossing: Certificaten

- Certificaten fungeren als digitale paspoorten
- Iedereen vertrouwt een derde partij (Certificate Authority - CA)
- CAs verstrekken "identiteitskaarten" of certificaten
- Zonder geldig certificaat = niet betrouwbaar
- Voorbeelden uit de echte wereld: Overheids-ID-kaarten, studentenkaarten, bankkaarten

## 7.3 Certificate Authorities

- Proces van certificaten aanvragen:
    1. Gebruiker genereert een Certificate Signing Request (CSR)
    2. CA verifieert de identiteit van de gebruiker
    3. CA maakt en ondertekent het certificaat met de privésleutel
- Certificaten volgen de X.509-standaard
- CA-certificaten worden vooraf geïnstalleerd met programma's (OS, browsers, enz.)
- Zelfondertekende certificaten zijn mogelijk, maar worden standaard niet vertrouwd

## 7.4 Toepassing: HTTPS

- Oud HTTP: transmissie in platte tekst
- HTTPS: gebruikt certificaten voor:
    - Zorgen voor de juiste communicatiepartner (geen MitM)
    - Versleuteling via TLS/SSL-protocol
- Browsers geven de HTTPS-status aan
- HTTPS biedt geen bescherming tegen kwaadaardige websites

## 7.5 Toepassing: VPN

- Creëert veilige communicatie over openbare netwerken
- Gebruik:
    - Verbinden van verschillende geografische locaties
    - Thuiswerken (work@home)
    - Privacy en het omzeilen van geografische beperkingen
- Gebruikt TLS/SSL-certificaten voor beveiliging
- Privacyoverwegingen:
    - VPN-aanbieders kunnen het verkeer zien
    - Het is belangrijk om loggingbeleid te overwegen
    - Snelheidsbeperkingen kunnen van toepassing zijn
    - Geen volledige anonimiteitoplossing

Het hoofdstuk benadrukt het belang van certificaten in moderne digitale beveiliging, vooral voor het verifiëren van identiteiten en het mogelijk maken van veilige communicatie via protocollen zoals HTTPS en VPN-diensten.