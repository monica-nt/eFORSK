# Person/pasient-håndtering

Integrasjon folkereg. 

## Samtykkehåndtering

Samtykket tilhører personen i registeret. Informasjonen ligger globalt, og gjelder alle skjema registrert på personen uansett enhet. Samtykket er altså det samme på tvers av alle enheter, og alle enheter kan oppdatere samtykket. Skjemaer knyttet på en person som ikke har gitt samtykke vil ikke sees av enheter høyere opp i tilgangstreet.

Konfigurasjon av registeret bestemmer hva som er personens standard samtykke-nivå ved opprettelse. 

### Samtykkenivåer

1. **Ikke forespurt** - man kan ikke registrere data på personen
2. **Ikke samtykket** - man kan ikke registrere data på personen. data allerede registrert på person blir slettet når dette samtykkenivået settes?
3. **Samtykke for enheten** (lokalt samtykke - bedre navn?) - data registrert blir kun synlig på den enheten det er registrert
4. **Samtykke for registeret** (Benevningen "Nasjonalt samtykke" blir nok feil å bruke i alle tilfeller?) - data registrert blir synlig oppover i tilgangstreet

### Samtykkekonfigurasjon

Hvert register kan konfigureres til å bruke en av følgende samtykkekonfigurasjoner:
1. samtykke håndteres utenfor registeret - man får da ikke spørsmål om samtykke ved registrering i registeret. Standard samtykkenivå for pasienten er da nivå **4**. Samtykke kan manuelt endres på pasienten.
2. samtykke håndteres utenfor registeret - man får da ikke spørsmål om samtykke ved registrering i registeret. Standard samtykkenivå for pasienten er da nivå **3**. Samtykke kan manuelt endres på pasienten.
3. samtykke håndteres med spørsmål til registrar i registeret - registrar må velge samtykkenivå ved opprettelse av første skjema på personen om dette allerede ikke er gjort. Det er mulighet for å gå inn på personen og gi/endre samtykke når som helst. Det er ikke mulig å opprette skjema på pasient før samtykkenivå er 3 eller 4.
4. samtykke bestille fra personen via PROMS, der et standard samtykkeskjema sendes ut fra registeret. Det vil finnes en knapp for å bestille dette på personens side i registeret, eller ved forsøk på å opprette skjema der samtykke ikke foreligger.
5. Kombinasjon av **3 og 4**. Registrar kan både gi samtykke manuelt eller ved å bestille fra PROMS.



