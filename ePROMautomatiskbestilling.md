# ePROM automatisk bestilling

Arbeidsdokument, forslag til funksjonalitet som skal støtte automatiske bestillinger.

# Oppsett av jobber

Man kan sette opp så mange automatiske bestillingsjobber man vil.

En automatisk bestilling må alltid grunne ut i fra et eksisterende skjema. Man kan for eksempel lage seg en registreringsskjematype for å inkludere personer i registeret, for videre å få trigget bestilling.

# Jobb

En jobb har en av følgende statuser:
* Kladd
* I test - Jobb er aktiv i testmodus
* Aktiv - kun denne statusen fører til bestillinger
* Stoppet

Hver jobb har følgende konfigurasjon:
* Hvilken ePROM aktivert skjematype som skal bestilles automatisk
* Hvilken skjematype skal trigge bestilling av ePROM, kalt "**triggerskjema**" (trenger ikke være foreldreskjematypen, hva som helst skal kunne trigge bestilling)
* Bestillingstidspunkt
  * X dager etter [opprettelse/første ferdigstillelse] av triggerskjema
  * Periodisk (gjentas for hver X dager)
    * Spesifiser max antall gjentakelser
  
    

