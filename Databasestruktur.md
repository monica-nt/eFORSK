# Databasestruktur :floppy_disk:

Applikasjonen består av flere databaser. En felles database (**Common**) og en egen database tilegnet hver enkelt register i løsningen. En **databasetool** vil sørge for å opprette databasene som trenges. 

Registerdatabasene opprettes ut i fra en **keys** fil (keys.xml, fil med krypteringsnøkler). Keysfila har en pool av tilgjengelige keys koblet mot en registryId. 

Hoveddatabasen "Common" inneholder oversikten over alle registrene i løsningen. Ved opprettelse av et nytt register, vil det plukkes en ledig ID fra keys fila - og forhåndsgenerert database tas i bruk.

*Varsel bør gis når det er mindre enn X antall ledige databaser i administratorgrensesnittet*

## Keys

Løsningen må ha en beskyttet keys.xml fil med en pool av nøkler for kryptering. Denne er på formen:

```
<?xml version="1.0" encoding="utf-8"?>
<EncryptionKeys>
	<!-- Test register -->
	<EncryptionKey registryId="1" key="EF5CE55D3CB361374A0E0F6D47B21712" />
	
	<!-- Register pool -->
	<EncryptionKey registryId="101" key="02EF90F07052644745452F041D44077C" />
  (..)
</EncryptionKeys>
```

Keysfila må alltid ha en oppføring for registryId = 1, da dette er standard testenhet for alle installasjoner.
