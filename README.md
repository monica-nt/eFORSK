# IKT støtte for forskning - prosjektnavn mangler! 

Dokumentasjon for utvikling av verktøyet. Brukes som kravspesifikasjon for utvikling, og som en funksjonalitetsoversikt for brukere av verktøyet. Tekst i *skråskrift* i lenkede dokumenter er ennå ikke planlagt implementert i kommende versjon.

## Terminologi

* **Register** - En egen database i løsningen, der et register eller forskningsprosjekt kan registrere sine data
* **Enhet** - En egen tilgang innad et register. Enhetene er definert i et tilgangstre, som bestemmer hvilke data som kan sees

## Dokumenter:
* [Overordnet arkitektur](https://github.com/HemitSystemutvikling/dokumentasjon-forskningsapp/blob/master/Overordnet%20arkitektur.md)
* [Databasestruktur](https://github.com/HemitSystemutvikling/dokumentasjon-forskningsapp/blob/master/Databasestruktur.md)
* [Roller & tilgangstre](https://github.com/HemitSystemutvikling/dokumentasjon-forskningsapp/blob/master/Roller%20og%20tilgangstre.md)
* [Grensesnitt](https://github.com/HemitSystemutvikling/dokumentasjon-forskningsapp/blob/master/Grensesnitt.md)
* [Skjemasystemet](https://github.com/HemitSystemutvikling/dokumentasjon-forskningsapp/blob/master/Skjemasystemet.md)
* Datadump/kodebok
* [PROMS integrasjon](https://github.com/HemitSystemutvikling/dokumentasjon-forskningsapp/blob/master/PROMS%20integrasjon.md)
* Randomisering

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
- Admingrensesnitt 
	- Opprette nye register
	- Status for registrene, debug info, statistikk

Kjekt å ha
- Notifikasjonssystem
- Async datadump/rapporter
- Datadump spss format
- Import (fihr format?, xml, csv, excel)
- Massebestilling proms
- Administrasjon: kopier register (import/eksport definisjoner)
- Administrasjon: arkiver/slette register
