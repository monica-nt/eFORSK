# Importering av data

*Planleggingsdokument, funksjonalitet ikke i implementasjon*

Grensesnitt vises med liste over eksisterende importer med status. Kan klikke seg inn på hver enkelt og se konfigurasjon og hvilke skjema som er lastet opp. Kan velge å slette alle skjemaene i importen.

Hvis tilgang til å opprette skjematyper vises knapp for å lage ny skjematype basert på importfil.
Hvis tilgang til å opprette skjemadata, vis knapp for å åpne dialog for å importere skjema:

* Bruker velger hvilken skjematype og versjon som skal importeres til, og legger til fil. Trykker "last opp". Lages evt funksjonalitet for å velge "til ny skjematype" for registeransvarlig.

	* Server: filinnhold analyseres (fil lagres ikke på server), og rapport sendes tilbake til klient med oversikt over
		* antall rader (skjema)
		* liste over skjemtypes felter (systemutfylte felter ekskludert, bortsett fra forskningsobjektets id/fnr)
			* må også vurdere å utvide til at man kan koble mot hovedskjema GUID
		* lister over kolonner/variabelnavn i fil, der for hver variabel:
			* variabelnavn
			* unike verdier per variabelnavn
			* mulige felttyper per variabelnavn (basert på dataverdier)
			* mulige skjemafelt per variabelnavn (basert på mulige felttyper)
			* foreslått skjemafelt per variabelnavn (basert på mulige skjemafelt matchet mot variabelnavn)
			
* Bruker må konfigurere importen
	* valg kombinasjon av variabler som skal gi unik nøkkel, for evt gjentagende import???
	* for hver variabel i importfil;
		* utlisting verdier funnet i importfil
		* liste over mulige skjemafelter å importere til, foreslått felt er forhåndsvalgt
			- forkningsobjektets id/fnr kommer først og er påkrevd
			- kan velge å ikke importere variabelen
	* oppsummering over variabler i importfil som evt mangler kobling
	* oppsummering over felter i skjematypen som evt mangler kobling
	* oppsummering over variabler som er koblet mot samme felt - må fikses før man kan fortsette
	* valg (forhåndsvalgt) om skjema skal forsøkes ferdigstilles (skjema får da status "til kontroll" om dem ikke validerer)
		* undervalg om skjemaregler skal ignoreres (skjema får status "ferdigstilt" uansett)

* start import valg
	* sender med original fildata på nytt, og konfigurasjon.
* forkast import valg
