# Roller, tilgangstre

## Tilgangstre

Tilgangstreet  består av en hierarkisk liste over tilgangsenheter som kan logges inn på i registeret. En tilgangsenhet i tilgangstreet har tilgang til data registrert på seg selv, på barn, og videre arvinger nedover i hierarkiet. En tilgangsenhet kan ikke se data registrert på sin foreldre/forfedre oppover i hiearkiet. Høyere opp i tilgangstreet vil si tilgang til å se mer data, laverene ned vil begrense tilgangen til data.

En tilgangsenhet har ikke tilgang til å se data i kladd eller uten samtykke på tilgangsenheter nedover i hiearkiet.

Et register av enkleste form vil kun ha en tilgangsenhet å registrere data på, slik at registeret ikke trenger å ha noen kunskap om tilganger og hierarki.

## Roller

Ved innlogging må brukeren komme inn i registeret med en rolle. Her beskrives rollene og hvilke operasjoner disse har tilgang til.

**Administrator** 
Dette er en administrativ rolle for å fasilitere registre i applikasjonen.
* Registre i applikasjonen: lese, opprette og endre
* Registeroppsettet: endre (hvis innlogget på et register)
* Tilgangsenheter: lese, opprette og endre (hvis innlogget på et register)
* Skjematyper: lese (hvis innlogget på et register)
* Forskningsobjekttyper: lese (hvis innlogget på et register)
* Status på integrasjoner: sjekke status (oppe/nede)
* ePROM skjemaer: lese hvilke registre som har ePROM skjemaer som trenger gjennomgang (godkjennelse/avslag)
* ePROM godkjennelse: godkjenne/avslå ePROM skjemaer (hvis innlogget på et register)

**Registeransvarlig** (RegistryResponsible)
Denne rollen har full tilgang til å administrere og bruke et register.
* Registeroppsettet: endre
* Tilgangsenheter: lese, opprette og endre
* Skjematyper: lese, opprette, endre, slette
* Forskningsobjekttyper: lese, opprette, endre
* Egne skjema: lese, opprette, endre, slette, ferdigstille og returnere
* Andres skjema: lese, opprette, endre, slette, ferdigstille og returnere
* Forskningsobjekter: lese identifisert, opprette, endre, sette samtykke
* ePORM: bestille, lese bestillinger

**Dataansvarlig** (DataResponsible) - kan se, opprette, gjenåpne, endre, slette, ferdigstille, returnere alles skjema
**Registrar** - kan se, opprette, gjenåpne, endre, slette, ferdigstille eget skjema, kan se eksistens men ikke innhold av andres skjema
**Leser** (Reader) - kan kun lese data fra registeret, som skjemaer, dataeksport, metadata
**LeserAnonymisert** (ReaderUnidentified) - forskningsobjektets id og navn er sensurert

## Operasjoner

En rolle har tilgang til et sett med operasjoner

Liste utarbeides
