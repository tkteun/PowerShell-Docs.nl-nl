---
title: Selectie sets definiëren | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 00dbb5ee-93d4-4914-a082-ef4d8b236b5c
caps.latest.revision: 16
ms.openlocfilehash: 95eeb037b3b9190fec1212a68029624993f3fd9f
ms.sourcegitcommit: 17d798a041851382b406ed789097843faf37692d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83692294"
---
# <a name="defining-selection-sets"></a><span data-ttu-id="fed1f-102">Selectiereeksen definiëren</span><span class="sxs-lookup"><span data-stu-id="fed1f-102">Defining Selection Sets</span></span>

<span data-ttu-id="fed1f-103">Wanneer u meerdere weer gaven en besturings elementen maakt, kunt u sets van objecten definiëren die worden aangeduid als selectie sets.</span><span class="sxs-lookup"><span data-stu-id="fed1f-103">When creating multiple views and controls, you can define sets of objects that are referred to as selection sets.</span></span> <span data-ttu-id="fed1f-104">Met een selectieset kunt u de objecten één keer definiëren, zonder dat u ze herhaaldelijk hoeft te definiëren voor elke weer gave of elk besturings element.</span><span class="sxs-lookup"><span data-stu-id="fed1f-104">A selection set enables you to define the objects one time, without having to define them repeatedly for each view or control.</span></span> <span data-ttu-id="fed1f-105">Selectie sets worden meestal gebruikt wanneer u een set gerelateerde .NET-objecten hebt.</span><span class="sxs-lookup"><span data-stu-id="fed1f-105">Typically, selection sets are used when you have a set of related .NET objects.</span></span> <span data-ttu-id="fed1f-106">Het `FileSystem` Opmaak bestand (bestands systeem. Format. ps1xml) definieert bijvoorbeeld een selectieset van de bestandssysteem typen die door verschillende weer gaven worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="fed1f-106">For example, The `FileSystem` formatting file (FileSystem.format.ps1xml) defines a selection set of the file system types that several views use.</span></span>

## <a name="where-selection-sets-are-defined-and-referenced"></a><span data-ttu-id="fed1f-107">Waar worden selectie sets gedefinieerd en waarnaar wordt verwezen</span><span class="sxs-lookup"><span data-stu-id="fed1f-107">Where Selection Sets are Defined and Referenced</span></span>

<span data-ttu-id="fed1f-108">U definieert selectie sets als onderdeel van de algemene gegevens die kunnen worden gebruikt door alle weer gaven en besturings elementen die in het opmaak bestand zijn gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="fed1f-108">You define selection sets as part of the common data that can be used by all the views and controls defined in the formatting file.</span></span> <span data-ttu-id="fed1f-109">In het volgende voor beeld ziet u hoe u drie selectie sets definieert.</span><span class="sxs-lookup"><span data-stu-id="fed1f-109">The following example shows how to define three selection sets.</span></span>

```xml
<Configuration>
  <SelectionSets>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
  </SelectionSets>
</Configuration>
```

<span data-ttu-id="fed1f-110">U kunt op de volgende manieren naar een selectie sets verwijzen:</span><span class="sxs-lookup"><span data-stu-id="fed1f-110">You can reference a selection sets in the following ways:</span></span>

- <span data-ttu-id="fed1f-111">Elke weer gave bevat een `ViewSelectedBy` element dat bepaalt welke objecten worden weer gegeven met behulp van de weer gave.</span><span class="sxs-lookup"><span data-stu-id="fed1f-111">Each view has a `ViewSelectedBy` element that defines which objects are displayed by using the view.</span></span> <span data-ttu-id="fed1f-112">Het `ViewSelectedBy` element heeft een `SelectionSetName` onderliggend element waarmee de selectieset wordt opgegeven die alle definities van de weer gave gebruiken.</span><span class="sxs-lookup"><span data-stu-id="fed1f-112">The `ViewSelectedBy` element has a `SelectionSetName` child element that specifies the selection set that all the definitions of the view use.</span></span> <span data-ttu-id="fed1f-113">Er is geen beperking voor het aantal selectie sets waarnaar u kunt verwijzen vanuit een weer gave.</span><span class="sxs-lookup"><span data-stu-id="fed1f-113">There is no restriction on the number of selection sets that you can reference from a view.</span></span>

