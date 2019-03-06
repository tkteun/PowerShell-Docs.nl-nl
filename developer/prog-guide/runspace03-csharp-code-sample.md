---
title: RunSpace03 (C#) codevoorbeeld | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9ac8ab99-1856-4d6f-b30d-c0a18b8dd1fc
caps.latest.revision: 6
ms.openlocfilehash: 0e80f4d850a7c6dc044526a56b92f16eea4040b5
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429904"
---
# <a name="runspace03-c-code-sample"></a><span data-ttu-id="bcf6a-102">Runspace03-codevoorbeeld (C#)</span><span class="sxs-lookup"><span data-stu-id="bcf6a-102">RunSpace03 (C#) Code Sample</span></span>

<span data-ttu-id="bcf6a-103">Hier volgt de C# broncode voor de consoletoepassing die is beschreven in [het maken van een Console-toepassing die wordt uitgevoerd een Script opgegeven](http://msdn.microsoft.com/en-us/a93e6006-36db-4bcc-b9da-c5bebf4ffd68).</span><span class="sxs-lookup"><span data-stu-id="bcf6a-103">Here is the C# source code for the console application described in [Creating a Console Application That Runs a Specified Script](http://msdn.microsoft.com/en-us/a93e6006-36db-4bcc-b9da-c5bebf4ffd68).</span></span> <span data-ttu-id="bcf6a-104">In dit voorbeeld wordt de [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) klasse voor het uitvoeren van een script dat haalt informatie verwerken met behulp van de lijst met procesnamen die zijn doorgegeven aan het script.</span><span class="sxs-lookup"><span data-stu-id="bcf6a-104">This sample uses the [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) class to execute a script that retrieves process information by using the list of process names passed into the script.</span></span> <span data-ttu-id="bcf6a-105">Deze leest hoe gebruikersinvoer objecten doorgeven aan een script en foutobjecten, evenals de uitvoer-objecten ophalen.</span><span class="sxs-lookup"><span data-stu-id="bcf6a-105">It shows how to pass input objects to a script and how to retrieve error objects as well as the output objects.</span></span>

> [!NOTE]
> <span data-ttu-id="bcf6a-106">U kunt downloaden de C# bronbestand (runspace03.cs) voor dit voorbeeld met behulp van de Microsoft Windows Software Development Kit voor Windows Vista en Microsoft .NET Framework 3.0 Runtime-onderdelen.</span><span class="sxs-lookup"><span data-stu-id="bcf6a-106">You can download the C# source file (runspace03.cs) for this sample using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="bcf6a-107">Zie voor instructies voor het downloaden [hoe u Windows PowerShell installeren en Download de Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="bcf6a-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="bcf6a-108">De bronbestanden van de gedownloade zijn beschikbaar in de  **\<voorbeelden van PowerShell >** directory.</span><span class="sxs-lookup"><span data-stu-id="bcf6a-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="bcf6a-109">Voorbeeld van code</span><span class="sxs-lookup"><span data-stu-id="bcf6a-109">Code Sample</span></span>

[!code-csharp[Runspace03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace03/Runspace03.cs#L11-L88 "Runspace03.cs")]

## <a name="see-also"></a><span data-ttu-id="bcf6a-110">Zie ook</span><span class="sxs-lookup"><span data-stu-id="bcf6a-110">See Also</span></span>

[<span data-ttu-id="bcf6a-111">Windows PowerShell-programmeergids</span><span class="sxs-lookup"><span data-stu-id="bcf6a-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="bcf6a-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="bcf6a-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)