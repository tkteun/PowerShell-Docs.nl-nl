---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: Gedeeltelijke PowerShell Desired State Configuration-configuraties
ms.openlocfilehash: 4401ea80cffd09f4b92c9fcca16d5dcad7f6a327
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/15/2018
---
# <a name="powershell-desired-state-configuration-partial-configurations"></a>Gedeeltelijke PowerShell Desired State Configuration-configuraties

>Van toepassing op: Windows PowerShell 5.0 en hoger.

In PowerShell 5.0 kan Desired State Configuration (DSC) configuraties moeten worden geleverd in fragmenten en uit meerdere bronnen. De lokale Configuration Manager (LCM) in het doelknooppunt plaatst de fragmenten samen voordat u deze als een configuratie voor één toepast. Deze mogelijkheid ondersteunt het beheer van de configuratie tussen teams of personen delen. Bijvoorbeeld, als twee of meer teams van ontwikkelaars aan een service samenwerken, ze mogelijk elk wilt configuraties voor het beheren van hun deel van de service maken. Elk van deze configuraties kan worden opgehaald uit verschillende pull-servers en ze in verschillende stadia van de ontwikkeling van kunnen worden toegevoegd. Gedeeltelijke configuraties kunnen ook verschillende personen of teams verschillende aspecten van de knooppunten configureren zonder dat voor het coördineren van het bewerken van een configuratie voor één document te bepalen. Een team worden verantwoordelijk voor het implementeren van een virtuele machine en het besturingssysteem, terwijl een ander team andere toepassingen en services op deze virtuele machine kunt implementeren. Met gedeeltelijke configuraties kunt elk team maken van een eigen configuratie, zonder een van beide wordt onnodig ingewikkeld.

U kunt gedeeltelijke configuraties in push-modus, pull-modus of een combinatie van beide gebruiken.

## <a name="partial-configurations-in-push-mode"></a>Gedeeltelijke configuraties in de modus push
Voor het gebruik van gedeeltelijke configuraties in de modus push, configureert u de LCM op het doelknooppunt voor het ontvangen van de gedeeltelijk configuraties. Elke gedeeltelijke configuratie moet worden geactiveerd met de doel-met de cmdlet Publish-DSCConfiguration. Het doelknooppunt vervolgens combineert de gedeeltelijke configuratie in een configuratie voor één, en u kunt de configuratie toepassen door het aanroepen van de [Start DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) cmdlet.

