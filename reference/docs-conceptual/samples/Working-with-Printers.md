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
# <a name="working-with-printers-in-windows"></a><span data-ttu-id="a1f88-104">Werken met printers in Windows</span><span class="sxs-lookup"><span data-stu-id="a1f88-104">Working with Printers in Windows</span></span>

<span data-ttu-id="a1f88-105">U kunt Power shell gebruiken voor het beheren van printers met behulp van WMI en het object **WScript. Network** com van WSH.</span><span class="sxs-lookup"><span data-stu-id="a1f88-105">You can use PowerShell to manage printers by using WMI and the **WScript.Network** COM object from WSH.</span></span> <span data-ttu-id="a1f88-106">We gebruiken een combi natie van beide hulpprogram ma's voor het demonstreren van specifieke taken.</span><span class="sxs-lookup"><span data-stu-id="a1f88-106">We will use a mix of both tools to demonstrate specific tasks.</span></span>

## <a name="listing-printer-connections"></a><span data-ttu-id="a1f88-107">Printer verbindingen weer geven</span><span class="sxs-lookup"><span data-stu-id="a1f88-107">Listing Printer Connections</span></span>

<span data-ttu-id="a1f88-108">De eenvoudigste manier om de printers weer te geven die op een computer zijn geïnstalleerd, is door de WMI- **Win32_Printer** klasse te gebruiken:</span><span class="sxs-lookup"><span data-stu-id="a1f88-108">The simplest way to list the printers installed on a computer is to use the WMI **Win32_Printer** class:</span></span>

```powershell
Get-CimInstance -Class Win32_Printer
```

<span data-ttu-id="a1f88-109">U kunt ook de printers weer geven met behulp van het object **WScript. Network** com dat doorgaans wordt gebruikt in WSH-scripts:</span><span class="sxs-lookup"><span data-stu-id="a1f88-109">You can also list the printers by using the **WScript.Network** COM object that is typically used in WSH scripts:</span></span>

```powershell
(New-Object -ComObject WScript.Network).EnumPrinterConnections()
```

<span data-ttu-id="a1f88-110">Omdat met deze opdracht een eenvoudige teken reeks verzameling van poort namen en printer apparaatnamen zonder onderscheidende labels wordt geretourneerd, is het niet eenvoudig om te interpreteren.</span><span class="sxs-lookup"><span data-stu-id="a1f88-110">Because this command returns a simple string collection of port names and printer device names without any distinguishing labels, it is not easy to interpret.</span></span>

## <a name="adding-a-network-printer"></a><span data-ttu-id="a1f88-111">Een netwerk printer toevoegen</span><span class="sxs-lookup"><span data-stu-id="a1f88-111">Adding a Network Printer</span></span>

<span data-ttu-id="a1f88-112">Als u een nieuwe netwerk printer wilt toevoegen, gebruikt u **WScript. Network**:</span><span class="sxs-lookup"><span data-stu-id="a1f88-112">To add a new network printer, use **WScript.Network**:</span></span>

```powershell
(New-Object -ComObject WScript.Network).AddWindowsPrinterConnection("\\Printserver01\Xerox5")
```

## <a name="setting-a-default-printer"></a><span data-ttu-id="a1f88-113">Een standaard printer instellen</span><span class="sxs-lookup"><span data-stu-id="a1f88-113">Setting a Default Printer</span></span>

<span data-ttu-id="a1f88-114">Als u WMI wilt gebruiken om de standaard printer in te stellen, zoekt u de printer op in de verzameling **Win32_Printer** en roept u de methode **SetDefaultPrinter** aan:</span><span class="sxs-lookup"><span data-stu-id="a1f88-114">To use WMI to set the default printer, find the printer in the **Win32_Printer** collection and then invoke the **SetDefaultPrinter** method:</span></span>

```powershell
$printer = Get-CimInstance -Class Win32_Printer -Filter "Name='HP LaserJet 5Si'"
Invoke-CimMethod -InputObject $printer -MethodName SetDefaultPrinter
```

<span data-ttu-id="a1f88-115">**WScript. Network** is iets eenvoudiger te gebruiken, omdat het een **SetDefaultPrinter** -methode heeft waarbij alleen de printer naam als argument wordt gebruikt:</span><span class="sxs-lookup"><span data-stu-id="a1f88-115">**WScript.Network** is a little simpler to use, because it has a **SetDefaultPrinter** method that takes only the printer name as an argument:</span></span>

```powershell
(New-Object -ComObject WScript.Network).SetDefaultPrinter('HP LaserJet 5Si')
```

## <a name="removing-a-printer-connection"></a><span data-ttu-id="a1f88-116">Een printer verbinding verwijderen</span><span class="sxs-lookup"><span data-stu-id="a1f88-116">Removing a Printer Connection</span></span>

<span data-ttu-id="a1f88-117">Als u een printer verbinding wilt verwijderen, gebruikt u de methode **WScript. Network RemovePrinterConnection** :</span><span class="sxs-lookup"><span data-stu-id="a1f88-117">To remove a printer connection, use the **WScript.Network RemovePrinterConnection** method:</span></span>

```powershell
(New-Object -ComObject WScript.Network).RemovePrinterConnection("\\Printserver01\Xerox5")
```
