---
title: Codevoorbeeld AccessDbProviderSample02 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b89a4903-3efc-4b08-9b20-2baadf1d1b66
caps.latest.revision: 6
ms.openlocfilehash: 67a169bfac0b0fc90e6ccd276d3d3592d1b70bb0
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082022"
---
# <a name="accessdbprovidersample02-code-sample"></a><span data-ttu-id="4431f-102">AccessDBProviderSample02-codevoorbeeld</span><span class="sxs-lookup"><span data-stu-id="4431f-102">AccessDbProviderSample02 Code Sample</span></span>

<span data-ttu-id="4431f-103">De volgende code toont de uitvoering van de Windows PowerShell-provider wordt beschreven in [het maken van een Windows PowerShell station Provider](./creating-a-windows-powershell-drive-provider.md).</span><span class="sxs-lookup"><span data-stu-id="4431f-103">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Windows PowerShell Drive Provider](./creating-a-windows-powershell-drive-provider.md).</span></span> <span data-ttu-id="4431f-104">Deze implementatie maakt een pad, maakt een verbinding met een Access-database en vervolgens verwijdert u het station.</span><span class="sxs-lookup"><span data-stu-id="4431f-104">This implementation creates a path, makes a connection to an Access database, and then removes the drive.</span></span>

> [!NOTE]
> <span data-ttu-id="4431f-105">U kunt downloaden de C# bronbestand (AccessDBSampleProvider02.cs) voor deze provider met behulp van de Microsoft Windows Software Development Kit voor Windows Vista en Microsoft .NET Framework 3.0 Runtime-onderdelen.</span><span class="sxs-lookup"><span data-stu-id="4431f-105">You can download the C# source file (AccessDBSampleProvider02.cs) for this provider using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="4431f-106">Zie voor instructies voor het downloaden [hoe u Windows PowerShell installeren en Download de Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="4431f-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="4431f-107">De bronbestanden van de gedownloade zijn beschikbaar in de  **\<voorbeelden van PowerShell >** directory.</span><span class="sxs-lookup"><span data-stu-id="4431f-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>
>
> <span data-ttu-id="4431f-108">Zie voor meer informatie over andere Windows PowerShell-provider-implementaties, [het ontwerpen van uw Windows PowerShell-Provider](./designing-your-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="4431f-108">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="4431f-109">Voorbeeld van code</span><span class="sxs-lookup"><span data-stu-id="4431f-109">Code Sample</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L11-L154 "AccessDBProviderSample02.cs")]


## <a name="see-also"></a><span data-ttu-id="4431f-110">Zie ook</span><span class="sxs-lookup"><span data-stu-id="4431f-110">See Also</span></span>

[<span data-ttu-id="4431f-111">Windows PowerShell-programmeergids</span><span class="sxs-lookup"><span data-stu-id="4431f-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="4431f-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="4431f-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)