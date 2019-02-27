---
title: EnumerableExpansions-Element (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 50c33892-2ade-44c2-906c-81e5f5ca21f2
caps.latest.revision: 9
ms.openlocfilehash: 1ecbda8a3b623757517019105e3b1ee46ccbb55c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849789"
---
# <a name="enumerableexpansions-element-format"></a><span data-ttu-id="ca31e-102">Het element EnumerableExpansions (opmaak)</span><span class="sxs-lookup"><span data-stu-id="ca31e-102">EnumerableExpansions Element (Format)</span></span>

<span data-ttu-id="ca31e-103">Hiermee definieert u hoe .NET-verzameling objecten worden uitgevouwen wanneer ze worden weergegeven in een weergave.</span><span class="sxs-lookup"><span data-stu-id="ca31e-103">Defines how .NET collection objects are expanded when they are displayed in a view.</span></span>

<span data-ttu-id="ca31e-104">Configuratie Element (indeling) DefaultSettings-Element (indeling) EnumerableExpansions-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="ca31e-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ca31e-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="ca31e-105">Syntax</span></span>

```xml
<EnumerableExpansions>
  <EnumerableExpansion>...</EnumerableExpansion>
</EnumerableExpansions>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ca31e-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="ca31e-106">Attributes and Elements</span></span>

<span data-ttu-id="ca31e-107">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `EnumerableExpansions` element.</span><span class="sxs-lookup"><span data-stu-id="ca31e-107">The following sections describe attributes, child elements, and the parent element of the `EnumerableExpansions` element.</span></span> <span data-ttu-id="ca31e-108">Er is geen limiet voor het aantal onderliggende elementen die u kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="ca31e-108">There is no limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="ca31e-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="ca31e-109">Attributes</span></span>

<span data-ttu-id="ca31e-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="ca31e-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ca31e-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="ca31e-111">Child Elements</span></span>

|<span data-ttu-id="ca31e-112">Element</span><span class="sxs-lookup"><span data-stu-id="ca31e-112">Element</span></span>|<span data-ttu-id="ca31e-113">Description</span><span class="sxs-lookup"><span data-stu-id="ca31e-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ca31e-114">EnumerableExpansion-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="ca31e-114">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="ca31e-115">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="ca31e-115">Optional element.</span></span><br /><br /> <span data-ttu-id="ca31e-116">Hiermee definieert u de specifieke versie van .NET verzameling objecten die worden uitgevouwen wanneer ze worden weergegeven in een weergave.</span><span class="sxs-lookup"><span data-stu-id="ca31e-116">Defines the specific .NET collection objects that are expanded when they are displayed in a view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ca31e-117">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="ca31e-117">Parent Elements</span></span>

|<span data-ttu-id="ca31e-118">Element</span><span class="sxs-lookup"><span data-stu-id="ca31e-118">Element</span></span>|<span data-ttu-id="ca31e-119">Description</span><span class="sxs-lookup"><span data-stu-id="ca31e-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ca31e-120">DefaultSettings-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="ca31e-120">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="ca31e-121">Algemene instellingen die betrekking hebben op alle weergaven van de opmaak bestand definieert.</span><span class="sxs-lookup"><span data-stu-id="ca31e-121">Defines common settings that apply to all the views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ca31e-122">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="ca31e-122">Remarks</span></span>

<span data-ttu-id="ca31e-123">Dit element wordt gebruikt om te definiëren hoe de verzameling en de objecten in de verzameling worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="ca31e-123">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="ca31e-124">In dit geval een verzamelingsobject verwijst naar objecten die ondersteuning biedt voor de **System.Collections.ICollection** interface.</span><span class="sxs-lookup"><span data-stu-id="ca31e-124">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

## <a name="see-also"></a><span data-ttu-id="ca31e-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="ca31e-125">See Also</span></span>

[<span data-ttu-id="ca31e-126">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="ca31e-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
