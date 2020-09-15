---
title: Script block-element voor SelectionCondition voor EntrySelectedBy voor ListControl (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 56bd04c9af74bdaa7a186a208fc15a67cb08b004
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87772855"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="1ef24-102">Het element ScriptBlock voor SelectionCondition voor EntrySelectedBy voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="1ef24-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="1ef24-103">Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="1ef24-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="1ef24-104">Wanneer dit script wordt geëvalueerd `true` , wordt voldaan aan de voor waarde en wordt de vermelding in de lijst gebruikt.</span><span class="sxs-lookup"><span data-stu-id="1ef24-104">When this script is evaluated to `true`, the condition is met, and the list entry is used.</span></span>

<span data-ttu-id="1ef24-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) ListControl element (indeling) item type-element (indeling) EntrySelectedBy element (Format) element list item (Format) voor List entry (Format) SelectionCondition-element voor EntrySelectedBy voor List entry (Format) script block-element voor SelectionCondition voor List entry (Format)</span><span class="sxs-lookup"><span data-stu-id="1ef24-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1ef24-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="1ef24-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1ef24-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="1ef24-107">Attributes and Elements</span></span>

<span data-ttu-id="1ef24-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `ScriptBlock` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="1ef24-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1ef24-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="1ef24-109">Attributes</span></span>

<span data-ttu-id="1ef24-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="1ef24-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1ef24-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="1ef24-111">Child Elements</span></span>

<span data-ttu-id="1ef24-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="1ef24-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1ef24-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="1ef24-113">Parent Elements</span></span>

|<span data-ttu-id="1ef24-114">Element</span><span class="sxs-lookup"><span data-stu-id="1ef24-114">Element</span></span>|<span data-ttu-id="1ef24-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="1ef24-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1ef24-116">SelectionCondition-element voor EntrySelectedBy voor List entry (indeling)</span><span class="sxs-lookup"><span data-stu-id="1ef24-116">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="1ef24-117">Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van deze lijst vermelding.</span><span class="sxs-lookup"><span data-stu-id="1ef24-117">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1ef24-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="1ef24-118">Text Value</span></span>

<span data-ttu-id="1ef24-119">Geef het script op dat wordt geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="1ef24-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="1ef24-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="1ef24-120">Remarks</span></span>

<span data-ttu-id="1ef24-121">Voor de selectie voorwaarde moet ten minste één script of eigenschaps naam worden opgegeven die moet worden geëvalueerd, maar kan niet beide worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="1ef24-121">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="1ef24-122">(Zie voor [waarden definiëren voor het gebruik van een weergave vermelding of-item](./defining-conditions-for-displaying-data.md)voor meer informatie over hoe selectie voorwaarden kunnen worden gebruikt.)</span><span class="sxs-lookup"><span data-stu-id="1ef24-122">(For more information about how selection conditions can be used, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).)</span></span>

<span data-ttu-id="1ef24-123">Zie [lijst weergave](./creating-a-list-view.md)voor meer informatie over de andere onderdelen van een lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="1ef24-123">For more information about the other components of a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1ef24-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="1ef24-124">See Also</span></span>

[<span data-ttu-id="1ef24-125">Element List entry (indeling)</span><span class="sxs-lookup"><span data-stu-id="1ef24-125">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="1ef24-126">Het element PropertyName voor SelectionCondition voor EntrySelectedBy voor List entry (indeling)</span><span class="sxs-lookup"><span data-stu-id="1ef24-126">PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="1ef24-127">SelectionCondition-element voor EntrySelectedBy voor List entry (indeling)</span><span class="sxs-lookup"><span data-stu-id="1ef24-127">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="1ef24-128">Lijst weergave</span><span class="sxs-lookup"><span data-stu-id="1ef24-128">List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="1ef24-129">Voor waarden definiëren voor het gebruik van een weergave vermelding of een item</span><span class="sxs-lookup"><span data-stu-id="1ef24-129">Defining Conditions for when a View Entry or Item is Used</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="1ef24-130">Een Windows Power shell-indeling en-type bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="1ef24-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
