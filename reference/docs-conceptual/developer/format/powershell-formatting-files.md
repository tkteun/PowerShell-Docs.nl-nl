---
ms.date: 09/13/2016
ms.topic: reference
title: Windows PowerShell-opmaakbestanden
description: Windows PowerShell-opmaakbestanden
ms.openlocfilehash: 7fa58a3463dc4b2a23d38d161d83387744334d44
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92666362"
---
# <a name="windows-powershell-formatting-files"></a>Windows PowerShell-opmaakbestanden

Windows Power shell biedt verschillende indelings bestanden (.format.ps1XML) die zich in de installatiemap ( `$pshome` ) bevinden. Elk van deze bestanden definieert de standaard weergave voor een specifieke set .NET-objecten. Deze bestanden mogen nooit worden gewijzigd. U kunt deze echter gebruiken als referentie voor het maken van uw eigen aangepaste opmaak bestanden.

`Certificate.Format.ps1xml` Hiermee wordt de weer gave van objecten in het certificaat archief gedefinieerd, zoals x. 509-certificaten en certificaat archieven.

`DotNetTypes.Format.ps1xml` Hiermee wordt de weer gave van diverse .NET-objecten gedefinieerd, zoals Culture info-, FileVersionInfo-en EventLogEntry-objecten.

`FileSystem.Format.ps1xml` Hiermee definieert u de weer gave van bestandssysteem objecten, zoals bestands-en Directory-objecten.

`Help.Format.ps1xml` Hiermee worden de verschillende weer gaven gedefinieerd die worden gebruikt door de cmdlet [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) , zoals de gedetailleerde, volledige, para meters en voorbeeld weergaven.

`PowerShellCore.Format.ps1xml` Hiermee wordt de weer gave gedefinieerd van de objecten die worden gegenereerd door de kern-cmdlets van Windows Power shell, zoals de objecten die worden geretourneerd door de cmdlets [Get-member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) en [Get-History](/powershell/module/Microsoft.PowerShell.Core/Get-History) .

`PowerShellTrace.Format.ps1xml` Hiermee wordt de weer gave van traceer objecten gedefinieerd, zoals die worden gegenereerd door de cmdlet [Trace-opdracht](/powershell/module/Microsoft.PowerShell.Utility/Trace-Command) .

`Registry.Format.ps1xml` Hiermee definieert u de weer gave van register objecten, zoals sleutel-en item objecten.

## <a name="see-also"></a>Zie ook

[Een Windows PowerShell-cmdlet schrijven](../cmdlet/writing-a-windows-powershell-cmdlet.md)
