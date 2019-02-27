---
title: ScriptBlock-Element voor SelectionCondition voor CustomControl voor weergave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7031fa8b-3e2b-4ea8-89cb-95171f467b5a
caps.latest.revision: 6
ms.openlocfilehash: e55d1c5aa533005b258ecbbbf3ed9d55f852eab6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847801"
---
# <a name="scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="45b7a-102">Het element ScriptBlock voor SelectionCondition voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="45b7a-102">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="45b7a-103">Hiermee geeft u het script dat de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="45b7a-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="45b7a-104">Wanneer dit script wordt geëvalueerd naar `true`, de voorwaarde wordt voldaan en de definitie wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="45b7a-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="45b7a-105">Dit element wordt gebruikt bij het definiëren van een aangepast besturingselement-weergave.</span><span class="sxs-lookup"><span data-stu-id="45b7a-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="45b7a-106">Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) CustomControl Element voor weergave (indeling) CustomEntries-Element voor CustomControl voor weergave (indeling) CustomEntry Element voor CustomEntries voor CustomControl voor weergave ( -Indeling) CustomItem Element voor CustomEntry voor CustomControl voor weergave (indeling) SelectionCondition Element voor EntrySelectedBy voor CustomControl voor weergave (indeling) ScriptBlock Element voor SelectionCondition voor CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="45b7a-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format) ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="45b7a-107">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="45b7a-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="45b7a-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="45b7a-108">Attributes and Elements</span></span>

<span data-ttu-id="45b7a-109">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `ScriptBlock` element.</span><span class="sxs-lookup"><span data-stu-id="45b7a-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="45b7a-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="45b7a-110">Attributes</span></span>

<span data-ttu-id="45b7a-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="45b7a-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="45b7a-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="45b7a-112">Child Elements</span></span>

<span data-ttu-id="45b7a-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="45b7a-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="45b7a-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="45b7a-114">Parent Elements</span></span>

|<span data-ttu-id="45b7a-115">Element</span><span class="sxs-lookup"><span data-stu-id="45b7a-115">Element</span></span>|<span data-ttu-id="45b7a-116">Description</span><span class="sxs-lookup"><span data-stu-id="45b7a-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="45b7a-117">SelectionCondition-Element voor EntrySelectedBy voor CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="45b7a-117">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="45b7a-118">Hiermee definieert u een voorwaarde die moet aanwezig zijn voor de besturingselementdefinitie van het moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="45b7a-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="45b7a-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="45b7a-119">Text Value</span></span>

<span data-ttu-id="45b7a-120">Geef het script dat wordt geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="45b7a-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="45b7a-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="45b7a-121">Remarks</span></span>

<span data-ttu-id="45b7a-122">De selectievoorwaarde moet een minimaal één script of de eigenschap naam opgeven om te evalueren, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="45b7a-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="45b7a-123">Zie voor meer informatie over hoe voorwaarden van de selectie kunnen worden gebruikt, [voorwaarden definiëren voor het weergeven van gegevens](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="45b7a-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="45b7a-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="45b7a-124">See Also</span></span>

[<span data-ttu-id="45b7a-125">SelectionCondition-Element voor EntrySelectedBy voor CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="45b7a-125">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="45b7a-126">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="45b7a-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
