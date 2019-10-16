---
title: Script block-element voor SelectionCondition voor EntrySelectedBy voor TableControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b11fbcf-3426-48ae-9319-2c847969f723
caps.latest.revision: 10
ms.openlocfilehash: 7afc834e68ef332bee1e23da782fb5c5527fcf54
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72358917"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="7c1cd-102">Het element ScriptBlock voor SelectionCondition voor EntrySelectedBy voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7c1cd-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="7c1cd-103">Hiermee geeft u het script blok op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="7c1cd-103">Specifies the script block that triggers the condition.</span></span> <span data-ttu-id="7c1cd-104">Wanneer dit script wordt geëvalueerd als `true`, wordt aan de voor waarde voldaan en wordt het tabel item gebruikt.</span><span class="sxs-lookup"><span data-stu-id="7c1cd-104">When this script is evaluated to `true`, the condition is met, and the table entry is used.</span></span>

<span data-ttu-id="7c1cd-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) TableControl element (indeling) TableRowEntries element (indeling) TableRowEntry element (indeling) EntrySelectedBy-element voor TableRowEntry (indeling) SelectionCondition-element voor EntrySelectedBy voor TableRowEntry (Format) script block element voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="7c1cd-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7c1cd-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="7c1cd-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7c1cd-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="7c1cd-107">Attributes and Elements</span></span>

<span data-ttu-id="7c1cd-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `ScriptBlock` beschreven.</span><span class="sxs-lookup"><span data-stu-id="7c1cd-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7c1cd-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="7c1cd-109">Attributes</span></span>

<span data-ttu-id="7c1cd-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="7c1cd-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7c1cd-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="7c1cd-111">Child Elements</span></span>

<span data-ttu-id="7c1cd-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="7c1cd-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7c1cd-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="7c1cd-113">Parent Elements</span></span>

|<span data-ttu-id="7c1cd-114">Element</span><span class="sxs-lookup"><span data-stu-id="7c1cd-114">Element</span></span>|<span data-ttu-id="7c1cd-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="7c1cd-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7c1cd-116">SelectionCondition-element voor EntrySelectedBy voor TableRowEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="7c1cd-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="7c1cd-117">Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit tabel item.</span><span class="sxs-lookup"><span data-stu-id="7c1cd-117">Defines the condition that must exist for this table entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="7c1cd-118">Tekst waarde</span><span class="sxs-lookup"><span data-stu-id="7c1cd-118">Text Value</span></span>

<span data-ttu-id="7c1cd-119">Geef het script op dat wordt geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="7c1cd-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="7c1cd-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="7c1cd-120">Remarks</span></span>

<span data-ttu-id="7c1cd-121">Voor de selectie voorwaarde moet ten minste één script blok of een eigenschaps naam worden opgegeven, maar kan niet beide worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="7c1cd-121">The selection condition must specify at least one script block or property name, but cannot specify both.</span></span> <span data-ttu-id="7c1cd-122">Zie voor [waarden definiëren voor wanneer een weergave vermelding of-item wordt gebruikt](./defining-conditions-for-displaying-data.md)voor meer informatie over het gebruik van selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="7c1cd-122">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="7c1cd-123">Zie [een tabel weergave maken](./creating-a-table-view.md)voor meer informatie over de onderdelen van een tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="7c1cd-123">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7c1cd-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="7c1cd-124">See Also</span></span>

[<span data-ttu-id="7c1cd-125">Een tabel weergave maken</span><span class="sxs-lookup"><span data-stu-id="7c1cd-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="7c1cd-126">Voor waarden definiëren voor wanneer gegevens worden weer gegeven</span><span class="sxs-lookup"><span data-stu-id="7c1cd-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="7c1cd-127">Het element PropertyName voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="7c1cd-127">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)

[<span data-ttu-id="7c1cd-128">SelectionCondition-element voor EntrySelectedBy voor TableRowEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="7c1cd-128">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="7c1cd-129">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="7c1cd-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
