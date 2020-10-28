---
ms.date: 09/13/2016
ms.topic: reference
title: AccessDBProviderSample04-codevoorbeeld
description: AccessDBProviderSample04-codevoorbeeld
ms.openlocfilehash: bb70ce9f1b1c94349c354a8771fedf7fcb1bb320
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92647560"
---
# <a name="accessdbprovidersample04-code-sample"></a><span data-ttu-id="ed6be-103">AccessDBProviderSample04-codevoorbeeld</span><span class="sxs-lookup"><span data-stu-id="ed6be-103">AccessDbProviderSample04 Code Sample</span></span>

<span data-ttu-id="ed6be-104">De volgende code toont de implementatie van de Windows Power shell-provider die wordt beschreven in [een Windows Power shell-container provider maken](./creating-a-windows-powershell-container-provider.md).</span><span class="sxs-lookup"><span data-stu-id="ed6be-104">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Windows PowerShell Container Provider](./creating-a-windows-powershell-container-provider.md).</span></span>
<span data-ttu-id="ed6be-105">Deze provider werkt op gegevens archieven met meerdere lagen.</span><span class="sxs-lookup"><span data-stu-id="ed6be-105">This provider works on multi-layer data stores.</span></span> <span data-ttu-id="ed6be-106">Voor dit type gegevens archief bevat het hoogste niveau van de Store de hoofd items en elk volgend niveau wordt een knoop punt van onderliggende items genoemd.</span><span class="sxs-lookup"><span data-stu-id="ed6be-106">For this type of data store, the top level of the store contains the root items and each subsequent level is referred to as a node of child items.</span></span> <span data-ttu-id="ed6be-107">Door de gebruiker toe te staan om deze onderliggende knoop punten te gebruiken, kan een gebruiker hiërarchisch communiceren via het gegevens archief.</span><span class="sxs-lookup"><span data-stu-id="ed6be-107">By allowing the user to work on these child nodes, a user can interact hierarchically through the data store.</span></span>

## <a name="code-sample"></a><span data-ttu-id="ed6be-108">Code voorbeeld</span><span class="sxs-lookup"><span data-stu-id="ed6be-108">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs" range="11-1635":::

## <a name="see-also"></a><span data-ttu-id="ed6be-109">Zie ook</span><span class="sxs-lookup"><span data-stu-id="ed6be-109">See Also</span></span>

[<span data-ttu-id="ed6be-110">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="ed6be-110">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
