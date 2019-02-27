---
title: Codevoorbeeld AccessDbProviderSample04 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9374c4a-e499-4516-9eb6-107c59df98d9
caps.latest.revision: 7
ms.openlocfilehash: 43f01b9cd6af3ab6c26f88ee0c1e9269499b2bc3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845134"
---
# <a name="accessdbprovidersample04-code-sample"></a><span data-ttu-id="a4e8b-102">AccessDBProviderSample04-codevoorbeeld</span><span class="sxs-lookup"><span data-stu-id="a4e8b-102">AccessDbProviderSample04 Code Sample</span></span>

<span data-ttu-id="a4e8b-103">De volgende code toont de uitvoering van de Windows PowerShell-provider wordt beschreven in [het maken van een Windows PowerShell-Provider Container](./creating-a-windows-powershell-container-provider.md).</span><span class="sxs-lookup"><span data-stu-id="a4e8b-103">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Windows PowerShell Container Provider](./creating-a-windows-powershell-container-provider.md).</span></span> <span data-ttu-id="a4e8b-104">Deze provider werkt op meerdere lagen gegevensarchieven.</span><span class="sxs-lookup"><span data-stu-id="a4e8b-104">This provider works on multi-layer data stores.</span></span> <span data-ttu-id="a4e8b-105">Het hoogste niveau van de store bevat de items van de hoofdmap voor dit type gegevensarchief, en elke latere niveau wordt aangeduid als een knooppunt van het onderliggende items.</span><span class="sxs-lookup"><span data-stu-id="a4e8b-105">For this type of data store, the top level of the store contains the root items and each subsequent level is referred to as a node of child items.</span></span> <span data-ttu-id="a4e8b-106">Een gebruiker kan door de gebruiker om te werken op deze onderliggende knooppunten, hiërarchisch communiceren via het gegevensarchief.</span><span class="sxs-lookup"><span data-stu-id="a4e8b-106">By allowing the user to work on these child nodes, a user can interact hierarchically through the data store.</span></span>

## <a name="code-sample"></a><span data-ttu-id="a4e8b-107">Voorbeeld van code</span><span class="sxs-lookup"><span data-stu-id="a4e8b-107">Code Sample</span></span>

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a><span data-ttu-id="a4e8b-108">Zie ook</span><span class="sxs-lookup"><span data-stu-id="a4e8b-108">See Also</span></span>

[<span data-ttu-id="a4e8b-109">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="a4e8b-109">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)