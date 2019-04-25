---
title: PropertyName-Element voor SelectionCondition voor EntrySelectedBy voor WideEntry (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 340abb12-6df1-42f4-bdae-b0509c90952c
caps.latest.revision: 11
ms.openlocfilehash: 196877b97db9ed0592e357486c1318dc1e7efd31
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064676"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="b2de2-102">Het element PropertyName voor SelectionCondition voor EntrySelectedBy voor WideEntry (opmaak)</span><span class="sxs-lookup"><span data-stu-id="b2de2-102">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="b2de2-103">Hiermee geeft u de .NET-eigenschap die de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="b2de2-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="b2de2-104">Als deze eigenschap is aanwezig, of wanneer deze wordt geëvalueerd naar `true`, de voorwaarde wordt voldaan en de definitie wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="b2de2-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span>

<span data-ttu-id="b2de2-105">Configuratie Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) WideControl-Element (indeling) WideEntries-Element (indeling) WideEntry-Element (indeling) EntrySelectedBy Element voor WideEntry (indeling) SelectionCondition-Element voor EntrySelectedBy voor WideEntry (indeling) PropertyName-Element voor SelectionCondition voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="b2de2-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b2de2-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="b2de2-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

```csharp

```

## <a name="attributes-and-elements"></a><span data-ttu-id="b2de2-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="b2de2-107">Attributes and Elements</span></span>

<span data-ttu-id="b2de2-108">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `PropertyName` element.</span><span class="sxs-lookup"><span data-stu-id="b2de2-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b2de2-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="b2de2-109">Attributes</span></span>

<span data-ttu-id="b2de2-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="b2de2-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b2de2-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="b2de2-111">Child Elements</span></span>

<span data-ttu-id="b2de2-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="b2de2-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b2de2-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="b2de2-113">Parent Elements</span></span>

|<span data-ttu-id="b2de2-114">Element</span><span class="sxs-lookup"><span data-stu-id="b2de2-114">Element</span></span>|<span data-ttu-id="b2de2-115">Description</span><span class="sxs-lookup"><span data-stu-id="b2de2-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b2de2-116">SelectionCondition-Element voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="b2de2-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="b2de2-117">Hiermee definieert u de voorwaarde die moet bestaan voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="b2de2-117">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b2de2-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="b2de2-118">Text Value</span></span>

<span data-ttu-id="b2de2-119">Geef de naam van de .NET-eigenschap.</span><span class="sxs-lookup"><span data-stu-id="b2de2-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="b2de2-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="b2de2-120">Remarks</span></span>

<span data-ttu-id="b2de2-121">De selectievoorwaarde moet opgeven de naam van ten minste één eigenschap of een script om te evalueren, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="b2de2-121">The selection condition must specify at least one property name or a script to evaluate, but cannot specify both.</span></span> <span data-ttu-id="b2de2-122">Zie voor meer informatie over het gebruik van de voorwaarden van de selectie [definiëren voorwaarden voor wanneer gegevens worden weergegeven](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="b2de2-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="b2de2-123">Zie voor meer informatie over andere onderdelen van een brede weergave [brede weergave](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="b2de2-123">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b2de2-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="b2de2-124">See Also</span></span>

[<span data-ttu-id="b2de2-125">Het maken van een brede weergave</span><span class="sxs-lookup"><span data-stu-id="b2de2-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="b2de2-126">Voorwaarden voor wanneer gegevens worden weergegeven definiëren</span><span class="sxs-lookup"><span data-stu-id="b2de2-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="b2de2-127">ScriptBlock-Element voor SelectionCondition voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="b2de2-127">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="b2de2-128">SelectionCondition-Element voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="b2de2-128">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="b2de2-129">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="b2de2-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
