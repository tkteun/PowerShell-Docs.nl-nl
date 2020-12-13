---
ms.date: 09/13/2016
ms.topic: reference
title: Het element Naam voor SelectionSet (opmaak)
description: Het element Naam voor SelectionSet (opmaak)
ms.openlocfilehash: 98c13be6ea352055231fbdb3a60f0eb508f661b8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666452"
---
# <a name="name-element-for-selectionset-format"></a><span data-ttu-id="f20f0-103">Het element Naam voor SelectionSet (opmaak)</span><span class="sxs-lookup"><span data-stu-id="f20f0-103">Name Element for SelectionSet (Format)</span></span>

<span data-ttu-id="f20f0-104">Hiermee geeft u de naam op die wordt gebruikt om te verwijzen naar de selectieset.</span><span class="sxs-lookup"><span data-stu-id="f20f0-104">Specifies the name used to reference the selection set.</span></span>

<span data-ttu-id="f20f0-105">Configuratie-element (indeling) SelectionSets element (Format) element van de verzameling (indeling) naam element van de Selectieset (indeling)</span><span class="sxs-lookup"><span data-stu-id="f20f0-105">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Name Element of SelectionSet (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f20f0-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="f20f0-106">Syntax</span></span>

```xml
<Name>Name of selection set</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f20f0-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="f20f0-107">Attributes and Elements</span></span>

<span data-ttu-id="f20f0-108">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `Name` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="f20f0-108">The following sections describe the attributes, child elements, and parent element of the `Name` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f20f0-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="f20f0-109">Attributes</span></span>

<span data-ttu-id="f20f0-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="f20f0-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f20f0-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="f20f0-111">Child Elements</span></span>

<span data-ttu-id="f20f0-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="f20f0-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f20f0-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="f20f0-113">Parent Elements</span></span>

|<span data-ttu-id="f20f0-114">Element</span><span class="sxs-lookup"><span data-stu-id="f20f0-114">Element</span></span>|<span data-ttu-id="f20f0-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="f20f0-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f20f0-116">Het element SelectionSet (opmaak)</span><span class="sxs-lookup"><span data-stu-id="f20f0-116">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="f20f0-117">Hiermee wordt één set .NET-objecten gedefinieerd waarnaar kan worden verwezen met de naam van de set.</span><span class="sxs-lookup"><span data-stu-id="f20f0-117">Defines a single set of .NET objects that can be referenced by the name of the set.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f20f0-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="f20f0-118">Text Value</span></span>

<span data-ttu-id="f20f0-119">Geef de naam op om te verwijzen naar de selectieset.</span><span class="sxs-lookup"><span data-stu-id="f20f0-119">Specify the name to reference the selection set.</span></span> <span data-ttu-id="f20f0-120">Er zijn geen beperkingen met betrekking tot welke tekens kunnen worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="f20f0-120">There are no restrictions as to what characters can be used.</span></span>

## <a name="remarks"></a><span data-ttu-id="f20f0-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="f20f0-121">Remarks</span></span>

<span data-ttu-id="f20f0-122">De naam die u hier opgeeft, wordt gebruikt in het- `SelectionSetName` element.</span><span class="sxs-lookup"><span data-stu-id="f20f0-122">The name specified here is used in the `SelectionSetName` element.</span></span> <span data-ttu-id="f20f0-123">De selectieset die kan worden gebruikt door een weer gave, door een definitie van een weer gave (weer gaven kunnen meerdere definities hebben) of wanneer een selectie voorwaarde wordt opgegeven.</span><span class="sxs-lookup"><span data-stu-id="f20f0-123">The selection set that can be used by a view, by a definition of a view (views can have multiple definitions), or when specifying a selection condition.</span></span> <span data-ttu-id="f20f0-124">Zie [sets van objecten definiëren](./defining-selection-sets.md)voor meer informatie over selectie sets.</span><span class="sxs-lookup"><span data-stu-id="f20f0-124">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="f20f0-125">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="f20f0-125">Example</span></span>

<span data-ttu-id="f20f0-126">In dit voor beeld ziet u een- `SelectionSet` element dat vier .net-typen definieert.</span><span class="sxs-lookup"><span data-stu-id="f20f0-126">This example shows a `SelectionSet` element that defines four .NET types.</span></span> <span data-ttu-id="f20f0-127">De naam van de selectieset is ' FileSystemTypes '.</span><span class="sxs-lookup"><span data-stu-id="f20f0-127">The name of the selection set is "FileSystemTypes".</span></span>

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

## <a name="see-also"></a><span data-ttu-id="f20f0-128">Zie ook</span><span class="sxs-lookup"><span data-stu-id="f20f0-128">See Also</span></span>

[<span data-ttu-id="f20f0-129">Selectiereeksen definiëren</span><span class="sxs-lookup"><span data-stu-id="f20f0-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="f20f0-130">Het element SelectionSet (opmaak)</span><span class="sxs-lookup"><span data-stu-id="f20f0-130">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="f20f0-131">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="f20f0-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
