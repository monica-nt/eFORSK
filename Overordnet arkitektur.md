# Overordnet arkitektur

Basert på MRS, tre lags applikasjon.

## Sikkerhetsmodell

MRS sin sikkerhetsmodell beholdes, WS federation

## eFORSK.Client

### Teknologi

* .Net Framework
* Web Api 2
* Angular
  * bootstrap 4
  * ngBootstrap
 
### Ansvarsområde

**API**:
I hovedsak så dum som mulig, kopi av service lagets API.
For hastighet finnes det hjelpemetoder som syr sammmen flere API kall mot service laget.

**App**:
Angular SPA som konsumerer APIet

## eFORSK.Service

### Teknologi

* .Net Framework
* WCF

### Ansvarsområder:

**Wcf Servicer**: 
Forretningslogikk.
Autorisasjon.
Validering (skal kaste exception ved feil)

## eFORSK.Service.Data

### Teknologi
* MsSQL
* Dapper for spørringer
* EF for migrations

### Ansvarsområder:
Database

### DbManagers
Alle klasser med kommunikasjon med database postfixes med \*DbManager.cs. Disse klassene skal være så dumme som mulig. Skal ta seg av mapping melling databaseentiteter til modeller. Tar seg av caching og logging

## eFORSK.Service.Integration

### Ansvarsområder:
Integrasjoner (mot eksterne systemer).

### IntegrationManagers
Alle klasser med kommunikasjon med integrasjoner postfixes med \*IntegrationManager.cs
