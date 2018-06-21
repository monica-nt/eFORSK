# PROMS integrasjon

## Opprettelse

Ved ferdigstillelse av en versjon som er konfigurert for å ha PROMS skjema, vil skjemaet opprettes og publiseres i PROMS via API og knyttes til versjonen. 
Man kan overstyre opprettelse av nytt PROMS skjema ved å gi en GUID til eksisterende publisert PROMS skjema.

*Import av eksisterende skjema fra PROMS, og samleskjemafunksjonalitet er ikke planlagt støttet i første omgang - men slike skjema i PROMS kan benyttes hvis man overstyrer GUID som forklart over*

## Bestilling av utfylling

Ved opprettelse av et nytt skjema kan man enten fylle det ut i applikasjonen eller bestille det utfylt fra pasient. 

*Det bør på sikt lages et grensesnitt for å kunne massebestille skjema ved å gi inn en liste med fødselsnummer. Vil kun kunne gjøres hvis skjemaet er et hovedskjema. For underskjema må man inn på hver enkelt pasient og bestille på korrekt skjema.*
