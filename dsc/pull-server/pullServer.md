---
ms.date: 03/04/2019
keywords: DSC, powershell, configuratie en installatie
title: DSC-pull-service
ms.openlocfilehash: 3cb2ca09111100f39589072a0d8e7010f9188efb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079401"
---
# <a name="desired-state-configuration-pull-service"></a>Desired State Configuration Pull Service

> [!IMPORTANT]
> De Pull-Server (Windows-functie *DSC-Service*) is een ondersteunde onderdeel van Windows Server maar er zijn geen plannen om nieuwe functies en mogelijkheden bieden. Het verdient aanbeveling om te beginnen met het overstappen clients beheerd [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inclusief functies dan Pull-Server op Windows Server) of een van de community-oplossingen die zijn opgenomen [hier](pullserver.md#community-solutions-for-pull-service).

Local Configuration Manager kan centraal worden beheerd door een Pull-Service-oplossing.
Wanneer u deze methode gebruikt, is het knooppunt dat wordt beheerd geregistreerd bij een service en een configuratie-instellingen LCM toegewezen.
De configuratie en alle DSC-resources die nodig zijn als de afhankelijkheden voor de configuratie zijn gedownload naar de machine en gebruikt door LCM om de configuratie te beheren.
Informatie over de status van de machine wordt beheerd, is geüpload naar de service voor rapportage.
Dit concept wordt aangeduid als 'pull-service'.

De huidige opties voor het pull-service zijn onder andere:

- Azure Automation Desired State Configuration service
- Een pull-service die wordt uitgevoerd op Windows Server
- Community onderhouden open-source-oplossingen
- Een SMB-share

**De aanbevolen oplossing**, en de optie met de meeste functies die beschikbaar zijn, is [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).

De Azure-service kan knooppunten on-premises beheren in persoonlijke datacenters of in openbare clouds, zoals Azure en AWS.
Voor persoonlijke omgevingen waar servers kunnen niet rechtstreeks verbinding met Internet maken, kunt u overwegen uitgaand verkeer naar de gepubliceerde Azure IP-bereik beperken (Zie [Azure Datacenter IP-adresbereiken](https://www.microsoft.com/en-us/download/details.aspx?id=41653)).

Functies van de online service die niet op dit moment beschikbaar zijn in de pull-service op Windows Server zijn onder andere:

- Alle gegevens worden versleuteld in-transit en inactieve
- Clientcertificaten worden gemaakt en automatisch beheerd
- Geheimen opslaan voor het beheren van centraal [wachtwoorden/referenties](/azure/automation/automation-credentials), of [variabelen](/azure/automation/automation-variables) , zoals namen of verbindingsreeksen
- Centraal beheren knooppunt [LCM configureren](../managing-nodes/metaConfig.md#basic-settings)
- Centraal configuraties toewijzen aan client-knooppunten
- Release-configuratie wordt gewijzigd naar 'canary groepen' voor het testen alvorens productie
- Grafische rapportage
  - Details van de status op het niveau van de DSC-resource van granulariteit
  - Uitgebreide foutberichten van clientcomputers voor het oplossen van problemen
- [Integratie met Azure Log Analytics](/azure/automation/automation-dsc-diagnostics) voor waarschuwingen, geautomatiseerde taken Android/iOS-app voor rapportage en meldingen

## <a name="dsc-pull-service-in-windows-server"></a>DSC-pull-service in Windows Server

Het is mogelijk om een pull-service uit te voeren op Windows Server te configureren.
Er rekening mee dat de pull-serviceoplossing is opgenomen in Windows Server alleen mogelijkheden bevat van het opslaan van configuraties/modules downloaden en het vastleggen van gegevens in database.
Deze omvatten geen veel van de mogelijkheden die door de service in Azure en is dus niet een goed hulpmiddel voor het evalueren van hoe de service kan worden gebruikt.

De pull-service die wordt aangeboden in Windows Server is een webservice in IIS die gebruikmaakt van een OData-interface om beschikbaar te doelknooppunten als deze knooppunten voor DSC-configuratiebestanden maken.

Vereisten voor het gebruik van een pull-server:

- Een server met:
  - WMF/PowerShell 4.0 of hoger
  - IIS-serverrol
  - DSC Service
- In het ideale geval sommige betekent dat voor het genereren van een certificaat voor het beveiligen van referenties die zijn doorgegeven aan de lokale Configuration Manager (LCM) op de doelknooppunten

De beste manier om Windows Server configureren voor host pull-service is het gebruik van een DSC-configuratie.
Hieronder vindt u een voorbeeldscript.

### <a name="supported-database-systems"></a>Ondersteunde databasesystemen

|WMF 4.0   |WMF 5.0  |WMF 5.1 |WMF 5.1 (Windows Server Insider Preview 17090)|
|---------|---------|---------|---------|
|MDB     |ESENT (Default), MDB |ESENT (Default), MDB|ESENT (standaard), SQL Server, MDB

Vanaf de release 17090 van [Windows Server Insider Preview](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewserver), SQL Server is een ondersteunde optie voor het Pull-Service (Windows-functie *DSC-Service*). Dit biedt een nieuwe optie voor het schalen van grote DSC-omgevingen die nog niet zijn gemigreerd naar [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).

> [!NOTE]
> Ondersteuning van SQL Server wordt niet naar de vorige versie van WMF 5.1 (of eerder) toegevoegd en is alleen beschikbaar op Windows Server-versies groter is dan of gelijk zijn aan 17090.

Voor het configureren van de pull-server voor het gebruik van SQL Server, stelt **SqlProvider** naar `$true` en **SqlConnectionString** naar een geldige SQL Server-verbindingsreeks. Zie voor meer informatie, [SqlClient verbindingsreeksen](/dotnet/framework/data/adonet/connection-string-syntax#sqlclient-connection-strings).
Voor een voorbeeld van SQL Server-configuratie met **xDscWebService**, eerst lezen [met behulp van de resource xDscWebService](#using-the-xdscwebservice-resource) en bekijk [Sample_xDscWebServiceRegistration_ UseSQLProvider.ps1 op GitHub](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/Examples/Sample_xDscWebServiceRegistration_UseSQLProvider.ps1).

### <a name="using-the-xdscwebservice-resource"></a>Met behulp van de resource xDscWebService

De eenvoudigste manier voor het instellen van een web-pull-server is met de **xDscWebService** resource, opgenomen in de **xPSDesiredStateConfiguration** module.
De volgende stappen wordt uitgelegd over het gebruik van de resource in een configuratie waarvoor u de webservice stelt.

1. Roep de [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet voor het installeren van de **xPSDesiredStateConfiguration** module.
   > [!NOTE]
   > **Install-Module** is opgenomen in de **PowerShellGet** module die is opgenomen in PowerShell 5.0. U kunt downloaden de **PowerShellGet** -module voor PowerShell 3.0 en 4.0 op [PackageManagement PowerShell-Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).
2. Een SSL-certificaat voor de DSC-Pull-server ophalen van een vertrouwde certificeringsinstantie, zich binnen uw organisatie of een openbare CA. Het certificaat dat is ontvangen van de instantie is meestal in de PFX-indeling.
3. Installeer het certificaat op het knooppunt dat de DSC-Pull-server op de standaardlocatie bevindt, die moet worden `CERT:\LocalMachine\My`.
   - Noteer de certificaatvingerafdruk van het.
4. Selecteer een GUID moet worden gebruikt als de registratiesleutel. Voor het genereren van een met behulp van PowerShell, typ het volgende bij de PS-prompt en druk op enter: `[guid]::newGuid()` of `New-Guid`. Deze sleutel worden door knooppunten van de client gebruikt, dus als een gedeelde sleutel voor verificatie tijdens de registratie. Zie de sectie registratiesleutel hieronder voor meer informatie.
5. Start in de PowerShell ISE (F5) het volgende configuratiescript (opgenomen in de map met voorbeelden van de **xPSDesiredStateConfiguration** module als `Sample_xDscWebServiceRegistration.ps1`). Met dit script stelt u de pull-server.

    ```powershell
    configuration Sample_xDscWebServiceRegistration
    {
        param
        (
            [string[]]$NodeName = 'localhost',

            [ValidateNotNullOrEmpty()]
            [string] $certificateThumbPrint,

            [Parameter(HelpMessage='This should be a string with enough entropy (randomness) to protect the registration of clients to the pull server.  We will use new GUID by default.')]
            [ValidateNotNullOrEmpty()]
            [string] $RegistrationKey   # A guid that clients use to initiate conversation with pull server
        )

        Import-DSCResource -ModuleName PSDesiredStateConfiguration
        Import-DSCResource -ModuleName xPSDesiredStateConfiguration

        Node $NodeName
        {
            WindowsFeature DSCServiceFeature
            {
                Ensure = "Present"
                Name   = "DSC-Service"
            }

            xDscWebService PSDSCPullServer
            {
                Ensure                  = "Present"
                EndpointName            = "PSDSCPullServer"
                Port                    = 8080
                PhysicalPath            = "$env:SystemDrive\inetpub\PSDSCPullServer"
                CertificateThumbPrint   = $certificateThumbPrint
                ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
                ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
                State                   = "Started"
                DependsOn               = "[WindowsFeature]DSCServiceFeature"
                RegistrationKeyPath     = "$env:PROGRAMFILES\WindowsPowerShell\DscService"
                AcceptSelfSignedCertificates = $true
                UseSecurityBestPractices     = $true
                Enable32BitAppOnWin64   = $false
            }

            File RegistrationKeyFile
            {
                Ensure          = 'Present'
                Type            = 'File'
                DestinationPath = "$env:ProgramFiles\WindowsPowerShell\DscService\RegistrationKeys.txt"
                Contents        = $RegistrationKey
            }
        }
    }
    ```

6. Voer de configuratie, geven de vingerafdruk van het SSL-certificaat als de **certificateThumbPrint** parameter en de registratie van een GUID-sleutel als de **RegistrationKey** parameter:

    ```powershell
    # To find the Thumbprint for an installed SSL certificate for use with the pull server list all certificates in your local store
    # and then copy the thumbprint for the appropriate certificate by reviewing the certificate subjects
    dir Cert:\LocalMachine\my

    # Then include this thumbprint when running the configuration
    Sample_xDscWebServiceRegistration -certificateThumbprint 'A7000024B753FA6FFF88E966FD6E19301FAE9CCC' -RegistrationKey '140a952b-b9d6-406b-b416-e0f759c9c0e4' -OutputPath c:\Configs\PullServer

    # Run the compiled configuration to make the target node a DSC Pull Server
    Start-DscConfiguration -Path c:\Configs\PullServer -Wait -Verbose
    ```

#### <a name="registration-key"></a>Registratiesleutel

Als u wilt toestaan client knooppunten om u te registreren bij de server, zodat ze namen in plaats van een configuratie-ID gebruiken kunnen, een registratiesleutel die is gemaakt door de bovenstaande configuratie is opgeslagen in een bestand met de naam `RegistrationKeys.txt` in `C:\Program Files\WindowsPowerShell\DscService`. De registratiesleutel fungeert als een gedeeld geheim dat is gebruikt tijdens de registratie door de client met de pull-server. De client genereert een zelfondertekend certificaat dat wordt gebruikt voor een unieke verificatie naar de pull-server wanneer de registratie is voltooid. De vingerafdruk van dit certificaat wordt lokaal opgeslagen en die zijn gekoppeld aan de URL van de pull-server.

> [!NOTE]
> Registratiesleutels worden niet ondersteund in PowerShell 4.0.

Als u wilt configureren op een knooppunt om te verifiëren met de pull-server, moet de registratiesleutel in de metaconfiguration voor elk doelknooppunt dat zal worden geregistreerd met deze pull-server. Houd er rekening mee dat de **RegistrationKey** in de onderstaande metaconfiguration wordt verwijderd nadat de doel-VM heeft geregistreerd, en dat de waarde moet overeenkomen met de waarde die is opgeslagen de `RegistrationKeys.txt` -bestand op de pull-server (' 140a952b-b9d6-406b-b416-e0f759c9c0e4' in dit voorbeeld). Altijd net zo behandelt de waarde van de registratie-sleutel veilig, omdat wetenschap dat deze een doel-VM om te registreren bij de pull-server kunt.

```powershell
[DSCLocalConfigurationManager()]
configuration Sample_MetaConfigurationToRegisterWithLessSecurePullServer
{
    param
    (
        [ValidateNotNullOrEmpty()]
        [string] $NodeName = 'localhost',

        [ValidateNotNullOrEmpty()]
        [string] $RegistrationKey, #same as the one used to set up pull server in previous configuration

        [ValidateNotNullOrEmpty()]
        [string] $ServerName = 'localhost' #node name of the pull server, same as $NodeName used in previous configuration
    )

    Node $NodeName
    {
        Settings
        {
            RefreshMode        = 'Pull'
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL          = "https://$ServerName`:8080/PSDSCPullServer.svc" # notice it is https
            RegistrationKey    = $RegistrationKey
            ConfigurationNames = @('ClientConfig')
        }

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL       = "https://$ServerName`:8080/PSDSCPullServer.svc" # notice it is https
            RegistrationKey = $RegistrationKey
        }
    }
}

Sample_MetaConfigurationToRegisterWithLessSecurePullServer -RegistrationKey $RegistrationKey -OutputPath c:\Configs\TargetNodes
```

> [!NOTE]
> De **ReportServerWeb** sectie kan rapportagegegevens worden verzonden naar de pull-server.

Het ontbreken van de **ConfigurationID** eigenschap in het bestand metaconfiguration impliciet betekent dat pull-server ondersteunt de V2-versie van het protocol voor pull-server, zodat een eerste registratie vereist is.
Daarentegen de aanwezigheid van een **ConfigurationID** betekent dat de V1-versie van de pull-server-protocol wordt gebruikt en er geen registratie-verwerking is.

> [!NOTE]
> In een PUSH-scenario bestaat een bug in de huidige release die nodig is voor het definiëren van een eigenschap ConfigurationID in het bestand metaconfiguration voor knooppunten die nooit hebt geregistreerd met een pull-server. Dit wordt het protocol V1-Pull-Server dwingen en te voorkomen dat foutberichten van inschrijving.

## <a name="placing-configurations-and-resources"></a>Het plaatsen van configuraties en resources

Nadat de pull server setup is voltooid, de mappen die zijn gedefinieerd door de **ConfigurationPath** en **ModulePath** eigenschappen in de configuratie van de pull-server zijn waar u plaatst modules en configuraties dat zijn beschikbaar voor de doelknooppunten om op te halen.
Deze bestanden moeten zich in een specifieke indeling in volgorde van de pull-server deze correct kan verwerken.

### <a name="dsc-resource-module-package-format"></a>Indeling van de DSC-resource-module-pakket

Elke resource-module moet worden ingepakt en met de naam op basis van het volgende patroon `{Module Name}_{Module Version}.zip`.

Bijvoorbeeld, een module met de naam xWebAdminstration met de moduleversie van een van 3.1.2.0 naam `xWebAdministration_3.2.1.0.zip`.
Elke versie van een module moet worden opgenomen in een enkel zip-bestand.
Omdat er slechts één versie van een resource in het zipbestand, wordt de indeling van de module toegevoegd in WMF 5.0 met ondersteuning voor meerdere moduleversies in één map wordt niet ondersteund.
Dit betekent dat voordat verpakking van DSC-resource-modules voor gebruik met pull-server moet u een kleine wijziging aanbrengen in de mapstructuur.
De standaardnotatie van modules met DSC-resource in WMF 5.0 is `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`.
Verwijderen voordat u de pakketten voor de pull-server, de **{moduleversie}** map, zodat het pad wordt `{Module Folder}\DscResources\{DSC Resource Folder}\`.
Met deze wijziging, zip-de map, zoals hierboven beschreven en plaats deze zip-bestanden in de **ModulePath** map.

Gebruik `New-DscChecksum {module zip file}` een controlesom-bestand voor de toegevoegde module te maken.

### <a name="configuration-mof-format"></a>Indeling van de MOF-configuratie

Een MOF-configuratiebestand moet worden gekoppeld aan een bestand controlesom zodat een LCM op een doelknooppunt kan de configuratie valideren.
Aanroepen voor het maken van een controlesom, de [New-DscChecksum](/powershell/module/PSDesiredStateConfiguration/New-DscChecksum) cmdlet.
De cmdlet voert een **pad** parameter waarmee de map waarin de configuratie van de MOF zich bevindt.
De cmdlet maakt een controlesom-bestand met de naam `ConfigurationMOFName.mof.checksum`, waarbij `ConfigurationMOFName` is de naam van de mof-configuratiebestand.
Als er meer dan één configuratie MOF-bestanden in de opgegeven map, wordt een controlesom gemaakt voor elke configuratie in de map.
Plaats het MOF-bestanden en de bijbehorende controlesom-bestanden in de **ConfigurationPath** map.

> [!NOTE]
> Als u het MOF-configuratiebestand op geen enkele manier wijzigt, moet u ook het bestand controlesom opnieuw maken.

### <a name="tooling"></a>Hulpprogramma 's

Om de instelling gezamenlijk, valideren en het beheren van de eenvoudiger, pull-server de volgende hulpprogramma's zijn opgenomen als voorbeelden in de meest recente versie van de module xPSDesiredStateConfiguration:

1. Een module die helpt bij het verpakken van DSC-resource-modules en configuratiebestanden voor gebruik op de pull-server.
   [PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).
   Voorbeelden:

    ```powershell
        # Example 1 - Package all versions of given modules installed locally and MOF files are in c:\LocalDepot
         $moduleList = @('xWebAdministration', 'xPhp')
         Publish-DSCModuleAndMof -Source C:\LocalDepot -ModuleNameList $moduleList

         # Example 2 - Package modules and mof documents from c:\LocalDepot
         Publish-DSCModuleAndMof -Source C:\LocalDepot -Force
    ```

1. Een script dat de pull-server valideert is correct geconfigureerd. [PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).

## <a name="community-solutions-for-pull-service"></a>Community-oplossingen voor Pull-Service

De DSC-community heeft meerdere oplossingen voor het implementeren van de pull-service-protocol worden samengesteld.
Voor on-premises omgevingen bieden deze mogelijkheden voor pull-service en de mogelijkheid om bij te dragen naar de community met incrementele verbeteringen.

- [Tug](https://github.com/powershellorg/tug)
- [DSC-TRÆK](https://github.com/powershellorg/dsc-traek)

## <a name="pull-client-configuration"></a>Configuratie van de pull-client

De volgende onderwerpen wordt het instellen van pull-clients in detail beschreven:

- [Instellen van een DSC-pull-client met behulp van een configuratie-ID](pullClientConfigID.md)
- [Instellen van een DSC-pull-client met behulp van configuratienamen](pullClientConfigNames.md)
- [Gedeeltelijke configuraties](partialConfigs.md)

## <a name="see-also"></a>Zie ook

- [Windows PowerShell Desired State Configuration-overzicht](../overview/overview.md)
- [Configuraties doorvoeren](enactingConfigurations.md)
- [Een DSC-rapportserver gebruiken](reportServer.md)
- [[MS-DSCPM]: Desired State Configuration Pull Model Protocol](https://msdn.microsoft.com/library/dn393548.aspx)
- [[MS-DSCPM]: Desired State Configuration Pull Model Protocol Errata](https://msdn.microsoft.com/library/mt612824.aspx)
