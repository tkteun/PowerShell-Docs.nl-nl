---
ms.date: 09/13/2016
ms.topic: reference
title: AccessDBProviderSample04-codevoorbeeld
description: AccessDBProviderSample04-codevoorbeeld
ms.openlocfilehash: bb70ce9f1b1c94349c354a8771fedf7fcb1bb320
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92647560"
---
# <a name="accessdbprovidersample04-code-sample"></a><span data-ttu-id="6ba51-103">AccessDBProviderSample04-codevoorbeeld</span><span class="sxs-lookup"><span data-stu-id="6ba51-103">AccessDbProviderSample04 Code Sample</span></span>

<span data-ttu-id="6ba51-104">De volgende code toont de implementatie van de Windows Power shell-provider die wordt beschreven in [een Windows Power shell-container provider maken](./creating-a-windows-powershell-container-provider.md).</span><span class="sxs-lookup"><span data-stu-id="6ba51-104">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Windows PowerShell Container Provider](./creating-a-windows-powershell-container-provider.md).</span></span>
<span data-ttu-id="6ba51-105">Deze provider werkt op gegevens archieven met meerdere lagen.</span><span class="sxs-lookup"><span data-stu-id="6ba51-105">This provider works on multi-layer data stores.</span></span> <span data-ttu-id="6ba51-106">Voor dit type gegevens archief bevat het hoogste niveau van de Store de hoofd items en elk volgend niveau wordt een knoop punt van onderliggende items genoemd.</span><span class="sxs-lookup"><span data-stu-id="6ba51-106">For this type of data store, the top level of the store contains the root items and each subsequent level is referred to as a node of child items.</span></span> <span data-ttu-id="6ba51-107">Door de gebruiker toe te staan om deze onderliggende knoop punten te gebruiken, kan een gebruiker hiërarchisch communiceren via het gegevens archief.</span><span class="sxs-lookup"><span data-stu-id="6ba51-107">By allowing the user to work on these child nodes, a user can interact hierarchically through the data store.</span></span>

## <a name="code-sample"></a><span data-ttu-id="6ba51-108">Code voorbeeld</span><span class="sxs-lookup"><span data-stu-id="6ba51-108">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs" range="11-1635":::

## <a name="see-also"></a><span data-ttu-id="6ba51-109">Zie ook</span><span class="sxs-lookup"><span data-stu-id="6ba51-109">See Also</span></span>

[<span data-ttu-id="6ba51-110">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="6ba51-110">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
