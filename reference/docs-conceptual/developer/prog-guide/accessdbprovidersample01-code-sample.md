---
title: Voor beeld van AccessDbProviderSample01-code | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 35540d2a-c18f-4179-b869-1a3dc5a8c1bd
caps.latest.revision: 6
ms.openlocfilehash: b52882c3f38b64347b9e9f2c3dedcc8a7dd02458
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/08/2020
ms.locfileid: "80978590"
---
# <a name="accessdbprovidersample01-code-sample"></a><span data-ttu-id="3287b-102">AccessDbProviderSample01-codevoorbeeld</span><span class="sxs-lookup"><span data-stu-id="3287b-102">AccessDbProviderSample01 Code Sample</span></span>

<span data-ttu-id="3287b-103">De volgende code toont de implementatie van de Windows Power shell-provider die wordt beschreven in [een eenvoudige Windows Power shell-provider maken](./creating-a-basic-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="3287b-103">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Basic Windows PowerShell Provider](./creating-a-basic-windows-powershell-provider.md).</span></span>
<span data-ttu-id="3287b-104">Deze implementatie biedt methoden voor het starten en stoppen van de provider, en hoewel het geen manier biedt om toegang te krijgen tot een gegevens archief of om gegevens op te halen of in te stellen in het gegevens archief, beschikt u over de basis functionaliteit die is vereist voor alle providers.</span><span class="sxs-lookup"><span data-stu-id="3287b-104">This implementation provides methods for starting and stopping the provider, and although it does not provide a means to access a data store or to get or set the data in the data store, it does provide the basic functionality that is required by all providers.</span></span>

> [!NOTE]
> <span data-ttu-id="3287b-105">U kunt het C# bron bestand (AccessDBSampleProvider01.cs) voor deze provider downloaden met behulp van de Windows Software Development Kit voor Windows Vista en Microsoft .NET Framework 3,0 runtime-onderdelen.</span><span class="sxs-lookup"><span data-stu-id="3287b-105">You can download the C# source file (AccessDBSampleProvider01.cs) for this provider by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="3287b-106">Zie [Windows Power Shell installeren en de Windows Power shell-SDK downloaden](/powershell/scripting/developer/installing-the-windows-powershell-sdk)voor instructies voor het downloaden.</span><span class="sxs-lookup"><span data-stu-id="3287b-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="3287b-107">De gedownloade bron bestanden zijn beschikbaar in de **\<Power shell-voor beelden >** map.</span><span class="sxs-lookup"><span data-stu-id="3287b-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span> <span data-ttu-id="3287b-108">Zie [uw Windows Power shell-provider ontwerpen](./designing-your-windows-powershell-provider.md)voor meer informatie over andere implementaties van Windows Power shell-providers.</span><span class="sxs-lookup"><span data-stu-id="3287b-108">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="3287b-109">Code voorbeeld</span><span class="sxs-lookup"><span data-stu-id="3287b-109">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs" range="11-30":::

## <a name="see-also"></a><span data-ttu-id="3287b-110">Zie ook</span><span class="sxs-lookup"><span data-stu-id="3287b-110">See Also</span></span>

[<span data-ttu-id="3287b-111">Hand leiding voor Windows Power shell-programmeurs</span><span class="sxs-lookup"><span data-stu-id="3287b-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="3287b-112">Windows Power shell SDK</span><span class="sxs-lookup"><span data-stu-id="3287b-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
