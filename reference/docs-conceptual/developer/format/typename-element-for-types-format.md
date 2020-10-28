---
ms.date: 09/13/2016
ms.topic: reference
title: Het element TypeName voor Typen (opmaak)
description: Het element TypeName voor Typen (opmaak)
ms.openlocfilehash: c656b8e7e5877b72ff2164e5b417857273cada61
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92664615"
---
# <a name="typename-element-for-types-format"></a><span data-ttu-id="32f2e-103">Het element TypeName voor Typen (opmaak)</span><span class="sxs-lookup"><span data-stu-id="32f2e-103">TypeName Element for Types (Format)</span></span>

<span data-ttu-id="32f2e-104">Hiermee geeft u het .NET-type op van een object dat tot de selectieset behoort.</span><span class="sxs-lookup"><span data-stu-id="32f2e-104">Specifies the .NET type of an object that belongs to the selection set.</span></span>

<span data-ttu-id="32f2e-105">Configuratie-element (indeling) SelectionSets element (Format) element van het type Selectionset (indeling)-element (Format) elementen van het type TypeName-element van typen (indeling)</span><span class="sxs-lookup"><span data-stu-id="32f2e-105">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Types Element (Format) TypeName Element of Types (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="32f2e-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="32f2e-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="32f2e-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="32f2e-107">Attributes and Elements</span></span>

<span data-ttu-id="32f2e-108">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `TypeName` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="32f2e-108">The following sections describe the attributes, child elements, and the parent element of the `TypeName` element.</span></span> <span data-ttu-id="32f2e-109">Ten minste één `TypeName` element moet worden opgenomen in de selectieset.</span><span class="sxs-lookup"><span data-stu-id="32f2e-109">At least one `TypeName` element must be included in the selection set.</span></span>

### <a name="attributes"></a><span data-ttu-id="32f2e-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="32f2e-110">Attributes</span></span>

<span data-ttu-id="32f2e-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="32f2e-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="32f2e-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="32f2e-112">Child Elements</span></span>

<span data-ttu-id="32f2e-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="32f2e-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="32f2e-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="32f2e-114">Parent Elements</span></span>

|<span data-ttu-id="32f2e-115">Element</span><span class="sxs-lookup"><span data-stu-id="32f2e-115">Element</span></span>|<span data-ttu-id="32f2e-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="32f2e-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="32f2e-117">Type-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="32f2e-117">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)|<span data-ttu-id="32f2e-118">Hiermee definieert u de .NET-objecten die zich in de selectieset bevinden.</span><span class="sxs-lookup"><span data-stu-id="32f2e-118">Defines the .NET objects that are in the selection set.</span></span>|

## <a name="text-value"></a><span data-ttu-id="32f2e-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="32f2e-119">Text Value</span></span>

<span data-ttu-id="32f2e-120">Geef de volledig gekwalificeerde naam voor het .NET-type op.</span><span class="sxs-lookup"><span data-stu-id="32f2e-120">Specify the fully qualified name for the .NET type.</span></span>

## <a name="remarks"></a><span data-ttu-id="32f2e-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="32f2e-121">Remarks</span></span>

<span data-ttu-id="32f2e-122">U kunt selectie sets gebruiken wanneer u een set verwante objecten hebt waarnaar u wilt verwijzen met behulp van één naam, zoals een set objecten die zijn gerelateerd aan overname.</span><span class="sxs-lookup"><span data-stu-id="32f2e-122">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="32f2e-123">Wanneer u uw weer gaven definieert, kunt u de set met objecten opgeven door de naam van de selectieset te gebruiken in plaats van alle objecten in elke weer gave te vermelden.</span><span class="sxs-lookup"><span data-stu-id="32f2e-123">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="32f2e-124">Algemene selectie sets worden opgegeven met hun naam bij het definiëren van de weer gaven van het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="32f2e-124">Common selection sets are specified by their name when defining the views of the formatting file.</span></span> <span data-ttu-id="32f2e-125">In deze gevallen `SelectionSetName` specificeert het onderliggende element van het `ViewSelectedBy` element voor de weer gave de set.</span><span class="sxs-lookup"><span data-stu-id="32f2e-125">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` element for the view specifies the set.</span></span> <span data-ttu-id="32f2e-126">Met verschillende vermeldingen in een weer gave kunt u echter ook een selectie reeks opgeven die alleen van toepassing is op die vermelding van de weer gave.</span><span class="sxs-lookup"><span data-stu-id="32f2e-126">However, different entries of a view can also specify a selection set that applies to only that entry of the view.</span></span> <span data-ttu-id="32f2e-127">Zie [sets van objecten definiëren](./defining-selection-sets.md)voor meer informatie over selectie sets.</span><span class="sxs-lookup"><span data-stu-id="32f2e-127">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="32f2e-128">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="32f2e-128">Example</span></span>

<span data-ttu-id="32f2e-129">In het volgende voor beeld ziet u een- `SelectionSet` element dat vier .net-typen definieert.</span><span class="sxs-lookup"><span data-stu-id="32f2e-129">The following example shows a `SelectionSet` element that defines four .NET types.</span></span>

```
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

## <a name="see-also"></a><span data-ttu-id="32f2e-130">Zie ook</span><span class="sxs-lookup"><span data-stu-id="32f2e-130">See Also</span></span>

[<span data-ttu-id="32f2e-131">Selectiereeksen definiëren</span><span class="sxs-lookup"><span data-stu-id="32f2e-131">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="32f2e-132">Het element SelectionSet (opmaak)</span><span class="sxs-lookup"><span data-stu-id="32f2e-132">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="32f2e-133">Het element SelectionSets (opmaak)</span><span class="sxs-lookup"><span data-stu-id="32f2e-133">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="32f2e-134">Type-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="32f2e-134">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="32f2e-135">Een Windows PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="32f2e-135">Writing a Windows PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
