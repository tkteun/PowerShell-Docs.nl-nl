---
title: Runspace01 (C#)-code voorbeeld | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d59f8b7c-e800-4633-aa5b-74d4c57e2706
caps.latest.revision: 6
ms.openlocfilehash: 607113ed566fc1e08e5b1d7092c83da2a22366ca
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74418016"
---
# <a name="runspace01-c-code-sample"></a><span data-ttu-id="f1987-102">Runspace01-codevoorbeeld (C#)</span><span class="sxs-lookup"><span data-stu-id="f1987-102">Runspace01 (C#) Code Sample</span></span>

<span data-ttu-id="f1987-103">Hier volgen de code voorbeelden voor de runs Pace die wordt beschreven in [een console toepassing maken die een opgegeven opdracht uitvoert](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program).</span><span class="sxs-lookup"><span data-stu-id="f1987-103">Here are the code samples for the runspace described in [Creating a Console Application That Runs a Specified Command](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program).</span></span> <span data-ttu-id="f1987-104">Hiervoor roept de toepassing een runs Pace aan en roept hij een opdracht aan.</span><span class="sxs-lookup"><span data-stu-id="f1987-104">To do this, the application invokes a runspace, and then invokes a command.</span></span> <span data-ttu-id="f1987-105">(Houd er rekening mee dat met deze toepassing geen runs Pace-configuratie gegevens worden opgegeven, noch expliciet een pijp lijn wordt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="f1987-105">(Note that this application does not specify runspace configuration information, nor does it explicitly create a pipeline).</span></span> <span data-ttu-id="f1987-106">De opdracht die wordt aangeroepen, is de `Get-Process`-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f1987-106">The command that is invoked is the `Get-Process` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="f1987-107">U kunt het C# bron bestand (runspace01.cs) voor deze runs Pace downloaden met behulp van de micro soft Windows Software Development Kit voor Windows Vista en Microsoft .NET Framework 3,0 runtime-onderdelen.</span><span class="sxs-lookup"><span data-stu-id="f1987-107">You can download the C# source file (runspace01.cs) for this runspace using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="f1987-108">Zie [Windows Power Shell installeren en de Windows Power shell-SDK downloaden](/powershell/scripting/developer/installing-the-windows-powershell-sdk)voor instructies voor het downloaden.</span><span class="sxs-lookup"><span data-stu-id="f1987-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="f1987-109">De gedownloade bron bestanden zijn beschikbaar in de **\<Power shell-voor beelden >** map.</span><span class="sxs-lookup"><span data-stu-id="f1987-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="f1987-110">Code voorbeeld</span><span class="sxs-lookup"><span data-stu-id="f1987-110">Code Sample</span></span>

[!code-csharp[Runspace01.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace01/Runspace01.cs#L11-L62 "Runspace01.cs")]

## <a name="see-also"></a><span data-ttu-id="f1987-111">Zie ook</span><span class="sxs-lookup"><span data-stu-id="f1987-111">See Also</span></span>

[<span data-ttu-id="f1987-112">Hand leiding voor Windows Power shell-programmeurs</span><span class="sxs-lookup"><span data-stu-id="f1987-112">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="f1987-113">Windows Power shell SDK</span><span class="sxs-lookup"><span data-stu-id="f1987-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
