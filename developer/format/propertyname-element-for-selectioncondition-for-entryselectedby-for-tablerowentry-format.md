---
title: PropertyName-Element voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ba3b4d9b-2b8c-4a3a-8887-6c606eb9d490
caps.latest.revision: 10
ms.openlocfilehash: 48011950ed64e78a84292762f2c7779003dc59fd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064659"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format"></a><span data-ttu-id="79268-102">Het element PropertyName voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (opmaak)</span><span class="sxs-lookup"><span data-stu-id="79268-102">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

<span data-ttu-id="79268-103">Hiermee geeft u de .NET-eigenschap die de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="79268-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="79268-104">Als deze eigenschap is aanwezig, of wanneer deze wordt geëvalueerd naar `true`, de voorwaarde wordt voldaan en de vermelding in de tabel wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="79268-104">When this property is present or when it evaluates to `true`, the condition is met, and the table entry is used.</span></span>

<span data-ttu-id="79268-105">Configuratie Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) TableControl-Element (indeling) TableRowEntries-Element (indeling) TableRowEntry-Element (indeling) EntrySelectedBy Element voor TableRowEntry (indeling) SelectionCondition-Element voor EntrySelectedBy voor TableRowEntry (indeling) PropertyName-Element voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="79268-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="79268-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="79268-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="79268-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="79268-107">Attributes and Elements</span></span>

<span data-ttu-id="79268-108">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `PropertyName` element.</span><span class="sxs-lookup"><span data-stu-id="79268-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="79268-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="79268-109">Attributes</span></span>

<span data-ttu-id="79268-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="79268-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="79268-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="79268-111">Child Elements</span></span>

<span data-ttu-id="79268-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="79268-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="79268-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="79268-113">Parent Elements</span></span>

|<span data-ttu-id="79268-114">Element</span><span class="sxs-lookup"><span data-stu-id="79268-114">Element</span></span>|<span data-ttu-id="79268-115">Description</span><span class="sxs-lookup"><span data-stu-id="79268-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="79268-116">SelectionCondition-Element voor EntrySelectedBy voor TableRowEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="79268-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="79268-117">Hiermee definieert u de voorwaarde die moet aanwezig zijn voor de vermelding in deze tabel moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="79268-117">Defines the condition that must exist for this table entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="79268-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="79268-118">Text Value</span></span>

<span data-ttu-id="79268-119">Geef de naam van de .NET-eigenschap.</span><span class="sxs-lookup"><span data-stu-id="79268-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="79268-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="79268-120">Remarks</span></span>

<span data-ttu-id="79268-121">De selectievoorwaarde moet ten minste één eigenschap name of een scriptblok opgeven, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="79268-121">The selection condition must specify at least one property name or a script block, but cannot specify both.</span></span> <span data-ttu-id="79268-122">Zie voor meer informatie over hoe voorwaarden van de selectie kunnen worden gebruikt, [definiëren voorwaarden voor wanneer een item weergeven of Item wordt gebruikt](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="79268-122">For more information about how selection conditions can be used, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="79268-123">Zie voor meer informatie over de onderdelen van een tabelweergave [het maken van een tabelweergave](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="79268-123">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="79268-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="79268-124">See Also</span></span>

[<span data-ttu-id="79268-125">Het maken van een tabelweergave</span><span class="sxs-lookup"><span data-stu-id="79268-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="79268-126">Voorwaarden voor wanneer gegevens worden weergegeven definiëren</span><span class="sxs-lookup"><span data-stu-id="79268-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="79268-127">ScriptBlock-Element voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="79268-127">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="79268-128">SelectionCondition-Element voor EntrySelectedBy voor TableRowEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="79268-128">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="79268-129">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="79268-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
