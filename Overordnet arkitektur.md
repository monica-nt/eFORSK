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

Front-end støttes med komponeneter fra enten Angular Material eller ngBootstrap. 
Etter en studie av disse to bibliotekene ser det ut som man får mye mer ut av boksen fra bootstrap, og man kan spare veldig mye tid og få et visuelt mye bedre resultat ved å gå for den. Det er også et mye større miljø rundt bootstrap. Andre prosjekter i Hemit bruker bootstrap.

## Service-app

Implementeres med .Net, eksponerer WCF servicer
Har kobling mot databasene

Ansvarsområder:
Wcf Servicer: Autorisasjon, Validering, Feilhåndtering?
Db Managere: Databaseoperasjoner, mapping til og fra databaseentiteter, Caching, Logging

## Database

Separate databaser per register
MsSql som database
ORM: Dapper for spørringer, EF for migrations
