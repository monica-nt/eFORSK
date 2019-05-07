# Kriterier for ny funksjonalitet

- Funksjonen gir nytte for flere potensielle prosjekter/registre/brukere
- Funksjonen tilfører ikke unødvendig kompleksistet til eFORSK

# Backlog (foreløbig ikke avklart/prioritert)

- Administrator skal kunne "stoppe" et register for endringer
- Mulig å låse en skjematype for nye skjema og endring av eksisterende data (kan delvis løses i dag med avpublisering av versjoner)
- Komplett skjemalogg på forskningsobjektnivå (for å kunne oppdage slettede og gjenopprettede randomiseringsskjema)
- ~~Mulighet for å få forhåndsvisning av ePROM digitalt og papirsrkjema (krever ePROM arbeid)~~
- Varsler
	- Mulighet for registeransvarlig å sende ut et varsel for alle brukerene av registeret
	- Mulighet for administrator å sende ut et varsel for alle brukerene av eFORSK instansen (eks. varsel om oppgradering av server)
- Skjemabygger
	- Mulig å legge til standardskjema etter en skjematype er opprettet
	- ~~[Listehåndtering innad i registeret (for gjenbruk av lister på tvers av felter og skjematyper)](Listehåndtering)~~
		- Mulighet for å importere standardlister (volven?)
	- Flere valideringsregler (krever ePROM implementasjon)
	- mulighet for å skjule hjelpetekst for ePROM papirformat
- Importer data
	- Paging på importjobb liste
	- ~~Mulig å opprette skjematype fra importfil~~
- Skjema
	- Mulighet for å konvertere et skjema til en annen versjon
	- Mulighet for å hente ut en tekstlig versjon av spørsmål og svar (tenkt for journalnotat)
	- Ny skjemastatus: Godkjent. Bruker med rolle "Mentor" kan sette ferdigstilte skjema til denne statusen. Mentor kan også returnere et skjema til kontroll.
- Skjemaimport
- ~~Grensesnitt for å lese og søke i logg under administrasjon (for oversikt over all aktivitet)~~
- ~~Liste over brukere som har vært innlogget i et register (under administrasjon)~~
- ~~Legge brukermanual/Om eFORSK i et github repo - og automatisk hente inn dette i appen~~
- ePROM
	- [Støtte for å sette opp automatiske bestillingsjobber](ePROMautomatiskbestilling) (in progress)
	- Mulighet for å eksportere skjemabestillinger/ordrer til excel
	- person initialiserte skjema (in progress)
	- variabler/metadata i informasjon til pasienten
- Mentorrolle
	- Skal kunne "godkjenne" skjema opp til ny skjemastatus "Godkjent", kun tilgjengelig for denne rollen
- Teknologi
	- Skifte ut Typewriter + js-api med Swaggergenerering? Nye modeller vil si mye arbeid, derfor blir denne vanskelig og lite sansynlig gjennomførbar
	- Skifte ut polling fra clienten med SignalR?
	- Fjern WCF
	- .NET Core
	

# Backlog fra planlegging av prosjektet

Minimumsliste må-gjøre MRS for forskning
- ~~App skall (Fungerendes applikasjon som kommuniserer med service-lag. Ingen funksjonalitet)~~
	- ~~Angular front-end~~
	- ~~WCF~~
- ~~Databasestruktur~~
	- ~~Videreutviklet MRS modell~~
	- ~~Dapper~~
- ~~Mulighet for å definere et skjema~~
	- ~~mulighet for å lage nye versjoner av et skjema~~
- ~~Mulighet for å fylle ut skjema~~
- ~~Integrasjon mot ePROM (inkl manuell bestilling,  mottak)~~
- ~~Eksporter data (excel, csv)~~
- ~~Kodebok~~
- ~~Logging~~ og innsyn
- ~~Randomisering (enkel knapp, tildelt gruppe  A,B,C...)~~
- ~~Samtykkehåndtering~~

Bør gjøre
- ~~Optimalt databaselag for løsningen (dapper, dbup, databasetool)~~
- ~~Tilgangsstyring innad register~~
- ~~Koblede skjematyper~~
- ~~Enkel bruksstatistikk~~
- Standard for utvidelser per enkelt register (rapporter)
- ~~Dokumenthåndtering (ePROM papir/signerte dokument)~~
- ~~Administrasjonsgrensesnitt~~
	- ~~Opprette nye register~~
	- ~~Status for registrene, debug info, statistikk~~

Kjekt å ha
- Varslingssystem (delvis implementert)
- ~~Async datadump/rapporter~~
- Eksporter data: spss format
- ~~Import~~ (fihr format?, xml, ~~csv~~, ~~excel~~)
- ~~Massebestilling proms~~
- Administrasjonsgrensesnitt: kopier register (import/eksport definisjoner)
- Administrasjonsgrensesnitt: arkiver/slette register
- ~~Listehåndtering (gjenbruk og felles vedlikehold av lister innad et register, eks.: ja, nei, ukjent.~~ samt standardiserte lister globalt tilgjengelig)