- <span data-ttu-id="fed1f-114">In elke definitie van een weer gave of besturings element `EntrySelectedBy` definieert het element welke objecten worden weer gegeven met behulp van de definitie.</span><span class="sxs-lookup"><span data-stu-id="fed1f-114">In each definition of a view or control, the `EntrySelectedBy` element defines which objects are displayed by using that definition.</span></span> <span data-ttu-id="fed1f-115">Normaal gesp roken bevat een weer gave of besturings element slechts één definitie, zodat de objecten door het element worden gedefinieerd `ViewSelectedBy` .</span><span class="sxs-lookup"><span data-stu-id="fed1f-115">Typically a view or control has only one definition so the objects are defined by the `ViewSelectedBy` element.</span></span> <span data-ttu-id="fed1f-116">Het `EntrySelectedBy` element van de definitie heeft een `SelectionSetName` onderliggend element waarmee de selectieset wordt opgegeven.</span><span class="sxs-lookup"><span data-stu-id="fed1f-116">The `EntrySelectedBy` element of the definition has a `SelectionSetName` child element that specifies the selection set.</span></span> <span data-ttu-id="fed1f-117">Als u de selectie sets voor een definitie opgeeft, kunt u geen van de onderliggende elementen van het element opgeven `EntrySelectedBy` .</span><span class="sxs-lookup"><span data-stu-id="fed1f-117">If you specify the selection set for a definition, you cannot specify any of the other child elements of the `EntrySelectedBy` element.</span></span>

- <span data-ttu-id="fed1f-118">In elke definitie van een weer gave of besturings element `SelectionCondition` kan het element worden gebruikt om een voor waarde op te geven voor het gebruik van de definitie.</span><span class="sxs-lookup"><span data-stu-id="fed1f-118">In each definition of a view or control, the `SelectionCondition` element can be used to specify a condition for when the definition is used.</span></span> <span data-ttu-id="fed1f-119">Het `SelectionCondition` element heeft een `SelectionSetName` onderliggend element waarmee de selectieset wordt opgegeven waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="fed1f-119">The `SelectionCondition` element has a `SelectionSetName` child element that specifies the selection set that triggers the condition.</span></span> <span data-ttu-id="fed1f-120">De voor waarde wordt geactiveerd wanneer een van de objecten die in de selectieset zijn gedefinieerd, worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="fed1f-120">The condition is triggered when any of the objects defined in the selection set are displayed.</span></span> <span data-ttu-id="fed1f-121">Zie voor [waarden definiëren voor wanneer gegevens worden weer gegeven](./defining-conditions-for-displaying-data.md)voor meer informatie over het instellen van deze voor waarden.</span><span class="sxs-lookup"><span data-stu-id="fed1f-121">For more information about how to set these conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="selection-set-example"></a><span data-ttu-id="fed1f-122">Voor beeld van selectie sets</span><span class="sxs-lookup"><span data-stu-id="fed1f-122">Selection Set Example</span></span>

<span data-ttu-id="fed1f-123">In het volgende voor beeld ziet u een selectie reeks die rechtstreeks afkomstig is uit het `FileSystem` Opmaak bestand dat wordt meegeleverd met Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="fed1f-123">The following example shows a selection set that is taken directly from the `FileSystem` formatting file provided by Windows PowerShell.</span></span> <span data-ttu-id="fed1f-124">Zie [Windows Power shell-indelings bestanden](./powershell-formatting-files.md)voor meer informatie over andere Windows Power shell-indelings bestanden.</span><span class="sxs-lookup"><span data-stu-id="fed1f-124">For more information about other Windows PowerShell formatting files, see [Windows PowerShell Formatting Files](./powershell-formatting-files.md).</span></span>

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

<span data-ttu-id="fed1f-125">Er wordt naar de vorige selectieset verwezen in het `ViewSelectedBy` element van een tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="fed1f-125">The previous selection set is referenced in the `ViewSelectedBy` element of a table view.</span></span>

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

