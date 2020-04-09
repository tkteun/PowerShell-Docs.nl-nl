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
ms.openlocfilehash: d1d5e7f4096288ed09dada8eb8a61773921dc1ce
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/08/2020
ms.locfileid: "80978224"
---
# <a name="runspace06-code-sample"></a><span data-ttu-id="db6c0-102">Runspace06-codevoorbeeld</span><span class="sxs-lookup"><span data-stu-id="db6c0-102">RunSpace06 Code Sample</span></span>

<span data-ttu-id="db6c0-103">Dit is de bron code voor het Runspace06-voor beeld dat wordt beschreven in [een runs Pace configureren met een Windows Power shell-module](https://msdn.microsoft.com/a7289ee8-9732-49ee-91c7-d533e9538b83).</span><span class="sxs-lookup"><span data-stu-id="db6c0-103">Here is the source code for the Runspace06 sample described in [Configuring a Runspace Using a Windows PowerShell Snap-in](https://msdn.microsoft.com/a7289ee8-9732-49ee-91c7-d533e9538b83).</span></span>
<span data-ttu-id="db6c0-104">Deze voorbeeld toepassing maakt een runs Pace op basis van een Windows Power shell-module, die vervolgens wordt gebruikt om een pijp lijn uit te voeren met één opdracht.</span><span class="sxs-lookup"><span data-stu-id="db6c0-104">This sample application creates a runspace based on a Windows PowerShell snap-in, which is then used to run a pipeline with a single command.</span></span> <span data-ttu-id="db6c0-105">Om dit te doen, maakt de toepassing de runs Pace-configuratie-informatie, maakt u een runs Pace, maakt u een pijp lijn met één opdracht en voert u de pijp lijn uit.</span><span class="sxs-lookup"><span data-stu-id="db6c0-105">To do this, the application creates the runspace configuration information, creates a runspace, creates a pipeline with a single command, and then executes the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="db6c0-106">U kunt het C# bron bestand (runspace06.cs) downloaden met behulp van de Windows-Software Development Kit voor Windows Vista en Microsoft .NET Framework 3,0 runtime-onderdelen.</span><span class="sxs-lookup"><span data-stu-id="db6c0-106">You can download the C# source file (runspace06.cs) by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="db6c0-107">Zie [Windows Power Shell installeren en de Windows Power shell-SDK downloaden](/powershell/scripting/developer/installing-the-windows-powershell-sdk)voor instructies voor het downloaden.</span><span class="sxs-lookup"><span data-stu-id="db6c0-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="db6c0-108">De gedownloade bron bestanden zijn beschikbaar in de **\<Power shell-voor beelden >** map.</span><span class="sxs-lookup"><span data-stu-id="db6c0-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="db6c0-109">Code voorbeeld</span><span class="sxs-lookup"><span data-stu-id="db6c0-109">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace06/Runspace06.cs" range="11-85":::

## <a name="see-also"></a><span data-ttu-id="db6c0-110">Zie ook</span><span class="sxs-lookup"><span data-stu-id="db6c0-110">See Also</span></span>

[<span data-ttu-id="db6c0-111">Hand leiding voor Windows Power shell-programmeurs</span><span class="sxs-lookup"><span data-stu-id="db6c0-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="db6c0-112">Windows Power shell SDK</span><span class="sxs-lookup"><span data-stu-id="db6c0-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
