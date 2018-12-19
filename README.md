# eFORSK dokumentasjon

Her følger dokumentasjon for utvikling av verktøyet. Brukes som kravspesifikasjon ved utvikling, dokumentasjon og funksjonalitetsoversikt for (potensielle) brukere av verktøyet. Tekst i *skråskrift* i lenkede dokumenter er ennå ikke planlagt implementert i kommende versjon.

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
* **Mine skjema** - brukeren som oppretter et skjema (eller har bestilt det utfylt via ePROM) er den som eier skjemaet
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

- flere valideringsregler (krever ePROM implementasjon)
- mulighet for å få forhåndsvisning av ePROM digitalt og papirsrkjema (krever ePROM arbeid)
- mulighet for registeransvarlig å sende ut et varsel for alle brukerene av registeret
- Skjemabygger
	- Mulig å legge til standardskjema etter en skjematype er opprettet
