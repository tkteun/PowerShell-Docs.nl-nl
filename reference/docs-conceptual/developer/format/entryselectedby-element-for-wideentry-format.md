---
ms.date: 09/13/2016
ms.topic: reference
title: Het element EntrySelectedBy voor WideEntry (opmaak)
description: Het element EntrySelectedBy voor WideEntry (opmaak)
ms.openlocfilehash: 246a1967300ab0551f376c4799deac275068308c
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660248"
---
# <a name="entryselectedby-element-for-wideentry-format"></a><span data-ttu-id="36bb7-103">Het element EntrySelectedBy voor WideEntry (opmaak)</span><span class="sxs-lookup"><span data-stu-id="36bb7-103">EntrySelectedBy Element for WideEntry (Format)</span></span>

<span data-ttu-id="36bb7-104">Hiermee definieert u de .NET-typen die gebruikmaken van deze definitie van de brede weer gave of de voor waarde die voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="36bb7-104">Defines the .NET types that use this definition of the wide view or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="36bb7-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) WideControl element (indeling) WideEntries element (indeling) WideEntry element (indeling) EntrySelectedBy-element voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="36bb7-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="36bb7-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="36bb7-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="36bb7-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="36bb7-107">Attributes and Elements</span></span>

<span data-ttu-id="36bb7-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `EntrySelectedBy` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="36bb7-108">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="36bb7-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="36bb7-109">Attributes</span></span>

<span data-ttu-id="36bb7-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="36bb7-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="36bb7-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="36bb7-111">Child Elements</span></span>

|<span data-ttu-id="36bb7-112">Element</span><span class="sxs-lookup"><span data-stu-id="36bb7-112">Element</span></span>|<span data-ttu-id="36bb7-113">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="36bb7-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="36bb7-114">SelectionCondition-element voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="36bb7-114">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="36bb7-115">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="36bb7-115">Optional element.</span></span><br /><br /> <span data-ttu-id="36bb7-116">Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van deze brede weergave definitie.</span><span class="sxs-lookup"><span data-stu-id="36bb7-116">Defines the condition that must exist for this wide view definition to be used.</span></span>|
|[<span data-ttu-id="36bb7-117">SelectionSetName-element voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="36bb7-117">SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="36bb7-118">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="36bb7-118">Optional element.</span></span><br /><br /> <span data-ttu-id="36bb7-119">Hiermee geeft u een set .NET-typen op die gebruikmaken van deze brede weergave definitie.</span><span class="sxs-lookup"><span data-stu-id="36bb7-119">Specifies a set of .NET types that use this wide view definition.</span></span>|
|[<span data-ttu-id="36bb7-120">Het element TypeName voor EntrySelectedBy voor WideEntry (opmaak)</span><span class="sxs-lookup"><span data-stu-id="36bb7-120">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="36bb7-121">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="36bb7-121">Optional element.</span></span><br /><br /> <span data-ttu-id="36bb7-122">Hiermee geeft u een .NET-type op dat gebruikmaakt van deze brede weergave definitie.</span><span class="sxs-lookup"><span data-stu-id="36bb7-122">Specifies a .NET type that uses this wide view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="36bb7-123">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="36bb7-123">Parent Elements</span></span>

|<span data-ttu-id="36bb7-124">Element</span><span class="sxs-lookup"><span data-stu-id="36bb7-124">Element</span></span>|<span data-ttu-id="36bb7-125">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="36bb7-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="36bb7-126">WideEntry-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="36bb7-126">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="36bb7-127">Biedt een definitie van de brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="36bb7-127">Provides a definition of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="36bb7-128">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="36bb7-128">Remarks</span></span>

<span data-ttu-id="36bb7-129">U moet ten minste één type, selectieset of selectie voorwaarde opgeven voor een brede weergave definitie.</span><span class="sxs-lookup"><span data-stu-id="36bb7-129">You must specify at least one type, selection set, or selection condition for a wide view definition.</span></span> <span data-ttu-id="36bb7-130">Er is geen maximum limiet voor het aantal onderliggende elementen dat u kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="36bb7-130">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="36bb7-131">Selectie voorwaarden worden gebruikt voor het definiëren van een voor waarde die voor de definitie moet bestaan, zoals wanneer een object een specifieke eigenschap heeft of een bepaalde eigenschaps waarde of script waarde resulteert in `true` .</span><span class="sxs-lookup"><span data-stu-id="36bb7-131">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script value evaluates to `true`.</span></span> <span data-ttu-id="36bb7-132">Zie voor [waarden definiëren voor het weer geven van gegevens](./defining-conditions-for-displaying-data.md)voor meer informatie over selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="36bb7-132">For more information about selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="36bb7-133">Zie [een brede weer gave maken](./creating-a-wide-view.md)voor meer informatie over andere onderdelen van een brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="36bb7-133">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="36bb7-134">Zie ook</span><span class="sxs-lookup"><span data-stu-id="36bb7-134">See Also</span></span>

[<span data-ttu-id="36bb7-135">WideEntry-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="36bb7-135">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="36bb7-136">SelectionCondition-element voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="36bb7-136">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="36bb7-137">SelectionSetName-element voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="36bb7-137">SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="36bb7-138">Het element TypeName voor EntrySelectedBy voor WideEntry (opmaak)</span><span class="sxs-lookup"><span data-stu-id="36bb7-138">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="36bb7-139">Een brede weergave maken</span><span class="sxs-lookup"><span data-stu-id="36bb7-139">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="36bb7-140">Voorwaarden voor het weergeven van gegevens definiëren</span><span class="sxs-lookup"><span data-stu-id="36bb7-140">Defining Conditions for Displaying Data</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="36bb7-141">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="36bb7-141">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
