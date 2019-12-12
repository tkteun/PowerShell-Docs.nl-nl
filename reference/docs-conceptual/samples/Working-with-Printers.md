---
ms.date: 06/05/2017
keywords: Power shell, cmdlet
title: Met printers werken
ms.openlocfilehash: 816388325cc3155f1dbd1bc15fc1736155216092
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030677"
---
# <a name="working-with-printers"></a>Met printers werken

U kunt Windows Power shell gebruiken voor het beheren van printers met behulp van WMI en het object WScript. Network COM van WSH. We gebruiken een combi natie van beide hulpprogram ma's voor het demonstreren van specifieke taken.

## <a name="listing-printer-connections"></a>Printer verbindingen weer geven

De eenvoudigste manier om de printers weer te geven die op een computer zijn geïnstalleerd, is door de WMI- **Win32_Printer** klasse te gebruiken:

```powershell
Get-WmiObject -Class Win32_Printer
```

U kunt ook de printers weer geven met behulp van het object **WScript. Network** com dat doorgaans wordt gebruikt in WSH-scripts:

```powershell
(New-Object -ComObject WScript.Network).EnumPrinterConnections()
```

Omdat met deze opdracht een eenvoudige teken reeks verzameling van poort namen en printer apparaatnamen zonder onderscheidende labels wordt geretourneerd, is het niet eenvoudig om te interpreteren.

## <a name="adding-a-network-printer"></a>Een netwerk printer toevoegen

Als u een nieuwe netwerk printer wilt toevoegen, gebruikt u **WScript. Network**:

```powershell
(New-Object -ComObject WScript.Network).AddWindowsPrinterConnection("\\Printserver01\Xerox5")
```

## <a name="setting-a-default-printer"></a>Een standaard printer instellen

Als u WMI wilt gebruiken om de standaard printer in te stellen, zoekt u de printer op in de verzameling **Win32_Printer** en roept u de methode **SetDefaultPrinter** aan:

```powershell
(Get-WmiObject -ComputerName . -Class Win32_Printer -Filter "Name='HP LaserJet 5Si'").SetDefaultPrinter()
```

**WScript. Network** is iets eenvoudiger te gebruiken, omdat het een **SetDefaultPrinter** -methode heeft waarbij alleen de printer naam als argument wordt gebruikt:

```powershell
(New-Object -ComObject WScript.Network).SetDefaultPrinter('HP LaserJet 5Si')
```

## <a name="removing-a-printer-connection"></a>Een printer verbinding verwijderen

Als u een printer verbinding wilt verwijderen, gebruikt u de methode **WScript. Network RemovePrinterConnection** :

```powershell
(New-Object -ComObject WScript.Network).RemovePrinterConnection("\\Printserver01\Xerox5")
```
