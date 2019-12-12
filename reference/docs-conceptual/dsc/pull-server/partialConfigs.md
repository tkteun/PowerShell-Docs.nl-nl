---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: Gedeeltelijke configuraties van de desired state Configuration van Power shell
ms.openlocfilehash: 379ecf804329f318e9604c1af43a60a0e24551f1
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74417739"
---
# <a name="powershell-desired-state-configuration-partial-configurations"></a>Gedeeltelijke configuraties van de desired state Configuration van Power shell

_Van toepassing op: Windows Power shell 5,0 en hoger._

In Power shell 5,0 kunnen configuraties met desired state Configuration (DSC) worden geleverd in fragmenten en uit meerdere bronnen. De lokale Configuration Manager (LCM) op het doel knooppunt plaatst de fragmenten samen voordat ze als één configuratie worden toegepast. Met deze functie kunt u het beheer van de configuratie tussen teams of individuen delen. Als bijvoorbeeld twee of meer teams van ontwikkel aars samen werken aan een service, kunnen ze elk een configuratie maken om hun onderdeel van de service te beheren. Elk van deze configuraties kan worden opgehaald van verschillende pull-servers en ze kunnen worden toegevoegd tijdens verschillende ontwikkelings fasen. Gedeeltelijke configuraties staan ook toe dat verschillende personen of teams verschillende aspecten van het configureren van knoop punten beheren zonder dat ze het bewerken van één configuratie document hoeven te coördineren. Het is bijvoorbeeld mogelijk dat een team verantwoordelijk is voor de implementatie van een virtuele machine en een besturings systeem, terwijl een ander team mogelijk andere toepassingen en services op die virtuele machine implementeert. Met gedeeltelijke configuraties kan elk team een eigen configuratie maken, zonder dat ze onnodig ingewikkeld zijn.

U kunt gedeeltelijke configuraties gebruiken in de push-modus, de pull-modus of een combi natie van beide.

## <a name="partial-configurations-in-push-mode"></a>Gedeeltelijke configuraties in push-modus

Als u gedeeltelijke configuraties wilt gebruiken in de push-modus, configureert u de LCM op het doel knooppunt om de gedeeltelijke configuraties te ontvangen. Elke gedeeltelijke configuratie moet worden gepusht naar het doel met behulp van de cmdlet `Publish-DSCConfiguration`. Op het doel knooppunt wordt de gedeeltelijke configuratie vervolgens gecombineerd tot één configuratie en kunt u de configuratie Toep assen door de [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) -cmdlet aan te roepen.

### <a name="configuring-the-lcm-for-push-mode-partial-configurations"></a>De LCM configureren voor gedeeltelijke configuratie van de push modus

Als u de LCM wilt configureren voor gedeeltelijke configuraties in de push-modus, maakt u een **DSCLocalConfigurationManager** -configuratie met één **PartialConfiguration** -blok voor elke gedeeltelijke configuratie. Zie [Windows Configuring the Local Configuration Manager](/powershell/scripting/dsc/metaConfig)voor meer informatie over het configureren van de LCM. In het volgende voor beeld ziet u een configuratie van de LCM die twee gedeeltelijke configuraties verwacht, een die het besturings systeem implementeert en een die share point implementeert en configureert.

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

De **RefreshMode** voor elke gedeeltelijke configuratie is ingesteld op push. De namen van de **PartialConfiguration** -blokken (in dit geval ' ServiceAccountConfig ' en ' SharePointConfig ') moeten exact overeenkomen met de namen van de configuraties die naar het doel knooppunt worden gepusht.

> [!Note]
> De naam van elk **PartialConfiguration** -blok moet overeenkomen met de werkelijke naam van de configuratie zoals die is opgegeven in het configuratie script, niet de naam van het MOF-bestand. dit moet de naam van het doel knooppunt of `localhost`zijn.

### <a name="publishing-and-starting-push-mode-partial-configurations"></a>Gedeeltelijke configuraties van push-modus publiceren en starten

Vervolgens roept u [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) aan voor elke configuratie, waarbij de mappen die de configuratie documenten bevatten worden door gegeven als de para meters voor het **pad** . `Publish-DSCConfiguration`plaatst de configuratie-MOF-bestanden naar de doel knooppunten. Na het publiceren van beide configuraties kunt u `Start-DSCConfiguration –UseExisting` aanroepen op het doel knooppunt.

