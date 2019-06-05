# Driftsmiljø

## Miljøer

### Lokal pc

* Autentisering: Falk DEMO
* ePROM testmodus: ePROM lokal
* ePROM prodmodus: ePROM DEV
* P-reg testmodus: p-reg test
* P-reg prodmodus: p-reg test

### Dev

* Autentisering: Falk DEMO
* ePROM testmodus: ePROM DEV
* ePROM prodmodus: ePROM DEV
* P-reg testmodus: p-reg test
* P-reg prodmodus: p-reg test
* Octopus: Hemit

### Demo

* Autentisering: Gammel STS
* ePROM testmodus: ePROM DEV
* ePROM prodmodus: ePROM DEV
* P-reg testmodus: p-reg test
* P-reg prodmodus: p-reg test
* Octopus: Hemit

### QA 

* Autentisering: Falk QA
* ePROM testmodus: ePROM QA
* ePROM prodmodus: ePROM QA
* P-reg testmodus: p-reg test
* P-reg prodmodus: p-reg test
* Octopus: NHN

### Prod

* Autentisering: eFORSK-Falk
* ePROM testmodus: ePROM QA
* ePROM prodmodus: ePROM **PROD**
* P-reg testmodus: p-reg test
* P-reg prodmodus: p-reg **PROD**
* Octopus: NHN

## NHN (QA og prod)

Satt opp kjøring av WithdrawnConsentTool nattlig kl 01:30

Recycle er satt til å skje nattlig kl 04:55

Splunk søk (etter feilmeldinger): index=efo_prod Type=Error host="ptrd-efo-app01.prod.drift.nhn.no" 
