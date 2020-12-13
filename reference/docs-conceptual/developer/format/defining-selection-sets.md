---
ms.date: 09/13/2016
ms.topic: reference
title: Selectiereeksen definiëren
description: Selectiereeksen definiëren
ms.openlocfilehash: d709a368a45623d56fdbf4e98a11a5e5f8a193fa
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92648256"
---
# <a name="defining-selection-sets"></a><span data-ttu-id="20bd0-103">Selectiereeksen definiëren</span><span class="sxs-lookup"><span data-stu-id="20bd0-103">Defining Selection Sets</span></span>

<span data-ttu-id="20bd0-104">Wanneer u meerdere weer gaven en besturings elementen maakt, kunt u sets van objecten definiëren die worden aangeduid als selectie sets.</span><span class="sxs-lookup"><span data-stu-id="20bd0-104">When creating multiple views and controls, you can define sets of objects that are referred to as selection sets.</span></span> <span data-ttu-id="20bd0-105">Met een selectieset kunt u de objecten één keer definiëren, zonder dat u ze herhaaldelijk hoeft te definiëren voor elke weer gave of elk besturings element.</span><span class="sxs-lookup"><span data-stu-id="20bd0-105">A selection set enables you to define the objects one time, without having to define them repeatedly for each view or control.</span></span> <span data-ttu-id="20bd0-106">Selectie sets worden meestal gebruikt wanneer u een set gerelateerde .NET-objecten hebt.</span><span class="sxs-lookup"><span data-stu-id="20bd0-106">Typically, selection sets are used when you have a set of related .NET objects.</span></span> <span data-ttu-id="20bd0-107">Bijvoorbeeld, het `FileSystem` Opmaak bestand (FileSystem.format.ps1XML) definieert een selectie reeks van de bestandssysteem typen die door verschillende weer gaven worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="20bd0-107">For example, The `FileSystem` formatting file (FileSystem.format.ps1xml) defines a selection set of the file system types that several views use.</span></span>

## <a name="where-selection-sets-are-defined-and-referenced"></a><span data-ttu-id="20bd0-108">Waar worden selectie sets gedefinieerd en waarnaar wordt verwezen</span><span class="sxs-lookup"><span data-stu-id="20bd0-108">Where Selection Sets are Defined and Referenced</span></span>

<span data-ttu-id="20bd0-109">U definieert selectie sets als onderdeel van de algemene gegevens die kunnen worden gebruikt door alle weer gaven en besturings elementen die in het opmaak bestand zijn gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="20bd0-109">You define selection sets as part of the common data that can be used by all the views and controls defined in the formatting file.</span></span> <span data-ttu-id="20bd0-110">In het volgende voor beeld ziet u hoe u drie selectie sets definieert.</span><span class="sxs-lookup"><span data-stu-id="20bd0-110">The following example shows how to define three selection sets.</span></span>

```xml
<Configuration>
  <SelectionSets>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
  </SelectionSets>
</Configuration>
```

<span data-ttu-id="20bd0-111">U kunt op de volgende manieren naar een selectie sets verwijzen:</span><span class="sxs-lookup"><span data-stu-id="20bd0-111">You can reference a selection sets in the following ways:</span></span>

- <span data-ttu-id="20bd0-112">Elke weer gave bevat een `ViewSelectedBy` element dat bepaalt welke objecten worden weer gegeven met behulp van de weer gave.</span><span class="sxs-lookup"><span data-stu-id="20bd0-112">Each view has a `ViewSelectedBy` element that defines which objects are displayed by using the view.</span></span> <span data-ttu-id="20bd0-113">Het `ViewSelectedBy` element heeft een `SelectionSetName` onderliggend element waarmee de selectieset wordt opgegeven die alle definities van de weer gave gebruiken.</span><span class="sxs-lookup"><span data-stu-id="20bd0-113">The `ViewSelectedBy` element has a `SelectionSetName` child element that specifies the selection set that all the definitions of the view use.</span></span> <span data-ttu-id="20bd0-114">Er is geen beperking voor het aantal selectie sets waarnaar u kunt verwijzen vanuit een weer gave.</span><span class="sxs-lookup"><span data-stu-id="20bd0-114">There is no restriction on the number of selection sets that you can reference from a view.</span></span>

