# Testscenarier

## Innlogging

- Hvis man er innlogget og åpner to faner/vinduer;
	- Endrer man innlogging i fane 1 (logger inn som annen bruker, endrer rolle eller enhet), skal man få beskjed om endret innlogging i fane 2 og man må laste inn applikasjonen på nytt for å fortsette. Ny innlogging reklekteres så i fane 2.
	- Prøver man å redigere på et objekt (skjema, skjematype, skjemaversjon osv) i fane 1, skal man få beskjed om at man allerede redigerer objektet i fane 2 og redigering blir sperret. Dette gjelder om en annen bruker redigerer objektet.
	- Vær utlogget fra eFORSK. Logg på et MRS register. Bruk samme nettleser og naviger til eFORSK. Feilmelding skal vises.
  
## Skjemabygger

- Skjema koblet mot ePROM skjema
    - ePROM skjemaene kan kun ligge på rot
    - kan kun opprette egne grupper på rot, ingen andre skjemaelementer
    - kan drop-droppe rekkefølgen på rot, men ikke dra ned noen andre skjemaelementer enn grupper
    
## Forskningsobjekter

- Registerets forskningsobjekter
	- Et forskningsobjekt som har et skjema (uansett status) skal vises i lista over "registerets forskningsobjekter", sortert etter siste endringstidspunkt på skjemaet. Blir alle skjema slettet eller samtykkestatus ikke er "samtykket" skal ikke forskningsobjektet vises i lista.
