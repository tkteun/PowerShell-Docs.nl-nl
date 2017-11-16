---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Werken met Printers
ms.assetid: 4f29ead3-f83b-4706-ac3e-f2154ff38dc5
ms.openlocfilehash: c8b4d728c9fddd39e1aeb56d6f9b8ffffe4c7292
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/03/2017
---
# <a name="working-with-printers"></a>Werken met Printers
U kunt Windows PowerShell gebruiken om printers te beheren met behulp van WMI en de WScript.Network COM-object uit WSH. We gebruiken een combinatie van beide hulpprogramma's voor het demonstreren van specifieke taken.

### <a name="listing-printer-connections"></a>Printerverbindingen van aanbieding
De eenvoudigste manier om een lijst van de printers die zijn geïnstalleerd op een computer is met de WMI **Win32_Printer** klasse:

```
Get-WmiObject -Class Win32_Printer -ComputerName
```

U kunt ook de printers weergeven met behulp van de **WScript.Network** COM-object dat doorgaans in WSH scripts gebruikt wordt:

```
(New-Object -ComObject WScript.Network).EnumPrinterConnections()
```

Omdat deze opdracht een verzameling eenvoudige tekenreeks poortnamen en printer apparaat zonder eventuele onderscheidende labels retourneert, is het niet eenvoudig worden geïnterpreteerd.

### <a name="adding-a-network-printer"></a>Netwerkprinters
U kunt een nieuwe netwerkprinter toevoegen **WScript.Network**:

```
(New-Object -ComObject WScript.Network).AddWindowsPrinterConnection("\\Printserver01\Xerox5")
```

### <a name="setting-a-default-printer"></a>Instellen van een
Als u wilt gebruiken WMI om in te stellen van de standaardprinter, de printer zoeken in de **Win32_Printer** verzameling en roep daarna de **SetDefaultPrinter** methode:

```
(Get-WmiObject -ComputerName . -Class Win32_Printer -Filter "Name='HP LaserJet 5Si'").SetDefaultPrinter()
```

**WScript.Network** is enigszins eenvoudiger is om te gebruiken, omdat er een **SetDefaultPrinter** methode die de printernaam als argument:

```
(New-Object -ComObject WScript.Network).SetDefaultPrinter('HP LaserJet 5Si')
```

### <a name="removing-a-printer-connection"></a>Een verbinding verwijderen
U kunt een printerverbinding verwijderen met de **WScript.Network RemovePrinterConnection** methode:

```
(New-Object -ComObject WScript.Network).RemovePrinterConnection("\\Printserver01\Xerox5")
```

