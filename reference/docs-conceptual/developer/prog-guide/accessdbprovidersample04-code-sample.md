---
title: Voor beeld van AccessDbProviderSample04-code | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 05509c5b36475bcd3f91c9ab7413974994d668d6
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787271"
---
# <a name="accessdbprovidersample04-code-sample"></a><span data-ttu-id="c9346-102">AccessDBProviderSample04-codevoorbeeld</span><span class="sxs-lookup"><span data-stu-id="c9346-102">AccessDbProviderSample04 Code Sample</span></span>

<span data-ttu-id="c9346-103">De volgende code toont de implementatie van de Windows Power shell-provider die wordt beschreven in [een Windows Power shell-container provider maken](./creating-a-windows-powershell-container-provider.md).</span><span class="sxs-lookup"><span data-stu-id="c9346-103">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Windows PowerShell Container Provider](./creating-a-windows-powershell-container-provider.md).</span></span>
<span data-ttu-id="c9346-104">Deze provider werkt op gegevens archieven met meerdere lagen.</span><span class="sxs-lookup"><span data-stu-id="c9346-104">This provider works on multi-layer data stores.</span></span> <span data-ttu-id="c9346-105">Voor dit type gegevens archief bevat het hoogste niveau van de Store de hoofd items en elk volgend niveau wordt een knoop punt van onderliggende items genoemd.</span><span class="sxs-lookup"><span data-stu-id="c9346-105">For this type of data store, the top level of the store contains the root items and each subsequent level is referred to as a node of child items.</span></span> <span data-ttu-id="c9346-106">Door de gebruiker toe te staan om deze onderliggende knoop punten te gebruiken, kan een gebruiker hiërarchisch communiceren via het gegevens archief.</span><span class="sxs-lookup"><span data-stu-id="c9346-106">By allowing the user to work on these child nodes, a user can interact hierarchically through the data store.</span></span>

## <a name="code-sample"></a><span data-ttu-id="c9346-107">Code voorbeeld</span><span class="sxs-lookup"><span data-stu-id="c9346-107">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs" range="11-1635":::

## <a name="see-also"></a><span data-ttu-id="c9346-108">Zie ook</span><span class="sxs-lookup"><span data-stu-id="c9346-108">See Also</span></span>

[<span data-ttu-id="c9346-109">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="c9346-109">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
