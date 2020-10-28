---
ms.date: 09/13/2016
ms.topic: reference
title: Voorwaarden voor het weergeven van gegevens definiëren
description: Voorwaarden voor het weergeven van gegevens definiëren
ms.openlocfilehash: 9a8b7a618da8c64de978c13b527435a2d7793677
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92660321"
---
# <a name="defining-conditions-for-displaying-data"></a><span data-ttu-id="40992-103">Voorwaarden voor het weergeven van gegevens definiëren</span><span class="sxs-lookup"><span data-stu-id="40992-103">Defining Conditions for Displaying Data</span></span>

<span data-ttu-id="40992-104">Wanneer u definieert welke gegevens door een weer gave of een besturings element worden weer gegeven, kunt u een voor waarde opgeven die moet bestaan voor de gegevens die moeten worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="40992-104">When defining what data is displayed by a view or a control, you can specify a condition that must exist for the data to be displayed.</span></span> <span data-ttu-id="40992-105">De voor waarde kan worden geactiveerd door een specifieke eigenschap of wanneer de waarde van een script of eigenschap wordt geëvalueerd `true` .</span><span class="sxs-lookup"><span data-stu-id="40992-105">The condition can be triggered by a specific property, or when a script or property value evaluates to `true`.</span></span> <span data-ttu-id="40992-106">Wanneer aan de voor waarde voor de selectie wordt voldaan, wordt de definitie van de weer gave of het besturings element gebruikt.</span><span class="sxs-lookup"><span data-stu-id="40992-106">When the selection condition is met, the definition of the view or control is used.</span></span>

## <a name="specifying-a-selection-condition-for-a-definition"></a><span data-ttu-id="40992-107">Een selectie voorwaarde voor een definitie opgeven</span><span class="sxs-lookup"><span data-stu-id="40992-107">Specifying a Selection Condition for a Definition</span></span>

<span data-ttu-id="40992-108">Wanneer u een definitie voor een weer gave of besturings element maakt, `EntrySelectedBy` wordt het element gebruikt om op te geven welke objecten de definitie zullen gebruiken, of welke voor waarde moet bestaan om de definitie te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="40992-108">When creating a definition for a view or control, the `EntrySelectedBy` element is used to specify which objects will use the definition or what condition must exist for the definition to be used.</span></span> <span data-ttu-id="40992-109">De voor waarde wordt opgegeven door het `SelectionCondition` element.</span><span class="sxs-lookup"><span data-stu-id="40992-109">The condition is specified by the `SelectionCondition` element.</span></span>

<span data-ttu-id="40992-110">In het volgende voor beeld wordt een selectie voorwaarde opgegeven voor een definitie van een tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="40992-110">In the following example, a selection condition is specified for a definition of a table view.</span></span> <span data-ttu-id="40992-111">In dit voor beeld wordt de definitie alleen gebruikt wanneer het opgegeven script wordt geëvalueerd `true` .</span><span class="sxs-lookup"><span data-stu-id="40992-111">In this example, the definition is used only when the specified script is evaluated to `true`.</span></span>

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <SelectionCondition>
      <ScriptBlock>ScriptToEvaluate</ScriptBlock>
    </SelectionCondition>
  </EntrySelectedBy>
  <TableColumnItems>
  </TableColumnItems>
</TableRowEntry>

```

<span data-ttu-id="40992-112">Er is geen limiet voor het aantal selectie omstandigheden dat u kunt opgeven voor een definitie van een weer gave of besturings element.</span><span class="sxs-lookup"><span data-stu-id="40992-112">There is no limit to the number of selection conditions that you can specify for a definition of a view or control.</span></span> <span data-ttu-id="40992-113">De enige vereisten zijn de volgende:</span><span class="sxs-lookup"><span data-stu-id="40992-113">The only requirements are the following:</span></span>

- <span data-ttu-id="40992-114">De selectie voorwaarde moet één eigenschaps naam of script opgeven om de voor waarde te activeren, maar kan niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="40992-114">The selection condition must specify one property name or script to trigger the condition, but cannot specify both.</span></span>

- <span data-ttu-id="40992-115">Met de selectie voorwaarde kan een wille keurig aantal .NET-typen of-selectie sets worden opgegeven, maar kan niet beide worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="40992-115">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

## <a name="specifying-a-selection-condition-for-an-item"></a><span data-ttu-id="40992-116">Een selectie voorwaarde voor een item opgeven</span><span class="sxs-lookup"><span data-stu-id="40992-116">Specifying a Selection Condition for an Item</span></span>

<span data-ttu-id="40992-117">U kunt ook opgeven wanneer een item van een lijst weergave of besturings element wordt gebruikt door het `ItemSelectionCondition` element op te nemen in de definitie van het item.</span><span class="sxs-lookup"><span data-stu-id="40992-117">You can also specify when an item of a list view or control is used by including the `ItemSelectionCondition` element in the item definition.</span></span> <span data-ttu-id="40992-118">In het volgende voor beeld wordt een selectie voorwaarde opgegeven voor een item van een lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="40992-118">In the following example, a selection condition is specified for an item of a list view.</span></span> <span data-ttu-id="40992-119">In dit voor beeld wordt het item alleen gebruikt wanneer het script wordt geëvalueerd `true` .</span><span class="sxs-lookup"><span data-stu-id="40992-119">In this example, the item is used only when the script is evaluated to `true`.</span></span>

```xml
<ListItem>
  <ItemSelectionCondition>
    <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  </ItemSelectionCondition>
