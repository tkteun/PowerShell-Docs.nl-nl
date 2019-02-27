---
title: SelectionSetName-Element voor EntrySelectedBy voor TableControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5dd0bd5d-f206-4cc6-a0f8-70700ee2c4b7
caps.latest.revision: 8
ms.openlocfilehash: 819906127e81355c45103ede85ef3608e1c1cfeb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846877"
---
# <a name="selectionsetname-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="d577a-102">Het element SelectionSetName voor EntrySelectedBy voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="d577a-102">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="d577a-103">Hiermee geeft u dat een set met .NET typen het gebruik van deze vermelding van de tabelweergave.</span><span class="sxs-lookup"><span data-stu-id="d577a-103">Specifies a set of .NET types the use this entry of the table view.</span></span> <span data-ttu-id="d577a-104">Er is geen limiet voor het aantal selectiesets die kan worden opgegeven voor een vermelding.</span><span class="sxs-lookup"><span data-stu-id="d577a-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="d577a-105">Configuratie Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) TableControl-Element (indeling) TableRowEntries-Element (indeling) TableRowEntry-Element (indeling) EntrySelectedBy-Element (indeling) SelectionSetName-Element voor EntrySelectedBy voor TableRowEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="d577a-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format) SelectionSetName Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d577a-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="d577a-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d577a-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="d577a-107">Attributes and Elements</span></span>

<span data-ttu-id="d577a-108">De volgende secties beschrijven kenmerken, elementen van de onderliggende en bovenliggende elementen.</span><span class="sxs-lookup"><span data-stu-id="d577a-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="d577a-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="d577a-109">Attributes</span></span>

<span data-ttu-id="d577a-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="d577a-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d577a-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="d577a-111">Child Elements</span></span>

<span data-ttu-id="d577a-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="d577a-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d577a-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="d577a-113">Parent Elements</span></span>

|<span data-ttu-id="d577a-114">Element</span><span class="sxs-lookup"><span data-stu-id="d577a-114">Element</span></span>|<span data-ttu-id="d577a-115">Description</span><span class="sxs-lookup"><span data-stu-id="d577a-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d577a-116">EntrySelectedBy-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="d577a-116">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="d577a-117">Hiermee definieert u de .NET-typen die gebruikmaken van deze vermelding of de voorwaarde die moet aanwezig zijn voor dit item moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="d577a-117">Defines the .NET types that use this entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d577a-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="d577a-118">Text Value</span></span>

<span data-ttu-id="d577a-119">Geef de naam van de selectie is ingesteld.</span><span class="sxs-lookup"><span data-stu-id="d577a-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="d577a-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="d577a-120">Remarks</span></span>

<span data-ttu-id="d577a-121">Selectiesets worden meestal gebruikt wanneer u wilt definiëren van een groep objecten die worden gebruikt in meerdere weergaven.</span><span class="sxs-lookup"><span data-stu-id="d577a-121">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="d577a-122">Bijvoorbeeld, als u wilt weergeven als een tabel en een lijst weergeven voor dezelfde set objecten maken.</span><span class="sxs-lookup"><span data-stu-id="d577a-122">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="d577a-123">Zie voor meer informatie over het definiëren van selectiesets [van objecten voor een weergave definiëren ingesteld](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="d577a-123">For more information about defining selection sets, see [Defining Sets of objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="d577a-124">Als u een selectie instellen voor een vermelding opgeeft, kunt u de typenaam van een kan niet opgeven.</span><span class="sxs-lookup"><span data-stu-id="d577a-124">If you specify a selection set for an entry, you cannot specify a type name.</span></span> <span data-ttu-id="d577a-125">Zie voor meer informatie over het opgeven van een .NET-type [TypeName-Element voor EntrySelectedBy voor TableRowEntry (indeling)](./typename-element-for-entryselectedby-for-tablecontrol-format.md).</span><span class="sxs-lookup"><span data-stu-id="d577a-125">For more information about how to specify a .NET type, see [TypeName Element for EntrySelectedBy for TableRowEntry (Format)](./typename-element-for-entryselectedby-for-tablecontrol-format.md).</span></span>

<span data-ttu-id="d577a-126">Zie voor meer informatie over de onderdelen van een tabelweergave [het maken van een tabelweergave](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="d577a-126">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d577a-127">Zie ook</span><span class="sxs-lookup"><span data-stu-id="d577a-127">See Also</span></span>

[<span data-ttu-id="d577a-128">EntrySelectedBy-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="d577a-128">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="d577a-129">Sets van objecten voor een weergave definiëren</span><span class="sxs-lookup"><span data-stu-id="d577a-129">Defining Sets of objects for a View</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="d577a-130">Het maken van een tabelweergave</span><span class="sxs-lookup"><span data-stu-id="d577a-130">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="d577a-131">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="d577a-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