- <span data-ttu-id="20bd0-115">In elke definitie van een weer gave of besturings element `EntrySelectedBy` definieert het element welke objecten worden weer gegeven met behulp van de definitie.</span><span class="sxs-lookup"><span data-stu-id="20bd0-115">In each definition of a view or control, the `EntrySelectedBy` element defines which objects are displayed by using that definition.</span></span> <span data-ttu-id="20bd0-116">Normaal gesp roken bevat een weer gave of besturings element slechts één definitie, zodat de objecten door het element worden gedefinieerd `ViewSelectedBy` .</span><span class="sxs-lookup"><span data-stu-id="20bd0-116">Typically a view or control has only one definition so the objects are defined by the `ViewSelectedBy` element.</span></span> <span data-ttu-id="20bd0-117">Het `EntrySelectedBy` element van de definitie heeft een `SelectionSetName` onderliggend element waarmee de selectieset wordt opgegeven.</span><span class="sxs-lookup"><span data-stu-id="20bd0-117">The `EntrySelectedBy` element of the definition has a `SelectionSetName` child element that specifies the selection set.</span></span> <span data-ttu-id="20bd0-118">Als u de selectie sets voor een definitie opgeeft, kunt u geen van de onderliggende elementen van het element opgeven `EntrySelectedBy` .</span><span class="sxs-lookup"><span data-stu-id="20bd0-118">If you specify the selection set for a definition, you cannot specify any of the other child elements of the `EntrySelectedBy` element.</span></span>

- <span data-ttu-id="20bd0-119">In elke definitie van een weer gave of besturings element `SelectionCondition` kan het element worden gebruikt om een voor waarde op te geven voor het gebruik van de definitie.</span><span class="sxs-lookup"><span data-stu-id="20bd0-119">In each definition of a view or control, the `SelectionCondition` element can be used to specify a condition for when the definition is used.</span></span> <span data-ttu-id="20bd0-120">Het `SelectionCondition` element heeft een `SelectionSetName` onderliggend element waarmee de selectieset wordt opgegeven waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="20bd0-120">The `SelectionCondition` element has a `SelectionSetName` child element that specifies the selection set that triggers the condition.</span></span> <span data-ttu-id="20bd0-121">De voor waarde wordt geactiveerd wanneer een van de objecten die in de selectieset zijn gedefinieerd, worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="20bd0-121">The condition is triggered when any of the objects defined in the selection set are displayed.</span></span> <span data-ttu-id="20bd0-122">Zie voor [waarden definiëren voor wanneer gegevens worden weer gegeven](./defining-conditions-for-displaying-data.md)voor meer informatie over het instellen van deze voor waarden.</span><span class="sxs-lookup"><span data-stu-id="20bd0-122">For more information about how to set these conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="selection-set-example"></a><span data-ttu-id="20bd0-123">Voor beeld van selectie sets</span><span class="sxs-lookup"><span data-stu-id="20bd0-123">Selection Set Example</span></span>

<span data-ttu-id="20bd0-124">In het volgende voor beeld ziet u een selectie reeks die rechtstreeks afkomstig is uit het `FileSystem` Opmaak bestand dat wordt meegeleverd met Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="20bd0-124">The following example shows a selection set that is taken directly from the `FileSystem` formatting file provided by Windows PowerShell.</span></span> <span data-ttu-id="20bd0-125">Zie [Windows Power shell-indelings bestanden](./powershell-formatting-files.md)voor meer informatie over andere Windows Power shell-indelings bestanden.</span><span class="sxs-lookup"><span data-stu-id="20bd0-125">For more information about other Windows PowerShell formatting files, see [Windows PowerShell Formatting Files](./powershell-formatting-files.md).</span></span>

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

<span data-ttu-id="20bd0-126">Er wordt naar de vorige selectieset verwezen in het `ViewSelectedBy` element van een tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="20bd0-126">The previous selection set is referenced in the `ViewSelectedBy` element of a table view.</span></span>

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

