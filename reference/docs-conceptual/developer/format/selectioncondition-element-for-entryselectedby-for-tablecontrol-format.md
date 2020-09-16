---
title: SelectionCondition-element voor EntrySelectedBy voor TableControl (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 4a829f9daef22c4b3fd6b21dfb3af2f8539bdeb3
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780284"
---
# <a name="selectioncondition-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="60565-102">Het element SelectionCondition voor EntrySelectedBy voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="60565-102">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="60565-103">Hiermee definieert u de voor waarde die moet bestaan om te gebruiken voor deze definitie van de tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="60565-103">Defines the condition that must exist to use for this definition of the table view.</span></span> <span data-ttu-id="60565-104">Er is geen limiet voor het aantal selectie omstandigheden dat kan worden opgegeven voor een tabel definitie.</span><span class="sxs-lookup"><span data-stu-id="60565-104">There is no limit to the number of selection conditions that can be specified for a table definition.</span></span>

<span data-ttu-id="60565-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) TableControl element (indeling) TableRowEntries element (indeling) TableRowEntry element (indeling) EntrySelectedBy element voor TableRowEntry (Format) SelectionCondition-element voor EntrySelectedBy voor TableRowEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="60565-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="60565-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="60565-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="60565-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="60565-107">Attributes and Elements</span></span>

<span data-ttu-id="60565-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element SelectionCondition beschreven.</span><span class="sxs-lookup"><span data-stu-id="60565-108">The following sections describe attributes, child elements, and the parent element of the SelectionCondition element.</span></span>

### <a name="attributes"></a><span data-ttu-id="60565-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="60565-109">Attributes</span></span>

<span data-ttu-id="60565-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="60565-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="60565-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="60565-111">Child Elements</span></span>

|<span data-ttu-id="60565-112">Element</span><span class="sxs-lookup"><span data-stu-id="60565-112">Element</span></span>|<span data-ttu-id="60565-113">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="60565-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="60565-114">Het element PropertyName voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (opmaak)</span><span class="sxs-lookup"><span data-stu-id="60565-114">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)|<span data-ttu-id="60565-115">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="60565-115">Optional element.</span></span><br /><br /> <span data-ttu-id="60565-116">Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="60565-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="60565-117">Script block-element voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="60565-117">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="60565-118">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="60565-118">Optional element.</span></span><br /><br /> <span data-ttu-id="60565-119">Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="60565-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="60565-120">SelectionSetName-element voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="60565-120">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="60565-121">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="60565-121">Optional element.</span></span><br /><br /> <span data-ttu-id="60565-122">Hiermee geeft u de set .NET-typen op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="60565-122">Specifies the set of .NET types that trigger the condition.</span></span>|
|[<span data-ttu-id="60565-123">TypeName-element voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="60565-123">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="60565-124">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="60565-124">Optional element.</span></span><br /><br /> <span data-ttu-id="60565-125">Hiermee geeft u een .NET-type op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="60565-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="60565-126">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="60565-126">Parent Elements</span></span>

|<span data-ttu-id="60565-127">Element</span><span class="sxs-lookup"><span data-stu-id="60565-127">Element</span></span>|<span data-ttu-id="60565-128">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="60565-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="60565-129">EntrySelectedBy-element voor TableRowEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="60565-129">EntrySelectedBy Element for TableRowEntry (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="60565-130">Hiermee definieert u de .NET-typen die gebruikmaken van deze tabel vermelding of de voor waarde die moet bestaan voor het gebruik van deze vermelding.</span><span class="sxs-lookup"><span data-stu-id="60565-130">Defines the .NET types that use this table entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="60565-131">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="60565-131">Remarks</span></span>

<span data-ttu-id="60565-132">Voor elke lijst vermelding moet ten minste één type naam, selectieset of selectie voorwaarde zijn gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="60565-132">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="60565-133">Wanneer u een selectie voorwaarde definieert, gelden de volgende vereisten:</span><span class="sxs-lookup"><span data-stu-id="60565-133">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="60565-134">De selectie voorwaarde moet ten minste één eigenschaps naam of een script blok opgeven, maar kan niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="60565-134">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="60565-135">Met de selectie voorwaarde kan een wille keurig aantal .NET-typen of-selectie sets worden opgegeven, maar kan niet beide worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="60565-135">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="60565-136">Zie voor [waarden definiëren voor wanneer een weergave vermelding of-item wordt gebruikt](./defining-conditions-for-displaying-data.md)voor meer informatie over het gebruik van selectie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="60565-136">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="60565-137">Zie [een tabel weergave maken](./creating-a-table-view.md)voor meer informatie over de onderdelen van een tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="60565-137">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="60565-138">Zie ook</span><span class="sxs-lookup"><span data-stu-id="60565-138">See Also</span></span>

[<span data-ttu-id="60565-139">Een tabelweergave maken</span><span class="sxs-lookup"><span data-stu-id="60565-139">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="60565-140">Voor waarden definiëren voor wanneer gegevens worden weer gegeven</span><span class="sxs-lookup"><span data-stu-id="60565-140">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="60565-141">EntrySelectedBy-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="60565-141">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="60565-142">Het element PropertyName voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (opmaak)</span><span class="sxs-lookup"><span data-stu-id="60565-142">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)

[<span data-ttu-id="60565-143">Script block-element voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="60565-143">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="60565-144">SelectionSetName-element voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="60565-144">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="60565-145">TypeName-element voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="60565-145">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="60565-146">Een Windows Power shell-indeling en-type bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="60565-146">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
