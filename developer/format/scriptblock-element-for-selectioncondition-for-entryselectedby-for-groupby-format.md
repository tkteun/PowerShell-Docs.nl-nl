---
title: ScriptBlock-Element voor SelectionCondition voor EntrySelectedBy voor GroupBy (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e01344bd-ad69-4789-8e9f-2e79880c3a33
caps.latest.revision: 6
ms.openlocfilehash: cb79fb942111cee89c6b2abba75de4c494082b7e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56844763"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="60040-102">Het element ScriptBlock voor SelectionCondition voor EntrySelectedBy voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="60040-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="60040-103">Hiermee geeft u het script dat de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="60040-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="60040-104">Wanneer dit script wordt geëvalueerd naar `true`, de voorwaarde wordt voldaan en de definitie wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="60040-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="60040-105">Dit element wordt gebruikt bij het definiëren van hoe een nieuwe groep objecten worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="60040-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="60040-106">Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) GroupBy Element voor weergave (indeling) CustomControl Element voor GroupBy (indeling) CustomEntries Element voor CustomControl voor GroupBy (indeling) CustomEntry Element voor CustomControl voor GroupBy (indeling) EntrySelectedBy Element voor CustomEntry voor GroupBy (indeling) SelectionCondition Element voor EntrySelectedBy voor GroupBy (indeling) ScriptBlock Element voor SelectionCondition voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="60040-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) ScriptBlock Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="60040-107">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="60040-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="60040-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="60040-108">Attributes and Elements</span></span>

<span data-ttu-id="60040-109">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `ScriptBlock` element.</span><span class="sxs-lookup"><span data-stu-id="60040-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="60040-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="60040-110">Attributes</span></span>

<span data-ttu-id="60040-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="60040-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="60040-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="60040-112">Child Elements</span></span>

<span data-ttu-id="60040-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="60040-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="60040-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="60040-114">Parent Elements</span></span>

|<span data-ttu-id="60040-115">Element</span><span class="sxs-lookup"><span data-stu-id="60040-115">Element</span></span>|<span data-ttu-id="60040-116">Description</span><span class="sxs-lookup"><span data-stu-id="60040-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="60040-117">SelectionCondition-Element voor EntrySelectedBy voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="60040-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="60040-118">Hiermee definieert u een voorwaarde die moet aanwezig zijn voor de besturingselementdefinitie van het moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="60040-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="60040-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="60040-119">Text Value</span></span>

<span data-ttu-id="60040-120">Geef het script dat wordt geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="60040-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="60040-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="60040-121">Remarks</span></span>

<span data-ttu-id="60040-122">De selectievoorwaarde moet een minimaal één script of de eigenschap naam opgeven om te evalueren, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="60040-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="60040-123">Zie voor meer informatie over hoe voorwaarden van de selectie kunnen worden gebruikt, [voorwaarden definiëren voor het weergeven van gegevens](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="60040-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="60040-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="60040-124">See Also</span></span>

[<span data-ttu-id="60040-125">SelectionCondition-Element voor EntrySelectedBy voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="60040-125">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="60040-126">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="60040-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
