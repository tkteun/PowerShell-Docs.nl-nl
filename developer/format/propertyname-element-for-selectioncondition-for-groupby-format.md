---
title: PropertyName-Element voor SelectionCondition voor GroupBy (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d1707317-6c26-4866-bcc1-8924103c9014
caps.latest.revision: 6
ms.openlocfilehash: 7241ea0ea364befa7ad4ab0af4c4209be72214a7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064812"
---
# <a name="propertyname-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="0a171-102">Het element PropertyName voor SelectionCondition voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="0a171-102">PropertyName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="0a171-103">Hiermee geeft u de .NET-eigenschap die de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="0a171-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="0a171-104">Als deze eigenschap is aanwezig, of wanneer deze wordt geëvalueerd naar `true`, de voorwaarde wordt voldaan en de definitie wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="0a171-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="0a171-105">Dit element wordt gebruikt bij het definiëren van hoe een nieuwe groep objecten worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="0a171-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="0a171-106">Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) GroupBy Element voor weergave (indeling) CustomControl Element voor GroupBy (indeling) CustomEntries Element voor CustomControl voor GroupBy (indeling) CustomEntry Element voor CustomControl voor GroupBy (indeling) EntrySelectedBy Element voor CustomEntry voor GroupBy (indeling) SelectionCondition Element voor EntrySelectedBy voor GroupBy (indeling) PropertyName-Element voor SelectionCondition voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="0a171-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) PropertyName Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0a171-107">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="0a171-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0a171-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="0a171-108">Attributes and Elements</span></span>

<span data-ttu-id="0a171-109">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `PropertyName` element.</span><span class="sxs-lookup"><span data-stu-id="0a171-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0a171-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="0a171-110">Attributes</span></span>

<span data-ttu-id="0a171-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="0a171-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0a171-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="0a171-112">Child Elements</span></span>

<span data-ttu-id="0a171-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="0a171-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0a171-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="0a171-114">Parent Elements</span></span>

|<span data-ttu-id="0a171-115">Element</span><span class="sxs-lookup"><span data-stu-id="0a171-115">Element</span></span>|<span data-ttu-id="0a171-116">Description</span><span class="sxs-lookup"><span data-stu-id="0a171-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0a171-117">SelectionCondition-Element voor EntrySelectedBy voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="0a171-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="0a171-118">Hiermee definieert u een voorwaarde die moet aanwezig zijn voor de besturingselementdefinitie van het moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="0a171-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="0a171-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="0a171-119">Text Value</span></span>

<span data-ttu-id="0a171-120">Geef de naam van de .NET-eigenschap.</span><span class="sxs-lookup"><span data-stu-id="0a171-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="0a171-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="0a171-121">Remarks</span></span>

<span data-ttu-id="0a171-122">De selectievoorwaarde moet de naam van een minimaal één eigenschap of een script opgeven, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="0a171-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="0a171-123">Zie voor meer informatie over hoe voorwaarden van de selectie kunnen worden gebruikt, [voorwaarden definiëren voor het weergeven van gegevens](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="0a171-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0a171-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="0a171-124">See Also</span></span>

[<span data-ttu-id="0a171-125">SelectionCondition-Element voor EntrySelectedBy voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="0a171-125">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="0a171-126">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="0a171-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
