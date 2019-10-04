---
ms.date: 12/12/2018
keywords: DSC, Power shell, configuratie, installatie
title: Een pull-client instellen met configuratie-Id's in Power Shell 4,0
ms.openlocfilehash: 9259c624c8725f7d76f61e9ad7caa42e1bfa308c
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/04/2019
ms.locfileid: "71942781"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-40"></a>Een pull-client instellen met configuratie-Id's in Power Shell 4,0

>Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5,0

> [!IMPORTANT]
> De pull-server (Windows *-functie DSC-service*) is een ondersteund onderdeel van Windows Server, maar er zijn geen plannen om nieuwe functies of mogelijkheden aan te bieden. Het wordt aangeraden om te beginnen met het overschakelen van beheerde clients naar [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inclusief functies die verder gaan dan pull server op Windows Server) of een van de [hieronder vermelde Community](pullserver.md#community-solutions-for-pull-service)-oplossingen.

Voordat u een pull-client instelt, moet u een pull-server instellen. Deze volg orde is niet vereist, maar helpt bij het oplossen van problemen en helpt u ervoor te zorgen dat de registratie is geslaagd. U kunt de volgende hand leidingen gebruiken om een pull-server in te stellen:

- [Een DSC SMB-pull-server instellen](pullServerSmb.md)
- [Een DSC HTTP-pull-server instellen](pullServer.md)

Elk doel knooppunt kan worden geconfigureerd voor het downloaden van configuraties, resources en zelfs het rapporteren van de status ervan. In de volgende secties ziet u hoe u een pull-client kunt configureren met een SMB-share of een HTTP DSC-pull-server. Wanneer de LCM van het knoop punt wordt vernieuwd, neemt het contact op met de geconfigureerde locatie voor het downloaden van toegewezen configuraties. Als er vereiste bronnen niet aanwezig zijn op het knoop punt, worden deze automatisch gedownload vanaf de geconfigureerde locatie. Als het knoop punt is geconfigureerd met een [rapport server](reportServer.md), wordt de status van de bewerking gerapporteerd.

## <a name="configure-the-pull-client-lcm"></a>De pull-client LCM configureren

Als u een van de onderstaande voor beelden uitvoert, maakt u een nieuwe uitvoermap met de naam **PullClientConfigID** en plaatst u daar een MOF-bestand met de meta configuratie. In dit geval wordt het MOF-bestand van de meta configuratie `localhost.meta.mof`aangeduid met de naam.

Als u de configuratie wilt Toep assen, roept u de cmdlet **set-DscLocalConfigurationManager** aan, waarbij het **pad** is ingesteld op de locatie van het MOF-bestand met de meta configuratie. Bijvoorbeeld:

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a>Configuratie-ID

In de onderstaande voor beelden wordt de eigenschap **ConfigurationID** van de LCM ingesteld op een **GUID** die eerder is gemaakt voor dit doel. De **ConfigurationID** is wat de LCM gebruikt om de juiste configuratie op de pull-server te vinden. Het MOF-configuratie bestand op de pull-server moet `ConfigurationID.mof`een naam hebben, waarbij *ConfigurationID* de waarde is van de eigenschap **ConfigurationID** van de LCM van het doel knooppunt. Zie [configuraties publiceren naar een pull-server (v4/V5)](publishConfigs.md)voor meer informatie.

U kunt een wille keurige **GUID** maken met behulp van het onderstaande voor beeld.

```powershell
[System.Guid]::NewGuid()
```

## <a name="set-up-a-pull-client-to-download-configurations"></a>Een pull-client instellen om configuraties te downloaden

Elke client moet worden geconfigureerd in de **pull** -modus en krijgt de URL van de pull-server waar de configuratie is opgeslagen. Hiervoor moet u de lokale Configuration Manager (LCM) configureren met de benodigde gegevens. Als u de LCM wilt configureren, maakt u een speciaal type configuratie, met een **LocalConfigurationManager** -blok. Zie [Configuring the Local Configuration Manager](../managing-nodes/metaConfig4.md)(Engelstalig) voor meer informatie over het configureren van de LCM.

## <a name="http-dsc-pull-server"></a>HTTP DSC-pull-server

Als de pull-server is ingesteld als een webservice, stelt u de **DownloadManagerName** in op **WebDownloadManager**. De **WebDownloadManager** vereist dat u een **ServerUrl** opgeeft bij de **DownloadManagerCustomData** -sleutel. U kunt ook een waarde opgeven voor **AllowUnsecureConnection**, zoals in het onderstaande voor beeld. Met het volgende script wordt de LCM geconfigureerd voor het ophalen van configuraties van een server met de naam ' PullServer '.

```powershell
Configuration PullClientConfigId
{
    LocalConfigurationManager
    {
        ConfigurationID = "1C707B86-EF8E-4C29-B7C1-34DA2190AE24";
        RefreshMode = "PULL";
        DownloadManagerName = "WebDownloadManager";
        RebootNodeIfNeeded = $true;
        RefreshFrequencyMins = 30;
        ConfigurationModeFrequencyMins = 30;
        ConfigurationMode = "ApplyAndAutoCorrect";
        DownloadManagerCustomData = @{ServerUrl = "http://PullServer:8080/PSDSCPullServer/PSDSCPullServer.svc"; AllowUnsecureConnection = "TRUE"}
    }
}
PullClientConfigId -Output "."
```

## <a name="smb-share"></a>SMB-share

Als de pull-server is ingesteld als een SMB-bestands share in plaats van een webservice, stelt u de **DownloadManagerName** in op **DscFileDownloadManager** in plaats van de **WebDownLoadManager**. De **DscFileDownloadManager** vereist dat u een eigenschap **SourcePath** opgeeft in de **DownloadManagerCustomData**. Met het volgende script wordt de LCM geconfigureerd voor het ophalen van configuraties van een SMB-share met de naam ' SmbDscShare ' op een server met de naam ' CONTOSO-SERVER '.

```powershell
Configuration PullClientConfigId
{
    LocalConfigurationManager
    {
        ConfigurationID = "1C707B86-EF8E-4C29-B7C1-34DA2190AE24";
        RefreshMode = "PULL";
        DownloadManagerName = "DscFileDownloadManager";
        RebootNodeIfNeeded = $true;
        RefreshFrequencyMins = 30;
        ConfigurationModeFrequencyMins = 30;
        ConfigurationMode = "ApplyAndAutoCorrect";
        DownloadManagerCustomData = @{ServerUrl = "\\CONTOSO-SERVER\SmbDscShare"}
    }
}
PullClientConfigId -Output "."
```

## <a name="next-steps"></a>Volgende stappen

Zodra de pull-client is geconfigureerd, kunt u de volgende hand leidingen gebruiken om de volgende stappen uit te voeren:

- [Configuraties publiceren naar een pull-server (v4/V5)](publishConfigs.md)
- [Resources verpakken en uploaden naar een pull-server (v4)](package-upload-resources.md)

## <a name="see-also"></a>Zie ook

- [Een DSC Web-pull-server instellen](pullServer.md)
- [Een DSC SMB-pull-server instellen](pullServerSMB.md)
