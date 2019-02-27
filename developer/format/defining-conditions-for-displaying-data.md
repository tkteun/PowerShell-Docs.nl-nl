---
title: Voorwaarden voor het weergeven van gegevens definiëren | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c1e05821-6aec-437b-84a5-218a5727f88b
caps.latest.revision: 10
ms.openlocfilehash: 8a5b84b6a461e9fc340a5981578d95ca2ac6b9f7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846562"
---
# <a name="defining-conditions-for-displaying-data"></a><span data-ttu-id="320e3-102">Voorwaarden voor het weergeven van gegevens definiëren</span><span class="sxs-lookup"><span data-stu-id="320e3-102">Defining Conditions for Displaying Data</span></span>

<span data-ttu-id="320e3-103">Bij het definiëren van welke gegevens door een weergave of een besturingselement wordt weergegeven, kunt u een voorwaarde die moet aanwezig zijn voor de gegevens moet worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="320e3-103">When defining what data is displayed by a view or a control, you can specify a condition that must exist for the data to be displayed.</span></span> <span data-ttu-id="320e3-104">De voorwaarde kan worden geactiveerd door een bepaalde eigenschap, of wanneer een script of de waarde van de eigenschap resulteert in `true`.</span><span class="sxs-lookup"><span data-stu-id="320e3-104">The condition can be triggered by a specific property, or when a script or property value evaluates to `true`.</span></span> <span data-ttu-id="320e3-105">Wanneer de selectievoorwaarde wordt voldaan, wordt de definitie van de weergave of het besturingselement gebruikt.</span><span class="sxs-lookup"><span data-stu-id="320e3-105">When the selection condition is met, the definition of the view or control is used.</span></span>

## <a name="specifying-a-selection-condition-for-a-definition"></a><span data-ttu-id="320e3-106">Een Selectievoorwaarde voor een definitie op te geven</span><span class="sxs-lookup"><span data-stu-id="320e3-106">Specifying a Selection Condition for a Definition</span></span>

<span data-ttu-id="320e3-107">Bij het maken van een definitie voor een weergave of een besturingselement, de `EntrySelectedBy` element wordt gebruikt om op te geven welke objecten de definitie wordt gebruikt of welke voorwaarde moet bestaan voor de definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="320e3-107">When creating a definition for a view or control, the `EntrySelectedBy` element is used to specify which objects will use the definition or what condition must exist for the definition to be used.</span></span> <span data-ttu-id="320e3-108">De voorwaarde wordt opgegeven door de `SelectionCondition` element.</span><span class="sxs-lookup"><span data-stu-id="320e3-108">The condition is specified by the `SelectionCondition` element.</span></span>

<span data-ttu-id="320e3-109">In het volgende voorbeeld wordt een selectievoorwaarde opgegeven voor een definitie van een tabelweergave.</span><span class="sxs-lookup"><span data-stu-id="320e3-109">In the following example, a selection condition is specified for a definition of a table view.</span></span> <span data-ttu-id="320e3-110">In dit voorbeeld wordt de definitie wordt alleen gebruikt als het opgegeven script wordt geëvalueerd naar `true`.</span><span class="sxs-lookup"><span data-stu-id="320e3-110">In this example, the definition is used only when the specified script is evaluated to `true`.</span></span>

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

<span data-ttu-id="320e3-111">Er is geen limiet voor het aantal selectie voorwaarden die u voor een definitie van een weergave of een besturingselement opgeven kunt.</span><span class="sxs-lookup"><span data-stu-id="320e3-111">There is no limit to the number of selection conditions that you can specify for a definition of a view or control.</span></span> <span data-ttu-id="320e3-112">De enige vereisten zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="320e3-112">The only requirements are the following:</span></span>

- <span data-ttu-id="320e3-113">De selectievoorwaarde moet één naam van de eigenschap of een script voor het activeren van de voorwaarde opgeven, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="320e3-113">The selection condition must specify one property name or script to trigger the condition, but cannot specify both.</span></span>

- <span data-ttu-id="320e3-114">De selectievoorwaarde een willekeurig aantal .NET-typen kunt opgeven of de selectie wordt ingesteld, maar niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="320e3-114">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

## <a name="specifying-a-selection-condition-for-an-item"></a><span data-ttu-id="320e3-115">Een Selectievoorwaarde van een Item op te geven</span><span class="sxs-lookup"><span data-stu-id="320e3-115">Specifying a Selection Condition for an Item</span></span>

<span data-ttu-id="320e3-116">U kunt ook opgeven wanneer een item van een lijst of een besturingselement wordt gebruikt door de `ItemSelectionCondition` -element in de definitie van het item.</span><span class="sxs-lookup"><span data-stu-id="320e3-116">You can also specify when an item of a list view or control is used by including the `ItemSelectionCondition` element in the item definition.</span></span> <span data-ttu-id="320e3-117">In het volgende voorbeeld wordt een selectievoorwaarde opgegeven voor een item van een lijst weergeven.</span><span class="sxs-lookup"><span data-stu-id="320e3-117">In the following example, a selection condition is specified for an item of a list view.</span></span> <span data-ttu-id="320e3-118">In dit voorbeeld wordt het item wordt alleen gebruikt als het script wordt geëvalueerd naar `true`.</span><span class="sxs-lookup"><span data-stu-id="320e3-118">In this example, the item is used only when the script is evaluated to `true`.</span></span>

