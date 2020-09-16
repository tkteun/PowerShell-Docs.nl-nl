---
title: SelectionSets-element (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 718b08e02220f285ef215fdca727492fd4407466
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785197"
---
# <a name="selectionsets-element-format"></a><span data-ttu-id="e5f27-102">Het element SelectionSets (opmaak)</span><span class="sxs-lookup"><span data-stu-id="e5f27-102">SelectionSets Element (Format)</span></span>

<span data-ttu-id="e5f27-103">Hiermee worden de algemene sets van .NET-objecten gedefinieerd die kunnen worden gebruikt door alle weer gaven van het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="e5f27-103">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span> <span data-ttu-id="e5f27-104">De weer gaven en besturings elementen van het opmaak bestand kunnen verwijzen naar de volledige set met objecten door alleen de naam van de selectieset te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="e5f27-104">The views and controls of the formatting file can reference the complete set of objects by using only the name of the selection set.</span></span>

<span data-ttu-id="e5f27-105">SelectionSets element indeling van configuratie-element</span><span class="sxs-lookup"><span data-stu-id="e5f27-105">Configuration Element SelectionSets Element Format</span></span>

## <a name="syntax"></a><span data-ttu-id="e5f27-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="e5f27-106">Syntax</span></span>

```xml
<SelectionSets>
  <SelectionSet>...</SelectionSet>
</SelectionSets>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e5f27-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="e5f27-107">Attributes and Elements</span></span>

<span data-ttu-id="e5f27-108">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `SelectionSets` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="e5f27-108">The following sections describe the attributes, child elements, and parent element of the `SelectionSets` element.</span></span> <span data-ttu-id="e5f27-109">Elk onderliggend element definieert een set objecten waarnaar kan worden verwezen door de naam van de set.</span><span class="sxs-lookup"><span data-stu-id="e5f27-109">Each child element defines a set of objects that can be referenced by the name of the set.</span></span> <span data-ttu-id="e5f27-110">De volg orde van de onderliggende elementen is niet significant.</span><span class="sxs-lookup"><span data-stu-id="e5f27-110">The order of the child elements is not significant.</span></span>

### <a name="attributes"></a><span data-ttu-id="e5f27-111">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="e5f27-111">Attributes</span></span>

<span data-ttu-id="e5f27-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="e5f27-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e5f27-113">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="e5f27-113">Child Elements</span></span>

|<span data-ttu-id="e5f27-114">Element</span><span class="sxs-lookup"><span data-stu-id="e5f27-114">Element</span></span>|<span data-ttu-id="e5f27-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e5f27-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e5f27-116">Het element SelectionSet (opmaak)</span><span class="sxs-lookup"><span data-stu-id="e5f27-116">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="e5f27-117">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="e5f27-117">Required element.</span></span><br /><br /> <span data-ttu-id="e5f27-118">Hiermee wordt één set .NET-objecten gedefinieerd waarnaar kan worden verwezen met de naam van de set.</span><span class="sxs-lookup"><span data-stu-id="e5f27-118">Defines a single set of .NET objects that can be referenced by the name of the set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e5f27-119">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="e5f27-119">Parent Elements</span></span>

|<span data-ttu-id="e5f27-120">Element</span><span class="sxs-lookup"><span data-stu-id="e5f27-120">Element</span></span>|<span data-ttu-id="e5f27-121">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e5f27-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e5f27-122">Configuratie-element</span><span class="sxs-lookup"><span data-stu-id="e5f27-122">Configuration Element</span></span>](./configuration-element-format.md)|<span data-ttu-id="e5f27-123">Vertegenwoordigt het element op het hoogste niveau van een opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="e5f27-123">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e5f27-124">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="e5f27-124">Remarks</span></span>

<span data-ttu-id="e5f27-125">U kunt selectie sets gebruiken wanneer u een set verwante objecten hebt waarnaar u wilt verwijzen met behulp van één naam, zoals een set objecten die zijn gerelateerd aan overname.</span><span class="sxs-lookup"><span data-stu-id="e5f27-125">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="e5f27-126">Wanneer u uw weer gaven definieert, kunt u de set met objecten opgeven door de naam van de selectieset te gebruiken in plaats van alle objecten in elke weer gave te vermelden.</span><span class="sxs-lookup"><span data-stu-id="e5f27-126">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="e5f27-127">Algemene selectie sets worden opgegeven met hun naam bij het definiëren van de weer gaven van het opmaak bestand of de definities van de weer gaven.</span><span class="sxs-lookup"><span data-stu-id="e5f27-127">Common selection sets are specified by their name when defining the views of the formatting file or the definitions of the views.</span></span> <span data-ttu-id="e5f27-128">In deze gevallen geeft het `SelectionSetName` onderliggende element van de- `ViewSelectedBy` en- `EntrySelectedBy` elementen de set op die moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="e5f27-128">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` and `EntrySelectedBy` elements specifies the set to be used.</span></span> <span data-ttu-id="e5f27-129">Zie [sets van objecten definiëren](./defining-selection-sets.md)voor meer informatie over selectie sets.</span><span class="sxs-lookup"><span data-stu-id="e5f27-129">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e5f27-130">Zie ook</span><span class="sxs-lookup"><span data-stu-id="e5f27-130">See Also</span></span>

[<span data-ttu-id="e5f27-131">Configuratie-element</span><span class="sxs-lookup"><span data-stu-id="e5f27-131">Configuration Element</span></span>](./configuration-element-format.md)

[<span data-ttu-id="e5f27-132">Selectiereeksen definiëren</span><span class="sxs-lookup"><span data-stu-id="e5f27-132">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="e5f27-133">Het element SelectionSet (opmaak)</span><span class="sxs-lookup"><span data-stu-id="e5f27-133">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="e5f27-134">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="e5f27-134">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
