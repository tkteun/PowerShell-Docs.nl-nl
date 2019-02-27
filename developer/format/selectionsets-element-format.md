---
title: SelectionSets-Element (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ebbac73a-1c99-4388-9f47-703cd024dc6d
caps.latest.revision: 18
ms.openlocfilehash: a9356635d60d5f8c5d4dec4ec8b7d0aea2b037dd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845106"
---
# <a name="selectionsets-element-format"></a><span data-ttu-id="2c92b-102">Het element SelectionSets (opmaak)</span><span class="sxs-lookup"><span data-stu-id="2c92b-102">SelectionSets Element (Format)</span></span>

<span data-ttu-id="2c92b-103">Hiermee definieert u de algemene sets met .NET-objecten die kunnen worden gebruikt door alle weergaven van de opmaak-bestand.</span><span class="sxs-lookup"><span data-stu-id="2c92b-103">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span> <span data-ttu-id="2c92b-104">De weergaven en besturingselementen van het bestand opmaak kunnen de volledige set van objecten verwijzen naar een met behulp van alleen de naam van de selectie op.</span><span class="sxs-lookup"><span data-stu-id="2c92b-104">The views and controls of the formatting file can reference the complete set of objects by using only the name of the selection set.</span></span>

<span data-ttu-id="2c92b-105">Indeling van de configuratie-Element SelectionSets-Element</span><span class="sxs-lookup"><span data-stu-id="2c92b-105">Configuration Element SelectionSets Element Format</span></span>

## <a name="syntax"></a><span data-ttu-id="2c92b-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="2c92b-106">Syntax</span></span>

```xml
<SelectionSets>
  <SelectionSet>...</SelectionSet>
</SelectionSets>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2c92b-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="2c92b-107">Attributes and Elements</span></span>

<span data-ttu-id="2c92b-108">De volgende secties worden de kenmerken, de onderliggende elementen en het bovenliggende element van de `SelectionSets` element.</span><span class="sxs-lookup"><span data-stu-id="2c92b-108">The following sections describe the attributes, child elements, and parent element of the `SelectionSets` element.</span></span> <span data-ttu-id="2c92b-109">Elk onderliggend element definieert een set van objecten die kan worden verwezen door de naam van de set.</span><span class="sxs-lookup"><span data-stu-id="2c92b-109">Each child element defines a set of objects that can be referenced by the name of the set.</span></span> <span data-ttu-id="2c92b-110">De volgorde van de onderliggende elementen is niet belangrijk.</span><span class="sxs-lookup"><span data-stu-id="2c92b-110">The order of the child elements is not significant.</span></span>

### <a name="attributes"></a><span data-ttu-id="2c92b-111">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="2c92b-111">Attributes</span></span>

<span data-ttu-id="2c92b-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="2c92b-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2c92b-113">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="2c92b-113">Child Elements</span></span>

|<span data-ttu-id="2c92b-114">Element</span><span class="sxs-lookup"><span data-stu-id="2c92b-114">Element</span></span>|<span data-ttu-id="2c92b-115">Description</span><span class="sxs-lookup"><span data-stu-id="2c92b-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2c92b-116">SelectionSet-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="2c92b-116">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="2c92b-117">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="2c92b-117">Required element.</span></span><br /><br /> <span data-ttu-id="2c92b-118">Definieert één set met .NET-objecten die kan worden verwezen door de naam van de set.</span><span class="sxs-lookup"><span data-stu-id="2c92b-118">Defines a single set of .NET objects that can be referenced by the name of the set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="2c92b-119">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="2c92b-119">Parent Elements</span></span>

|<span data-ttu-id="2c92b-120">Element</span><span class="sxs-lookup"><span data-stu-id="2c92b-120">Element</span></span>|<span data-ttu-id="2c92b-121">Description</span><span class="sxs-lookup"><span data-stu-id="2c92b-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2c92b-122">Configuratie-Element</span><span class="sxs-lookup"><span data-stu-id="2c92b-122">Configuration Element</span></span>](./configuration-element-format.md)|<span data-ttu-id="2c92b-123">Hiermee geeft u het element op het hoogste niveau van een bestand met opmaak.</span><span class="sxs-lookup"><span data-stu-id="2c92b-123">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2c92b-124">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="2c92b-124">Remarks</span></span>

<span data-ttu-id="2c92b-125">U kunt selectiesets gebruiken wanneer u een set van gerelateerde objecten die u verwijzen wilt met behulp van één naam, zoals een set objecten die via overname verwant zijn hebt.</span><span class="sxs-lookup"><span data-stu-id="2c92b-125">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="2c92b-126">Bij het definiëren van uw weergaven, kunt u de set objecten opgeven met behulp van de naam van de selectie instellen in plaats van de lijst van alle objecten in elke weergave.</span><span class="sxs-lookup"><span data-stu-id="2c92b-126">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="2c92b-127">Algemene selectiesets worden opgegeven door de naam bij het definiëren van de weergaven van de opmaak bestand of de definities van de weergaven.</span><span class="sxs-lookup"><span data-stu-id="2c92b-127">Common selection sets are specified by their name when defining the views of the formatting file or the definitions of the views.</span></span> <span data-ttu-id="2c92b-128">In dergelijke gevallen de `SelectionSetName` onderliggend element van de `ViewSelectedBy` en `EntrySelectedBy` elementen Hiermee geeft u de set moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="2c92b-128">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` and `EntrySelectedBy` elements specifies the set to be used.</span></span> <span data-ttu-id="2c92b-129">Zie voor meer informatie over selectiesets [ingesteld definiëren van objecten](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="2c92b-129">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2c92b-130">Zie ook</span><span class="sxs-lookup"><span data-stu-id="2c92b-130">See Also</span></span>

[<span data-ttu-id="2c92b-131">Configuratie-Element</span><span class="sxs-lookup"><span data-stu-id="2c92b-131">Configuration Element</span></span>](./configuration-element-format.md)

[<span data-ttu-id="2c92b-132">Selectiesets definiëren</span><span class="sxs-lookup"><span data-stu-id="2c92b-132">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="2c92b-133">SelectionSet-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="2c92b-133">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="2c92b-134">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="2c92b-134">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
