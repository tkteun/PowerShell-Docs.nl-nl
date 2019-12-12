---
title: Voor beeld van AccessDbProviderSample04-code | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9374c4a-e499-4516-9eb6-107c59df98d9
caps.latest.revision: 7
ms.openlocfilehash: ff43286bc90c1a4d2270be0ee03ca5910867cec2
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72357300"
---
# <a name="accessdbprovidersample04-code-sample"></a><span data-ttu-id="553fd-102">AccessDBProviderSample04-codevoorbeeld</span><span class="sxs-lookup"><span data-stu-id="553fd-102">AccessDbProviderSample04 Code Sample</span></span>

<span data-ttu-id="553fd-103">De volgende code toont de implementatie van de Windows Power shell-provider die wordt beschreven in [een Windows Power shell-container provider maken](./creating-a-windows-powershell-container-provider.md).</span><span class="sxs-lookup"><span data-stu-id="553fd-103">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Windows PowerShell Container Provider](./creating-a-windows-powershell-container-provider.md).</span></span> <span data-ttu-id="553fd-104">Deze provider werkt op gegevens archieven met meerdere lagen.</span><span class="sxs-lookup"><span data-stu-id="553fd-104">This provider works on multi-layer data stores.</span></span> <span data-ttu-id="553fd-105">Voor dit type gegevens archief bevat het hoogste niveau van de Store de hoofd items en elk volgend niveau wordt een knoop punt van onderliggende items genoemd.</span><span class="sxs-lookup"><span data-stu-id="553fd-105">For this type of data store, the top level of the store contains the root items and each subsequent level is referred to as a node of child items.</span></span> <span data-ttu-id="553fd-106">Door de gebruiker toe te staan om deze onderliggende knoop punten te gebruiken, kan een gebruiker hiërarchisch communiceren via het gegevens archief.</span><span class="sxs-lookup"><span data-stu-id="553fd-106">By allowing the user to work on these child nodes, a user can interact hierarchically through the data store.</span></span>

## <a name="code-sample"></a><span data-ttu-id="553fd-107">Code voorbeeld</span><span class="sxs-lookup"><span data-stu-id="553fd-107">Code Sample</span></span>

[!code-csharp[AccessDBProviderSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a><span data-ttu-id="553fd-108">Zie ook</span><span class="sxs-lookup"><span data-stu-id="553fd-108">See Also</span></span>

[<span data-ttu-id="553fd-109">Windows Power shell SDK</span><span class="sxs-lookup"><span data-stu-id="553fd-109">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
