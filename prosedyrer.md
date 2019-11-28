# Prosedyrer

## Ny database i eFORSK (prod)

* Det må først foreligge en avtale om bruk av eFORSK. Informasjon fra denne brukes for å sette opp databasen. http://virksomhetsportal.helsemn.no/omrader/hemit/enhet/Systemutvikling/Oppdrag/Forms/AllItems.aspx?RootFolder=%2fomrader%2fhemit%2fenhet%2fSystemutvikling%2fOppdrag%2feFORSK%5fBruk%20av%20somatropin%5fforskningsstudie%5fHMR&FolderCTID=&View=%7b7BD7272F%2dCD5E%2d4156%2d87CF%2d9F1921AF505A%7d
* Brukere som skal ha tilgang må søke her: https://falk.eforsk.nhn.no/u/apply?app=eFORSK
* Aktiver database på https://eforsk.nhn.no/ 
* Hvis ePROM
  * Opprett bestillersystem for testmodus på http://pasientrapportering.qa.nhn.no/   og hent inn API nøkkel til eFORSK
  * Opprett bestillersystem for ikke-testmodus på http://pasientrapportering.nhn.no/  og hent inn API nøkkel til eFORSK
* Gi tilgang til brukere i FALK. Superbruker bør få tilgangstildererollen for databasen. https://falk.eforsk.nhn.no/u/a/orders/4
* Hvis gjenstående ledige databaser har nådd 3 eller mindre, bestill opp flere fra NHN

## Produksjonssetting av ny versjon

* Hold endringslogg i brukermanual oppdatert på endringer og datoer fortløpende
* Logg på eFORSK prod i administrasjon og opprett nye varsler for ny versjon (se tidligere varsler for eksempel her)
* (Send ut e-post til alle aktive brukere siste måned med varsler om ny versjon?)
* Etter produksjonssetting, sjekk status på integrasjoner i eFORSK administrasjon
* Følg opp feil og advarsler i splunk
