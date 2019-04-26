---
title: Codevoorbeeld RunSpace05 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9688cd69-07ea-4ea0-8822-0a4850bcf86c
caps.latest.revision: 7
ms.openlocfilehash: b16ee45383059c52ce3433699c6b8d2120992431
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081339"
---
# <a name="runspace05-code-sample"></a><span data-ttu-id="8bccb-102">Runspace05-codevoorbeeld</span><span class="sxs-lookup"><span data-stu-id="8bccb-102">RunSpace05 Code Sample</span></span>

<span data-ttu-id="8bccb-103">Hier volgt de broncode voor het voorbeeld Runspace05 die wordt beschreven in [configureren van een Runspace met behulp van RunspaceConfiguration](http://msdn.microsoft.com/en-us/42681d19-2d05-4975-befd-afb1990e79b2).</span><span class="sxs-lookup"><span data-stu-id="8bccb-103">Here is the source code for the Runspace05 sample that is described in [Configuring a Runspace Using RunspaceConfiguration](http://msdn.microsoft.com/en-us/42681d19-2d05-4975-befd-afb1990e79b2).</span></span> <span data-ttu-id="8bccb-104">In dit voorbeeld laat zien hoe de configuratiegegevens runspace maken, een runspace maken, een pijplijn maken met één opdracht en uitvoeren van de pijplijn.</span><span class="sxs-lookup"><span data-stu-id="8bccb-104">This sample shows how to create the runspace configuration information, create a runspace, create a pipeline with a single command, and then execute the pipeline.</span></span> <span data-ttu-id="8bccb-105">De opdracht die wordt uitgevoerd, is de `Get-Process` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8bccb-105">The command that is executed is the `Get-Process` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="8bccb-106">U kunt downloaden de C# bronbestand (runspace05.cs) met behulp van de Microsoft Windows Software Development Kit voor Windows Vista en Microsoft .NET Framework 3.0 Runtime-onderdelen.</span><span class="sxs-lookup"><span data-stu-id="8bccb-106">You can download the C# source file (runspace05.cs) by using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="8bccb-107">Zie voor instructies voor het downloaden [hoe u Windows PowerShell installeren en Download de Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="8bccb-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="8bccb-108">De bronbestanden van de gedownloade zijn beschikbaar in de  **\<voorbeelden van PowerShell >** directory.</span><span class="sxs-lookup"><span data-stu-id="8bccb-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="8bccb-109">Voorbeeld van code</span><span class="sxs-lookup"><span data-stu-id="8bccb-109">Code Sample</span></span>

[!code-csharp[Runspace05.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace05/Runspace05.cs#L11-L86 "Runspace05.cs")]

## <a name="see-also"></a><span data-ttu-id="8bccb-110">Zie ook</span><span class="sxs-lookup"><span data-stu-id="8bccb-110">See Also</span></span>

[<span data-ttu-id="8bccb-111">Windows PowerShell-programmeergids</span><span class="sxs-lookup"><span data-stu-id="8bccb-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="8bccb-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="8bccb-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)