# ePROM integrasjon

## Krav til api støtte
* Hente ut skjemadef
* Opprette skjemaer

## Opprettelse av skjematype

Ved ferdigstillelse av en versjon som er konfigurert for å ha ePROM skjema, vil skjemaet opprettes og publiseres i ePROM via API og knyttes til versjonen. 
Man kan overstyre opprettelse av nytt ePROM skjema ved å gi en GUID til eksisterende publisert ePROM skjema, men man er da selv ansvarlig for at felter og regler stemmer overens.

Konfigurasjonsvalg for ePROM på en skjemaversjon:
* PromsActivated (bool) - Skal ha ePROM 
* PromsPaperActivated (bool) - Skal ha støtte for papirutsendelse (her må det defineres en manuell kvalitetssikringprosess) 
* PromsGuidOverrided (bool) - man angir ePROM guid manuelt, og ePROM skjema opprettes ikke automatisk ved ferdigstillelse av skjemaversjon
* PromsGuid (Guid) - Guid til skjemaet i ePROM
* PromsExpireDays (int) - antall dager før bestillingen går ut på dato
* PromsReminderDays (int?) - antall dager før purring på svar sendes
* *PromsSideView (bool) - sidevisning i ePROM skjema*
* *PromsHideProgressBar (bool) - skjul progressbar*
* *PromsSignature (bool) - skjemaet må signeres i ePROM*

*Det er også funksjonalitet for å importere en komplett skjematype fra ePROM. Dette kan gjøres via et importgrensesnitt som lister ut fellesskjemaer fra ePROM, samt registerets egne publiserte skjemaer. Ved import får man en skjematype med en ferdig publisert versjon (for å sikre at felter og regler ikke tukles med på registersiden, som kan føre til tap av data). Er ePROM sitt skjema et samleskjema, vil dette gå tilbake i registeret som bare ett skjema. Det er ingen konsept om samleskjema i denne applikasjonen.*

## Bestilling av utfylling

Ved opprettelse av et nytt skjema kan man enten fylle det ut i applikasjonen eller bestille det utfylt fra pasient. 

*Det bør på sikt lages et grensesnitt for å kunne massebestille skjema ved å gi inn en liste med fødselsnummer. Vil kun kunne gjøres hvis skjemaet er et hovedskjema. For underskjema må man inn på hver enkelt pasient og bestille på korrekt skjema.*
