# Randomisering

Randomisering kan legges inn som en egen felttype ved bygging av skjematype. Felttypen fungerer på samme måte som et valgfelt, der man kan opprette alternativer. Forskjellen ligger i grensesnittet ved utfylling av skjema, der man får en knapp for å kjøre randomisering. Ved trykk på knappen blir randomisert alternativ valgt, handlingen kan ikke angres.

Om man forsøker å slette et skjema som har en utført randomisering vil man få advarsel at handlingen blir logget for å forhindre forskningsjuks.

Algoritme som ligger til grunn for randomsering: Fisher-Yates (aka Knuth) Shuffle.
Første element velges etter at algoritmen er kjørt.

Forslag til utvidelse: man kan konfigurere når randomiseringen utføres:
* Ved skjemaopprettelse (ferdig randomisert når man kommer inn i skjema)
* Ved ferdigstillelse
* Manuelt (man får knapp som må trykkes på)

## ePROM

I tilfelle et randomiseringsfelt er lagt til en ePROM skjematype, vil dette feltet ikke være synlig ved utfyllelse i ePROM. Feltet vil bli randomisert ved bestillelse. I tilfelle papirbesvarelse, vil feltet bli randomisert ved leveranse tilbake til registeret.

## Typer randomisering

### Enkel randomisering

Kun enkel randomisering (myntkast) støttes i dagens versjon, det vil si tilfeldig valg av gruppe.

### Blokkrandomisering

Løsningsforslag ved eventuell utvidelse til å støtte stratifisert blokkrandomisering:

Administrasjon:
* Grupper: så mange man vil, eks. A, B, C  (støtte ulike fordelig?)
* Blokkstørrelse: flere mulige, eks. 3, 6, 9 (må være multiplum av grupper)
* Stratifisering (begrenset): fastsatte egenskaper som man kan plukke i (aldersgrupper, kjønn)
* Kunne sette maks antall "deltakelser"

Utførelse:
* Når man på et skjema trykker randomiser, spørres servicen om å få en gruppe.
* Servicen vil finne blokk med ledig "plass"
	* Hvis blokk med ledig "plass" ikke finnes, generer ny blokk 
		* velg tilfeldig blokkstørrelse
		* fyll blokken med grupper i tilfeldig rekkefølge
	* Hvis maks antall "deltakelser" er oppnådd - returner ingen
* Merk plassen med skjemaets GUID
* Returner plassens gruppe til skjema.
	
Testmodus og ikke-testmodus har separate blokker

Sletting av skjema, frigjør plassen fra blokk?

Lagring av blokker;

```
[
	{
		id: 1,
		testmode: false,
		stratification: [
			{ Variable = "Kjoenn", Value = "1" }
		]
		groups: [
			{ Group: A, FormDataId = null },
			{ Group: B, FormDataId = null },
			{ Group: C, FormDataId = null }
		]
	},	
	{
		id: 2,
		testmode: false,
		stratification: [
			{ Variable = "Kjoenn", Value = "0" }
		]
		groups: [
			{ Group: A, FormDataId = null },
			{ Group: B, FormDataId = null },
			{ Group: C, FormDataId = null },
			{ Group: A, FormDataId = null },
			{ Group: B, FormDataId = null },
			{ Group: C, FormDataId = null }
		]
	}
]
```
