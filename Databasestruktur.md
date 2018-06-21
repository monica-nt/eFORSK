# Databasestruktur

Applikasjonen består av flere databaser. En felles database (**Common**) og en egen database tilegnet hver enkelt register i løsningen. En **databasetool** vil sørge for å opprette databasene som trenges. 

Registerdatabasene opprettes ut i fra en **keys** fil (keys.xml, fil med krypteringsnøkler). Keysfila har en pool av tilgjengelige keys koblet mot en ID. 

Hoveddatabasen "Common" inneholder oversikten over alle registrene i løsningen. Ved opprettelse av et nytt register, vil det plukkes en ledig ID fra keys fila - og forhåndsgenerert database tas i bruk.

*Varsel bør gis når det er mindre enn X antall ledige databaser i superadmingrensesnittet*
