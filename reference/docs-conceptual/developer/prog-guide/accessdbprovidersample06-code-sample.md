---
title: Voor beeld van AccessDbProviderSample06-code | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: baab6a56-c199-48d7-a03e-a904b1bb1baa
caps.latest.revision: 7
ms.openlocfilehash: 90927917550ade695f32c6f763f8cc4a8b347275
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72357279"
---
# <a name="accessdbprovidersample06-code-sample"></a><span data-ttu-id="2ab1d-102">AccessDBProviderSample06-codevoorbeeld</span><span class="sxs-lookup"><span data-stu-id="2ab1d-102">AccessDbProviderSample06 Code Sample</span></span>

<span data-ttu-id="2ab1d-103">De volgende code toont de implementatie van de Windows Power shell-inhouds provider die wordt beschreven in [een Windows Power shell-inhouds provider maken](./creating-a-windows-powershell-content-provider.md).</span><span class="sxs-lookup"><span data-stu-id="2ab1d-103">The following code shows the implementation of the Windows PowerShell content provider described in [Creating a Windows PowerShell Content Provider](./creating-a-windows-powershell-content-provider.md).</span></span> <span data-ttu-id="2ab1d-104">Met deze provider kan de gebruiker de inhoud van de items in een gegevens archief bewerken.</span><span class="sxs-lookup"><span data-stu-id="2ab1d-104">This provider enables the user to manipulate the contents of the items in a data store.</span></span>

> [!NOTE]
> <span data-ttu-id="2ab1d-105">U kunt het C# bron bestand (AccessDBSampleProvider06.cs) voor deze provider downloaden met behulp van de micro soft Windows Software Development Kit voor Windows Vista en Microsoft .NET Framework 3,0 runtime-onderdelen.</span><span class="sxs-lookup"><span data-stu-id="2ab1d-105">You can download the C# source file (AccessDBSampleProvider06.cs) for this provider by using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="2ab1d-106">Zie [Windows Power Shell installeren en de Windows Power shell-SDK downloaden](/powershell/developer/installing-the-windows-powershell-sdk)voor instructies voor het downloaden.</span><span class="sxs-lookup"><span data-stu-id="2ab1d-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="2ab1d-107">De gedownloade bron bestanden zijn beschikbaar in de **\<PowerShell-voor beelden >** map.</span><span class="sxs-lookup"><span data-stu-id="2ab1d-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>
>
> <span data-ttu-id="2ab1d-108">Zie [uw Windows Power shell-provider ontwerpen](./designing-your-windows-powershell-provider.md)voor meer informatie over andere implementaties van Windows Power shell-providers.</span><span class="sxs-lookup"><span data-stu-id="2ab1d-108">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="2ab1d-109">Code voorbeeld</span><span class="sxs-lookup"><span data-stu-id="2ab1d-109">Code Sample</span></span>

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L2399 "AccessDBProviderSample06.cs")]

## <a name="see-also"></a><span data-ttu-id="2ab1d-110">Zie ook</span><span class="sxs-lookup"><span data-stu-id="2ab1d-110">See Also</span></span>

[<span data-ttu-id="2ab1d-111">Hand leiding voor Windows Power shell-programmeurs</span><span class="sxs-lookup"><span data-stu-id="2ab1d-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="2ab1d-112">Windows Power shell SDK</span><span class="sxs-lookup"><span data-stu-id="2ab1d-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
