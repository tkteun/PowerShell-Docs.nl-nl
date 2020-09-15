---
title: Voor waarden definiëren voor het weer geven van gegevens | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 13de078e681708b02e378b2c7d531032b2ffdc05
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774334"
---
# <a name="defining-conditions-for-displaying-data"></a><span data-ttu-id="6b2ec-102">Voorwaarden voor het weergeven van gegevens definiëren</span><span class="sxs-lookup"><span data-stu-id="6b2ec-102">Defining Conditions for Displaying Data</span></span>

<span data-ttu-id="6b2ec-103">Wanneer u definieert welke gegevens door een weer gave of een besturings element worden weer gegeven, kunt u een voor waarde opgeven die moet bestaan voor de gegevens die moeten worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="6b2ec-103">When defining what data is displayed by a view or a control, you can specify a condition that must exist for the data to be displayed.</span></span> <span data-ttu-id="6b2ec-104">De voor waarde kan worden geactiveerd door een specifieke eigenschap of wanneer de waarde van een script of eigenschap wordt geëvalueerd `true` .</span><span class="sxs-lookup"><span data-stu-id="6b2ec-104">The condition can be triggered by a specific property, or when a script or property value evaluates to `true`.</span></span> <span data-ttu-id="6b2ec-105">Wanneer aan de voor waarde voor de selectie wordt voldaan, wordt de definitie van de weer gave of het besturings element gebruikt.</span><span class="sxs-lookup"><span data-stu-id="6b2ec-105">When the selection condition is met, the definition of the view or control is used.</span></span>

## <a name="specifying-a-selection-condition-for-a-definition"></a><span data-ttu-id="6b2ec-106">Een selectie voorwaarde voor een definitie opgeven</span><span class="sxs-lookup"><span data-stu-id="6b2ec-106">Specifying a Selection Condition for a Definition</span></span>

<span data-ttu-id="6b2ec-107">Wanneer u een definitie voor een weer gave of besturings element maakt, `EntrySelectedBy` wordt het element gebruikt om op te geven welke objecten de definitie zullen gebruiken, of welke voor waarde moet bestaan om de definitie te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="6b2ec-107">When creating a definition for a view or control, the `EntrySelectedBy` element is used to specify which objects will use the definition or what condition must exist for the definition to be used.</span></span> <span data-ttu-id="6b2ec-108">De voor waarde wordt opgegeven door het `SelectionCondition` element.</span><span class="sxs-lookup"><span data-stu-id="6b2ec-108">The condition is specified by the `SelectionCondition` element.</span></span>

<span data-ttu-id="6b2ec-109">In het volgende voor beeld wordt een selectie voorwaarde opgegeven voor een definitie van een tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="6b2ec-109">In the following example, a selection condition is specified for a definition of a table view.</span></span> <span data-ttu-id="6b2ec-110">In dit voor beeld wordt de definitie alleen gebruikt wanneer het opgegeven script wordt geëvalueerd `true` .</span><span class="sxs-lookup"><span data-stu-id="6b2ec-110">In this example, the definition is used only when the specified script is evaluated to `true`.</span></span>

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

<span data-ttu-id="6b2ec-111">Er is geen limiet voor het aantal selectie omstandigheden dat u kunt opgeven voor een definitie van een weer gave of besturings element.</span><span class="sxs-lookup"><span data-stu-id="6b2ec-111">There is no limit to the number of selection conditions that you can specify for a definition of a view or control.</span></span> <span data-ttu-id="6b2ec-112">De enige vereisten zijn de volgende:</span><span class="sxs-lookup"><span data-stu-id="6b2ec-112">The only requirements are the following:</span></span>

- <span data-ttu-id="6b2ec-113">De selectie voorwaarde moet één eigenschaps naam of script opgeven om de voor waarde te activeren, maar kan niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="6b2ec-113">The selection condition must specify one property name or script to trigger the condition, but cannot specify both.</span></span>

- <span data-ttu-id="6b2ec-114">Met de selectie voorwaarde kan een wille keurig aantal .NET-typen of-selectie sets worden opgegeven, maar kan niet beide worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="6b2ec-114">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

## <a name="specifying-a-selection-condition-for-an-item"></a><span data-ttu-id="6b2ec-115">Een selectie voorwaarde voor een item opgeven</span><span class="sxs-lookup"><span data-stu-id="6b2ec-115">Specifying a Selection Condition for an Item</span></span>

<span data-ttu-id="6b2ec-116">U kunt ook opgeven wanneer een item van een lijst weergave of besturings element wordt gebruikt door het `ItemSelectionCondition` element op te nemen in de definitie van het item.</span><span class="sxs-lookup"><span data-stu-id="6b2ec-116">You can also specify when an item of a list view or control is used by including the `ItemSelectionCondition` element in the item definition.</span></span> <span data-ttu-id="6b2ec-117">In het volgende voor beeld wordt een selectie voorwaarde opgegeven voor een item van een lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="6b2ec-117">In the following example, a selection condition is specified for an item of a list view.</span></span> <span data-ttu-id="6b2ec-118">In dit voor beeld wordt het item alleen gebruikt wanneer het script wordt geëvalueerd `true` .</span><span class="sxs-lookup"><span data-stu-id="6b2ec-118">In this example, the item is used only when the script is evaluated to `true`.</span></span>

