---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: Gedeeltelijke configuraties van PowerShell Desired State Configuration
ms.openlocfilehash: b2b17e35597707eb97ecdcea9dda4466deeab0cb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079520"
---
# <a name="powershell-desired-state-configuration-partial-configurations"></a>Gedeeltelijke configuraties van PowerShell Desired State Configuration

_Van toepassing op: Windows PowerShell 5.0 en hoger._

In PowerShell 5.0 kunt Desired State Configuration (DSC) configuraties moeten worden geleverd in fragmenten en uit meerdere bronnen. De lokale Configuration Manager (LCM) op het doelknooppunt wordt de fragmenten samen geplaatst voordat u deze als een configuratie voor één toepast. Op deze manier kunt delen van de controle van de configuratie tussen teams of personen. Bijvoorbeeld, als twee of meer teams van ontwikkelaars aan een service samenwerken, ze mogelijk elke wilt configuraties voor het beheren van hun onderdeel van de service maken. Elk van deze configuraties kan worden opgehaald uit verschillende pull-servers en ze in verschillende stadia van de ontwikkeling kunnen worden toegevoegd. Gedeeltelijke configuraties kunnen ook verschillende personen of teams voor het beheren van verschillende aspecten van het configureren van knooppunten zonder voor de coördinatie van het bewerken van een configuratie voor één document. Bijvoorbeeld, kan één team zijn verantwoordelijk voor het implementeren van een virtuele machine en het besturingssysteem, terwijl een ander team zou kunnen voor andere toepassingen en services op deze VM implementeren. Gedeeltelijke configuraties kan elk team een eigen configuratie, zonder een van beide wordt onnodig ingewikkeld maken.

U kunt gedeeltelijke configuraties in push-modus, pull-modus of een combinatie van beide.

## <a name="partial-configurations-in-push-mode"></a>Gedeeltelijke configuraties in de pushmodus gebruikt

