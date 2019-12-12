---
title: Windows Power shell-indelings bestanden | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5d4c8f84-ebd2-4405-bb10-cfc5400d4ad6
caps.latest.revision: 6
ms.openlocfilehash: 3ec127d5ff60754de5d7f1ac73f2965524228b9c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72355928"
---
# <a name="windows-powershell-formatting-files"></a>Windows PowerShell-opmaakbestanden

Windows Power shell biedt verschillende indelings bestanden (. Format. ps1xml) die zich in de installatiemap (`$pshome`) bevinden. Elk van deze bestanden definieert de standaard weergave voor een specifieke set .NET-objecten. Deze bestanden mogen nooit worden gewijzigd. U kunt deze echter gebruiken als referentie voor het maken van uw eigen aangepaste opmaak bestanden.

`Certificate.Format.ps1xml` definieert de weer gave van objecten in het certificaat archief, zoals x. 509-certificaten en certificaat archieven.

`DotNetTypes.Format.ps1xml` definieert de weer gave van diverse .NET-objecten, zoals Culture info-, FileVersionInfo-en EventLogEntry-objecten.

`FileSystem.Format.ps1xml` definieert de weer gave van bestandssysteem objecten, zoals bestands-en Directory-objecten.

`Help.Format.ps1xml` definieert de verschillende weer gaven die worden gebruikt door de cmdlet [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) , zoals gedetailleerde, volledige, para meters en voorbeeld weergaven.

`PowerShellCore.Format.ps1xml` definieert de weer gave van de objecten die worden gegenereerd door de kern-cmdlets van Windows Power shell, zoals de objecten die worden geretourneerd door de cmdlets [Get-member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) en [Get-History](/powershell/module/Microsoft.PowerShell.Core/Get-History) .

`PowerShellTrace.Format.ps1xml` definieert de weer gave van traceer objecten, zoals die worden gegenereerd door de cmdlet [Trace-opdracht](/powershell/module/Microsoft.PowerShell.Utility/Trace-Command) .

`Registry.Format.ps1xml` definieert de weer gave van register objecten, zoals sleutel-en item objecten.

## <a name="see-also"></a>Zie ook

[Een Windows Power shell-cmdlet schrijven](../cmdlet/writing-a-windows-powershell-cmdlet.md)
