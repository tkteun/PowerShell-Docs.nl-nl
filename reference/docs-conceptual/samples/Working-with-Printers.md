---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Met printers werken
ms.assetid: 4f29ead3-f83b-4706-ac3e-f2154ff38dc5
ms.openlocfilehash: 77ebb26369b6a40e9c8c7bbbc52347d614cbf083
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058536"
---
# <a name="working-with-printers"></a><span data-ttu-id="8639c-103">Met printers werken</span><span class="sxs-lookup"><span data-stu-id="8639c-103">Working with Printers</span></span>

<span data-ttu-id="8639c-104">U kunt Windows PowerShell gebruiken voor het beheren van printers met behulp van WMI en het WScript.Network COM-object van WSH.</span><span class="sxs-lookup"><span data-stu-id="8639c-104">You can use Windows PowerShell to manage printers by using WMI and the WScript.Network COM object from WSH.</span></span> <span data-ttu-id="8639c-105">We gebruiken een combinatie van beide hulpprogramma's om specifieke taken te demonstreren.</span><span class="sxs-lookup"><span data-stu-id="8639c-105">We will use a mix of both tools to demonstrate specific tasks.</span></span>

## <a name="listing-printer-connections"></a><span data-ttu-id="8639c-106">Printerverbindingen van aanbieding</span><span class="sxs-lookup"><span data-stu-id="8639c-106">Listing Printer Connections</span></span>

<span data-ttu-id="8639c-107">De eenvoudigste manier om de printers die zijn geïnstalleerd op een computer weer te geven is met de WMI **Win32_Printer** klasse:</span><span class="sxs-lookup"><span data-stu-id="8639c-107">The simplest way to list the printers installed on a computer is to use the WMI **Win32_Printer** class:</span></span>

```powershell
Get-WmiObject -Class Win32_Printer -ComputerName
```

<span data-ttu-id="8639c-108">U kunt ook de printers weergeven met behulp van de **WScript.Network** COM-object dat doorgaans in WSH scripts gebruikt wordt:</span><span class="sxs-lookup"><span data-stu-id="8639c-108">You can also list the printers by using the **WScript.Network** COM object that is typically used in WSH scripts:</span></span>

```powershell
(New-Object -ComObject WScript.Network).EnumPrinterConnections()
```

<span data-ttu-id="8639c-109">Omdat deze opdracht een eenvoudige tekenreeks verzameling poort- en mapnamen van de printer apparaat zonder een onderscheidende labels retourneert, is het niet eenvoudig om te interpreteren.</span><span class="sxs-lookup"><span data-stu-id="8639c-109">Because this command returns a simple string collection of port names and printer device names without any distinguishing labels, it is not easy to interpret.</span></span>

## <a name="adding-a-network-printer"></a><span data-ttu-id="8639c-110">Toevoegen van een netwerkprinter</span><span class="sxs-lookup"><span data-stu-id="8639c-110">Adding a Network Printer</span></span>

<span data-ttu-id="8639c-111">U kunt een nieuwe netwerkprinter toevoegen met **WScript.Network**:</span><span class="sxs-lookup"><span data-stu-id="8639c-111">To add a new network printer, use **WScript.Network**:</span></span>

```powershell
(New-Object -ComObject WScript.Network).AddWindowsPrinterConnection("\\Printserver01\Xerox5")
```

## <a name="setting-a-default-printer"></a><span data-ttu-id="8639c-112">Instellen van een standaardprinter</span><span class="sxs-lookup"><span data-stu-id="8639c-112">Setting a Default Printer</span></span>

<span data-ttu-id="8639c-113">Als u wilt gebruiken WMI om in te stellen van de printer, vinden de printer in het **Win32_Printer** verzameling en vervolgens de **SetDefaultPrinter** methode:</span><span class="sxs-lookup"><span data-stu-id="8639c-113">To use WMI to set the default printer, find the printer in the **Win32_Printer** collection and then invoke the **SetDefaultPrinter** method:</span></span>

```powershell
(Get-WmiObject -ComputerName . -Class Win32_Printer -Filter "Name='HP LaserJet 5Si'").SetDefaultPrinter()
```

<span data-ttu-id="8639c-114">**WScript.Network** is iets eenvoudiger is om te gebruiken, omdat er een **SetDefaultPrinter** methode die alleen de printernaam als een argument:</span><span class="sxs-lookup"><span data-stu-id="8639c-114">**WScript.Network** is a little simpler to use, because it has a **SetDefaultPrinter** method that takes only the printer name as an argument:</span></span>

```powershell
(New-Object -ComObject WScript.Network).SetDefaultPrinter('HP LaserJet 5Si')
```

## <a name="removing-a-printer-connection"></a><span data-ttu-id="8639c-115">Een verbinding verwijderen</span><span class="sxs-lookup"><span data-stu-id="8639c-115">Removing a Printer Connection</span></span>

<span data-ttu-id="8639c-116">Als u wilt verwijderen van een printerverbinding, gebruikt u de **WScript.Network RemovePrinterConnection** methode:</span><span class="sxs-lookup"><span data-stu-id="8639c-116">To remove a printer connection, use the **WScript.Network RemovePrinterConnection** method:</span></span>

```powershell
(New-Object -ComObject WScript.Network).RemovePrinterConnection("\\Printserver01\Xerox5")
```