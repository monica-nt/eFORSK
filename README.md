# IKT støtte for forskning - prosjektnavn mangler! 

Her følger dokumentasjon for utvikling av verktøyet. Brukes som kravspesifikasjon ved utvikling, dokumentasjon og funksjonalitetsoversikt for (potensielle) brukere av verktøyet. Tekst i *skråskrift* i lenkede dokumenter er ennå ikke planlagt implementert i kommende versjon.

## Terminologi

Skal brukes for konsistens i dokumentasjon, kode og grensesnitt. Engelsk brukes i programmeringskode.

* **Register** (Registry) - En egen database i løsningen, der et register eller forskningsprosjekt kan registrere sine data
* **Tilgangsenhet** (AccessUnit) - En egen tilgang innad et register. Tilgangsenhetene er definert i et tilgangstre, som bestemmer hvilke data som kan sees
* **Skjematype** (FormType) - Definisjonen bak et skjema som kan fylles ut i et register. Skjematypene opprettes av registeransvarlige i hvert enkelt register.
* **Skjemaversjon** (FormVersion) - En versjon av skjematypen
* **Felt** (Field) - En felt som kan besvares i et skjema
	* **Kodenavn** (CodeName) - Et felts kodenavn ved datauttrekk (datadump o.l.)
	* **Visningsnavn** (DisplayName) - Overskrift for feltet ved utfyllelse i grensesnitt (brukervennlig forklaring av feltet)

## Dokumenter:
* [Overordnet arkitektur](https://github.com/HemitSystemutvikling/dokumentasjon-forskningsapp/blob/master/Overordnet%20arkitektur.md)
* [Databasestruktur](https://github.com/HemitSystemutvikling/dokumentasjon-forskningsapp/blob/master/Databasestruktur.md)
* [Roller & tilgangstre](https://github.com/HemitSystemutvikling/dokumentasjon-forskningsapp/blob/master/Roller%20og%20tilgangstre.md)
* [Grensesnitt & funksjonalitet](https://github.com/HemitSystemutvikling/dokumentasjon-forskningsapp/blob/master/Grensesnitt.md)
* [Skjemasystemet](https://github.com/HemitSystemutvikling/dokumentasjon-forskningsapp/blob/master/Skjemasystemet.md)
* [Datadump & kodebok](https://github.com/HemitSystemutvikling/dokumentasjon-forskningsapp/blob/master/Datadump%20og%20kodebok.md)
* [PROMS integrasjon](https://github.com/HemitSystemutvikling/dokumentasjon-forskningsapp/blob/master/PROMS%20integrasjon.md)
* Randomisering - her trenger vi mer input!

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
- Integrasjon mot PROMS (inkl manuell bestilling,  mottak)
- Datadump (excel, csv)
- Kodebok

Bør gjøre
- Optimalt databaselag for løsningen (dapper, dbup, databasetool)
- Tilgangsstyring innad register
- Randomisering
- Koblede skjematyper
- Enkel bruksstatistikk
- Standard for utvidelser per enkelt register (rapporter)
- Samtykkehåndtering
- Dokumenthåndtering (proms papir/signerte dokument)
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

## Navneforslag

* DAFF = Digitalt Assistert Fremragende Forskning . På folkemunne Dæffy. / Tore
* HEPFØ - Helse Midts Platform for Førskning / Rune
* FØKK - Forskningens Øremerkede KomputerKrykker / Astrid
* HEMFIKTT - Helse Midtnorges Forskings- og IKT-Tilrettelegging / Øyvind
* FORSKNING - Forskning Over Ressurssterke Skjema Kan Nyttes I Næring, Godt. / Christian W
* FIKS - Forskningens IKt-Støtte / Håvard S
* FAKS - er en telekommunikasjonsteknologi for overføring av informasjon, som dokumenter, tekst, brev, tegninger og fotografier, spesielt ved overføring via et telefonnett. Ordet brukes også som betegnelse på dokumentene som er overført. Ordet er også opprinnelse til verbalformen å fakse. / Eilev
* FRAM - ForskningRegister bAsert på MRS / Rune
* MUFFEDILLE - Mrsbasert Understøttelse For Forskning Eller Domenebasert Integrerte Lavkostnads Lengevirkende Effektmål / Øyvind
* MOPP - MRS Og Pretensiøse Professorer / Håvard S
* FLOM - Forskningsregister Lagd Oppå MRS / Håvard S
* STØFF - ikt STØtte For Forskning / Eilev
* KØTT - iKt stØTTe for forskning / Christian W
* IS - Ikt Støtte for forskning / Rune
* SØTE ORK - ikt StØTtE for fORsKing / Håvard S
* TØTTE - ikt sTØTTE for forsking / Christian W
* STORK - ikt STøtte for fORsKning / Johan
* TORSK - ikt sTøtte fOR forSKning / Håvard S
* TØFF - ikt sTØtte For Forskning / Eilev
* SCIENCE - IKT Støtte for Forskning / Christian W
* FORMula / Christian W