## <a name="xml-elements"></a><span data-ttu-id="20bd0-127">XML-elementen</span><span class="sxs-lookup"><span data-stu-id="20bd0-127">XML Elements</span></span>

 <span data-ttu-id="20bd0-128">Er is geen limiet voor het aantal selectie sets dat u kunt definiëren.</span><span class="sxs-lookup"><span data-stu-id="20bd0-128">There is no limit to the number of selection sets that you can define.</span></span> <span data-ttu-id="20bd0-129">De volgende XML-elementen worden gebruikt voor het maken van een selectieset.</span><span class="sxs-lookup"><span data-stu-id="20bd0-129">The following XML elements are used to create a selection set.</span></span>

- <span data-ttu-id="20bd0-130">Het [SelectionSets](./selectionsets-element-format.md) -element definieert de sets .net-objecten waarnaar wordt verwezen door de weer gaven en besturings elementen van het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="20bd0-130">The [SelectionSets](./selectionsets-element-format.md) element defines the sets of .NET objects that are referenced by the views and controls of the formatting file.</span></span>

- <span data-ttu-id="20bd0-131">Met het element [selectionset](./selectionset-element-format.md) wordt één set .net-objecten gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="20bd0-131">The [SelectionSet](./selectionset-element-format.md) element defines a single set of .NET objects.</span></span>

- <span data-ttu-id="20bd0-132">Het element [name](./name-element-for-selectionset-format.md) bevat de naam die wordt gebruikt om te verwijzen naar de selectieset.</span><span class="sxs-lookup"><span data-stu-id="20bd0-132">The [Name](./name-element-for-selectionset-format.md) element specifies the name that is used to reference the selection set.</span></span>

- <span data-ttu-id="20bd0-133">Het element [types](./types-element-for-selectionset-format.md) specificeert de .net-typen van de objecten van de selectieset.</span><span class="sxs-lookup"><span data-stu-id="20bd0-133">The [Types](./types-element-for-selectionset-format.md) element specifies the .NET types of the objects of the selection set.</span></span> <span data-ttu-id="20bd0-134">(Bij het format teren van bestanden worden objecten door hun .NET-type opgegeven.)</span><span class="sxs-lookup"><span data-stu-id="20bd0-134">(Within formatting files, objects are specified by their .NET type.)</span></span>

 <span data-ttu-id="20bd0-135">De volgende XML-elementen worden gebruikt om een selectieset op te geven.</span><span class="sxs-lookup"><span data-stu-id="20bd0-135">The following XML elements are used to specify a selection set.</span></span>

