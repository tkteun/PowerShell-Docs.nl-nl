---
ms.date: 12/12/2018
keywords: DSC, powershell, configuratie en installatie
title: Instellen van een Pull-Client met behulp van configuratie-ID's in PowerShell 5.0 en hoger
ms.openlocfilehash: 8d8cf478f9127e1b7005d1b9e832e84b11612c9c
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404293"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-50-and-later"></a>Instellen van een Pull-Client met behulp van configuratie-ID's in PowerShell 5.0 en hoger

> Van toepassing op: Windows PowerShell 5.0

> [!IMPORTANT]
> De Pull-Server (Windows-functie *DSC-Service*) is een ondersteunde onderdeel van Windows Server maar er zijn geen plannen om nieuwe functies en mogelijkheden bieden. Het verdient aanbeveling om te beginnen met het overstappen clients beheerd [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inclusief functies dan Pull-Server op Windows Server) of een van de community-oplossingen die zijn opgenomen [hier](pullserver.md#community-solutions-for-pull-service).

Voordat u een pull-client instelt, moet u een pull-server instellen. Al deze order niet vereist is, helpt bij het oplossen van problemen en kunt u ervoor zorgen dat de registratie geslaagd is. Als u een pull-server instelt, kunt u de volgende handleidingen:

- [Een DSC SMB-Pull-Server instellen](pullServerSmb.md)
- [Een DSC HTTP-Pull-Server instellen](pullServer.md)

Elk doelknooppunt kan worden geconfigureerd voor het downloaden van configuraties, resources, en zelfs de status rapporteren. De volgende secties laten zien hoe u een pull-client configureren met een SMB-share of een HTTP-DSC-Pull-Server. Wanneer van het knooppunt LCM vernieuwd, wordt het contact opnemen met de geconfigureerde locatie voor het downloaden van de toegewezen configuraties. Als alle vereiste resources niet aanwezig zijn op het knooppunt, wordt deze ze automatisch downloaden van de geconfigureerde locatie. Als het knooppunt is geconfigureerd met een [Report Server](reportServer.md), deze wordt vervolgens rapporteert de status van de bewerking.

> **Houd er rekening mee**: In dit onderwerp is van toepassing op PowerShell 5.0. Zie voor meer informatie over het instellen van een pull-client in PowerShell 4.0 [instellen van een pull-client met behulp van configuratie-ID in PowerShell 4.0](pullClientConfigID4.md)

## <a name="configure-the-pull-client-lcm"></a>De pull-client LCM configureren

Uitvoeren van een van de voorbeelden hieronder maakt u een nieuwe map voor uitvoer met de naam **PullClientConfigID** en er een metaconfiguration MOF-bestand geplaatst. In dit geval het metaconfiguration MOF-bestand de naam `localhost.meta.mof`.

Aanroepen om toe te passen de configuratie, de **Set-DscLocalConfigurationManager** -cmdlet met de **pad** ingesteld op de locatie van het metaconfiguration MOF-bestand. Bijvoorbeeld:

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a>Configuratie-ID

De voorbeelden hieronder wordt de **ConfigurationID** eigenschap van de LCM om een **Guid** die eerder is gemaakt voor dit doel. De **ConfigurationID** is wat de LCM gebruikt om te vinden van de juiste configuratie op de pull-server. Het MOF-configuratiebestand op de pull-server moet de naam `ConfigurationID.mof`, waarbij *ConfigurationID* is de waarde van de **ConfigurationID** eigenschap van het doelknooppunt LCM. Zie voor meer informatie [configuraties publiceren naar een Pull-Server (v4/v5)](publishConfigs.md).

U kunt een willekeurige maken **Guid** met behulp van het voorbeeld hieronder of met behulp van de [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.

```powershell
[System.Guid]::NewGuid()
```

Voor meer informatie over het gebruik van **GUID's** in uw omgeving, Zie [plannen voor GUID's](/powershell/dsc/secureserver#guids).

## <a name="set-up-a-pull-client-to-download-configurations"></a>Instellen van een Pull-Client voor het downloaden van configuraties

Elke client moet worden geconfigureerd in **Pull** modus en de url van de pull-server waar de configuratie is opgeslagen. Om dit te doen, moet u de lokale Configuration Manager (LCM) configureren met de benodigde informatie. Als u wilt de LCM configureren, maakt u een speciaal soort configuratie, voorzien van de **DSCLocalConfigurationManager** kenmerk. Zie voor meer informatie over het configureren van de LCM [de Local Configuration Manager configureren](../managing-nodes/metaConfig.md).

### <a name="http-dsc-pull-server"></a>HTTP-DSC-Pull-Server

Het volgende script wordt de LCM geconfigureerd voor pull-configuraties van een server met de naam 'CONTOSO-PullSrv'.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }
    }
}
PullClientConfigID
```

In het script de **ConfigurationRepositoryWeb** blok definieert de pull-server. De **ServerUrl** geeft de url van de DSC-Pull

### <a name="smb-share"></a>SMB-Share

Het volgende script configureert u de LCM met pull-configuraties van de SMB-Share `\\SMBPullServer\Pull`.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryShare SMBPullServer
        {
            SourcePath = '\\SMBPullServer\Pull'
        }
    }
}
PullClientConfigID
```

