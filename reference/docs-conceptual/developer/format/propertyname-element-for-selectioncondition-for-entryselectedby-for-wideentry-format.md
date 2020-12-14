---
ms.date: 09/13/2016
ms.topic: reference
title: Het element PropertyName voor SelectionCondition voor EntrySelectedBy voor WideEntry (opmaak)
description: Het element PropertyName voor SelectionCondition voor EntrySelectedBy voor WideEntry (opmaak)
ms.openlocfilehash: bda34b0c1e97fb85536132bedcec3986072801b7
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665699"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="945dc-103">Het element PropertyName voor SelectionCondition voor EntrySelectedBy voor WideEntry (opmaak)</span><span class="sxs-lookup"><span data-stu-id="945dc-103">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="945dc-104">Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="945dc-104">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="945dc-105">Wanneer deze eigenschap aanwezig is of wanneer deze wordt geëvalueerd `true` , wordt voldaan aan de voor waarde en wordt de definitie gebruikt.</span><span class="sxs-lookup"><span data-stu-id="945dc-105">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span>

<span data-ttu-id="945dc-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) WideControl element (indeling) WideEntries element (indeling) WideEntry element (indeling) EntrySelectedBy element voor WideEntry (Format) SelectionCondition element voor EntrySelectedBy voor WideEntry (Format) voor SelectionCondition voor EntrySelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="945dc-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="945dc-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="945dc-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

```csharp

```

## <a name="attributes-and-elements"></a><span data-ttu-id="945dc-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="945dc-108">Attributes and Elements</span></span>

<span data-ttu-id="945dc-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `PropertyName` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="945dc-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="945dc-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="945dc-110">Attributes</span></span>

<span data-ttu-id="945dc-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="945dc-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="945dc-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="945dc-112">Child Elements</span></span>

<span data-ttu-id="945dc-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="945dc-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="945dc-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="945dc-114">Parent Elements</span></span>

|<span data-ttu-id="945dc-115">Element</span><span class="sxs-lookup"><span data-stu-id="945dc-115">Element</span></span>|<span data-ttu-id="945dc-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="945dc-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="945dc-117">SelectionCondition-element voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="945dc-117">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="945dc-118">Hiermee definieert u de voor waarde die voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="945dc-118">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="945dc-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="945dc-119">Text Value</span></span>

<span data-ttu-id="945dc-120">Geef de .NET-eigenschaps naam op.</span><span class="sxs-lookup"><span data-stu-id="945dc-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="945dc-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="945dc-121">Remarks</span></span>

<span data-ttu-id="945dc-122">Voor de selectie voorwaarde moet ten minste één eigenschaps naam of een script worden opgegeven om te evalueren, maar kan niet beide worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="945dc-122">The selection condition must specify at least one property name or a script to evaluate, but cannot specify both.</span></span> <span data-ttu-id="945dc-123">Zie voor [waarden definiëren voor wanneer gegevens worden weer gegeven](./defining-conditions-for-displaying-data.md)voor meer informatie over het gebruik van selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="945dc-123">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="945dc-124">Zie [brede weer gave](./creating-a-wide-view.md)voor meer informatie over andere onderdelen van een brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="945dc-124">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="945dc-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="945dc-125">See Also</span></span>

[<span data-ttu-id="945dc-126">Een brede weergave maken</span><span class="sxs-lookup"><span data-stu-id="945dc-126">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="945dc-127">Voor waarden definiëren voor wanneer gegevens worden weer gegeven</span><span class="sxs-lookup"><span data-stu-id="945dc-127">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="945dc-128">Script block-element voor SelectionCondition voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="945dc-128">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="945dc-129">SelectionCondition-element voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="945dc-129">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="945dc-130">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="945dc-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
