---
ms.date: 01/08/2020
keywords: DSC, Power shell, configuratie, installatie
title: DSC-pull-service
ms.openlocfilehash: cf2420e6889f63ac3b2859e5ee36fa888b728afc
ms.sourcegitcommit: 01c60c0c97542dbad48ae34339cddbd813f1353b
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/04/2020
ms.locfileid: "78278440"
---
# <a name="desired-state-configuration-pull-service"></a>Pull-service desired state Configuration

> [!IMPORTANT]
> De pull-server (Windows *-functie DSC-service*) is een ondersteund onderdeel van Windows Server, maar er zijn geen plannen om nieuwe functies of mogelijkheden aan te bieden. Het wordt aangeraden om te beginnen met het overschakelen van beheerde clients naar [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inclusief functies die verder gaan dan pull server op Windows Server) of een van de [hieronder vermelde Community](pullserver.md#community-solutions-for-pull-service)-oplossingen.

Local Configuration Manager (LCM) kan centraal worden beheerd door een pull-service oplossing. Wanneer u deze methode gebruikt, wordt het knoop punt dat wordt beheerd, geregistreerd bij een service en een configuratie toegewezen in de instellingen van de LCM. De configuratie en alle DSC-resources die nodig zijn als afhankelijkheden voor de configuratie, worden gedownload naar de computer en gebruikt door LCM voor het beheren van de configuratie. Informatie over de status van de computer die wordt beheerd, wordt geüpload naar de service voor rapportage. Dit concept wordt ' pull-service ' genoemd.

De huidige opties voor de pull-service zijn onder andere:

- Azure Automation desired state Configuration-service
- Een pull-service die wordt uitgevoerd op Windows Server
- Door de Community beheerde open-source-oplossingen
- Een SMB-share

De aanbevolen schaal voor elke oplossing is als volgt:

|                   Oplossing                   |              Client knooppunten              |
| -------------------------------------------- | -------------------------------------- |
| Windows pull-server met MDB/ESENT-data base | Maxi maal 500 knoop punten                        |
| Windows pull-server met SQL database       | Maxi maal 3500 knoop punten                       |
| Azure Automation DSC                         | Zowel kleine als grote omgevingen      |

**De aanbevolen oplossing**en de optie met de meeste beschik bare functies is [Azure Automation DSC](/azure/automation/automation-dsc-getting-started). Een bovengrens voor het aantal knoop punten per Automation-account is niet geïdentificeerd.

Met de Azure-service kunt u knoop punten on-premises beheren in particuliere data centers of in open bare Clouds, zoals Azure en AWS. Voor particuliere omgevingen waarbij servers niet rechtstreeks verbinding kunnen maken met internet, kunt u overwegen om uitgaand verkeer alleen te beperken tot het gepubliceerde Azure IP-bereik (Zie [IP-bereiken van Azure-data centers](https://www.microsoft.com/download/details.aspx?id=41653)).

De functies van de online service die momenteel niet beschikbaar zijn in de pull-service op Windows Server zijn:

- Alle gegevens worden versleuteld tijdens de overdracht en in rust
- Client certificaten worden automatisch gemaakt en beheerd
- Archief geheimen voor het centraal beheren van [wacht woorden/referenties](/azure/automation/automation-credentials)of [variabelen](/azure/automation/automation-variables) zoals server namen of verbindings reeksen
- De configuratie van het knoop punt [LCM](../managing-nodes/metaConfig.md#basic-settings) centraal beheren
- Configuraties centraal toewijzen aan client knooppunten
- Wijzigingen in de configuratie van ' Canarische groups ' vrijgeven voordat de productie wordt bereikt
- Grafische rapportage
  - Status Details op DSC-resource niveau granulatie
  - Uitgebreide fout berichten van client computers voor het oplossen van problemen
- [Integratie met Azure log Analytics](/azure/automation/automation-dsc-diagnostics) voor waarschuwingen, geautomatiseerde taken, Android/IOS-app voor rapportage en waarschuwingen

## <a name="dsc-pull-service-in-windows-server"></a>DSC-pull-service in Windows Server

Het is mogelijk om een pull-service te configureren om te worden uitgevoerd op Windows Server. U wordt aangeraden dat de pull-service oplossing die is opgenomen in Windows Server, alleen mogelijkheden bevat voor het opslaan van configuraties/modules voor het downloaden en vastleggen van rapport gegevens in een Data Base. Het bevat niet veel van de mogelijkheden die de service in Azure biedt, en is dus geen goed hulp programma voor het evalueren van de manier waarop de service wordt gebruikt.

De pull-service in Windows Server is een webservice in IIS die gebruikmaakt van een OData-interface om DSC-configuratie bestanden beschikbaar te maken voor doel knooppunten wanneer deze knoop punten hen vragen.

Vereisten voor het gebruik van een pull-server:

- Een server met:
  - WMF/Power Shell 4,0 of hoger
  - IIS-serverrol
  - DSC Service
- In het ideale geval wordt een certificaat gegenereerd voor het beveiligen van referenties die worden door gegeven aan de lokale Configuration Manager (LCM) op doel knooppunten

De beste manier om Windows Server te configureren voor het hosten van pull-service is het gebruik van een DSC-configuratie. Hieronder vindt u een voorbeeld script.

### <a name="supported-database-systems"></a>Ondersteunde database systemen

| WMF 4.0 |       WMF 5.0        |       WMF 5.1        | WMF 5,1 (Windows Server Insider preview 17090) |
| ------- | -------------------- | -------------------- | ---------------------------------------------- |
| EXTENSIE     | ESENT (standaard), MDB | ESENT (standaard), MDB | ESENT (standaard), SQL Server, MDB               |

Vanaf release 17090 van [Windows Server Insider preview](https://www.microsoft.com/software-download/windowsinsiderpreviewserver)is SQL Server een ondersteunde optie voor de pull-service (Windows-functie *DSC-service*). Dit biedt een nieuwe optie voor het schalen van grote DSC-omgevingen die niet zijn gemigreerd naar [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).

> [!NOTE]
> SQL Server ondersteuning wordt niet toegevoegd aan eerdere versies van WMF 5,1 (of eerder) en is alleen beschikbaar op Windows Server-versies die groter zijn dan of gelijk zijn aan 17090.

Als u de pull-server wilt configureren voor het gebruik van SQL Server, stelt u **SqlProvider** in op `$true` en **SqlConnectionString** op een geldige SQL Server verbindings reeks. Zie voor meer informatie [SqlClient-verbindings reeksen](/dotnet/framework/data/adonet/connection-string-syntax#sqlclient-connection-strings).
Voor een voor beeld van SQL Server configuratie met **xDscWebService**, lees dan eerst [met behulp van de xDscWebService-resource](#using-the-xdscwebservice-resource) en controleer vervolgens [Sample_xDscWebServiceRegistration_UseSQLProvider. ps1 op github](https://github.com/dsccommunity/xPSDesiredStateConfiguration/blob/master/source/Examples/Sample_xDscWebServiceRegistration_UseSQLProvider.ps1).

### <a name="using-the-xdscwebservice-resource"></a>De xDscWebService-Resource gebruiken

De eenvoudigste manier om een webpull-server in te stellen, is door gebruik te maken van de **xDscWebService** -resource die is opgenomen in de **xPSDesiredStateConfiguration** -module. In de volgende stappen wordt uitgelegd hoe u de resource gebruikt in een `Configuration` waarmee de webservice wordt ingesteld.

1. Roep de cmdlet [install-module](/reference/6/PowerShellGet/Install-Module.md) aan om de **xPSDesiredStateConfiguration** -module te installeren.

   > [!NOTE]
   > `Install-Module` is opgenomen in de **PowerShellGet** -module, die is opgenomen in power shell 5,0 en hoger.

1. Een SSL-certificaat voor de DSC-pull-server ophalen van een vertrouwde certificerings instantie, binnen uw organisatie of een open bare instantie. Het certificaat dat is ontvangen van de certificerings instantie is meestal in de PFX-indeling.
1. Installeer het certificaat op het knoop punt dat de DSC-pull-server wordt op de standaard locatie, dat moet worden `CERT:\LocalMachine\My`.
   - Noteer de vinger afdruk van het certificaat.
1. Selecteer een GUID die moet worden gebruikt als de registratie sleutel. Als u een rapport wilt genereren met Power shell, voert u het volgende in bij de PS-prompt en drukt u op ENTER: `[guid]::newGuid()` of `New-Guid`. Deze sleutel wordt gebruikt door client knooppunten als een gedeelde sleutel voor verificatie tijdens de registratie. Zie de sectie registratie sleutel hieronder voor meer informatie.
1. In het Power shell-ISE start (<kbd>F5</kbd>) het volgende configuratie script (opgenomen in de map van de **xPSDesiredStateConfiguration** -module als `Sample_xDscWebServiceRegistration.ps1`). Met dit script wordt de pull-server ingesteld.

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

1. Voer de configuratie uit, waarbij de vinger afdruk van het SSL-certificaat wordt door gegeven als de para meter **certificateThumbPrint** en een GUID-registratie sleutel als de para meter **RegistrationKey** :

    ```powershell
    # To find the Thumbprint for an installed SSL certificate for use with the pull server list all certificates in your local store
    # and then copy the thumbprint for the appropriate certificate by reviewing the certificate subjects
    dir Cert:\LocalMachine\my

    # Then include this thumbprint when running the configuration
    Sample_xDscWebServiceRegistration -certificateThumbprint 'A7000024B753FA6FFF88E966FD6E19301FAE9CCC' -RegistrationKey '140a952b-b9d6-406b-b416-e0f759c9c0e4' -OutputPath c:\Configs\PullServer

    # Run the compiled configuration to make the target node a DSC Pull Server
    Start-DscConfiguration -Path c:\Configs\PullServer -Wait -Verbose
    ```

#### <a name="registration-key"></a>Registratie sleutel

Als u client knooppunten wilt toestaan om te registreren bij de server, zodat ze configuratie namen kunnen gebruiken in plaats van een configuratie-ID, wordt een registratie sleutel die is gemaakt met de bovenstaande configuratie opgeslagen in een bestand met de naam `RegistrationKeys.txt` in `C:\Program Files\WindowsPowerShell\DscService`. De registratie sleutel functioneert als een gedeeld geheim dat wordt gebruikt tijdens de eerste registratie door de client met de pull-server. De client genereert een zelfondertekend certificaat dat wordt gebruikt om een unieke verificatie uit te dienen bij de pull-server zodra de registratie is voltooid. De vinger afdruk van dit certificaat wordt lokaal opgeslagen en gekoppeld aan de URL van de pull-server.

> [!NOTE]
> Registratie sleutels worden niet ondersteund in Power Shell 4,0.

Als u een knoop punt wilt configureren voor verificatie met de pull-server, moet de registratie sleutel zich in de-configuratie voor elk doel knooppunt bevindt dat wordt geregistreerd bij deze pull-server. Houd er rekening mee dat de **RegistrationKey** in de onderstaande meta configuratie wordt verwijderd nadat de doel computer is geregistreerd en dat de waarde moet overeenkomen met de waarde die is opgeslagen in het `RegistrationKeys.txt` bestand op de pull-server (' 140a952b-b9d6-406b-b416-e0f759c9c0e4 ' voor dit voor beeld). De registratie sleutel waarde altijd veilig behandelen, omdat een doel machine kan worden geregistreerd bij de pull-server.

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
> Met de sectie **ReportServerWeb** kunnen rapport gegevens naar de pull-server worden verzonden.

Het ontbreken van de eigenschap **ConfigurationID** in het meta configuratie bestand betekent impliciet dat de pull-server de v2-versie van het pull-server protocol ondersteunt, zodat er een eerste registratie nodig is. De aanwezigheid van een **ConfigurationID** betekent echter wel dat de V1-versie van het pull-server protocol wordt gebruikt en dat er geen registratie verwerking is.

> [!NOTE]
> In een PUSH scenario bestaat er een fout in de huidige release waardoor het nodig is om een eigenschap ConfigurationID te definiëren in het meta configuratie bestand voor knoop punten die nooit zijn geregistreerd bij een pull-server. Hiermee wordt het v1 pull server-protocol geforceerd en kunnen er geen registratie fout berichten worden geregistreerd.

## <a name="placing-configurations-and-resources"></a>Configuraties en resources plaatsen

Nadat de installatie van de pull-server is voltooid, worden in de mappen die zijn gedefinieerd door de eigenschappen **ConfigurationPath** en **para modulepath in** in de configuratie van de pull-server, de modules en configuraties geplaatst die beschikbaar zijn voor doel knooppunten die kunnen worden opgehaald. Deze bestanden moeten een specifieke indeling hebben zodat de pull-server deze op de juiste wijze kan verwerken.

### <a name="dsc-resource-module-package-format"></a>Pakket indeling voor DSC-resource module

Elke resource module moet een gezipte en een naam hebben volgens het volgende patroon `{Module Name}_{Module Version}.zip`.

Een module met de naam **xWebAdminstration** met een module versie van 3.1.2.0 krijgt bijvoorbeeld de naam `xWebAdministration_3.1.2.0.zip`. Elke versie van een module moet zich in één ZIP-bestand bevinden.
Omdat er slechts één versie van een resource in elk zip-bestand is, wordt de module-indeling die is toegevoegd in WMF 5,0 met ondersteuning voor meerdere module versies in één map niet ondersteund. Dit betekent dat voordat u DSC-resource modules inpakt voor gebruik met een pull-server, een kleine wijziging in de directory structuur moet worden aangebracht. De standaard indeling van modules met DSC-resource in WMF 5,0 is `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`. Voordat u de pull-server inpakt, verwijdert u de map **{module versie}** zodat het pad wordt `{Module Folder}\DscResources\{DSC Resource Folder}\`. Ga met deze wijziging naar de map die hierboven is beschreven en plaats deze zip-bestanden in de map **para modulepath in** .

Gebruik `New-DscChecksum {module zip file}` om een controlesom bestand te maken voor de zojuist toegevoegde module.

### <a name="configuration-mof-format"></a>MOF-indeling voor configuratie

Een configuratie-MOF-bestand moet worden gekoppeld aan een controlesom bestand zodat een LCM op een doel knooppunt de configuratie kan valideren. Als u een controlesom wilt maken, roept u de cmdlet [New-DscChecksum](/reference/6/PSDesiredStateConfiguration/New-DSCCheckSum.md) aan. De cmdlet neemt een para meter **Path** op die de map specificeert waarin de configuratie-MOF zich bevindt. De cmdlet maakt een controlesom bestand met de naam `ConfigurationMOFName.mof.checksum`, waarbij `ConfigurationMOFName` de naam is van het MOF-configuratie bestand. Als er meer dan één configuratie-MOF-bestanden in de opgegeven map zijn, wordt er een controlesom gemaakt voor elke configuratie in de map. Plaats de MOF-bestanden en de bijbehorende controlesom bestanden in de map **ConfigurationPath** .

> [!NOTE]
> Als u het MOF-configuratie bestand op een wille keurige manier wijzigt, moet u het controlesom bestand ook opnieuw maken.

### <a name="tooling"></a>Hulpprogramma's

De volgende hulpprogram ma's zijn opgenomen in de meest recente versie van de xPSDesiredStateConfiguration-module, zodat het instellen, valideren en beheren van de pull-server eenvoudiger wordt.

1. Een module die u helpt bij het inpakken van DSC-resource modules en configuratie bestanden die op de pull-server kunnen worden gebruikt.
   [PublishModulesAndMofsToPullServer. psm1](https://github.com/dsccommunity/xPSDesiredStateConfiguration/blob/master/source/Modules/DscPullServerSetup/DscPullServerSetup.psm1).
   Voor beelden:

    ```powershell
        # Example 1 - Package all versions of given modules installed locally and MOF files are in c:\LocalDepot
         $moduleList = @('xWebAdministration', 'xPhp')
         Publish-DSCModuleAndMof -Source C:\LocalDepot -ModuleNameList $moduleList

         # Example 2 - Package modules and mof documents from c:\LocalDepot
         Publish-DSCModuleAndMof -Source C:\LocalDepot -Force
    ```

1. Een script dat de pull-server valideert, is op de juiste wijze geconfigureerd. [PullServerSetupTests. ps1](https://github.com/dsccommunity/xPSDesiredStateConfiguration/blob/master/source/Modules/DscPullServerSetup/DscPullServerSetupTest/DscPullServerSetupTest.ps1).

## <a name="community-solutions-for-pull-service"></a>Community-oplossingen voor pull-service

De DSC-Community heeft meerdere oplossingen ontworpen om het pull-service protocol te implementeren. Voor on-premises omgevingen bieden deze pull-service mogelijkheden en een kans om een bijdrage te leveren aan de community met incrementele uitbrei dingen.

- [Tug](https://github.com/powershellorg/tug)
- [DSC-TRÆK](https://github.com/powershellorg/dsc-traek)

## <a name="pull-client-configuration"></a>Pull-client configuratie

In de volgende onderwerpen wordt beschreven hoe u pull-clients in detail instelt:

- [Een DSC-pull-client instellen met behulp van een configuratie-ID](pullClientConfigID.md)
- [Een DSC-pull-client instellen met behulp van configuratie namen](pullClientConfigNames.md)
- [Gedeeltelijke configuraties](partialConfigs.md)

## <a name="see-also"></a>Zie ook

- [Overzicht van desired state Configuration voor Windows Power shell](../overview/overview.md)
- [Configuraties doorvoeren](enactingConfigurations.md)
- [Een DSC-rapportserver gebruiken](reportServer.md)
- [[MS-DSCPM]: gewenst status configuratie pull model Protocol](https://docs.microsoft.com/openspecs/windows_protocols/ms-dscpm/ea744c01-51a2-4000-9ef2-312711dcc8c9)
- [[MS-DSCPM]: desired state Configuration pull model protocol errata](https://docs.microsoft.com/openspecs/windows_protocols/ms-winerrata/f5fc7ae3-9172-41e8-ac6a-2a5a5b7bfaf5)
