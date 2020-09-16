---
title: Het element PropertyName voor SelectionCondition voor de EntrySelectedBy voor ListControl (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 3f0a6b6b381f39492da36dab271503fc7cf6e7fc
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785554"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="c97c6-102">Het element PropertyName voor SelectionCondition voor EntrySelectedBy voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c97c6-102">PropertyName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="c97c6-103">Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="c97c6-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="c97c6-104">Wanneer deze eigenschap aanwezig is of wanneer deze wordt geëvalueerd `true` , wordt voldaan aan de voor waarde en wordt de vermelding in de lijst gebruikt.</span><span class="sxs-lookup"><span data-stu-id="c97c6-104">When this property is present or when it evaluates to `true`, the condition is met, and the list entry is used.</span></span>

<span data-ttu-id="c97c6-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element van weer gave (indeling) bestand van ListControl element (indeling) (Format) element (indeling) EntrySelectedBy element (Format) element list item (Format) voor List entry (Format) SelectionCondition element voor EntrySelectedBy voor List entry (Format) eigenschap naam van SelectionCondition voor List entry (Format)</span><span class="sxs-lookup"><span data-stu-id="c97c6-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c97c6-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="c97c6-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c97c6-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="c97c6-107">Attributes and Elements</span></span>

<span data-ttu-id="c97c6-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `PropertyName` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="c97c6-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c97c6-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="c97c6-109">Attributes</span></span>

<span data-ttu-id="c97c6-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="c97c6-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c97c6-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="c97c6-111">Child Elements</span></span>

<span data-ttu-id="c97c6-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="c97c6-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c97c6-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="c97c6-113">Parent Elements</span></span>

|<span data-ttu-id="c97c6-114">Element</span><span class="sxs-lookup"><span data-stu-id="c97c6-114">Element</span></span>|<span data-ttu-id="c97c6-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="c97c6-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c97c6-116">SelectionCondition-element voor EntrySelectedBy voor List entry (indeling)</span><span class="sxs-lookup"><span data-stu-id="c97c6-116">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="c97c6-117">Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van deze lijst vermelding.</span><span class="sxs-lookup"><span data-stu-id="c97c6-117">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c97c6-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="c97c6-118">Text Value</span></span>

<span data-ttu-id="c97c6-119">Geef de .NET-eigenschaps naam op.</span><span class="sxs-lookup"><span data-stu-id="c97c6-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="c97c6-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="c97c6-120">Remarks</span></span>

<span data-ttu-id="c97c6-121">Voor de selectie voorwaarde moet ten minste één eigenschaps naam of een script blok worden opgegeven, maar kan niet beide worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="c97c6-121">The selection condition must specify at least one property name or a script block, but cannot specify both.</span></span> <span data-ttu-id="c97c6-122">Zie voor [waarden definiëren voor wanneer een weergave vermelding of-item wordt gebruikt](./defining-conditions-for-displaying-data.md)voor meer informatie over het gebruik van selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="c97c6-122">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="c97c6-123">Zie [lijst weergave maken](./creating-a-list-view.md)voor meer informatie over andere onderdelen van een lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="c97c6-123">For more information about other components of a list view, see [Creating List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c97c6-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="c97c6-124">See Also</span></span>

[<span data-ttu-id="c97c6-125">Een lijstweergave maken</span><span class="sxs-lookup"><span data-stu-id="c97c6-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="c97c6-126">Voor waarden definiëren voor wanneer gegevens worden weer gegeven</span><span class="sxs-lookup"><span data-stu-id="c97c6-126">Defining Conditions for When Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="c97c6-127">Element List entry (indeling)</span><span class="sxs-lookup"><span data-stu-id="c97c6-127">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="c97c6-128">Script block-element voor SelectionCondition voor EntrySelectedBy voor List entry (indeling)</span><span class="sxs-lookup"><span data-stu-id="c97c6-128">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="c97c6-129">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="c97c6-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
