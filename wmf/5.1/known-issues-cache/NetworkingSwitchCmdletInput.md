---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.topic: conceptual
contributor: vaibch
title: Fout Netwerkswitchbeheer-cmdlets
ms.openlocfilehash: a0f84c35974b6674faba4b0f19a28bd6e2490a96
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893151"
---
# <a name="network-switch-manager-cmdlets-failure"></a><span data-ttu-id="efcf4-103">Fout bij Netwerkswitchbeheer-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="efcf4-103">Network Switch Manager Cmdlets Failure</span></span>

<span data-ttu-id="efcf4-104">De cmdlets Netwerkswitchbeheer kan worden gebruikt voor het beheren van netwerkswitches via WSMAN.</span><span class="sxs-lookup"><span data-stu-id="efcf4-104">The Network Switch Manager cmdlets can be used to manage network switches over WSMAN.</span></span>
<span data-ttu-id="efcf4-105">Enkele cmdlets van deze module zijn geschikt voor het accepteren van waarden van pijplijnen.</span><span class="sxs-lookup"><span data-stu-id="efcf4-105">A few cmdlets of this module are capable of accepting values from pipelines.</span></span>
<span data-ttu-id="efcf4-106">WMF 5.1 Preview-versie mislukt de cmdlets die de waarde van de pijplijn kan accepteren om uit te voeren wanneer de waarden niet via pijplijnen doorgegeven worden.</span><span class="sxs-lookup"><span data-stu-id="efcf4-106">In WMF 5.1 Preview, the cmdlets that can accept value from pipeline fail to execute when the values are not passed through pipelines.</span></span>

<span data-ttu-id="efcf4-107">Als de parameter 'InputObject' niet gebruikt wordt, moet de cmdlet blijven uitvoeren zonder fouten.</span><span class="sxs-lookup"><span data-stu-id="efcf4-107">If "InputObject" parameter is not used, the cmdlet should continue to execute without failures.</span></span>

<span data-ttu-id="efcf4-108">Hier volgt de lijst van betreft de cmdlets dat wil zeggen deze cmdlets kunt accepteren waarde voor parameter 'InputObject' van de pijplijn.</span><span class="sxs-lookup"><span data-stu-id="efcf4-108">Here is the list of affected cmdlets i.e. these cmdlets can accept value for "InputObject" parameter from pipeline.</span></span>
<span data-ttu-id="efcf4-109">Als deze waarde niet is doorgegeven door de pijplijn mislukt de uitvoering van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="efcf4-109">If this value is not passed from pipeline the execution of cmdlet will fail.</span></span>

- <span data-ttu-id="efcf4-110">Disable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="efcf4-110">Disable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="efcf4-111">Enable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="efcf4-111">Enable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="efcf4-112">Remove-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="efcf4-112">Remove-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="efcf4-113">Set-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="efcf4-113">Set-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="efcf4-114">Set-NetworkSwitchPortMode</span><span class="sxs-lookup"><span data-stu-id="efcf4-114">Set-NetworkSwitchPortMode</span></span>
- <span data-ttu-id="efcf4-115">Set-NetworkSwitchPortProperty</span><span class="sxs-lookup"><span data-stu-id="efcf4-115">Set-NetworkSwitchPortProperty</span></span>
- <span data-ttu-id="efcf4-116">Disable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="efcf4-116">Disable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="efcf4-117">Enable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="efcf4-117">Enable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="efcf4-118">Remove-NetworkSwitchVlan</span><span class="sxs-lookup"><span data-stu-id="efcf4-118">Remove-NetworkSwitchVlan</span></span>
- <span data-ttu-id="efcf4-119">Set-NetworkSwitchVlanProperty</span><span class="sxs-lookup"><span data-stu-id="efcf4-119">Set-NetworkSwitchVlanProperty</span></span>

## <a name="resolution"></a><span data-ttu-id="efcf4-120">Oplossing</span><span class="sxs-lookup"><span data-stu-id="efcf4-120">Resolution</span></span>

<span data-ttu-id="efcf4-121">De cmdlets werken prima als de waarde van parameter InputObject erin worden doorgegeven via de pijplijn.</span><span class="sxs-lookup"><span data-stu-id="efcf4-121">The cmdlets work fine when the value of InputObject parameter are passed into it through pipeline.</span></span> <span data-ttu-id="efcf4-122">Er zijn enkele voorbeelden die voor de bovenstaande cmdlets werken:</span><span class="sxs-lookup"><span data-stu-id="efcf4-122">A few examples that work for the above cmdlets are:</span></span>

- `Disable-NetworkSwitchEthernetPort`

  ```powershell
  $port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
  $port | Disable-NetworkSwitchEthernetPort -CimSession $cimSession
  ```

- `Enable-NetworkSwitchEthernetPort`

  ```powershell
  $port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
  $port | Enable-NetworkSwitchEthernetPort -CimSession $cimSession
  ```

- `Remove-NetworkSwitchEthernetPortIPAddress`

  ```powershell
  $port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
  $port | Remove-NetworkSwitchEthernetPortIPAddress -CimSession $cimSession
  ```

- `Set-NetworkSwitchEthernetPortIPAddress`

  ```powershell
  $port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
  $ipAddress = "192.168.10.1"
  $subnetAddress = "255.255.255.0"
  $port | Set-NetworkSwitchEthernetPortIPAddress -IpAddress $ipAddress -SubnetAddress $subnetAddress -CimSession $cimSession
  ```

- `Set-NetworkSwitchPortProperty`

  ```powershell
  $portProperties = @{Caption = "New Caption"}
  $port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
  $port | Set-NetworkSwitchPortProperty -Property $portProperties -CimSession $cimSession
  ```

- `Disable-NetworkSwitchFeature`

  ```powershell
  $feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
  $feature | Disable-NetworkSwitchFeature -CimSession $cimSession
  ```

- `Enable-NetworkSwitchFeature`

  ```powershell
  $feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
  $feature | Enable-NetworkSwitchFeature -CimSession $cimSession
  ```

- `Set-NetworkSwitchVlanProperty`

  ```powershell
  $properties = @{Caption = "New Caption"}
  $vlan = Get-CimInstance -ClassName CIM_NetworkVlan -Namespace root/interop -CimSession $cimSession | Select-Object -First 1
  $vlan | Set-NetworkSwitchVlanProperty -Property $properties -CimSession $cimSession
  ```