# Kodemiljø

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

Bygg så løsningen på nytt med den nye migration. Kjør så databasetool med parameter -u
