---
title: Selectiesets definiëren | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 00dbb5ee-93d4-4914-a082-ef4d8b236b5c
caps.latest.revision: 16
ms.openlocfilehash: 596212f2e64401a751cf3dca0ee7d60b80912c00
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848858"
---
# <a name="defining-selection-sets"></a><span data-ttu-id="157ab-102">Selectiereeksen definiëren</span><span class="sxs-lookup"><span data-stu-id="157ab-102">Defining Selection Sets</span></span>

<span data-ttu-id="157ab-103">Bij het maken van meerdere weergaven en besturingselementen, kunt u sets van objecten die worden aangeduid als selectiesets definiëren.</span><span class="sxs-lookup"><span data-stu-id="157ab-103">When creating multiple views and controls, you can define sets of objects that are referred to as selection sets.</span></span> <span data-ttu-id="157ab-104">Een selectie kunt u de objecten definiëren die één keer zonder herhaaldelijk definiëren voor elke weergave of het besturingselement.</span><span class="sxs-lookup"><span data-stu-id="157ab-104">A selection set enables you to define the objects one time, without having to define them repeatedly for each view or control.</span></span> <span data-ttu-id="157ab-105">Selectiesets worden meestal gebruikt wanneer u een set van gerelateerde .NET-objecten.</span><span class="sxs-lookup"><span data-stu-id="157ab-105">Typically, selection sets are used when you have a set of related .NET objects.</span></span> <span data-ttu-id="157ab-106">Bijvoorbeeld, de `FileSystem` opmaak-bestand (FileSystem.format.ps1xml) definieert een van selectieset-systeem met de bestandstypen die gebruikmaken van verschillende weergaven.</span><span class="sxs-lookup"><span data-stu-id="157ab-106">For example, The `FileSystem` formatting file (FileSystem.format.ps1xml) defines a selection set of the file system types that several views use.</span></span>

## <a name="where-selection-sets-are-defined-and-referenced"></a><span data-ttu-id="157ab-107">Waar selectiesets zijn gedefinieerd en referentie</span><span class="sxs-lookup"><span data-stu-id="157ab-107">Where Selection Sets are Defined and Referenced</span></span>

<span data-ttu-id="157ab-108">U definiëren selectiesets als onderdeel van de algemene gegevens die kunnen worden gebruikt door alle weergaven en besturingselementen die zijn gedefinieerd in het bestand met opmaak.</span><span class="sxs-lookup"><span data-stu-id="157ab-108">You define selection sets as part of the common data that can be used by all the views and controls defined in the formatting file.</span></span> <span data-ttu-id="157ab-109">Het volgende voorbeeld ziet drie selectiesets definiëren.</span><span class="sxs-lookup"><span data-stu-id="157ab-109">The following example shows how to define three selection sets.</span></span>

```xml
<Configuration>
  <SelectionSets>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
  </SelectionSets>
</Configuration>
```

<span data-ttu-id="157ab-110">U kunt verwijzen naar een selectie wordt ingesteld op de volgende manieren:</span><span class="sxs-lookup"><span data-stu-id="157ab-110">You can reference a selection sets in the following ways:</span></span>

- <span data-ttu-id="157ab-111">Elke weergave bevat een `ViewSelectedBy` element waarmee wordt gedefinieerd welke objecten worden weergegeven met behulp van de weergave.</span><span class="sxs-lookup"><span data-stu-id="157ab-111">Each view has a `ViewSelectedBy` element that defines which objects are displayed by using the view.</span></span> <span data-ttu-id="157ab-112">De `ViewSelectedBy` element heeft een `SelectionSetName` onderliggende element dat Hiermee geeft u de selectie instellen dat de definities van het gebruik van de weergave.</span><span class="sxs-lookup"><span data-stu-id="157ab-112">The `ViewSelectedBy` element has a `SelectionSetName` child element that specifies the selection set that all the definitions of the view use.</span></span> <span data-ttu-id="157ab-113">Er is geen beperking voor het aantal opgegeven selecteren waarnaar u vanuit een weergave verwijzen kunt.</span><span class="sxs-lookup"><span data-stu-id="157ab-113">There is no restriction on the number of selection sets that you can reference from a view.</span></span>

