---
title: Codevoorbeeld RunSpace07 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ad306d9-45c2-4d55-8e64-fdcba43402c5
caps.latest.revision: 6
ms.openlocfilehash: 064e7d7ea2ee173bbcdd75a9f3a6c12582afe17b
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429632"
---
# <a name="runspace07-code-sample"></a><span data-ttu-id="48f79-102">Runspace07-codevoorbeeld</span><span class="sxs-lookup"><span data-stu-id="48f79-102">RunSpace07 Code Sample</span></span>

<span data-ttu-id="48f79-103">Hier volgt de broncode voor het voorbeeld Runspace07 die zijn beschreven [het maken van een toepassing die wordt toegevoegd consoleopdrachten voor een pijplijn](http://msdn.microsoft.com/en-us/01eb7808-e97b-4905-80be-9e2fa38c262e).</span><span class="sxs-lookup"><span data-stu-id="48f79-103">Here is the source code for the Runspace07 sample described in [Creating a Console Application That Adds Commands to a Pipeline](http://msdn.microsoft.com/en-us/01eb7808-e97b-4905-80be-9e2fa38c262e).</span></span> <span data-ttu-id="48f79-104">Deze voorbeeldtoepassing maakt een runspace, wordt een pijplijn gemaakt, worden twee opdrachten toegevoegd aan de pijplijn en voert de pijplijn.</span><span class="sxs-lookup"><span data-stu-id="48f79-104">This sample application creates a runspace, creates a pipeline, adds two commands to the pipeline, and then executes the pipeline.</span></span> <span data-ttu-id="48f79-105">De opdrachten toegevoegd aan de pijplijn zijn de `Get-Process` en `Measure-Object` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="48f79-105">The commands added to the pipeline are the `Get-Process` and `Measure-Object` cmdlets.</span></span>

> [!NOTE]
> <span data-ttu-id="48f79-106">U kunt downloaden de C# bronbestand (runspace07.cs) met behulp van de Microsoft Windows Software Development Kit voor Windows Vista en Microsoft .NET Framework 3.0 Runtime-onderdelen.</span><span class="sxs-lookup"><span data-stu-id="48f79-106">You can download the C# source file (runspace07.cs) using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="48f79-107">Zie voor instructies voor het downloaden [hoe u Windows PowerShell installeren en Download de Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="48f79-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="48f79-108">De bronbestanden van de gedownloade zijn beschikbaar in de  **\<voorbeelden van PowerShell >** directory.</span><span class="sxs-lookup"><span data-stu-id="48f79-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="48f79-109">Voorbeeld van code</span><span class="sxs-lookup"><span data-stu-id="48f79-109">Code Sample</span></span>

[!code-csharp[Runspace07.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace07/Runspace07.cs#L11-L108 "Runspace07.cs")]

## <a name="see-also"></a><span data-ttu-id="48f79-110">Zie ook</span><span class="sxs-lookup"><span data-stu-id="48f79-110">See Also</span></span>

[<span data-ttu-id="48f79-111">Windows PowerShell-programmeergids</span><span class="sxs-lookup"><span data-stu-id="48f79-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="48f79-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="48f79-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)