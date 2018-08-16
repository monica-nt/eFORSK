# Kodemiljø

Kode skrives på engelsk. Følger standarder til Resharper, Angular/TS

## Verktøyoppsett

VS:
npm task runner: https://marketplace.visualstudio.com/items?itemName=MadsKristensen.NPMTaskRunner 
Hvis VS klager på for gammel node versjon: https://stackoverflow.com/questions/43849585/update-node-version-in-visual-studio-2017

## Prosjektoppsett

todo!

1. Bygg løsningen
2. Kjør setup.ps1
   * Registrerer event logging
   * Kjører databasetool
  
## Databaseendringer

Åpne packe manager console, og velg 'Default project' eFORSK.Service.Data.

Husk å bygg løsningen først slik at alle endringer er kompilert.

For å oppdatere Common database:  
PM> Update-Database -ConfigurationTypeName CommonMigrationsConfiguration  
PM> Add-Migration navn-på-endringene -ConfigurationTypeName CommonMigrationsConfiguration

For å oppdatere Registry database:  
PM> Update-Database -ConfigurationTypeName RegistryMigrationsConfiguration  
PM> Add-Migration navn-på-endringene -ConfigurationTypeName RegistryMigrationsConfiguration

Bygg så løsningen på nytt med den nye migration. Kjør så databasetool med parameter: 
-p=E:\VSTS\eFORSK\eFORSK.Service -u