</ListItem>

```

<span data-ttu-id="40992-120">U kunt slechts één selectie voorwaarde voor een item opgeven.</span><span class="sxs-lookup"><span data-stu-id="40992-120">You can specify only one selection condition for an item.</span></span> <span data-ttu-id="40992-121">En de voor waarde moet één eigenschaps naam of script opgeven om de voor waarde te activeren, maar kan niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="40992-121">And the condition must specify one property name or script to trigger the condition, but cannot specify both.</span></span>

## <a name="xml-elements"></a><span data-ttu-id="40992-122">XML-elementen</span><span class="sxs-lookup"><span data-stu-id="40992-122">XML Elements</span></span>

 <span data-ttu-id="40992-123">De volgende XML-elementen worden gebruikt om een selectie voorwaarde te maken.</span><span class="sxs-lookup"><span data-stu-id="40992-123">The following XML elements are used to create a selection condition.</span></span>

- <span data-ttu-id="40992-124">In de volgende elementen worden de selectie voorwaarden voor weergave definities opgegeven:</span><span class="sxs-lookup"><span data-stu-id="40992-124">The following elements specify selection conditions for view definitions:</span></span>

  - [<span data-ttu-id="40992-125">Het element SelectionCondition voor EntrySelectedBy voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="40992-125">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

  - [<span data-ttu-id="40992-126">Het element SelectionCondition voor EntrySelectedBy voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="40992-126">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

  - [<span data-ttu-id="40992-127">Het element SelectionCondition voor EntrySelectedBy voor WideControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="40992-127">SelectionCondition Element for EntrySelectedBy for WideControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

  - [<span data-ttu-id="40992-128">Het element SelectionCondition voor EntrySelectedBy voor CustomControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="40992-128">SelectionCondition Element for EntrySelectedBy for CustomControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

- <span data-ttu-id="40992-129">In de volgende elementen worden de selectie voorwaarden voor algemene en de weer gave van besturings definities opgegeven:</span><span class="sxs-lookup"><span data-stu-id="40992-129">The following elements specify selection conditions for common and view control definitions:</span></span>

  - [<span data-ttu-id="40992-130">Het element SelectionCondition voor EntrySelectedBy voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="40992-130">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

  - [<span data-ttu-id="40992-131">Het element SelectionCondition voor EntrySelectedBy voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="40992-131">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

- <span data-ttu-id="40992-132">Het volgende element specificeert de selectie voorwaarde voor het uitbreiden van verzamelings objecten:</span><span class="sxs-lookup"><span data-stu-id="40992-132">The following element specifies the selection condition for expanding collection objects:</span></span>

  - [<span data-ttu-id="40992-133">Het element SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (opmaak)</span><span class="sxs-lookup"><span data-stu-id="40992-133">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

- <span data-ttu-id="40992-134">Het volgende element specificeert de selectie voorwaarde voor het weer geven van een nieuwe groep gegevens:</span><span class="sxs-lookup"><span data-stu-id="40992-134">The following element specifies the selection condition for displaying a new group of data:</span></span>

  - [<span data-ttu-id="40992-135">Het element SelectionCondition voor EntrySelectedBy voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="40992-135">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

- <span data-ttu-id="40992-136">Met het volgende element wordt een item selectie voorwaarde voor een lijst weergave opgegeven:</span><span class="sxs-lookup"><span data-stu-id="40992-136">The following element specifies an item selection condition for a list view:</span></span>

  - [<span data-ttu-id="40992-137">Het element ItemSelectionCondition voor ListItem voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="40992-137">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

- <span data-ttu-id="40992-138">De volgende elementen geven een item selectie voorwaarde voor besturings elementen aan:</span><span class="sxs-lookup"><span data-stu-id="40992-138">The following elements specify an item selection condition for controls:</span></span>

  - [<span data-ttu-id="40992-139">Het element ItemSelectionCondition voor ExpressionBinding voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="40992-139">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

  - [<span data-ttu-id="40992-140">Het element ItemSelectionCondition voor ExpressionBinding voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="40992-140">ItemSelectionCondition Element for ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

  - [<span data-ttu-id="40992-141">Het element ItemSelectionCondition voor ExpressionBinding voor CustomControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="40992-141">ItemSelectionCondition Element for ExpressionBinding for CustomControl (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

## <a name="see-also"></a><span data-ttu-id="40992-142">Zie ook</span><span class="sxs-lookup"><span data-stu-id="40992-142">See Also</span></span>

[<span data-ttu-id="40992-143">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="40992-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
