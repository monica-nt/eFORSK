# Roller, tilgangstre

## Tilgangsenheter
Tilgangsenhetene er en hierarkisk liste over enheter man kan logges inn på i databasen. En tilgangsenhet har tilgang til data registrert på seg selv, på barn, og videre arvinger nedover i hierarkiet. En tilgangsenhet kan ikke se data registrert på sin foreldre (og forfedre) oppover i hiearkiet. Tilgang høyere opp i tilgangstreet vil si tilgang til å mer data, tilgang laverene ned vil begrense tilgangen til data.

En tilgangsenhet har ikke tilgang til å se data i kladd tilgangsenheter nedover i hiearkiet. Data må ferdigstilles eller være til kontroll for at dem skal være synlig på andre enn tilgangsenheten dem er opprettet på.

En database av enkleste form vil kun ha en stykk tilgangsenhet, man trenger da ikke å ha noen kunnskap om tilganger og hierarki.

## Roller

Ved innlogging må brukeren komme inn i databasen med en rolle. Her beskrives rollene og hvilke operasjoner disse har tilgang til.

**Administrator**

Dette er en administrativ rolle for å fasilitere registre i applikasjonen.
* Registre i applikasjonen: lese, opprette og endre
* Registeroppsett: endre (hvis innlogget på et register)
* Tilgangsenheter: lese, opprette og endre (hvis innlogget på et register)
* Skjematyper: lese (hvis innlogget på et register)
* Forskningsobjekttyper: lese (hvis innlogget på et register)
* Status på integrasjoner: sjekke status (oppe/nede)
* ePROM skjemaer: lese hvilke registre som har ePROM skjemaer som trenger gjennomgang (godkjennelse/avslag)
* ePROM godkjennelse: godkjenne/avslå ePROM skjemaer (hvis innlogget på et register)

**Ansvarlig** (RegistryResponsible)

Dette er den øverste rollen i en database. Denne har full tilgang, og som eneste rolle kan den endre registerinnstillinger og bygge skjematyper.
* Registeroppsett: endre
* Tilgangsenheter: lese, opprette og endre
* Skjematyper: lese, opprette, endre, slette
* Forskningsobjekttyper: lese, opprette, endre
* Egne skjema: lese, opprette, endre, slette, ferdigstille og returnere
* Andres skjema: lese, endre, slette, ferdigstille og returnere
* Forskningsobjekter: lese identifisert, opprette, endre, sette samtykke
* ePROM: bestille, lese bestillinger
* Dokumenter: opprette, lese
* Rapporter: skjematype metadata, eksportere data

**Dataansvarlig** (DataResponsible)

Denne rollen har full tilgang rundt datainnsamlingen/databehandlingen, men kan ikke administrere registeret (eksempelvis ikke lage eller endre skjematyper)
* Egne skjema: lese, opprette, endre, slette, ferdigstille og returnere
* Andres skjema: lese, endre, slette, ferdigstille og returnere
* Forskningsobjekter: lese identifisert, opprette, endre, sette samtykke
* ePROM: bestille, lese bestillinger
* Dokumenter: opprette, lese
* Rapporter: skjematype metadata, eksportere data

**Registrar** 

Dette er en begrenset datainnsamlingsrolle, som ikke kan se data på andres skjemaer.
* Egne skjema: lese, opprette, endre, slette, ferdigstille 
* Andres skjema: se eksistensen av skjema, ikke lese data
* Forskningsobjekter: lese identifisert, opprette, endre, sette samtykke
* ePROM: bestille, lese bestillinger
* Dokumenter: opprette, lese
* Rapporter: skjematype metadata, eksportere data

**Leser** (Reader)

Kan kun lese data fra registeret, kan ikke tilføye ny data.
* Egne skjema: lese
* Andres skjema: lese
* Forskningsobjekter: lese identifisert
* ePROM: lese bestillinger
* Dokumenter: lese
* Rapporter: skjematype metadata, eksportere data

**LeserAnonymisert** (ReaderUnidentified)

Som Leser-rollen, men skal ikke se identifiserbar data.
* Egne skjema: lese
* Andres skjema: lese
* Forskningsobjekter: lese uidentifisert
* ePROM: lese bestillinger
* Dokumenter: lese
* Rapporter: skjematype metadata, eksportere data
