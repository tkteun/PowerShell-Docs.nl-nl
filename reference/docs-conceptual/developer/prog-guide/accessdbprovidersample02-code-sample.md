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
ms.openlocfilehash: 122fc8ec4fc4388cca01f1a7e5014fa875506bb7
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72352785"
---
# <a name="accessdbprovidersample02-code-sample"></a><span data-ttu-id="5dbde-102">AccessDBProviderSample02-codevoorbeeld</span><span class="sxs-lookup"><span data-stu-id="5dbde-102">AccessDbProviderSample02 Code Sample</span></span>

<span data-ttu-id="5dbde-103">De volgende code toont de implementatie van de Windows Power shell-provider die wordt beschreven in [een Windows Power shell-schijf provider maken](./creating-a-windows-powershell-drive-provider.md).</span><span class="sxs-lookup"><span data-stu-id="5dbde-103">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Windows PowerShell Drive Provider](./creating-a-windows-powershell-drive-provider.md).</span></span> <span data-ttu-id="5dbde-104">Deze implementatie maakt een pad, maakt verbinding met een Access-Data Base en verwijdert vervolgens het station.</span><span class="sxs-lookup"><span data-stu-id="5dbde-104">This implementation creates a path, makes a connection to an Access database, and then removes the drive.</span></span>

> [!NOTE]
> <span data-ttu-id="5dbde-105">U kunt het C# bron bestand (AccessDBSampleProvider02.cs) voor deze provider downloaden met behulp van de micro soft Windows Software Development Kit voor Windows Vista en Microsoft .NET Framework 3,0 runtime-onderdelen.</span><span class="sxs-lookup"><span data-stu-id="5dbde-105">You can download the C# source file (AccessDBSampleProvider02.cs) for this provider using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="5dbde-106">Zie [Windows Power Shell installeren en de Windows Power shell-SDK downloaden](/powershell/developer/installing-the-windows-powershell-sdk)voor instructies voor het downloaden.</span><span class="sxs-lookup"><span data-stu-id="5dbde-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="5dbde-107">De gedownloade bron bestanden zijn beschikbaar in de **\<PowerShell-voor beelden >** map.</span><span class="sxs-lookup"><span data-stu-id="5dbde-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>
>
> <span data-ttu-id="5dbde-108">Zie [uw Windows Power shell-provider ontwerpen](./designing-your-windows-powershell-provider.md)voor meer informatie over andere implementaties van Windows Power shell-providers.</span><span class="sxs-lookup"><span data-stu-id="5dbde-108">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="5dbde-109">Code voorbeeld</span><span class="sxs-lookup"><span data-stu-id="5dbde-109">Code Sample</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L11-L154 "AccessDBProviderSample02.cs")]


## <a name="see-also"></a><span data-ttu-id="5dbde-110">Zie ook</span><span class="sxs-lookup"><span data-stu-id="5dbde-110">See Also</span></span>

[<span data-ttu-id="5dbde-111">Hand leiding voor Windows Power shell-programmeurs</span><span class="sxs-lookup"><span data-stu-id="5dbde-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="5dbde-112">Windows Power shell SDK</span><span class="sxs-lookup"><span data-stu-id="5dbde-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
