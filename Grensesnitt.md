# Informasjonsarkitektur & funksjonalitet

Skisse: [https://docs.google.com/drawings/d/1f_DttcP3IAL8rGsNkuAhyoxv2KBahc3H3YwTk9uSWOo/edit?usp=sharing]

## Hovedgrensesnittet består av følgende deler:

* Header
  * App tittel/logo
  * Brukerinformasjon
  * Logg ut
  * Meny
* Innhold
* Footer
  * App versjonsnummer

## Innholdet er delt opp i følgende deler:

* **Startside** - arbeidsliste for innlogget person? Enkel statistikk over registeret?
* **Administrasjon** - for å legge til og endre registre
	* Registerliste
		* liste over eksisterende registre
		* mulighet for å opprette nye
		* *kopiere eksisterende*
 	* Registerredigering
		* tittel
		* beskrivelse (med Markdown?)
		* PROMS api-nøkkel
		* *tilgangsenheter (første versjon uten tilgangstre?)*
* **Registeradministrasjon** - for å legge til og endre skjematype, konfigurere opp PROMS, og andre innstillinger for registeret
* **Pasienter** - for å søke opp eller se pasienter
	* Pasient - se en pasient
* **Skjemaer** - for å søke opp eller se skjema
	* Skjema - se/redigere et skjema


## Hjelpefunksjoner

Ved redigering av eksisterende objekter vil applikasjonen sørge for å låse objektet slik at ingen andre brukere kan gjøre dette samtidig.
