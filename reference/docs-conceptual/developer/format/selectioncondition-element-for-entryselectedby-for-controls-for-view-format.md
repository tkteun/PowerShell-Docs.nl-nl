---
title: SelectionCondition-element voor EntrySelectedBy voor besturings elementen voor weer gave (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 1c14b2638249bdbfe25f7a96e917d66ea10ed239
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787577"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-view-format"></a><span data-ttu-id="8955a-102">Het element SelectionCondition voor EntrySelectedBy voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="8955a-102">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>

<span data-ttu-id="8955a-103">Hiermee definieert u een voor waarde die moet bestaan voor het gebruik van de controle definitie.</span><span class="sxs-lookup"><span data-stu-id="8955a-103">Defines a condition that must exist for the control definition to be used.</span></span> <span data-ttu-id="8955a-104">Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.</span><span class="sxs-lookup"><span data-stu-id="8955a-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="8955a-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) Controls-element (Format) Control element (opmaak) voor besturings elementen voor de weer gave (indeling) CustomControl-element voor besturings elementen voor Controls (Format) CustomEntries element voor CustomControl voor besturings elementen voor weer gave (indeling) CustomEntry element voor CustomEntries voor besturings elementen voor de weer gave (Format) EntrySelectedBy-element voor CustomEntry voor besturings elementen voor de weer gave (Format) SelectionCondition-element voor EntrySelectedBy voor besturings elementen</span><span class="sxs-lookup"><span data-stu-id="8955a-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8955a-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="8955a-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8955a-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="8955a-107">Attributes and Elements</span></span>

<span data-ttu-id="8955a-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `SelectionCondition` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="8955a-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8955a-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="8955a-109">Attributes</span></span>

<span data-ttu-id="8955a-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="8955a-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8955a-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="8955a-111">Child Elements</span></span>

|<span data-ttu-id="8955a-112">Element</span><span class="sxs-lookup"><span data-stu-id="8955a-112">Element</span></span>|<span data-ttu-id="8955a-113">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="8955a-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8955a-114">Het element PropertyName voor SelectionCondition voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="8955a-114">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="8955a-115">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="8955a-115">Optional element.</span></span><br /><br /> <span data-ttu-id="8955a-116">Hiermee geeft u een .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="8955a-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="8955a-117">Het element ScriptBlock voor SelectionCondition voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="8955a-117">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="8955a-118">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="8955a-118">Optional element.</span></span><br /><br /> <span data-ttu-id="8955a-119">Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="8955a-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="8955a-120">Het element SelectionSetName voor SelectionCondition voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="8955a-120">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="8955a-121">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="8955a-121">Optional element.</span></span><br /><br /> <span data-ttu-id="8955a-122">Hiermee geeft u de set .NET-typen op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="8955a-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="8955a-123">Het element TypeName voor SelectionCondition voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="8955a-123">TypeName Element for SelectionCondition for Controls for View (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="8955a-124">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="8955a-124">Optional element.</span></span><br /><br /> <span data-ttu-id="8955a-125">Hiermee geeft u een .NET-type op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="8955a-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="8955a-126">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="8955a-126">Parent Elements</span></span>

|<span data-ttu-id="8955a-127">Element</span><span class="sxs-lookup"><span data-stu-id="8955a-127">Element</span></span>|<span data-ttu-id="8955a-128">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="8955a-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8955a-129">Het element EntrySelectedBy voor CustomEntry voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="8955a-129">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="8955a-130">Hiermee definieert u de .NET-typen die gebruikmaken van deze controle definitie of de voor waarde die voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="8955a-130">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8955a-131">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="8955a-131">Remarks</span></span>

<span data-ttu-id="8955a-132">Wanneer u een selectie voorwaarde definieert, gelden de volgende vereisten:</span><span class="sxs-lookup"><span data-stu-id="8955a-132">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="8955a-133">De selectie voorwaarde moet ten minste één eigenschaps naam of een script blok opgeven, maar kan niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="8955a-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="8955a-134">Met de selectie voorwaarde kan een wille keurig aantal .NET-typen of-selectie sets worden opgegeven, maar kan niet beide worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="8955a-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="8955a-135">Zie voor [waarden definiëren voor wanneer gegevens worden weer gegeven](./defining-conditions-for-displaying-data.md)voor meer informatie over het gebruik van selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="8955a-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8955a-136">Zie ook</span><span class="sxs-lookup"><span data-stu-id="8955a-136">See Also</span></span>

[<span data-ttu-id="8955a-137">Het element PropertyName voor SelectionCondition voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="8955a-137">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="8955a-138">Het element ScriptBlock voor SelectionCondition voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="8955a-138">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="8955a-139">Het element SelectionSetName voor SelectionCondition voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="8955a-139">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="8955a-140">Het element TypeName voor SelectionCondition voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="8955a-140">TypeName Element for SelectionCondition for Controls for View (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="8955a-141">Het element EntrySelectedBy voor CustomEntry voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="8955a-141">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="8955a-142">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="8955a-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
