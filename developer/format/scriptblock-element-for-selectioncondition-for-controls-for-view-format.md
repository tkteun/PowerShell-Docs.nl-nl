---
title: ScriptBlock-Element voor SelectionCondition voor besturingselementen voor weergave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 08512496-5682-4539-ab56-0c5394ce1f01
caps.latest.revision: 6
ms.openlocfilehash: 0137886437f01518f396613c564517e7910e657a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064387"
---
# <a name="scriptblock-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="da4fe-102">Het element ScriptBlock voor SelectionCondition voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="da4fe-102">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="da4fe-103">Hiermee geeft u het script dat de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="da4fe-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="da4fe-104">Wanneer dit script wordt geëvalueerd naar `true`, de voorwaarde wordt voldaan en de definitie wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="da4fe-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="da4fe-105">Dit element wordt gebruikt bij het definiëren van besturingselementen die kunnen worden gebruikt door een weergave.</span><span class="sxs-lookup"><span data-stu-id="da4fe-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="da4fe-106">Configuratie-Element (indeling) ViewDefinitions-Element (indeling) weergave-Element (indeling) besturingselementen Element (indeling) controle-Element voor besturingselementen voor weergave (indeling) CustomControl Element voor de controle voor besturingselementen voor weergave (indeling) CustomEntries Element voor CustomControl voor besturingselementen voor weergave (indeling) CustomEntry Element voor CustomEntries voor besturingselementen voor weergave (indeling) EntrySelectedBy Element voor CustomEntry voor besturingselementen voor weergave (indeling) SelectionCondition Element voor EntrySelectedBy voor besturingselementen voor weergave ( -Indeling) ScriptBlock Element voor SelectionCondition voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="da4fe-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="da4fe-107">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="da4fe-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="da4fe-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="da4fe-108">Attributes and Elements</span></span>

<span data-ttu-id="da4fe-109">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `ScriptBlock` element.</span><span class="sxs-lookup"><span data-stu-id="da4fe-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="da4fe-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="da4fe-110">Attributes</span></span>

<span data-ttu-id="da4fe-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="da4fe-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="da4fe-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="da4fe-112">Child Elements</span></span>

<span data-ttu-id="da4fe-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="da4fe-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="da4fe-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="da4fe-114">Parent Elements</span></span>

|<span data-ttu-id="da4fe-115">Element</span><span class="sxs-lookup"><span data-stu-id="da4fe-115">Element</span></span>|<span data-ttu-id="da4fe-116">Description</span><span class="sxs-lookup"><span data-stu-id="da4fe-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="da4fe-117">SelectionCondition-Element voor EntrySelectedBy voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="da4fe-117">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="da4fe-118">Hiermee definieert u een voorwaarde die moet aanwezig zijn voor de besturingselementdefinitie van het moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="da4fe-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="da4fe-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="da4fe-119">Text Value</span></span>

<span data-ttu-id="da4fe-120">Geef het script dat wordt geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="da4fe-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="da4fe-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="da4fe-121">Remarks</span></span>

<span data-ttu-id="da4fe-122">De selectievoorwaarde moet een minimaal één script of de eigenschap naam opgeven om te evalueren, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="da4fe-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="da4fe-123">Zie voor meer informatie over hoe voorwaarden van de selectie kunnen worden gebruikt, [voorwaarden definiëren voor het weergeven van gegevens](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="da4fe-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="da4fe-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="da4fe-124">See Also</span></span>

[<span data-ttu-id="da4fe-125">SelectionCondition-Element voor EntrySelectedBy voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="da4fe-125">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="da4fe-126">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="da4fe-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
