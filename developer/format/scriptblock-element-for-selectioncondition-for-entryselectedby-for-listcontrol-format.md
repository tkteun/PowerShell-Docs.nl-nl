---
title: ScriptBlock-Element voor SelectionCondition voor EntrySelectedBy voor ListControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a1adad7-e864-4892-9d26-a6476a9698d2
caps.latest.revision: 7
ms.openlocfilehash: fd708473d04a76bcf6cf3a8f8278e1d15fb9addf
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848669"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="a1fc4-102">Het element ScriptBlock voor SelectionCondition voor EntrySelectedBy voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="a1fc4-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="a1fc4-103">Hiermee geeft u het script dat de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="a1fc4-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="a1fc4-104">Wanneer dit script wordt geëvalueerd naar `true`, de voorwaarde wordt voldaan en vermelding in de lijst wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="a1fc4-104">When this script is evaluated to `true`, the condition is met, and the list entry is used.</span></span>

<span data-ttu-id="a1fc4-105">Configuratie Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) ListControl Element (indeling) ListEntries-Element (indeling) ListEntry-Element (indeling) EntrySelectedBy Element voor ListEntry (indeling) SelectionCondition-Element voor EntrySelectedBy voor ListEntry (indeling) ScriptBlock Element voor SelectionCondition voor EntrySelectedBy voor ListEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="a1fc4-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a1fc4-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="a1fc4-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a1fc4-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="a1fc4-107">Attributes and Elements</span></span>

<span data-ttu-id="a1fc4-108">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `ScriptBlock` element.</span><span class="sxs-lookup"><span data-stu-id="a1fc4-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a1fc4-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="a1fc4-109">Attributes</span></span>

<span data-ttu-id="a1fc4-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="a1fc4-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a1fc4-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="a1fc4-111">Child Elements</span></span>

<span data-ttu-id="a1fc4-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="a1fc4-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a1fc4-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="a1fc4-113">Parent Elements</span></span>

|<span data-ttu-id="a1fc4-114">Element</span><span class="sxs-lookup"><span data-stu-id="a1fc4-114">Element</span></span>|<span data-ttu-id="a1fc4-115">Description</span><span class="sxs-lookup"><span data-stu-id="a1fc4-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a1fc4-116">SelectionCondition-Element voor EntrySelectedBy voor ListEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="a1fc4-116">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="a1fc4-117">Hiermee definieert u de voorwaarde die moet bestaan voor deze vermelding lijst moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="a1fc4-117">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a1fc4-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="a1fc4-118">Text Value</span></span>

<span data-ttu-id="a1fc4-119">Geef het script dat wordt geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="a1fc4-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="a1fc4-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="a1fc4-120">Remarks</span></span>

<span data-ttu-id="a1fc4-121">De selectievoorwaarde moet een minimaal één script of de eigenschap naam opgeven om te evalueren, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="a1fc4-121">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="a1fc4-122">(Zie voor meer informatie over hoe voorwaarden van de selectie kunnen worden gebruikt, [definiëren voorwaarden voor wanneer een item weergeven of Item wordt gebruikt](./defining-conditions-for-displaying-data.md).)</span><span class="sxs-lookup"><span data-stu-id="a1fc4-122">(For more information about how selection conditions can be used, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).)</span></span>

<span data-ttu-id="a1fc4-123">Zie voor meer informatie over de andere onderdelen van een lijst weergeven, [lijstweergave](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="a1fc4-123">For more information about the other components of a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a1fc4-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="a1fc4-124">See Also</span></span>

[<span data-ttu-id="a1fc4-125">ListEntry-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="a1fc4-125">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="a1fc4-126">PropertyName-Element voor SelectionCondition voor EmtrySelectedBy voor ListEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="a1fc4-126">PropertyName Element for SelectionCondition for EmtrySelectedBy for ListEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="a1fc4-127">SelectionCondition-Element voor EntrySelectedBy voor ListEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="a1fc4-127">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="a1fc4-128">Lijstweergave</span><span class="sxs-lookup"><span data-stu-id="a1fc4-128">List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="a1fc4-129">Voorwaarden voor het definiëren wanneer een item weergeven of een Item wordt gebruikt</span><span class="sxs-lookup"><span data-stu-id="a1fc4-129">Defining Conditions for when a View Entry or Item is Used</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="a1fc4-130">Schrijven van een Windows PowerShell opmaak en het bestand van het type</span><span class="sxs-lookup"><span data-stu-id="a1fc4-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
