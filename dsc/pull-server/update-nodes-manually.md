---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: Knooppunten van een Pull-Server bijwerken
ms.openlocfilehash: 4333a5bf82ef45f22a062942ebe93409433623f5
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53403878"
---
# <a name="update-nodes-from-a-pull-server"></a><span data-ttu-id="7f4c8-103">Knooppunten van een Pull-Server bijwerken</span><span class="sxs-lookup"><span data-stu-id="7f4c8-103">Update Nodes from a Pull Server</span></span>

<span data-ttu-id="7f4c8-104">De volgende secties wordt ervan uitgegaan dat u al hebt ingesteld om een Pull-Server.</span><span class="sxs-lookup"><span data-stu-id="7f4c8-104">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="7f4c8-105">Als u niet uw Pull-Server hebt ingesteld, kunt u de volgende handleidingen:</span><span class="sxs-lookup"><span data-stu-id="7f4c8-105">If you have not set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="7f4c8-106">Een DSC SMB-Pull-Server instellen</span><span class="sxs-lookup"><span data-stu-id="7f4c8-106">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="7f4c8-107">Een DSC HTTP-Pull-Server instellen</span><span class="sxs-lookup"><span data-stu-id="7f4c8-107">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="7f4c8-108">Elk doelknooppunt kan worden geconfigureerd voor het downloaden van configuraties, resources, en zelfs de status rapporteren.</span><span class="sxs-lookup"><span data-stu-id="7f4c8-108">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="7f4c8-109">In dit artikel wordt beschreven hoe het uploaden van resources, zodat ze beschikbaar zijn voor worden gedownload en Configureer clients voor het automatisch downloaden van resources.</span><span class="sxs-lookup"><span data-stu-id="7f4c8-109">This article will show you how to upload resources so they are available to be downloaded, and configure clients to download resources automatically.</span></span> <span data-ttu-id="7f4c8-110">Wanneer een toegewezen configuratie van het knooppunt ontvangt door middel van **Pull** of **Push** (v5), wordt kan alle resources die vereist zijn de configuratie van de opgegeven locatie in de LCM automatisch gedownload.</span><span class="sxs-lookup"><span data-stu-id="7f4c8-110">When the Node's receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the LCM.</span></span>

## <a name="using-the-update-dscconfiguration-cmdlet"></a><span data-ttu-id="7f4c8-111">Met behulp van de cmdlet Update-DSCConfiguration</span><span class="sxs-lookup"><span data-stu-id="7f4c8-111">Using the Update-DSCConfiguration cmdlet</span></span>

<span data-ttu-id="7f4c8-112">PowerShell 5.0, vanaf de [Update-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/update-dscconfiguration) cmdlet, wordt een knooppunt de configuratie van de Pull-Server is geconfigureerd in de LCM bij te werken.</span><span class="sxs-lookup"><span data-stu-id="7f4c8-112">Beginning in PowerShell 5.0, the [Update-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/update-dscconfiguration) cmdlet, forces a Node to update its configuration from the Pull Server configured in the LCM.</span></span>

```powershell
Update-DSCConfiguration -ComputerName "Server01"
```

## <a name="using-invoke-cimmethod"></a><span data-ttu-id="7f4c8-113">Met behulp van Invoke-CIMMethod</span><span class="sxs-lookup"><span data-stu-id="7f4c8-113">Using Invoke-CIMMethod</span></span>

<span data-ttu-id="7f4c8-114">In PowerShell 4.0, kunt u nog steeds handmatig een Pull-Client om bij te werken met de configuratie met behulp dwingen [Invoke-CIMMethod](/powershell/module/cimcmdlets/invoke-cimmethod).</span><span class="sxs-lookup"><span data-stu-id="7f4c8-114">In PowerShell 4.0, you can still manually force a Pull Client to update its Configuration using [Invoke-CIMMethod](/powershell/module/cimcmdlets/invoke-cimmethod).</span></span> <span data-ttu-id="7f4c8-115">Het volgende voorbeeld maakt u een CIM-sessie met de opgegeven referenties, de juiste CIM-methode aanroept en verwijdert u de sessie.</span><span class="sxs-lookup"><span data-stu-id="7f4c8-115">The following example creates a CIM session with specified credentials, invokes the appropriate CIM method, and removes the session.</span></span>

```powershell
$cimSession = New-CimSession -ComputerName "Server01" -Credential $(Get-Credential)
Invoke-CimMethod -CimSession $cimSession -Namespace 'root/microsoft/windows/desiredstateconfiguration' -Class 'MSFT_DscLocalConfigurationManager' -MethodName 'PerformRequiredConfigurationChecks' -Arguments @{ 'Flags' = [uint32]1 } -Verbose
$cimSession | Remove-CimSession
```

## <a name="see-also"></a><span data-ttu-id="7f4c8-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="7f4c8-116">See Also</span></span>

[<span data-ttu-id="7f4c8-117">De PerformRequiredConfigurationChecks</span><span class="sxs-lookup"><span data-stu-id="7f4c8-117">PerformRequiredConfigurationChecks</span></span>](/powershell/dsc/msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks)
