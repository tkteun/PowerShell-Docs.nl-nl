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
# <a name="working-with-printers"></a><span data-ttu-id="e6a98-103">Werken met Printers</span><span class="sxs-lookup"><span data-stu-id="e6a98-103">Working with Printers</span></span>
<span data-ttu-id="e6a98-104">U kunt Windows PowerShell gebruiken om printers te beheren met behulp van WMI en de WScript.Network COM-object uit WSH.</span><span class="sxs-lookup"><span data-stu-id="e6a98-104">You can use Windows PowerShell to manage printers by using WMI and the WScript.Network COM object from WSH.</span></span> <span data-ttu-id="e6a98-105">We gebruiken een combinatie van beide hulpprogramma's voor het demonstreren van specifieke taken.</span><span class="sxs-lookup"><span data-stu-id="e6a98-105">We will use a mix of both tools to demonstrate specific tasks.</span></span>

### <a name="listing-printer-connections"></a><span data-ttu-id="e6a98-106">Printerverbindingen van aanbieding</span><span class="sxs-lookup"><span data-stu-id="e6a98-106">Listing Printer Connections</span></span>
<span data-ttu-id="e6a98-107">De eenvoudigste manier om een lijst van de printers die zijn geïnstalleerd op een computer is met de WMI **Win32_Printer** klasse:</span><span class="sxs-lookup"><span data-stu-id="e6a98-107">The simplest way to list the printers installed on a computer is to use the WMI **Win32_Printer** class:</span></span>

```
Get-WmiObject -Class Win32_Printer -ComputerName
```

<span data-ttu-id="e6a98-108">U kunt ook de printers weergeven met behulp van de **WScript.Network** COM-object dat doorgaans in WSH scripts gebruikt wordt:</span><span class="sxs-lookup"><span data-stu-id="e6a98-108">You can also list the printers by using the **WScript.Network** COM object that is typically used in WSH scripts:</span></span>

```
(New-Object -ComObject WScript.Network).EnumPrinterConnections()
```

<span data-ttu-id="e6a98-109">Omdat deze opdracht een verzameling eenvoudige tekenreeks poortnamen en printer apparaat zonder eventuele onderscheidende labels retourneert, is het niet eenvoudig worden geïnterpreteerd.</span><span class="sxs-lookup"><span data-stu-id="e6a98-109">Because this command returns a simple string collection of port names and printer device names without any distinguishing labels, it is not easy to interpret.</span></span>

### <a name="adding-a-network-printer"></a><span data-ttu-id="e6a98-110">Netwerkprinters</span><span class="sxs-lookup"><span data-stu-id="e6a98-110">Adding a Network Printer</span></span>
<span data-ttu-id="e6a98-111">U kunt een nieuwe netwerkprinter toevoegen **WScript.Network**:</span><span class="sxs-lookup"><span data-stu-id="e6a98-111">To add a new network printer, use **WScript.Network**:</span></span>

```
(New-Object -ComObject WScript.Network).AddWindowsPrinterConnection("\\Printserver01\Xerox5")
```

### <a name="setting-a-default-printer"></a><span data-ttu-id="e6a98-112">Instellen van een</span><span class="sxs-lookup"><span data-stu-id="e6a98-112">Setting a Default Printer</span></span>
<span data-ttu-id="e6a98-113">Als u wilt gebruiken WMI om in te stellen van de standaardprinter, de printer zoeken in de **Win32_Printer** verzameling en roep daarna de **SetDefaultPrinter** methode:</span><span class="sxs-lookup"><span data-stu-id="e6a98-113">To use WMI to set the default printer, find the printer in the **Win32_Printer** collection and then invoke the **SetDefaultPrinter** method:</span></span>

```
(Get-WmiObject -ComputerName . -Class Win32_Printer -Filter "Name='HP LaserJet 5Si'").SetDefaultPrinter()
```

<span data-ttu-id="e6a98-114">**WScript.Network** is enigszins eenvoudiger is om te gebruiken, omdat er een **SetDefaultPrinter** methode die de printernaam als argument:</span><span class="sxs-lookup"><span data-stu-id="e6a98-114">**WScript.Network** is a little simpler to use, because it has a **SetDefaultPrinter** method that takes only the printer name as an argument:</span></span>

```
(New-Object -ComObject WScript.Network).SetDefaultPrinter('HP LaserJet 5Si')
```

### <a name="removing-a-printer-connection"></a><span data-ttu-id="e6a98-115">Een verbinding verwijderen</span><span class="sxs-lookup"><span data-stu-id="e6a98-115">Removing a Printer Connection</span></span>
<span data-ttu-id="e6a98-116">U kunt een printerverbinding verwijderen met de **WScript.Network RemovePrinterConnection** methode:</span><span class="sxs-lookup"><span data-stu-id="e6a98-116">To remove a printer connection, use the **WScript.Network RemovePrinterConnection** method:</span></span>

```
(New-Object -ComObject WScript.Network).RemovePrinterConnection("\\Printserver01\Xerox5")
```

