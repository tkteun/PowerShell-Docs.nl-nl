---
title: SelectionCondition-Element voor EntrySelectedBy voor besturingselementen voor de configuratie (-indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f23ef405-0f1e-4607-b3f4-4017b7ead106
caps.latest.revision: 7
ms.openlocfilehash: a5098da55d0a63272a121b973cb05e26dc47e3e1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845512"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format"></a><span data-ttu-id="edaff-102">Het element SelectionCondition voor EntrySelectedBy voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="edaff-102">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

<span data-ttu-id="edaff-103">Hiermee definieert u een voorwaarde die moet aanwezig zijn voor de besturingselementdefinitie van een algemene moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="edaff-103">Defines a condition that must exist for a common control definition to be used.</span></span> <span data-ttu-id="edaff-104">Dit element wordt gebruikt bij het definiëren van een algemene besturingselement dat kan worden gebruikt door alle weergaven in de opmaak-bestand.</span><span class="sxs-lookup"><span data-stu-id="edaff-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="edaff-105">Configuratie-Element (indeling) besturingselementen Element van configuratie (-indeling) besturingselement Element controles voor configuratie (-indeling) CustomControl-Element voor configuratie (-indeling) CustomEntries-Element voor CustomControl voor besturingselementen voor het besturingselement Configuratie (-indeling) CustomEntry-Element voor CustomControl controles voor configuratie (-indeling) EntrySelectedBy-Element voor CustomEntry controles voor configuratie (-indeling) SelectionCondition-Element voor EntrySelectedBy voor CustomEntry voor Configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="edaff-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Controls for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="edaff-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="edaff-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="edaff-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="edaff-107">Attributes and Elements</span></span>

<span data-ttu-id="edaff-108">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `SelectionCondition` element.</span><span class="sxs-lookup"><span data-stu-id="edaff-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="edaff-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="edaff-109">Attributes</span></span>

<span data-ttu-id="edaff-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="edaff-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="edaff-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="edaff-111">Child Elements</span></span>

|<span data-ttu-id="edaff-112">Element</span><span class="sxs-lookup"><span data-stu-id="edaff-112">Element</span></span>|<span data-ttu-id="edaff-113">Description</span><span class="sxs-lookup"><span data-stu-id="edaff-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="edaff-114">PropertyName-Element voor SelectionCondition voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="edaff-114">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="edaff-115">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="edaff-115">Optional element.</span></span><br /><br /> <span data-ttu-id="edaff-116">Hiermee geeft u een .NET-eigenschap die de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="edaff-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="edaff-117">ScriptBlock-Element voor SelectionCondition voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="edaff-117">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="edaff-118">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="edaff-118">Optional element.</span></span><br /><br /> <span data-ttu-id="edaff-119">Hiermee geeft u het script dat de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="edaff-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="edaff-120">SelectionSetName-Element voor SelectionCondition voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="edaff-120">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="edaff-121">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="edaff-121">Optional element.</span></span><br /><br /> <span data-ttu-id="edaff-122">Hiermee geeft u de set van .NET-typen die de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="edaff-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="edaff-123">TypeName-Element voor SelectionCondition voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="edaff-123">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="edaff-124">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="edaff-124">Optional element.</span></span><br /><br /> <span data-ttu-id="edaff-125">Hiermee geeft u een .NET-type dat de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="edaff-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="edaff-126">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="edaff-126">Parent Elements</span></span>

|<span data-ttu-id="edaff-127">Element</span><span class="sxs-lookup"><span data-stu-id="edaff-127">Element</span></span>|<span data-ttu-id="edaff-128">Description</span><span class="sxs-lookup"><span data-stu-id="edaff-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="edaff-129">EntrySelectedBy-Element voor CustomEntry voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="edaff-129">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="edaff-130">Hiermee definieert u de .NET-typen die gebruikmaken van deze vermelding van de definitie van de algemene controle.</span><span class="sxs-lookup"><span data-stu-id="edaff-130">Defines the .NET types that use this entry of the common control definition.</span></span>|

## <a name="remarks"></a><span data-ttu-id="edaff-131">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="edaff-131">Remarks</span></span>

<span data-ttu-id="edaff-132">De volgende richtlijnen moeten worden gevolgd bij het definiëren van een voorwaarde selecteren:</span><span class="sxs-lookup"><span data-stu-id="edaff-132">The following guidelines must be followed when defining a selection condition:</span></span>

- <span data-ttu-id="edaff-133">De selectievoorwaarde moet de naam van een minimaal één eigenschap of een scriptblok opgeven, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="edaff-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="edaff-134">De selectievoorwaarde een willekeurig aantal .NET-typen kunt opgeven of de selectie wordt ingesteld, maar niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="edaff-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="edaff-135">Zie voor meer informatie over hoe voorwaarden van de selectie kunnen worden gebruikt, [definiëren voorwaarden voor wanneer gegevens worden weergegeven](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="edaff-135">For more information about how selection conditions can be used, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="edaff-136">Zie ook</span><span class="sxs-lookup"><span data-stu-id="edaff-136">See Also</span></span>

[<span data-ttu-id="edaff-137">PropertyName-Element voor SelectionCondition voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="edaff-137">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="edaff-138">ScriptBlock-Element voor SelectionCondition voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="edaff-138">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="edaff-139">SelectionSetName-Element voor SelectionCondition voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="edaff-139">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="edaff-140">TypeName-Element voor SelectionCondition voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="edaff-140">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="edaff-141">EntrySelectedBy-Element voor CustomEntry voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="edaff-141">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="edaff-142">Schrijven van een Windows PowerShell opmaak en het bestand van het type</span><span class="sxs-lookup"><span data-stu-id="edaff-142">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
