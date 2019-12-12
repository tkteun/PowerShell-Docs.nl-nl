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
# <a name="working-with-printers"></a><span data-ttu-id="c1c38-103">Met printers werken</span><span class="sxs-lookup"><span data-stu-id="c1c38-103">Working with Printers</span></span>

<span data-ttu-id="c1c38-104">U kunt Windows Power shell gebruiken voor het beheren van printers met behulp van WMI en het object WScript. Network COM van WSH.</span><span class="sxs-lookup"><span data-stu-id="c1c38-104">You can use Windows PowerShell to manage printers by using WMI and the WScript.Network COM object from WSH.</span></span> <span data-ttu-id="c1c38-105">We gebruiken een combi natie van beide hulpprogram ma's voor het demonstreren van specifieke taken.</span><span class="sxs-lookup"><span data-stu-id="c1c38-105">We will use a mix of both tools to demonstrate specific tasks.</span></span>

## <a name="listing-printer-connections"></a><span data-ttu-id="c1c38-106">Printer verbindingen weer geven</span><span class="sxs-lookup"><span data-stu-id="c1c38-106">Listing Printer Connections</span></span>

<span data-ttu-id="c1c38-107">De eenvoudigste manier om de printers weer te geven die op een computer zijn geïnstalleerd, is door de WMI- **Win32_Printer** klasse te gebruiken:</span><span class="sxs-lookup"><span data-stu-id="c1c38-107">The simplest way to list the printers installed on a computer is to use the WMI **Win32_Printer** class:</span></span>

```powershell
Get-WmiObject -Class Win32_Printer
```

<span data-ttu-id="c1c38-108">U kunt ook de printers weer geven met behulp van het object **WScript. Network** com dat doorgaans wordt gebruikt in WSH-scripts:</span><span class="sxs-lookup"><span data-stu-id="c1c38-108">You can also list the printers by using the **WScript.Network** COM object that is typically used in WSH scripts:</span></span>

```powershell
(New-Object -ComObject WScript.Network).EnumPrinterConnections()
```

<span data-ttu-id="c1c38-109">Omdat met deze opdracht een eenvoudige teken reeks verzameling van poort namen en printer apparaatnamen zonder onderscheidende labels wordt geretourneerd, is het niet eenvoudig om te interpreteren.</span><span class="sxs-lookup"><span data-stu-id="c1c38-109">Because this command returns a simple string collection of port names and printer device names without any distinguishing labels, it is not easy to interpret.</span></span>

## <a name="adding-a-network-printer"></a><span data-ttu-id="c1c38-110">Een netwerk printer toevoegen</span><span class="sxs-lookup"><span data-stu-id="c1c38-110">Adding a Network Printer</span></span>

<span data-ttu-id="c1c38-111">Als u een nieuwe netwerk printer wilt toevoegen, gebruikt u **WScript. Network**:</span><span class="sxs-lookup"><span data-stu-id="c1c38-111">To add a new network printer, use **WScript.Network**:</span></span>

```powershell
(New-Object -ComObject WScript.Network).AddWindowsPrinterConnection("\\Printserver01\Xerox5")
```

## <a name="setting-a-default-printer"></a><span data-ttu-id="c1c38-112">Een standaard printer instellen</span><span class="sxs-lookup"><span data-stu-id="c1c38-112">Setting a Default Printer</span></span>

<span data-ttu-id="c1c38-113">Als u WMI wilt gebruiken om de standaard printer in te stellen, zoekt u de printer op in de verzameling **Win32_Printer** en roept u de methode **SetDefaultPrinter** aan:</span><span class="sxs-lookup"><span data-stu-id="c1c38-113">To use WMI to set the default printer, find the printer in the **Win32_Printer** collection and then invoke the **SetDefaultPrinter** method:</span></span>

```powershell
(Get-WmiObject -ComputerName . -Class Win32_Printer -Filter "Name='HP LaserJet 5Si'").SetDefaultPrinter()
```

<span data-ttu-id="c1c38-114">**WScript. Network** is iets eenvoudiger te gebruiken, omdat het een **SetDefaultPrinter** -methode heeft waarbij alleen de printer naam als argument wordt gebruikt:</span><span class="sxs-lookup"><span data-stu-id="c1c38-114">**WScript.Network** is a little simpler to use, because it has a **SetDefaultPrinter** method that takes only the printer name as an argument:</span></span>

```powershell
(New-Object -ComObject WScript.Network).SetDefaultPrinter('HP LaserJet 5Si')
```

## <a name="removing-a-printer-connection"></a><span data-ttu-id="c1c38-115">Een printer verbinding verwijderen</span><span class="sxs-lookup"><span data-stu-id="c1c38-115">Removing a Printer Connection</span></span>

<span data-ttu-id="c1c38-116">Als u een printer verbinding wilt verwijderen, gebruikt u de methode **WScript. Network RemovePrinterConnection** :</span><span class="sxs-lookup"><span data-stu-id="c1c38-116">To remove a printer connection, use the **WScript.Network RemovePrinterConnection** method:</span></span>

```powershell
(New-Object -ComObject WScript.Network).RemovePrinterConnection("\\Printserver01\Xerox5")
```
