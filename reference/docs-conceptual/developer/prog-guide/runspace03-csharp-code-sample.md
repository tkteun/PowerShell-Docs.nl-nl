---
ms.date: 09/13/2016
ms.topic: reference
title: Runspace03-codevoorbeeld (C#)
description: Runspace03-codevoorbeeld (C#)
ms.openlocfilehash: cdb08811de13f8bbf5cd91fcbef552c78594b788
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92653841"
---
# <a name="runspace03-c-code-sample"></a><span data-ttu-id="cc8f2-103">Runspace03-codevoorbeeld (C#)</span><span class="sxs-lookup"><span data-stu-id="cc8f2-103">RunSpace03 (C#) Code Sample</span></span>

<span data-ttu-id="cc8f2-104">Hier volgt de C#-bron code voor de console toepassing die wordt beschreven in een console toepassing maken die een opgegeven script uitvoert.</span><span class="sxs-lookup"><span data-stu-id="cc8f2-104">Here is the C# source code for the console application described in "Creating a Console Application That Runs a Specified Script".</span></span> <span data-ttu-id="cc8f2-105">In dit voor beeld wordt de klasse [System. Management. Automation. Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) gebruikt om een script uit te voeren waarmee proces gegevens worden opgehaald met behulp van de lijst met proces namen die in het script zijn door gegeven.</span><span class="sxs-lookup"><span data-stu-id="cc8f2-105">This sample uses the [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) class to execute a script that retrieves process information by using the list of process names passed into the script.</span></span> <span data-ttu-id="cc8f2-106">Hierin ziet u hoe invoer objecten worden door gegeven aan een script en hoe fout objecten worden opgehaald, evenals de uitvoer objecten.</span><span class="sxs-lookup"><span data-stu-id="cc8f2-106">It shows how to pass input objects to a script and how to retrieve error objects as well as the output objects.</span></span>

> [!NOTE]
> <span data-ttu-id="cc8f2-107">U kunt het C#-bron bestand (runspace03.cs) voor dit voor beeld downloaden met behulp van de micro soft Windows Software Development Kit voor Windows Vista en Microsoft .NET Framework 3,0 runtime-onderdelen.</span><span class="sxs-lookup"><span data-stu-id="cc8f2-107">You can download the C# source file (runspace03.cs) for this sample using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="cc8f2-108">Zie [Windows Power Shell installeren en de Windows Power shell-SDK downloaden](/powershell/scripting/developer/installing-the-windows-powershell-sdk)voor instructies voor het downloaden.</span><span class="sxs-lookup"><span data-stu-id="cc8f2-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="cc8f2-109">De gedownloade bron bestanden bevinden zich in de **\<PowerShell Samples>** map.</span><span class="sxs-lookup"><span data-stu-id="cc8f2-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="cc8f2-110">Code voorbeeld</span><span class="sxs-lookup"><span data-stu-id="cc8f2-110">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace03/Runspace03.cs" range="11-88":::

## <a name="see-also"></a><span data-ttu-id="cc8f2-111">Zie ook</span><span class="sxs-lookup"><span data-stu-id="cc8f2-111">See Also</span></span>

[<span data-ttu-id="cc8f2-112">Handleiding voor Windows PowerShell-programmeurs</span><span class="sxs-lookup"><span data-stu-id="cc8f2-112">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="cc8f2-113">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="cc8f2-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
