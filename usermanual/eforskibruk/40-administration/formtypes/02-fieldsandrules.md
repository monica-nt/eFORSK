# Felter og regler

Under bygging av skjematyper skal man legge til elementer. Dette kan være felter eller regler.
                    
## Felter
Feltene er det som skal besvares i et skjema. Felttypene som støttes er tallfelt, avkrysningsfelt, datofelt, tekstfelt, valgfelt og randomiseringsfelt. eFORSK støtter ikke flervalgsfelt da analyse av eksportert data blir vanskelig om et svar inneholder flere verdier for et felt.

Alle felt vil ha et variabelnavn som brukes ved eksport, og en visningstekst som gjør det enkelt for bruker å vite hva som skal fylles ut.

## Randomiseringsfelt
Et randomiseringsfelt fungerer på samme måte som et valgfelt, hvor man kan opprette flere alternativer. Forskjellen ligger i grensesnittet ved utfylling av skjema; man får en knapp for randomisering som gir et tilfeldig valgt alternativ. Denne handlingen kan ikke angres.

I de tilfellene et randomiseringsfelt er lagt til en skjematype som kan bestilles utfylt (ePROM), så vil ikke feltet være synlig for vedkommende som skal fylle ut. Feltet vil bli randomisert ved bestilling. I de tilfellene hvor det er papirbesvarelse, så vil feltet bli randomisert ved leveranse tilbake til registeret.

## Systemutfylte felt
Man har også muligheten til å legge til systemutfylte felt. Et systemutfylt felt vil automatisk fylles ut ved opprettelse, endring eller ferdigstillelse. Vedkommende som fyller ut skjema har ikke muligheten til å fylle ut eller endre disse feltene. Dette er typisk skjemaID, pasientalder, kjønn og lignende.

## Skjemaregler
Skjemaregler omfavner både validerings- og vis/skjul-regler. Reglene kan på lik linje med felter opprettes på en versjon, og fjernes i senere versjoner.

Man kan teste reglene i forhåndsvisning av skjematypen under bygging.
