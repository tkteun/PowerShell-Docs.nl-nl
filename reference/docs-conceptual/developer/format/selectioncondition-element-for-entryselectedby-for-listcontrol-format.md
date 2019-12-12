---
title: SelectionCondition-element voor EntrySelectedBy voor ListControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7649d5d0-2b56-49b5-a670-dde46caca343
caps.latest.revision: 11
ms.openlocfilehash: 7150b29ad84dfb587215ee3e64c356adbd5a6305
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74417533"
---
# <a name="selectioncondition-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="881eb-102">Het element SelectionCondition voor EntrySelectedBy voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="881eb-102">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="881eb-103">Hiermee definieert u de voor waarde die moet bestaan om deze definitie van de lijst weergave te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="881eb-103">Defines the condition that must exist to use this definition of the list view.</span></span> <span data-ttu-id="881eb-104">Er is geen limiet voor het aantal selectie omstandigheden dat kan worden opgegeven voor een lijst definitie.</span><span class="sxs-lookup"><span data-stu-id="881eb-104">There is no limit to the number of selection conditions that can be specified for a list definition.</span></span>

<span data-ttu-id="881eb-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) bestand van ListControl element (indeling) item type-element (indeling) EntrySelectedBy element (Format) voor List entry (Format) SelectionCondition element voor EntrySelectedBy voor List entry (indeling)</span><span class="sxs-lookup"><span data-stu-id="881eb-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="881eb-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="881eb-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="881eb-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="881eb-107">Attributes and Elements</span></span>

<span data-ttu-id="881eb-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `SelectionCondition` beschreven.</span><span class="sxs-lookup"><span data-stu-id="881eb-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="881eb-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="881eb-109">Attributes</span></span>

<span data-ttu-id="881eb-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="881eb-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="881eb-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="881eb-111">Child Elements</span></span>

|<span data-ttu-id="881eb-112">Element</span><span class="sxs-lookup"><span data-stu-id="881eb-112">Element</span></span>|<span data-ttu-id="881eb-113">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="881eb-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="881eb-114">Het element PropertyName voor SelectionCondition voor EntrySelectedBy voor List entry (indeling)</span><span class="sxs-lookup"><span data-stu-id="881eb-114">PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="881eb-115">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="881eb-115">Optional element.</span></span><br /><br /> <span data-ttu-id="881eb-116">Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="881eb-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="881eb-117">Script block-element voor SelectionCondition voor EntrySelectedBy voor List entry (indeling)</span><span class="sxs-lookup"><span data-stu-id="881eb-117">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="881eb-118">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="881eb-118">Optional element.</span></span><br /><br /> <span data-ttu-id="881eb-119">Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="881eb-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="881eb-120">SelectionSetName-element voor SelectionCondition voor EntrySelectedBy voor List entry (indeling)</span><span class="sxs-lookup"><span data-stu-id="881eb-120">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)|<span data-ttu-id="881eb-121">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="881eb-121">Optional element.</span></span><br /><br /> <span data-ttu-id="881eb-122">Hiermee geeft u de set .NET-typen op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="881eb-122">Specifies the set of .NET types that trigger the condition.</span></span>|
|[<span data-ttu-id="881eb-123">TypeName-element voor SelectionCondition voor EntrySelectedBy voor List entry (indeling)</span><span class="sxs-lookup"><span data-stu-id="881eb-123">TypeName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="881eb-124">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="881eb-124">Optional element.</span></span><br /><br /> <span data-ttu-id="881eb-125">Hiermee geeft u een .NET-type op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="881eb-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="881eb-126">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="881eb-126">Parent Elements</span></span>

|<span data-ttu-id="881eb-127">Element</span><span class="sxs-lookup"><span data-stu-id="881eb-127">Element</span></span>|<span data-ttu-id="881eb-128">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="881eb-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="881eb-129">EntrySelectedBy-element voor TableRowEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="881eb-129">EntrySelectedBy Element for TableRowEntry (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="881eb-130">Hiermee definieert u de .NET-typen die gebruikmaken van deze tabel vermelding of de voor waarde die moet bestaan voor het gebruik van deze vermelding.</span><span class="sxs-lookup"><span data-stu-id="881eb-130">Defines the .NET types that use this table entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="881eb-131">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="881eb-131">Remarks</span></span>

<span data-ttu-id="881eb-132">lWhen u een selectie voorwaarde definieert, gelden de volgende vereisten:</span><span class="sxs-lookup"><span data-stu-id="881eb-132">lWhen you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="881eb-133">De selectie voorwaarde moet ten minste één eigenschaps naam of een script blok opgeven, maar kan niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="881eb-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="881eb-134">Met de selectie voorwaarde kan een wille keurig aantal .NET-typen of-selectie sets worden opgegeven, maar kan niet beide worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="881eb-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="881eb-135">Zie voor [waarden definiëren voor wanneer gegevens worden weer gegeven](./defining-conditions-for-displaying-data.md)voor meer informatie over het gebruik van selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="881eb-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="881eb-136">Zie [een lijst weergave maken](./creating-a-list-view.md)voor meer informatie over andere onderdelen van een lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="881eb-136">For more information about other components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="881eb-137">Zie ook</span><span class="sxs-lookup"><span data-stu-id="881eb-137">See Also</span></span>

[<span data-ttu-id="881eb-138">Een lijst weergave maken</span><span class="sxs-lookup"><span data-stu-id="881eb-138">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="881eb-139">Voor waarden definiëren voor wanneer gegevens worden weer gegeven</span><span class="sxs-lookup"><span data-stu-id="881eb-139">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="881eb-140">Element List entry (indeling)</span><span class="sxs-lookup"><span data-stu-id="881eb-140">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="881eb-141">SelectionSetName-element voor EntrySelectedBy voor List entry (indeling)</span><span class="sxs-lookup"><span data-stu-id="881eb-141">SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="881eb-142">TypeName-element voor EntrySelectedBy voor List entry (indeling)</span><span class="sxs-lookup"><span data-stu-id="881eb-142">TypeName Element for EntrySelectedBy for ListEntry (Format)</span></span>](/powershell/scripting/developer/format/typename-element-for-entryselectedby-for-listcontrol-format)

[<span data-ttu-id="881eb-143">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="881eb-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