Voor het gebruik van gedeeltelijke configuraties in de pushmodus gebruikt, kunt u de LCM configureren in het doelknooppunt voor het ontvangen van de gedeeltelijke configuraties. Elke gedeeltelijke configuratie moet worden gepusht naar het doel met behulp van de `Publish-DSCConfiguration` cmdlet. Het doelknooppunt vervolgens combineert de gedeeltelijke configuratie in een configuratie voor één, en u kunt de configuratie toepassen door het aanroepen van de [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.

### <a name="configuring-the-lcm-for-push-mode-partial-configurations"></a>De LCM voor push-modus gedeeltelijke configuraties configureren

Als u wilt configureren de LCM voor gedeeltelijke configuraties in de pushmodus gebruikt, maakt u een **DSCLocalConfigurationManager** configuratie met een **PartialConfiguration** blokkeren voor elke gedeeltelijke configuratie. Zie voor meer informatie over het configureren van de LCM [Windows de Local Configuration Manager configureren](/powershell/dsc/metaConfig). Het volgende voorbeeld ziet u een LCM-configuratie die wordt verwacht twee gedeeltelijke configuraties dat: één waarmee het besturingssysteem wordt geïmplementeerd, en één die wordt geïmplementeerd en geconfigureerd van SharePoint.

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemo
{
    Node localhost
    {

        PartialConfiguration ServiceAccountConfig
        {
            Description = 'Configuration to add the SharePoint service account to the Administrators group.'
            RefreshMode = 'Push'
        }
           PartialConfiguration SharePointConfig
        {
            Description = 'Configuration for the SharePoint server'
            RefreshMode = 'Push'
        }
    }
}

PartialConfigDemo
```

De **RefreshMode** voor elke gedeeltelijke configuratie is ingesteld op 'Push'. De namen van de **PartialConfiguration** blokken (in dit geval "ServiceAccountConfig" en "SharePointConfig") moeten overeenkomen met precies de namen van de configuraties die worden gepusht naar het doelknooppunt.

> [!Note]
> De naam van elk **PartialConfiguration** blok moet overeenkomen met de werkelijke naam van de configuratie als deze is opgegeven in het configuratiescript, niet de naam van het MOF-bestand de naam van het doelknooppunt of moet`localhost`.

### <a name="publishing-and-starting-push-mode-partial-configurations"></a>Publiceren en starten van push-modus gedeeltelijke configuraties

Vervolgens aanroepen [publiceren-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) voor elke configuratie geven de mappen die de van configuratiedocumenten als bevatten de **pad** parameters. `Publish-DSCConfiguration`Hiermee plaatst u de configuratie van MOF-bestanden naar de doelknooppunten. Na het publiceren van beide configuraties, u kunt aanroepen `Start-DSCConfiguration –UseExisting` op het doelknooppunt.

Bijvoorbeeld, als u hebt de volgende configuratie MOF-documenten op het knooppunt authoring gecompileerd:

```powershell
Get-ChildItem -Recurse
```

```output
    Directory: C:\PartialConfigTest

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        8/11/2016   1:55 PM                ServiceAccountConfig
d-----       11/17/2016   4:14 PM                SharePointConfig

    Directory: C:\PartialConfigTest\ServiceAccountConfig

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        8/11/2016   2:02 PM           2034 TestVM.mof

    Directory: C:\DscTests\SharePointConfig

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       11/17/2016   4:14 PM           1930 TestVM.mof
```

U zou publiceren en voer de configuraties als volgt uit:

```powershell
Publish-DscConfiguration .\ServiceAccountConfig -ComputerName 'TestVM'
Publish-DscConfiguration .\SharePointConfig -ComputerName 'TestVM'
Start-DscConfiguration -UseExisting -ComputerName 'TestVM'
```

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
17     Job17           Configuratio... Running       True            TestVM            Start-DscConfiguration...
```

> [!Note]
> De gebruiker die de [publiceren-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) cmdlet moet beheerdersbevoegdheden hebben op het doelknooppunt.

## <a name="partial-configurations-in-pull-mode"></a>Gedeeltelijke configuraties in de pull-modus

Gedeeltelijke configuraties kunnen worden opgehaald uit een of meer pull-servers (Zie voor meer informatie over pull-servers, [Windows PowerShell Desired State Configuration Pull Servers](pullServer.md). Om dit te doen, moet u de LCM configureren op het doelknooppunt voor het ophalen van de gedeeltelijke configuraties, en geef de naam en zoek de configuratiedocumenten correct op de pull-servers.

### <a name="configuring-the-lcm-for-pull-node-configurations"></a>De LCM voor pull-knooppuntconfiguraties configureren

Als u wilt de LCM om op te halen van gedeeltelijke configuraties van een pull-server is geconfigureerd, definieert u de pull-server in een een **ConfigurationRepositoryWeb** (voor een HTTP-pull-server) of **ConfigurationRepositoryShare** () voor een SMB-pull-server) blokkeren. Vervolgens maakt u **PartialConfiguration** blokken die naar de pull-server met behulp van verwijzen de **ConfigurationSource** eigenschap. U moet ook maken een **instellingen** blokkeren om op te geven dat de LCM pull-modus gebruikt, en om op te geven de **ConfigurationNames** of **ConfigurationID** die de pull-server en doel-knooppunt gebruiken om u te identificeren van de configuraties. De volgende meta-configuratie definieert een HTTP-pull-server met de naam CONTOSO-PullSrv en twee gedeeltelijke configuraties die gebruikmaken van die pull-server.

Voor meer informatie over het configureren van de LCM via **ConfigurationNames**, Zie [instellen van een pull-client met behulp van configuratienamen](pullClientConfigNames.md). Voor informatie over het configureren van de LCM via **ConfigurationID**, Zie [instellen van een pull-client met behulp van configuratie-ID](pullClientConfigID.md).

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configuration-names"></a>De LCM voor pull-modus configuraties met behulp van configuratienamen configureren

```powershell
[DscLocalConfigurationManager()]
Configuration PartialConfigDemoConfigNames
{
        Settings
        {
            RefreshFrequencyMins            = 30;
            RefreshMode                     = "PULL";
            ConfigurationMode               ="ApplyAndAutocorrect";
            AllowModuleOverwrite            = $true;
            RebootNodeIfNeeded              = $true;
            ConfigurationModeFrequencyMins  = 60;
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL                       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey                 = 5b41f4e6-5e6d-45f5-8102-f2227468ef38
            ConfigurationNames              = @("ServiceAccountConfig", "SharePointConfig")
        }

        PartialConfiguration ServiceAccountConfig
        {
            Description                     = "ServiceAccountConfig"
            ConfigurationSource             = @("[ConfigurationRepositoryWeb]CONTOSO-PullSrv")
        }

        PartialConfiguration SharePointConfig
        {
            Description                     = "SharePointConfig"
            ConfigurationSource             = @("[ConfigurationRepositoryWeb]CONTOSO-PullSrv")
            DependsOn                       = '[PartialConfiguration]ServiceAccountConfig'
        }
}
```

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configurationid"></a>De LCM voor pull-modus configuraties met behulp van ConfigurationID configureren

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemoConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode                     = 'Pull'
            ConfigurationID                 = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins            = 30
            RebootNodeIfNeeded              = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL                       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

           PartialConfiguration ServiceAccountConfig
        {
            Description                     = 'Configuration for the Base OS'
            ConfigurationSource             = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            RefreshMode                     = 'Pull'
        }
           PartialConfiguration SharePointConfig
        {
            Description                     = 'Configuration for the Sharepoint Server'
            ConfigurationSource             = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            DependsOn                       = '[PartialConfiguration]ServiceAccountConfig'
            RefreshMode                     = 'Pull'
        }
    }
}
PartialConfigDemo
```

U kunt gedeeltelijke configuraties van meer dan één pull-server ophalen, moet u alleen voor het definiëren van elke pull-server en vervolgens verwijzen naar de juiste pull-server in elk **PartialConfiguration** blokkeren.

Nadat de configuratie van de metagegevens is gemaakt, moet u het voor het maken van een configuratiedocument (een MOF-bestand) en roep vervolgens uitvoeren [Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) de LCM configureren.

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationnames"></a>Naamgeving en het plaatsen van de van configuratiedocumenten op de pull-server (ConfigurationNames)

De documenten gedeeltelijke configuratie moeten worden geplaatst in de map die is opgegeven als de **ConfigurationPath** in de `web.config` -bestand voor de pull-server (meestal `C:\Program
Files\WindowsPowerShell\DscService\Configuration`).

#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-51"></a>Naamgeving van configuratiedocumenten op de pull-server in PowerShell 5.1

Als u van slechts een gedeeltelijke configuratie van een afzonderlijke pull-server binnenhalen, kan het configuratiebestand voor elke naam hebben. Als u van meer dan een gedeeltelijke configuratie van een pull-server binnenhalen, het configuratiebestand kan worden met de naam `<ConfigurationName>.mof`, waarbij *ConfigurationName* is de naam van de gedeeltelijke configuratie of `<ConfigurationName>.<NodeName>.mof`, waarbij *ConfigurationName* is de naam van de gedeeltelijke configuratie en *knooppuntnaam* is de naam van het doelknooppunt. Hiermee kunt u pull-configuraties van Azure Automation DSC pull-server.

#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-50"></a>Naamgeving van configuratiedocumenten op de pull-server in PowerShell 5.0

De configuratiedocumenten moeten de naam als volgt: `ConfigurationName.mof`, waarbij *ConfigurationName* is de naam van de gedeeltelijke configuratie. In ons voorbeeld moeten u als volgt de van configuratiedocumenten krijgen:

```
ServiceAccountConfig.mof
ServiceAccountConfig.mof.checksum
SharePointConfig.mof
SharePointConfig.mof.checksum
```

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationid"></a>Naamgeving en het plaatsen van de van configuratiedocumenten op de pull-server (ConfigurationID)

De documenten gedeeltelijke configuratie moeten worden geplaatst in de map die is opgegeven als de **ConfigurationPath** in de `web.config` -bestand voor de pull-server (meestal `C:\Program Files\WindowsPowerShell\DscService\Configuration`). De configuratiedocumenten moeten de naam als volgt: `<ConfigurationName>.<ConfigurationID>.mof`, waarbij _ConfigurationName_ is de naam van de configuratie van de gedeeltelijke en _ConfigurationID_ is de configuratie-ID die is gedefinieerd in de De LCM op het doelknooppunt. In ons voorbeeld moeten u als volgt de van configuratiedocumenten krijgen:

```
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
```

### <a name="running-partial-configurations-from-a-pull-server"></a>Gedeeltelijke configuraties uitvoeren vanaf een pull-server

Nadat de LCM op het doelknooppunt is geconfigureerd en de configuratiedocumenten zijn gemaakt en naar behoren met de naam van de pull-server, wordt het doelknooppunt de gedeeltelijke configuraties ophalen, deze combineren en de resulterende configuratie tegen de normale toepassen intervallen zoals opgegeven door de **RefreshFrequencyMins** eigenschap van de LCM. Als u wilt vernieuwen wilt afdwingen, u kunt aanroepen de [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration) -cmdlet voor het ophalen van de configuraties, en vervolgens `Start-DSCConfiguration –UseExisting` om toe te passen.

## <a name="partial-configurations-in-mixed-push-and-pull-modes"></a>Gedeeltelijke configuraties in gemengde push als pull-modi

U kunt ook push combineren en pull-modi voor gedeeltelijke configuraties. Dat wil zeggen, hebt u kunnen een gedeeltelijke configuratie die is opgehaald uit een pull-server, terwijl een andere gedeeltelijke configuratie wordt gepusht. Geef de vernieuwingsmodus voor voor elke gedeeltelijke configuratie zoals beschreven in de vorige secties. Bijvoorbeeld, de volgende meta-configuratie wordt beschreven hoe u het hetzelfde voorbeeld het `ServiceAccountConfig` gedeeltelijke configuratie in de pull-modus en de `SharePointConfig` gedeeltelijke configuratie in de pushmodus gebruikt.

### <a name="mixed-push-and-pull-modes-using-configurationnames"></a>Gemengde push als pull-modi ConfigurationNames gebruiken

```powershell
[DscLocalConfigurationManager()]
Configuration PartialConfigDemoConfigNames
{
        Settings
        {
            RefreshFrequencyMins            = 30;
            RefreshMode                     = "PULL";
            ConfigurationMode               = "ApplyAndAutocorrect";
            AllowModuleOverwrite            = $true;
            RebootNodeIfNeeded              = $true;
            ConfigurationModeFrequencyMins  = 60;
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL                       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey                 = 5b41f4e6-5e6d-45f5-8102-f2227468ef38
            ConfigurationNames              = @("ServiceAccountConfig", "SharePointConfig")
        }

        PartialConfiguration ServiceAccountConfig
        {
            Description                     = "ServiceAccountConfig"
            ConfigurationSource             = @("[ConfigurationRepositoryWeb]CONTOSO-PullSrv")
            RefreshMode                     = 'Pull'
        }

        PartialConfiguration SharePointConfig
        {
            Description                     = "SharePointConfig"
            DependsOn                       = '[PartialConfiguration]ServiceAccountConfig'
            RefreshMode                     = 'Push'
        }

}
```

### <a name="mixed-push-and-pull-modes-using-configurationid"></a>Gemengde push als pull-modi ConfigurationID gebruiken

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemo
{
    Node localhost
    {
        Settings
        {
            RefreshMode             = 'Pull'
            ConfigurationID         = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins    = 30
            RebootNodeIfNeeded      = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL               = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

           PartialConfiguration ServiceAccountConfig
        {
            Description             = 'Configuration for the Base OS'
            ConfigurationSource     = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            RefreshMode             = 'Pull'
        }
           PartialConfiguration SharePointConfig
        {
            Description             = 'Configuration for the Sharepoint Server'
            DependsOn               = '[PartialConfiguration]ServiceAccountConfig'
            RefreshMode             = 'Push'
        }
    }
}
PartialConfigDemo
```