- <span data-ttu-id="20bd0-136">Met het volgende element wordt de selectie ingesteld die moet worden gebruikt in alle definities van de weer gave:</span><span class="sxs-lookup"><span data-stu-id="20bd0-136">The following element specifies the selection set to use in all the definitions of the view:</span></span>

  - [<span data-ttu-id="20bd0-137">Het element SelectionSetName voor ViewSelectedBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="20bd0-137">SelectionSetName Element for ViewSelectedBy (Format)</span></span>](./selectionsetname-element-for-viewselectedby-format.md)

  - [<span data-ttu-id="20bd0-138">Het element SelectionSetName voor EntrySelectedBy voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="20bd0-138">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

- <span data-ttu-id="20bd0-139">De volgende elementen geven de selectieset op die wordt gebruikt door een enkele weergave definitie:</span><span class="sxs-lookup"><span data-stu-id="20bd0-139">The following elements specify the selection set used by a single view definition:</span></span>

  - [<span data-ttu-id="20bd0-140">Het element SelectionSetName voor EntrySelectedBy voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="20bd0-140">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

  - [<span data-ttu-id="20bd0-141">Het element SelectionSetName voor EntrySelectedBy voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="20bd0-141">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

  - [<span data-ttu-id="20bd0-142">Het element SelectionSetName voor EntrySelectedBy voor WideControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="20bd0-142">SelectionSetName Element for EntrySelectedBy for WideControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

  - [<span data-ttu-id="20bd0-143">Het element SelectionSetName voor EntrySelectedBy voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="20bd0-143">SelectionSetName Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

- <span data-ttu-id="20bd0-144">De volgende elementen geven de selectieset op die wordt gebruikt door algemene en besturings definities weer geven:</span><span class="sxs-lookup"><span data-stu-id="20bd0-144">The following elements specify the selection set used by common and view control definitions:</span></span>

  - [<span data-ttu-id="20bd0-145">Het element SelectionSetName voor EntrySelectedBy voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="20bd0-145">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)

  - [<span data-ttu-id="20bd0-146">Het element SelectionSetName voor EntrySelectedBy voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="20bd0-146">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format.md)

- <span data-ttu-id="20bd0-147">De volgende elementen geven de selectieset op die wordt gebruikt wanneer u definieert welk object moet worden uitgebreid:</span><span class="sxs-lookup"><span data-stu-id="20bd0-147">The following elements specify the selection set used when you define which object to expand:</span></span>

  - [<span data-ttu-id="20bd0-148">Het element SelectionSetName voor EntrySelectedBy voor EnumerableExpansion (opmaak)</span><span class="sxs-lookup"><span data-stu-id="20bd0-148">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

- <span data-ttu-id="20bd0-149">De volgende elementen geven de selectieset op die wordt gebruikt voor de selectie omstandigheden.</span><span class="sxs-lookup"><span data-stu-id="20bd0-149">The following elements specify the selection set used by selection conditions.</span></span>

  - [<span data-ttu-id="20bd0-150">Het element SelectionSetName voor SelectionCondition voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="20bd0-150">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

  - [<span data-ttu-id="20bd0-151">Het element SelectionSetName voor SelectionCondition voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="20bd0-151">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

  - [<span data-ttu-id="20bd0-152">Het element SelectionSetName voor SelectionCondition voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="20bd0-152">SelectionSetName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

  - [<span data-ttu-id="20bd0-153">Het element SelectionSetName voor SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (opmaak)</span><span class="sxs-lookup"><span data-stu-id="20bd0-153">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

  - [<span data-ttu-id="20bd0-154">Het element SelectionSetName voor SelectionCondition voor EntrySelectedBy voor ListEntry (opmaak)</span><span class="sxs-lookup"><span data-stu-id="20bd0-154">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)

  - [<span data-ttu-id="20bd0-155">Het element SelectionSetName voor SelectionCondition voor EntrySelectedBy voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="20bd0-155">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

  - [<span data-ttu-id="20bd0-156">Het element SelectionSetName voor SelectionCondition voor EntrySelectedBy voor WideEntry (opmaak)</span><span class="sxs-lookup"><span data-stu-id="20bd0-156">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

  - [<span data-ttu-id="20bd0-157">Het element SelectionSetName voor SelectionCondition voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="20bd0-157">SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)

## <a name="see-also"></a><span data-ttu-id="20bd0-158">Zie ook</span><span class="sxs-lookup"><span data-stu-id="20bd0-158">See Also</span></span>

[<span data-ttu-id="20bd0-159">SelectionSets</span><span class="sxs-lookup"><span data-stu-id="20bd0-159">SelectionSets</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="20bd0-160">Selectieset</span><span class="sxs-lookup"><span data-stu-id="20bd0-160">SelectionSet</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="20bd0-161">Naam</span><span class="sxs-lookup"><span data-stu-id="20bd0-161">Name</span></span>](./name-element-for-selectionset-format.md)

[<span data-ttu-id="20bd0-162">Typen</span><span class="sxs-lookup"><span data-stu-id="20bd0-162">Types</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="20bd0-163">PowerShell-opmaakbestanden</span><span class="sxs-lookup"><span data-stu-id="20bd0-163">PowerShell Formatting Files</span></span>](./powershell-formatting-files.md)

[<span data-ttu-id="20bd0-164">Voor waarden definiëren voor wanneer gegevens worden weer gegeven</span><span class="sxs-lookup"><span data-stu-id="20bd0-164">Defining Conditions for when Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="20bd0-165">Een Power shell-indeling en-typen bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="20bd0-165">Writing a PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
