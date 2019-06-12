---
title: Windows PowerShell bestanden opmaak | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5d4c8f84-ebd2-4405-bb10-cfc5400d4ad6
caps.latest.revision: 6
ms.openlocfilehash: 3ec127d5ff60754de5d7f1ac73f2965524228b9c
ms.sourcegitcommit: 4ec9e10647b752cc62b1eabb897ada3dc03c93eb
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/11/2019
ms.locfileid: "66830268"
---
# <a name="windows-powershell-formatting-files"></a>Windows PowerShell-opmaakbestanden

Windows PowerShell biedt verschillende opmaak bestanden (. format.ps1xml) die zich in de installatiemap (`$pshome`). Elk van deze bestanden definieert de standaardweergave voor een specifieke set .NET-objecten. Deze bestanden moeten nooit worden gewijzigd. Echter, kunt u ze als uitgangspunt voor het maken van uw eigen aangepaste opmaak-bestanden.

`Certificate.Format.ps1xml` Definieert de objecten worden weergegeven in het certificaatarchief zoals x.509-certificaten en certificaatarchieven.

`DotNetTypes.Format.ps1xml` Hiermee definieert u de weergave van diverse .NET-objecten, zoals CultureInfo, FileVersionInfo en EventLogEntry-objecten.

`FileSystem.Format.ps1xml` Hiermee definieert u de weergave van bestandssysteemobjecten zoals bestands- en -objecten.

`Help.Format.ps1xml` Definieert de verschillende weergaven die worden gebruikt door de [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet, zoals de gedetailleerde, volledige, parameters en voorbeeld-weergaven.

`PowerShellCore.Format.ps1xml` Definieert de weergave van de objecten die worden gegenereerd door de Windows PowerShell core-cmdlets, zoals de objecten die worden geretourneerd door de [Get-Member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) en [Get-geschiedenis](/powershell/module/Microsoft.PowerShell.Core/Get-History) cmdlets.

`PowerShellTrace.Format.ps1xml` Definieert de weergave van traceringsobjecten, zoals systemen die worden gegenereerd door de [Trace-opdracht](/powershell/module/Microsoft.PowerShell.Utility/Trace-Command) cmdlet.

`Registry.Format.ps1xml` Hiermee definieert u de weergave van registerobjecten, zoals de sleutel en post-objecten.

## <a name="see-also"></a>Zie ook

[Schrijven van een Windows PowerShell-Cmdlet](../cmdlet/writing-a-windows-powershell-cmdlet.md)