- <span data-ttu-id="157ab-114">In elke definitie van een weergave of een besturingselement, de `EntrySelectedBy` element wordt gedefinieerd welke objecten worden weergegeven met behulp van deze definitie.</span><span class="sxs-lookup"><span data-stu-id="157ab-114">In each definition of a view or control, the `EntrySelectedBy` element defines which objects are displayed by using that definition.</span></span> <span data-ttu-id="157ab-115">Een weergave of een besturingselement heeft meestal slechts één definitie, zodat de objecten worden gedefinieerd door de `ViewSelectedBy` element.</span><span class="sxs-lookup"><span data-stu-id="157ab-115">Typically a view or control has only one definition so the objects are defined by the `ViewSelectedBy` element.</span></span> <span data-ttu-id="157ab-116">De `EntrySelectedBy` -element van de definitie is een `SelectionSetName` onderliggende element dat Hiermee geeft u de selectie.</span><span class="sxs-lookup"><span data-stu-id="157ab-116">The `EntrySelectedBy` element of the definition has a `SelectionSetName` child element that specifies the selection set.</span></span> <span data-ttu-id="157ab-117">Als u de selectie instellen voor een definitie opgeeft, u niet opgeven een van de andere onderliggende elementen van de `EntrySelectedBy` element.</span><span class="sxs-lookup"><span data-stu-id="157ab-117">If you specify the selection set for a definition, you cannot specify any of the other child elements of the `EntrySelectedBy` element.</span></span>

