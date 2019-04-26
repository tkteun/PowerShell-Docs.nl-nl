---
title: ScriptBlock-Element voor SelectionCondition voor EntrySelectedBy voor WideControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ec68309-7826-4643-a521-e29c996663fb
caps.latest.revision: 11
ms.openlocfilehash: 649a978e21e9421a3f3e953261e1d309e23c3f9c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064319"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="5171b-102">Het element ScriptBlock voor SelectionCondition voor EntrySelectedBy voor WideControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="5171b-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="5171b-103">Hiermee geeft u het script dat de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="5171b-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="5171b-104">Wanneer dit script wordt geëvalueerd naar `true`, de voorwaarde wordt voldaan en de definitie van de brede vermelding wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="5171b-104">When this script is evaluated to `true`, the condition is met, and the wide entry definition is used.</span></span>

<span data-ttu-id="5171b-105">Configuratie Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) WideControl-Element (indeling) WideEntries-Element (indeling) WideEntry-Element (indeling) EntrySelectedBy Element voor WideEntry (indeling) SelectionCondition-Element voor EntrySelectedBy voor WideEntry (indeling) ScriptBlock Element voor SelectionCondition voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="5171b-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5171b-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="5171b-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5171b-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="5171b-107">Attributes and Elements</span></span>

<span data-ttu-id="5171b-108">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `ScriptBlock` element.</span><span class="sxs-lookup"><span data-stu-id="5171b-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5171b-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="5171b-109">Attributes</span></span>

<span data-ttu-id="5171b-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="5171b-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5171b-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="5171b-111">Child Elements</span></span>

<span data-ttu-id="5171b-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="5171b-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5171b-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="5171b-113">Parent Elements</span></span>

|<span data-ttu-id="5171b-114">Element</span><span class="sxs-lookup"><span data-stu-id="5171b-114">Element</span></span>|<span data-ttu-id="5171b-115">Description</span><span class="sxs-lookup"><span data-stu-id="5171b-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5171b-116">SelectionCondition-Element voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="5171b-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="5171b-117">Hiermee definieert u de voorwaarde die moet bestaan voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="5171b-117">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="5171b-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="5171b-118">Text Value</span></span>

<span data-ttu-id="5171b-119">Geef het script dat wordt geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="5171b-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="5171b-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="5171b-120">Remarks</span></span>

<span data-ttu-id="5171b-121">De selectievoorwaarde moet Geef ten minste één script of eigenschap op om te evalueren, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="5171b-121">The selection condition must specify at least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="5171b-122">Zie voor meer informatie over het gebruik van de voorwaarden van de selectie [definiëren voorwaarden voor wanneer gegevens worden weergegeven](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="5171b-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="5171b-123">Zie voor meer informatie over andere onderdelen van een brede weergave [brede weergave](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="5171b-123">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5171b-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="5171b-124">See Also</span></span>

[<span data-ttu-id="5171b-125">Het maken van een brede weergave</span><span class="sxs-lookup"><span data-stu-id="5171b-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="5171b-126">Voorwaarden voor wanneer gegevens worden weergegeven definiëren</span><span class="sxs-lookup"><span data-stu-id="5171b-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="5171b-127">PropertyName-Element voor SelectionCondition voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="5171b-127">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="5171b-128">SelectionCondition-Element voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="5171b-128">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="5171b-129">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="5171b-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
