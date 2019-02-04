---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: Knooppunten bijwerken vanaf een pull-server
ms.openlocfilehash: 4333a5bf82ef45f22a062942ebe93409433623f5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686101"
---
# <a name="update-nodes-from-a-pull-server"></a>Knooppunten bijwerken vanaf een pull-server

De volgende secties wordt ervan uitgegaan dat u al hebt ingesteld om een Pull-Server. Als u niet uw Pull-Server hebt ingesteld, kunt u de volgende handleidingen:

- [Een DSC SMB-Pull-Server instellen](pullServerSmb.md)
- [Een DSC HTTP-Pull-Server instellen](pullServer.md)

Elk doelknooppunt kan worden geconfigureerd voor het downloaden van configuraties, resources, en zelfs de status rapporteren. In dit artikel wordt beschreven hoe het uploaden van resources, zodat ze beschikbaar zijn voor worden gedownload en Configureer clients voor het automatisch downloaden van resources. Wanneer een toegewezen configuratie van het knooppunt ontvangt door middel van **Pull** of **Push** (v5), wordt kan alle resources die vereist zijn de configuratie van de opgegeven locatie in de LCM automatisch gedownload.

## <a name="using-the-update-dscconfiguration-cmdlet"></a>Met behulp van de cmdlet Update-DSCConfiguration

PowerShell 5.0, vanaf de [Update-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/update-dscconfiguration) cmdlet, wordt een knooppunt de configuratie van de Pull-Server is geconfigureerd in de LCM bij te werken.

```powershell
Update-DSCConfiguration -ComputerName "Server01"
```

## <a name="using-invoke-cimmethod"></a>Met behulp van Invoke-CIMMethod

In PowerShell 4.0, kunt u nog steeds handmatig een Pull-Client om bij te werken met de configuratie met behulp dwingen [Invoke-CIMMethod](/powershell/module/cimcmdlets/invoke-cimmethod). Het volgende voorbeeld maakt u een CIM-sessie met de opgegeven referenties, de juiste CIM-methode aanroept en verwijdert u de sessie.

```powershell
$cimSession = New-CimSession -ComputerName "Server01" -Credential $(Get-Credential)
Invoke-CimMethod -CimSession $cimSession -Namespace 'root/microsoft/windows/desiredstateconfiguration' -Class 'MSFT_DscLocalConfigurationManager' -MethodName 'PerformRequiredConfigurationChecks' -Arguments @{ 'Flags' = [uint32]1 } -Verbose
$cimSession | Remove-CimSession
```

## <a name="see-also"></a>Zie ook

[PerformRequiredConfigurationChecks](/powershell/dsc/msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks)
