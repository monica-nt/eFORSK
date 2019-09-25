# Hendelsesovervåking - løsningsforslag

Databaseansvarlig kan i administrasjon opprette hendelsesovervåkinger. Hendelser trigger varsel.

## Typer overvåking

#### Skjema

En skjematype velges.

Skjemadatastatuser velges (ferdigstilt, til kontroll, monitorert).

Kan sette opp OG + ELLER regler for hvilke verdier som skal trigge varsler.
(samme OG ELLER system som for automatiske ePROM bestillinger, videreutvikle og standardiser)

#### ePROM bestilling statusendring

En ePROM aktivert skjematype velges.

Eventuelt konfigurasjon av hvilke notifikasjonskanaler som overvåkes.

Ordrestatus velges.

Varsel gis hvis en bestilling av gitt konfigurasjon når denne ordrestatusen.

*Eksempel 1: overvåke når det kommer et personinitisert svar*

*Eksempel 2: overvåke når en bestilling har utløpt*

## Konfigurasjon

I tillegg til konfigurasjon spesifisert per type varsel, kan også følgende spesifiseres:

Navn (brukes ved varsling)

Aktiv i testmodus
Aktiv

Hvem skal varsles: Man kan velge blant dem som har logget seg på databasen. Hver enkelt kan supplementeres med e-post og telefonnummer for å få varsel til de kanalene. Hver bruker vil få sitt eget varsel. Selv om den ene har sjekket ut varselet, vil det ennå være aktivt for den andre.

## Varsling om hendelse

Det varsles i eFORSKs interne varslingssystem. 
På sikt kan man i tillegg velge epost og SMS varsling i tillegg, der man kan gi en liste over adresser/numre som skal motta varsel. Separat liste for testmodus og ikke testmodus.


## Overvåking

Lytter på oppdatering av skjema og oppdatering av eprom bestillinger. 
Oppretter et hendelsesvarsel. Hver oppsatte bruker får da sin egen varsling som lenker til hendelsesvarselet.
Køes.
