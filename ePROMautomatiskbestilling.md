# ePROM automatisk bestilling

Arbeidsdokument, forslag til funksjonalitet som skal støtte automatiske bestillinger.

# Oppsett av jobber

Som registeransvarlig kan man i administrasjonen sette opp så mange automatiske bestillingsjobber man vil.

En automatisk bestillingsjobb må alltid grunne ut i fra et eksisterende skjema (**triggerskjema**). Man kan for eksempel lage seg en registreringsskjematype for å inkludere forskningsobjekter i registeret, for videre å få trigget automatiske bestillinger.

Automatiske bestillingsjobber kjøres en gang hver natt (?).

# Jobb

En jobb har en av følgende statuser:
* **Stoppet** 
* **Testkjører** - Jobb kjøres i testmodus
* **Kjører** - jobb kjøres også i ikke-testmodus

Konfigurasjon:
* **Triggerskjematype**: Hvilken skjematype (uansett versjonsnummer) skal trigge bestilling av ePROM (trenger ikke være foreldreskjematypen, hva som helst skal kunne trigge bestilling). Kan ikke endres etter opprettelse av jobb.
* **Bestillingsskjematype**: Hvilken ePROM aktivert skjematype (+ versjonnummer) som skal bestilles automatisk. Bestiller høyeste publiserte versjonsnummer. Kan ikke endres etter opprettelse av jobb.
  * Hvis bestillingsskjematype er en tilknyttet skjematype og triggerskjematypen ikke er foreldretypen til bestillingsskjematypen - må det opplyses om at foreldreskjema vil opprettes som kladd ved mottatt svar. 
* Bestillingstidspunkt
  * **X** dager etter opprettelse/første ferdigstillelse(default)/siste endring av triggerskjema
  * Valg om bestillingen skal gjentas (gjentas da for hver **X** dager spesifisert i forrige punkt. kan ikke spesifiseres hvis bestillingsskjematype og triggerskjemastype er den samme typen, da denne allerede blir gjentagende)
    * Spesifiser max antall gjentakelser (**Z**)
    * Valg for å avvent gjentakelse hvis det mangler svar på forrige bestilling
* Valg for å stoppe bestilling
  * hvis forskningsobjektet allerede har **Y** antall skjemaer (eller aktive bestillinger) av bestillingsskjematypen (uavhengig av versjonsnummer) på forskningsobjektet. Y er default 1 for ikke gjentagende bestillinger, og default Z i tilfelle gjentagende bestillinger - men kan overstyres.
  * Forskningsobjekt sorteliste
  * Triggerskjema opprettet før dato **D** (default dagens dato for å hindre at jobben fyrer mange bestillinger ved opprettelse)
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

# Teknisk: kjøring av jobb

Finn status for triggerskjema for tidspunkt **T**:
- Hent eksisterende ordrer som stammer fra bestillingsjobben
- Hent liste av triggerskjemaer (alle uansett kriterier) - denne listen med status skal loggføres etter kjøring av jobb. Innhold i lista:
  - Triggerskjema
  - Om den skal føre til bestilling
  - Årsak til at den eventuelt ikke skal føre til bestilling
- For hvert triggerskjema:
  - Sjekk om triggerskjemaet er opprettet før dato **D**
  - Sjekk om hvis forskningsobjektet er sortelistet i jobb
  - Sjekk om oppfyller regler for bestillingstidspunkt i forhold til tidspunkt **T**
  - I tilfelle ikke gjentagende bestillingsjobb, sjekk triggerskjemaer om allerede er "brukt"
  - I tilfelle gjentagende bestillingsjobb med maks bestillinger satt, sjekk om bestillinger har passert maks
  - Sjekk om forskningsobjektet har passert maks antall skjema (+ aktive bestillinger) av bestillingsskjematypen
  
Kjør Jobb:
- Hvis bestillingsskjematypen ikke har noen publiserte versjoner lenger, sett jobbstatus til stoppet og avbryt kjøringen
- Kjør bestilling basert på triggerskjemaene
