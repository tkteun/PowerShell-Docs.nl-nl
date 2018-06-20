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
De cmdlets Netwerkswitchbeheer kan worden gebruikt voor het beheren van netwerkswitches via WSMAN.
Er zijn enkele cmdlets van deze module geschikt is voor het accepteren van waarden van pijplijnen.
WMF Preview-versie 5.1 mislukt de cmdlets die de waarde van de pijplijn kan accepteren moet worden uitgevoerd wanneer de waarden niet via pijplijnen doorgegeven worden.

Als de parameter 'InputObject' niet gebruikt wordt, blijven de cmdlet moet worden uitgevoerd zonder fouten.

Hier volgt de lijst van beïnvloede cmdlets dat wil zeggen deze cmdlets kunnen accepteren waarde voor parameter 'InputObject' van de pijplijn.
Als deze waarde niet uit de pijplijn wordt doorgegeven mislukt tijdens de uitvoering van de cmdlet.

- Schakel NetworkSwitchEthernetPort
- Schakel NetworkSwitchEthernetPort
- Verwijder NetworkSwitchEthernetPortIPAddress
- Set-NetworkSwitchEthernetPortIPAddress
- Set-NetworkSwitchPortMode
- Set-NetworkSwitchPortProperty
- Schakel NetworkSwitchFeature
- Schakel NetworkSwitchFeature
- Verwijder NetworkSwitchVlan
- Set-NetworkSwitchVlanProperty

### <a name="resolution"></a>Oplossing
De cmdlets werk fijn wanneer de waarde van parameter InputObject doorgegeven in deze pijplijn. Er zijn enkele voorbeelden die voor de bovenstaande cmdlets werken:

- Schakel NetworkSwitchEthernetPort
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Disable-NetworkSwitchEthernetPort -CimSession $cimSession
```

- Schakel NetworkSwitchEthernetPort
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Enable-NetworkSwitchEthernetPort -CimSession $cimSession
```

- Verwijder NetworkSwitchEthernetPortIPAddress
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Remove-NetworkSwitchEthernetPortIPAddress -CimSession $cimSession
```

- Set-NetworkSwitchEthernetPortIPAddress
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$ipAddress = "192.168.10.1"
$subnetAddress = "255.255.255.0"
$port | Set-NetworkSwitchEthernetPortIPAddress -IpAddress $ipAddress -SubnetAddress $subnetAddress -CimSession $cimSession
```

- Set-NetworkSwitchPortProperty
```powershell
$portProperties = @{Caption = "New Caption"}
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Set-NetworkSwitchPortProperty -Property $portProperties -CimSession $cimSession
```

- Schakel NetworkSwitchFeature
```powershell
$feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
$feature | Disable-NetworkSwitchFeature -CimSession $cimSession
```

- Schakel NetworkSwitchFeature
```powershell
$feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
$feature | Enable-NetworkSwitchFeature -CimSession $cimSession
```

- Set-NetworkSwitchVlanProperty
```powershell
$properties = @{Caption = "New Caption"}
$vlan = Get-CimInstance -ClassName CIM_NetworkVlan -Namespace root/interop -CimSession $cimSession | Select-Object -First 1
$vlan | Set-NetworkSwitchVlanProperty -Property $properties -CimSession $cimSession
```
