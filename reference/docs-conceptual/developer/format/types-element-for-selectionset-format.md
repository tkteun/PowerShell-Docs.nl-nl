---
title: Type-element voor Selectieset (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 9978daefb3e97ab131774ca4dff633dde6b4dfbf
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87772515"
---
# <a name="types-element-for-selectionset-format"></a><span data-ttu-id="d0341-102">Het element Typen voor SelectionSet (opmaak)</span><span class="sxs-lookup"><span data-stu-id="d0341-102">Types Element for SelectionSet (Format)</span></span>

<span data-ttu-id="d0341-103">Hiermee definieert u de .NET-objecten die zich in de selectieset bevinden.</span><span class="sxs-lookup"><span data-stu-id="d0341-103">Defines the .NET objects that are in the selection set.</span></span>

<span data-ttu-id="d0341-104">Configuratie-element (indeling) SelectionSets element (Format) element van het type Selectionset (indeling) element (indeling)</span><span class="sxs-lookup"><span data-stu-id="d0341-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Types Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d0341-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="d0341-105">Syntax</span></span>

```xml
<Types>
  <TypeName>Nameof.NetType</TypeName>
</Types>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="d0341-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="d0341-106">Attributes and Elements</span></span>

<span data-ttu-id="d0341-107">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `Types` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="d0341-107">The following sections describe the attributes, child elements, and the parent element of the `Types` element.</span></span> <span data-ttu-id="d0341-108">Er moet ten minste één onderliggend element zijn, maar er is geen maximum limiet voor het aantal onderliggende elementen dat kan worden toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="d0341-108">There must be at least one child element, but there is no maximum limit to the number of child elements that can be added.</span></span>

### <a name="attributes"></a><span data-ttu-id="d0341-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="d0341-109">Attributes</span></span>

<span data-ttu-id="d0341-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="d0341-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d0341-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="d0341-111">Child Elements</span></span>

|<span data-ttu-id="d0341-112">Element</span><span class="sxs-lookup"><span data-stu-id="d0341-112">Element</span></span>|<span data-ttu-id="d0341-113">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="d0341-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d0341-114">TypeName-element van typen (indeling)</span><span class="sxs-lookup"><span data-stu-id="d0341-114">TypeName Element of Types (Format)</span></span>](./typename-element-for-types-format.md)|<span data-ttu-id="d0341-115">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="d0341-115">Required element.</span></span><br /><br /> <span data-ttu-id="d0341-116">Hiermee geeft u het .NET-object op dat deel uitmaakt van de selectieset.</span><span class="sxs-lookup"><span data-stu-id="d0341-116">Specifies the .NET object that belongs to the selection set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d0341-117">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="d0341-117">Parent Elements</span></span>

|<span data-ttu-id="d0341-118">Element</span><span class="sxs-lookup"><span data-stu-id="d0341-118">Element</span></span>|<span data-ttu-id="d0341-119">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="d0341-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d0341-120">Het element SelectionSet (opmaak)</span><span class="sxs-lookup"><span data-stu-id="d0341-120">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="d0341-121">Hiermee wordt een set .NET-objecten gedefinieerd waarnaar kan worden verwezen door de naam van de set.</span><span class="sxs-lookup"><span data-stu-id="d0341-121">Defines a set of .NET objects that can be referenced by the name of the set.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d0341-122">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="d0341-122">Remarks</span></span>

<span data-ttu-id="d0341-123">De objecten die door dit element worden gedefinieerd, vormen een selectie reeks die kan worden gebruikt door een weer gave, op basis van een definitie van een weer gave (weer gaven kunnen meerdere definities hebben) of wanneer een selectie voorwaarde wordt opgegeven.</span><span class="sxs-lookup"><span data-stu-id="d0341-123">The objects defined by this element make up a selection set that can be used by a view, by a definition of a view (views can have multiple definitions), or when specifying a selection condition.</span></span>  <span data-ttu-id="d0341-124">Zie [sets van objecten definiëren](./defining-selection-sets.md)voor meer informatie over selectie sets.</span><span class="sxs-lookup"><span data-stu-id="d0341-124">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="d0341-125">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="d0341-125">Example</span></span>

<span data-ttu-id="d0341-126">In dit voor beeld ziet u een- `SelectionSet` element dat vier .net-typen definieert.</span><span class="sxs-lookup"><span data-stu-id="d0341-126">This example shows a `SelectionSet` element that defines four .NET types.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d0341-127">Zie ook</span><span class="sxs-lookup"><span data-stu-id="d0341-127">See Also</span></span>

[<span data-ttu-id="d0341-128">Sets van objecten definiëren</span><span class="sxs-lookup"><span data-stu-id="d0341-128">Defining Sets of Objects</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="d0341-129">Het element SelectionSet (opmaak)</span><span class="sxs-lookup"><span data-stu-id="d0341-129">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="d0341-130">TypeName-element van typen (indeling)</span><span class="sxs-lookup"><span data-stu-id="d0341-130">TypeName Element of Types (Format)</span></span>](./typename-element-for-types-format.md)

[<span data-ttu-id="d0341-131">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="d0341-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
