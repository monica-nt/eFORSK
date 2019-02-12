[![Build Status](https://hemit.visualstudio.com/eFORSK/_apis/build/status/eFORSK-CI%20Pack%20Publish?branchName=master)](https://hemit.visualstudio.com/eFORSK/_build/latest?definitionId=28?branchName=master)

# eFORSK dokumentasjon

Her følger dokumentasjon for utvikling av verktøyet. Brukes som kravspesifikasjon ved utvikling, dokumentasjon og funksjonalitetsoversikt for (potensielle) brukere av verktøyet. Tekst i *skråskrift* i lenkede dokumenter er ennå ikke planlagt implementert i kommende versjon.

## Hva er eFORSK
eFORSK er en frittstående IKT løsning for elektronisk innsamling av data basert på skjema. eFORSK tilbyr selvbetjeningsløsning for oppsett av skjematyper og innsamling av data. Løsningen tilbyr tett integrasjon med Helse Midt-Norge sin ePROM-løsning og gjennom denne mulighet for skjemabasert sikker digital kommunikasjon med pasienter via HelseNorge.no, digipost/eboks og papirskjema i posten. 

## Terminologi og definisjoner

Skal brukes for konsistens i dokumentasjon, kode og grensesnitt. Engelsk brukes i programmeringskode.

* **Register** (Registry) - En egen database i løsningen, der et register eller forskningsprosjekt kan registrere sine data
* **Tilgangsenhet** (AccessUnit) - En egen tilgang innad et register. Tilgangsenhetene er definert i et tilgangstre, som bestemmer hvilke data som kan sees
* **Skjematype** (FormType) - Definisjonen bak et skjema som kan fylles ut i et register. Skjematypene opprettes av registeransvarlige i hvert enkelt register.
* **Skjemaversjon** (FormVersion) - En versjon av skjematypen
* **Felt** (Field) - En felt som kan besvares i et skjema
	* **Variabelnavn** (CodeName) - Et felts navn ved datauttrekk (datadump o.l.)
	* **Visningstekst** (DisplayName) - Spørsmålet ved feltet ved utfyllelse i grensesnitt (brukervennlig forklaring av feltet)
* **Forskningsobjekt** (ResearchObject) - data/skjemaer legges på et forskningsobjekt (i et vanlig registers tilfelle: pasient) i registeret. det er valgt å kalle dette forskningsobjekt da det nødvendigvis ikke trenger å være en pasient eller person, men f.eks. legemiddel.
* **Mine skjema, egne skjema, andres skjema** - brukeren som oppretter et skjema (eller har bestilt det utfylt via ePROM) er den som eier skjemaet
* **Skjema i arbeid** - et skjema som ikke har status "ferdigstilt"
* **Hovedskjematype** - en skjematype som kan registreres uten at det plasseres på en annen skjematype
* **Underskjematype** - en skjematype som må registreres på en allerede eksisterende foreldreskjematype

## Dokumenter:
* [Overordnet arkitektur](Overordnet%20arkitektur)
* [Databasestruktur](Databasestruktur)
* [Roller, tilgangstre](Roller%20og%20tilgangstre)
* [Forskningsobjekter, samtykkehåndtering](Forskningsobjekter)
* [Logging og innsyn](Logging%20og%20innsyn)
* [Informasjonsarkitektur & funksjonalitet](Informasjonsarkitektur)
* [Skjemasystemet](Skjemasystemet)
* [Eksporter data & kodebok](Datadump%20og%20kodebok)
* [ePROM integrasjon](PROMS%20integrasjon)
* [Randomisering](Randomisering)
* [Testscenarier](Testscenarier) - for testing av applikasjonen
* [Kodemiljø](Kodemiljø) - prosjektoppsett for utviklere 

## Milepæler

1. 15.09.2018: Mulighet for å opprette en skjematype med skjemabyggeren
2. 15.10.2018: Pasienthåndtering på plass, med mulighet for å fylle ut skjema i eFORSK
3. 06.11.2018: Integrasjon med ePROM på plass med mulighet for å bestille skjema
4. 30.11.2018: Rapporter på plass: Eksport av data (datadump) og kodebok
5. 21.12.2018: Samtykkehåndtering
6. 06.01.2019: Randomisering
7. 20.02.2019: v1.0 Ferdig utviklet

## Prioriteringsliste utvikling

Minimumsliste må-gjøre MRS for forskning
- App skall (Fungerendes applikasjon som kommuniserer med service-lag. Ingen funksjonalitet)
	- Angular front-end
	- WCF
- Databasestruktur
	- Videreutviklet MRS modell
	- Dapper?
- Mulighet for å definere et skjema
	- mulighet for å lage nye versjoner av et skjema
- Mulighet for å fylle ut skjema
- Integrasjon mot ePROM (inkl manuell bestilling,  mottak)
- Eksporter data (excel, csv)
- Kodebok
- Logging og innsyn
- Randomisering (enkel knapp, tildelt gruppe  A,B,C...)
- Samtykkehåndtering

Bør gjøre
- Optimalt databaselag for løsningen (dapper, dbup, databasetool)
- Tilgangsstyring innad register
- Koblede skjematyper
- Enkel bruksstatistikk
- Standard for utvidelser per enkelt register (rapporter)
- Dokumenthåndtering (ePROM papir/signerte dokument)
- Administrasjonsgrensesnitt 
	- Opprette nye register
	- Status for registrene, debug info, statistikk

Kjekt å ha
- Notifikasjonssystem
- Async datadump/rapporter
- Datadump spss format
- Import (fihr format?, xml, csv, excel)
- Massebestilling proms
- Administrasjonsgrensesnitt: kopier register (import/eksport definisjoner)
- Administrasjonsgrensesnitt: arkiver/slette register
- Listehåndtering (gjenbruk og felles vedlikehold av lister innad et register, eks.: ja, nei, ukjent. samt standardiserte lister globalt tilgjengelig)

## Fase 2 (forslag)

- Administrator skal kunne "stoppe" et register for endringer
- Mulig å låse en skjematype for nye skjema og endring av eksisterende data
- Komplett skjemalogg på forskningsobjektnivå (for å kunne oppdage slettede og gjenopprettede randomiseringsskjema)
- Flere valideringsregler (krever ePROM implementasjon)
- Mlighet for å få forhåndsvisning av ePROM digitalt og papirsrkjema (krever ePROM arbeid)
- Mulighet for registeransvarlig å sende ut et varsel for alle brukerene av registeret
- Skjemabygger
	- Mulig å legge til standardskjema etter en skjematype er opprettet
	- Listehåndtering innad i registeret (for gjenbruk av lister på tvers av felter og skjematyper)
- Importer data
	- Paging på importjobb liste
	- Mulig å opprette skjematype fra importfil
- Grensesnitt for å lese og søke i logg under administrasjon (for oversikt over all aktivitet)
- Liste over brukere som har vært innlogget i et register (under administrasjon)
- Legge brukermanual/Om eFORSK i et github repo - og automatisk hente inn dette i appen
