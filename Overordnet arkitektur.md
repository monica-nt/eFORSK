# Overordnet arkitektur

Basert på MRS, tre lags applikasjon.

## Klient-app

Implementert med .Net Web Api 

Front-end bygges med Angular, støttet av komponeneter fra enten Angular Material eller ngBootstrap. 
Etter en studie av disse to bibliotekene ser det ut som man får mye mer ut av boksen fra bootstrap, og man kan spare veldig mye tid og få et visuelt mye bedre resultat ved å gå for den. Det er også et mye større miljø rundt bootstrap. Andre prosjekter i Hemit bruker bootstrap.

## Service-app

Implementert med .Net, eksponerer WCF servicer

## Database

MsSql som database
ORM: Dapper og/eller EF
