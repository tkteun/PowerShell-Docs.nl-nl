---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Met printers werken
ms.assetid: 4f29ead3-f83b-4706-ac3e-f2154ff38dc5
ms.openlocfilehash: 5638629fdf79371c8eff9ee9194b642034250fff
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="working-with-printers"></a>Met printers werken

U kunt Windows PowerShell gebruiken om printers te beheren met behulp van WMI en de WScript.Network COM-object uit WSH. We gebruiken een combinatie van beide hulpprogramma's voor het demonstreren van specifieke taken.

### <a name="listing-printer-connections"></a>Printerverbindingen van aanbieding

De eenvoudigste manier om een lijst van de printers die zijn geïnstalleerd op een computer is met de WMI **Win32_Printer** klasse:

```powershell
Get-WmiObject -Class Win32_Printer -ComputerName
```

U kunt ook de printers weergeven met behulp van de **WScript.Network** COM-object dat doorgaans in WSH scripts gebruikt wordt:

```powershell
(New-Object -ComObject WScript.Network).EnumPrinterConnections()
```

Omdat deze opdracht een verzameling eenvoudige tekenreeks poortnamen en printer apparaat zonder eventuele onderscheidende labels retourneert, is het niet eenvoudig worden geïnterpreteerd.

### <a name="adding-a-network-printer"></a>Netwerkprinters

U kunt een nieuwe netwerkprinter toevoegen **WScript.Network**:

```powershell
(New-Object -ComObject WScript.Network).AddWindowsPrinterConnection("\\Printserver01\Xerox5")
```

### <a name="setting-a-default-printer"></a>Instellen van een

Als u wilt gebruiken WMI om in te stellen van de standaardprinter, de printer zoeken in de **Win32_Printer** verzameling en roep daarna de **SetDefaultPrinter** methode:

```powershell
(Get-WmiObject -ComputerName . -Class Win32_Printer -Filter "Name='HP LaserJet 5Si'").SetDefaultPrinter()
```

**WScript.Network** is enigszins eenvoudiger is om te gebruiken, omdat er een **SetDefaultPrinter** methode die de printernaam als argument:

```powershell
(New-Object -ComObject WScript.Network).SetDefaultPrinter('HP LaserJet 5Si')
```

### <a name="removing-a-printer-connection"></a>Een verbinding verwijderen

U kunt een printerverbinding verwijderen met de **WScript.Network RemovePrinterConnection** methode:

```powershell
(New-Object -ComObject WScript.Network).RemovePrinterConnection("\\Printserver01\Xerox5")
```