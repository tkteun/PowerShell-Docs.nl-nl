---
title: TypeName-Element voor SelectionCondition voor EntrySelectedBy voor TableControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e97d56fb-4e35-447a-9282-26f10d0a4609
caps.latest.revision: 11
ms.openlocfilehash: fe65ac95cead7df0069ffdae666fb34b7309fbb6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847157"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="ad4cb-102">Het element TypeName voor SelectionCondition voor EntrySelectedBy voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="ad4cb-102">TypeName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="ad4cb-103">Hiermee geeft u een .NET-type dat de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="ad4cb-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="ad4cb-104">Wanneer dit type aanwezig is, wordt de voorwaarde wordt voldaan en wordt een rij in de tabel wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="ad4cb-104">When this type is present, the condition is met, and the table row is used.</span></span>

<span data-ttu-id="ad4cb-105">Configuratie Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) TableControl-Element (indeling) TableRowEntries-Element (indeling) TableRowEntry-Element (indeling) EntrySelectedBy Element voor TableRowEntry (indeling) SelectionCondition-Element voor EntrySelectedBy voor TableRowEntry (indeling) TypeName Element voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="ad4cb-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ad4cb-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="ad4cb-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ad4cb-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="ad4cb-107">Attributes and Elements</span></span>

<span data-ttu-id="ad4cb-108">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `TypeName` element.</span><span class="sxs-lookup"><span data-stu-id="ad4cb-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ad4cb-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="ad4cb-109">Attributes</span></span>

<span data-ttu-id="ad4cb-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="ad4cb-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ad4cb-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="ad4cb-111">Child Elements</span></span>

<span data-ttu-id="ad4cb-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="ad4cb-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ad4cb-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="ad4cb-113">Parent Elements</span></span>

|<span data-ttu-id="ad4cb-114">Element</span><span class="sxs-lookup"><span data-stu-id="ad4cb-114">Element</span></span>|<span data-ttu-id="ad4cb-115">Description</span><span class="sxs-lookup"><span data-stu-id="ad4cb-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ad4cb-116">SelectionCondition-Element voor EntrySelectedBy voor TableRowEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="ad4cb-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="ad4cb-117">Hiermee definieert u de voorwaarde die moet aanwezig zijn voor een rij in deze tabel moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="ad4cb-117">Defines the condition that must exist for this table row to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ad4cb-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="ad4cb-118">Text Value</span></span>

<span data-ttu-id="ad4cb-119">Geef de volledig gekwalificeerde naam van het .NET-type, bijvoorbeeld `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="ad4cb-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="ad4cb-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="ad4cb-120">Remarks</span></span>

<span data-ttu-id="ad4cb-121">De selectievoorwaarde een willekeurig aantal .NET-typen kunt opgeven of de selectie wordt ingesteld, maar niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="ad4cb-121">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span> <span data-ttu-id="ad4cb-122">Zie voor meer informatie over het gebruik van de voorwaarden van de selectie [definiëren voorwaarden voor wanneer een item weergeven of Item wordt gebruikt](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="ad4cb-122">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="ad4cb-123">Zie voor meer informatie over de onderdelen van een tabelweergave [het maken van een tabelweergave](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="ad4cb-123">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ad4cb-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="ad4cb-124">See Also</span></span>

[<span data-ttu-id="ad4cb-125">Het maken van een tabelweergave</span><span class="sxs-lookup"><span data-stu-id="ad4cb-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="ad4cb-126">Voorwaarden voor wanneer gegevens worden weergegeven definiëren</span><span class="sxs-lookup"><span data-stu-id="ad4cb-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="ad4cb-127">SelectionCondition-Element voor EntrySelectedBy voor TableRowEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="ad4cb-127">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="ad4cb-128">SelectionSetName-Element voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="ad4cb-128">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="ad4cb-129">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="ad4cb-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
