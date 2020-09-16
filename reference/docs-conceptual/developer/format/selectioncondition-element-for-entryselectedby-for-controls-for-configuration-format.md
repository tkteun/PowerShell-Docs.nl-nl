---
title: SelectionCondition-element voor EntrySelectedBy voor besturings elementen voor configuratie (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 748aa1aa0ba603a44334d9401e9e2c0e68f14e03
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783412"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format"></a><span data-ttu-id="8c2a5-102">Het element SelectionCondition voor EntrySelectedBy voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="8c2a5-102">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

<span data-ttu-id="8c2a5-103">Hiermee definieert u een voor waarde die moet bestaan voor het gebruik van een algemene definitie van het besturings element.</span><span class="sxs-lookup"><span data-stu-id="8c2a5-103">Defines a condition that must exist for a common control definition to be used.</span></span> <span data-ttu-id="8c2a5-104">Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="8c2a5-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="8c2a5-105">Configuratie-element (Format) Controls element van configuratie (indeling) Control element voor besturings elementen voor configuratie (Format) CustomControl-element voor besturings element voor configuratie (indeling) CustomEntries element voor CustomControl voor besturings elementen voor configuratie (Format) CustomEntry-element voor CustomControl voor besturings elementen voor configuratie (Format) SelectionCondition-element voor EntrySelectedBy voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="8c2a5-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Controls for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8c2a5-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="8c2a5-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8c2a5-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="8c2a5-107">Attributes and Elements</span></span>

<span data-ttu-id="8c2a5-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `SelectionCondition` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="8c2a5-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8c2a5-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="8c2a5-109">Attributes</span></span>

<span data-ttu-id="8c2a5-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="8c2a5-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8c2a5-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="8c2a5-111">Child Elements</span></span>

|<span data-ttu-id="8c2a5-112">Element</span><span class="sxs-lookup"><span data-stu-id="8c2a5-112">Element</span></span>|<span data-ttu-id="8c2a5-113">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="8c2a5-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8c2a5-114">Het element PropertyName voor SelectionCondition voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="8c2a5-114">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="8c2a5-115">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="8c2a5-115">Optional element.</span></span><br /><br /> <span data-ttu-id="8c2a5-116">Hiermee geeft u een .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="8c2a5-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="8c2a5-117">Het element ScriptBlock voor SelectionCondition voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="8c2a5-117">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="8c2a5-118">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="8c2a5-118">Optional element.</span></span><br /><br /> <span data-ttu-id="8c2a5-119">Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="8c2a5-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="8c2a5-120">Het element SelectionSetName voor SelectionCondition voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="8c2a5-120">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="8c2a5-121">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="8c2a5-121">Optional element.</span></span><br /><br /> <span data-ttu-id="8c2a5-122">Hiermee geeft u de set .NET-typen op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="8c2a5-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="8c2a5-123">Het element TypeName voor SelectionCondition voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="8c2a5-123">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="8c2a5-124">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="8c2a5-124">Optional element.</span></span><br /><br /> <span data-ttu-id="8c2a5-125">Hiermee geeft u een .NET-type op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="8c2a5-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="8c2a5-126">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="8c2a5-126">Parent Elements</span></span>

|<span data-ttu-id="8c2a5-127">Element</span><span class="sxs-lookup"><span data-stu-id="8c2a5-127">Element</span></span>|<span data-ttu-id="8c2a5-128">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="8c2a5-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8c2a5-129">Het element EntrySelectedBy voor CustomEntry voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="8c2a5-129">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="8c2a5-130">Hiermee worden de .NET-typen gedefinieerd die dit item van de algemene besturings definitie gebruiken.</span><span class="sxs-lookup"><span data-stu-id="8c2a5-130">Defines the .NET types that use this entry of the common control definition.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8c2a5-131">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="8c2a5-131">Remarks</span></span>

<span data-ttu-id="8c2a5-132">De volgende richt lijnen moeten worden gevolgd bij het definiëren van een selectie voorwaarde:</span><span class="sxs-lookup"><span data-stu-id="8c2a5-132">The following guidelines must be followed when defining a selection condition:</span></span>

- <span data-ttu-id="8c2a5-133">De selectie voorwaarde moet ten minste één eigenschaps naam of een script blok opgeven, maar kan niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="8c2a5-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="8c2a5-134">Met de selectie voorwaarde kan een wille keurig aantal .NET-typen of-selectie sets worden opgegeven, maar kan niet beide worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="8c2a5-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="8c2a5-135">Zie voor [waarden definiëren voor wanneer gegevens worden weer gegeven](./defining-conditions-for-displaying-data.md)voor meer informatie over hoe selectie omstandigheden kunnen worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="8c2a5-135">For more information about how selection conditions can be used, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8c2a5-136">Zie ook</span><span class="sxs-lookup"><span data-stu-id="8c2a5-136">See Also</span></span>

[<span data-ttu-id="8c2a5-137">Het element PropertyName voor SelectionCondition voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="8c2a5-137">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="8c2a5-138">Het element ScriptBlock voor SelectionCondition voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="8c2a5-138">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="8c2a5-139">Het element SelectionSetName voor SelectionCondition voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="8c2a5-139">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="8c2a5-140">Het element TypeName voor SelectionCondition voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="8c2a5-140">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="8c2a5-141">Het element EntrySelectedBy voor CustomEntry voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="8c2a5-141">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="8c2a5-142">Een Windows Power shell-indeling en-type bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="8c2a5-142">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
