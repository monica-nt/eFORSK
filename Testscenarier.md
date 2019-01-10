# Testscenarier

## Innlogging

- Hvis man er innlogget og åpner to faner/vinduer;
	- Endrer man innlogging i fane 1 (logger inn som annen bruker, endrer rolle eller enhet), skal man få beskjed om endret innlogging i fane 2 og man må laste inn applikasjonen på nytt for å fortsette. Ny innlogging reklekteres så i fane 2.
	- Prøver man å redigere på et objekt (skjema, skjematype, skjemaversjon osv) i fane 1, skal man få beskjed om at man allerede redigerer objektet i fane 2 og redigering blir sperret. Dette gjelder også om en annen bruker redigerer objektet.
- Vær utlogget fra eFORSK. Logg på et MRS register. Bruk samme nettleser og naviger til eFORSK. Feilmelding skal vises.
  
## Skjematyper


### Skjemabygger
- Skjema koblet mot ePROM skjema
    - ePROM skjemaene kan kun ligge på rot
    - kan kun opprette egne grupper på rot, ingen andre skjemaelementer
    - kan endre rekkefølgen på rot-elementer, men ikke flytte ned noen andre skjemaelementer enn grupper
    
### ePROM aktivert skjema
- Et ePROM aktivert skjema skal ikke kunne bestille utenfor testmodus før det er godkjent av en administrator
    
## Forskningsobjekter
- Registerets forskningsobjekter
	- Et forskningsobjekt som har et skjema (uansett status) skal vises i lista over "registerets forskningsobjekter", sortert etter siste endringstidspunkt på skjemaet. Blir alle skjema slettet eller samtykkestatus ikke er "samtykket" skal ikke forskningsobjektet vises i lista.
	
## Samtykke
- Samtykke skal kun være i forbindelse med forskningsobjekter av typen "personer fra folkeregisteret"
- Et register med samtykkekonfigurasjon A..
	- skal etterspørre samtykke ved opprettelse av skjema for et forskningsobjekt som ikke har samtykket
	- skal vise hvilke forskningsobjekter  som mangler samtykke ved bestilling av ePROM og som vil bli forespurt dette
	- skal ved ePROM bestilling med forskningsobjekter som mangler samtykke ikke kunne velge utsendelsesvalg: "Sendes ikke, mottaker må varsles manuelt"
- Et register med samtykkekonfigurasjon B..
	- skal vise informasjon om samtykke, men skal settes automatisk til samtykket ved skjemaopprettelse eller ePROM svar. 
	- skal kunne endres manuelt på forskningsobjektet
	- skal ikke kunne bestilles via ePROM.
- Et register med samtykkekonfigurasjon C..
	- skal ikke vise noe informasjon om samtykke for brukeren, man skal kunne registrere uten spørsmål om dette.

## Testmodus
- Et skjema eller en skjemabestilling opprettet utenfor testmodus skal ikke være tilgjengelig i testmodus, og omvendt.

## Registre
- Data i et register skal ikke være tilgjengelig i et annet register (datalekkasje)
