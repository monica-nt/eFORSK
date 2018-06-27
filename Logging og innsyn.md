# Logging og innsyn

## Logging

Logging skal sørge for total sporbarhet over hva som har skjedd i applikasjonen. Logger skal ikke inneholde sensitiv data.

To typer logging:
* ServerLog (logger til windows event log, plukkes opp av splunk o.l.)
* ApplicationLog (logger til applikasjonens egen database, samtidig også til ServerLog)

ServerLog brukes for det meste til å logge kjøring av bakgrunnsjobber og feil i applikasjonen.
ApplicationLog brukes for å logge brukerhandlinger i applikasjonen.

### Teknisk

Objekter som skal logges implementerer et interface IAppLogObject som gir informasjon til loggeren

Tabell:
* Id (int)
* Username (nvarchar(255))  - hvem som utførte handlingen
* Timestamp (DateTime) - når det skjedde
* Object (nvarchar(255)) - navn på objektet som logges (eks. FormData)
* ObjectId (int?) - id til objektet, i tilfelle int
* ObjectGuid (guid?) - id til objektet, i tilfelle guid
* Action (nvarchar(255)) - handlingen som utføres (eks. Create, Save, Delete, View)
* DataJson (nvarchar(max)) - evt ekstra data om loggoppføringen

## Innsyn

En person skal kunne spørre applikasjonen om den har data om personen,  hvilke data og kunne be om å få seg slettet. Sletting blir håndtert av samtykkesystemet.
todo
