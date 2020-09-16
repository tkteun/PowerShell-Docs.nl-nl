---
title: SelectionCondition-element voor EntrySelectedBy voor EnumerableExpansion (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: d5858145e092dc962174a776889a4f62db366d71
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785333"
---
# <a name="selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="b7ae2-102">Het element SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (opmaak)</span><span class="sxs-lookup"><span data-stu-id="b7ae2-102">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="b7ae2-103">Hiermee definieert u de voor waarde die moet bestaan om de verzamelings objecten van deze definitie uit te breiden.</span><span class="sxs-lookup"><span data-stu-id="b7ae2-103">Defines the condition that must exist to expand the collection objects of this definition.</span></span>

<span data-ttu-id="b7ae2-104">Configuratie-element (indeling) DefaultSettings element (indeling) EnumerableExpansions element (indeling) EnumerableExpansion element (indeling) EntrySelectedBy element voor EnumerableExpansion (Format) SelectionCondition-element voor EntrySelectedBy voor EnumerableExpansion (indeling)</span><span class="sxs-lookup"><span data-stu-id="b7ae2-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b7ae2-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="b7ae2-105">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b7ae2-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="b7ae2-106">Attributes and Elements</span></span>

<span data-ttu-id="b7ae2-107">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `SelectionCondition` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="b7ae2-107">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span> <span data-ttu-id="b7ae2-108">U moet één `PropertyName` element of opgeven `ScriptBlock` .</span><span class="sxs-lookup"><span data-stu-id="b7ae2-108">You must specify a single `PropertyName` or `ScriptBlock` element.</span></span> <span data-ttu-id="b7ae2-109">De `SelectionSetName` `TypeName` elementen en zijn optioneel.</span><span class="sxs-lookup"><span data-stu-id="b7ae2-109">The `SelectionSetName` and `TypeName` elements are optional.</span></span> <span data-ttu-id="b7ae2-110">U kunt een van beide elementen opgeven.</span><span class="sxs-lookup"><span data-stu-id="b7ae2-110">You can specify one of either element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b7ae2-111">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="b7ae2-111">Attributes</span></span>

<span data-ttu-id="b7ae2-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="b7ae2-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b7ae2-113">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="b7ae2-113">Child Elements</span></span>

|<span data-ttu-id="b7ae2-114">Element</span><span class="sxs-lookup"><span data-stu-id="b7ae2-114">Element</span></span>|<span data-ttu-id="b7ae2-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="b7ae2-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b7ae2-116">Het element PropertyName voor SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (opmaak)</span><span class="sxs-lookup"><span data-stu-id="b7ae2-116">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="b7ae2-117">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="b7ae2-117">Optional element.</span></span><br /><br /> <span data-ttu-id="b7ae2-118">Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="b7ae2-118">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="b7ae2-119">Het element ScriptBlock voor SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (opmaak)</span><span class="sxs-lookup"><span data-stu-id="b7ae2-119">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="b7ae2-120">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="b7ae2-120">Optional element.</span></span><br /><br /> <span data-ttu-id="b7ae2-121">Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="b7ae2-121">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="b7ae2-122">Het element SelectionSetName voor SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (opmaak)</span><span class="sxs-lookup"><span data-stu-id="b7ae2-122">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="b7ae2-123">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="b7ae2-123">Optional element.</span></span><br /><br /> <span data-ttu-id="b7ae2-124">Hiermee geeft u de set .NET-typen op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="b7ae2-124">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="b7ae2-125">Het element TypeName voor SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (opmaak)</span><span class="sxs-lookup"><span data-stu-id="b7ae2-125">TypeName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="b7ae2-126">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="b7ae2-126">Optional element.</span></span><br /><br /> <span data-ttu-id="b7ae2-127">Hiermee geeft u een .NET-type op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="b7ae2-127">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b7ae2-128">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="b7ae2-128">Parent Elements</span></span>

|<span data-ttu-id="b7ae2-129">Element</span><span class="sxs-lookup"><span data-stu-id="b7ae2-129">Element</span></span>|<span data-ttu-id="b7ae2-130">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="b7ae2-130">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b7ae2-131">Het element EntrySelectedBy voor EnumerableExpansion (opmaak)</span><span class="sxs-lookup"><span data-stu-id="b7ae2-131">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="b7ae2-132">Hiermee definieert u welke .NET-verzamelings objecten worden uitgevouwen door deze definitie.</span><span class="sxs-lookup"><span data-stu-id="b7ae2-132">Defines which .NET collection objects are expanded by this definition.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b7ae2-133">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="b7ae2-133">Remarks</span></span>

<span data-ttu-id="b7ae2-134">Voor elke definitie moet ten minste één type naam, selectieset of selectie voorwaarde zijn gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="b7ae2-134">Each definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="b7ae2-135">Wanneer u een selectie voorwaarde definieert, gelden de volgende vereisten:</span><span class="sxs-lookup"><span data-stu-id="b7ae2-135">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="b7ae2-136">De selectie voorwaarde moet ten minste één eigenschaps naam of een script blok opgeven, maar kan niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="b7ae2-136">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="b7ae2-137">Met de selectie voorwaarde kan een wille keurig aantal .NET-typen of-selectie sets worden opgegeven, maar kan niet beide worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="b7ae2-137">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="b7ae2-138">Zie voor [waarden definiëren voor Diplaying-gegevens](./defining-conditions-for-displaying-data.md)voor meer informatie over het gebruik van selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="b7ae2-138">For more information about how to use selection conditions, see [Defining Conditions for Diplaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="b7ae2-139">Zie [brede weer gave](./creating-a-wide-view.md)voor meer informatie over andere onderdelen van een brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="b7ae2-139">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b7ae2-140">Zie ook</span><span class="sxs-lookup"><span data-stu-id="b7ae2-140">See Also</span></span>

[<span data-ttu-id="b7ae2-141">Voor waarden definiëren voor wanneer gegevens worden weer gegeven</span><span class="sxs-lookup"><span data-stu-id="b7ae2-141">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="b7ae2-142">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="b7ae2-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
