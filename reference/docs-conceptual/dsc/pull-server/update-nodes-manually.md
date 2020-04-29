---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: Knooppunten bijwerken vanaf een pull-server
ms.openlocfilehash: fa59a2f6574db2dbc96621be4326f1d5a55e5de9
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "80500661"
---
# <a name="update-nodes-from-a-pull-server"></a>Knooppunten bijwerken vanaf een pull-server

In de volgende secties wordt ervan uitgegaan dat u al een pull-server hebt ingesteld. Als u uw pull-server niet hebt ingesteld, kunt u de volgende hand leidingen gebruiken:

- [Een DSC SMB-pull-server instellen](pullServerSmb.md)
- [Een DSC HTTP-pull-server instellen](pullServer.md)

Elk doel knooppunt kan worden geconfigureerd voor het downloaden van configuraties, resources en zelfs het rapporteren van de status ervan. In dit artikel wordt uitgelegd hoe u bronnen uploadt, zodat ze beschikbaar zijn om te worden gedownload en clients zodanig configureren dat bronnen automatisch worden gedownload. Wanneer het knoop punt een toegewezen configuratie ontvangt via **pull** -of **Push** (V5), downloadt het automatisch alle resources die vereist zijn voor de configuratie van de locatie die is opgegeven in de LCM.

## <a name="using-the-update-dscconfiguration-cmdlet"></a>De cmdlet Update-DSCConfiguration gebruiken

Vanaf Power shell 5,0, de cmdlet [Update-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/update-dscconfiguration) , wordt een knoop punt gedwongen de configuratie bij te werken van de pull-server die is geconfigureerd in de LCM.

```powershell
Update-DSCConfiguration -ComputerName "Server01"
```

## <a name="using-invoke-cimmethod"></a>Invoke-CIMMethod gebruiken

In Power Shell 4,0 kunt u nog steeds hand matig een pull-client afdwingen om de configuratie bij te werken met [invoke-CIMMethod](/powershell/module/cimcmdlets/invoke-cimmethod). In het volgende voor beeld wordt een CIM-sessie met opgegeven referenties gemaakt, wordt de juiste CIM-methode aangeroepen en wordt de sessie verwijderd.

```powershell
$cimSession = New-CimSession -ComputerName "Server01" -Credential $(Get-Credential)
Invoke-CimMethod -CimSession $cimSession -Namespace 'root/microsoft/windows/desiredstateconfiguration' -Class 'MSFT_DscLocalConfigurationManager' -MethodName 'PerformRequiredConfigurationChecks' -Arguments @{ 'Flags' = [uint32]1 } -Verbose
$cimSession | Remove-CimSession
```

## <a name="see-also"></a>Zie ook

[De performrequiredconfigurationchecks](../reference/mof-classes/msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks.md)
