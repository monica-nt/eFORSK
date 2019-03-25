# ePROM automatisk bestilling

Arbeidsdokument, forslag til funksjonalitet som skal støtte automatiske bestillinger.

# Oppsett av jobber

Som registeransvarlig kan man i administrasjonen sette opp så mange automatiske bestillingsjobber man vil.

En automatisk bestillingsjobb må alltid grunne ut i fra et eksisterende skjema (**triggerskjema**). Man kan for eksempel lage seg en registreringsskjematype for å inkludere forskningsobjekter i registeret, for videre å få trigget automatiske bestillinger.

En automatisk bestillingsjobb vil opprette planlagte bestillinger basert på reglene.

# Jobb

En jobb har en av følgende statuser:
* **Stoppet** - Eventuelt eksisterende planlagte bestillinger kanselleres.
* **Aktiv i testmodus** - Jobb kjøres i testmodus. Eventuelt eksisterende planlagte bestillinger i ikke-testmodus kanselleres. 
* **Aktiv** - jobb kjøres også i ikke-testmodus

Konfigurasjon:
* **Triggerskjematype**: Hvilken skjematype (uansett versjonsnummer) skal trigge bestilling av ePROM (trenger ikke være foreldreskjematypen, hvilken som helst type skal kunne trigge bestilling av hvilken som helst type). Kan ikke endres etter opprettelse av jobb. Regler **R** for at triggerskjemaet fører til en bestilling:
  * Skjemastatuser
  * **X** dager etter **A**=(opprettelse/første ferdigstillelse(default)/siste endring) av triggerskjema
  * Triggerskjema opprettet etter dato **D** (default dagens dato for å hindre at jobben fyrer mange bestillinger ved opprettelse)
  * Verdier på skjemaet?
  
* **Bestillingsskjematype**: Hvilken ePROM aktivert skjematype (+ versjonnummer) som skal bestilles automatisk. Bestiller default høyeste publiserte versjonsnummer. Kan ikke endres etter opprettelse av jobb.
  * Hvis bestillingsskjematype er en tilknyttet skjematype og triggerskjematypen ikke er foreldretypen til bestillingsskjematypen - må det opplyses om at foreldreskjema vil opprettes som kladd ved mottatt svar. (kan evt videreutvikles så den plasseres på sist opprettede foreldreskjema hvis det finnes)

 * **Bestillingsvalg**: Valg om bestillingen skal gjentas (gjentas da for hver **X** dager spesifisert i forrige punkt. Kan ikke spesifiseres hvis bestillingsskjematype og triggerskjemastype er den samme typen, da denne allerede blir gjentagende)
   * Spesifiser max antall gjentakelser (**Z**)
   * Valg om gjentakelse krever svar på forrige bestilling i rekken (default = ja)
* Antall utløpsdager
* Antall dager før purring
* Valg for å stoppe bestilling
  * Hvis forskningsobjektet allerede har **Y** antall skjemaer (eller aktive bestillinger) av bestillingsskjematypen (uavhengig av versjonsnummer) på forskningsobjektet. Y er default 1 for ikke gjentagende bestillinger, og default Z i tilfelle gjentagende bestillinger - men kan overstyres.
  * *Forskningsobjekt sorteliste* (utgår da man kan kansellere en planlagt bestilling?)
  
Hver bestilling og hvert skjemasvar fra bestillingen vil merkes med den automatiske bestillingsjobbens ID for sporing.

Bestillinger som planlegges vil aldri bestilles mindre enn en time(?) etter opprettelse, slik at brukeren har mulighet til å oppdage eventuelle feil i regler og stoppe jobben.

Vis ePROM bestillinger som er planlagt (for jobben) inne på automatisk jobb.

# Scenarier

