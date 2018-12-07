# Forskningsobjekter

Et skjema må registreres på et forskningsobjekt. Forskningsobjektene er kategorisert i typer. Som standard tilbyr eFORSK typen "Folkeregisteret" som gir personer fra folkeregisteret. I tillegg kan registre legge til sine egne typer, for eksempel legemidler, avdelinger, anonyme personer osv. På disse egenlagde typene må hvert forskningsobjekt registreres med en unik ID og et navn.

Når man lager en skjematype må man velge hvilken forskningsobjekttype som skjemaet er koblet til. Dette kan ikke endres i ettertid. Alle underskjema av skjematypen er låst til samme forskningsobjekttypen som hovedskjemaet.

Merk at kun skjematyper med forskningsobjekttypen "Folkeregisteret" kan kobles mot ePROM.

## Samtykkehåndtering

Gjelder kun for forskningsobjekt: personer fra folkeregisteret.

Samtykket tilhører personen i registeret. Informasjonen ligger globalt, og gjelder alle skjema registrert på personen uansett tilgangsenhet. Samtykket er altså det samme på tvers av alle tilgangsenheter, og alle enheter kan oppdatere samtykket. 

Konfigurasjon av registeret bestemmer hva som er personens standard samtykke-nivå ved opprettelse. 

### Samtykkenivåer

* **0. Ikke forespurt** - grunntilstand
* **1. Forespurt (ePROM)** - avventer svar. kan løpe ut på tid
* **2. Forespørsel utløpt (ePROM)** - antatt ikke samtykket
* **3. Ikke samtykket** - man kan ikke registrere data på personen. data allerede registrert på person blir slettet når dette samtykkenivået settes?
* **4. Trukket** - ikke mulig å endre *registeransvarlig vil i senere versjoner kanskje få tilgang til å endre dette*
* **5. Samtykket** 

Ved setting av 5. samtykket må man oppgi samtykkedato.
Samtykkenivået lagres med en dato for når det sist var endret. Endringer loggføres.

### Samtykkekonfigurasjon

Hvert register kan konfigureres til å bruke en av følgende samtykkekonfigurasjoner:

* **A.** samtykke settes med spørsmål til brukeren i registeret eller etterspørres automatisk ved bestilling av ePROM - bruker må velge samtykkenivå ved opprettelse av første skjema på personen om dette allerede ikke er gjort. Det er mulighet for å gå inn på personen og gi/endre samtykke når som helst. Det er ikke mulig å opprette skjema på pasient før samtykkenivå er **5**.
* **B.** samtykke håndteres utenfor registeret - man får da ikke spørsmål om samtykke ved registrering i registeret. Standard samtykkenivå for pasienten er da nivå **5**. Samtykke kan manuelt endres på pasienten.
* **C.** ikke aktuelt, hjemlet et annet sted

I tilfelle B eller C må administrator oppgi grunn til at samtykke håndteres utenfor registeret.

### Samtykke bestilling ePROM

Ved bestilling av ePROM vil eFORSK bestille et skjema som etterspør samtykke i tilfelle forskningsobjektet ikke har samtykke

### *Innsyn* (ikke implementert i første fase)

Via innsynsløsningen kan man velge å få sine data slettet. Dette setter samtykkenivået på til 4. som vil slette eksisterende data.
Todo
