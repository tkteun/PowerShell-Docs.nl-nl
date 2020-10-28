---
ms.date: 09/13/2016
ms.topic: reference
title: Het element TypeName voor EntrySelectedBy voor ListControl (opmaak)
description: Het element TypeName voor EntrySelectedBy voor ListControl (opmaak)
ms.openlocfilehash: 6fc5a2385fde3140abbc984e3da6a4dda483b2a8
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92645662"
---
# <a name="typename-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="3c88f-103">Het element TypeName voor EntrySelectedBy voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="3c88f-103">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="3c88f-104">Hiermee geeft u een .NET-type op dat gebruikmaakt van dit item van de lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="3c88f-104">Specifies a .NET type that uses this entry of the list view.</span></span> <span data-ttu-id="3c88f-105">Er is geen limiet voor het aantal typen dat kan worden opgegeven voor een vermelding in de lijst.</span><span class="sxs-lookup"><span data-stu-id="3c88f-105">There is no limit to the number of types that can be specified for a list entry.</span></span>

<span data-ttu-id="3c88f-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element van weer gave (indeling) bestand van ListControl element (indeling) (Format) List item (Format) element Entry element (indeling) EntrySelectedBy element voor List entry (Format) TypeName element voor EntrySelectedBy voor ListControl</span><span class="sxs-lookup"><span data-stu-id="3c88f-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3c88f-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="3c88f-107">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3c88f-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="3c88f-108">Attributes and Elements</span></span>

<span data-ttu-id="3c88f-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `TypeName` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="3c88f-109">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3c88f-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="3c88f-110">Attributes</span></span>

<span data-ttu-id="3c88f-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="3c88f-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3c88f-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="3c88f-112">Child Elements</span></span>

<span data-ttu-id="3c88f-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="3c88f-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="3c88f-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="3c88f-114">Parent Elements</span></span>

|<span data-ttu-id="3c88f-115">Element</span><span class="sxs-lookup"><span data-stu-id="3c88f-115">Element</span></span>|<span data-ttu-id="3c88f-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="3c88f-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3c88f-117">Element EntrySelectedBy voor List entry (indeling)</span><span class="sxs-lookup"><span data-stu-id="3c88f-117">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="3c88f-118">Hiermee definieert u de .NET-typen die gebruikmaken van deze lijst vermelding of de voor waarde die moet bestaan voor het gebruik van deze vermelding.</span><span class="sxs-lookup"><span data-stu-id="3c88f-118">Defines the .NET types that use this list entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="3c88f-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="3c88f-119">Text Value</span></span>

<span data-ttu-id="3c88f-120">Geef de volledig gekwalificeerde naam van het .NET-type op, zoals `System.IO.DirectoryInfo` .</span><span class="sxs-lookup"><span data-stu-id="3c88f-120">Specify the fully-qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="3c88f-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="3c88f-121">Remarks</span></span>

<span data-ttu-id="3c88f-122">Voor elke lijst vermelding moet ten minste één type naam, selectieset of selectie voorwaarde zijn gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="3c88f-122">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="3c88f-123">Zie [lijst weergave](./creating-a-list-view.md)voor meer informatie over het gebruik van dit element in een lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="3c88f-123">For more information about how this element is used in a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="3c88f-124">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="3c88f-124">Example</span></span>

<span data-ttu-id="3c88f-125">In het volgende voor beeld ziet u hoe u een selectieset kunt opgeven voor een vermelding van een lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="3c88f-125">The following example shows how to specify a selection set for an entry of a list view.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>Nameof.NetType</TypeName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="3c88f-126">Zie ook</span><span class="sxs-lookup"><span data-stu-id="3c88f-126">See Also</span></span>

[<span data-ttu-id="3c88f-127">Een lijstweergave maken</span><span class="sxs-lookup"><span data-stu-id="3c88f-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="3c88f-128">Element EntrySelectedBy voor List entry (indeling)</span><span class="sxs-lookup"><span data-stu-id="3c88f-128">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="3c88f-129">SelectionSetName-element voor EntrySelectedBy voor List entry (indeling)</span><span class="sxs-lookup"><span data-stu-id="3c88f-129">SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="3c88f-130">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="3c88f-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
