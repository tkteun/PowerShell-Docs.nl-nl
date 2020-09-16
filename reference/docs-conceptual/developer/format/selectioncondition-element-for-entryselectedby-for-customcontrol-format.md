---
title: SelectionCondition-element voor EntrySelectedBy voor CustomControl (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 52858dba5c7a5222b5410835f3374546ce8b88a2
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785350"
---
# <a name="selectioncondition-element-for-entryselectedby-for-customcontrol-format"></a><span data-ttu-id="7400d-102">Het element SelectionCondition voor EntrySelectedBy voor CustomControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7400d-102">SelectionCondition Element for EntrySelectedBy for CustomControl (Format)</span></span>

<span data-ttu-id="7400d-103">Hiermee definieert u een voor waarde die moet bestaan voor het gebruik van een definitie van een besturings element.</span><span class="sxs-lookup"><span data-stu-id="7400d-103">Defines a condition that must exist for a control definition to be used.</span></span> <span data-ttu-id="7400d-104">Dit element wordt gebruikt bij het definiëren van een aangepaste beheer weergave.</span><span class="sxs-lookup"><span data-stu-id="7400d-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="7400d-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element van weer gave (Format) CustomControl element voor weer gave (Format) CustomEntries element voor CustomControl voor weer gave (Format) CustomEntry-element voor CustomEntries voor CustomControl voor weer gave (Format) CustomItem-element voor CustomEntry voor het object CustomControl voor weer gave (Format) EntrySelectedBy voor CustomEntry</span><span class="sxs-lookup"><span data-stu-id="7400d-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) EntrySelectedBy Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7400d-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="7400d-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7400d-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="7400d-107">Attributes and Elements</span></span>

<span data-ttu-id="7400d-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `SelectionCondition` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="7400d-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7400d-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="7400d-109">Attributes</span></span>

<span data-ttu-id="7400d-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="7400d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7400d-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="7400d-111">Child Elements</span></span>

|<span data-ttu-id="7400d-112">Element</span><span class="sxs-lookup"><span data-stu-id="7400d-112">Element</span></span>|<span data-ttu-id="7400d-113">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="7400d-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7400d-114">Het element PropertyName voor SelectionCondition voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7400d-114">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="7400d-115">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="7400d-115">Optional element.</span></span><br /><br /> <span data-ttu-id="7400d-116">Hiermee geeft u een .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="7400d-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="7400d-117">Het element ScriptBlock voor SelectionCondition voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7400d-117">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="7400d-118">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="7400d-118">Optional element.</span></span><br /><br /> <span data-ttu-id="7400d-119">Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="7400d-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="7400d-120">SelectionSetName-element voor SelectionCondition voor aangepast besturings element voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="7400d-120">SelectionSetName Element for SelectionCondition for Custom Control for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="7400d-121">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="7400d-121">Optional element.</span></span><br /><br /> <span data-ttu-id="7400d-122">Hiermee geeft u de set .NET-typen op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="7400d-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="7400d-123">Het element TypeName voor SelectionCondition voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7400d-123">TypeName Element for SelectionCondition for CustomControl for View  (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="7400d-124">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="7400d-124">Optional element.</span></span><br /><br /> <span data-ttu-id="7400d-125">Hiermee geeft u een .NET-type op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="7400d-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="7400d-126">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="7400d-126">Parent Elements</span></span>

|<span data-ttu-id="7400d-127">Element</span><span class="sxs-lookup"><span data-stu-id="7400d-127">Element</span></span>|<span data-ttu-id="7400d-128">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="7400d-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7400d-129">Het element EntrySelectedBy voor CustomEntry voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7400d-129">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="7400d-130">Hiermee definieert u de .NET-typen die gebruikmaken van deze controle definitie of de voor waarde die voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="7400d-130">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7400d-131">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="7400d-131">Remarks</span></span>

<span data-ttu-id="7400d-132">Wanneer u een selectie voorwaarde definieert, gelden de volgende vereisten:</span><span class="sxs-lookup"><span data-stu-id="7400d-132">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="7400d-133">De selectie voorwaarde moet ten minste één eigenschaps naam of een script blok opgeven, maar kan niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="7400d-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="7400d-134">Met de selectie voorwaarde kan een wille keurig aantal .NET-typen of-selectie sets worden opgegeven, maar kan niet beide worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="7400d-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="7400d-135">Zie voor [waarden definiëren voor wanneer gegevens worden weer gegeven](./defining-conditions-for-displaying-data.md)voor meer informatie over het gebruik van selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="7400d-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7400d-136">Zie ook</span><span class="sxs-lookup"><span data-stu-id="7400d-136">See Also</span></span>

[<span data-ttu-id="7400d-137">Het element PropertyName voor SelectionCondition voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7400d-137">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="7400d-138">Het element ScriptBlock voor SelectionCondition voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7400d-138">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="7400d-139">SelectionSetName-element voor SelectionCondition voor aangepast besturings element voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="7400d-139">SelectionSetName Element for SelectionCondition for Custom Control for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="7400d-140">Het element TypeName voor SelectionCondition voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7400d-140">TypeName Element for SelectionCondition for CustomControl for View  (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="7400d-141">Het element EntrySelectedBy voor CustomEntry voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7400d-141">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="7400d-142">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="7400d-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