## <a name="xml-elements"></a><span data-ttu-id="fed1f-126">XML-elementen</span><span class="sxs-lookup"><span data-stu-id="fed1f-126">XML Elements</span></span>

 <span data-ttu-id="fed1f-127">Er is geen limiet voor het aantal selectie sets dat u kunt definiëren.</span><span class="sxs-lookup"><span data-stu-id="fed1f-127">There is no limit to the number of selection sets that you can define.</span></span> <span data-ttu-id="fed1f-128">De volgende XML-elementen worden gebruikt voor het maken van een selectieset.</span><span class="sxs-lookup"><span data-stu-id="fed1f-128">The following XML elements are used to create a selection set.</span></span>

- <span data-ttu-id="fed1f-129">Het [SelectionSets](./selectionsets-element-format.md) -element definieert de sets .net-objecten waarnaar wordt verwezen door de weer gaven en besturings elementen van het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="fed1f-129">The [SelectionSets](./selectionsets-element-format.md) element defines the sets of .NET objects that are referenced by the views and controls of the formatting file.</span></span>

- <span data-ttu-id="fed1f-130">Met het element [selectionset](./selectionset-element-format.md) wordt één set .net-objecten gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="fed1f-130">The [SelectionSet](./selectionset-element-format.md) element defines a single set of .NET objects.</span></span>

- <span data-ttu-id="fed1f-131">Het element [name](./name-element-for-selectionset-format.md) bevat de naam die wordt gebruikt om te verwijzen naar de selectieset.</span><span class="sxs-lookup"><span data-stu-id="fed1f-131">The [Name](./name-element-for-selectionset-format.md) element specifies the name that is used to reference the selection set.</span></span>

- <span data-ttu-id="fed1f-132">Het element [types](./types-element-for-selectionset-format.md) specificeert de .net-typen van de objecten van de selectieset.</span><span class="sxs-lookup"><span data-stu-id="fed1f-132">The [Types](./types-element-for-selectionset-format.md) element specifies the .NET types of the objects of the selection set.</span></span> <span data-ttu-id="fed1f-133">(Bij het format teren van bestanden worden objecten door hun .NET-type opgegeven.)</span><span class="sxs-lookup"><span data-stu-id="fed1f-133">(Within formatting files, objects are specified by their .NET type.)</span></span>

 <span data-ttu-id="fed1f-134">De volgende XML-elementen worden gebruikt om een selectieset op te geven.</span><span class="sxs-lookup"><span data-stu-id="fed1f-134">The following XML elements are used to specify a selection set.</span></span>

