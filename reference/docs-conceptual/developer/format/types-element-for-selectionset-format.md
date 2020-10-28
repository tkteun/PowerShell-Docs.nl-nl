---
ms.date: 09/13/2016
ms.topic: reference
title: Het element Typen voor SelectionSet (opmaak)
description: Het element Typen voor SelectionSet (opmaak)
ms.openlocfilehash: ff3c24e7f52f862dc416b88d50983196ce907012
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92645460"
---
# <a name="types-element-for-selectionset-format"></a><span data-ttu-id="33989-103">Het element Typen voor SelectionSet (opmaak)</span><span class="sxs-lookup"><span data-stu-id="33989-103">Types Element for SelectionSet (Format)</span></span>

<span data-ttu-id="33989-104">Hiermee definieert u de .NET-objecten die zich in de selectieset bevinden.</span><span class="sxs-lookup"><span data-stu-id="33989-104">Defines the .NET objects that are in the selection set.</span></span>

<span data-ttu-id="33989-105">Configuratie-element (indeling) SelectionSets element (Format) element van het type Selectionset (indeling) element (indeling)</span><span class="sxs-lookup"><span data-stu-id="33989-105">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Types Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="33989-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="33989-106">Syntax</span></span>

```xml
<Types>
  <TypeName>Nameof.NetType</TypeName>
</Types>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="33989-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="33989-107">Attributes and Elements</span></span>

<span data-ttu-id="33989-108">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `Types` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="33989-108">The following sections describe the attributes, child elements, and the parent element of the `Types` element.</span></span> <span data-ttu-id="33989-109">Er moet ten minste één onderliggend element zijn, maar er is geen maximum limiet voor het aantal onderliggende elementen dat kan worden toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="33989-109">There must be at least one child element, but there is no maximum limit to the number of child elements that can be added.</span></span>

### <a name="attributes"></a><span data-ttu-id="33989-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="33989-110">Attributes</span></span>

<span data-ttu-id="33989-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="33989-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="33989-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="33989-112">Child Elements</span></span>

|<span data-ttu-id="33989-113">Element</span><span class="sxs-lookup"><span data-stu-id="33989-113">Element</span></span>|<span data-ttu-id="33989-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="33989-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="33989-115">TypeName-element van typen (indeling)</span><span class="sxs-lookup"><span data-stu-id="33989-115">TypeName Element of Types (Format)</span></span>](./typename-element-for-types-format.md)|<span data-ttu-id="33989-116">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="33989-116">Required element.</span></span><br /><br /> <span data-ttu-id="33989-117">Hiermee geeft u het .NET-object op dat deel uitmaakt van de selectieset.</span><span class="sxs-lookup"><span data-stu-id="33989-117">Specifies the .NET object that belongs to the selection set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="33989-118">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="33989-118">Parent Elements</span></span>

|<span data-ttu-id="33989-119">Element</span><span class="sxs-lookup"><span data-stu-id="33989-119">Element</span></span>|<span data-ttu-id="33989-120">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="33989-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="33989-121">Het element SelectionSet (opmaak)</span><span class="sxs-lookup"><span data-stu-id="33989-121">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="33989-122">Hiermee wordt een set .NET-objecten gedefinieerd waarnaar kan worden verwezen door de naam van de set.</span><span class="sxs-lookup"><span data-stu-id="33989-122">Defines a set of .NET objects that can be referenced by the name of the set.</span></span>|

## <a name="remarks"></a><span data-ttu-id="33989-123">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="33989-123">Remarks</span></span>

<span data-ttu-id="33989-124">De objecten die door dit element worden gedefinieerd, vormen een selectie reeks die kan worden gebruikt door een weer gave, op basis van een definitie van een weer gave (weer gaven kunnen meerdere definities hebben) of wanneer een selectie voorwaarde wordt opgegeven.</span><span class="sxs-lookup"><span data-stu-id="33989-124">The objects defined by this element make up a selection set that can be used by a view, by a definition of a view (views can have multiple definitions), or when specifying a selection condition.</span></span>  <span data-ttu-id="33989-125">Zie [sets van objecten definiëren](./defining-selection-sets.md)voor meer informatie over selectie sets.</span><span class="sxs-lookup"><span data-stu-id="33989-125">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="33989-126">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="33989-126">Example</span></span>

<span data-ttu-id="33989-127">In dit voor beeld ziet u een- `SelectionSet` element dat vier .net-typen definieert.</span><span class="sxs-lookup"><span data-stu-id="33989-127">This example shows a `SelectionSet` element that defines four .NET types.</span></span>

```xml
<SelectionSets>
  <SelectionSet>
    <Name>FileSystemTypes</Name>
    <Types>
     <TypeName>System.IO.DirectoryInfo</TypeName>
     <TypeName>System.IO.FileInfo</TypeName>
     <TypeName>Deserialized.System.IO.DirectoryInfo</TypeName>
     <TypeName>Deserialized.System.IO.FileInfo</TypeName>
    </Types>
  </SelectionSet>
</SelectionSets>
```

## <a name="see-also"></a><span data-ttu-id="33989-128">Zie ook</span><span class="sxs-lookup"><span data-stu-id="33989-128">See Also</span></span>

[<span data-ttu-id="33989-129">Sets van objecten definiëren</span><span class="sxs-lookup"><span data-stu-id="33989-129">Defining Sets of Objects</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="33989-130">Het element SelectionSet (opmaak)</span><span class="sxs-lookup"><span data-stu-id="33989-130">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="33989-131">TypeName-element van typen (indeling)</span><span class="sxs-lookup"><span data-stu-id="33989-131">TypeName Element of Types (Format)</span></span>](./typename-element-for-types-format.md)

[<span data-ttu-id="33989-132">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="33989-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
