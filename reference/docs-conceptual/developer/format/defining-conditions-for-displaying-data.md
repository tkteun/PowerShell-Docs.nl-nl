---
title: Voor waarden definiëren voor het weer geven van gegevens | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c1e05821-6aec-437b-84a5-218a5727f88b
caps.latest.revision: 10
ms.openlocfilehash: 8a5b84b6a461e9fc340a5981578d95ca2ac6b9f7
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355151"
---
# <a name="defining-conditions-for-displaying-data"></a><span data-ttu-id="542e6-102">Voorwaarden voor het weergeven van gegevens definiëren</span><span class="sxs-lookup"><span data-stu-id="542e6-102">Defining Conditions for Displaying Data</span></span>

<span data-ttu-id="542e6-103">Wanneer u definieert welke gegevens door een weer gave of een besturings element worden weer gegeven, kunt u een voor waarde opgeven die moet bestaan voor de gegevens die moeten worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="542e6-103">When defining what data is displayed by a view or a control, you can specify a condition that must exist for the data to be displayed.</span></span> <span data-ttu-id="542e6-104">De voor waarde kan worden geactiveerd door een specifieke eigenschap of wanneer een script of eigenschaps waarde wordt geëvalueerd als `true`.</span><span class="sxs-lookup"><span data-stu-id="542e6-104">The condition can be triggered by a specific property, or when a script or property value evaluates to `true`.</span></span> <span data-ttu-id="542e6-105">Wanneer aan de voor waarde voor de selectie wordt voldaan, wordt de definitie van de weer gave of het besturings element gebruikt.</span><span class="sxs-lookup"><span data-stu-id="542e6-105">When the selection condition is met, the definition of the view or control is used.</span></span>

## <a name="specifying-a-selection-condition-for-a-definition"></a><span data-ttu-id="542e6-106">Een selectie voorwaarde voor een definitie opgeven</span><span class="sxs-lookup"><span data-stu-id="542e6-106">Specifying a Selection Condition for a Definition</span></span>

<span data-ttu-id="542e6-107">Wanneer u een definitie voor een weer gave of besturings element maakt, wordt het element `EntrySelectedBy` gebruikt om op te geven welke objecten de definitie gebruiken of welke voor waarde moet bestaan om de definitie te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="542e6-107">When creating a definition for a view or control, the `EntrySelectedBy` element is used to specify which objects will use the definition or what condition must exist for the definition to be used.</span></span> <span data-ttu-id="542e6-108">De voor waarde wordt opgegeven door het element `SelectionCondition`.</span><span class="sxs-lookup"><span data-stu-id="542e6-108">The condition is specified by the `SelectionCondition` element.</span></span>

<span data-ttu-id="542e6-109">In het volgende voor beeld wordt een selectie voorwaarde opgegeven voor een definitie van een tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="542e6-109">In the following example, a selection condition is specified for a definition of a table view.</span></span> <span data-ttu-id="542e6-110">In dit voor beeld wordt de definitie alleen gebruikt wanneer het opgegeven script wordt geëvalueerd als `true`.</span><span class="sxs-lookup"><span data-stu-id="542e6-110">In this example, the definition is used only when the specified script is evaluated to `true`.</span></span>

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

<span data-ttu-id="542e6-111">Er is geen limiet voor het aantal selectie omstandigheden dat u kunt opgeven voor een definitie van een weer gave of besturings element.</span><span class="sxs-lookup"><span data-stu-id="542e6-111">There is no limit to the number of selection conditions that you can specify for a definition of a view or control.</span></span> <span data-ttu-id="542e6-112">De enige vereisten zijn de volgende:</span><span class="sxs-lookup"><span data-stu-id="542e6-112">The only requirements are the following:</span></span>

- <span data-ttu-id="542e6-113">De selectie voorwaarde moet één eigenschaps naam of script opgeven om de voor waarde te activeren, maar kan niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="542e6-113">The selection condition must specify one property name or script to trigger the condition, but cannot specify both.</span></span>

- <span data-ttu-id="542e6-114">Met de selectie voorwaarde kan een wille keurig aantal .NET-typen of-selectie sets worden opgegeven, maar kan niet beide worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="542e6-114">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

## <a name="specifying-a-selection-condition-for-an-item"></a><span data-ttu-id="542e6-115">Een selectie voorwaarde voor een item opgeven</span><span class="sxs-lookup"><span data-stu-id="542e6-115">Specifying a Selection Condition for an Item</span></span>

<span data-ttu-id="542e6-116">U kunt ook opgeven wanneer een item van een lijst weergave of besturings element wordt gebruikt door het element `ItemSelectionCondition` in de definitie van het item op te nemen.</span><span class="sxs-lookup"><span data-stu-id="542e6-116">You can also specify when an item of a list view or control is used by including the `ItemSelectionCondition` element in the item definition.</span></span> <span data-ttu-id="542e6-117">In het volgende voor beeld wordt een selectie voorwaarde opgegeven voor een item van een lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="542e6-117">In the following example, a selection condition is specified for an item of a list view.</span></span> <span data-ttu-id="542e6-118">In dit voor beeld wordt het item alleen gebruikt wanneer het script wordt geëvalueerd als `true`.</span><span class="sxs-lookup"><span data-stu-id="542e6-118">In this example, the item is used only when the script is evaluated to `true`.</span></span>

