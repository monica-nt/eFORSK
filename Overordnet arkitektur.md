# Overordnet arkitektur

Basert på MRS, tre lags applikasjon.

## Klient-app

* Implementeres med .Net
* Web Api
* Angular

Front-end støttes med komponeneter fra enten Angular Material eller ngBootstrap. 
Etter en studie av disse to bibliotekene ser det ut som man får mye mer ut av boksen fra bootstrap, og man kan spare veldig mye tid og få et visuelt mye bedre resultat ved å gå for den. Det er også et mye større miljø rundt bootstrap. Andre prosjekter i Hemit bruker bootstrap.

## Service-app

Implementeres med .Net, eksponerer WCF servicer
Har kobling mot databasene

## Database

MsSql som database
ORM: Dapper og/eller EF
