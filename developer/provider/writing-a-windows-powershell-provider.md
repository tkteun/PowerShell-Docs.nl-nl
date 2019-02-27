---
title: Schrijven van een Windows PowerShell-Provider | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a54ce657-e0e0-4b3e-b9dc-aed39876f933
caps.latest.revision: 11
ms.openlocfilehash: 58252956184703fdcdb3aa9b1db617c6e91294c1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849649"
---
# <a name="writing-a-windows-powershell-provider"></a><span data-ttu-id="fdf55-102">Een Windows PowerShell-provider schrijven</span><span class="sxs-lookup"><span data-stu-id="fdf55-102">Writing a Windows PowerShell Provider</span></span>

<span data-ttu-id="fdf55-103">'Het schrijven van een Windows PowerShell-Provider' is voor programmamanagers aan wie het ontwerpen van Windows PowerShell-providers en voor ontwikkelaars die provider code implementeert.</span><span class="sxs-lookup"><span data-stu-id="fdf55-103">"Writing a Windows PowerShell Provider" is for program managers who are designing Windows PowerShell providers and for developers who are implementing provider code.</span></span> <span data-ttu-id="fdf55-104">Deze krijgt u inzicht in de werking van Windows PowerShell-providers, en biedt voorbeeldcode die u gebruiken kunt om het ontwerpen van of schrijven van uw eigen providers te starten.</span><span class="sxs-lookup"><span data-stu-id="fdf55-104">It will help you understand how Windows PowerShell providers work, and it provides sample code that you can use to start designing or writing your own providers.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="fdf55-105">In deze sectie</span><span class="sxs-lookup"><span data-stu-id="fdf55-105">In This Section</span></span>

<span data-ttu-id="fdf55-106">[Quick Start Windows PowerShell-Provider](./windows-powershell-provider-quickstart.md) voorbeeldcode en overzicht van de provider van een zeer eenvoudig.</span><span class="sxs-lookup"><span data-stu-id="fdf55-106">[Windows PowerShell Provider QuickStart](./windows-powershell-provider-quickstart.md) Example code and walkthrough of a very basic provider.</span></span>

<span data-ttu-id="fdf55-107">[Overzicht van Windows PowerShell-Provider](./windows-powershell-provider-overview.md) in deze sectie bevat onderwerpen waarin wordt beschreven wat er in Windows PowerShell-providers zijn en hoe deze werken.</span><span class="sxs-lookup"><span data-stu-id="fdf55-107">[Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md) This section contains topics that describe what Windows PowerShell providers are and how they work.</span></span>

<span data-ttu-id="fdf55-108">[Schrijven van een provider item](./writing-an-item-provider.md) voorbeeldcode en overzicht van de methoden die ondersteuning bieden voor ophalen en instellen van items.</span><span class="sxs-lookup"><span data-stu-id="fdf55-108">[Writing an item provider](./writing-an-item-provider.md) Example code and walkthrough of methods that support getting and setting items.</span></span>

<span data-ttu-id="fdf55-109">[Schrijven van een provider container](./writing-a-container-provider.md) voorbeeldcode en overzicht van de methoden die ondersteuning bieden voor containers (items die andere items als onderliggende items hebben).</span><span class="sxs-lookup"><span data-stu-id="fdf55-109">[Writing a container provider](./writing-a-container-provider.md) Example code and walkthrough of methods that support containers (items that have other items as children).</span></span>

<span data-ttu-id="fdf55-110">[Schrijven van een provider navigatie](./writing-a-navigation-provider.md) voorbeeldcode en overzicht van de methoden die ondersteuning bieden voor geneste containers, relatieve paden en items van een pad naar de andere verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="fdf55-110">[Writing a navigation provider](./writing-a-navigation-provider.md) Example code and walkthrough of methods that support nested containers, relative paths, and moving items from one path to another.</span></span>

<span data-ttu-id="fdf55-111">[Voorbeelden van de provider](./provider-samples.md) in deze sectie bevat voorbeelden van providers.</span><span class="sxs-lookup"><span data-stu-id="fdf55-111">[Provider Samples](./provider-samples.md) This section provides samples of providers.</span></span>

## <a name="see-also"></a><span data-ttu-id="fdf55-112">Zie ook</span><span class="sxs-lookup"><span data-stu-id="fdf55-112">See Also</span></span>

[<span data-ttu-id="fdf55-113">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="fdf55-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)