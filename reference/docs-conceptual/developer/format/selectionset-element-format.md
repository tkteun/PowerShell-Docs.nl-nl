---
ms.date: 09/13/2016
ms.topic: reference
title: Het element SelectionSet (opmaak)
description: Het element SelectionSet (opmaak)
ms.openlocfilehash: 944aa83569ad8ca789746a71f60e5da5c19fbf01
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92647875"
---
# <a name="selectionset-element-format"></a><span data-ttu-id="374f0-103">Het element SelectionSet (opmaak)</span><span class="sxs-lookup"><span data-stu-id="374f0-103">SelectionSet Element (Format)</span></span>

<span data-ttu-id="374f0-104">Hiermee wordt een set .NET-objecten gedefinieerd waarnaar kan worden verwezen door de naam van de set.</span><span class="sxs-lookup"><span data-stu-id="374f0-104">Defines a set of .NET objects that can be referenced by the name of the set.</span></span>

<span data-ttu-id="374f0-105">Configuratie-element (indeling) SelectionSets element (indeling) element verzameling (indeling)</span><span class="sxs-lookup"><span data-stu-id="374f0-105">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="374f0-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="374f0-106">Syntax</span></span>

```xml
<SelectionSet>
  <Name>SelectionSetName</Name>
  <Types>...</Types>
</SelectionSet>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="374f0-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="374f0-107">Attributes and Elements</span></span>

<span data-ttu-id="374f0-108">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `SelectionSet` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="374f0-108">The following sections describe the attributes, child elements, and the parent element of the `SelectionSet` element.</span></span> <span data-ttu-id="374f0-109">Elke selectie reeks moet een naam hebben en moet de .NET-objecten van de set opgeven.</span><span class="sxs-lookup"><span data-stu-id="374f0-109">Each selection set must have a name, and it must specify the .NET objects of the set.</span></span>

### <a name="attributes"></a><span data-ttu-id="374f0-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="374f0-110">Attributes</span></span>

<span data-ttu-id="374f0-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="374f0-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="374f0-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="374f0-112">Child Elements</span></span>

|<span data-ttu-id="374f0-113">Element</span><span class="sxs-lookup"><span data-stu-id="374f0-113">Element</span></span>|<span data-ttu-id="374f0-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="374f0-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="374f0-115">Het element Naam voor SelectionSet (opmaak)</span><span class="sxs-lookup"><span data-stu-id="374f0-115">Name Element for SelectionSet (Format)</span></span>](./name-element-for-selectionset-format.md)|<span data-ttu-id="374f0-116">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="374f0-116">Required element.</span></span><br /><br /> <span data-ttu-id="374f0-117">Hiermee geeft u de naam op die wordt gebruikt om te verwijzen naar de selectieset.</span><span class="sxs-lookup"><span data-stu-id="374f0-117">Specifies the name used to reference the selection set.</span></span>|
|[<span data-ttu-id="374f0-118">Type-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="374f0-118">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)|<span data-ttu-id="374f0-119">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="374f0-119">Required element.</span></span><br /><br /> <span data-ttu-id="374f0-120">Hiermee definieert u de .NET-objecten die zich in de selectieset bevinden.</span><span class="sxs-lookup"><span data-stu-id="374f0-120">Defines the .NET objects that are in the selection set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="374f0-121">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="374f0-121">Parent Elements</span></span>

|<span data-ttu-id="374f0-122">Element</span><span class="sxs-lookup"><span data-stu-id="374f0-122">Element</span></span>|<span data-ttu-id="374f0-123">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="374f0-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="374f0-124">SelectionSets element indeling</span><span class="sxs-lookup"><span data-stu-id="374f0-124">SelectionSets Element Format</span></span>](./selectionsets-element-format.md)|<span data-ttu-id="374f0-125">Hiermee worden de algemene sets van .NET-objecten gedefinieerd die kunnen worden gebruikt door alle weer gaven van het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="374f0-125">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="374f0-126">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="374f0-126">Remarks</span></span>

<span data-ttu-id="374f0-127">U kunt selectie sets gebruiken wanneer u een set verwante objecten hebt waarnaar u wilt verwijzen met behulp van één naam, zoals een set objecten die zijn gerelateerd aan overname.</span><span class="sxs-lookup"><span data-stu-id="374f0-127">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="374f0-128">Wanneer u uw weer gaven definieert, kunt u de set met objecten opgeven door de naam van de selectieset te gebruiken in plaats van alle objecten in elke weer gave te vermelden.</span><span class="sxs-lookup"><span data-stu-id="374f0-128">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="374f0-129">Algemene selectie sets worden opgegeven met hun naam bij het definiëren van de weer gaven van het opmaak bestand of de definities van de weer gaven.</span><span class="sxs-lookup"><span data-stu-id="374f0-129">Common selection sets are specified by their name when defining the views of the formatting file or the definitions of the views.</span></span> <span data-ttu-id="374f0-130">In deze gevallen geeft het `SelectionSetName` onderliggende element van de- `ViewSelectedBy` en- `EntrySelectedBy` elementen de set op die moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="374f0-130">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` and `EntrySelectedBy` elements specifies the set to be used.</span></span> <span data-ttu-id="374f0-131">Zie [sets van objecten definiëren](./defining-selection-sets.md)voor meer informatie over selectie sets.</span><span class="sxs-lookup"><span data-stu-id="374f0-131">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="374f0-132">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="374f0-132">Example</span></span>

<span data-ttu-id="374f0-133">In het volgende voor beeld ziet u een- `SelectionSet` element dat vier .net-typen definieert.</span><span class="sxs-lookup"><span data-stu-id="374f0-133">The following example shows a `SelectionSet` element that defines four .NET types.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="374f0-134">Zie ook</span><span class="sxs-lookup"><span data-stu-id="374f0-134">See Also</span></span>

[<span data-ttu-id="374f0-135">Selectiereeksen definiëren</span><span class="sxs-lookup"><span data-stu-id="374f0-135">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="374f0-136">Element naam van de Selectieset (indeling)</span><span class="sxs-lookup"><span data-stu-id="374f0-136">Name Element of SelectionSet (Format)</span></span>](./name-element-for-selectionset-format.md)

[<span data-ttu-id="374f0-137">Het element SelectionSets (opmaak)</span><span class="sxs-lookup"><span data-stu-id="374f0-137">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="374f0-138">Type-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="374f0-138">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="374f0-139">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="374f0-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
