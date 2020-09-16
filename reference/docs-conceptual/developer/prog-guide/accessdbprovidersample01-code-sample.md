---
title: Voor beeld van AccessDbProviderSample01-code | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 2e9f81b3011ea1b27bafd9e02ea7e0faf7903a62
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784823"
---
# <a name="accessdbprovidersample01-code-sample"></a><span data-ttu-id="00de8-102">AccessDbProviderSample01-codevoorbeeld</span><span class="sxs-lookup"><span data-stu-id="00de8-102">AccessDbProviderSample01 Code Sample</span></span>

<span data-ttu-id="00de8-103">De volgende code toont de implementatie van de Windows Power shell-provider die wordt beschreven in [een eenvoudige Windows Power shell-provider maken](./creating-a-basic-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="00de8-103">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Basic Windows PowerShell Provider](./creating-a-basic-windows-powershell-provider.md).</span></span>
<span data-ttu-id="00de8-104">Deze implementatie biedt methoden voor het starten en stoppen van de provider, en hoewel het geen manier biedt om toegang te krijgen tot een gegevens archief of om gegevens op te halen of in te stellen in het gegevens archief, beschikt u over de basis functionaliteit die is vereist voor alle providers.</span><span class="sxs-lookup"><span data-stu-id="00de8-104">This implementation provides methods for starting and stopping the provider, and although it does not provide a means to access a data store or to get or set the data in the data store, it does provide the basic functionality that is required by all providers.</span></span>

> [!NOTE]
> <span data-ttu-id="00de8-105">U kunt het C#-bron bestand (AccessDBSampleProvider01.cs) voor deze provider downloaden met behulp van de Windows Software Development Kit voor Windows Vista en Microsoft .NET Framework 3,0 runtime-onderdelen.</span><span class="sxs-lookup"><span data-stu-id="00de8-105">You can download the C# source file (AccessDBSampleProvider01.cs) for this provider by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="00de8-106">Zie [Windows Power Shell installeren en de Windows Power shell-SDK downloaden](/powershell/scripting/developer/installing-the-windows-powershell-sdk)voor instructies voor het downloaden.</span><span class="sxs-lookup"><span data-stu-id="00de8-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="00de8-107">De gedownloade bron bestanden bevinden zich in de **\<PowerShell Samples>** map.</span><span class="sxs-lookup"><span data-stu-id="00de8-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span> <span data-ttu-id="00de8-108">Zie [uw Windows Power shell-provider ontwerpen](./designing-your-windows-powershell-provider.md)voor meer informatie over andere implementaties van Windows Power shell-providers.</span><span class="sxs-lookup"><span data-stu-id="00de8-108">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="00de8-109">Code voorbeeld</span><span class="sxs-lookup"><span data-stu-id="00de8-109">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs" range="11-30":::

## <a name="see-also"></a><span data-ttu-id="00de8-110">Zie ook</span><span class="sxs-lookup"><span data-stu-id="00de8-110">See Also</span></span>

[<span data-ttu-id="00de8-111">Handleiding voor Windows PowerShell-programmeurs</span><span class="sxs-lookup"><span data-stu-id="00de8-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="00de8-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="00de8-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