### Skjema bestilles manuelt før den automatiske jobben kjører
Har man ikke konfigurert "Valg for å stoppe bestilling hvis det allerede finnes Y antall skjemaer" vil ny bestilling kjøres, og man har da flere bestillinger på samme forskningsobjekt. Man kan eventuelt manual kansellere en planlagt bestilling.

### Jobben stoppes, for så å startes igjen lenge etterpå slik at flere gjentakende perioder har passert
Vil kun føre til en stk ny bestilling per forskningsobjekt, ikke en stk per passerte periode.

### En bestillingsjobb bestiller samme skjematype som er satt som triggerskjema
Dette vil si gjentangende bestilling av samme skjematype (at svar på bestilling av skjematypen også vil trigge ny bestilling av samme skjematype). Denne vil foregå uendelig hvis man ikke har definert "Valg for å stoppe bestilling..". 
Man får ikke mulighet til å sette "Valg om bestillingen skal gjentas" hvis bestillingsskjematype og triggerskjematype er den samme typen, siden jobben vil gjenta seg selv allerede.

### Triggerskjema endres etter gjentagende bestilling er i gang
Eksisterende utførte bestillinger blir ikke berørt, videre gjentagende bestillinger vi forholde seg til oppdaterte verdier på triggerskjemaet

# Teknisk

Velger her annen strategi enn MRS. MRS kjører nattlig igjennom jobbene for å bestille skjema direkte. Bakdelen med dette er at alle potensielle triggerskjema må gås igjennom hver eneste natt (tung operasjon), og man vet ikke hvilke skjema som vil bestilles fremover i tid før faktisk jobb er kjørt.

eFORSK vil ta den tunge operasjonen med å gå igjennom alle skjema ved lagring av automatisk jobb (altså stor jobb en gang, kontra hver eneste natt). Ved hver endring på forskningsobjektets skjema vil jobbene gås igjennom igjen kun for dette forskningsobjektet. Fordelen er at tung operasjon kun kjøres sjelden. Videre fordel er at man vil se planlagte bestillinger fremover i tid, det gjør det lettere å avdekke feil i jobbregler for brukeren. Bakdelen er at det er kodemessig vanskeligere å sykronisere planlagte bestilliger ved endring på forskningsobjektets skjemaer.

## Finn potensielle triggerskjemaer

Ved endring av jobb, vil alle triggerskjema gås igjennom (tungt). (lås redigering av jobb mens dette kjøres, via AsyncJob)
- Finn alle triggerskjema som oppfyller regler **R**. Grupper på unike forskningsobjekt => **Sjekk forskningsobjekt**

Ved endring av triggerskjema (create, update, return, delete) vil det async gås gjennom jobber for triggerskjematypen og oppdatere fremtidige bestillinger i kontekst av ekisterende bestillinger.  => **Sjekk forskningsobjekt**

Ved create på bestillingsskjematypen (fått svar på bestilling, kan trigge neste bestilling) vil det async gås gjennom jobber for dens triggerskjematype på samme forskningsobjekt => **Sjekk forskningsobjekt**

## Sjekk forskningsobjekt

- Hent alle ePROM bestilling for forskningsobjektet.
- Hent alle skjema for forskningsobjektet.
- Finn alle triggerskjema av disse (uansett jobb)

For hvert triggerskjema:
- Stopp hvis triggerskjemaet har oppnådd sin maks antall ordrer (ikke gjentagende: 1, gjentagende: **Z**)
- Stopp hvis forskningsobjektet har trukket samtykke
- Stopp hvis forskningsobjektet er død
- Finn tidspunkt for neste bestilling
- Sjekk eksisterende planlagte bestillinger
  - Fjern hvis forskningsobjektet vil passere maks antall skjema av bestillingsskjematypen
  - Oppdatert eksisterende hvis avvik
  - Opprett nye planlagte bestillinger hvis mangler
  

# Utvidelser

- EPromFormOrderStatus
  - scheduled (planlagt)
  - cancelled
  
- PromFormOrder
  - automaticjobID
  - nullable 

