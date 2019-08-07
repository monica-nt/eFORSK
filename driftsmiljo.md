# Driftsmiljø

## Miljøer

### Lokal pc

* Autentisering: Falk Demo
* ePROM testmodus: ePROM lokal
* ePROM prodmodus: ePROM DEV
* P-reg testmodus: p-reg test
* P-reg prodmodus: p-reg test

### Dev

* Autentisering: Falk Demo
* ePROM testmodus: ePROM Dev
* ePROM prodmodus: ePROM Dev
* P-reg testmodus: p-reg test
* P-reg prodmodus: p-reg test
* Octopus: Hemit

### Demo

* Autentisering: Falk Demo
* ePROM testmodus: ePROM Demo
* ePROM prodmodus: ePROM Demo
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

## Produksjonsetting

Ved deploy av ny versjon til prod skal det ett døgn i forveien opprettes varsel fra administrasjonen i eFORSK som sier når ny versjon skal deployes.
Varselet skal vises frem til 10 minutter før deploy. Det opprettes et varsel som ikke kan lukkes fra 10 minutter før deploy som sier at applikasjonen nå oppdateres. Dette varselet fjernes så når ny versjon er verifisert OK.
