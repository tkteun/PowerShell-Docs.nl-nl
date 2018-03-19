---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: Een pull-client met behulp van configuratie-ID in PowerShell 4.0 instellen
ms.openlocfilehash: 2449a4ddfea5c0ee7096ad7478e80166eb095bbe
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/17/2018
---
# <a name="setting-up-a-pull-client-using-configuration-id-in-powershell-40"></a><span data-ttu-id="31908-103">Een pull-client met behulp van configuratie-ID in PowerShell 4.0 instellen</span><span class="sxs-lookup"><span data-stu-id="31908-103">Setting up a pull client using configuration ID in PowerShell 4.0</span></span>

><span data-ttu-id="31908-104">Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="31908-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="31908-105">Elk doelknooppunt heeft adviseert het gebruik van pull-modus en de URL opgegeven waar deze contact opnemen met de pull-server configuraties ophalen.</span><span class="sxs-lookup"><span data-stu-id="31908-105">Each target node has to be told to use pull mode and given the URL where it can contact the pull server to get configurations.</span></span> <span data-ttu-id="31908-106">U moet de lokale Configuration Manager (LCM) configureren met de benodigde informatie om dit te doen.</span><span class="sxs-lookup"><span data-stu-id="31908-106">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="31908-107">Als u wilt de LCM configureren, moet u een speciaal soort configuratie bekend als een 'metaconfiguratie' maken.</span><span class="sxs-lookup"><span data-stu-id="31908-107">To configure the LCM, you create a special type of configuration known as a "metaconfiguration".</span></span> <span data-ttu-id="31908-108">Zie voor meer informatie over het configureren van de LCM [Windows PowerShell 4.0 Gewenste statusconfiguratie Lokale configuratiebeheerder](metaConfig4.md)</span><span class="sxs-lookup"><span data-stu-id="31908-108">For more information about configuring the LCM, see [Windows PowerShell 4.0 Desired State Configuration Local Configuration Manager](metaConfig4.md)</span></span>

<span data-ttu-id="31908-109">Het volgende script voor het configureren van de LCM naar pull-configuraties van een server met de naam 'PullServer':</span><span class="sxs-lookup"><span data-stu-id="31908-109">The following script configures the LCM to pull configurations from a server named "PullServer":</span></span>

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

<span data-ttu-id="31908-110">In het script **DownloadManagerCustomData** geeft de URL van de pull-server en (voor dit voorbeeld) een onbeveiligde verbinding toestaat.</span><span class="sxs-lookup"><span data-stu-id="31908-110">In the script, **DownloadManagerCustomData** passes the URL of the pull server and (for this example) allows an unsecured connection.</span></span> 

<span data-ttu-id="31908-111">Nadat dit script wordt uitgevoerd, maakt deze een nieuwe uitvoermap met de naam **SimpleMetaConfigurationForPull** en er een MOF-bestand metaconfiguratie plaatst.</span><span class="sxs-lookup"><span data-stu-id="31908-111">After this script runs, it creates a new output folder called **SimpleMetaConfigurationForPull** and puts a metaconfiguration MOF file there.</span></span>

<span data-ttu-id="31908-112">Gebruiken om toe te passen op de configuratie, **Set DscLocalConfigurationManager** met parameters voor **ComputerName** (gebruiken 'localhost') en **pad** (het pad naar de locatie van de doel van het knooppunt localhost.meta.mof-bestand).</span><span class="sxs-lookup"><span data-stu-id="31908-112">To apply the configuration, use **Set-DscLocalConfigurationManager** with parameters for **ComputerName** (use “localhost”) and **Path** (the path to the location of the target node’s localhost.meta.mof file).</span></span> <span data-ttu-id="31908-113">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="31908-113">For example:</span></span> 
```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path . –Verbose.
```

## <a name="configuration-id"></a><span data-ttu-id="31908-114">Configuratie-ID</span><span class="sxs-lookup"><span data-stu-id="31908-114">Configuration ID</span></span>
<span data-ttu-id="31908-115">Het script wordt de **ConfigurationID** eigenschap van de LCM naar een GUID die eerder is gemaakt voor dit doel (u kunt een GUID maken met behulp van de **New-Guid** cmdlet).</span><span class="sxs-lookup"><span data-stu-id="31908-115">The script sets the **ConfigurationID** property of the LCM to a GUID that had been previously created for this purpose (you can create a GUID by using the **New-Guid** cmdlet).</span></span> <span data-ttu-id="31908-116">De **ConfigurationID** is de LCM gebruikt de juiste configuratie vinden op de pull-server.</span><span class="sxs-lookup"><span data-stu-id="31908-116">The **ConfigurationID** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="31908-117">Het MOF-bestand van de configuratie op de pull-server moet de naam `ConfigurationID.mof`, waarbij *ConfigurationID* is de waarde van de **ConfigurationID** eigenschap van het doelknooppunt LCM.</span><span class="sxs-lookup"><span data-stu-id="31908-117">The configuration MOF file on the pull server must be named `ConfigurationID.mof`, where *ConfigurationID* is the value of the **ConfigurationID** property of the target node's LCM.</span></span>

## <a name="pulling-from-an-smb-server"></a><span data-ttu-id="31908-118">Binnenhalen van een SMB-server</span><span class="sxs-lookup"><span data-stu-id="31908-118">Pulling from an SMB server</span></span>

<span data-ttu-id="31908-119">Als de pull-server als een SMB-bestandsshare in plaats van een webservice instellen, geeft u de **DscFileDownloadManager** in plaats van de **WebDownLoadManager**.</span><span class="sxs-lookup"><span data-stu-id="31908-119">If the pull server is set up as an SMB file share, rather than a web service, you specify the **DscFileDownloadManager** rather than the **WebDownLoadManager**.</span></span>
<span data-ttu-id="31908-120">De **DscFileDownloadManager** duurt een **bronpad** in plaats van de eigenschap **ServerUrl**.</span><span class="sxs-lookup"><span data-stu-id="31908-120">The **DscFileDownloadManager** takes a **SourcePath** property instead of **ServerUrl**.</span></span> <span data-ttu-id="31908-121">Het volgende script configureert de LCM om op te halen van de configuraties van een SMB-share met de naam 'SmbDscShare' op een server met de naam 'CONTOSO-SERVER':</span><span class="sxs-lookup"><span data-stu-id="31908-121">The following script configures the LCM to pull configurations from an SMB share named "SmbDscShare" on a server named "CONTOSO-SERVER":</span></span>

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

## <a name="see-also"></a><span data-ttu-id="31908-122">Zie ook</span><span class="sxs-lookup"><span data-stu-id="31908-122">See Also</span></span>

- [<span data-ttu-id="31908-123">Een DSC web pull-server instellen</span><span class="sxs-lookup"><span data-stu-id="31908-123">Setting up a DSC web pull server</span></span>](pullServer.md)
- [<span data-ttu-id="31908-124">Een DSC SMB-pull-server instellen</span><span class="sxs-lookup"><span data-stu-id="31908-124">Setting up a DSC SMB pull server</span></span>](pullServerSMB.md)

