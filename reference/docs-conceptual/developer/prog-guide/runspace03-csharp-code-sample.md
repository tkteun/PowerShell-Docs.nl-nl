---
title: RunSpace03 (C#)-code voorbeeld | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9ac8ab99-1856-4d6f-b30d-c0a18b8dd1fc
caps.latest.revision: 6
ms.openlocfilehash: 28cef037f56f2a101f631d3a234974a8868b4ef9
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/08/2020
ms.locfileid: "80978318"
---
# <a name="runspace03-c-code-sample"></a><span data-ttu-id="3157e-102">Runspace03-codevoorbeeld (C#)</span><span class="sxs-lookup"><span data-stu-id="3157e-102">RunSpace03 (C#) Code Sample</span></span>

<span data-ttu-id="3157e-103">Dit is de C# bron code voor de console toepassing die wordt beschreven in een console toepassing maken die een opgegeven script uitvoert.</span><span class="sxs-lookup"><span data-stu-id="3157e-103">Here is the C# source code for the console application described in "Creating a Console Application That Runs a Specified Script".</span></span> <span data-ttu-id="3157e-104">In dit voor beeld wordt de klasse [System. Management. Automation. Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) gebruikt om een script uit te voeren waarmee proces gegevens worden opgehaald met behulp van de lijst met proces namen die in het script zijn door gegeven.</span><span class="sxs-lookup"><span data-stu-id="3157e-104">This sample uses the [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) class to execute a script that retrieves process information by using the list of process names passed into the script.</span></span> <span data-ttu-id="3157e-105">Hierin ziet u hoe invoer objecten worden door gegeven aan een script en hoe fout objecten worden opgehaald, evenals de uitvoer objecten.</span><span class="sxs-lookup"><span data-stu-id="3157e-105">It shows how to pass input objects to a script and how to retrieve error objects as well as the output objects.</span></span>

> [!NOTE]
> <span data-ttu-id="3157e-106">U kunt het C# bron bestand (runspace03.cs) voor dit voor beeld downloaden met behulp van de micro soft Windows Software Development Kit voor Windows Vista en Microsoft .NET Framework 3,0 runtime-onderdelen.</span><span class="sxs-lookup"><span data-stu-id="3157e-106">You can download the C# source file (runspace03.cs) for this sample using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="3157e-107">Zie [Windows Power Shell installeren en de Windows Power shell-SDK downloaden](/powershell/scripting/developer/installing-the-windows-powershell-sdk)voor instructies voor het downloaden.</span><span class="sxs-lookup"><span data-stu-id="3157e-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="3157e-108">De gedownloade bron bestanden zijn beschikbaar in de **\<Power shell-voor beelden >** map.</span><span class="sxs-lookup"><span data-stu-id="3157e-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="3157e-109">Code voorbeeld</span><span class="sxs-lookup"><span data-stu-id="3157e-109">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace03/Runspace03.cs" range="11-88":::

## <a name="see-also"></a><span data-ttu-id="3157e-110">Zie ook</span><span class="sxs-lookup"><span data-stu-id="3157e-110">See Also</span></span>

[<span data-ttu-id="3157e-111">Hand leiding voor Windows Power shell-programmeurs</span><span class="sxs-lookup"><span data-stu-id="3157e-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="3157e-112">Windows Power shell SDK</span><span class="sxs-lookup"><span data-stu-id="3157e-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
