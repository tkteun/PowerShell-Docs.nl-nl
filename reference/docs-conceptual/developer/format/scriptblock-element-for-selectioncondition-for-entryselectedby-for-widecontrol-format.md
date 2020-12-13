---
ms.date: 09/13/2016
ms.topic: reference
title: Het element ScriptBlock voor SelectionCondition voor EntrySelectedBy voor WideControl (opmaak)
description: Het element ScriptBlock voor SelectionCondition voor EntrySelectedBy voor WideControl (opmaak)
ms.openlocfilehash: 53d3eba9d453dbcc96afbe8f81a16b61573f2874
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651970"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="ee89b-103">Het element ScriptBlock voor SelectionCondition voor EntrySelectedBy voor WideControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="ee89b-103">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="ee89b-104">Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="ee89b-104">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="ee89b-105">Wanneer dit script wordt geëvalueerd naar `true` , wordt voldaan aan de voor waarde en wordt de definitie van het grote item gebruikt.</span><span class="sxs-lookup"><span data-stu-id="ee89b-105">When this script is evaluated to `true`, the condition is met, and the wide entry definition is used.</span></span>

<span data-ttu-id="ee89b-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) WideControl element (indeling) WideEntries element (indeling) WideEntry element (indeling) EntrySelectedBy element voor WideEntry (Format) SelectionCondition-element voor EntrySelectedBy voor WideEntry (Format) script block-element voor SelectionCondition voor EntrySelectedBy</span><span class="sxs-lookup"><span data-stu-id="ee89b-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ee89b-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="ee89b-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ee89b-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="ee89b-108">Attributes and Elements</span></span>

<span data-ttu-id="ee89b-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `ScriptBlock` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="ee89b-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ee89b-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="ee89b-110">Attributes</span></span>

<span data-ttu-id="ee89b-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="ee89b-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ee89b-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="ee89b-112">Child Elements</span></span>

<span data-ttu-id="ee89b-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="ee89b-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ee89b-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="ee89b-114">Parent Elements</span></span>

|<span data-ttu-id="ee89b-115">Element</span><span class="sxs-lookup"><span data-stu-id="ee89b-115">Element</span></span>|<span data-ttu-id="ee89b-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="ee89b-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ee89b-117">SelectionCondition-element voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="ee89b-117">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="ee89b-118">Hiermee definieert u de voor waarde die voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="ee89b-118">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ee89b-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="ee89b-119">Text Value</span></span>

<span data-ttu-id="ee89b-120">Geef het script op dat wordt geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="ee89b-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="ee89b-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="ee89b-121">Remarks</span></span>

<span data-ttu-id="ee89b-122">Voor de selectie voorwaarde moet ten minste één script of eigenschaps naam worden opgegeven die moet worden geëvalueerd, maar kan niet beide worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="ee89b-122">The selection condition must specify at least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="ee89b-123">Zie voor [waarden definiëren voor wanneer gegevens worden weer gegeven](./defining-conditions-for-displaying-data.md)voor meer informatie over het gebruik van selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="ee89b-123">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="ee89b-124">Zie [brede weer gave](./creating-a-wide-view.md)voor meer informatie over andere onderdelen van een brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="ee89b-124">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ee89b-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="ee89b-125">See Also</span></span>

[<span data-ttu-id="ee89b-126">Een brede weergave maken</span><span class="sxs-lookup"><span data-stu-id="ee89b-126">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="ee89b-127">Voor waarden definiëren voor wanneer gegevens worden weer gegeven</span><span class="sxs-lookup"><span data-stu-id="ee89b-127">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="ee89b-128">Het element PropertyName voor SelectionCondition voor EntrySelectedBy voor WideEntry (opmaak)</span><span class="sxs-lookup"><span data-stu-id="ee89b-128">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="ee89b-129">SelectionCondition-element voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="ee89b-129">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="ee89b-130">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="ee89b-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
