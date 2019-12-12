---
title: Voor beeld van RunSpace06-code | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d71f86d5-eb62-4b16-aa95-5fd3f314ffd3
caps.latest.revision: 6
ms.openlocfilehash: c3ae45ae9587bd130bbe9bb65ef47dc246f6e465
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74417916"
---
# <a name="runspace06-code-sample"></a><span data-ttu-id="4f0ee-102">Runspace06-codevoorbeeld</span><span class="sxs-lookup"><span data-stu-id="4f0ee-102">RunSpace06 Code Sample</span></span>

<span data-ttu-id="4f0ee-103">Dit is de bron code voor het Runspace06-voor beeld dat wordt beschreven in [een runs Pace configureren met een Windows Power shell-module](https://msdn.microsoft.com/en-us/a7289ee8-9732-49ee-91c7-d533e9538b83).</span><span class="sxs-lookup"><span data-stu-id="4f0ee-103">Here is the source code for the Runspace06 sample described in [Configuring a Runspace Using a Windows PowerShell Snap-in](https://msdn.microsoft.com/en-us/a7289ee8-9732-49ee-91c7-d533e9538b83).</span></span> <span data-ttu-id="4f0ee-104">Deze voorbeeld toepassing maakt een runs Pace op basis van een Windows Power shell-module, die vervolgens wordt gebruikt om een pijp lijn uit te voeren met één opdracht.</span><span class="sxs-lookup"><span data-stu-id="4f0ee-104">This sample application creates a runspace based on a Windows PowerShell snap-in, which is then used to run a pipeline with a single command.</span></span> <span data-ttu-id="4f0ee-105">Om dit te doen, maakt de toepassing de runs Pace-configuratie-informatie, maakt u een runs Pace, maakt u een pijp lijn met één opdracht en voert u de pijp lijn uit.</span><span class="sxs-lookup"><span data-stu-id="4f0ee-105">To do this, the application creates the runspace configuration information, creates a runspace, creates a pipeline with a single command, and then executes the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="4f0ee-106">U kunt het C# bron bestand (runspace06.cs) downloaden met behulp van de Windows-Software Development Kit voor Windows Vista en Microsoft .NET Framework 3,0 runtime-onderdelen.</span><span class="sxs-lookup"><span data-stu-id="4f0ee-106">You can download the C# source file (runspace06.cs) by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="4f0ee-107">Zie [Windows Power Shell installeren en de Windows Power shell-SDK downloaden](/powershell/scripting/developer/installing-the-windows-powershell-sdk)voor instructies voor het downloaden.</span><span class="sxs-lookup"><span data-stu-id="4f0ee-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="4f0ee-108">De gedownloade bron bestanden zijn beschikbaar in de **\<Power shell-voor beelden >** map.</span><span class="sxs-lookup"><span data-stu-id="4f0ee-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="4f0ee-109">Code voorbeeld</span><span class="sxs-lookup"><span data-stu-id="4f0ee-109">Code Sample</span></span>

[!code-csharp[Runspace06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace06/Runspace06.cs#L11-L85 "Runspace06.cs")]

## <a name="see-also"></a><span data-ttu-id="4f0ee-110">Zie ook</span><span class="sxs-lookup"><span data-stu-id="4f0ee-110">See Also</span></span>

[<span data-ttu-id="4f0ee-111">Hand leiding voor Windows Power shell-programmeurs</span><span class="sxs-lookup"><span data-stu-id="4f0ee-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="4f0ee-112">Windows Power shell SDK</span><span class="sxs-lookup"><span data-stu-id="4f0ee-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
