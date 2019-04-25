---
title: EntrySelectedBy-Element voor EnumerableExpansion (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3af6aff8-4c2d-4f08-9bb1-e1f3ed3e583e
caps.latest.revision: 11
ms.openlocfilehash: 6a371bdbb85d07730c32931a4a79ee40856ce298
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066206"
---
# <a name="entryselectedby-element-for-enumerableexpansion-format"></a><span data-ttu-id="696f0-102">Het element EntrySelectedBy voor EnumerableExpansion (opmaak)</span><span class="sxs-lookup"><span data-stu-id="696f0-102">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="696f0-103">Hiermee definieert u de .NET-typen die gebruikmaken van deze definitie of de voorwaarde die moet bestaan voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="696f0-103">Defines the .NET types that use this definition or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="696f0-104">Configuratie van Element (indeling) DefaultSettings-Element (indeling) EnumerableExpansions-Element (indeling) EnumerableExpansion-Element (indeling) EntrySelectedBy Element voor EnumerableExpansion (indeling)</span><span class="sxs-lookup"><span data-stu-id="696f0-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="696f0-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="696f0-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="696f0-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="696f0-106">Attributes and Elements</span></span>

<span data-ttu-id="696f0-107">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `EntrySelectedBy` element.</span><span class="sxs-lookup"><span data-stu-id="696f0-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="696f0-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="696f0-108">Attributes</span></span>

<span data-ttu-id="696f0-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="696f0-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="696f0-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="696f0-110">Child Elements</span></span>

|<span data-ttu-id="696f0-111">Element</span><span class="sxs-lookup"><span data-stu-id="696f0-111">Element</span></span>|<span data-ttu-id="696f0-112">Description</span><span class="sxs-lookup"><span data-stu-id="696f0-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="696f0-113">SelectionCondition-Element voor EntrySelectedBy voor EnumerableExpansion (indeling)</span><span class="sxs-lookup"><span data-stu-id="696f0-113">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="696f0-114">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="696f0-114">Optional element.</span></span><br /><br /> <span data-ttu-id="696f0-115">De voorwaarde die moet aanwezig zijn om uit te breiden, de verzameling objecten van deze definitie wordt gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="696f0-115">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|
|[<span data-ttu-id="696f0-116">SelectionSetName-Element voor EntrySelectedBy voor EnumerableExpansion (indeling)</span><span class="sxs-lookup"><span data-stu-id="696f0-116">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="696f0-117">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="696f0-117">Optional element.</span></span><br /><br /> <span data-ttu-id="696f0-118">Hiermee geeft u een set van .NET-typen die gebruikmaken van deze definitie van hoe verzameling objecten worden uitgevouwen.</span><span class="sxs-lookup"><span data-stu-id="696f0-118">Specifies a set of .NET types that use this definition of how collection objects are expanded.</span></span>|
|[<span data-ttu-id="696f0-119">TypeName-Element voor EntrySelectedBy voor EnumerableExpansion (indeling)</span><span class="sxs-lookup"><span data-stu-id="696f0-119">TypeName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="696f0-120">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="696f0-120">Optional element.</span></span><br /><br /> <span data-ttu-id="696f0-121">Hiermee geeft u een .NET-type dat gebruikmaakt van deze definitie van hoe verzameling objecten worden uitgevouwen.</span><span class="sxs-lookup"><span data-stu-id="696f0-121">Specifies a .NET type that uses this definition of how collection objects are expanded.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="696f0-122">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="696f0-122">Parent Elements</span></span>

|<span data-ttu-id="696f0-123">Element</span><span class="sxs-lookup"><span data-stu-id="696f0-123">Element</span></span>|<span data-ttu-id="696f0-124">Description</span><span class="sxs-lookup"><span data-stu-id="696f0-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="696f0-125">EnumerableExpansion-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="696f0-125">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="696f0-126">Hiermee definieert u hoe specifieke .NET-verzameling objecten worden uitgevouwen wanneer ze worden weergegeven in een weergave.</span><span class="sxs-lookup"><span data-stu-id="696f0-126">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="696f0-127">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="696f0-127">Remarks</span></span>

<span data-ttu-id="696f0-128">U moet ten minste één type, selectie instellen of selectievoorwaarde voor een definitie-invoer opgeven.</span><span class="sxs-lookup"><span data-stu-id="696f0-128">You must specify at least one type, selection set, or selection condition for a definition entry.</span></span> <span data-ttu-id="696f0-129">Er is geen maximale limiet voor het aantal onderliggende elementen die u kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="696f0-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="696f0-130">Selectie voorwaarden worden gebruikt voor het definiëren van een voorwaarde die moet aanwezig zijn voor de definitie moet worden gebruikt, zoals wanneer een object een bepaalde eigenschap heeft of die een bepaalde eigenschapwaarde of een script wordt geëvalueerd als `true`.</span><span class="sxs-lookup"><span data-stu-id="696f0-130">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="696f0-131">Zie voor meer informatie over de voorwaarden van de selectie [voorwaarden definiëren voor het weergeven van gegevens](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="696f0-131">For more information about selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="696f0-132">Zie ook</span><span class="sxs-lookup"><span data-stu-id="696f0-132">See Also</span></span>

[<span data-ttu-id="696f0-133">Voorwaarden voor het weergeven van gegevens definiëren</span><span class="sxs-lookup"><span data-stu-id="696f0-133">Defining Conditions for Displaying Data</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="696f0-134">EnumerableExpansion-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="696f0-134">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)

[<span data-ttu-id="696f0-135">SelectionCondition-Element voor EntrySelectedBy voor EnumerableExpansion (indeling)</span><span class="sxs-lookup"><span data-stu-id="696f0-135">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="696f0-136">SelectionSetName-Element voor EntrySelectedBy voor EnumerableExpansion (indeling)</span><span class="sxs-lookup"><span data-stu-id="696f0-136">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="696f0-137">TypeName-Element voor EntrySelectedBy voor EnumerableExpansion (indeling)</span><span class="sxs-lookup"><span data-stu-id="696f0-137">TypeName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="696f0-138">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="696f0-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
