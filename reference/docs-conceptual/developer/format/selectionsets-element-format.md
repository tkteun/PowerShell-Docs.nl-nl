---
ms.date: 09/13/2016
ms.topic: reference
title: Het element SelectionSets (opmaak)
description: Het element SelectionSets (opmaak)
ms.openlocfilehash: e5c928dfb82bc6963b4a87aef9ec06d34cacfdcb
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92654929"
---
# <a name="selectionsets-element-format"></a><span data-ttu-id="80499-103">Het element SelectionSets (opmaak)</span><span class="sxs-lookup"><span data-stu-id="80499-103">SelectionSets Element (Format)</span></span>

<span data-ttu-id="80499-104">Hiermee worden de algemene sets van .NET-objecten gedefinieerd die kunnen worden gebruikt door alle weer gaven van het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="80499-104">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span> <span data-ttu-id="80499-105">De weer gaven en besturings elementen van het opmaak bestand kunnen verwijzen naar de volledige set met objecten door alleen de naam van de selectieset te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="80499-105">The views and controls of the formatting file can reference the complete set of objects by using only the name of the selection set.</span></span>

<span data-ttu-id="80499-106">SelectionSets element indeling van configuratie-element</span><span class="sxs-lookup"><span data-stu-id="80499-106">Configuration Element SelectionSets Element Format</span></span>

## <a name="syntax"></a><span data-ttu-id="80499-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="80499-107">Syntax</span></span>

```xml
<SelectionSets>
  <SelectionSet>...</SelectionSet>
</SelectionSets>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="80499-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="80499-108">Attributes and Elements</span></span>

<span data-ttu-id="80499-109">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `SelectionSets` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="80499-109">The following sections describe the attributes, child elements, and parent element of the `SelectionSets` element.</span></span> <span data-ttu-id="80499-110">Elk onderliggend element definieert een set objecten waarnaar kan worden verwezen door de naam van de set.</span><span class="sxs-lookup"><span data-stu-id="80499-110">Each child element defines a set of objects that can be referenced by the name of the set.</span></span> <span data-ttu-id="80499-111">De volg orde van de onderliggende elementen is niet significant.</span><span class="sxs-lookup"><span data-stu-id="80499-111">The order of the child elements is not significant.</span></span>

### <a name="attributes"></a><span data-ttu-id="80499-112">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="80499-112">Attributes</span></span>

<span data-ttu-id="80499-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="80499-113">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="80499-114">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="80499-114">Child Elements</span></span>

|<span data-ttu-id="80499-115">Element</span><span class="sxs-lookup"><span data-stu-id="80499-115">Element</span></span>|<span data-ttu-id="80499-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="80499-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="80499-117">Het element SelectionSet (opmaak)</span><span class="sxs-lookup"><span data-stu-id="80499-117">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="80499-118">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="80499-118">Required element.</span></span><br /><br /> <span data-ttu-id="80499-119">Hiermee wordt één set .NET-objecten gedefinieerd waarnaar kan worden verwezen met de naam van de set.</span><span class="sxs-lookup"><span data-stu-id="80499-119">Defines a single set of .NET objects that can be referenced by the name of the set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="80499-120">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="80499-120">Parent Elements</span></span>

|<span data-ttu-id="80499-121">Element</span><span class="sxs-lookup"><span data-stu-id="80499-121">Element</span></span>|<span data-ttu-id="80499-122">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="80499-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="80499-123">Configuratie-element</span><span class="sxs-lookup"><span data-stu-id="80499-123">Configuration Element</span></span>](./configuration-element-format.md)|<span data-ttu-id="80499-124">Vertegenwoordigt het element op het hoogste niveau van een opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="80499-124">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="80499-125">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="80499-125">Remarks</span></span>

<span data-ttu-id="80499-126">U kunt selectie sets gebruiken wanneer u een set verwante objecten hebt waarnaar u wilt verwijzen met behulp van één naam, zoals een set objecten die zijn gerelateerd aan overname.</span><span class="sxs-lookup"><span data-stu-id="80499-126">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="80499-127">Wanneer u uw weer gaven definieert, kunt u de set met objecten opgeven door de naam van de selectieset te gebruiken in plaats van alle objecten in elke weer gave te vermelden.</span><span class="sxs-lookup"><span data-stu-id="80499-127">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="80499-128">Algemene selectie sets worden opgegeven met hun naam bij het definiëren van de weer gaven van het opmaak bestand of de definities van de weer gaven.</span><span class="sxs-lookup"><span data-stu-id="80499-128">Common selection sets are specified by their name when defining the views of the formatting file or the definitions of the views.</span></span> <span data-ttu-id="80499-129">In deze gevallen geeft het `SelectionSetName` onderliggende element van de- `ViewSelectedBy` en- `EntrySelectedBy` elementen de set op die moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="80499-129">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` and `EntrySelectedBy` elements specifies the set to be used.</span></span> <span data-ttu-id="80499-130">Zie [sets van objecten definiëren](./defining-selection-sets.md)voor meer informatie over selectie sets.</span><span class="sxs-lookup"><span data-stu-id="80499-130">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="80499-131">Zie ook</span><span class="sxs-lookup"><span data-stu-id="80499-131">See Also</span></span>

[<span data-ttu-id="80499-132">Configuratie-element</span><span class="sxs-lookup"><span data-stu-id="80499-132">Configuration Element</span></span>](./configuration-element-format.md)

[<span data-ttu-id="80499-133">Selectiereeksen definiëren</span><span class="sxs-lookup"><span data-stu-id="80499-133">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="80499-134">Het element SelectionSet (opmaak)</span><span class="sxs-lookup"><span data-stu-id="80499-134">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="80499-135">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="80499-135">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
