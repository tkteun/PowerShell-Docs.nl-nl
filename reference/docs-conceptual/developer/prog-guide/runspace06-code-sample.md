---
title: Voor beeld van RunSpace06-code | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: c8767ac8dc3a3d9253c2a53a4754d9bd54304abb
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784721"
---
# <a name="runspace06-code-sample"></a><span data-ttu-id="41706-102">Runspace06-codevoorbeeld</span><span class="sxs-lookup"><span data-stu-id="41706-102">RunSpace06 Code Sample</span></span>

<span data-ttu-id="41706-103">Dit is de bron code voor het Runspace06-voor beeld dat wordt beschreven in [een runs Pace configureren met een Windows Power shell-module](https://msdn.microsoft.com/a7289ee8-9732-49ee-91c7-d533e9538b83).</span><span class="sxs-lookup"><span data-stu-id="41706-103">Here is the source code for the Runspace06 sample described in [Configuring a Runspace Using a Windows PowerShell Snap-in](https://msdn.microsoft.com/a7289ee8-9732-49ee-91c7-d533e9538b83).</span></span>
<span data-ttu-id="41706-104">Deze voorbeeld toepassing maakt een runs Pace op basis van een Windows Power shell-module, die vervolgens wordt gebruikt om een pijp lijn uit te voeren met één opdracht.</span><span class="sxs-lookup"><span data-stu-id="41706-104">This sample application creates a runspace based on a Windows PowerShell snap-in, which is then used to run a pipeline with a single command.</span></span> <span data-ttu-id="41706-105">Om dit te doen, maakt de toepassing de runs Pace-configuratie-informatie, maakt u een runs Pace, maakt u een pijp lijn met één opdracht en voert u de pijp lijn uit.</span><span class="sxs-lookup"><span data-stu-id="41706-105">To do this, the application creates the runspace configuration information, creates a runspace, creates a pipeline with a single command, and then executes the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="41706-106">U kunt het C#-bron bestand (runspace06.cs) downloaden met behulp van de Windows-Software Development Kit voor Windows Vista en Microsoft .NET Framework 3,0 runtime-onderdelen.</span><span class="sxs-lookup"><span data-stu-id="41706-106">You can download the C# source file (runspace06.cs) by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="41706-107">Zie [Windows Power Shell installeren en de Windows Power shell-SDK downloaden](/powershell/scripting/developer/installing-the-windows-powershell-sdk)voor instructies voor het downloaden.</span><span class="sxs-lookup"><span data-stu-id="41706-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="41706-108">De gedownloade bron bestanden bevinden zich in de **\<PowerShell Samples>** map.</span><span class="sxs-lookup"><span data-stu-id="41706-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="41706-109">Code voorbeeld</span><span class="sxs-lookup"><span data-stu-id="41706-109">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace06/Runspace06.cs" range="11-85":::

## <a name="see-also"></a><span data-ttu-id="41706-110">Zie ook</span><span class="sxs-lookup"><span data-stu-id="41706-110">See Also</span></span>

[<span data-ttu-id="41706-111">Handleiding voor Windows PowerShell-programmeurs</span><span class="sxs-lookup"><span data-stu-id="41706-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="41706-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="41706-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
