---
title: PropertyName-Element voor SelectionCondition voor CustomControl voor weergave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fc48a417-2083-46d4-ac38-16c12e65b6b9
caps.latest.revision: 7
ms.openlocfilehash: e08037d5d051d3be51e90193c7e87cc2e738f78a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850286"
---
# <a name="propertyname-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="3d71b-102">Het element PropertyName voor SelectionCondition voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="3d71b-102">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="3d71b-103">Hiermee geeft u de .NET-eigenschap die de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="3d71b-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="3d71b-104">Als deze eigenschap is aanwezig, of wanneer deze wordt geëvalueerd naar `true`, de voorwaarde wordt voldaan en de definitie wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="3d71b-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="3d71b-105">Dit element wordt gebruikt bij het definiëren van een aangepast besturingselement-weergave.</span><span class="sxs-lookup"><span data-stu-id="3d71b-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="3d71b-106">Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) CustomControl Element voor weergave (indeling) CustomEntries-Element voor CustomControl voor weergave (indeling) CustomEntry Element voor CustomEntries voor CustomControl voor weergave ( -Indeling) CustomItem Element voor CustomEntry voor CustomControl voor weergave (indeling) EntrySelectedBy Element voor CustomEntry voor CustomControl voor weergave (indeling) SelectionCondition Element voor EntrySelectedBy voor CustomControl voor PropertyName weergeven (indeling) Element voor SelectionCondition voor CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="3d71b-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) EntrySelectedBy Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format) PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3d71b-107">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="3d71b-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3d71b-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="3d71b-108">Attributes and Elements</span></span>

<span data-ttu-id="3d71b-109">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `PropertyName` element.</span><span class="sxs-lookup"><span data-stu-id="3d71b-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3d71b-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="3d71b-110">Attributes</span></span>

<span data-ttu-id="3d71b-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="3d71b-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3d71b-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="3d71b-112">Child Elements</span></span>

<span data-ttu-id="3d71b-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="3d71b-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="3d71b-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="3d71b-114">Parent Elements</span></span>

|<span data-ttu-id="3d71b-115">Element</span><span class="sxs-lookup"><span data-stu-id="3d71b-115">Element</span></span>|<span data-ttu-id="3d71b-116">Description</span><span class="sxs-lookup"><span data-stu-id="3d71b-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3d71b-117">SelectionCondition-Element voor EntrySelectedBy voor CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="3d71b-117">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="3d71b-118">Hiermee definieert u een voorwaarde die moet aanwezig zijn voor de besturingselementdefinitie van het moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="3d71b-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="3d71b-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="3d71b-119">Text Value</span></span>

<span data-ttu-id="3d71b-120">Geef de naam van de .NET-eigenschap.</span><span class="sxs-lookup"><span data-stu-id="3d71b-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="3d71b-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="3d71b-121">Remarks</span></span>

<span data-ttu-id="3d71b-122">De selectievoorwaarde moet de naam van een minimaal één eigenschap of een script opgeven, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="3d71b-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="3d71b-123">Zie voor meer informatie over hoe voorwaarden van de selectie kunnen worden gebruikt, [voorwaarden definiëren voor het weergeven van gegevens](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="3d71b-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3d71b-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="3d71b-124">See Also</span></span>

[<span data-ttu-id="3d71b-125">SelectionCondition-Element voor EntrySelectedBy voor CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="3d71b-125">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="3d71b-126">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="3d71b-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
