---
title: PropertyName-Element voor SelectionCondition voor EntrySelectedBy voor ListControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 71c3f1f6-6fe2-42f1-8260-6974d3871748
caps.latest.revision: 11
ms.openlocfilehash: f857f5944b9e971215a06d6f5c39f7c22c6cf99f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56844917"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="c4bf1-102">Het element PropertyName voor SelectionCondition voor EntrySelectedBy voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c4bf1-102">PropertyName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="c4bf1-103">Hiermee geeft u de .NET-eigenschap die de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="c4bf1-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="c4bf1-104">Als deze eigenschap is aanwezig, of wanneer deze wordt geëvalueerd naar `true`, de voorwaarde wordt voldaan en vermelding in de lijst wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="c4bf1-104">When this property is present or when it evaluates to `true`, the condition is met, and the list entry is used.</span></span>

<span data-ttu-id="c4bf1-105">Configuratie Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) ListControl Element (indeling) ListEntries-Element (indeling) ListEntry-Element (indeling) EntrySelectedBy Element voor ListEntry (indeling) SelectionCondition-Element voor EntrySelectedBy voor ListEntry (indeling) PropertyName-Element voor SelectionCondition voor EmtrySelectedBy voor ListEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="c4bf1-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) PropertyName Element for SelectionCondition for EmtrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c4bf1-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="c4bf1-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c4bf1-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="c4bf1-107">Attributes and Elements</span></span>

<span data-ttu-id="c4bf1-108">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `PropertyName` element.</span><span class="sxs-lookup"><span data-stu-id="c4bf1-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c4bf1-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="c4bf1-109">Attributes</span></span>

<span data-ttu-id="c4bf1-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="c4bf1-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c4bf1-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="c4bf1-111">Child Elements</span></span>

<span data-ttu-id="c4bf1-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="c4bf1-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c4bf1-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="c4bf1-113">Parent Elements</span></span>

|<span data-ttu-id="c4bf1-114">Element</span><span class="sxs-lookup"><span data-stu-id="c4bf1-114">Element</span></span>|<span data-ttu-id="c4bf1-115">Description</span><span class="sxs-lookup"><span data-stu-id="c4bf1-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c4bf1-116">SelectionCondition-Element voor EntrySelectedBy voor ListEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="c4bf1-116">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="c4bf1-117">Hiermee definieert u de voorwaarde die moet bestaan voor deze vermelding lijst moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="c4bf1-117">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c4bf1-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="c4bf1-118">Text Value</span></span>

<span data-ttu-id="c4bf1-119">Geef de naam van de .NET-eigenschap.</span><span class="sxs-lookup"><span data-stu-id="c4bf1-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="c4bf1-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="c4bf1-120">Remarks</span></span>

<span data-ttu-id="c4bf1-121">De selectievoorwaarde moet ten minste één eigenschap name of een scriptblok opgeven, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="c4bf1-121">The selection condition must specify at least one property name or a script block, but cannot specify both.</span></span> <span data-ttu-id="c4bf1-122">Zie voor meer informatie over het gebruik van de voorwaarden van de selectie [definiëren voorwaarden voor wanneer een item weergeven of Item wordt gebruikt](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="c4bf1-122">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="c4bf1-123">Zie voor meer informatie over andere onderdelen van een lijst weergeven, [lijstweergave maken](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="c4bf1-123">For more information about other components of a list view, see [Creating List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c4bf1-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="c4bf1-124">See Also</span></span>

[<span data-ttu-id="c4bf1-125">Het maken van een lijst weergeven</span><span class="sxs-lookup"><span data-stu-id="c4bf1-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="c4bf1-126">Voorwaarden voor wanneer gegevens definiëren wordt weergegeven</span><span class="sxs-lookup"><span data-stu-id="c4bf1-126">Defining Conditions for When Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="c4bf1-127">ListEntry-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="c4bf1-127">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="c4bf1-128">ScriptBlock-Element voor SelectionCondition voor EntrySelectedBy voor ListEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="c4bf1-128">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="c4bf1-129">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="c4bf1-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
