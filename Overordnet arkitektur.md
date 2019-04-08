# Overordnet arkitektur

Basert på MRS, tre lags applikasjon.

## Sikkerhetsmodell

MRS sin sikkerhetsmodell beholdes, WS federation

## Klientlaget

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

## Servicelaget

### Teknologi

* .Net Framework
* WCF
* ORM: Dapper for spørringer, EF for migrations

### Ansvarsområder:

**Wcf Servicer**: 
Forretningslogikk.
Autorisasjon.
Validering (skal kaste exception ved feil)

**DbManagers**: 
Mest mulig dum.
Databaseoperasjoner, mapping til og fra databaseentiteter, Caching, Logging

**IntegrationManagers**:
Kommuniserer med eksterne API

## Databaselaget

### Teknologi
* MsSQL

### Ansvarsområder:
Database