- <span data-ttu-id="157ab-118">In elke definitie van een weergave of een besturingselement, de `SelectionCondition` element kan worden gebruikt om op te geven van een voorwaarde voor wanneer de definitie wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="157ab-118">In each definition of a view or control, the `SelectionCondition` element can be used to specify a condition for when the definition is used.</span></span> <span data-ttu-id="157ab-119">De `SelectionCondition` element heeft een `SelectionSetName` onderliggende element dat Hiermee geeft u de selectie ingesteld die wordt geactiveerd voor de voorwaarde.</span><span class="sxs-lookup"><span data-stu-id="157ab-119">The `SelectionCondition` element has a `SelectionSetName` child element that specifies the selection set that triggers the condition.</span></span> <span data-ttu-id="157ab-120">De voorwaarde wordt geactiveerd wanneer een van de objecten die zijn gedefinieerd in de selectie worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="157ab-120">The condition is triggered when any of the objects defined in the selection set are displayed.</span></span> <span data-ttu-id="157ab-121">Zie voor meer informatie over het instellen van deze voorwaarden [definiëren voorwaarden voor wanneer gegevens worden weergegeven](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="157ab-121">For more information about how to set these conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="selection-set-example"></a><span data-ttu-id="157ab-122">Voorbeeld van de selectie van instellen</span><span class="sxs-lookup"><span data-stu-id="157ab-122">Selection Set Example</span></span>

<span data-ttu-id="157ab-123">Het volgende voorbeeld ziet u een selectie instellen die rechtstreeks vanuit de `FileSystem` opmaak bestand dat is opgegeven door de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="157ab-123">The following example shows a selection set that is taken directly from the `FileSystem` formatting file provided by Windows PowerShell.</span></span> <span data-ttu-id="157ab-124">Zie voor meer informatie over andere Windows PowerShell bestanden opmaak [bestanden van Windows PowerShell-opmaak](./powershell-formatting-files.md).</span><span class="sxs-lookup"><span data-stu-id="157ab-124">For more information about other Windows PowerShell formatting files, see [Windows PowerShell Formatting Files](./powershell-formatting-files.md).</span></span>

```xml
<SelectionSets>
  <SelectionSet>
    <Name>FileSystemTypes</Name>
    <Types>
     <TypeName>System.IO.DirectoryInfo</TypeName>
     <TypeName>System.IO.FileInfo</TypeName>
     <TypeName>Deserialized.System.IO.DirectoryInfo</TypeName>
     <TypeName>Deserialized.System.IO.FileInfo</TypeName>
    </Types>
  </SelectionSet>
</SelectionSets>
```

<span data-ttu-id="157ab-125">De voorgaande selectieset wordt verwezen in de `ViewSelectedBy` element van een tabelweergave.</span><span class="sxs-lookup"><span data-stu-id="157ab-125">The previous selection set is referenced in the `ViewSelectedBy` element of a table view.</span></span>

```xml
<ViewDefinitions>
  <View>
    <Name>Files</Name>
    <ViewSelectedBy>
      <SelectionSetName>FileSystemTypes</SelectionSetName>
    </ViewSelectedBy>
    <TableControl>...</TableControl>
  </View>
</ViewDefinitions>

```

## <a name="xml-elements"></a><span data-ttu-id="157ab-126">XML-elementen</span><span class="sxs-lookup"><span data-stu-id="157ab-126">XML Elements</span></span>

 <span data-ttu-id="157ab-127">Er is geen limiet voor het aantal opgegeven selectie die u kunt definiëren.</span><span class="sxs-lookup"><span data-stu-id="157ab-127">There is no limit to the number of selection sets that you can define.</span></span> <span data-ttu-id="157ab-128">De volgende XML-elementen worden gebruikt voor het maken van een verzameling selecteren.</span><span class="sxs-lookup"><span data-stu-id="157ab-128">The following XML elements are used to create a selection set.</span></span>

- <span data-ttu-id="157ab-129">De [SelectionSets](./selectionsets-element-format.md) element wordt gedefinieerd voor de sets met .NET-objecten waarnaar wordt verwezen door de weergaven en besturingselementen van het bestand opmaak.</span><span class="sxs-lookup"><span data-stu-id="157ab-129">The [SelectionSets](./selectionsets-element-format.md) element defines the sets of .NET objects that are referenced by the views and controls of the formatting file.</span></span>

- <span data-ttu-id="157ab-130">De [SelectionSet](./selectionset-element-format.md) element wordt gedefinieerd voor één set met .NET-objecten.</span><span class="sxs-lookup"><span data-stu-id="157ab-130">The [SelectionSet](./selectionset-element-format.md) element defines a single set of .NET objects.</span></span>

- <span data-ttu-id="157ab-131">De [naam](./name-element-for-selectionset-format.md) element Hiermee geeft u de naam die wordt gebruikt om te verwijzen naar de selectieset.</span><span class="sxs-lookup"><span data-stu-id="157ab-131">The [Name](./name-element-for-selectionset-format.md) element specifies the name that is used to reference the selection set.</span></span>

- <span data-ttu-id="157ab-132">De [typen](./types-element-for-selectionset-format.md) element Hiermee geeft u de .NET-typen van de objecten van de selectie is ingesteld.</span><span class="sxs-lookup"><span data-stu-id="157ab-132">The [Types](./types-element-for-selectionset-format.md) element specifies the .NET types of the objects of the selection set.</span></span> <span data-ttu-id="157ab-133">(In de opmaak van bestanden, objecten zijn opgegeven door hun .NET-type.)</span><span class="sxs-lookup"><span data-stu-id="157ab-133">(Within formatting files, objects are specified by their .NET type.)</span></span>

 <span data-ttu-id="157ab-134">De volgende XML-elementen worden gebruikt om op te geven van een selectieset.</span><span class="sxs-lookup"><span data-stu-id="157ab-134">The following XML elements are used to specify a selection set.</span></span>

- <span data-ttu-id="157ab-135">Het volgende element Hiermee geeft u de selectie is ingesteld op in de definities van de weergave gebruiken:</span><span class="sxs-lookup"><span data-stu-id="157ab-135">The following element specifies the selection set to use in all the definitions of the view:</span></span>

    - [<span data-ttu-id="157ab-136">SelectionSetName-Element voor ViewSelectedBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="157ab-136">SelectionSetName Element for ViewSelectedBy (Format)</span></span>](./selectionsetname-element-for-viewselectedby-format.md)

    - [<span data-ttu-id="157ab-137">SelectionSetName-Element voor EntrySelectedBy voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="157ab-137">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

- <span data-ttu-id="157ab-138">De volgende elementen geeft u de selectieset die worden gebruikt door de definitie van een enkelvoudige weergave:</span><span class="sxs-lookup"><span data-stu-id="157ab-138">The following elements specify the selection set used by a single view definition:</span></span>

    - [<span data-ttu-id="157ab-139">SelectionSetName-Element voor EntrySelectedBy voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="157ab-139">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

    - [<span data-ttu-id="157ab-140">SelectionSetName-Element voor EntrySelectedBy voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="157ab-140">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

    - [<span data-ttu-id="157ab-141">SelectionSetName-Element voor EntrySelectedBy voor WideControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="157ab-141">SelectionSetName Element for EntrySelectedBy for WideControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

    - [<span data-ttu-id="157ab-142">SelectionSetName-Element voor EntrySelectedBy voor CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="157ab-142">SelectionSetName Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

- <span data-ttu-id="157ab-143">De volgende elementen selectie opgeven die worden gebruikt door de gemeenschappelijke en definities van besturingselement weer te geven:</span><span class="sxs-lookup"><span data-stu-id="157ab-143">The following elements specify the selection set used by common and view control definitions:</span></span>

    - [<span data-ttu-id="157ab-144">SelectionSetName-Element voor EntrySelectedBy voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="157ab-144">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)

    - [<span data-ttu-id="157ab-145">SelectionSetName-Element voor EntrySelectedBy voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="157ab-145">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format.md)

- <span data-ttu-id="157ab-146">De volgende elementen geeft u de selectieset die wordt gebruikt bij het definiëren van welk object om uit te vouwen:</span><span class="sxs-lookup"><span data-stu-id="157ab-146">The following elements specify the selection set used when you define which object to expand:</span></span>

    - [<span data-ttu-id="157ab-147">SelectionSetName-Element voor EntrySelectedBy voor EnumerableExpansion (indeling)</span><span class="sxs-lookup"><span data-stu-id="157ab-147">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

- <span data-ttu-id="157ab-148">De selectieset die worden gebruikt door de selectie voorwaarden opgeven die de volgende elementen.</span><span class="sxs-lookup"><span data-stu-id="157ab-148">The following elements specify the selection set used by selection conditions.</span></span>

    - [<span data-ttu-id="157ab-149">SelectionSetName-Element voor SelectionCondition voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="157ab-149">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

    - [<span data-ttu-id="157ab-150">SelectionSetName-Element voor SelectionCondition voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="157ab-150">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

    - [<span data-ttu-id="157ab-151">SelectionSetName-Element voor SelectionCondition voor CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="157ab-151">SelectionSetName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

    - [<span data-ttu-id="157ab-152">SelectionSetName-Element voor SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (indeling)</span><span class="sxs-lookup"><span data-stu-id="157ab-152">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

    - [<span data-ttu-id="157ab-153">SelectionSetName-Element voor SelectionCondition voor EntrySelectedBy voor ListEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="157ab-153">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)

    - [<span data-ttu-id="157ab-154">SelectionSetName-Element voor SelectionCondition voor EntrySelectedBy voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="157ab-154">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

    - [<span data-ttu-id="157ab-155">SelectionSetName-Element voor SelectionCondition voor EntrySelectedBy voor WideEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="157ab-155">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

    - [<span data-ttu-id="157ab-156">SelectionSetName-Element voor SelectionCondition voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="157ab-156">SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)

## <a name="see-also"></a><span data-ttu-id="157ab-157">Zie ook</span><span class="sxs-lookup"><span data-stu-id="157ab-157">See Also</span></span>

[<span data-ttu-id="157ab-158">SelectionSets</span><span class="sxs-lookup"><span data-stu-id="157ab-158">SelectionSets</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="157ab-159">SelectionSet</span><span class="sxs-lookup"><span data-stu-id="157ab-159">SelectionSet</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="157ab-160">Naam</span><span class="sxs-lookup"><span data-stu-id="157ab-160">Name</span></span>](./name-element-for-selectionset-format.md)

[<span data-ttu-id="157ab-161">Types</span><span class="sxs-lookup"><span data-stu-id="157ab-161">Types</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="157ab-162">PowerShell-bestanden voor opmaak</span><span class="sxs-lookup"><span data-stu-id="157ab-162">PowerShell Formatting Files</span></span>](./powershell-formatting-files.md)

[<span data-ttu-id="157ab-163">Voorwaarden voor wanneer gegevens worden weergegeven definiëren</span><span class="sxs-lookup"><span data-stu-id="157ab-163">Defining Conditions for when Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="157ab-164">Schrijven van een PowerShell-opmaak en typen bestand</span><span class="sxs-lookup"><span data-stu-id="157ab-164">Writing a PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
