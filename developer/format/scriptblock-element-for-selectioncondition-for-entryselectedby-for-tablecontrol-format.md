---
title: ScriptBlock-Element voor SelectionCondition voor EntrySelectedBy voor TableControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b11fbcf-3426-48ae-9319-2c847969f723
caps.latest.revision: 10
ms.openlocfilehash: 7afc834e68ef332bee1e23da782fb5c5527fcf54
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076341"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="6cff2-102">Het element ScriptBlock voor SelectionCondition voor EntrySelectedBy voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="6cff2-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="6cff2-103">Hiermee geeft u het scriptblok waarmee de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="6cff2-103">Specifies the script block that triggers the condition.</span></span> <span data-ttu-id="6cff2-104">Wanneer dit script wordt geëvalueerd naar `true`, de voorwaarde wordt voldaan en de vermelding in de tabel wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="6cff2-104">When this script is evaluated to `true`, the condition is met, and the table entry is used.</span></span>

<span data-ttu-id="6cff2-105">Configuratie Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) TableControl-Element (indeling) TableRowEntries-Element (indeling) TableRowEntry-Element (indeling) EntrySelectedBy Element voor TableRowEntry (indeling) SelectionCondition-Element voor EntrySelectedBy voor TableRowEntry (indeling) ScriptBlock Element voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="6cff2-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6cff2-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="6cff2-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6cff2-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="6cff2-107">Attributes and Elements</span></span>

<span data-ttu-id="6cff2-108">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `ScriptBlock` element.</span><span class="sxs-lookup"><span data-stu-id="6cff2-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6cff2-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="6cff2-109">Attributes</span></span>

<span data-ttu-id="6cff2-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="6cff2-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6cff2-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="6cff2-111">Child Elements</span></span>

<span data-ttu-id="6cff2-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="6cff2-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="6cff2-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="6cff2-113">Parent Elements</span></span>

|<span data-ttu-id="6cff2-114">Element</span><span class="sxs-lookup"><span data-stu-id="6cff2-114">Element</span></span>|<span data-ttu-id="6cff2-115">Description</span><span class="sxs-lookup"><span data-stu-id="6cff2-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6cff2-116">SelectionCondition-Element voor EntrySelectedBy voor TableRowEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="6cff2-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="6cff2-117">Hiermee definieert u de voorwaarde die moet aanwezig zijn voor de vermelding in deze tabel moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="6cff2-117">Defines the condition that must exist for this table entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="6cff2-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="6cff2-118">Text Value</span></span>

<span data-ttu-id="6cff2-119">Geef het script dat wordt geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="6cff2-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="6cff2-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="6cff2-120">Remarks</span></span>

<span data-ttu-id="6cff2-121">De selectievoorwaarde moet ten minste één script blokkeren of de eigenschap naam opgeven, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="6cff2-121">The selection condition must specify at least one script block or property name, but cannot specify both.</span></span> <span data-ttu-id="6cff2-122">Zie voor meer informatie over het gebruik van de voorwaarden van de selectie [definiëren voorwaarden voor wanneer een item weergeven of Item wordt gebruikt](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="6cff2-122">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="6cff2-123">Zie voor meer informatie over de onderdelen van een tabelweergave [het maken van een tabelweergave](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="6cff2-123">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6cff2-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="6cff2-124">See Also</span></span>

[<span data-ttu-id="6cff2-125">Het maken van een tabelweergave</span><span class="sxs-lookup"><span data-stu-id="6cff2-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="6cff2-126">Voorwaarden voor wanneer gegevens worden weergegeven definiëren</span><span class="sxs-lookup"><span data-stu-id="6cff2-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="6cff2-127">PropertyName-Element voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="6cff2-127">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)

[<span data-ttu-id="6cff2-128">SelectionCondition-Element voor EntrySelectedBy voor TableRowEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="6cff2-128">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="6cff2-129">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="6cff2-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
