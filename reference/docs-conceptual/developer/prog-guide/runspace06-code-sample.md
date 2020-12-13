---
ms.date: 09/13/2016
ms.topic: reference
title: Runspace06-codevoorbeeld
description: Runspace06-codevoorbeeld
ms.openlocfilehash: 627fa2be51721dd8bfdd63fabdd2e6f286d593be
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667471"
---
# <a name="runspace06-code-sample"></a><span data-ttu-id="53220-103">Runspace06-codevoorbeeld</span><span class="sxs-lookup"><span data-stu-id="53220-103">RunSpace06 Code Sample</span></span>

<span data-ttu-id="53220-104">Dit is de bron code voor het Runspace06-voor beeld dat wordt beschreven in [een runs Pace configureren met een Windows Power shell-module](https://msdn.microsoft.com/a7289ee8-9732-49ee-91c7-d533e9538b83).</span><span class="sxs-lookup"><span data-stu-id="53220-104">Here is the source code for the Runspace06 sample described in [Configuring a Runspace Using a Windows PowerShell Snap-in](https://msdn.microsoft.com/a7289ee8-9732-49ee-91c7-d533e9538b83).</span></span>
<span data-ttu-id="53220-105">Deze voorbeeld toepassing maakt een runs Pace op basis van een Windows Power shell-module, die vervolgens wordt gebruikt om een pijp lijn uit te voeren met één opdracht.</span><span class="sxs-lookup"><span data-stu-id="53220-105">This sample application creates a runspace based on a Windows PowerShell snap-in, which is then used to run a pipeline with a single command.</span></span> <span data-ttu-id="53220-106">Om dit te doen, maakt de toepassing de runs Pace-configuratie-informatie, maakt u een runs Pace, maakt u een pijp lijn met één opdracht en voert u de pijp lijn uit.</span><span class="sxs-lookup"><span data-stu-id="53220-106">To do this, the application creates the runspace configuration information, creates a runspace, creates a pipeline with a single command, and then executes the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="53220-107">U kunt het C#-bron bestand (runspace06.cs) downloaden met behulp van de Windows-Software Development Kit voor Windows Vista en Microsoft .NET Framework 3,0 runtime-onderdelen.</span><span class="sxs-lookup"><span data-stu-id="53220-107">You can download the C# source file (runspace06.cs) by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="53220-108">Zie [Windows Power Shell installeren en de Windows Power shell-SDK downloaden](/powershell/scripting/developer/installing-the-windows-powershell-sdk)voor instructies voor het downloaden.</span><span class="sxs-lookup"><span data-stu-id="53220-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="53220-109">De gedownloade bron bestanden bevinden zich in de **\<PowerShell Samples>** map.</span><span class="sxs-lookup"><span data-stu-id="53220-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="53220-110">Code voorbeeld</span><span class="sxs-lookup"><span data-stu-id="53220-110">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace06/Runspace06.cs" range="11-85":::

## <a name="see-also"></a><span data-ttu-id="53220-111">Zie ook</span><span class="sxs-lookup"><span data-stu-id="53220-111">See Also</span></span>

[<span data-ttu-id="53220-112">Handleiding voor Windows PowerShell-programmeurs</span><span class="sxs-lookup"><span data-stu-id="53220-112">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="53220-113">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="53220-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
