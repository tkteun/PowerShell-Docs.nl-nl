---
title: Script block-element voor SelectionCondition voor EntrySelectedBy voor ListControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a1adad7-e864-4892-9d26-a6476a9698d2
caps.latest.revision: 7
ms.openlocfilehash: b65d953169f6daf15fb617ce4d0303cf4cb584ee
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72358926"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="ebe45-102">Het element ScriptBlock voor SelectionCondition voor EntrySelectedBy voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="ebe45-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="ebe45-103">Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="ebe45-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="ebe45-104">Wanneer dit script wordt geëvalueerd als `true`, wordt aan de voor waarde voldaan en wordt de vermelding in de lijst gebruikt.</span><span class="sxs-lookup"><span data-stu-id="ebe45-104">When this script is evaluated to `true`, the condition is met, and the list entry is used.</span></span>

<span data-ttu-id="ebe45-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) bestand van ListControl element (indeling) item type-element (indeling) EntrySelectedBy element (Format) voor List entry (Format) SelectionCondition element voor EntrySelectedBy voor List entry (Format) script block-element voor SelectionCondition voor EntrySelectedBy voor List entry (Format)</span><span class="sxs-lookup"><span data-stu-id="ebe45-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ebe45-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="ebe45-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ebe45-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="ebe45-107">Attributes and Elements</span></span>

<span data-ttu-id="ebe45-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `ScriptBlock` beschreven.</span><span class="sxs-lookup"><span data-stu-id="ebe45-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ebe45-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="ebe45-109">Attributes</span></span>

<span data-ttu-id="ebe45-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="ebe45-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ebe45-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="ebe45-111">Child Elements</span></span>

<span data-ttu-id="ebe45-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="ebe45-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ebe45-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="ebe45-113">Parent Elements</span></span>

|<span data-ttu-id="ebe45-114">Element</span><span class="sxs-lookup"><span data-stu-id="ebe45-114">Element</span></span>|<span data-ttu-id="ebe45-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="ebe45-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ebe45-116">SelectionCondition-element voor EntrySelectedBy voor List entry (indeling)</span><span class="sxs-lookup"><span data-stu-id="ebe45-116">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="ebe45-117">Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van deze lijst vermelding.</span><span class="sxs-lookup"><span data-stu-id="ebe45-117">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ebe45-118">Tekst waarde</span><span class="sxs-lookup"><span data-stu-id="ebe45-118">Text Value</span></span>

<span data-ttu-id="ebe45-119">Geef het script op dat wordt geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="ebe45-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="ebe45-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="ebe45-120">Remarks</span></span>

<span data-ttu-id="ebe45-121">Voor de selectie voorwaarde moet ten minste één script of eigenschaps naam worden opgegeven die moet worden geëvalueerd, maar kan niet beide worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="ebe45-121">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="ebe45-122">(Zie voor [waarden definiëren voor het gebruik van een weergave vermelding of-item](./defining-conditions-for-displaying-data.md)voor meer informatie over hoe selectie voorwaarden kunnen worden gebruikt.)</span><span class="sxs-lookup"><span data-stu-id="ebe45-122">(For more information about how selection conditions can be used, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).)</span></span>

<span data-ttu-id="ebe45-123">Zie [lijst weergave](./creating-a-list-view.md)voor meer informatie over de andere onderdelen van een lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="ebe45-123">For more information about the other components of a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ebe45-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="ebe45-124">See Also</span></span>

[<span data-ttu-id="ebe45-125">Element List entry (indeling)</span><span class="sxs-lookup"><span data-stu-id="ebe45-125">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="ebe45-126">Het element PropertyName voor SelectionCondition voor EntrySelectedBy voor List entry (indeling)</span><span class="sxs-lookup"><span data-stu-id="ebe45-126">PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="ebe45-127">SelectionCondition-element voor EntrySelectedBy voor List entry (indeling)</span><span class="sxs-lookup"><span data-stu-id="ebe45-127">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="ebe45-128">Lijst weergave</span><span class="sxs-lookup"><span data-stu-id="ebe45-128">List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="ebe45-129">Voor waarden definiëren voor het gebruik van een weergave vermelding of een item</span><span class="sxs-lookup"><span data-stu-id="ebe45-129">Defining Conditions for when a View Entry or Item is Used</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="ebe45-130">Een Windows Power shell-indeling en-type bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="ebe45-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
