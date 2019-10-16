---
title: EntrySelectedBy-element voor TableRowEntry voor TableControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49623fcf-1238-4d20-a7ce-238d47d9d565
caps.latest.revision: 15
ms.openlocfilehash: 9302bfed0324773cb98d698acdcf608f34ee19c1
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72354759"
---
# <a name="entryselectedby-element-for-tablerowentry--for-tablecontrol-format"></a><span data-ttu-id="e5714-102">Het element EntrySelectedBy voor TableRowEntry voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="e5714-102">EntrySelectedBy Element for TableRowEntry  for TableControl (Format)</span></span>

<span data-ttu-id="e5714-103">Hiermee worden de .NET-typen gedefinieerd die gebruikmaken van deze definitie van de tabel weergave of de voor waarde die voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="e5714-103">Defines the .NET types that use this definition of the table view or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="e5714-104">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) TableControl element (indeling) TableRowEntries element (indeling) TableRowEntry element (indeling) EntrySelectedBy element (indeling)</span><span class="sxs-lookup"><span data-stu-id="e5714-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e5714-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="e5714-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e5714-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="e5714-106">Attributes and Elements</span></span>

<span data-ttu-id="e5714-107">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `EntrySelectedBy` beschreven.</span><span class="sxs-lookup"><span data-stu-id="e5714-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e5714-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="e5714-108">Attributes</span></span>

<span data-ttu-id="e5714-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="e5714-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e5714-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="e5714-110">Child Elements</span></span>

|<span data-ttu-id="e5714-111">Element</span><span class="sxs-lookup"><span data-stu-id="e5714-111">Element</span></span>|<span data-ttu-id="e5714-112">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e5714-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e5714-113">SelectionCondition-element voor EntrySelectedBy voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="e5714-113">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="e5714-114">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="e5714-114">Optional element.</span></span><br /><br /> <span data-ttu-id="e5714-115">Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van deze tabel weergave definitie.</span><span class="sxs-lookup"><span data-stu-id="e5714-115">Defines the condition that must exist for this table view definition to be used.</span></span>|
|[<span data-ttu-id="e5714-116">SelectionSetName-element voor EntrySelectedBy voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="e5714-116">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="e5714-117">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="e5714-117">Optional element.</span></span><br /><br /> <span data-ttu-id="e5714-118">Hiermee geeft u een set .NET-typen op die gebruikmaken van deze tabel weergave definitie.</span><span class="sxs-lookup"><span data-stu-id="e5714-118">Specifies a set of .NET types that use this table view definition.</span></span>|
|[<span data-ttu-id="e5714-119">TypeName-element voor EntrySelectedBy voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="e5714-119">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>](./typename-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="e5714-120">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="e5714-120">Optional element.</span></span><br /><br /> <span data-ttu-id="e5714-121">Hiermee geeft u een .NET-type op dat gebruikmaakt van deze tabel weergave definitie.</span><span class="sxs-lookup"><span data-stu-id="e5714-121">Specifies a .NET type that uses this table view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e5714-122">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="e5714-122">Parent Elements</span></span>

|<span data-ttu-id="e5714-123">Element</span><span class="sxs-lookup"><span data-stu-id="e5714-123">Element</span></span>|<span data-ttu-id="e5714-124">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e5714-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e5714-125">TableRowEntry-element voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="e5714-125">TableRowEntry Element for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|<span data-ttu-id="e5714-126">Hiermee worden de gegevens gedefinieerd die worden weer gegeven in een rij van de tabel.</span><span class="sxs-lookup"><span data-stu-id="e5714-126">Defines the data that is displayed in a row of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e5714-127">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="e5714-127">Remarks</span></span>

<span data-ttu-id="e5714-128">U moet ten minste één type, selectieset of selectie voorwaarde opgeven voor een tabel weergave definitie.</span><span class="sxs-lookup"><span data-stu-id="e5714-128">You must specify at least one type, selection set, or selection condition for a table view definition.</span></span> <span data-ttu-id="e5714-129">Er is geen maximum limiet voor het aantal onderliggende elementen dat u kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="e5714-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="e5714-130">De selectie voorwaarden worden gebruikt voor het definiëren van een voor waarde die voor de definitie moet bestaan, zoals wanneer een object een specifieke eigenschap heeft of een bepaalde eigenschaps waarde of een script het `true` evalueert.</span><span class="sxs-lookup"><span data-stu-id="e5714-130">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="e5714-131">Zie voor [waarden definiëren voor het gebruik van een weergave vermelding of-item](./defining-conditions-for-displaying-data.md)voor meer informatie over selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="e5714-131">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="e5714-132">Zie [een tabel weergave maken](./creating-a-table-view.md)voor meer informatie over de onderdelen van een tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="e5714-132">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="e5714-133">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="e5714-133">Example</span></span>

<span data-ttu-id="e5714-134">In het volgende voor beeld ziet u een `TableRowEntry`-element dat wordt gebruikt om de eigenschappen van het object [System. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) weer te geven.</span><span class="sxs-lookup"><span data-stu-id="e5714-134">The following example shows a `TableRowEntry` element that is used to display the properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </EntrySelectedBy>
  <TableColumnItems>
    <TableColumnItem>
      <PropertyName>PropertyForFirstColumn</PropertyName>
    </TableColumnItem>
    <TableColumnItem>
      <PropertyName>PropertyForSecondColumn</PropertyName>
    </TableColumnItem>
  </TableColumnItems>
</TableRowEntry>
```

## <a name="see-also"></a><span data-ttu-id="e5714-135">Zie ook</span><span class="sxs-lookup"><span data-stu-id="e5714-135">See Also</span></span>

[<span data-ttu-id="e5714-136">Een tabel weergave maken</span><span class="sxs-lookup"><span data-stu-id="e5714-136">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="e5714-137">SelectionCondition-element voor EntrySelectedBy voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="e5714-137">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="e5714-138">SelectionSetName-element voor EntrySelectedBy voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="e5714-138">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="e5714-139">TableRowEntry-element voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="e5714-139">TableRowEntry Element for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[<span data-ttu-id="e5714-140">TypeName-element voor EntrySelectedBy voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="e5714-140">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>](./typename-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="e5714-141">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="e5714-141">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
