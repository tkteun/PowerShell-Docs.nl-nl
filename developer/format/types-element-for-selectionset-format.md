---
title: Element van het type voor SelectionSet (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4606fec0-ff31-4d36-af68-227405335ec3
caps.latest.revision: 15
ms.openlocfilehash: 0427367efa2c8a7e352d718706d1341a0c8e3621
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851273"
---
# <a name="types-element-for-selectionset-format"></a><span data-ttu-id="9433e-102">Het element Typen voor SelectionSet (opmaak)</span><span class="sxs-lookup"><span data-stu-id="9433e-102">Types Element for SelectionSet (Format)</span></span>

<span data-ttu-id="9433e-103">Hiermee definieert u de .NET-objecten die in de selectie.</span><span class="sxs-lookup"><span data-stu-id="9433e-103">Defines the .NET objects that are in the selection set.</span></span>

<span data-ttu-id="9433e-104">Configuratie Element (indeling) SelectionSets-Element (indeling) SelectionSet-Element (indeling) van het type Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="9433e-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Types Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9433e-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="9433e-105">Syntax</span></span>

```xml
<Types>
  <TypeName>Nameof.NetType</TypeName>
</Types>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="9433e-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="9433e-106">Attributes and Elements</span></span>

<span data-ttu-id="9433e-107">De volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van de `Types` element.</span><span class="sxs-lookup"><span data-stu-id="9433e-107">The following sections describe the attributes, child elements, and the parent element of the `Types` element.</span></span> <span data-ttu-id="9433e-108">Er moet ten minste één onderliggend element, maar er is geen maximale limiet voor het aantal onderliggende elementen die kunnen worden toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="9433e-108">There must be at least one child element, but there is no maximum limit to the number of child elements that can be added.</span></span>

### <a name="attributes"></a><span data-ttu-id="9433e-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="9433e-109">Attributes</span></span>

<span data-ttu-id="9433e-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="9433e-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9433e-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="9433e-111">Child Elements</span></span>

|<span data-ttu-id="9433e-112">Element</span><span class="sxs-lookup"><span data-stu-id="9433e-112">Element</span></span>|<span data-ttu-id="9433e-113">Description</span><span class="sxs-lookup"><span data-stu-id="9433e-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9433e-114">TypeName Element van de typen (indeling)</span><span class="sxs-lookup"><span data-stu-id="9433e-114">TypeName Element of Types (Format)</span></span>](./typename-element-for-types-format.md)|<span data-ttu-id="9433e-115">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="9433e-115">Required element.</span></span><br /><br /> <span data-ttu-id="9433e-116">Hiermee geeft u de .NET-object die deel uitmaakt van de selectieset.</span><span class="sxs-lookup"><span data-stu-id="9433e-116">Specifies the .NET object that belongs to the selection set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="9433e-117">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="9433e-117">Parent Elements</span></span>

|<span data-ttu-id="9433e-118">Element</span><span class="sxs-lookup"><span data-stu-id="9433e-118">Element</span></span>|<span data-ttu-id="9433e-119">Description</span><span class="sxs-lookup"><span data-stu-id="9433e-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9433e-120">SelectionSet-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="9433e-120">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="9433e-121">Hiermee definieert een set van .NET-objecten die kan worden verwezen door de naam van de set.</span><span class="sxs-lookup"><span data-stu-id="9433e-121">Defines a set of .NET objects that can be referenced by the name of the set.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9433e-122">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="9433e-122">Remarks</span></span>

<span data-ttu-id="9433e-123">De objecten die zijn gedefinieerd door dit element gezamenlijk een selectie instellen die door een weergave kan worden gebruikt door een definitie van een weergave (weergaven kunnen meerdere definities hebben), of wanneer een selectievoorwaarde op te geven.</span><span class="sxs-lookup"><span data-stu-id="9433e-123">The objects defined by this element make up a selection set that can be used by a view, by a definition of a view (views can have multiple definitions), or when specifying a selection condition.</span></span>  <span data-ttu-id="9433e-124">Zie voor meer informatie over selectiesets [ingesteld definiëren van objecten](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="9433e-124">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="9433e-125">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="9433e-125">Example</span></span>

<span data-ttu-id="9433e-126">In dit voorbeeld ziet u een `SelectionSet` element waarin vier .NET-typen.</span><span class="sxs-lookup"><span data-stu-id="9433e-126">This example shows a `SelectionSet` element that defines four .NET types.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="9433e-127">Zie ook</span><span class="sxs-lookup"><span data-stu-id="9433e-127">See Also</span></span>

[<span data-ttu-id="9433e-128">Sets van objecten te definiëren</span><span class="sxs-lookup"><span data-stu-id="9433e-128">Defining Sets of Objects</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="9433e-129">SelectionSet-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="9433e-129">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="9433e-130">TypeName Element van de typen (indeling)</span><span class="sxs-lookup"><span data-stu-id="9433e-130">TypeName Element of Types (Format)</span></span>](./typename-element-for-types-format.md)

[<span data-ttu-id="9433e-131">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="9433e-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
