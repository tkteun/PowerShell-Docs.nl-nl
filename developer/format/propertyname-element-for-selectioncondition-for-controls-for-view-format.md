---
title: PropertyName-Element voor SelectionCondition voor besturingselementen voor weergave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 92c4237d-c2b2-4908-82ac-f36070f89d26
caps.latest.revision: 6
ms.openlocfilehash: 79859bed3d762948182e03babf71d4270278bae7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845078"
---
# <a name="propertyname-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="16201-102">Het element PropertyName voor SelectionCondition voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="16201-102">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="16201-103">Hiermee geeft u de .NET-eigenschap die de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="16201-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="16201-104">Als deze eigenschap is aanwezig, of wanneer deze wordt geëvalueerd naar `true`, de voorwaarde wordt voldaan en de vermelding wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="16201-104">When this property is present or when it evaluates to `true`, the condition is met, and the entry is used.</span></span> <span data-ttu-id="16201-105">Dit element wordt gebruikt bij het definiëren van besturingselementen die kunnen worden gebruikt door een weergave.</span><span class="sxs-lookup"><span data-stu-id="16201-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="16201-106">Configuratie-Element (indeling) ViewDefinitions-Element (indeling) weergave-Element (indeling) besturingselementen Element (indeling) controle-Element voor besturingselementen voor weergave (indeling) CustomControl Element voor de controle voor besturingselementen voor weergave (indeling) CustomEntries Element voor CustomControl voor besturingselementen voor weergave (indeling) CustomEntry Element voor CustomEntries voor besturingselementen voor weergave (indeling) EntrySelectedBy Element voor CustomEntry voor besturingselementen voor weergave (indeling) SelectionCondition Element voor EntrySelectedBy voor besturingselementen voor weergave ( -Indeling) PropertyName-Element voor SelectionCondition voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="16201-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="16201-107">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="16201-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="16201-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="16201-108">Attributes and Elements</span></span>

<span data-ttu-id="16201-109">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `PropertyName` element.</span><span class="sxs-lookup"><span data-stu-id="16201-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="16201-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="16201-110">Attributes</span></span>

<span data-ttu-id="16201-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="16201-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="16201-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="16201-112">Child Elements</span></span>

<span data-ttu-id="16201-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="16201-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="16201-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="16201-114">Parent Elements</span></span>

|<span data-ttu-id="16201-115">Element</span><span class="sxs-lookup"><span data-stu-id="16201-115">Element</span></span>|<span data-ttu-id="16201-116">Description</span><span class="sxs-lookup"><span data-stu-id="16201-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="16201-117">SelectionCondition-Element voor EntrySelectedBy voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="16201-117">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="16201-118">Hiermee definieert u een voorwaarde die moet aanwezig zijn voor de besturingselementdefinitie van het moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="16201-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="16201-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="16201-119">Text Value</span></span>

<span data-ttu-id="16201-120">Geef de naam van de .NET-eigenschap.</span><span class="sxs-lookup"><span data-stu-id="16201-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="16201-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="16201-121">Remarks</span></span>

<span data-ttu-id="16201-122">De selectievoorwaarde moet de naam van een minimaal één eigenschap of een script opgeven, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="16201-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="16201-123">Zie voor meer informatie over hoe voorwaarden van de selectie kunnen worden gebruikt, [voorwaarden definiëren voor het weergeven van gegevens](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="16201-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="16201-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="16201-124">See Also</span></span>

[<span data-ttu-id="16201-125">SelectionCondition-Element voor EntrySelectedBy voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="16201-125">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="16201-126">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="16201-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
