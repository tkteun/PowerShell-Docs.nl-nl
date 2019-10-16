---
title: Het element PropertyName voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ba3b4d9b-2b8c-4a3a-8887-6c606eb9d490
caps.latest.revision: 10
ms.openlocfilehash: 48011950ed64e78a84292762f2c7779003dc59fd
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355921"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format"></a><span data-ttu-id="152bf-102">Het element PropertyName voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (opmaak)</span><span class="sxs-lookup"><span data-stu-id="152bf-102">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

<span data-ttu-id="152bf-103">Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="152bf-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="152bf-104">Als deze eigenschap aanwezig is of als deze wordt geëvalueerd als `true`, wordt aan de voor waarde voldaan en wordt het tabel item gebruikt.</span><span class="sxs-lookup"><span data-stu-id="152bf-104">When this property is present or when it evaluates to `true`, the condition is met, and the table entry is used.</span></span>

<span data-ttu-id="152bf-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) TableControl element (indeling) TableRowEntries element (indeling) TableRowEntry element (indeling) EntrySelectedBy-element voor TableRowEntry (indeling) SelectionCondition-element voor EntrySelectedBy voor TableRowEntry (indeling) Property element voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="152bf-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="152bf-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="152bf-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="152bf-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="152bf-107">Attributes and Elements</span></span>

<span data-ttu-id="152bf-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `PropertyName` beschreven.</span><span class="sxs-lookup"><span data-stu-id="152bf-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="152bf-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="152bf-109">Attributes</span></span>

<span data-ttu-id="152bf-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="152bf-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="152bf-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="152bf-111">Child Elements</span></span>

<span data-ttu-id="152bf-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="152bf-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="152bf-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="152bf-113">Parent Elements</span></span>

|<span data-ttu-id="152bf-114">Element</span><span class="sxs-lookup"><span data-stu-id="152bf-114">Element</span></span>|<span data-ttu-id="152bf-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="152bf-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="152bf-116">SelectionCondition-element voor EntrySelectedBy voor TableRowEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="152bf-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="152bf-117">Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit tabel item.</span><span class="sxs-lookup"><span data-stu-id="152bf-117">Defines the condition that must exist for this table entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="152bf-118">Tekst waarde</span><span class="sxs-lookup"><span data-stu-id="152bf-118">Text Value</span></span>

<span data-ttu-id="152bf-119">Geef de .NET-eigenschaps naam op.</span><span class="sxs-lookup"><span data-stu-id="152bf-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="152bf-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="152bf-120">Remarks</span></span>

<span data-ttu-id="152bf-121">Voor de selectie voorwaarde moet ten minste één eigenschaps naam of een script blok worden opgegeven, maar kan niet beide worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="152bf-121">The selection condition must specify at least one property name or a script block, but cannot specify both.</span></span> <span data-ttu-id="152bf-122">Zie voor [waarden definiëren voor het gebruik van een weergave vermelding of-item](./defining-conditions-for-displaying-data.md)voor meer informatie over hoe selectie omstandigheden kunnen worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="152bf-122">For more information about how selection conditions can be used, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="152bf-123">Zie [een tabel weergave maken](./creating-a-table-view.md)voor meer informatie over de onderdelen van een tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="152bf-123">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="152bf-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="152bf-124">See Also</span></span>

[<span data-ttu-id="152bf-125">Een tabel weergave maken</span><span class="sxs-lookup"><span data-stu-id="152bf-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="152bf-126">Voor waarden definiëren voor wanneer gegevens worden weer gegeven</span><span class="sxs-lookup"><span data-stu-id="152bf-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="152bf-127">Script block-element voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="152bf-127">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="152bf-128">SelectionCondition-element voor EntrySelectedBy voor TableRowEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="152bf-128">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="152bf-129">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="152bf-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
