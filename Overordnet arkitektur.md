# Overordnet arkitektur

Basert på MRS, tre lags applikasjon.

## Sikkerhetsmodell

MRS sin sikkerhetsmodell beholdes, WS federation

## Klient-app

* Implementeres med .Net
* Web Api
* Angular
  * Reactive forms
  * Redux? https://redux.js.org/basics 
  * ngBootstrap

## Service-app

Implementeres med .Net, eksponerer WCF servicer
Har kobling mot databasene

Ansvarsområder:


**Wcf Servicer**: 
Forretningslogikk.
Autorisasjon, Validering, Feilhåndtering?  


**Db Managere**: 
Mest mulig dum.
Databaseoperasjoner, mapping til og fra databaseentiteter, Caching, Logging

## Database

Separate databaser per register
MsSql som database
ORM: Dapper for spørringer, EF for migrations