### <a name="configuring-the-lcm-for-push-mode-partial-configurations"></a>De LCM voor push-modus gedeeltelijke configuraties configureren
Voor het configureren van de LCM voor gedeeltelijke configuraties in push-modus, die u maakt een **DSCLocalConfigurationManager** configuratie met een **PartialConfiguration** blok voor elke gedeeltelijke configuratie. Zie voor meer informatie over het configureren van de LCM [Windows configureren van de lokale Configuration Manager](https://technet.microsoft.com/library/mt421188.aspx). Het volgende voorbeeld ziet u de configuratie van een LCM die twee gedeeltelijke configuraties verwacht: één waarmee het besturingssysteem wordt geïmplementeerd en één die wordt geïmplementeerd en SharePoint configureert.

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

De **RefreshMode** voor elke gedeeltelijke configuratie is ingesteld op 'Push'. De namen van de **PartialConfiguration** blokken (in dit geval 'ServiceAccountConfig' en "SharePointConfig") moeten overeenkomen met precies de namen van de configuraties die naar het doelknooppunt worden gepusht.

>**Opmerking:** de benoemde van elke **PartialConfiguration** blok moet overeenkomen met de werkelijke naam van de configuratie zoals deze is opgegeven in het configuratiescript, niet de naam van het MOF-bestand dat moet de naam van de doelknooppunt of `localhost`.

### <a name="publishing-and-starting-push-mode-partial-configurations"></a>Publiceren en starten van de push-modus gedeeltelijke configuraties

Vervolgens aanroepen [publiceren DSCConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/psdesiredstateconfiguration/publish-dscconfiguration) voor elke configuratie de configuratiedocumenten als de mappen die wordt doorgegeven bevatten de **pad** parameters. `Publish-DSCConfiguration`de configuratie MOF-bestanden naar de doelknooppunten plaatst. Na het publiceren van beide configuraties die u kunt aanroepen `Start-DSCConfiguration –UseExisting` in het doelknooppunt.

Bijvoorbeeld, als u hebt de volgende configuratie MOF-documenten op het knooppunt authoring gecompileerd:

```powershell
PS C:\PartialConfigTest> Get-ChildItem -Recurse


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

U wilt publiceren en de configuraties als volgt uitvoeren:

```powershell
PS C:\PartialConfigTest> Publish-DscConfiguration .\ServiceAccountConfig -ComputerName 'TestVM'
PS C:\PartialConfigTest> Publish-DscConfiguration .\SharePointConfig -ComputerName 'TestVM'
PS C:\PartialConfigTest> Start-DscConfiguration -UseExisting -ComputerName 'TestVM'

Id     Name            PSJobTypeName   State         HasMoreData     Location             Command                  
--     ----            -------------   -----         -----------     --------             -------                  
17     Job17           Configuratio... Running       True            TestVM            Start-DscConfiguration...
```

>**Opmerking:** de gebruiker die de [publiceren DSCConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/psdesiredstateconfiguration/publish-dscconfiguration) cmdlet moet beheerdersbevoegdheden hebben op het doelknooppunt.

## <a name="partial-configurations-in-pull-mode"></a>Gedeeltelijke configuraties in pull-modus

Gedeeltelijke configuraties kunnen worden opgehaald uit een of meer pull-servers (Zie voor meer informatie over pull-servers [Windows PowerShell Desired status Pull configuratieservers](pullServer.md). Om dit te doen, moet u de LCM configureren op het doelknooppunt voor de gedeeltelijke configuraties ophalen, naam en zoek de configuratiedocumenten correct op de pull-servers.

### <a name="configuring-the-lcm-for-pull-node-configurations"></a>De LCM voor pull-knooppuntconfiguraties configureren

Voor het configureren van de LCM om op te halen van gedeeltelijke configuraties van een pull-server, u de pull-server definiëren in hetzij een **ConfigurationRepositoryWeb** (voor een HTTP-pull-server) of **ConfigurationRepositoryShare** () voor een SMB-pull-server) blokkeren. Vervolgens maakt u **PartialConfiguration** blokken die naar de pull-server met behulp van verwijzen de **ConfigurationSource** eigenschap. U moet ook maken een **instellingen** blok om op te geven dat de LCM pull-modus gebruikt en op te geven de **ConfigurationNames** of **ConfigurationID** die de pull-server en doel knooppunt gebruiken om te bepalen van de configuraties. De volgende meta-configuratie definieert een HTTP-pull-server met de naam CONTOSO PullSrv en twee gedeeltelijke configuraties die gebruikmaken van die pull-server.

Voor meer informatie over het configureren van het gebruik van LCM **ConfigurationNames**, Zie [instellen van een pull-client met behulp van configuratienamen](pullClientConfigNames.md). Voor informatie over het configureren van het gebruik van LCM **ConfigurationID**, Zie [instellen van een pull-client met behulp van configuratie-ID](pullClientConfigID.md).

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configuration-names"></a>De LCM voor pull-modus configuraties met configuratienamen configureren

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

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configurationid"></a>De LCM voor pull-modus configuraties met ConfigurationID configureren

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

U kunt gedeeltelijke configuraties uit meer dan één pull-server ophalen, moet u alleen voor het definiëren van elk pull-server en vervolgens verwijzen naar de juiste pull-server in elk **PartialConfiguration** blok.

Nadat de meta-configuratie is gemaakt, moet u het voor het maken van een configuratie-document (een MOF-bestand) en vervolgens aanroepen uitvoeren [Set DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621(v=wps.630).aspx) de LCM configureren.

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationnames"></a>Naamgeving en de configuratiedocumenten te plaatsen op de pull-server (ConfigurationNames)

De configuratiedocumenten gedeeltelijke moeten worden geplaatst in de map die is opgegeven als de **ConfigurationPath** in de `web.config` -bestand voor de pull-server (meestal `C:\Program Files\WindowsPowerShell\DscService\Configuration`). 

#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-51"></a>Naamgeving van configuratiedocumenten op de pull-server in PowerShell 5.1

Als u van slechts één gedeeltelijke configuratie van een afzonderlijke pull-server binnenhalen, kan het configuratiebestand voor elke naam hebben. Als u van meer dan één gedeeltelijke configuratie van een pull-server binnenhalen, de configuratie-document kan worden benoemd ofwel `<ConfigurationName>.mof`, waarbij _ConfigurationName_ is de naam van de configuratie van de gedeeltelijke of `<ConfigurationName>.<NodeName>.mof`, waarbij  _ConfigurationName_ is de naam van de configuratie van de gedeeltelijk en _NodeName_ is de naam van het doelknooppunt. Hiermee kunt u pull-configuraties van Azure Automation DSC-pull-server.


#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-50"></a>Naamgeving van configuratiedocumenten op de pull-server in PowerShell 5.0

De configuratiedocumenten moeten als volgt de naam: `ConfigurationName.mof`, waarbij _ConfigurationName_ is de naam van de configuratie van de gedeeltelijk. De configuratiedocumenten moeten als volgt worden genoemd in ons voorbeeld:

```
ServiceAccountConfig.mof
ServiceAccountConfig.mof.checksum
SharePointConfig.mof
SharePointConfig.mof.checksum
```

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationid"></a>Naamgeving en de configuratiedocumenten te plaatsen op de pull-server (ConfigurationID)

De configuratiedocumenten gedeeltelijke moeten worden geplaatst in de map die is opgegeven als de **ConfigurationPath** in de `web.config` -bestand voor de pull-server (meestal `C:\Program Files\WindowsPowerShell\DscService\Configuration`). De configuratiedocumenten moeten als volgt de naam: _ConfigurationName_. _ConfigurationID_`.mof`, waarbij _ConfigurationName_ is de naam van de configuratie van de gedeeltelijk en _ConfigurationID_ is de configuratie-ID is gedefinieerd in de LCM op het doel knooppunt. De configuratiedocumenten moeten als volgt worden genoemd in ons voorbeeld:

```
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
```


### <a name="running-partial-configurations-from-a-pull-server"></a>Gedeeltelijke configuraties uitvoert vanuit een pull-server

Nadat de LCM in het doelknooppunt is geconfigureerd en de configuratie van documenten hebt gemaakt en correct met de naam op de pull-server, het doelknooppunt haalt binnen de gedeeltelijke configuraties, ze combineren en de resulterende configuratie tegen de gebruikelijke toepassen intervallen zoals opgegeven door de **RefreshFrequencyMins** eigenschap van de LCM. Als u vernieuwen wilt, belt u het [Update DscConfiguration](https://technet.microsoft.com/en-us/library/mt143541.aspx) cmdlet voor het ophalen van de configuraties en vervolgens `Start-DSCConfiguration –UseExisting` om toe te passen.


## <a name="partial-configurations-in-mixed-push-and-pull-modes"></a>Gedeeltelijke configuraties in gemengde push als pull-modi

U kunt ook push mix en pull-modi voor gedeeltelijke configuraties. U kunt één gedeeltelijke configuratie die is opgehaald uit een pull-server, terwijl een andere gedeeltelijke configuratie wordt doorgeschoven, dat wil zeggen, kunnen hebben. Geef de vernieuwingsmodus voor elke gedeeltelijke configuratie zoals beschreven in de vorige secties. Bijvoorbeeld de volgende meta-configuratie wordt beschreven in het hetzelfde voorbeeld door de `ServiceAccountConfig` gedeeltelijke configuratie in pull-modus en de `SharePointConfig` gedeeltelijke configuratie in de modus push.

### <a name="mixed-push-and-pull-modes-using-configurationnames"></a>Gemengde push als pull-modi met ConfigurationNames

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

### <a name="mixed-push-and-pull-modes-using-configurationid"></a>Gemengde push als pull-modi met ConfigurationID

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

Houd er rekening mee dat de **RefreshMode** opgegeven in het instellingenblok is 'Pull', maar de **RefreshMode** voor de `SharePointConfig` gedeeltelijke configuratie is 'Push'.

Naam en de configuratiebestanden van de MOF vinden, zoals hierboven beschreven voor de modi van hun respectieve vernieuwen. Aanroepen **publiceren DSCConfiguration** voor het publiceren van de `SharePointConfig` gedeeltelijke configuratie vallen of wacht u totdat de `ServiceAccountConfig` configuratie die moet worden opgehaald uit de pull-server of een vernieuwing forceren door het aanroepen van [ Update DscConfiguration](https://technet.microsoft.com/en-us/library/mt143541(v=wps.630).aspx).

## <a name="example-serviceaccountconfig-partial-configuration"></a>Voorbeeld ServiceAccountConfig gedeeltelijk configuratie

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
## <a name="example-sharepointconfig-partial-configuration"></a>Voorbeeld SharePointConfig gedeeltelijk configuratie
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
##<a name="see-also"></a>Zie ook 

**Concepten**
[Windows PowerShell Desired State Configuration Pull-Servers](pullServer.md) 

[Windows configureren van de lokale Configuration Manager](https://technet.microsoft.com/library/mt421188.aspx) 

