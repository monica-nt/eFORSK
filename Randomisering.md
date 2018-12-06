# Randomisering

Kun enkel randomisering støttes, det vil si tilfeldig valg av randomiseringsgruppe.

Randomisering kan legges inn som et kalkulert felt ved bygging av skjematype. Felttypen fungerer på samme måte som et valgfelt, der man kan opprette alternativer. Forskjellen ligger i grensesnittet ved utfylling av skjema, der man får en knapp for å kjøre randomisering. Ved trykk på knappen blir tilfeldig alternativ valgt, handlingen kan ikke angres. 

Algoritme som ligger til grunn for randomsering: Fisher-Yates (aka Knuth) Shuffle.
Første element velges etter at algoritmen er kjørt.

## ePROM

I tilfelle et randomiseringsfelt er lagt til en ePROM skjematype, vil dette feltet ikke være synlig ved utfyllelse i ePROM. Feltet vil bli randomisert ved bestillelse. I tilfelle papirbesvarelse, vil feltet bli randomisert ved leveranse tilbake til registeret.
