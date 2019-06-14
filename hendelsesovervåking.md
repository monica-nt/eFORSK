# Hendelsesovervåking - løsningsforslag

Databaseansvarlig kan i administrasjon opprette hendelsesovervåkinger. Hendelser trigger varsel.

## Typer overvåking

#### Skjemaverdier

En skjematype velges.

Overvåker ferdigstilte skjemaer av typen.

Kan sette opp OG + ELLER regler for hvilke verdier som skal trigge varsler.
(samme OG ELLER system som for automatiske ePROM bestillinger, videreutvikle og standardiser)

#### Skjemastatus

En skjematype velges.

En skjemadatastatus velges (ferdigstilt, til kontroll, monitorert).

Varsel gis når det kommer en nytt skjema med denne statusen.

#### ePROM bestilling statusendring

En ePROM aktivert skjematype velges.

Eventuelt konfigurasjon av hvilke notifikasjonskanaler som overvåkes.

Ordrestatus velges.

Varsel gis hvis en bestilling av gitt konfigurasjon når denne ordrestatusen.

*Eksempel 1: overvåke når det kommer et personinitisert svar*

*Eksempel 2: overvåke når det en bestilling har utløpt*

## Varsel

Det varsles i eFORSKs interne varslingssystem. 
På sikt kan man i tillegg velge epost og SMS varsling i tillegg, der man kan gi en liste over adresser/numre.

## Overvåking

Nattlig jobb?
