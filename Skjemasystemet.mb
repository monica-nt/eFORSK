# Skjemasystemet

# Skjematyper
Hvert register kan opprette så mange skjematyper dem ønsker.
*En skjematype kan definere å være tilknyttet en annen skjematype. Et skjema av denne skjematypen sies da å være et tilknyttet skjema av dens hovedskjema. Et hovedskjema må være tilstede for at et tilknyttet skjematype skal kunne opprettes*

**Data**
* Id (int)
* ParentId (int?)
* Navn

# Skjemaversjon
En skjematype har alltid en versjon. Disse gies løpende nummre. En skjematype kan kun ha en stk versjon i status kladd. Denne må publiseres, og eventuelt tilbaketrekkes, før man kan opprette en ny kladd. En ny versjon er alltid basert på sin forrige versjon. Man kan ha flere samtidige aktive versjoner, ved opprettelse av et skjema må man velge hvilken versjon man vil fylle ut. Man har mulighet til å slette en versjon i kladd. En versjon som er publisert kan aldri slettes, men kan trekkes tilbake (avpubliseres).

**data**
* FormTypeId (int)
* VersionId  (int)
* Name
* Status (draft,published,withdrawn,deleted) <- Versjoner kan slettes hvis den er den nyeste versjonen i kladd
* FormDesignJson (nvarchar(max))  <- parent/child og rekkefølger av felter 
* PromsActivated (bool)
* PromsConfigJson (nvarchar(max))
  * PromsPaperActivated (bool) - manuell proms
  * PromsId (guid?)
	* (..)
  
# Felt
Et skjemafelt kan kun opprettes **og endres** i en versjon med status kladd. Så fort versjonen er publisert, kan man i etterfølgende versjoner kun velge og deprekere (deaktivere) feltet (for godt). Brukeren kan selv lage et kodenavn (kolonneoverskrift i datadump) for feltet, dette må være unikt for skjematypen. Merk at man aldri kan ta i bruk kodenavnet igjen på andre felt i skjematypen selv om det på et tidspunkt blir deprekert.

**data**
* UniqueName (nvarchar(16)) <- generert unikt, brukes i kode/database som nøkkel og aldri eksponert for brukeren
* CodeName (nvarchar(50)) <- brukerdefinert kodenavn, kan ikke endres etter at versjonen er ferdigstilt
* DisplayName (nvarchar(255)) <- visningsnavnet for feltet ved utfylling av skjema
* FormTypeId (int)
* FromVersionId (int)
* ToVersionId (int?)
* PropertyTypeId (int)
* SortIndex (int) <- kun for datadump, feltet har sin egen rekkefølge i FormVersion sin FormDesign. Denne må vurderes.
* Deleted (bool) <- Properties can be deleted from the version they are created on when version is not active yet
* ConfigurationJson (nvarchar(max)) <- spesifikk konfigurasjon for felttypen

# Skjemaregel
Skjemaregler omfavner både validerings- og vis/skjul-regler. Skjemaregler kan på lik linje med felter opprettes på en versjon, og deprekeres i senere versjoner. 

**data**
* UniqueName (nvarchar(16)) <- generert unik 
* FormTypeId (int)
* FromVersionId (int)
* ToVersionId (int?)
* RuleType (show,hide,validation-warning,(validation-dismissable,)validation-required)
* FormPropertyId1 (int?)
* FormPropertyId2 (int?)
* RuleData (nvarchar(max)) <- json med regel-data