Als u bijvoorbeeld de volgende configuratie-MOF-documenten hebt gecompileerd op het knoop punt voor ontwerpen:

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

    Directory: C:\PartialConfigTest\SharePointConfig

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       11/17/2016   4:14 PM           1930 TestVM.mof
```

U publiceert en voert de volgende configuraties uit:

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
> De gebruiker die de cmdlet [Publish-DSCConfiguration uitvoert,](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) moet Administrator bevoegdheden hebben op het doel knooppunt.

## <a name="partial-configurations-in-pull-mode"></a>Gedeeltelijke configuraties in de pull-modus

Gedeeltelijke configuraties kunnen worden opgehaald van een of meer pull-servers (Zie [Windows Power shell desired state Configuration pull servers](pullServer.md)voor meer informatie over pull-servers. Als u dit wilt doen, moet u de LCM op het doel knooppunt configureren om de gedeeltelijke configuraties te halen en de configuratie documenten op de pull-servers goed te vinden.

### <a name="configuring-the-lcm-for-pull-node-configurations"></a>De LCM configureren voor pull-knooppunt configuraties

Als u de LCM wilt configureren voor het verzamelen van gedeeltelijke configuraties van een pull-server, definieert u de pull-server in een **ConfigurationRepositoryWeb** (voor een http-pull-server) of **ConfigurationRepositoryShare** (voor een SMB pull-server)-blok. Vervolgens maakt u **PartialConfiguration** -blokken die verwijzen naar de pull-server met behulp van de eigenschap **ConfigurationSource** . U moet ook een **instellingen** blok maken om op te geven dat de LCM de pull-modus gebruikt en om de **ConfigurationNames** of **ConfigurationID** op te geven die door de pull-server en het doel knooppunt wordt gebruikt om de configuraties te identificeren. De volgende meta configuratie definieert een HTTP-pull-server met de naam CONTOSO-PullSrv en twee gedeeltelijke configuraties die deze pull-server gebruiken.

Zie [een pull-client instellen met behulp van configuratie namen](pullClientConfigNames.md)voor meer informatie over het configureren van de LCM met behulp van **ConfigurationNames**. Zie [een pull-client instellen met behulp van de configuratie-ID](pullClientConfigID.md)voor meer informatie over het configureren van de LCM met behulp van **ConfigurationID**.

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configuration-names"></a>De LCM configureren voor pull-modus configuraties met configuratie namen

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

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configurationid"></a>De LCM configureren voor pull-modus configuraties met behulp van ConfigurationID

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

U kunt gedeeltelijke configuraties van meer dan één pull-server halen: u hoeft alleen elke pull-server te definiëren en vervolgens naar de juiste pull-server in elk **PartialConfiguration** -blok te verwijzen.

Nadat u de meta configuratie hebt gemaakt, moet u deze uitvoeren om een configuratie document (een MOF-bestand) te maken en vervolgens [set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) aanroepen om de LCM te configureren.

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationnames"></a>Naamgeving en plaatsen van de configuratie documenten op de pull-server (ConfigurationNames)

De gedeeltelijke configuratie documenten moeten worden geplaatst in de map die is opgegeven als de **ConfigurationPath** in het `web.config`-bestand voor de pull-server (meestal `C:\Program
Files\WindowsPowerShell\DscService\Configuration`).

#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-51"></a>Naamgeving van configuratie documenten op de pull-server in Power shell 5,1

Als u slechts één gedeeltelijke configuratie van een afzonderlijke pull-server haalt, kan het configuratie document een wille keurige naam hebben. Als u meer dan één gedeeltelijke configuratie haalt van een pull-server, kan het configuratie document een naam hebben van `<ConfigurationName>.mof`, waarbij *configuratiepad* de naam van de gedeeltelijke configuratie is, of `<ConfigurationName>.<NodeName>.mof`, waarbij *configuratiepad* de naam van de gedeeltelijke configuratie is en *knooppunt* naam het doel knooppunt is. Hierdoor kunt u configuraties van Azure Automation DSC-pull-server ophalen.

#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-50"></a>Naamgeving van configuratie documenten op de pull-server in Power shell 5,0

De configuratie documenten moeten de volgende naam hebben: `ConfigurationName.mof`, waarbij *configuratiepad* de naam van de gedeeltelijke configuratie is. In ons voor beeld moeten de configuratie documenten de volgende naam hebben:

```
ServiceAccountConfig.mof
ServiceAccountConfig.mof.checksum
SharePointConfig.mof
SharePointConfig.mof.checksum
```

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationid"></a>Naamgeving en plaatsen van de configuratie documenten op de pull-server (ConfigurationID)

De gedeeltelijke configuratie documenten moeten worden geplaatst in de map die is opgegeven als de **ConfigurationPath** in het `web.config`-bestand voor de pull-server (meestal `C:\Program Files\WindowsPowerShell\DscService\Configuration`). De configuratie documenten moeten de volgende naam hebben: `<ConfigurationName>.<ConfigurationID>.mof`, waarbij _configuratiepad_ de naam is van de gedeeltelijke configuratie en _ConfigurationID_ is de configuratie-id die is gedefinieerd in de LCM op het doel knooppunt. In ons voor beeld moeten de configuratie documenten de volgende naam hebben:

```
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
```

### <a name="running-partial-configurations-from-a-pull-server"></a>Gedeeltelijke configuraties uitvoeren vanaf een pull-server

Nadat de LCM op het doel knooppunt is geconfigureerd en de configuratie documenten zijn gemaakt en op de juiste manier zijn benoemd op de pull-server, haalt het doel knooppunt de gedeeltelijke configuraties op, combineert ze en past de resulterende configuratie met regel matige tussen pozen toe zoals opgegeven door de eigenschap **RefreshFrequencyMins** van de LCM. Als u het vernieuwen wilt forceren, kunt u de cmdlet [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration) aanroepen om de configuraties op te halen en vervolgens `Start-DSCConfiguration –UseExisting` om ze toe te passen.

## <a name="partial-configurations-in-mixed-push-and-pull-modes"></a>Gedeeltelijke configuraties in gemengde push-en pull-modi

U kunt ook push-en pull-modi combi neren voor gedeeltelijke configuraties. Dat wil zeggen dat u één gedeeltelijke configuratie kunt hebben die wordt opgehaald van een pull-server, terwijl een andere gedeeltelijke configuratie wordt gepusht. Geef de vernieuwings modus voor elke gedeeltelijke configuratie op, zoals beschreven in de vorige secties. De volgende meta configuratie bevat bijvoorbeeld hetzelfde voor beeld, met de `ServiceAccountConfig` gedeeltelijke configuratie in de pull-modus en de `SharePointConfig` gedeeltelijke configuratie in de push-modus.

### <a name="mixed-push-and-pull-modes-using-configurationnames"></a>Gemengde push-en pull-modi met ConfigurationNames

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

### <a name="mixed-push-and-pull-modes-using-configurationid"></a>Gemengde push-en pull-modi met ConfigurationID

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

Houd er rekening mee dat de **RefreshMode** die zijn opgegeven in het instellingen blok pull is, maar dat de **RefreshMode** voor de `SharePointConfig` gedeeltelijke configuratie ' push ' is.

Naam en zoek de MOF-bestanden van de configuratie zoals hierboven wordt beschreven voor de respectieve vernieuwings modi.
Roep `Publish-DSCConfiguration` aan om de `SharePointConfig` gedeeltelijke configuratie te publiceren en wacht totdat de `ServiceAccountConfig` configuratie wordt opgehaald van de pull-server of dwing een vernieuwing af door [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration)aan te roepen.

## <a name="example-serviceaccountconfig-partial-configuration"></a>Voor beeld van een gedeeltelijke configuratie van ServiceAccountConfig

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

## <a name="example-sharepointconfig-partial-configuration"></a>Voor beeld van een gedeeltelijke configuratie van SharePointConfig

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

[Windows Power shell desired state Configuration pull-servers](pullServer.md)

[Windows configureren van de lokale Configuration Manager](../managing-nodes/metaConfig.md)
