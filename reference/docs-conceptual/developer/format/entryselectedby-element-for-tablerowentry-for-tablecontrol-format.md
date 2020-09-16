---
title: EntrySelectedBy-element voor TableRowEntry voor TableControl (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 047a10fb6b38dfa8f78a7741fd50b781d4a14b6d
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787696"
---
# <a name="entryselectedby-element-for-tablerowentry--for-tablecontrol-format"></a><span data-ttu-id="77280-102">Het element EntrySelectedBy voor TableRowEntry voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="77280-102">EntrySelectedBy Element for TableRowEntry  for TableControl (Format)</span></span>

<span data-ttu-id="77280-103">Hiermee worden de .NET-typen gedefinieerd die gebruikmaken van deze definitie van de tabel weergave of de voor waarde die voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="77280-103">Defines the .NET types that use this definition of the table view or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="77280-104">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) TableControl element (indeling) TableRowEntries element (indeling) TableRowEntry element (indeling) EntrySelectedBy element (indeling)</span><span class="sxs-lookup"><span data-stu-id="77280-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="77280-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="77280-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="77280-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="77280-106">Attributes and Elements</span></span>

<span data-ttu-id="77280-107">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `EntrySelectedBy` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="77280-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="77280-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="77280-108">Attributes</span></span>

<span data-ttu-id="77280-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="77280-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="77280-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="77280-110">Child Elements</span></span>

|<span data-ttu-id="77280-111">Element</span><span class="sxs-lookup"><span data-stu-id="77280-111">Element</span></span>|<span data-ttu-id="77280-112">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="77280-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="77280-113">Het element SelectionCondition voor EntrySelectedBy voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="77280-113">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="77280-114">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="77280-114">Optional element.</span></span><br /><br /> <span data-ttu-id="77280-115">Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van deze tabel weergave definitie.</span><span class="sxs-lookup"><span data-stu-id="77280-115">Defines the condition that must exist for this table view definition to be used.</span></span>|
|[<span data-ttu-id="77280-116">Het element SelectionSetName voor EntrySelectedBy voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="77280-116">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="77280-117">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="77280-117">Optional element.</span></span><br /><br /> <span data-ttu-id="77280-118">Hiermee geeft u een set .NET-typen op die gebruikmaken van deze tabel weergave definitie.</span><span class="sxs-lookup"><span data-stu-id="77280-118">Specifies a set of .NET types that use this table view definition.</span></span>|
|[<span data-ttu-id="77280-119">Het element TypeName voor EntrySelectedBy voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="77280-119">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>](./typename-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="77280-120">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="77280-120">Optional element.</span></span><br /><br /> <span data-ttu-id="77280-121">Hiermee geeft u een .NET-type op dat gebruikmaakt van deze tabel weergave definitie.</span><span class="sxs-lookup"><span data-stu-id="77280-121">Specifies a .NET type that uses this table view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="77280-122">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="77280-122">Parent Elements</span></span>

|<span data-ttu-id="77280-123">Element</span><span class="sxs-lookup"><span data-stu-id="77280-123">Element</span></span>|<span data-ttu-id="77280-124">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="77280-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="77280-125">TableRowEntry-element voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="77280-125">TableRowEntry Element for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|<span data-ttu-id="77280-126">Hiermee worden de gegevens gedefinieerd die worden weer gegeven in een rij van de tabel.</span><span class="sxs-lookup"><span data-stu-id="77280-126">Defines the data that is displayed in a row of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="77280-127">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="77280-127">Remarks</span></span>

<span data-ttu-id="77280-128">U moet ten minste één type, selectieset of selectie voorwaarde opgeven voor een tabel weergave definitie.</span><span class="sxs-lookup"><span data-stu-id="77280-128">You must specify at least one type, selection set, or selection condition for a table view definition.</span></span> <span data-ttu-id="77280-129">Er is geen maximum limiet voor het aantal onderliggende elementen dat u kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="77280-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="77280-130">De selectie voorwaarden worden gebruikt voor het definiëren van een voor waarde die voor de definitie moet bestaan, zoals wanneer een object een specifieke eigenschap heeft of een bepaalde eigenschaps waarde of een specifiek script wordt geëvalueerd `true` .</span><span class="sxs-lookup"><span data-stu-id="77280-130">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="77280-131">Zie voor [waarden definiëren voor het gebruik van een weergave vermelding of-item](./defining-conditions-for-displaying-data.md)voor meer informatie over selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="77280-131">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="77280-132">Zie [een tabel weergave maken](./creating-a-table-view.md)voor meer informatie over de onderdelen van een tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="77280-132">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="77280-133">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="77280-133">Example</span></span>

<span data-ttu-id="77280-134">In het volgende voor beeld ziet u een- `TableRowEntry` element dat wordt gebruikt om de eigenschappen van het object [System. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) weer te geven.</span><span class="sxs-lookup"><span data-stu-id="77280-134">The following example shows a `TableRowEntry` element that is used to display the properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="77280-135">Zie ook</span><span class="sxs-lookup"><span data-stu-id="77280-135">See Also</span></span>

[<span data-ttu-id="77280-136">Een tabelweergave maken</span><span class="sxs-lookup"><span data-stu-id="77280-136">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="77280-137">Het element SelectionCondition voor EntrySelectedBy voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="77280-137">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="77280-138">Het element SelectionSetName voor EntrySelectedBy voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="77280-138">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="77280-139">TableRowEntry-element voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="77280-139">TableRowEntry Element for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[<span data-ttu-id="77280-140">Het element TypeName voor EntrySelectedBy voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="77280-140">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>](./typename-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="77280-141">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="77280-141">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
