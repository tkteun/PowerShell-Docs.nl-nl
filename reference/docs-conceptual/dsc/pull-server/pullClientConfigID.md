---
ms.date: 12/12/2018
keywords: DSC, Power shell, configuratie, installatie
title: Een pull-client instellen met configuratie-Id's in Power shell 5,0 en hoger
ms.openlocfilehash: 14db98d240bc87aca3ee985db08c14b7c65d8bb8
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/04/2019
ms.locfileid: "71941703"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-50-and-later"></a>Een pull-client instellen met configuratie-Id's in Power shell 5,0 en hoger

> Van toepassing op: Windows Power shell 5,0

> [!IMPORTANT]
> De pull-server (Windows *-functie DSC-service*) is een ondersteund onderdeel van Windows Server, maar er zijn geen plannen om nieuwe functies of mogelijkheden aan te bieden. Het wordt aangeraden om te beginnen met het overschakelen van beheerde clients naar [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inclusief functies die verder gaan dan pull server op Windows Server) of een van de [hieronder vermelde Community](pullserver.md#community-solutions-for-pull-service)-oplossingen.

Voordat u een pull-client instelt, moet u een pull-server instellen. Deze volg orde is niet vereist, maar helpt bij het oplossen van problemen en helpt u ervoor te zorgen dat de registratie is geslaagd. U kunt de volgende hand leidingen gebruiken om een pull-server in te stellen:

- [Een DSC SMB-pull-server instellen](pullServerSmb.md)
- [Een DSC HTTP-pull-server instellen](pullServer.md)

Elk doel knooppunt kan worden geconfigureerd voor het downloaden van configuraties, resources en zelfs het rapporteren van de status ervan. In de volgende secties ziet u hoe u een pull-client kunt configureren met een SMB-share of een HTTP DSC-pull-server. Wanneer de LCM van het knoop punt wordt vernieuwd, neemt het contact op met de geconfigureerde locatie voor het downloaden van toegewezen configuraties. Als er vereiste bronnen niet aanwezig zijn op het knoop punt, worden deze automatisch gedownload vanaf de geconfigureerde locatie. Als het knoop punt is geconfigureerd met een [rapport server](reportServer.md), wordt de status van de bewerking gerapporteerd.

> [!NOTE]
> Dit onderwerp is van toepassing op Power shell 5,0. Zie [een pull-client instellen met configuratie-ID in Power shell 4,0](pullClientConfigID4.md) voor informatie over het instellen van een pull-client in power Shell 4,0

## <a name="configure-the-pull-client-lcm"></a>De pull-client LCM configureren

Als u een van de onderstaande voor beelden uitvoert, maakt u een nieuwe uitvoermap met de naam **PullClientConfigID** en plaatst u daar een MOF-bestand met de meta configuratie. In dit geval wordt het MOF-bestand van de meta configuratie `localhost.meta.mof`aangeduid met de naam.

Als u de configuratie wilt Toep assen, roept u de cmdlet **set-DscLocalConfigurationManager** aan, waarbij het **pad** is ingesteld op de locatie van het MOF-bestand met de meta configuratie. Bijvoorbeeld:

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a>Configuratie-ID

In de onderstaande voor beelden wordt de eigenschap **ConfigurationID** van de LCM ingesteld op een **GUID** die eerder is gemaakt voor dit doel. De **ConfigurationID** is wat de LCM gebruikt om de juiste configuratie op de pull-server te vinden. Het MOF-configuratie bestand op de pull-server moet `ConfigurationID.mof`een naam hebben, waarbij *ConfigurationID* de waarde is van de eigenschap **ConfigurationID** van de LCM van het doel knooppunt. Zie [configuraties publiceren naar een pull-server (v4/V5)](publishConfigs.md)voor meer informatie.

U kunt een wille keurige **GUID** maken met behulp van het voor beeld hieronder of met de cmdlet [New-GUID](/powershell/module/microsoft.powershell.utility/new-guid) .

```powershell
[System.Guid]::NewGuid()
```

Zie voor meer informatie over het gebruik van **guid's** in uw omgeving [plan for guid's](/powershell/dsc/secureserver#guids).

## <a name="set-up-a-pull-client-to-download-configurations"></a>Een pull-client instellen om configuraties te downloaden

Elke client moet worden geconfigureerd in de **pull** -modus en krijgt de URL van de pull-server waar de configuratie is opgeslagen. Hiervoor moet u de lokale Configuration Manager (LCM) configureren met de benodigde gegevens. Als u de LCM wilt configureren, maakt u een speciaal type configuratie, gedecoreerd met het kenmerk **DSCLocalConfigurationManager** . Zie [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md)(Engelstalig) voor meer informatie over het configureren van de LCM.

### <a name="http-dsc-pull-server"></a>HTTP DSC-pull-server

Met het volgende script wordt de LCM geconfigureerd voor het ophalen van configuraties van een server met de naam ' CONTOSO-PullSrv '.

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

In het script definieert de pull-server in het **ConfigurationRepositoryWeb** -blok. De **ServerUrl** Hiermee wordt de URL van de DSC-pull opgegeven

### <a name="smb-share"></a>SMB-share

Met het volgende script wordt de LCM geconfigureerd om configuraties te halen uit de SMB-share `\\SMBPullServer\Pull`.

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

In het script definieert het **ConfigurationRepositoryShare** -blok de pull-server, in dit geval alleen een SMB-share.

## <a name="set-up-a-pull-client-to-download-resources"></a>Een pull-client instellen om resources te downloaden

Als u alleen het **ConfigurationRepositoryWeb** -of **ConfigurationRepositoryShare** -blok in uw LCM-configuratie opgeeft (zoals in de voor gaande voor beelden), haalt de pull-client resources op dezelfde locatie op die de configuraties ervan ophaalt. U kunt ook afzonderlijke locaties voor bronnen opgeven. Gebruik het **ResourceRepositoryWeb** -blok om een resource locatie als een afzonderlijke server op te geven. Als u een resource locatie als SMB-share wilt opgeven, gebruikt u het **ResourceRepositoryShare** -blok.

> [!NOTE]
> U kunt **ConfigurationRepositoryWeb** combi neren met **ResourceRepositoryShare** of **ConfigurationRepositoryShare** met **ResourceRepositoryWeb**. Voor beelden hiervan worden hieronder niet weer gegeven.

### <a name="http-dsc-pull-server"></a>HTTP DSC-pull-server

Met de volgende configuratie wordt een pull-client geconfigureerd voor het ophalen van de configuraties van **Contoso-PullSrv** en de bijbehorende resources van **Contoso-ResourceSrv**.

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

### <a name="smb-share"></a>SMB-share

In het volgende voor beeld ziet u een-configuratie die een client instelt voor het ophalen van configuraties uit de SMB-share `\\SMBPullServer\Configurations` en bronnen van de SMB-share `\\SMBPullServer\Resources`.

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

#### <a name="automatically-download-resources-in-push-mode"></a>Automatisch bronnen in de push-modus downloaden

Vanaf Power shell 5,0 kunnen uw pull-clients modules downloaden van een SMB-share, zelfs wanneer ze zijn geconfigureerd voor de **Push** -modus. Dit is vooral handig in scenario's waarin u geen pull-server wilt instellen. Het **ResourceRepositoryShare** -blok kan worden gebruikt zonder een **ConfigurationRepositoryShare**op te geven. In het volgende voor beeld ziet u een-configuratie die een client instelt voor het ophalen van resources van een SMB-share `\\SMBPullServer\Resources`. Wanneer het knoop punt een configuratie heeft **gepusht** , worden de vereiste resources automatisch gedownload van de opgegeven share.

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

## <a name="set-up-a-pull-client-to-report-status"></a>Een pull-client instellen om de status te rapporteren

Standaard worden door knoop punten geen rapporten naar een geconfigureerde pull-server verzonden. U kunt één pull-server gebruiken voor configuraties, resources en rapporten, maar u moet een **ReportRepositoryWeb** -blok maken om rapportage in te stellen.

### <a name="http-dsc-pull-server"></a>HTTP DSC-pull-server

In het volgende voor beeld ziet u een-configuratie die een client instelt voor het ophalen van configuraties en resources, en het verzenden van rapportage gegevens naar één pull-server.

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

Als u een rapport server wilt opgeven, gebruikt u een **ReportRepositoryWeb** -blok. Een rapport server kan geen SMB-server zijn.
Met de volgende configuratie wordt een pull-client geconfigureerd voor het ophalen van de configuraties van **Contoso-PullSrv** en de bijbehorende resources van **Contoso-ResourceSrv**, en het verzenden van status rapporten naar **CONTOSO-ReportSrv**:

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

### <a name="smb-share"></a>SMB-share

Een rapport server kan geen SMB-share zijn.

## <a name="next-steps"></a>Volgende stappen

Zodra de pull-client is geconfigureerd, kunt u de volgende hand leidingen gebruiken om de volgende stappen uit te voeren:

- [Configuraties publiceren naar een pull-server (v4/V5)](publishConfigs.md)
- [Resources verpakken en uploaden naar een pull-server (v4)](package-upload-resources.md)

## <a name="see-also"></a>Zie ook

* [Een pull-client met configuratie namen instellen](pullClientConfigNames.md)
