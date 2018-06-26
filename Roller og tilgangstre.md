# Roller, tilgangstre og samtykke

## Tilgangstre

Tilgangstreet  består av en hierarkisk liste over tilgangsenheter som kan logges inn på i registeret. En tilgangsenhet i tilgangstreet har tilgang til data registrert på seg selv, på barn, og videre arvinger nedover i hierarkiet. En tilgangsenhet kan ikke se data registrert på sin foreldre/forfedre oppover i hiearkiet. Høyere opp i tilgangstreet vil si tilgang til å se mer data, laverene ned vil begrense tilgangen til data.

En tilgangsenhet har ikke tilgang til å se data uten samtykke på tilgangsenhet nedover i hiearkiet.

Et register av enkleste form vil kun ha en tilgangsenhet å registrere data på, slik at registeret ikke trenger å ha noen kunskap om tilganger og hierarki.

## Samtykkehåndtering

Registreres data i registeret på en person antas det at det foreligger samtykke for dette allerede. Samtykkehåndtering i registeret vil si om en person samtykker i at data registrert på seg blir synlig oppover i tilgangstreet.

Samtykket tilhører personen i registeret. Informasjonen ligger globalt, og gjelder alle skjema registrert på personen uansett enhet. Samtykket er altså det samme på tvers av alle enheter, og alle enheter kan oppdatere samtykket. Skjemaer knyttet på en person som ikke har gitt samtykke vil ikke kun sees av enheter høyere opp i tilgangstreet.

## Roller

Ved innlogging må brukeren komme inn i registeret med en rolle.

* **Administrator** - brukt for å legge til og endre registre i løsningen
* **RegistryResponsible** - ansvarlig for et spesifikk register. har tilgang til alle operasjoner
* *Registrar* - kan registrere data inn i et spesifikk register
* LimitedRegitrar
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
