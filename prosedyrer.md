# Prosedyrer

## Ny database i eFORSK (prod)

Utføres av fagansvarlige.

#### Forberedelser

* Det må først foreligge en avtale om bruk av eFORSK. Informasjon fra denne brukes for å sette opp databasen. http://virksomhetsportal.helsemn.no/omrader/hemit/enhet/Systemutvikling/Oppdrag/Forms/AllItems.aspx?RootFolder=%2fomrader%2fhemit%2fenhet%2fSystemutvikling%2fOppdrag%2feFORSK%5fBruk%20av%20somatropin%5fforskningsstudie%5fHMR&FolderCTID=&View=%7b7BD7272F%2dCD5E%2d4156%2d87CF%2d9F1921AF505A%7d
* Brukere som skal ha tilgang må inn i Falk, send e-post til disse: "Fyll ut skjema på https://falk.eforsk.nhn.no/u/apply?app=eFORSK for å klargjøre din bruker i eFORSK. Lokasjon trengs ikke besvares, denne er ikke klar ennå."
* Hvis ePROM:
  * Bestill bestillersystem i ePROM til systemutvikling@hemit.no: "Bestiller bestillersystem i QA og PROD med navn [sett inn prosjektnavnet], send API-nøkler i retur". Benytt API-nøkkel for QA til testmodus, og API-nøkkel for PROD til ikke-testmodus. Etter API-nøkler er lagt inn i eFORSK, klikk "Test ePROM tilkobling" knappen.
  
#### Når dette er gjort, gå videre med selve opprettelsen i eFORSK
  
* Aktiver database på https://eforsk.nhn.no/ 
* Gi tilgang til brukere i FALK. Superbruker bør få tilgangstildererollen for databasen. https://falk.eforsk.nhn.no/u/a/orders/4
* Hvis gjenstående ledige databaser har nådd 3 eller mindre, bestill opp flere fra NHN kundesenter@nhn.no: "Bestiller herved opp 10 nye databaser for eFORSK PROD med tilhørende oppslag i keys-fila."

## Produksjonssetting av ny versjon

Utføres av utviklingsteam (?)

* Hold endringslogg i brukermanual oppdatert på endringer og datoer fortløpende
* Logg på eFORSK prod i administrasjon og opprett nye varsler for ny versjon (se tidligere varsler for eksempel her)
* (Send ut e-post til alle aktive brukere siste måned med varsler om ny versjon?)
* Etter produksjonssetting, sjekk status på integrasjoner i eFORSK administrasjon
* Følg opp feil og advarsler i splunk
* Oppdater brukermanual
