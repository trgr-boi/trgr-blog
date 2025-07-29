# cybersecurity-H05
2025-01-22 - 22:09
Tags: [[Cybersecurity]]
***
## 5.1 Digitale Handtekeningen
- Digitale handtekeningen kunnen aan bestanden worden toegevoegd (bijv. PDF) om integriteit te waarborgen
- Verifieert twee aspecten:
  - Bestand is niet gewijzigd na het genereren van de handtekening
  - Bestand is afkomstig van de beweerde persoon
- Gebruikt asymmetrische encryptie met publieke en private sleutels
## 5.2 Hashing Algoritmes
- Gebruikt om data-integriteit te verifiëren door hash-waarde berekening
- Eigenschappen:
  - Input kan elk aantal bits zijn
  - Output heeft altijd hetzelfde aantal bits
  - Eenrichtingsfunctie (onmogelijk om te omkeren)
  - Verschillende inputs geven altijd verschillende outputs
- Types:
  - MD5 (zwak) - 128-bit output
  - SHA familie (SHA-224, SHA-256, SHA-384, SHA-512)
  - SHA-2 en SHA-3 zijn sterke algoritmes die nog steeds gebruikt worden voor cyberbeveiliging
## 5.3 Toepassingen van Hashing
- Foutcontrole in data
- Veilige wachtwoordopslag
- Data-identificatie met hash als vingerafdruk
- Efficiënte opslag in hash tabellen
### Wachtwoordopslag Beveiliging:
- Platte tekst opslag: Gevaarlijk
- Gehashte wachtwoorden: Matig veilig
- Gehashte + gezouten wachtwoorden: Meest veilig
  - Zout voorkomt dat dezelfde wachtwoorden dezelfde hash hebben
  - Maakt rainbow tables onbruikbaar
## 5.4 Hashing Kraken
- Vinden van corresponderende input voor bekende hash-waarde
- Methoden:
  - Brute-force aanvallen
  - Rainbow tables (vooraf berekende hash lijsten)
- Vertragende hashing algoritmes (PBKDF2, bcrypt, Argon2) gebruikt als tegenmaatregel
## 5.5 HMAC
- Combineert hashing met symmetrische encryptie
- Verzekert bericht integriteit en authenticiteit
- Proces:
  1. Verzender berekent hash met gedeelde geheime sleutel
  2. Ontvanger verifieert hash met dezelfde sleutel
- Beschermt tegen Man-in-the-Middle aanvallen
- Alleen verzender en ontvanger kennen de geheime sleutel