---
ms.date: 09/13/2016
ms.topic: reference
title: Runspace01-codevoorbeeld (C#)
description: Runspace01-codevoorbeeld (C#)
ms.openlocfilehash: e6121c144e1a4c1a1d9460d01119f44ee5835821
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92657157"
---
# <a name="runspace01-c-code-sample"></a><span data-ttu-id="46a52-103">Runspace01-codevoorbeeld (C#)</span><span class="sxs-lookup"><span data-stu-id="46a52-103">Runspace01 (C#) Code Sample</span></span>

<span data-ttu-id="46a52-104">Hier volgen de code voorbeelden voor de runs Pace die wordt beschreven in [een console toepassing maken die een opgegeven opdracht uitvoert](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program).</span><span class="sxs-lookup"><span data-stu-id="46a52-104">Here are the code samples for the runspace described in [Creating a Console Application That Runs a Specified Command](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program).</span></span>
<span data-ttu-id="46a52-105">Hiervoor roept de toepassing een runs Pace aan en roept hij een opdracht aan.</span><span class="sxs-lookup"><span data-stu-id="46a52-105">To do this, the application invokes a runspace, and then invokes a command.</span></span> <span data-ttu-id="46a52-106">(Houd er rekening mee dat met deze toepassing geen runs Pace-configuratie gegevens worden opgegeven, noch expliciet een pijp lijn wordt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="46a52-106">(Note that this application does not specify runspace configuration information, nor does it explicitly create a pipeline).</span></span> <span data-ttu-id="46a52-107">De opdracht die wordt aangeroepen, is de `Get-Process` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="46a52-107">The command that is invoked is the `Get-Process` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="46a52-108">U kunt het C#-bron bestand (runspace01.cs) voor deze runs Pace downloaden met behulp van de micro soft Windows Software Development Kit voor Windows Vista en Microsoft .NET Framework 3,0 runtime-onderdelen.</span><span class="sxs-lookup"><span data-stu-id="46a52-108">You can download the C# source file (runspace01.cs) for this runspace using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span>
> <span data-ttu-id="46a52-109">Zie [Windows Power Shell installeren en de Windows Power shell-SDK downloaden](/powershell/scripting/developer/installing-the-windows-powershell-sdk)voor instructies voor het downloaden.</span><span class="sxs-lookup"><span data-stu-id="46a52-109">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="46a52-110">De gedownloade bron bestanden bevinden zich in de **\<PowerShell Samples>** map.</span><span class="sxs-lookup"><span data-stu-id="46a52-110">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="46a52-111">Code voorbeeld</span><span class="sxs-lookup"><span data-stu-id="46a52-111">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace01/Runspace01.cs" range="11-62":::

## <a name="see-also"></a><span data-ttu-id="46a52-112">Zie ook</span><span class="sxs-lookup"><span data-stu-id="46a52-112">See Also</span></span>

[<span data-ttu-id="46a52-113">Handleiding voor Windows PowerShell-programmeurs</span><span class="sxs-lookup"><span data-stu-id="46a52-113">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="46a52-114">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="46a52-114">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
