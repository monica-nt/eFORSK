# ePROM automatisk bestilling

Arbeidsdokument, forslag til funksjonalitet som skal støtte automatiske bestillinger.

# Oppsett av jobber

Som registeransvarlig kan man i administrasjonen sette opp så mange automatiske bestillingsjobber man vil.

En automatisk bestillingsjobb må alltid grunne ut i fra et eksisterende skjema (**triggerskjema**). Man kan for eksempel lage seg en registreringsskjematype for å inkludere forskningsobjekter i registeret, for videre å få trigget automatiske bestillinger.

Automatiske bestillingsjobber kjøres en gang hver natt (blir det for sjelden? ved feil, vil hvert døgn føre til 24 feilbestillinger frem til det oppdages).

# Jobb

En jobb har en av følgende statuser:
* **Stoppet** 
* **Aktiv i testmodus** - Jobb kjøres i testmodus
* **Aktiv** - jobb kjøres også i ikke-testmodus

Konfigurasjon:
* **Triggerskjematype**: Hvilken skjematype (uansett versjonsnummer) skal trigge bestilling av ePROM (trenger ikke være foreldreskjematypen, hvilken som helst type skal kunne trigge bestilling av hvilken som helst type). Kan ikke endres etter opprettelse av jobb. Regler for at triggerskjemaet fører til en bestilling:
  * Skjemastatuser
  * **X** dager etter **A**=(opprettelse/første ferdigstillelse(default)/siste endring) av triggerskjema
  * Triggerskjema opprettet etter dato **D** (default dagens dato for å hindre at jobben fyrer mange bestillinger ved opprettelse)
  
* **Bestillingsskjematype**: Hvilken ePROM aktivert skjematype (+ versjonnummer) som skal bestilles automatisk. Bestiller høyeste publiserte versjonsnummer. Kan ikke endres etter opprettelse av jobb.
  * Hvis bestillingsskjematype er en tilknyttet skjematype og triggerskjematypen ikke er foreldretypen til bestillingsskjematypen - må det opplyses om at foreldreskjema vil opprettes som kladd ved mottatt svar. (kan evt videreutvikles så den plasseres på sist opprettede foreldreskjema hvis det finnes)

 * Valg om bestillingen skal gjentas (gjentas da for hver **X** dager spesifisert i forrige punkt. Kan ikke spesifiseres hvis bestillingsskjematype og triggerskjemastype er den samme typen, da denne allerede blir gjentagende)
   * Spesifiser max antall gjentakelser (**Z**)
   * Valg om gjentakelse krever svar på forrige bestilling i rekken
* Antall utløpsdager
* Antall dager før purring
* Valg for å stoppe bestilling
  * Hvis forskningsobjektet allerede har **Y** antall skjemaer (eller aktive bestillinger) av bestillingsskjematypen (uavhengig av versjonsnummer) på forskningsobjektet. Y er default 1 for ikke gjentagende bestillinger, og default Z i tilfelle gjentagende bestillinger - men kan overstyres.
  * Forskningsobjekt sorteliste
  
Hver bestilling og hvert skjemasvar fra bestillingen vil merkes med den automatiske bestillingsjobbens ID for sporing.

Mulighet for å se hvilke bestillinger som vil trigges det neste døgnet?

Loggføre detaljer ved kjøring av jobb til db for sporing?

# Scenarier

### Skjema bestilles manuelt før den automatiske jobben kjører
Har man ikke konfigurert "Valg for å stoppe bestilling hvis det allerede finnes Y antall skjemaer" vil ny bestilling kjøres, og man har da flere bestillinger på samme forskningsobjekt. Man kan eventuelt sorteliste forskningsobjektet for jobben.

### Jobben stoppes, for så å startes igjen lenge etterpå slik at flere gjentakende perioder har passert
Vil kun føre til en stk ny bestilling per forskningsobjekt, ikke en stk per passerte periode.

### En bestillingsjobb bestiller samme skjematype som er satt som triggerskjema
Dette vil si gjentangende bestilling av samme skjematype (at svar på bestilling av skjematypen også vil trigge ny bestilling av samme skjematype). Denne vil foregå uendelig hvis man ikke har definert "Valg for å stoppe bestilling..". 
Man får ikke mulighet til å sette "Valg om bestillingen skal gjentas" hvis bestillingsskjematype og triggerskjematype er den samme typen, siden jobben vil gjenta seg selv allerede.

### Triggerskjema endres etter gjentagende bestilling er i gang
Eksisterende bestillinger blir ikke berørt, videre gjentagende bestillinger vi forholde seg til oppdaterte verdier på triggerskjemaet

# Teknisk: kjøring av jobb

Finn status for triggerskjemaer for tidspunkt **T**:
- Hent eksisterende ordrer som stammer fra bestillingsjobben
- Hent liste av triggerskjemaer (i henhold til definerte regler).
- Filtrer bort triggerskjemaer som har oppnådd sin maks antall ordrer (ikke gjentagende: 1, gjentagende: **Z**)
- For hvert triggerskjema (resultat her for hvert triggerskjema skal loggføres etter kjøring av jobb):
  - Sjekk om oppfyller regler for bestillingstidspunkt i forhold til tidspunkt **T**
    - Finn tidspunkt **A** eller forrige bestilling, sammenlignet med **X**
  - Sjekk om forskningsobjektet har trukket samtykke
  - Sjekk om forskningsobjektet er død
  - Sjekk om forskningsobjektet er sortelistet i jobb
  - Sjekk om forskningsobjektet har passert maks antall skjema (+ aktive bestillinger) av bestillingsskjematypen
- Resulterer i liste med
  - Triggerskjemaet
  - Om den skal føre til bestilling
  - Årsak til at den eventuelt ikke skal føre til bestilling (enum for hver årsak over)
  
Kjør Jobb:
- Hvis bestillingsskjematypen ikke har noen publiserte versjoner lenger, sett jobbstatus til stoppet og avbryt kjøringen
- Kjør bestilling for triggerskjemaene som skal føre til bestilling
