---
ms.date: 12/12/2018
keywords: DSC, powershell, configuratie en installatie
title: Instellen van een Pull-Client met behulp van configuratie-ID's in PowerShell 4.0
ms.openlocfilehash: 9adc767e91ff19d373c122a0d493e7b8703d5476
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685478"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-40"></a>Instellen van een Pull-Client met behulp van configuratie-ID's in PowerShell 4.0

>Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0

> [!IMPORTANT]
> De Pull-Server (Windows-functie *DSC-Service*) is een ondersteunde onderdeel van Windows Server maar er zijn geen plannen om nieuwe functies en mogelijkheden bieden. Het verdient aanbeveling om te beginnen met het overstappen clients beheerd [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inclusief functies dan Pull-Server op Windows Server) of een van de community-oplossingen die zijn opgenomen [hier](pullserver.md#community-solutions-for-pull-service).

Voordat u een pull-client instelt, moet u een pull-server instellen. Al deze order niet vereist is, helpt bij het oplossen van problemen en kunt u ervoor zorgen dat de registratie geslaagd is. Als u een pull-server instelt, kunt u de volgende handleidingen:

- [Een DSC SMB-Pull-Server instellen](pullServerSmb.md)
- [Een DSC HTTP-Pull-Server instellen](pullServer.md)

Elk doelknooppunt kan worden geconfigureerd voor het downloaden van configuraties, resources, en zelfs de status rapporteren. De volgende secties laten zien hoe u een pull-client configureren met een SMB-share of een HTTP-DSC-Pull-Server. Wanneer van het knooppunt LCM vernieuwd, wordt het contact opnemen met de geconfigureerde locatie voor het downloaden van de toegewezen configuraties. Als alle vereiste resources niet aanwezig zijn op het knooppunt, wordt deze ze automatisch downloaden van de geconfigureerde locatie. Als het knooppunt is geconfigureerd met een [Report Server](reportServer.md), deze wordt vervolgens rapporteert de status van de bewerking.

## <a name="configure-the-pull-client-lcm"></a>De pull-client LCM configureren

Uitvoeren van een van de voorbeelden hieronder maakt u een nieuwe map voor uitvoer met de naam **PullClientConfigID** en er een metaconfiguration MOF-bestand geplaatst. In dit geval het metaconfiguration MOF-bestand de naam `localhost.meta.mof`.

Aanroepen om toe te passen de configuratie, de **Set-DscLocalConfigurationManager** -cmdlet met de **pad** ingesteld op de locatie van het metaconfiguration MOF-bestand. Bijvoorbeeld:

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a>Configuratie-ID

De volgende set voorbeelden de **ConfigurationID** eigenschap van de LCM om een **Guid** die eerder is gemaakt voor dit doel. De **ConfigurationID** is wat de LCM gebruikt om te vinden van de juiste configuratie op de pull-server. Het MOF-configuratiebestand op de pull-server moet de naam `ConfigurationID.mof`, waarbij *ConfigurationID* is de waarde van de **ConfigurationID** eigenschap van het doelknooppunt LCM. Zie voor meer informatie, [configuraties publiceren naar een Pull-Server (v4/v5)](publishConfigs.md).

U kunt een willekeurige maken **Guid** met behulp van het voorbeeld hieronder.

```powershell
[System.Guid]::NewGuid()
```

## <a name="set-up-a-pull-client-to-download-configurations"></a>Instellen van een Pull-Client voor het downloaden van configuraties

Elke client moet worden geconfigureerd in **Pull** modus en de url van de pull-server waar de configuratie is opgeslagen. Om dit te doen, moet u de lokale Configuration Manager (LCM) configureren met de benodigde informatie. Als u wilt de LCM configureren, u een speciaal soort configuratie maken met een **LocalConfigurationManager** blokkeren. Zie voor meer informatie over het configureren van de LCM [de Local Configuration Manager configureren](../managing-nodes/metaConfig4.md).

## <a name="http-dsc-pull-server"></a>HTTP DSC Pull Server

Als de pull-server is ingesteld als een webservice, stelt u de **DownloadManagerName** naar **WebDownloadManager**. De **WebDownloadManager** dat u opgeeft moet een **ServerUrl** naar de **DownloadManagerCustomData** sleutel. U kunt ook een waarde voor opgeven **AllowUnsecureConnection**, zoals in het onderstaande voorbeeld. Het volgende script wordt de LCM geconfigureerd voor pull-configuraties van een server met de naam 'PullServer'.

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
        DownloadManagerCustomData = @{ServerUrl = "http://PullServer:8080/PSDSCPullServer/PSDSCPullServer.svc"; AllowUnsecureConnection = “TRUE”}
    }
}
PullClientConfigId -Output "."
```

## <a name="smb-share"></a>SMB-Share

Als de pull-server is ingesteld als een SMB-bestandsshare in plaats van een webservice, stelt u de **DownloadManagerName** naar **DscFileDownloadManager** in plaats van de **WebDownLoadManager**. De **DscFileDownloadManager** dat u opgeeft moet een **bronpad** eigenschap in de **DownloadManagerCustomData**. Het volgende script configureert de LCM om op te halen van configuraties van een SMB-share met de naam "SmbDscShare" op een server met de naam 'CONTOSO-SERVER'.

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

Nadat de pull-client is geconfigureerd, kunt u de volgende handleidingen gebruiken om uit te voeren van de volgende stappen:

- [Configuraties publiceren naar een Pull-Server (v4/v5)](publishConfigs.md)
- [Pakket- en Resources uploaden naar een Pull-Server (v4)](package-upload-resources.md)

## <a name="see-also"></a>Zie ook

- [Instellen van een DSC-pull-endwebserver](pullServer.md)
- [Een DSC SMB-pull-server instellen](pullServerSMB.md)
