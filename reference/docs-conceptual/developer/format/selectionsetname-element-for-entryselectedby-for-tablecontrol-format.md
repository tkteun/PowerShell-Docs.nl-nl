---
title: SelectionSetName-element voor EntrySelectedBy voor TableControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5dd0bd5d-f206-4cc6-a0f8-70700ee2c4b7
caps.latest.revision: 8
ms.openlocfilehash: 819906127e81355c45103ede85ef3608e1c1cfeb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72358849"
---
# <a name="selectionsetname-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="c93e5-102">Het element SelectionSetName voor EntrySelectedBy voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c93e5-102">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="c93e5-103">Hiermee geeft u een set .NET-typen op die gebruikmaken van dit item van de tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="c93e5-103">Specifies a set of .NET types the use this entry of the table view.</span></span> <span data-ttu-id="c93e5-104">Er is geen limiet voor het aantal selectie sets dat voor een vermelding kan worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="c93e5-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="c93e5-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element van weer gave (indeling) TableControl element (indeling) TableRowEntries element (indeling) TableRowEntry element (indeling) EntrySelectedBy element (indeling) SelectionSetName element voor EntrySelectedBy voor TableRowEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="c93e5-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format) SelectionSetName Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c93e5-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="c93e5-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c93e5-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="c93e5-107">Attributes and Elements</span></span>

<span data-ttu-id="c93e5-108">In de volgende secties worden kenmerken, onderliggende elementen en bovenliggende elementen beschreven.</span><span class="sxs-lookup"><span data-stu-id="c93e5-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="c93e5-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="c93e5-109">Attributes</span></span>

<span data-ttu-id="c93e5-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="c93e5-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c93e5-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="c93e5-111">Child Elements</span></span>

<span data-ttu-id="c93e5-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="c93e5-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c93e5-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="c93e5-113">Parent Elements</span></span>

|<span data-ttu-id="c93e5-114">Element</span><span class="sxs-lookup"><span data-stu-id="c93e5-114">Element</span></span>|<span data-ttu-id="c93e5-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="c93e5-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c93e5-116">EntrySelectedBy-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="c93e5-116">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="c93e5-117">Hiermee definieert u de .NET-typen die gebruikmaken van dit item of de voor waarde die voor deze vermelding moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="c93e5-117">Defines the .NET types that use this entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c93e5-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="c93e5-118">Text Value</span></span>

<span data-ttu-id="c93e5-119">Geef de naam op van de selectieset.</span><span class="sxs-lookup"><span data-stu-id="c93e5-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="c93e5-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="c93e5-120">Remarks</span></span>

<span data-ttu-id="c93e5-121">Selectie sets worden meestal gebruikt wanneer u een groep objecten wilt definiëren die worden gebruikt in meerdere weer gaven.</span><span class="sxs-lookup"><span data-stu-id="c93e5-121">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="c93e5-122">U kunt bijvoorbeeld een tabel weergave maken en een lijst weergave voor dezelfde set met objecten.</span><span class="sxs-lookup"><span data-stu-id="c93e5-122">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="c93e5-123">Zie [sets van objecten voor een weer gave definiëren](./defining-selection-sets.md)voor meer informatie over het definiëren van selectie sets.</span><span class="sxs-lookup"><span data-stu-id="c93e5-123">For more information about defining selection sets, see [Defining Sets of objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="c93e5-124">Als u een selectie reeks voor een vermelding opgeeft, kunt u geen type naam opgeven.</span><span class="sxs-lookup"><span data-stu-id="c93e5-124">If you specify a selection set for an entry, you cannot specify a type name.</span></span> <span data-ttu-id="c93e5-125">Zie voor meer informatie over het opgeven van een .NET-type [TypeName-element voor EntrySelectedBy voor TableRowEntry (Format)](./typename-element-for-entryselectedby-for-tablecontrol-format.md).</span><span class="sxs-lookup"><span data-stu-id="c93e5-125">For more information about how to specify a .NET type, see [TypeName Element for EntrySelectedBy for TableRowEntry (Format)](./typename-element-for-entryselectedby-for-tablecontrol-format.md).</span></span>

<span data-ttu-id="c93e5-126">Zie [een tabel weergave maken](./creating-a-table-view.md)voor meer informatie over de onderdelen van een tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="c93e5-126">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c93e5-127">Zie ook</span><span class="sxs-lookup"><span data-stu-id="c93e5-127">See Also</span></span>

[<span data-ttu-id="c93e5-128">EntrySelectedBy-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="c93e5-128">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="c93e5-129">Sets van objecten voor een weer gave definiëren</span><span class="sxs-lookup"><span data-stu-id="c93e5-129">Defining Sets of objects for a View</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="c93e5-130">Een tabel weergave maken</span><span class="sxs-lookup"><span data-stu-id="c93e5-130">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="c93e5-131">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="c93e5-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
