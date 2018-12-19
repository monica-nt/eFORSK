# Testscenarier

## Innlogging

- Hvis man er innlogget og åpner to faner/vinduer;
	- Endrer man innlogging i fane 1 (logger inn som annen bruker, endrer rolle eller enhet), skal man få beskjed om endret innlogging i fane 2 og man må laste inn applikasjonen på nytt for å fortsette. Ny innlogging reklekteres så i fane 2.
	- Prøver man å redigere på et objekt (skjema, skjematype, skjemaversjon osv) i fane 1, skal man få beskjed om at man allerede redigerer objektet i fane 2 og redigering blir sperret. Dette gjelder om en annen bruker redigerer objektet.
  
## Skjemabygger

- Skjema koblet mot ePROM skjema
    - ePROM skjemaene kan kun ligge på rot
    - kan kun opprette egne grupper på rot, ingen andre skjemaelementer
    - kan drop-droppe rekkefølgen på rot, men ikke dra ned noen andre skjemaelementer enn grupper