Houd er rekening mee dat de **RefreshMode** die is opgegeven in het blok instellingen is 'Pull', maar de **RefreshMode** voor de `SharePointConfig` gedeeltelijke configuratie is 'Push'.

Geef de naam en zoek de configuratiebestanden van de MOF zoals hierboven beschreven voor de modi van hun respectieve vernieuwen.
Bel `Publish-DSCConfiguration` publiceren de `SharePointConfig` gedeeltelijke configuratie, en een wachten op de `ServiceAccountConfig` configuratie die moet worden opgehaald uit de pull-server of een vernieuwing forceren door het aanroepen van [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration).

## <a name="example-serviceaccountconfig-partial-configuration"></a>Voorbeeldconfiguratie ServiceAccountConfig gedeeltelijk

```powershell
Configuration ServiceAccountConfig
{
    Param (
        [Parameter(Mandatory,
                   HelpMessage="Domain credentials required to add domain\sharepoint_svc to the local Administrators group.")]
        [ValidateNotNullOrEmpty()]
        [pscredential]$Credential
    )

    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node localhost
    {
        Group LocalAdmins
        {
            GroupName           = 'Administrators'
            MembersToInclude    = 'domain\sharepoint_svc',
                                  'admins@example.domain'
            Ensure              = 'Present'
            Credential          = $Credential
        }

        WindowsFeature Telnet
        {
            Name                = 'Telnet-Server'
            Ensure              = 'Absent'
        }
    }
}
ServiceAccountConfig
```

## <a name="example-sharepointconfig-partial-configuration"></a>Voorbeeldconfiguratie SharePointConfig gedeeltelijk

```powershell
Configuration SharePointConfig
{
    Param (
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [pscredential]$ProductKey
    )

    Import-DscResource -ModuleName xSharePoint

    Node localhost
    {
        xSPInstall SharePointDefault
        {
            Ensure      = 'Present'
            BinaryDir   = '\\FileServer\Installers\Sharepoint\'
            ProductKey  = $ProductKey
        }
    }
}
SharePointConfig
```

## <a name="see-also"></a>Zie ook

[Windows PowerShell Desired State Configuration Pull-Servers](pullServer.md)

[Windows de Local Configuration Manager configureren](../managing-nodes/metaConfig.md)