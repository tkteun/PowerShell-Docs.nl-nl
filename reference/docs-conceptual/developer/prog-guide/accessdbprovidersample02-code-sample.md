---
ms.date: 09/13/2016
ms.topic: reference
title: AccessDBProviderSample02-codevoorbeeld
description: AccessDBProviderSample02-codevoorbeeld
ms.openlocfilehash: f467ee59b36027e80852ae1f7b2f1af5c9aa8569
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92659396"
---
# <a name="accessdbprovidersample02-code-sample"></a><span data-ttu-id="8a4cf-103">AccessDBProviderSample02-codevoorbeeld</span><span class="sxs-lookup"><span data-stu-id="8a4cf-103">AccessDbProviderSample02 Code Sample</span></span>

<span data-ttu-id="8a4cf-104">De volgende code toont de implementatie van de Windows Power shell-provider die wordt beschreven in [een Windows Power shell-schijf provider maken](./creating-a-windows-powershell-drive-provider.md).</span><span class="sxs-lookup"><span data-stu-id="8a4cf-104">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Windows PowerShell Drive Provider](./creating-a-windows-powershell-drive-provider.md).</span></span>
<span data-ttu-id="8a4cf-105">Deze implementatie maakt een pad, maakt verbinding met een Access-Data Base en verwijdert vervolgens het station.</span><span class="sxs-lookup"><span data-stu-id="8a4cf-105">This implementation creates a path, makes a connection to an Access database, and then removes the drive.</span></span>

> [!NOTE]
> <span data-ttu-id="8a4cf-106">U kunt het C#-bron bestand (AccessDBSampleProvider02.cs) voor deze provider downloaden met behulp van de micro soft Windows Software Development Kit voor Windows Vista en Microsoft .NET Framework 3,0 runtime-onderdelen.</span><span class="sxs-lookup"><span data-stu-id="8a4cf-106">You can download the C# source file (AccessDBSampleProvider02.cs) for this provider using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="8a4cf-107">Zie [Windows Power Shell installeren en de Windows Power shell-SDK downloaden](/powershell/scripting/developer/installing-the-windows-powershell-sdk)voor instructies voor het downloaden.</span><span class="sxs-lookup"><span data-stu-id="8a4cf-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="8a4cf-108">De gedownloade bron bestanden bevinden zich in de **\<PowerShell Samples>** map.</span><span class="sxs-lookup"><span data-stu-id="8a4cf-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span> <span data-ttu-id="8a4cf-109">Zie [uw Windows Power shell-provider ontwerpen](./designing-your-windows-powershell-provider.md)voor meer informatie over andere implementaties van Windows Power shell-providers.</span><span class="sxs-lookup"><span data-stu-id="8a4cf-109">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="8a4cf-110">Code voorbeeld</span><span class="sxs-lookup"><span data-stu-id="8a4cf-110">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs" range="11-154":::

## <a name="see-also"></a><span data-ttu-id="8a4cf-111">Zie ook</span><span class="sxs-lookup"><span data-stu-id="8a4cf-111">See Also</span></span>

[<span data-ttu-id="8a4cf-112">Handleiding voor Windows PowerShell-programmeurs</span><span class="sxs-lookup"><span data-stu-id="8a4cf-112">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="8a4cf-113">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="8a4cf-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
