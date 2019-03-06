---
title: Runspace01 (C#) codevoorbeeld | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d59f8b7c-e800-4633-aa5b-74d4c57e2706
caps.latest.revision: 6
ms.openlocfilehash: 59320365c4a35c3d71af10273eb21b1ce01e5c0c
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429700"
---
# <a name="runspace01-c-code-sample"></a><span data-ttu-id="f9fec-102">Runspace01-codevoorbeeld (C#)</span><span class="sxs-lookup"><span data-stu-id="f9fec-102">Runspace01 (C#) Code Sample</span></span>

<span data-ttu-id="f9fec-103">Hier volgen de codevoorbeelden voor de runspace die zijn beschreven [het maken van een Console-toepassing die wordt uitgevoerd een opgegeven opdracht](http://msdn.microsoft.com/en-us/793a6570-a072-4799-840b-172f28ce620e).</span><span class="sxs-lookup"><span data-stu-id="f9fec-103">Here are the code samples for the runspace described in [Creating a Console Application That Runs a Specified Command](http://msdn.microsoft.com/en-us/793a6570-a072-4799-840b-172f28ce620e).</span></span> <span data-ttu-id="f9fec-104">U doet dit door de toepassing een runspace aanroept en roept vervolgens een opdracht.</span><span class="sxs-lookup"><span data-stu-id="f9fec-104">To do this, the application invokes a runspace, and then invokes a command.</span></span> <span data-ttu-id="f9fec-105">(Houd er rekening mee dat deze toepassing geen informatie over de configuratie van de runspace geeft, noch worden deze expliciet een pijplijn maken).</span><span class="sxs-lookup"><span data-stu-id="f9fec-105">(Note that this application does not specify runspace configuration information, nor does it explicitly create a pipeline).</span></span> <span data-ttu-id="f9fec-106">De opdracht die wordt opgeroepen, is de `Get-Process` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f9fec-106">The command that is invoked is the `Get-Process` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="f9fec-107">U kunt downloaden de C# bronbestand (runspace01.cs) voor deze runspace met de Microsoft Windows Software Development Kit voor Windows Vista en Microsoft .NET Framework 3.0 Runtime-onderdelen.</span><span class="sxs-lookup"><span data-stu-id="f9fec-107">You can download the C# source file (runspace01.cs) for this runspace using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="f9fec-108">Zie voor instructies voor het downloaden [hoe u Windows PowerShell installeren en Download de Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="f9fec-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="f9fec-109">De bronbestanden van de gedownloade zijn beschikbaar in de  **\<voorbeelden van PowerShell >** directory.</span><span class="sxs-lookup"><span data-stu-id="f9fec-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="f9fec-110">Voorbeeld van code</span><span class="sxs-lookup"><span data-stu-id="f9fec-110">Code Sample</span></span>

[!code-csharp[Runspace01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace01/Runspace01.cs#L11-L62 "Runspace01.cs")]

## <a name="see-also"></a><span data-ttu-id="f9fec-111">Zie ook</span><span class="sxs-lookup"><span data-stu-id="f9fec-111">See Also</span></span>

[<span data-ttu-id="f9fec-112">Windows PowerShell-programmeergids</span><span class="sxs-lookup"><span data-stu-id="f9fec-112">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="f9fec-113">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="f9fec-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)