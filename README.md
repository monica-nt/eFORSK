# IKT støtte for forskning 

Dokumentasjon for utvikling av verktøyet. Brukes som kravspesifikasjon for utvikling, og som en funksjonalitetsoversikt for brukere av verktøyet. Tekst i *skråskrift* er ennå ikke planlagt implementert i kommende versjon.

Dokumenter:
[Skjemasystemet](https://github.com/HemitSystemutvikling/dokumentasjon-forskningsapp/blob/master/Skjemasystemet.md)

# Prioriteringsliste utvikling

Minimumsliste må-gjøre MRS for forskning
- App skall (Fungerendes applikasjon som kommuniserer med service-lag. Ingen funksjonalitet)
	- Angular front-end
	- WCF
- Databasemodell
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
