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
ms.openlocfilehash: 0978880a4294edb96fc6edb00f420cd0a9ad197b
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/08/2020
ms.locfileid: "80977978"
---
# <a name="runspace01-c-code-sample"></a><span data-ttu-id="0bc5f-102">Runspace01-codevoorbeeld (C#)</span><span class="sxs-lookup"><span data-stu-id="0bc5f-102">Runspace01 (C#) Code Sample</span></span>

<span data-ttu-id="0bc5f-103">Hier volgen de code voorbeelden voor de runs Pace die wordt beschreven in [een console toepassing maken die een opgegeven opdracht uitvoert](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program).</span><span class="sxs-lookup"><span data-stu-id="0bc5f-103">Here are the code samples for the runspace described in [Creating a Console Application That Runs a Specified Command](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program).</span></span>
<span data-ttu-id="0bc5f-104">Hiervoor roept de toepassing een runs Pace aan en roept hij een opdracht aan.</span><span class="sxs-lookup"><span data-stu-id="0bc5f-104">To do this, the application invokes a runspace, and then invokes a command.</span></span> <span data-ttu-id="0bc5f-105">(Houd er rekening mee dat met deze toepassing geen runs Pace-configuratie gegevens worden opgegeven, noch expliciet een pijp lijn wordt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="0bc5f-105">(Note that this application does not specify runspace configuration information, nor does it explicitly create a pipeline).</span></span> <span data-ttu-id="0bc5f-106">De opdracht die wordt aangeroepen, is de `Get-Process`-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0bc5f-106">The command that is invoked is the `Get-Process` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="0bc5f-107">U kunt het C# bron bestand (runspace01.cs) voor deze runs Pace downloaden met behulp van de micro soft Windows Software Development Kit voor Windows Vista en Microsoft .NET Framework 3,0 runtime-onderdelen.</span><span class="sxs-lookup"><span data-stu-id="0bc5f-107">You can download the C# source file (runspace01.cs) for this runspace using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span>
> <span data-ttu-id="0bc5f-108">Zie [Windows Power Shell installeren en de Windows Power shell-SDK downloaden](/powershell/scripting/developer/installing-the-windows-powershell-sdk)voor instructies voor het downloaden.</span><span class="sxs-lookup"><span data-stu-id="0bc5f-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="0bc5f-109">De gedownloade bron bestanden zijn beschikbaar in de **\<Power shell-voor beelden >** map.</span><span class="sxs-lookup"><span data-stu-id="0bc5f-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="0bc5f-110">Code voorbeeld</span><span class="sxs-lookup"><span data-stu-id="0bc5f-110">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace01/Runspace01.cs" range="11-62":::

## <a name="see-also"></a><span data-ttu-id="0bc5f-111">Zie ook</span><span class="sxs-lookup"><span data-stu-id="0bc5f-111">See Also</span></span>

[<span data-ttu-id="0bc5f-112">Hand leiding voor Windows Power shell-programmeurs</span><span class="sxs-lookup"><span data-stu-id="0bc5f-112">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="0bc5f-113">Windows Power shell SDK</span><span class="sxs-lookup"><span data-stu-id="0bc5f-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
