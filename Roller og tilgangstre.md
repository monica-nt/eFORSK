# Roller, tilgangstre

## Tilgangstre

Tilgangstreet  består av en hierarkisk liste over tilgangsenheter som kan logges inn på i registeret. En tilgangsenhet i tilgangstreet har tilgang til data registrert på seg selv, på barn, og videre arvinger nedover i hierarkiet. En tilgangsenhet kan ikke se data registrert på sin foreldre/forfedre oppover i hiearkiet. Høyere opp i tilgangstreet vil si tilgang til å se mer data, laverene ned vil begrense tilgangen til data.

En tilgangsenhet har ikke tilgang til å se data i kladd eller uten samtykke på tilgangsenheter nedover i hiearkiet.

Et register av enkleste form vil kun ha en tilgangsenhet å registrere data på, slik at registeret ikke trenger å ha noen kunskap om tilganger og hierarki.

## Roller

Ved innlogging må brukeren komme inn i registeret med en rolle.

* **Administrator** - brukt for å legge til og endre registre i løsningen
* **RegistryResponsible/Registeransvarlig** - ansvarlig for et spesifikk register. har tilgang til alle operasjoner
* **DataResponsible/Dataansvarlig** - kan se, opprette, gjenåpne, endre, slette, ferdigstille, returnere alles skjema
* **Registrar** - kan se, opprette, gjenåpne, endre, slette, ferdigstille eget skjema, kan se eksistens men ikke innhold av andres skjema
* **Reader/Leser** - kan kun lese data fra registeret, som skjemaer, dataeksport, metadata
* **ReaderUnidentified/LeserAnonymisert** - forskningsobjektets id og navn er sensurert

## Operasjoner

En rolle har tilgang til et sett med operasjoner

Liste utarbeides
