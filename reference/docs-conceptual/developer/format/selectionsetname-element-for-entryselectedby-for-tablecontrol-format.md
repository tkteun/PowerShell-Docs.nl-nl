---
ms.date: 09/13/2016
ms.topic: reference
title: Het element SelectionSetName voor EntrySelectedBy voor TableControl (opmaak)
description: Het element SelectionSetName voor EntrySelectedBy voor TableControl (opmaak)
ms.openlocfilehash: a5a395f718d0e1a2d7f33d120ce4fd2ff787cc34
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651782"
---
# <a name="selectionsetname-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="495cd-103">Het element SelectionSetName voor EntrySelectedBy voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="495cd-103">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="495cd-104">Hiermee geeft u een set .NET-typen op die gebruikmaken van dit item van de tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="495cd-104">Specifies a set of .NET types the use this entry of the table view.</span></span> <span data-ttu-id="495cd-105">Er is geen limiet voor het aantal selectie sets dat voor een vermelding kan worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="495cd-105">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="495cd-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element van weer gave (indeling) TableControl element (indeling) TableRowEntries element (indeling) TableRowEntry element (indeling) EntrySelectedBy element (indeling) SelectionSetName element voor EntrySelectedBy voor TableRowEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="495cd-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format) SelectionSetName Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="495cd-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="495cd-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="495cd-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="495cd-108">Attributes and Elements</span></span>

<span data-ttu-id="495cd-109">In de volgende secties worden kenmerken, onderliggende elementen en bovenliggende elementen beschreven.</span><span class="sxs-lookup"><span data-stu-id="495cd-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="495cd-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="495cd-110">Attributes</span></span>

<span data-ttu-id="495cd-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="495cd-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="495cd-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="495cd-112">Child Elements</span></span>

<span data-ttu-id="495cd-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="495cd-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="495cd-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="495cd-114">Parent Elements</span></span>

|<span data-ttu-id="495cd-115">Element</span><span class="sxs-lookup"><span data-stu-id="495cd-115">Element</span></span>|<span data-ttu-id="495cd-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="495cd-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="495cd-117">EntrySelectedBy-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="495cd-117">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="495cd-118">Hiermee definieert u de .NET-typen die gebruikmaken van dit item of de voor waarde die voor deze vermelding moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="495cd-118">Defines the .NET types that use this entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="495cd-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="495cd-119">Text Value</span></span>

<span data-ttu-id="495cd-120">Geef de naam op van de selectieset.</span><span class="sxs-lookup"><span data-stu-id="495cd-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="495cd-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="495cd-121">Remarks</span></span>

<span data-ttu-id="495cd-122">Selectie sets worden meestal gebruikt wanneer u een groep objecten wilt definiëren die worden gebruikt in meerdere weer gaven.</span><span class="sxs-lookup"><span data-stu-id="495cd-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="495cd-123">U kunt bijvoorbeeld een tabel weergave maken en een lijst weergave voor dezelfde set met objecten.</span><span class="sxs-lookup"><span data-stu-id="495cd-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="495cd-124">Zie [sets van objecten voor een weer gave definiëren](./defining-selection-sets.md)voor meer informatie over het definiëren van selectie sets.</span><span class="sxs-lookup"><span data-stu-id="495cd-124">For more information about defining selection sets, see [Defining Sets of objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="495cd-125">Als u een selectie reeks voor een vermelding opgeeft, kunt u geen type naam opgeven.</span><span class="sxs-lookup"><span data-stu-id="495cd-125">If you specify a selection set for an entry, you cannot specify a type name.</span></span> <span data-ttu-id="495cd-126">Zie voor meer informatie over het opgeven van een .NET-type [TypeName-element voor EntrySelectedBy voor TableRowEntry (Format)](./typename-element-for-entryselectedby-for-tablecontrol-format.md).</span><span class="sxs-lookup"><span data-stu-id="495cd-126">For more information about how to specify a .NET type, see [TypeName Element for EntrySelectedBy for TableRowEntry (Format)](./typename-element-for-entryselectedby-for-tablecontrol-format.md).</span></span>

<span data-ttu-id="495cd-127">Zie [een tabel weergave maken](./creating-a-table-view.md)voor meer informatie over de onderdelen van een tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="495cd-127">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="495cd-128">Zie ook</span><span class="sxs-lookup"><span data-stu-id="495cd-128">See Also</span></span>

[<span data-ttu-id="495cd-129">EntrySelectedBy-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="495cd-129">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="495cd-130">Sets van objecten voor een weer gave definiëren</span><span class="sxs-lookup"><span data-stu-id="495cd-130">Defining Sets of objects for a View</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="495cd-131">Een tabelweergave maken</span><span class="sxs-lookup"><span data-stu-id="495cd-131">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="495cd-132">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="495cd-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
