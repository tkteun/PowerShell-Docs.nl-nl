---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: Met printers werken
description: In deze artikelen wordt beschreven hoe u printers beheert in Windows met WMI-objecten en COM-interfaces.
ms.openlocfilehash: 2606753783043eeae8e9d461e56f0901149cb8e3
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/24/2020
ms.locfileid: "92501079"
---
# <a name="working-with-printers-in-windows"></a>Werken met printers in Windows

U kunt Power shell gebruiken voor het beheren van printers met behulp van WMI en het object **WScript. Network** com van WSH. We gebruiken een combi natie van beide hulpprogram ma's voor het demonstreren van specifieke taken.

## <a name="listing-printer-connections"></a>Printer verbindingen weer geven

De eenvoudigste manier om de printers weer te geven die op een computer zijn geïnstalleerd, is door de WMI- **Win32_Printer** klasse te gebruiken:

```powershell
Get-CimInstance -Class Win32_Printer
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
$printer = Get-CimInstance -Class Win32_Printer -Filter "Name='HP LaserJet 5Si'"
Invoke-CimMethod -InputObject $printer -MethodName SetDefaultPrinter
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