```xml
<ListItem>
  <ItemSelectionCondition>
    <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  </ItemSelectionCondition>
</ListItem>

```

<span data-ttu-id="542e6-119">U kunt slechts één selectie voorwaarde voor een item opgeven.</span><span class="sxs-lookup"><span data-stu-id="542e6-119">You can specify only one selection condition for an item.</span></span> <span data-ttu-id="542e6-120">En de voor waarde moet één eigenschaps naam of script opgeven om de voor waarde te activeren, maar kan niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="542e6-120">And the condition must specify one property name or script to trigger the condition, but cannot specify both.</span></span>

## <a name="xml-elements"></a><span data-ttu-id="542e6-121">XML-elementen</span><span class="sxs-lookup"><span data-stu-id="542e6-121">XML Elements</span></span>

 <span data-ttu-id="542e6-122">De volgende XML-elementen worden gebruikt om een selectie voorwaarde te maken.</span><span class="sxs-lookup"><span data-stu-id="542e6-122">The following XML elements are used to create a selection condition.</span></span>

- <span data-ttu-id="542e6-123">In de volgende elementen worden de selectie voorwaarden voor weergave definities opgegeven:</span><span class="sxs-lookup"><span data-stu-id="542e6-123">The following elements specify selection conditions for view definitions:</span></span>

    - [<span data-ttu-id="542e6-124">SelectionCondition-element voor EntrySelectedBy voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="542e6-124">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

    - [<span data-ttu-id="542e6-125">SelectionCondition-element voor EntrySelectedBy voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="542e6-125">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

    - [<span data-ttu-id="542e6-126">SelectionCondition-element voor EntrySelectedBy voor WideControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="542e6-126">SelectionCondition Element for EntrySelectedBy for WideControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

    - [<span data-ttu-id="542e6-127">SelectionCondition-element voor EntrySelectedBy voor CustomControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="542e6-127">SelectionCondition Element for EntrySelectedBy for CustomControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

- <span data-ttu-id="542e6-128">In de volgende elementen worden de selectie voorwaarden voor algemene en de weer gave van besturings definities opgegeven:</span><span class="sxs-lookup"><span data-stu-id="542e6-128">The following elements specify selection conditions for common and view control definitions:</span></span>

    - [<span data-ttu-id="542e6-129">SelectionCondition-element voor EntrySelectedBy voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="542e6-129">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

    - [<span data-ttu-id="542e6-130">SelectionCondition-element voor EntrySelectedBy voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="542e6-130">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

- <span data-ttu-id="542e6-131">Het volgende element specificeert de selectie voorwaarde voor het uitbreiden van verzamelings objecten:</span><span class="sxs-lookup"><span data-stu-id="542e6-131">The following element specifies the selection condition for expanding collection objects:</span></span>

    - [<span data-ttu-id="542e6-132">SelectionCondition-element voor EntrySelectedBy voor EnumerableExpansion (indeling)</span><span class="sxs-lookup"><span data-stu-id="542e6-132">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

- <span data-ttu-id="542e6-133">Het volgende element specificeert de selectie voorwaarde voor het weer geven van een nieuwe groep gegevens:</span><span class="sxs-lookup"><span data-stu-id="542e6-133">The following element specifies the selection condition for displaying a new group of data:</span></span>

    - [<span data-ttu-id="542e6-134">SelectionCondition-element voor EntrySelectedBy voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="542e6-134">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

- <span data-ttu-id="542e6-135">Met het volgende element wordt een item selectie voorwaarde voor een lijst weergave opgegeven:</span><span class="sxs-lookup"><span data-stu-id="542e6-135">The following element specifies an item selection condition for a list view:</span></span>

    - [<span data-ttu-id="542e6-136">ItemSelectionCondition-element voor lijst item voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="542e6-136">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

- <span data-ttu-id="542e6-137">De volgende elementen geven een item selectie voorwaarde voor besturings elementen aan:</span><span class="sxs-lookup"><span data-stu-id="542e6-137">The following elements specify an item selection condition for controls:</span></span>

    - [<span data-ttu-id="542e6-138">ItemSelectionCondition-element voor ExpressionBinding voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="542e6-138">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

    - [<span data-ttu-id="542e6-139">ItemSelectionCondition-element voor ExpressionBinding voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="542e6-139">ItemSelectionCondition Element for ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

    - [<span data-ttu-id="542e6-140">ItemSelectionCondition-element voor ExpressionBinding voor CustomControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="542e6-140">ItemSelectionCondition Element for ExpressionBinding for CustomControl (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

## <a name="see-also"></a><span data-ttu-id="542e6-141">Zie ook</span><span class="sxs-lookup"><span data-stu-id="542e6-141">See Also</span></span>

[<span data-ttu-id="542e6-142">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="542e6-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
