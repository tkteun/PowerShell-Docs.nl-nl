---
title: SelectionCondition-element voor EntrySelectedBy voor CustomControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 231e9c6d-09ec-4e68-80ee-0c8f7fe1b9f5
caps.latest.revision: 7
ms.openlocfilehash: 49e2c0cf09dfa55b535effcd431e980daf12fac3
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72358889"
---
# <a name="selectioncondition-element-for-entryselectedby-for-customcontrol-format"></a><span data-ttu-id="67dba-102">Het element SelectionCondition voor EntrySelectedBy voor CustomControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="67dba-102">SelectionCondition Element for EntrySelectedBy for CustomControl (Format)</span></span>

<span data-ttu-id="67dba-103">Hiermee definieert u een voor waarde die moet bestaan voor het gebruik van een definitie van een besturings element.</span><span class="sxs-lookup"><span data-stu-id="67dba-103">Defines a condition that must exist for a control definition to be used.</span></span> <span data-ttu-id="67dba-104">Dit element wordt gebruikt bij het definiëren van een aangepaste beheer weergave.</span><span class="sxs-lookup"><span data-stu-id="67dba-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="67dba-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) CustomControl-element voor weer gave (indeling) CustomEntries element voor CustomControl voor weer gave (Format) CustomEntry-element voor CustomEntries voor CustomControl voor weer gave ( Format) CustomItem-element voor CustomEntry voor CustomControl voor weer gave (Format) EntrySelectedBy-element voor CustomEntry voor CustomControl voor weer gave (Format) SelectionCondition element voor EntrySelectedBy voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="67dba-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) EntrySelectedBy Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="67dba-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="67dba-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="67dba-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="67dba-107">Attributes and Elements</span></span>

<span data-ttu-id="67dba-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `SelectionCondition` beschreven.</span><span class="sxs-lookup"><span data-stu-id="67dba-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="67dba-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="67dba-109">Attributes</span></span>

<span data-ttu-id="67dba-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="67dba-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="67dba-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="67dba-111">Child Elements</span></span>

|<span data-ttu-id="67dba-112">Element</span><span class="sxs-lookup"><span data-stu-id="67dba-112">Element</span></span>|<span data-ttu-id="67dba-113">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="67dba-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="67dba-114">Het element PropertyName voor SelectionCondition voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="67dba-114">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="67dba-115">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="67dba-115">Optional element.</span></span><br /><br /> <span data-ttu-id="67dba-116">Hiermee geeft u een .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="67dba-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="67dba-117">Script block-element voor SelectionCondition voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="67dba-117">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="67dba-118">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="67dba-118">Optional element.</span></span><br /><br /> <span data-ttu-id="67dba-119">Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="67dba-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="67dba-120">SelectionSetName-element voor SelectionCondition voor aangepast besturings element voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="67dba-120">SelectionSetName Element for SelectionCondition for Custom Control for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="67dba-121">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="67dba-121">Optional element.</span></span><br /><br /> <span data-ttu-id="67dba-122">Hiermee geeft u de set .NET-typen op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="67dba-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="67dba-123">TypeName-element voor SelectionCondition voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="67dba-123">TypeName Element for SelectionCondition for CustomControl for View  (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="67dba-124">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="67dba-124">Optional element.</span></span><br /><br /> <span data-ttu-id="67dba-125">Hiermee geeft u een .NET-type op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="67dba-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="67dba-126">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="67dba-126">Parent Elements</span></span>

|<span data-ttu-id="67dba-127">Element</span><span class="sxs-lookup"><span data-stu-id="67dba-127">Element</span></span>|<span data-ttu-id="67dba-128">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="67dba-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="67dba-129">EntrySelectedBy-element voor CustomEntry voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="67dba-129">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="67dba-130">Hiermee definieert u de .NET-typen die gebruikmaken van deze controle definitie of de voor waarde die voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="67dba-130">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="67dba-131">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="67dba-131">Remarks</span></span>

<span data-ttu-id="67dba-132">Wanneer u een selectie voorwaarde definieert, gelden de volgende vereisten:</span><span class="sxs-lookup"><span data-stu-id="67dba-132">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="67dba-133">De selectie voorwaarde moet ten minste één eigenschaps naam of een script blok opgeven, maar kan niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="67dba-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="67dba-134">Met de selectie voorwaarde kan een wille keurig aantal .NET-typen of-selectie sets worden opgegeven, maar kan niet beide worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="67dba-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="67dba-135">Zie voor [waarden definiëren voor wanneer gegevens worden weer gegeven](./defining-conditions-for-displaying-data.md)voor meer informatie over het gebruik van selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="67dba-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="67dba-136">Zie ook</span><span class="sxs-lookup"><span data-stu-id="67dba-136">See Also</span></span>

[<span data-ttu-id="67dba-137">Het element PropertyName voor SelectionCondition voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="67dba-137">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="67dba-138">Script block-element voor SelectionCondition voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="67dba-138">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="67dba-139">SelectionSetName-element voor SelectionCondition voor aangepast besturings element voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="67dba-139">SelectionSetName Element for SelectionCondition for Custom Control for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="67dba-140">TypeName-element voor SelectionCondition voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="67dba-140">TypeName Element for SelectionCondition for CustomControl for View  (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="67dba-141">EntrySelectedBy-element voor CustomEntry voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="67dba-141">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="67dba-142">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="67dba-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
