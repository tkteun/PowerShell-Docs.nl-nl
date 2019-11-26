---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: Knooppunten bijwerken vanaf een pull-server
ms.openlocfilehash: 516e50b0c39e4747a123307cb3f5e25259ac7ce5
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74417710"
---
# <a name="update-nodes-from-a-pull-server"></a><span data-ttu-id="466d1-103">Knooppunten bijwerken vanaf een pull-server</span><span class="sxs-lookup"><span data-stu-id="466d1-103">Update Nodes from a Pull Server</span></span>

<span data-ttu-id="466d1-104">In de volgende secties wordt ervan uitgegaan dat u al een pull-server hebt ingesteld.</span><span class="sxs-lookup"><span data-stu-id="466d1-104">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="466d1-105">Als u uw pull-server niet hebt ingesteld, kunt u de volgende hand leidingen gebruiken:</span><span class="sxs-lookup"><span data-stu-id="466d1-105">If you have not set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="466d1-106">Een DSC SMB-pull-server instellen</span><span class="sxs-lookup"><span data-stu-id="466d1-106">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="466d1-107">Een DSC HTTP-pull-server instellen</span><span class="sxs-lookup"><span data-stu-id="466d1-107">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="466d1-108">Elk doel knooppunt kan worden geconfigureerd voor het downloaden van configuraties, resources en zelfs het rapporteren van de status ervan.</span><span class="sxs-lookup"><span data-stu-id="466d1-108">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="466d1-109">In dit artikel wordt uitgelegd hoe u bronnen uploadt, zodat ze beschikbaar zijn om te worden gedownload en clients zodanig configureren dat bronnen automatisch worden gedownload.</span><span class="sxs-lookup"><span data-stu-id="466d1-109">This article will show you how to upload resources so they are available to be downloaded, and configure clients to download resources automatically.</span></span> <span data-ttu-id="466d1-110">Wanneer het knoop punt een toegewezen configuratie ontvangt via **pull** -of **Push** (V5), downloadt het automatisch alle resources die vereist zijn voor de configuratie van de locatie die is opgegeven in de LCM.</span><span class="sxs-lookup"><span data-stu-id="466d1-110">When the Node's receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the LCM.</span></span>

## <a name="using-the-update-dscconfiguration-cmdlet"></a><span data-ttu-id="466d1-111">De cmdlet Update-DSCConfiguration gebruiken</span><span class="sxs-lookup"><span data-stu-id="466d1-111">Using the Update-DSCConfiguration cmdlet</span></span>

<span data-ttu-id="466d1-112">Vanaf Power shell 5,0, de cmdlet [Update-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/update-dscconfiguration) , wordt een knoop punt gedwongen de configuratie bij te werken van de pull-server die is geconfigureerd in de LCM.</span><span class="sxs-lookup"><span data-stu-id="466d1-112">Beginning in PowerShell 5.0, the [Update-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/update-dscconfiguration) cmdlet, forces a Node to update its configuration from the Pull Server configured in the LCM.</span></span>

```powershell
Update-DSCConfiguration -ComputerName "Server01"
```

## <a name="using-invoke-cimmethod"></a><span data-ttu-id="466d1-113">Invoke-CIMMethod gebruiken</span><span class="sxs-lookup"><span data-stu-id="466d1-113">Using Invoke-CIMMethod</span></span>

<span data-ttu-id="466d1-114">In Power Shell 4,0 kunt u nog steeds hand matig een pull-client afdwingen om de configuratie bij te werken met [invoke-CIMMethod](/powershell/module/cimcmdlets/invoke-cimmethod).</span><span class="sxs-lookup"><span data-stu-id="466d1-114">In PowerShell 4.0, you can still manually force a Pull Client to update its Configuration using [Invoke-CIMMethod](/powershell/module/cimcmdlets/invoke-cimmethod).</span></span> <span data-ttu-id="466d1-115">In het volgende voor beeld wordt een CIM-sessie met opgegeven referenties gemaakt, wordt de juiste CIM-methode aangeroepen en wordt de sessie verwijderd.</span><span class="sxs-lookup"><span data-stu-id="466d1-115">The following example creates a CIM session with specified credentials, invokes the appropriate CIM method, and removes the session.</span></span>

```powershell
$cimSession = New-CimSession -ComputerName "Server01" -Credential $(Get-Credential)
Invoke-CimMethod -CimSession $cimSession -Namespace 'root/microsoft/windows/desiredstateconfiguration' -Class 'MSFT_DscLocalConfigurationManager' -MethodName 'PerformRequiredConfigurationChecks' -Arguments @{ 'Flags' = [uint32]1 } -Verbose
$cimSession | Remove-CimSession
```

## <a name="see-also"></a><span data-ttu-id="466d1-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="466d1-116">See Also</span></span>

[<span data-ttu-id="466d1-117">De performrequiredconfigurationchecks</span><span class="sxs-lookup"><span data-stu-id="466d1-117">PerformRequiredConfigurationChecks</span></span>](/powershell/scripting/dsc/msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks)
