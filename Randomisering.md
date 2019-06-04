# Randomisering

Kun enkel randomisering støttes, det vil si tilfeldig valg av randomiseringsgruppe.

Randomisering kan legges inn som en egen felttype ved bygging av skjematype. Felttypen fungerer på samme måte som et valgfelt, der man kan opprette alternativer. Forskjellen ligger i grensesnittet ved utfylling av skjema, der man får en knapp for å kjøre randomisering. Ved trykk på knappen blir tilfeldig alternativ valgt, handlingen kan ikke angres. 

Algoritme som ligger til grunn for randomsering: Fisher-Yates (aka Knuth) Shuffle.
Første element velges etter at algoritmen er kjørt.

## ePROM

I tilfelle et randomiseringsfelt er lagt til en ePROM skjematype, vil dette feltet ikke være synlig ved utfyllelse i ePROM. Feltet vil bli randomisert ved bestillelse. I tilfelle papirbesvarelse, vil feltet bli randomisert ved leveranse tilbake til registeret.

## Blokkrandomisering

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
