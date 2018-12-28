---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Met printers werken
ms.assetid: 4f29ead3-f83b-4706-ac3e-f2154ff38dc5
ms.openlocfilehash: 5638629fdf79371c8eff9ee9194b642034250fff
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404537"
---
# <a name="working-with-printers"></a>Met printers werken

U kunt Windows PowerShell gebruiken voor het beheren van printers met behulp van WMI en het WScript.Network COM-object van WSH. We gebruiken een combinatie van beide hulpprogramma's om specifieke taken te demonstreren.

### <a name="listing-printer-connections"></a>Printerverbindingen van aanbieding

De eenvoudigste manier om de printers die zijn geïnstalleerd op een computer weer te geven is met de WMI **Win32_Printer** klasse:

```powershell
Get-WmiObject -Class Win32_Printer -ComputerName
```

U kunt ook de printers weergeven met behulp van de **WScript.Network** COM-object dat doorgaans in WSH scripts gebruikt wordt:

```powershell
(New-Object -ComObject WScript.Network).EnumPrinterConnections()
```

Omdat deze opdracht een eenvoudige tekenreeks verzameling poort- en mapnamen van de printer apparaat zonder een onderscheidende labels retourneert, is het niet eenvoudig om te interpreteren.

### <a name="adding-a-network-printer"></a>Toevoegen van een netwerkprinter

U kunt een nieuwe netwerkprinter toevoegen met **WScript.Network**:

```powershell
(New-Object -ComObject WScript.Network).AddWindowsPrinterConnection("\\Printserver01\Xerox5")
```

### <a name="setting-a-default-printer"></a>Instellen van een standaardprinter

Als u wilt gebruiken WMI om in te stellen van de printer, vinden de printer in het **Win32_Printer** verzameling en vervolgens de **SetDefaultPrinter** methode:

```powershell
(Get-WmiObject -ComputerName . -Class Win32_Printer -Filter "Name='HP LaserJet 5Si'").SetDefaultPrinter()
```

**WScript.Network** is iets eenvoudiger is om te gebruiken, omdat er een **SetDefaultPrinter** methode die alleen de printernaam als een argument:

```powershell
(New-Object -ComObject WScript.Network).SetDefaultPrinter('HP LaserJet 5Si')
```

### <a name="removing-a-printer-connection"></a>Een verbinding verwijderen

Als u wilt verwijderen van een printerverbinding, gebruikt u de **WScript.Network RemovePrinterConnection** methode:

```powershell
(New-Object -ComObject WScript.Network).RemovePrinterConnection("\\Printserver01\Xerox5")
```