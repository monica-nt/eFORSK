# Skjemasystemet

Skjemasystemet definerer hvordan skjemaer kan lages.
Dette er en videreutvikling av hvordan skjemaer løst i ePROM og MRS (spesielt fleksible felter). Mulighetene kan ikke overgå hva ePROM tilbyr, da skjemaene må støtte oversettelse til PROMS-format.

## Definisjon av skjemaer

### Skjematyper (FormType)
Hvert register kan opprette så mange skjematyper dem ønsker.
*En skjematype kan definere å være tilknyttet en annen skjematype. Et skjema av denne skjematypen sies da å være et tilknyttet skjema av dens hovedskjema. Et hovedskjema må være tilstede for at et tilknyttet skjematype skal kunne opprettes*

**Tabellstruktur**
* Id (int)
* ParentId (int?)
* Name
* Delete (bool)

### Skjemaversjon (FormVersion)
En skjematype har alltid en versjon. Disse gies løpende numre. En skjematype kan kun ha en versjon i status kladd samtidig. Denne må publiseres, og eventuelt tilbaketrekkes, før man kan opprette en ny kladd. En ny versjon er alltid basert på sin forrige versjon. Man kan ha flere samtidige aktive versjoner (ved utfyllelse av et skjema må man da velge hvilken versjon man vil fylle ut). Man har mulighet til å slette en versjon i kladd. En versjon som er publisert kan aldri slettes, men kan trekkes tilbake (avpubliseres).

En skjemaversjon kommer med en skjemadesigner hvor man kan flytte rundt på felter, legge til nye felt, og deprekere eksisterende felt. Man har et felt for å plassere "skjulte felter", hvor metadata ligger som standard.

**Tabellstruktur**
* FormTypeId (int)
* VersionNumber  (int)
* Name
* Status (draft,published,withdrawn,deleted) <- Versjoner kan slettes hvis den er den nyeste versjonen i kladd
* FormDesignJson (nvarchar(max))  <- parent/child og rekkefølger av felter 
* PromsActivated (bool)
* PromsConfigJson (nvarchar(max))
  * PromsPaperActivated (bool) - manuell proms
  * PromsId (guid?)
	* (..)
	
**Hjelpemetoder**
* CanHaveProms()   - kan ikke ha proms hvis:
	*  et felt av typen randomisering eksisterer 
  
### Felt (FormField)
Et skjemafelt kan kun opprettes **og endres** i en versjon med status kladd. Så fort versjonen er publisert, kan man i etterfølgende versjoner kun velge og deprekere (deaktivere) feltet (for godt). Brukeren kan selv lage et kodenavn (kolonneoverskrift i datadump) for feltet, dette må være unikt for skjematypen. Merk at man aldri kan ta i bruk kodenavnet igjen på andre felt i skjematypen selv om det på et tidspunkt blir deprekert.

**Tabellstruktur**
* Id (int)
* FormTypeId (int)
* FieldTypeId (int)
* FromVersionNumber (int)
* ToVersionNumber (int?)
* CodeName (nvarchar(50)) <- brukerdefinert kodenavn, kan ikke endres etter at versjonen er ferdigstilt
* DisplayName (nvarchar(255)) <- visningsnavnet for feltet ved utfylling av skjema
* HelpText
* AutoFieldRef (nvarchar(50)) <- om feltet skal tilegnes verdi automatisk ved lagring. feltet inneholder referanse til autofeltets ID, f.eks. PatientAge. Feltet blir da automatisk readonly ved utfyllelse.
* SortIndex (int)
* Deleted (bool) <- Properties can be deleted from the version they are created on when version is not active yet
* ConfigurationJson (nvarchar(max)) <- spesifikk konfigurasjon for felttypen
	* ..
	
### Skjemaregel (FormRule)
Skjemaregler omfavner både validerings- og vis/skjul-regler. Skjemaregler kan på lik linje med felter opprettes på en versjon, og deprekeres i senere versjoner. 

Regler som støttes er:
* Vis felt hvis _
* Skjul felt hvis _
* Tall: Mindre enn _
* todo..

