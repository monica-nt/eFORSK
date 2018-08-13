# Informasjonsarkitektur & funksjonalitet

## Hovedgrensesnittet består av følgende deler:

* Header
  * App tittel/logo: eFORSK + registerets tittel
  * Brukerinformasjon
  * Logg ut
  * Meny
* Innhold
* Footer
  * App versjonsnummer

## Innholdet er delt opp i følgende deler:

* **Startside/Dashboard** 
	* Oppgaveliste
		* registerets ikke ferdigstilte skjema
		* registerets returnerte skjema
		* mine ikke ferdigstilte skjema
		* mine returnerte skjema
	* Enkel statistikk?
	* Snarvei til handlinger man har tilgang til: fylle ut skjema, bestille skjemautfyllelse, finn person i folkereg..
* **Skjemaer** - for å søke opp eller se skjema
	* Fyll ut skjema
	* Bestill skjemautfyllelse (fra person)
	* Mine skjema
	* Skjemasøk
* **Personer**/pasient 
	* Finn person i folkeregisteret
	* *Opprett person med hjelpenummer*
	* Liste personer med skjema 
	* Liste personer med mine skjema  (*mine pasienter*)
	* Personens side
		* informasjon fra folkeregister
		* visning av skjema registrert på person
		* PROMS bestillinger
* **Rapporter**
	* Eksporter data (*Datadump*)
	* Kodebok
	* (..)
* **Registeradministrasjon** 
	* Registeroppsett (Instillinger/valg, registerinformasjon)
	* Tilgangseneheter
	* Skjematyper
	* Randomisering?
	* PROMS bestillinger
* **Administrasjon** - for å legge til og endre registre
	* Registerliste
		* liste over eksisterende registre
		* mulighet for å opprette nye
 	* Registerredigering
		* tittel
		* PROMS kobling


## Hjelpefunksjoner

Ved redigering av eksisterende objekter vil applikasjonen sørge for å låse objektet slik at ingen andre brukere kan gjøre dette samtidig.
