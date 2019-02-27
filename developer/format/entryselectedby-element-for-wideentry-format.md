---
title: EntrySelectedBy-Element voor WideEntry (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e0c98933-b7a5-4205-b811-06c0b0bf8988
caps.latest.revision: 9
ms.openlocfilehash: 54c7c261a23075721cd7bce75e530150dc0e0212
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846093"
---
# <a name="entryselectedby-element-for-wideentry-format"></a><span data-ttu-id="3ae0c-102">Het element EntrySelectedBy voor WideEntry (opmaak)</span><span class="sxs-lookup"><span data-stu-id="3ae0c-102">EntrySelectedBy Element for WideEntry (Format)</span></span>

<span data-ttu-id="3ae0c-103">Hiermee definieert u de .NET-typen die gebruikmaken van deze definitie van de brede weergave of de voorwaarde die moet bestaan voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="3ae0c-103">Defines the .NET types that use this definition of the wide view or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="3ae0c-104">Configuratie Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) WideControl-Element (indeling) WideEntries-Element (indeling) WideEntry-Element (indeling) EntrySelectedBy Element voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="3ae0c-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3ae0c-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="3ae0c-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3ae0c-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="3ae0c-106">Attributes and Elements</span></span>

<span data-ttu-id="3ae0c-107">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `EntrySelectedBy` element.</span><span class="sxs-lookup"><span data-stu-id="3ae0c-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3ae0c-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="3ae0c-108">Attributes</span></span>

<span data-ttu-id="3ae0c-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="3ae0c-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3ae0c-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="3ae0c-110">Child Elements</span></span>

|<span data-ttu-id="3ae0c-111">Element</span><span class="sxs-lookup"><span data-stu-id="3ae0c-111">Element</span></span>|<span data-ttu-id="3ae0c-112">Description</span><span class="sxs-lookup"><span data-stu-id="3ae0c-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3ae0c-113">SelectionCondition-Element voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="3ae0c-113">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="3ae0c-114">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="3ae0c-114">Optional element.</span></span><br /><br /> <span data-ttu-id="3ae0c-115">Hiermee definieert u de voorwaarde die moet bestaan voor deze definitie brede weergave moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="3ae0c-115">Defines the condition that must exist for this wide view definition to be used.</span></span>|
|[<span data-ttu-id="3ae0c-116">SelectionSetName-Element voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="3ae0c-116">SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="3ae0c-117">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="3ae0c-117">Optional element.</span></span><br /><br /> <span data-ttu-id="3ae0c-118">Hiermee geeft u een set van .NET-typen die gebruikmaken van deze definitie brede weergave.</span><span class="sxs-lookup"><span data-stu-id="3ae0c-118">Specifies a set of .NET types that use this wide view definition.</span></span>|
|[<span data-ttu-id="3ae0c-119">TypeName-Element voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="3ae0c-119">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="3ae0c-120">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="3ae0c-120">Optional element.</span></span><br /><br /> <span data-ttu-id="3ae0c-121">Hiermee geeft u een .NET-type dat gebruikmaakt van deze definitie brede weergave.</span><span class="sxs-lookup"><span data-stu-id="3ae0c-121">Specifies a .NET type that uses this wide view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3ae0c-122">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="3ae0c-122">Parent Elements</span></span>

|<span data-ttu-id="3ae0c-123">Element</span><span class="sxs-lookup"><span data-stu-id="3ae0c-123">Element</span></span>|<span data-ttu-id="3ae0c-124">Description</span><span class="sxs-lookup"><span data-stu-id="3ae0c-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3ae0c-125">WideEntry-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="3ae0c-125">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="3ae0c-126">Bevat een definitie van de brede weergave.</span><span class="sxs-lookup"><span data-stu-id="3ae0c-126">Provides a definition of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3ae0c-127">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="3ae0c-127">Remarks</span></span>

<span data-ttu-id="3ae0c-128">U moet ten minste één type, selectie instellen of selectievoorwaarde voor de definitie van een brede weergave opgeven.</span><span class="sxs-lookup"><span data-stu-id="3ae0c-128">You must specify at least one type, selection set, or selection condition for a wide view definition.</span></span> <span data-ttu-id="3ae0c-129">Er is geen maximale limiet voor het aantal onderliggende elementen die u kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="3ae0c-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="3ae0c-130">Selectie voorwaarden worden gebruikt voor het definiëren van een voorwaarde die moet aanwezig zijn voor de definitie moet worden gebruikt, zoals wanneer een object een bepaalde eigenschap heeft of die een bepaalde eigenschapwaarde of een Scriptwaarde resulteert in `true`.</span><span class="sxs-lookup"><span data-stu-id="3ae0c-130">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script value evaluates to `true`.</span></span> <span data-ttu-id="3ae0c-131">Zie voor meer informatie over de voorwaarden van de selectie [voorwaarden definiëren voor het weergeven van gegevens](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="3ae0c-131">For more information about selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="3ae0c-132">Zie voor meer informatie over andere onderdelen van een brede weergave [het maken van een brede weergave](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="3ae0c-132">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3ae0c-133">Zie ook</span><span class="sxs-lookup"><span data-stu-id="3ae0c-133">See Also</span></span>

[<span data-ttu-id="3ae0c-134">WideEntry-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="3ae0c-134">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="3ae0c-135">SelectionCondition-Element voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="3ae0c-135">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="3ae0c-136">SelectionSetName-Element voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="3ae0c-136">SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="3ae0c-137">TypeName-Element voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="3ae0c-137">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="3ae0c-138">Het maken van een brede weergave</span><span class="sxs-lookup"><span data-stu-id="3ae0c-138">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="3ae0c-139">Voorwaarden voor het weergeven van gegevens definiëren</span><span class="sxs-lookup"><span data-stu-id="3ae0c-139">Defining Conditions for Displaying Data</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="3ae0c-140">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="3ae0c-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
