---
ms.date: 09/13/2016
ms.topic: reference
title: Het element EntrySelectedBy voor TableRowEntry voor TableControl (opmaak)
description: Het element EntrySelectedBy voor TableRowEntry voor TableControl (opmaak)
ms.openlocfilehash: 1b7fc60b6fa9864b66e9edfebb3e4a86e287f3f8
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92645905"
---
# <a name="entryselectedby-element-for-tablerowentry--for-tablecontrol-format"></a><span data-ttu-id="f3996-103">Het element EntrySelectedBy voor TableRowEntry voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="f3996-103">EntrySelectedBy Element for TableRowEntry  for TableControl (Format)</span></span>

<span data-ttu-id="f3996-104">Hiermee worden de .NET-typen gedefinieerd die gebruikmaken van deze definitie van de tabel weergave of de voor waarde die voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="f3996-104">Defines the .NET types that use this definition of the table view or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="f3996-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) TableControl element (indeling) TableRowEntries element (indeling) TableRowEntry element (indeling) EntrySelectedBy element (indeling)</span><span class="sxs-lookup"><span data-stu-id="f3996-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f3996-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="f3996-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f3996-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="f3996-107">Attributes and Elements</span></span>

<span data-ttu-id="f3996-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `EntrySelectedBy` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="f3996-108">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f3996-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="f3996-109">Attributes</span></span>

<span data-ttu-id="f3996-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="f3996-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f3996-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="f3996-111">Child Elements</span></span>

|<span data-ttu-id="f3996-112">Element</span><span class="sxs-lookup"><span data-stu-id="f3996-112">Element</span></span>|<span data-ttu-id="f3996-113">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="f3996-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f3996-114">Het element SelectionCondition voor EntrySelectedBy voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="f3996-114">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="f3996-115">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="f3996-115">Optional element.</span></span><br /><br /> <span data-ttu-id="f3996-116">Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van deze tabel weergave definitie.</span><span class="sxs-lookup"><span data-stu-id="f3996-116">Defines the condition that must exist for this table view definition to be used.</span></span>|
|[<span data-ttu-id="f3996-117">Het element SelectionSetName voor EntrySelectedBy voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="f3996-117">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="f3996-118">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="f3996-118">Optional element.</span></span><br /><br /> <span data-ttu-id="f3996-119">Hiermee geeft u een set .NET-typen op die gebruikmaken van deze tabel weergave definitie.</span><span class="sxs-lookup"><span data-stu-id="f3996-119">Specifies a set of .NET types that use this table view definition.</span></span>|
|[<span data-ttu-id="f3996-120">Het element TypeName voor EntrySelectedBy voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="f3996-120">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>](./typename-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="f3996-121">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="f3996-121">Optional element.</span></span><br /><br /> <span data-ttu-id="f3996-122">Hiermee geeft u een .NET-type op dat gebruikmaakt van deze tabel weergave definitie.</span><span class="sxs-lookup"><span data-stu-id="f3996-122">Specifies a .NET type that uses this table view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f3996-123">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="f3996-123">Parent Elements</span></span>

|<span data-ttu-id="f3996-124">Element</span><span class="sxs-lookup"><span data-stu-id="f3996-124">Element</span></span>|<span data-ttu-id="f3996-125">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="f3996-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f3996-126">TableRowEntry-element voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="f3996-126">TableRowEntry Element for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|<span data-ttu-id="f3996-127">Hiermee worden de gegevens gedefinieerd die worden weer gegeven in een rij van de tabel.</span><span class="sxs-lookup"><span data-stu-id="f3996-127">Defines the data that is displayed in a row of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f3996-128">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="f3996-128">Remarks</span></span>

<span data-ttu-id="f3996-129">U moet ten minste één type, selectieset of selectie voorwaarde opgeven voor een tabel weergave definitie.</span><span class="sxs-lookup"><span data-stu-id="f3996-129">You must specify at least one type, selection set, or selection condition for a table view definition.</span></span> <span data-ttu-id="f3996-130">Er is geen maximum limiet voor het aantal onderliggende elementen dat u kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="f3996-130">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="f3996-131">De selectie voorwaarden worden gebruikt voor het definiëren van een voor waarde die voor de definitie moet bestaan, zoals wanneer een object een specifieke eigenschap heeft of een bepaalde eigenschaps waarde of een specifiek script wordt geëvalueerd `true` .</span><span class="sxs-lookup"><span data-stu-id="f3996-131">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="f3996-132">Zie voor [waarden definiëren voor het gebruik van een weergave vermelding of-item](./defining-conditions-for-displaying-data.md)voor meer informatie over selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="f3996-132">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="f3996-133">Zie [een tabel weergave maken](./creating-a-table-view.md)voor meer informatie over de onderdelen van een tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="f3996-133">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="f3996-134">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="f3996-134">Example</span></span>

<span data-ttu-id="f3996-135">In het volgende voor beeld ziet u een- `TableRowEntry` element dat wordt gebruikt om de eigenschappen van het object [System. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) weer te geven.</span><span class="sxs-lookup"><span data-stu-id="f3996-135">The following example shows a `TableRowEntry` element that is used to display the properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="f3996-136">Zie ook</span><span class="sxs-lookup"><span data-stu-id="f3996-136">See Also</span></span>

[<span data-ttu-id="f3996-137">Een tabelweergave maken</span><span class="sxs-lookup"><span data-stu-id="f3996-137">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="f3996-138">Het element SelectionCondition voor EntrySelectedBy voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="f3996-138">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="f3996-139">Het element SelectionSetName voor EntrySelectedBy voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="f3996-139">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="f3996-140">TableRowEntry-element voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="f3996-140">TableRowEntry Element for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[<span data-ttu-id="f3996-141">Het element TypeName voor EntrySelectedBy voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="f3996-141">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>](./typename-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="f3996-142">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="f3996-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