- <span data-ttu-id="fed1f-135">Met het volgende element wordt de selectie ingesteld die moet worden gebruikt in alle definities van de weer gave:</span><span class="sxs-lookup"><span data-stu-id="fed1f-135">The following element specifies the selection set to use in all the definitions of the view:</span></span>

  - [<span data-ttu-id="fed1f-136">Het element SelectionSetName voor ViewSelectedBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="fed1f-136">SelectionSetName Element for ViewSelectedBy (Format)</span></span>](./selectionsetname-element-for-viewselectedby-format.md)

  - [<span data-ttu-id="fed1f-137">Het element SelectionSetName voor EntrySelectedBy voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="fed1f-137">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

- <span data-ttu-id="fed1f-138">De volgende elementen geven de selectieset op die wordt gebruikt door een enkele weergave definitie:</span><span class="sxs-lookup"><span data-stu-id="fed1f-138">The following elements specify the selection set used by a single view definition:</span></span>

  - [<span data-ttu-id="fed1f-139">Het element SelectionSetName voor EntrySelectedBy voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="fed1f-139">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

  - [<span data-ttu-id="fed1f-140">Het element SelectionSetName voor EntrySelectedBy voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="fed1f-140">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

  - [<span data-ttu-id="fed1f-141">Het element SelectionSetName voor EntrySelectedBy voor WideControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="fed1f-141">SelectionSetName Element for EntrySelectedBy for WideControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

  - [<span data-ttu-id="fed1f-142">Het element SelectionSetName voor EntrySelectedBy voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="fed1f-142">SelectionSetName Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

- <span data-ttu-id="fed1f-143">De volgende elementen geven de selectieset op die wordt gebruikt door algemene en besturings definities weer geven:</span><span class="sxs-lookup"><span data-stu-id="fed1f-143">The following elements specify the selection set used by common and view control definitions:</span></span>

  - [<span data-ttu-id="fed1f-144">Het element SelectionSetName voor EntrySelectedBy voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="fed1f-144">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)

  - [<span data-ttu-id="fed1f-145">Het element SelectionSetName voor EntrySelectedBy voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="fed1f-145">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format.md)

- <span data-ttu-id="fed1f-146">De volgende elementen geven de selectieset op die wordt gebruikt wanneer u definieert welk object moet worden uitgebreid:</span><span class="sxs-lookup"><span data-stu-id="fed1f-146">The following elements specify the selection set used when you define which object to expand:</span></span>

  - [<span data-ttu-id="fed1f-147">Het element SelectionSetName voor EntrySelectedBy voor EnumerableExpansion (opmaak)</span><span class="sxs-lookup"><span data-stu-id="fed1f-147">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

- <span data-ttu-id="fed1f-148">De volgende elementen geven de selectieset op die wordt gebruikt voor de selectie omstandigheden.</span><span class="sxs-lookup"><span data-stu-id="fed1f-148">The following elements specify the selection set used by selection conditions.</span></span>

  - [<span data-ttu-id="fed1f-149">Het element SelectionSetName voor SelectionCondition voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="fed1f-149">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

  - [<span data-ttu-id="fed1f-150">Het element SelectionSetName voor SelectionCondition voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="fed1f-150">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

  - [<span data-ttu-id="fed1f-151">Het element SelectionSetName voor SelectionCondition voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="fed1f-151">SelectionSetName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

  - [<span data-ttu-id="fed1f-152">Het element SelectionSetName voor SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (opmaak)</span><span class="sxs-lookup"><span data-stu-id="fed1f-152">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

  - [<span data-ttu-id="fed1f-153">Het element SelectionSetName voor SelectionCondition voor EntrySelectedBy voor ListEntry (opmaak)</span><span class="sxs-lookup"><span data-stu-id="fed1f-153">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)

  - [<span data-ttu-id="fed1f-154">Het element SelectionSetName voor SelectionCondition voor EntrySelectedBy voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="fed1f-154">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

  - [<span data-ttu-id="fed1f-155">Het element SelectionSetName voor SelectionCondition voor EntrySelectedBy voor WideEntry (opmaak)</span><span class="sxs-lookup"><span data-stu-id="fed1f-155">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

  - [<span data-ttu-id="fed1f-156">Het element SelectionSetName voor SelectionCondition voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="fed1f-156">SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)

## <a name="see-also"></a><span data-ttu-id="fed1f-157">Zie ook</span><span class="sxs-lookup"><span data-stu-id="fed1f-157">See Also</span></span>

[<span data-ttu-id="fed1f-158">SelectionSets</span><span class="sxs-lookup"><span data-stu-id="fed1f-158">SelectionSets</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="fed1f-159">Selectieset</span><span class="sxs-lookup"><span data-stu-id="fed1f-159">SelectionSet</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="fed1f-160">Naam</span><span class="sxs-lookup"><span data-stu-id="fed1f-160">Name</span></span>](./name-element-for-selectionset-format.md)

[<span data-ttu-id="fed1f-161">Typen</span><span class="sxs-lookup"><span data-stu-id="fed1f-161">Types</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="fed1f-162">PowerShell-opmaakbestanden</span><span class="sxs-lookup"><span data-stu-id="fed1f-162">PowerShell Formatting Files</span></span>](./powershell-formatting-files.md)

[<span data-ttu-id="fed1f-163">Voor waarden definiëren voor wanneer gegevens worden weer gegeven</span><span class="sxs-lookup"><span data-stu-id="fed1f-163">Defining Conditions for when Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="fed1f-164">Een Power shell-indeling en-typen bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="fed1f-164">Writing a PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
