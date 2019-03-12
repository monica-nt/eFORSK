# ePROM automatisk bestilling

Arbeidsdokument, forslag til funksjonalitet som skal støtte automatiske bestillinger.

# Oppsett av jobber

Som registeransvarlig kan man i administrasjonen sette opp så mange automatiske bestillingsjobber man vil.

En automatisk bestillingsjobb må alltid grunne ut i fra et eksisterende skjema (**triggerskjema**). Man kan for eksempel lage seg en registreringsskjematype for å inkludere forskningsobjekter i registeret, for videre å få trigget automatiske bestillinger.

Automatiske bestillingsjobber kjøres en gang i timen (?).

# Jobb

En jobb har en av følgende statuser:
* **Stoppet** 
* **Testkjører** - Jobb kjøres i testmodus
* **Kjører** - jobb kjøres også i ikke-testmodus

Konfigurasjon som ikke kan endres etter opprettelse:
* Hvilken ePROM aktivert skjematype (+ versjonnummer) som skal bestilles automatisk, kalt **bestillingsskjematype**
* Hvilken skjematype (uspesifisert versjonsnummer) skal trigge bestilling av ePROM, kalt "**triggerskjema**" (trenger ikke være foreldreskjematypen, hva som helst skal kunne trigge bestilling)

Konfigurasjon som kan endres:
* Bestillingstidspunkt
  * **X** dager etter [opprettelse/første ferdigstillelse/siste endring] av triggerskjema
  * Valg om bestillingen skal gjentas (gjentas da for hver **X** dager spesifisert i forrige punkt. kan ikke spesifiseres hvis bestillingsskjametype og triggerskjemastype er den samme typen)
    * Spesifiser max antall gjentakelser (**Z**)
    * Valg for å stoppe gjentakelse hvis det mangler svar på forrige bestilling
* Valg for å stoppe bestilling hvis forskningsobjektet allerede har **Y** antall skjemaer (eller aktive bestillinger) av samme skjematype (uavhengig av versjonsnummer) på forskningsobjektet. Y er default 1 for ikke gjentagende bestillinger, og default Z i tilfelle gjentagende bestillinger - men kan overstyres.
* Antall utløpsdager
* Antall dager før purring
  
Hver bestilling og hvert skjemasvar fra bestillingen vil merkes med den automatiske bestillingsjobbens ID for sporing.

Mulighet for å se hvilke bestillinger som vil trigges det neste døgnet?

Loggføre detaljer ved kjøring av jobb til db for sporing?

# Scenarier

### Skjema bestilles manuelt før den automatiske jobben kjører
Har man ikke konfigurert "Valg for å stoppe bestilling hvis det allerede finnes Y antall skjemaer" vil ny bestilling kjøres, og man har da flere bestillinger på samme forskningsobjekt

### Jobben stoppes, for så å startes igjen lenge etterpå slik at flere gjentakende perioder har passert
Vil kun føre til en stk ny bestilling per forskningsobjekt, ikke en stk per passerte periode.

### En bestillingsjobb bestiller samme skjematype som er satt som triggerskjema
Dette vil si gjentangende bestilling av samme skjematype (at svar på bestilling av skjematypen også vil trigge ny bestilling av samme skjematype). Denne vil foregå uendelig hvis man ikke har definert "Valg for å stoppe bestilling..". 
Man får ikke mulighet til å sette "Valg om bestillingen skal gjentas" hvis bestillingsskjematype og triggerskjematype er den samme typen, siden jobben vil gjenta seg selv allerede.

### Triggerskjema endres etter gjentagende bestilling er i gang
Eksisterende bestillinger blir ikke berørt, videre gjentagende bestillinger vi forholde seg til oppdaterte verdier på triggerskjemaet

### Bestillingsjobb endres etter at den har vært aktiv
Endringer kan trigge veldig mange 
