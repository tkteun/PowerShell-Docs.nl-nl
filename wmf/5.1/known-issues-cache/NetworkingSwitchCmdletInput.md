---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.topic: conceptual
contributor: vaibch
title: Fout Netwerkswitchbeheer-cmdlets
ms.openlocfilehash: 197a25411a82e5d256a9420706535d5411991f1b
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188680"
---
<span data-ttu-id="1d066-103">De cmdlets Netwerkswitchbeheer kan worden gebruikt voor het beheren van netwerkswitches via WSMAN.</span><span class="sxs-lookup"><span data-stu-id="1d066-103">The Network Switch Manager cmdlets can be used to manage network switches over WSMAN.</span></span>
<span data-ttu-id="1d066-104">Er zijn enkele cmdlets van deze module geschikt is voor het accepteren van waarden van pijplijnen.</span><span class="sxs-lookup"><span data-stu-id="1d066-104">A few cmdlets of this module are capable of accepting values from pipelines.</span></span>
<span data-ttu-id="1d066-105">WMF Preview-versie 5.1 mislukt de cmdlets die de waarde van de pijplijn kan accepteren moet worden uitgevoerd wanneer de waarden niet via pijplijnen doorgegeven worden.</span><span class="sxs-lookup"><span data-stu-id="1d066-105">In WMF 5.1 Preview, the cmdlets that can accept value from pipeline fail to execute when the values are not passed through pipelines.</span></span>

<span data-ttu-id="1d066-106">Als de parameter 'InputObject' niet gebruikt wordt, blijven de cmdlet moet worden uitgevoerd zonder fouten.</span><span class="sxs-lookup"><span data-stu-id="1d066-106">If "InputObject" parameter is not used, the cmdlet should continue to execute without failures.</span></span>

<span data-ttu-id="1d066-107">Hier volgt de lijst van beïnvloede cmdlets dat wil zeggen deze cmdlets kunnen accepteren waarde voor parameter 'InputObject' van de pijplijn.</span><span class="sxs-lookup"><span data-stu-id="1d066-107">Here is the list of affected cmdlets i.e. these cmdlets can accept value for "InputObject" parameter from pipeline.</span></span>
<span data-ttu-id="1d066-108">Als deze waarde niet uit de pijplijn wordt doorgegeven mislukt tijdens de uitvoering van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1d066-108">If this value is not passed from pipeline the execution of cmdlet will fail.</span></span>

- <span data-ttu-id="1d066-109">Schakel NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="1d066-109">Disable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="1d066-110">Schakel NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="1d066-110">Enable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="1d066-111">Verwijder NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="1d066-111">Remove-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="1d066-112">Set-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="1d066-112">Set-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="1d066-113">Set-NetworkSwitchPortMode</span><span class="sxs-lookup"><span data-stu-id="1d066-113">Set-NetworkSwitchPortMode</span></span>
- <span data-ttu-id="1d066-114">Set-NetworkSwitchPortProperty</span><span class="sxs-lookup"><span data-stu-id="1d066-114">Set-NetworkSwitchPortProperty</span></span>
- <span data-ttu-id="1d066-115">Schakel NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="1d066-115">Disable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="1d066-116">Schakel NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="1d066-116">Enable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="1d066-117">Verwijder NetworkSwitchVlan</span><span class="sxs-lookup"><span data-stu-id="1d066-117">Remove-NetworkSwitchVlan</span></span>
- <span data-ttu-id="1d066-118">Set-NetworkSwitchVlanProperty</span><span class="sxs-lookup"><span data-stu-id="1d066-118">Set-NetworkSwitchVlanProperty</span></span>

### <a name="resolution"></a><span data-ttu-id="1d066-119">Oplossing</span><span class="sxs-lookup"><span data-stu-id="1d066-119">Resolution</span></span>
<span data-ttu-id="1d066-120">De cmdlets werk fijn wanneer de waarde van parameter InputObject doorgegeven in deze pijplijn.</span><span class="sxs-lookup"><span data-stu-id="1d066-120">The cmdlets work fine when the value of InputObject parameter are passed into it through pipeline.</span></span> <span data-ttu-id="1d066-121">Er zijn enkele voorbeelden die voor de bovenstaande cmdlets werken:</span><span class="sxs-lookup"><span data-stu-id="1d066-121">A few examples that work for the above cmdlets are:</span></span>

- <span data-ttu-id="1d066-122">Schakel NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="1d066-122">Disable-NetworkSwitchEthernetPort</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Disable-NetworkSwitchEthernetPort -CimSession $cimSession
```

- <span data-ttu-id="1d066-123">Schakel NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="1d066-123">Enable-NetworkSwitchEthernetPort</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Enable-NetworkSwitchEthernetPort -CimSession $cimSession
```

- <span data-ttu-id="1d066-124">Verwijder NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="1d066-124">Remove-NetworkSwitchEthernetPortIPAddress</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Remove-NetworkSwitchEthernetPortIPAddress -CimSession $cimSession
```

- <span data-ttu-id="1d066-125">Set-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="1d066-125">Set-NetworkSwitchEthernetPortIPAddress</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$ipAddress = "192.168.10.1"
$subnetAddress = "255.255.255.0"
$port | Set-NetworkSwitchEthernetPortIPAddress -IpAddress $ipAddress -SubnetAddress $subnetAddress -CimSession $cimSession
```

- <span data-ttu-id="1d066-126">Set-NetworkSwitchPortProperty</span><span class="sxs-lookup"><span data-stu-id="1d066-126">Set-NetworkSwitchPortProperty</span></span>
```powershell
$portProperties = @{Caption = "New Caption"}
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Set-NetworkSwitchPortProperty -Property $portProperties -CimSession $cimSession
```

- <span data-ttu-id="1d066-127">Schakel NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="1d066-127">Disable-NetworkSwitchFeature</span></span>
```powershell
$feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
$feature | Disable-NetworkSwitchFeature -CimSession $cimSession
```

- <span data-ttu-id="1d066-128">Schakel NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="1d066-128">Enable-NetworkSwitchFeature</span></span>
```powershell
$feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
$feature | Enable-NetworkSwitchFeature -CimSession $cimSession
```

- <span data-ttu-id="1d066-129">Set-NetworkSwitchVlanProperty</span><span class="sxs-lookup"><span data-stu-id="1d066-129">Set-NetworkSwitchVlanProperty</span></span>
```powershell
$properties = @{Caption = "New Caption"}
$vlan = Get-CimInstance -ClassName CIM_NetworkVlan -Namespace root/interop -CimSession $cimSession | Select-Object -First 1
$vlan | Set-NetworkSwitchVlanProperty -Property $properties -CimSession $cimSession
```
