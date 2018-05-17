---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie, setup
title: Een pull-client met behulp van configuratie-ID in PowerShell 4.0 instellen
ms.openlocfilehash: f9bea92f1a2dce94792d72e03bef884d2729f3c0
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/16/2018
---
# <a name="setting-up-a-pull-client-using-configuration-id-in-powershell-40"></a>Een pull-client met behulp van configuratie-ID in PowerShell 4.0 instellen

>Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0

Elk doelknooppunt heeft adviseert het gebruik van pull-modus en de URL opgegeven waar deze contact opnemen met de pull-server configuraties ophalen. U moet de lokale Configuration Manager (LCM) configureren met de benodigde informatie om dit te doen. Als u wilt de LCM configureren, moet u een speciaal soort configuratie bekend als een 'metaconfiguratie' maken. Zie voor meer informatie over het configureren van de LCM [Windows PowerShell 4.0 Desired State Configuration Local Configuration Manager](metaConfig4.md)

Het volgende script voor het configureren van de LCM naar pull-configuraties van een server met de naam 'PullServer':

```powershell
Configuration SimpleMetaConfigurationForPull
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
SimpleMetaConfigurationForPull -Output "."
```

In het script **DownloadManagerCustomData** geeft de URL van de pull-server en (voor dit voorbeeld) een onbeveiligde verbinding toestaat.

Nadat dit script wordt uitgevoerd, maakt deze een nieuwe uitvoermap met de naam **SimpleMetaConfigurationForPull** en er een MOF-bestand metaconfiguratie plaatst.

Gebruiken om toe te passen op de configuratie, **Set DscLocalConfigurationManager** met parameters voor **ComputerName** (gebruiken 'localhost') en **pad** (het pad naar de locatie van de doel van het knooppunt localhost.meta.mof-bestand). Bijvoorbeeld:
```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path . –Verbose.
```

## <a name="configuration-id"></a>Configuratie-ID
Het script wordt de **ConfigurationID** eigenschap van de LCM naar een GUID die eerder is gemaakt voor dit doel (u kunt een GUID maken met behulp van de **New-Guid** cmdlet). De **ConfigurationID** is de LCM gebruikt de juiste configuratie vinden op de pull-server. Het MOF-bestand van de configuratie op de pull-server moet de naam `ConfigurationID.mof`, waarbij *ConfigurationID* is de waarde van de **ConfigurationID** eigenschap van het doelknooppunt LCM.

## <a name="pulling-from-an-smb-server"></a>Binnenhalen van een SMB-server

Als de pull-server als een SMB-bestandsshare in plaats van een webservice instellen, geeft u de **DscFileDownloadManager** in plaats van de **WebDownLoadManager**.
De **DscFileDownloadManager** duurt een **bronpad** in plaats van de eigenschap **ServerUrl**. Het volgende script configureert de LCM om op te halen van de configuraties van een SMB-share met de naam 'SmbDscShare' op een server met de naam 'CONTOSO-SERVER':

```powershell
Configuration SimpleMetaConfigurationForPull
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
SimpleMetaConfigurationForPull -Output "."
```

## <a name="see-also"></a>Zie ook

- [Een DSC web pull-server instellen](pullServer.md)
- [Een DSC SMB-pull-server instellen](pullServerSMB.md)