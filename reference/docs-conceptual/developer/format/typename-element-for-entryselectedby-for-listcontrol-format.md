---
title: TypeName-element voor EntrySelectedBy voor ListControl (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 5e7b73db5aa597d96141454008c5c58b1827df24
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780216"
---
# <a name="typename-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="6c900-102">Het element TypeName voor EntrySelectedBy voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="6c900-102">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="6c900-103">Hiermee geeft u een .NET-type op dat gebruikmaakt van dit item van de lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="6c900-103">Specifies a .NET type that uses this entry of the list view.</span></span> <span data-ttu-id="6c900-104">Er is geen limiet voor het aantal typen dat kan worden opgegeven voor een vermelding in de lijst.</span><span class="sxs-lookup"><span data-stu-id="6c900-104">There is no limit to the number of types that can be specified for a list entry.</span></span>

<span data-ttu-id="6c900-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element van weer gave (indeling) bestand van ListControl element (indeling) (Format) List item (Format) element Entry element (indeling) EntrySelectedBy element voor List entry (Format) TypeName element voor EntrySelectedBy voor ListControl</span><span class="sxs-lookup"><span data-stu-id="6c900-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6c900-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="6c900-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6c900-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="6c900-107">Attributes and Elements</span></span>

<span data-ttu-id="6c900-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `TypeName` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="6c900-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6c900-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="6c900-109">Attributes</span></span>

<span data-ttu-id="6c900-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="6c900-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6c900-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="6c900-111">Child Elements</span></span>

<span data-ttu-id="6c900-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="6c900-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="6c900-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="6c900-113">Parent Elements</span></span>

|<span data-ttu-id="6c900-114">Element</span><span class="sxs-lookup"><span data-stu-id="6c900-114">Element</span></span>|<span data-ttu-id="6c900-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="6c900-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6c900-116">Element EntrySelectedBy voor List entry (indeling)</span><span class="sxs-lookup"><span data-stu-id="6c900-116">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="6c900-117">Hiermee definieert u de .NET-typen die gebruikmaken van deze lijst vermelding of de voor waarde die moet bestaan voor het gebruik van deze vermelding.</span><span class="sxs-lookup"><span data-stu-id="6c900-117">Defines the .NET types that use this list entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="6c900-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="6c900-118">Text Value</span></span>

<span data-ttu-id="6c900-119">Geef de volledig gekwalificeerde naam van het .NET-type op, zoals `System.IO.DirectoryInfo` .</span><span class="sxs-lookup"><span data-stu-id="6c900-119">Specify the fully-qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="6c900-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="6c900-120">Remarks</span></span>

<span data-ttu-id="6c900-121">Voor elke lijst vermelding moet ten minste één type naam, selectieset of selectie voorwaarde zijn gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="6c900-121">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="6c900-122">Zie [lijst weergave](./creating-a-list-view.md)voor meer informatie over het gebruik van dit element in een lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="6c900-122">For more information about how this element is used in a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="6c900-123">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="6c900-123">Example</span></span>

<span data-ttu-id="6c900-124">In het volgende voor beeld ziet u hoe u een selectieset kunt opgeven voor een vermelding van een lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="6c900-124">The following example shows how to specify a selection set for an entry of a list view.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>Nameof.NetType</TypeName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="6c900-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="6c900-125">See Also</span></span>

[<span data-ttu-id="6c900-126">Een lijstweergave maken</span><span class="sxs-lookup"><span data-stu-id="6c900-126">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="6c900-127">Element EntrySelectedBy voor List entry (indeling)</span><span class="sxs-lookup"><span data-stu-id="6c900-127">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="6c900-128">SelectionSetName-element voor EntrySelectedBy voor List entry (indeling)</span><span class="sxs-lookup"><span data-stu-id="6c900-128">SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="6c900-129">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="6c900-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