```xml
<ListItem>
  <ItemSelectionCondition>
    <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  </ItemSelectionCondition>
</ListItem>

```

<span data-ttu-id="320e3-119">U kunt slechts één selectievoorwaarde voor een item opgeven.</span><span class="sxs-lookup"><span data-stu-id="320e3-119">You can specify only one selection condition for an item.</span></span> <span data-ttu-id="320e3-120">En de voorwaarde moet één naam van de eigenschap of een script voor het activeren van de voorwaarde opgeven, maar niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="320e3-120">And the condition must specify one property name or script to trigger the condition, but cannot specify both.</span></span>

## <a name="xml-elements"></a><span data-ttu-id="320e3-121">XML-elementen</span><span class="sxs-lookup"><span data-stu-id="320e3-121">XML Elements</span></span>

 <span data-ttu-id="320e3-122">De volgende XML-elementen worden gebruikt om de selectievoorwaarde van een te maken.</span><span class="sxs-lookup"><span data-stu-id="320e3-122">The following XML elements are used to create a selection condition.</span></span>

- <span data-ttu-id="320e3-123">De volgende elementen opgeven selectie voorwaarden voor weergavedefinities:</span><span class="sxs-lookup"><span data-stu-id="320e3-123">The following elements specify selection conditions for view definitions:</span></span>

    - [<span data-ttu-id="320e3-124">SelectionCondition-Element voor EntrySelectedBy voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="320e3-124">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

    - [<span data-ttu-id="320e3-125">SelectionCondition-Element voor EntrySelectedBy voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="320e3-125">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

    - [<span data-ttu-id="320e3-126">SelectionCondition-Element voor EntrySelectedBy voor WideControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="320e3-126">SelectionCondition Element for EntrySelectedBy for WideControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

    - [<span data-ttu-id="320e3-127">SelectionCondition-Element voor EntrySelectedBy voor CustomControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="320e3-127">SelectionCondition Element for EntrySelectedBy for CustomControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

- <span data-ttu-id="320e3-128">De volgende elementen opgeven selectie voorwaarden voor algemene en weergave definities beheren:</span><span class="sxs-lookup"><span data-stu-id="320e3-128">The following elements specify selection conditions for common and view control definitions:</span></span>

    - [<span data-ttu-id="320e3-129">SelectionCondition-Element voor EntrySelectedBy voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="320e3-129">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

    - [<span data-ttu-id="320e3-130">SelectionCondition-Element voor EntrySelectedBy voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="320e3-130">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

- <span data-ttu-id="320e3-131">Het volgende element Hiermee geeft u de selectievoorwaarde voor het uitbreiden van verzameling objecten:</span><span class="sxs-lookup"><span data-stu-id="320e3-131">The following element specifies the selection condition for expanding collection objects:</span></span>

    - [<span data-ttu-id="320e3-132">SelectionCondition-Element voor EntrySelectedBy voor EnumerableExpansion (indeling)</span><span class="sxs-lookup"><span data-stu-id="320e3-132">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

- <span data-ttu-id="320e3-133">Het volgende element Hiermee geeft u de selectievoorwaarde voor het weergeven van een nieuwe groep van gegevens:</span><span class="sxs-lookup"><span data-stu-id="320e3-133">The following element specifies the selection condition for displaying a new group of data:</span></span>

    - [<span data-ttu-id="320e3-134">SelectionCondition-Element voor EntrySelectedBy voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="320e3-134">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

- <span data-ttu-id="320e3-135">Het volgende element Hiermee geeft u de voorwaarde van een item selecteren voor een lijst weergeven:</span><span class="sxs-lookup"><span data-stu-id="320e3-135">The following element specifies an item selection condition for a list view:</span></span>

    - [<span data-ttu-id="320e3-136">ItemSelectionCondition-Element voor ListItem voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="320e3-136">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

- <span data-ttu-id="320e3-137">De volgende elementen opgeven een voorwaarde voor de selectie van item voor besturingselementen:</span><span class="sxs-lookup"><span data-stu-id="320e3-137">The following elements specify an item selection condition for controls:</span></span>

    - [<span data-ttu-id="320e3-138">ItemSelectionCondition-Element voor ExpressionBinding voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="320e3-138">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

    - [<span data-ttu-id="320e3-139">ItemSelectionCondition-Element voor ExpressionBinding voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="320e3-139">ItemSelectionCondition Element for ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

    - [<span data-ttu-id="320e3-140">ItemSelectionCondition-Element voor ExpressionBinding voor CustomControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="320e3-140">ItemSelectionCondition Element for ExpressionBinding for CustomControl (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

## <a name="see-also"></a><span data-ttu-id="320e3-141">Zie ook</span><span class="sxs-lookup"><span data-stu-id="320e3-141">See Also</span></span>

[<span data-ttu-id="320e3-142">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="320e3-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
