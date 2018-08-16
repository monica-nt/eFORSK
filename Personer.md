# Person/pasient-håndtering

Integrasjon folkereg. 

## Samtykkehåndtering

Hvert register kan konfigureres til en av følgende samtykkesystem:
1. samtykke håndteres utenfor registeret - man får da ikke spørsmål om samtykke ved registrering i registeret
2. samtykke må foreligge på personen før man kan registrere skjema
3. samtykke må foreligge for at skjemaet skal bli synlig oppover i tilgangstreet (standard samtykke på nye pasienter er satt til "samtykke for enheten")

Det er definert fire nivå av samtykke (i tilfelle samtykkesystem 2,3):
1. **Ikke forespurt** - man kan ikke registrere data på personen
2. **Ikke samtykket** (kan også være trukket) - man kan ikke registrere data på personen. data allerede registrert blir slettet ved fjerning av samtykke?
3. **Samtykke for enheten** (lokalt samtykke - bedre navn?) - data registrert blir kun synlig på den enheten det er registrert
4. **Samtykke for registeret** (Benevningen "Nasjonalt samtykke" blir nok feil å bruke i alle tilfeller?) - data registrert blir synlig oppover i tilgangstreet

Samtykket tilhører personen i registeret. Informasjonen ligger globalt, og gjelder alle skjema registrert på personen uansett enhet. Samtykket er altså det samme på tvers av alle enheter, og alle enheter kan oppdatere samtykket. Skjemaer knyttet på en person som ikke har gitt samtykke vil ikke sees av enheter høyere opp i tilgangstreet.

Konfigurasjon av registeret bestemmer hva som er personens standard samtykke-nivå ved opprettelse. 
