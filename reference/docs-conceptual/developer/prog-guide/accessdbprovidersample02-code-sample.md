---
title: Voor beeld van AccessDbProviderSample02-code | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b89a4903-3efc-4b08-9b20-2baadf1d1b66
caps.latest.revision: 6
ms.openlocfilehash: 32abcfafb207ada23667cc6f0f03d382c6868ccb
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/08/2020
ms.locfileid: "80978604"
---
# <a name="accessdbprovidersample02-code-sample"></a><span data-ttu-id="e85fa-102">AccessDBProviderSample02-codevoorbeeld</span><span class="sxs-lookup"><span data-stu-id="e85fa-102">AccessDbProviderSample02 Code Sample</span></span>

<span data-ttu-id="e85fa-103">De volgende code toont de implementatie van de Windows Power shell-provider die wordt beschreven in [een Windows Power shell-schijf provider maken](./creating-a-windows-powershell-drive-provider.md).</span><span class="sxs-lookup"><span data-stu-id="e85fa-103">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Windows PowerShell Drive Provider](./creating-a-windows-powershell-drive-provider.md).</span></span>
<span data-ttu-id="e85fa-104">Deze implementatie maakt een pad, maakt verbinding met een Access-Data Base en verwijdert vervolgens het station.</span><span class="sxs-lookup"><span data-stu-id="e85fa-104">This implementation creates a path, makes a connection to an Access database, and then removes the drive.</span></span>

> [!NOTE]
> <span data-ttu-id="e85fa-105">U kunt het C# bron bestand (AccessDBSampleProvider02.cs) voor deze provider downloaden met behulp van de micro soft Windows Software Development Kit voor Windows Vista en Microsoft .NET Framework 3,0 runtime-onderdelen.</span><span class="sxs-lookup"><span data-stu-id="e85fa-105">You can download the C# source file (AccessDBSampleProvider02.cs) for this provider using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="e85fa-106">Zie [Windows Power Shell installeren en de Windows Power shell-SDK downloaden](/powershell/scripting/developer/installing-the-windows-powershell-sdk)voor instructies voor het downloaden.</span><span class="sxs-lookup"><span data-stu-id="e85fa-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="e85fa-107">De gedownloade bron bestanden zijn beschikbaar in de **\<Power shell-voor beelden >** map.</span><span class="sxs-lookup"><span data-stu-id="e85fa-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span> <span data-ttu-id="e85fa-108">Zie [uw Windows Power shell-provider ontwerpen](./designing-your-windows-powershell-provider.md)voor meer informatie over andere implementaties van Windows Power shell-providers.</span><span class="sxs-lookup"><span data-stu-id="e85fa-108">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="e85fa-109">Code voorbeeld</span><span class="sxs-lookup"><span data-stu-id="e85fa-109">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs" range="11-154":::

## <a name="see-also"></a><span data-ttu-id="e85fa-110">Zie ook</span><span class="sxs-lookup"><span data-stu-id="e85fa-110">See Also</span></span>

[<span data-ttu-id="e85fa-111">Hand leiding voor Windows Power shell-programmeurs</span><span class="sxs-lookup"><span data-stu-id="e85fa-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="e85fa-112">Windows Power shell SDK</span><span class="sxs-lookup"><span data-stu-id="e85fa-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
