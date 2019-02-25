# Testscenarier

Følgende scenarier skal skapes og testes i hver versjon som skal produksjonssettes.

## Innlogging

- Hvis man er innlogget og åpner to faner/vinduer;
	- Endrer man innlogging i fane 1 (logger inn som annen bruker, endrer rolle eller enhet), skal man få beskjed om endret innlogging i fane 2 og man må laste inn applikasjonen på nytt for å fortsette. Ny innlogging reklekteres så i fane 2.
	- Prøver man å redigere på et objekt (skjema, skjematype, skjemaversjon osv) i fane 1, skal man få beskjed om at man allerede redigerer objektet i fane 2 og redigering blir sperret. Dette gjelder også om en annen bruker redigerer objektet.
- Vær utlogget fra eFORSK. Logg på et MRS register. Bruk samme nettleser og naviger til eFORSK. Feilmelding skal vises.
  
## Registre
- Data i et register skal ikke være tilgjengelig i et annet register (datalekkasje)
- En administrator skal kunne konfigurere at et register kun kan opprette skjema og bestille ePROM i testmodus (funksjonene låses i ikke-testmodus)
- En administrator skal kunne konfigurere at et register ikke skal kunne bruke personregisteret. Har det på et tidspunkt vært i bruk og det finnes skjemaer koblet mot dette, skal utfylt skjemadata enda fungere.
- En administrator skal kunne teste ePROM tilkoblingen til et register, og ved feil API nøkkel skal man få beskjed om nettopp dette

## Skjematyper

### Skjematype
- Man skal kunne opprette en skjematype som en underskjematype av en annen (opprett to nivåer ned for å dekke mest komplekse scenarier)

### Skjemaversjoner
- Man skal kun kunne ha en skjemaversjon i kladd på en skjematype om gangen
- En skjemaversjon i kladd skal kunne slettes
	- Ved sletting av en versjon skal nye felter og regler i versjonen slettes
	- Ved sletting av en versjon skal fjernede felter og regler "reaktiveres" 
	- Ved opprettelse av ny versjon etter at en versjon er slettet, skal den nye versjonen få versjonssnummeret som den slettede versjonen hadde - slik at alle versjonssnummere er kronologiske.

### Skjemabygger
- Hvis man har opprettet en skjematype med en eller flere standardskjemaer..
    - skal standardskjemaene kan kun ligge på rot
    - skal det kan kun være mulig å ha egne grupper på rot, ingen andre skjemaelementer
    - skal man kunne endre rekkefølgen på rot-elementer, men ikke flytte ned noen andre skjemaelementer enn grupper
- Man skal ikke kunne redigere et felt eller en regel som er opprettet i en versjon som ikke er i kladd lenger (man skal kun kunne fjerne dem)
- I forhåndsvisning skal man se hvilke verdier man får ut ved eksportering av data
- I ePROM forhåndsvisning skal man kunne se
	- digitalt skjema
	- digitalt skjema med samtykkeforespørsel (for registre som har samtykke aktivert)
	- papirskjema (for skjematyper med ePROM papir aktivert)
	- papirskjema med samtykkeforspørsel (for skjematyper med ePROM papir aktivert og for registre som har samtykke aktivert)
    
### ePROM aktivert skjema
- Et ePROM aktivert skjema skal ikke kunne bestille utenfor testmodus før det er godkjent av en administrator
    
## Skjemautfylling
- Et synlig avkryssningsfelt som er avkrysset forventes å få verdi 1 ved dataeksport
- Et synlig avkryssningsfelt som ikke er avkrysset forventes å få verdi 0 ved dataeksport
- Et skjult avkryssningsfelt forventes å ikke få noen verdi (blank/tom) ved dataeksport.
    
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
