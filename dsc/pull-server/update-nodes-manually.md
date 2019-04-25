---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: Knooppunten bijwerken vanaf een pull-server
ms.openlocfilehash: 4333a5bf82ef45f22a062942ebe93409433623f5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079095"
---
# <a name="update-nodes-from-a-pull-server"></a><span data-ttu-id="b8556-103">Knooppunten bijwerken vanaf een pull-server</span><span class="sxs-lookup"><span data-stu-id="b8556-103">Update Nodes from a Pull Server</span></span>

<span data-ttu-id="b8556-104">De volgende secties wordt ervan uitgegaan dat u al hebt ingesteld om een Pull-Server.</span><span class="sxs-lookup"><span data-stu-id="b8556-104">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="b8556-105">Als u niet uw Pull-Server hebt ingesteld, kunt u de volgende handleidingen:</span><span class="sxs-lookup"><span data-stu-id="b8556-105">If you have not set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="b8556-106">Een DSC SMB-Pull-Server instellen</span><span class="sxs-lookup"><span data-stu-id="b8556-106">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="b8556-107">Een DSC HTTP-Pull-Server instellen</span><span class="sxs-lookup"><span data-stu-id="b8556-107">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="b8556-108">Elk doelknooppunt kan worden geconfigureerd voor het downloaden van configuraties, resources, en zelfs de status rapporteren.</span><span class="sxs-lookup"><span data-stu-id="b8556-108">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="b8556-109">In dit artikel wordt beschreven hoe het uploaden van resources, zodat ze beschikbaar zijn voor worden gedownload en Configureer clients voor het automatisch downloaden van resources.</span><span class="sxs-lookup"><span data-stu-id="b8556-109">This article will show you how to upload resources so they are available to be downloaded, and configure clients to download resources automatically.</span></span> <span data-ttu-id="b8556-110">Wanneer een toegewezen configuratie van het knooppunt ontvangt door middel van **Pull** of **Push** (v5), wordt kan alle resources die vereist zijn de configuratie van de opgegeven locatie in de LCM automatisch gedownload.</span><span class="sxs-lookup"><span data-stu-id="b8556-110">When the Node's receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the LCM.</span></span>

## <a name="using-the-update-dscconfiguration-cmdlet"></a><span data-ttu-id="b8556-111">Met behulp van de cmdlet Update-DSCConfiguration</span><span class="sxs-lookup"><span data-stu-id="b8556-111">Using the Update-DSCConfiguration cmdlet</span></span>

<span data-ttu-id="b8556-112">PowerShell 5.0, vanaf de [Update-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/update-dscconfiguration) cmdlet, wordt een knooppunt de configuratie van de Pull-Server is geconfigureerd in de LCM bij te werken.</span><span class="sxs-lookup"><span data-stu-id="b8556-112">Beginning in PowerShell 5.0, the [Update-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/update-dscconfiguration) cmdlet, forces a Node to update its configuration from the Pull Server configured in the LCM.</span></span>

```powershell
Update-DSCConfiguration -ComputerName "Server01"
```

## <a name="using-invoke-cimmethod"></a><span data-ttu-id="b8556-113">Met behulp van Invoke-CIMMethod</span><span class="sxs-lookup"><span data-stu-id="b8556-113">Using Invoke-CIMMethod</span></span>

<span data-ttu-id="b8556-114">In PowerShell 4.0, kunt u nog steeds handmatig een Pull-Client om bij te werken met de configuratie met behulp dwingen [Invoke-CIMMethod](/powershell/module/cimcmdlets/invoke-cimmethod).</span><span class="sxs-lookup"><span data-stu-id="b8556-114">In PowerShell 4.0, you can still manually force a Pull Client to update its Configuration using [Invoke-CIMMethod](/powershell/module/cimcmdlets/invoke-cimmethod).</span></span> <span data-ttu-id="b8556-115">Het volgende voorbeeld maakt u een CIM-sessie met de opgegeven referenties, de juiste CIM-methode aanroept en verwijdert u de sessie.</span><span class="sxs-lookup"><span data-stu-id="b8556-115">The following example creates a CIM session with specified credentials, invokes the appropriate CIM method, and removes the session.</span></span>

```powershell
$cimSession = New-CimSession -ComputerName "Server01" -Credential $(Get-Credential)
Invoke-CimMethod -CimSession $cimSession -Namespace 'root/microsoft/windows/desiredstateconfiguration' -Class 'MSFT_DscLocalConfigurationManager' -MethodName 'PerformRequiredConfigurationChecks' -Arguments @{ 'Flags' = [uint32]1 } -Verbose
$cimSession | Remove-CimSession
```

## <a name="see-also"></a><span data-ttu-id="b8556-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="b8556-116">See Also</span></span>

[<span data-ttu-id="b8556-117">PerformRequiredConfigurationChecks</span><span class="sxs-lookup"><span data-stu-id="b8556-117">PerformRequiredConfigurationChecks</span></span>](/powershell/dsc/msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks)
