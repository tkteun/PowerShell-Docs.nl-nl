---
title: TypeName-element voor EntrySelectedBy voor ListControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33c7345c-b808-4c1e-bd54-cb870b407432
caps.latest.revision: 14
ms.openlocfilehash: 0f7216d4dcc0380bceb47ea7c15b3d4a7e5ceeb2
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72353583"
---
# <a name="typename-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="0e249-102">Het element TypeName voor EntrySelectedBy voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="0e249-102">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="0e249-103">Hiermee geeft u een .NET-type op dat gebruikmaakt van dit item van de lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="0e249-103">Specifies a .NET type that uses this entry of the list view.</span></span> <span data-ttu-id="0e249-104">Er is geen limiet voor het aantal typen dat kan worden opgegeven voor een vermelding in de lijst.</span><span class="sxs-lookup"><span data-stu-id="0e249-104">There is no limit to the number of types that can be specified for a list entry.</span></span>

<span data-ttu-id="0e249-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) bestand van ListControl element (indeling) item type-element (indeling) EntrySelectedBy element (Format) voor List Entry-element (Format) voor EntrySelectedBy voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="0e249-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0e249-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="0e249-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0e249-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="0e249-107">Attributes and Elements</span></span>

<span data-ttu-id="0e249-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `TypeName` beschreven.</span><span class="sxs-lookup"><span data-stu-id="0e249-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0e249-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="0e249-109">Attributes</span></span>

<span data-ttu-id="0e249-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="0e249-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0e249-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="0e249-111">Child Elements</span></span>

<span data-ttu-id="0e249-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="0e249-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0e249-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="0e249-113">Parent Elements</span></span>

|<span data-ttu-id="0e249-114">Element</span><span class="sxs-lookup"><span data-stu-id="0e249-114">Element</span></span>|<span data-ttu-id="0e249-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="0e249-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0e249-116">Element EntrySelectedBy voor List entry (indeling)</span><span class="sxs-lookup"><span data-stu-id="0e249-116">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="0e249-117">Hiermee definieert u de .NET-typen die gebruikmaken van deze lijst vermelding of de voor waarde die moet bestaan voor het gebruik van deze vermelding.</span><span class="sxs-lookup"><span data-stu-id="0e249-117">Defines the .NET types that use this list entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="0e249-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="0e249-118">Text Value</span></span>

<span data-ttu-id="0e249-119">Geef de volledig gekwalificeerde naam van het .NET-type op, zoals `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="0e249-119">Specify the fully-qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="0e249-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="0e249-120">Remarks</span></span>

<span data-ttu-id="0e249-121">Voor elke lijst vermelding moet ten minste één type naam, selectieset of selectie voorwaarde zijn gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="0e249-121">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="0e249-122">Zie [lijst weergave](./creating-a-list-view.md)voor meer informatie over het gebruik van dit element in een lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="0e249-122">For more information about how this element is used in a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="0e249-123">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="0e249-123">Example</span></span>

<span data-ttu-id="0e249-124">In het volgende voor beeld ziet u hoe u een selectieset kunt opgeven voor een vermelding van een lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="0e249-124">The following example shows how to specify a selection set for an entry of a list view.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>Nameof.NetType</TypeName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="0e249-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="0e249-125">See Also</span></span>

[<span data-ttu-id="0e249-126">Een lijst weergave maken</span><span class="sxs-lookup"><span data-stu-id="0e249-126">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="0e249-127">Element EntrySelectedBy voor List entry (indeling)</span><span class="sxs-lookup"><span data-stu-id="0e249-127">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="0e249-128">SelectionSetName-element voor EntrySelectedBy voor List entry (indeling)</span><span class="sxs-lookup"><span data-stu-id="0e249-128">SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="0e249-129">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="0e249-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