**Tabellstruktur**
* Id (int)
* FormTypeId (int)
* FromVersionNumber (int)
* ToVersionNumber (int?)
* RuleTypeId (int)
* OwnerFieldId (int?)
* TargetFieldsJson (JSON representasjon av int[])
* ConfigurationJson (nvarchar(max)) <- json med regel-data
* Deleted (bool)

### FeltType (FieldType)
En felttype må velges når man oppretter et felt. 

Felttyper som støttes er:
* Tallfelt
	* Konfigurering:
		* Visning: tall/slider
		* Enhet
		* Antall desimaler (0,1,2,3,4)
		* Minimumsverdi
		* Maksimumsverdi
	* Valideringsregler:
		* Påkrevd
		* Mindre enn
		* Mindre enn eller lik
		* Mindre enn annet felt
		* Mindre enn eller lik annet felt
		* Større enn
		* Større enn eller lik
		* Større enn annet felt
		* Større enn eller lik annet felt
* Avkrysningsfelt
	* Ingen konfigurering eller valideringsregler
* Dato/*tid* - kun dato støttes i ePROM
	* Konfigurering
		* Vsining: dato, *datotid*, *månedår*, *år*
	* Valideringsregler
		* Påkrevd
		* Må være fortid
		* Må være fremtid
		* Må være før annet datofelt
		* Må være før eller samtidig som annet datofelt
		* Må være etter annet datofelt
		* Må være etter eller samtidig som annet datofelt
* Tekstfelt 
	* Konfigurering
		* Visning: string, tekstarea
	* Valideringsregler
		* Påkrevd
* Valgfelt (radio eller nedtrekssliste)
	* Konfigurering
		* Visning: radio, select, groupedselect
		* Svaralternativer (verdi, tekst, gruppering)
	* Valideringsregler
		* Påkrevd
* Randomisering (som valgfelt, men annen visning i GUI)
	* Konfigurering
		* Svaralternativer (verdi, tekst, gruppering)
	* Valideringsregler
		* Påkrevd

**Objektstruktur**
* Id (int)
* Navn
* todo..

### AutoFelt
*Foreløbig på idestadiet.*
Tanken er at man kan legge på felt som automatisk fylles ut/kalkuleres ved opprettelse og lagring, som ikke kan fylles ut eller endres av brukeren, eksempel på dette er:
* Skjema-metadata: Id, MainFormId, FormTypeId, PersonId, FormVersionId, UnitId, Status... (legges til som felt på skjematypen automatisk, men skjult fra grensesntitt ved utfyllelse)
* Pasientalder
* Kjønn
* Postnummer, *Poststed*, Bydelsnr, kommunenr, *kommunenavn* (i forhold til skjemadato), gjeldende kommunenr
* Enhetsnavn, Helseenhetsnavn, Helseenhets-kortnavn, Sykehusnavn, HF, RHF (i forhold til UnitId)
* Randomisert-gruppe
* *Felter fra hovedskjema* (må vurdere hva som gjøres når feltene i hovedskjemaet oppdateres)
* todo..

Autofelt blir tilgjengeliggjort for en bestemt felttype. For eksempel blir pasientalder tilgjengelig for tallfelt.

## Utfyllelse av skjemaer

### Skjemadata (FormData)
Dette er et utfylt skjema

**Tabellstruktur**
* Id (guid)
* MainFormId (guid?)
* IsTest (bool) - om skjemaet tilhører testmodus
* FormTypeId (int)
* PersonId (guid?)
* FormVersionId (int)
* UnitId (int)
* ImportSessionId (int?)
* Status (draft,closed,deleted,returned)
* Created
* CreatedBy
* Updated
* UpdatedBy
* FormDate
* PropertyDataJson (nvarchar(max))
	* key-value liste av UniqueName - verdi

## Testmodus
Man kan i grensesnittet hoppe mellom testmodus og produksjonsmodus av registeret når man vil. Dette for å teste skjemaer, opplæring, demonstrering eller øve seg på utfyllelse. Man vil i testmodus ikke se skjemaer fra prodmodus, og omvendt. Pasientene i testmodus hentes fra testfolkeregisteret.