```xml
<ListItem>
  <ItemSelectionCondition>
    <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  </ItemSelectionCondition>
</ListItem>

```

<span data-ttu-id="6b2ec-119">U kunt slechts één selectie voorwaarde voor een item opgeven.</span><span class="sxs-lookup"><span data-stu-id="6b2ec-119">You can specify only one selection condition for an item.</span></span> <span data-ttu-id="6b2ec-120">En de voor waarde moet één eigenschaps naam of script opgeven om de voor waarde te activeren, maar kan niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="6b2ec-120">And the condition must specify one property name or script to trigger the condition, but cannot specify both.</span></span>

## <a name="xml-elements"></a><span data-ttu-id="6b2ec-121">XML-elementen</span><span class="sxs-lookup"><span data-stu-id="6b2ec-121">XML Elements</span></span>

 <span data-ttu-id="6b2ec-122">De volgende XML-elementen worden gebruikt om een selectie voorwaarde te maken.</span><span class="sxs-lookup"><span data-stu-id="6b2ec-122">The following XML elements are used to create a selection condition.</span></span>

- <span data-ttu-id="6b2ec-123">In de volgende elementen worden de selectie voorwaarden voor weergave definities opgegeven:</span><span class="sxs-lookup"><span data-stu-id="6b2ec-123">The following elements specify selection conditions for view definitions:</span></span>

  - [<span data-ttu-id="6b2ec-124">Het element SelectionCondition voor EntrySelectedBy voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="6b2ec-124">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

  - [<span data-ttu-id="6b2ec-125">Het element SelectionCondition voor EntrySelectedBy voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="6b2ec-125">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

  - [<span data-ttu-id="6b2ec-126">Het element SelectionCondition voor EntrySelectedBy voor WideControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="6b2ec-126">SelectionCondition Element for EntrySelectedBy for WideControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

  - [<span data-ttu-id="6b2ec-127">Het element SelectionCondition voor EntrySelectedBy voor CustomControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="6b2ec-127">SelectionCondition Element for EntrySelectedBy for CustomControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

- <span data-ttu-id="6b2ec-128">In de volgende elementen worden de selectie voorwaarden voor algemene en de weer gave van besturings definities opgegeven:</span><span class="sxs-lookup"><span data-stu-id="6b2ec-128">The following elements specify selection conditions for common and view control definitions:</span></span>

  - [<span data-ttu-id="6b2ec-129">Het element SelectionCondition voor EntrySelectedBy voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="6b2ec-129">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

  - [<span data-ttu-id="6b2ec-130">Het element SelectionCondition voor EntrySelectedBy voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="6b2ec-130">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

- <span data-ttu-id="6b2ec-131">Het volgende element specificeert de selectie voorwaarde voor het uitbreiden van verzamelings objecten:</span><span class="sxs-lookup"><span data-stu-id="6b2ec-131">The following element specifies the selection condition for expanding collection objects:</span></span>

  - [<span data-ttu-id="6b2ec-132">Het element SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (opmaak)</span><span class="sxs-lookup"><span data-stu-id="6b2ec-132">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

- <span data-ttu-id="6b2ec-133">Het volgende element specificeert de selectie voorwaarde voor het weer geven van een nieuwe groep gegevens:</span><span class="sxs-lookup"><span data-stu-id="6b2ec-133">The following element specifies the selection condition for displaying a new group of data:</span></span>

  - [<span data-ttu-id="6b2ec-134">Het element SelectionCondition voor EntrySelectedBy voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="6b2ec-134">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

- <span data-ttu-id="6b2ec-135">Met het volgende element wordt een item selectie voorwaarde voor een lijst weergave opgegeven:</span><span class="sxs-lookup"><span data-stu-id="6b2ec-135">The following element specifies an item selection condition for a list view:</span></span>

  - [<span data-ttu-id="6b2ec-136">Het element ItemSelectionCondition voor ListItem voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="6b2ec-136">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

- <span data-ttu-id="6b2ec-137">De volgende elementen geven een item selectie voorwaarde voor besturings elementen aan:</span><span class="sxs-lookup"><span data-stu-id="6b2ec-137">The following elements specify an item selection condition for controls:</span></span>

  - [<span data-ttu-id="6b2ec-138">Het element ItemSelectionCondition voor ExpressionBinding voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="6b2ec-138">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

  - [<span data-ttu-id="6b2ec-139">Het element ItemSelectionCondition voor ExpressionBinding voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="6b2ec-139">ItemSelectionCondition Element for ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

  - [<span data-ttu-id="6b2ec-140">Het element ItemSelectionCondition voor ExpressionBinding voor CustomControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="6b2ec-140">ItemSelectionCondition Element for ExpressionBinding for CustomControl (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

## <a name="see-also"></a><span data-ttu-id="6b2ec-141">Zie ook</span><span class="sxs-lookup"><span data-stu-id="6b2ec-141">See Also</span></span>

[<span data-ttu-id="6b2ec-142">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="6b2ec-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
