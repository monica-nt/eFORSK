# Roller, tilgangstre og samtykke

## Tilgangstre

Tilgangstreet  består av en hierarkisk liste over tilgangsenheter som kan logges inn på i registeret. En tilgangsenhet i tilgangstreet har tilgang til data registrert på seg selv, på barn, og videre arvinger nedover i hierarkiet. En tilgangsenhet kan ikke se data registrert på sin foreldre/forfedre oppover i hiearkiet. Høyere opp i tilgangstreet vil si tilgang til å se mer data, laverene ned vil begrense tilgangen til data.

En tilgangsenhet har ikke tilgang til å se data uten samtykke på tilgangsenhet nedover i hiearkiet.

Et register av enkleste form vil kun ha en tilgangsenhet å registrere data på, slik at registeret ikke trenger å ha noen kunskap om tilganger og hierarki.

## Samtykkehåndtering

Det er definert tre nivå av samtykke:

1. **Ikke samtykket** (kan også være trukket) - man kan ikke registrere data på personen. data allerede registrert blir slettet ved fjerning av samtykke?
2. **Lokalt samtykke** - data registrert blir kun synlig på den enheten det er registrert
3. **Nasjonalt samtykke** (bedre navn? er nødvendig ikke snakk om "nasjon") - data registrert blir synlig oppover i tilgangstreet

Samtykket tilhører personen i registeret. Informasjonen ligger globalt, og gjelder alle skjema registrert på personen uansett enhet. Samtykket er altså det samme på tvers av alle enheter, og alle enheter kan oppdatere samtykket. Skjemaer knyttet på en person som ikke har gitt samtykke vil ikke sees av enheter høyere opp i tilgangstreet.

Konfigurasjon av registeret bestemmer hva som er personens standard samtykke-nivå ved opprettelse. 

## Roller

Ved innlogging må brukeren komme inn i registeret med en rolle.

* **Administrator** - brukt for å legge til og endre registre i løsningen
* **RegistryResponsible** - ansvarlig for et spesifikk register. har tilgang til alle operasjoner
* *RegistrarLimited* - kan registrere data inn i et spesifikk register, kan kun endre, slette, ferdigstille egne skjema, kan ikke se innhold i andres skjema
* *Registrar* - kan registrere data inn i et spesifikk register, kan kun gjenåpne, endre, slette, ferdigstille egne skjema, kan se innhold i andres skjema
* *RegistrarExtended* - kan registrere data inn i et register, kan også gjenåpne, endre, slette, ferdigstille andres skjema
* *Reader?* - kan hun hente lese data fra registeret, som skjemaer, datadump osv

Skal vi ha roller for anonym lese?

## Operasjoner

En rolle har tilgang til et sett med operasjoner

* **EditRegister** - opprette og redigere registre i løsningen
* **SeePersonIdentifiableData** - se fødselsnummer og pasientinformasjon
* **EditFormType** - opprette og redigere skjemaertyper
* **OrderProms**
* **EditForm** - opprette og redigere skjema
* todo..
