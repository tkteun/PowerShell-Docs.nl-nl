---
title: Voor beeld van AccessDbProviderSample02-code | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: ca7674ba5cff601394af4df20f0dda8794c14d22
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784806"
---
# <a name="accessdbprovidersample02-code-sample"></a><span data-ttu-id="e68f9-102">AccessDBProviderSample02-codevoorbeeld</span><span class="sxs-lookup"><span data-stu-id="e68f9-102">AccessDbProviderSample02 Code Sample</span></span>

<span data-ttu-id="e68f9-103">De volgende code toont de implementatie van de Windows Power shell-provider die wordt beschreven in [een Windows Power shell-schijf provider maken](./creating-a-windows-powershell-drive-provider.md).</span><span class="sxs-lookup"><span data-stu-id="e68f9-103">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Windows PowerShell Drive Provider](./creating-a-windows-powershell-drive-provider.md).</span></span>
<span data-ttu-id="e68f9-104">Deze implementatie maakt een pad, maakt verbinding met een Access-Data Base en verwijdert vervolgens het station.</span><span class="sxs-lookup"><span data-stu-id="e68f9-104">This implementation creates a path, makes a connection to an Access database, and then removes the drive.</span></span>

> [!NOTE]
> <span data-ttu-id="e68f9-105">U kunt het C#-bron bestand (AccessDBSampleProvider02.cs) voor deze provider downloaden met behulp van de micro soft Windows Software Development Kit voor Windows Vista en Microsoft .NET Framework 3,0 runtime-onderdelen.</span><span class="sxs-lookup"><span data-stu-id="e68f9-105">You can download the C# source file (AccessDBSampleProvider02.cs) for this provider using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="e68f9-106">Zie [Windows Power Shell installeren en de Windows Power shell-SDK downloaden](/powershell/scripting/developer/installing-the-windows-powershell-sdk)voor instructies voor het downloaden.</span><span class="sxs-lookup"><span data-stu-id="e68f9-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="e68f9-107">De gedownloade bron bestanden bevinden zich in de **\<PowerShell Samples>** map.</span><span class="sxs-lookup"><span data-stu-id="e68f9-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span> <span data-ttu-id="e68f9-108">Zie [uw Windows Power shell-provider ontwerpen](./designing-your-windows-powershell-provider.md)voor meer informatie over andere implementaties van Windows Power shell-providers.</span><span class="sxs-lookup"><span data-stu-id="e68f9-108">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="e68f9-109">Code voorbeeld</span><span class="sxs-lookup"><span data-stu-id="e68f9-109">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs" range="11-154":::

## <a name="see-also"></a><span data-ttu-id="e68f9-110">Zie ook</span><span class="sxs-lookup"><span data-stu-id="e68f9-110">See Also</span></span>

[<span data-ttu-id="e68f9-111">Handleiding voor Windows PowerShell-programmeurs</span><span class="sxs-lookup"><span data-stu-id="e68f9-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="e68f9-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="e68f9-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
