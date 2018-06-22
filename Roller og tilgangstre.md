# Roller & tilgangstre

## Tilgangstre

Tilgangstreet  består av en hierarkisk liste over enheter som kan logges inn på i registeret. En enhet i tilgangstreet har tilgang til data registrert på seg selv, på barn, og videre arvinger nedover i hierarkiet. En enhet kan ikke se data registrert på sin foreldre/forfedre oppover i hiearkiet.

*Hvis samtykkehåndtering implementeres en gang: En enhet har ikke tilgang til å se data på enheter nedover i hiearkiet hvis samtykke ikke er gitt.*

Et register av enkleste form vil kun ha en enhet å registrere data på, slik at registeret ikke trenger å ha noen kunskap om tilganger og hierarki.

## Roller

Ved innlogging må brukeren komme inn i registeret med en rolle.

* **Administrator** - brukt for å legge til og endre registre i løsningen
* **RegistryResponsible** - ansvarlig for et spesifikk register. har tilgang til alle operasjoner
* *Registrar* - kan registrere data inn i et spesifikk register
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
