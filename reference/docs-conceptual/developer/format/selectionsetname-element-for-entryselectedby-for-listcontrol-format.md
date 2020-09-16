---
title: SelectionSetName-element voor EntrySelectedBy voor ListControl (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 4315d81da4ceeb7a5b171087434ae15fb09e6592
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785265"
---
# <a name="selectionsetname-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="34286-102">Het element SelectionSetName voor EntrySelectedBy voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="34286-102">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="34286-103">Hiermee geeft u een set .NET-objecten voor de lijst vermelding op.</span><span class="sxs-lookup"><span data-stu-id="34286-103">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="34286-104">Er is geen limiet voor het aantal selectie sets dat voor een vermelding kan worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="34286-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="34286-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) bestand van ListControl element (indeling) item type element (indeling) EntrySelectedBy element (Format) element list item (Format) voor List entry (Format) SelectionSetName element voor de List entry (Format)</span><span class="sxs-lookup"><span data-stu-id="34286-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="34286-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="34286-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="34286-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="34286-107">Attributes and Elements</span></span>

<span data-ttu-id="34286-108">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `SelectionSetName` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="34286-108">The following sections describe attributes, child elements, and parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="34286-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="34286-109">Attributes</span></span>

<span data-ttu-id="34286-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="34286-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="34286-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="34286-111">Child Elements</span></span>

<span data-ttu-id="34286-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="34286-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="34286-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="34286-113">Parent Elements</span></span>

|<span data-ttu-id="34286-114">Element</span><span class="sxs-lookup"><span data-stu-id="34286-114">Element</span></span>|<span data-ttu-id="34286-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="34286-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="34286-116">Element EntrySelectedBy voor List entry (indeling)</span><span class="sxs-lookup"><span data-stu-id="34286-116">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="34286-117">Hiermee definieert u de .NET-typen die gebruikmaken van deze lijst vermelding of de voor waarde die moet bestaan voor het gebruik van deze vermelding.</span><span class="sxs-lookup"><span data-stu-id="34286-117">Defines the .NET types that use this list entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="34286-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="34286-118">Text Value</span></span>

<span data-ttu-id="34286-119">Geef de naam op van de selectieset.</span><span class="sxs-lookup"><span data-stu-id="34286-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="34286-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="34286-120">Remarks</span></span>

<span data-ttu-id="34286-121">Voor elke lijst vermelding moet ten minste één type naam, selectieset of selectie voorwaarde zijn gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="34286-121">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="34286-122">Selectie sets worden meestal gebruikt wanneer u een groep objecten wilt definiëren die worden gebruikt in meerdere weer gaven.</span><span class="sxs-lookup"><span data-stu-id="34286-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="34286-123">U kunt bijvoorbeeld een tabel weergave maken en een lijst weergave voor dezelfde set met objecten.</span><span class="sxs-lookup"><span data-stu-id="34286-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="34286-124">Zie [sets van objecten voor een weer gave definiëren](./defining-selection-sets.md)voor meer informatie over het definiëren van selectie sets.</span><span class="sxs-lookup"><span data-stu-id="34286-124">For more information about defining selection sets, see [Defining Sets of objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="34286-125">Zie [een lijst weergave maken](./creating-a-list-view.md)voor meer informatie over de onderdelen van een lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="34286-125">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="34286-126">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="34286-126">Example</span></span>

<span data-ttu-id="34286-127">In het volgende voor beeld ziet u hoe u een selectieset kunt opgeven voor een vermelding van een lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="34286-127">The following example shows how to specify a selection set for an entry of a list view.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="34286-128">Zie ook</span><span class="sxs-lookup"><span data-stu-id="34286-128">See Also</span></span>

[<span data-ttu-id="34286-129">Een lijstweergave maken</span><span class="sxs-lookup"><span data-stu-id="34286-129">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="34286-130">Element EntrySelectedBy voor List entry (indeling)</span><span class="sxs-lookup"><span data-stu-id="34286-130">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="34286-131">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="34286-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