In het script de **ConfigurationRepositoryShare** blok definieert de pull-server, die in dit geval een SMB-share is.

## <a name="set-up-a-pull-client-to-download-resources"></a>Instellen van een Pull-Client voor het downloaden van Resources

Als u alleen opgeeft de **ConfigurationRepositoryWeb** of **ConfigurationRepositoryShare** blokkeren in uw configuratie LCM (zoals in de vorige voorbeelden), de pull-client-resources van hetzelfde wordt opgehaald locatie van het ophalen van de configuraties. U kunt ook afzonderlijke locaties voor bronnen opgeven. Als u de Resourcelocatie van een als een afzonderlijke server, gebruikt de **ResourceRepositoryWeb** blokkeren. Als u de Resourcelocatie van een als een SMB-share, gebruikt de **ResourceRepositoryShare** blokkeren.

> [!NOTE]
> U kunt combineren **ConfigurationRepositoryWeb** met **ResourceRepositoryShare** of **ConfigurationRepositoryShare** met **ResourceRepositoryWeb** . Voorbeelden van deze worden hieronder niet weergegeven.

### <a name="http-dsc-pull-server"></a>HTTP-DSC-Pull-Server

De volgende metaconfiguration configureert u een pull-client om de configuraties van **CONTOSO-PullSrv** en de daarbij behorende bronnen uit **CONTOSO-ResourceSrv**.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

### <a name="smb-share"></a>SMB-Share

Het volgende voorbeeld ziet u een metaconfiguration die u een client naar pull-configuraties van de SMB-share stelt `\\SMBPullServer\Configurations`, en bronnen van de SMB-share `\\SMBPullServer\Resources`.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryShare SMBPullServer
        {
            SourcePath = '\\SMBPullServer\Configurations'
        }

        ResourceRepositoryShare SMBResourceServer
        {
            SourcePath = '\\SMBPullServer\Resources'
        }
    }
}
PullClientConfigID
```

#### <a name="automatically-download-resources-in-push-mode"></a>Automatisch downloaden van Resources in de Push-modus

Begin in PowerShell 5.0, uw pull-clients kunnen modules downloaden van een SMB-share, zelfs wanneer ze zijn geconfigureerd voor **Push** modus. Dit is vooral nuttig in scenario's waar u niet wilt instellen van een Pull-Server. De **ResourceRepositoryShare** blok kan worden gebruikt zonder op te geven een **ConfigurationRepositoryShare**. Het volgende voorbeeld ziet u een metaconfiguration die u een client naar pull-bronnen van een SMB-Share stelt `\\SMBPullServer\Resources`. Wanneer het knooppunt is **PUSHED** een configuratie worden automatisch gedownload die alle vereiste resources van de opgegeven share.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Push'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
        }

        ResourceRepositoryShare SMBResourceServer
        {
            SourcePath = '\\SMBPullServer\Resources'
        }
    }
}
PullClientConfigID
```

## <a name="set-up-a-pull-client-to-report-status"></a>Instellen van een Pull-Client voor statusrapportage

Standaard worden knooppunten rapporten niet verzenden naar een geconfigureerde Pull-Server. U kunt een enkel pull-server gebruiken voor configuraties, resources en rapportage, maar u moet maken een **ReportRepositoryWeb** blokkeren voor het instellen van rapportage.

### <a name="http-dsc-pull-server"></a>HTTP-DSC-Pull-Server

Het volgende voorbeeld ziet een metaconfiguration instellen van een client pull-configuraties, resources en verzenden gegevens rapporteren aan een enkele pull-server.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
        }

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

Als u een rapportserver, gebruikt u een **ReportRepositoryWeb** blokkeren. Een rapportserver mag niet een SMB-server.
De volgende metaconfiguration configureert u een pull-client om de configuraties van **CONTOSO-PullSrv** en de daarbij behorende bronnen uit **CONTOSO-ResourceSrv**, en voor het verzenden van rapporten naar  **CONTOSO-ReportSrv**:

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }

        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

### <a name="smb-share"></a>SMB-Share

Een rapportserver mag niet een SMB-share.

## <a name="next-steps"></a>Volgende stappen

Nadat de pull-client is geconfigureerd, kunt u de volgende handleidingen gebruiken om uit te voeren van de volgende stappen:

- [Configuraties publiceren naar een Pull-Server (v4/v5)](publishConfigs.md)
- [Pakket- en Resources uploaden naar een Pull-Server (v4)](package-upload-resources.md)

## <a name="see-also"></a>Zie ook

* [Instellen van een pull-client met configuratienamen](pullClientConfigNames.md)
