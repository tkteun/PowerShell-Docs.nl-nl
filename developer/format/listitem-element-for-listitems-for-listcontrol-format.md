---
title: Lijstitem-Element voor ListItems voor ListControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f96f4f5-8bd5-43ed-95e7-a7358115999a
caps.latest.revision: 11
ms.openlocfilehash: 1e0a1b2d20853650328b8cfd1513a08f7e167cd6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065764"
---
# <a name="listitem-element-for-listitems-for-listcontrol-format"></a><span data-ttu-id="829a3-102">Het element ListItem voor ListItems voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="829a3-102">ListItem Element for ListItems for ListControl (Format)</span></span>

<span data-ttu-id="829a3-103">Hiermee definieert de eigenschap of het script waarvan de waarde wordt weergegeven in een rij in de lijstweergave.</span><span class="sxs-lookup"><span data-stu-id="829a3-103">Defines the property or script whose value is displayed in a row of the list view.</span></span>

<span data-ttu-id="829a3-104">Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) ListControl Element (indeling) ListEntries Element voor ListControl (indeling) ListEntry-Element voor ListControl (indeling) ListItems Element voor ListControl (indeling) ListItem voor ListControl-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="829a3-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListControl (Format) ListItems Element for ListControl (Format) ListItem for ListControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="829a3-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="829a3-105">Syntax</span></span>

```xml
<ListItem>
  <PropertyName>PropertyToDisplay</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <Label>LabelToDisplay</Label>
  <FormatString>FormatPattern</FormatString>
  <ItemSelectionCondition>...</ItemSelectionCondition>
</ListItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="829a3-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="829a3-106">Attributes and Elements</span></span>

<span data-ttu-id="829a3-107">De volgende secties worden de kenmerken, de onderliggende elementen en het bovenliggende element van de `ListItem` element.</span><span class="sxs-lookup"><span data-stu-id="829a3-107">The following sections describe the attributes, child elements, and parent element of the `ListItem` element.</span></span> <span data-ttu-id="829a3-108">Slechts één eigenschap of het script kan worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="829a3-108">Only one property or script can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="829a3-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="829a3-109">Attributes</span></span>

<span data-ttu-id="829a3-110">Geen</span><span class="sxs-lookup"><span data-stu-id="829a3-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="829a3-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="829a3-111">Child Elements</span></span>

|<span data-ttu-id="829a3-112">Element</span><span class="sxs-lookup"><span data-stu-id="829a3-112">Element</span></span>|<span data-ttu-id="829a3-113">Description</span><span class="sxs-lookup"><span data-stu-id="829a3-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="829a3-114">FormatString-Element voor ListItem voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="829a3-114">FormatString Element for ListItem for ListControl (Format)</span></span>](./formatstring-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="829a3-115">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="829a3-115">Optional element.</span></span><br /><br /> <span data-ttu-id="829a3-116">Hiermee geeft u een opmaaktekenreeks waarmee wordt gedefinieerd hoe de waarde voor eigenschap of het script wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="829a3-116">Specifies a format string that defines how the property or script value is displayed.</span></span>|
|[<span data-ttu-id="829a3-117">ItemSelectionCondition-Element voor ListItem voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="829a3-117">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="829a3-118">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="829a3-118">Optional element.</span></span><br /><br /> <span data-ttu-id="829a3-119">Hiermee definieert u de voorwaarde die moet bestaan voor dit item in de lijst moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="829a3-119">Defines the condition that must exist for this list item to be used.</span></span>|
|[<span data-ttu-id="829a3-120">Label-Element voor ListItem voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="829a3-120">Label Element for ListItem for ListControl (Format)</span></span>](./label-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="829a3-121">Optioneel element</span><span class="sxs-lookup"><span data-stu-id="829a3-121">Optional element</span></span><br /><br /> <span data-ttu-id="829a3-122">Hiermee geeft u het label dat wordt weergegeven aan de linkerkant van de waarde voor eigenschap of het script in de rij.</span><span class="sxs-lookup"><span data-stu-id="829a3-122">Specifies the label that is displayed to the left of the property or script value in the row.</span></span>|
|[<span data-ttu-id="829a3-123">PropertyName-Element voor ListItem voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="829a3-123">PropertyName Element for ListItem for ListControl (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="829a3-124">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="829a3-124">Optional element.</span></span><br /><br /> <span data-ttu-id="829a3-125">Hiermee geeft u de .NET-eigenschap waarvan de waarde wordt weergegeven in de rij.</span><span class="sxs-lookup"><span data-stu-id="829a3-125">Specifies the .NET property whose value is displayed in the row.</span></span>|
|[<span data-ttu-id="829a3-126">ScriptBlock-Element voor ListItem voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="829a3-126">ScriptBlock Element for ListItem for ListControl (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="829a3-127">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="829a3-127">Optional element.</span></span><br /><br /> <span data-ttu-id="829a3-128">Hiermee geeft u het script waarvan de waarde wordt weergegeven in de rij.</span><span class="sxs-lookup"><span data-stu-id="829a3-128">Specifies the script whose value is displayed in the row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="829a3-129">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="829a3-129">Parent Elements</span></span>

|<span data-ttu-id="829a3-130">Element</span><span class="sxs-lookup"><span data-stu-id="829a3-130">Element</span></span>|<span data-ttu-id="829a3-131">Description</span><span class="sxs-lookup"><span data-stu-id="829a3-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="829a3-132">ListItems-Element voor het besturingselement (indeling)</span><span class="sxs-lookup"><span data-stu-id="829a3-132">ListItems Element for List Control (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="829a3-133">Definieert de eigenschappen en -scripts waarvan de waarden worden weergegeven in de lijstweergave.</span><span class="sxs-lookup"><span data-stu-id="829a3-133">Defines the properties and scripts whose values are displayed in the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="829a3-134">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="829a3-134">Remarks</span></span>

<span data-ttu-id="829a3-135">Zie voor meer informatie over de onderdelen van een lijst weergeven, [het maken van een lijstweergave](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="829a3-135">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="829a3-136">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="829a3-136">Example</span></span>

<span data-ttu-id="829a3-137">In dit voorbeeld ziet u de XML-elementen die drie rijen van de lijstweergave definiëren.</span><span class="sxs-lookup"><span data-stu-id="829a3-137">This example shows the XML elements that define three rows of the list view.</span></span> <span data-ttu-id="829a3-138">De waarde van een .NET-eigenschap van de eerste twee rijen weergeven en de laatste rij wordt een waarde die is gegenereerd door een script.</span><span class="sxs-lookup"><span data-stu-id="829a3-138">The first two rows display the value of a .NET property, and the last row displays a value generated by a script.</span></span>

```xml
<ListEntry>
    <ListItems>
      <ListItem>
        <Label>Property1: </Label>
        <PropertyName>DotNetProperty1</PropertyName>
      </ListItem>
      <ListItem>
        <PropertyName>DotNetProperty2</PropertyName>
      </ListItem>
      <ListItem>
        <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
      </ListItem>
    </ListItems>
</ListEntry>

```

## <a name="see-also"></a><span data-ttu-id="829a3-139">Zie ook</span><span class="sxs-lookup"><span data-stu-id="829a3-139">See Also</span></span>

[<span data-ttu-id="829a3-140">ListItems Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="829a3-140">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="829a3-141">FormatString-Element voor ListItem (indeling)</span><span class="sxs-lookup"><span data-stu-id="829a3-141">FormatString Element for ListItem (Format)</span></span>](./formatstring-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="829a3-142">Label-Element voor ListItem (indeling)</span><span class="sxs-lookup"><span data-stu-id="829a3-142">Label Element for ListItem (Format)</span></span>](./label-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="829a3-143">PropertyName-Element voor ListItem (indeling)</span><span class="sxs-lookup"><span data-stu-id="829a3-143">PropertyName Element for ListItem (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="829a3-144">ScriptBlock-Element voor ListItem (indeling)</span><span class="sxs-lookup"><span data-stu-id="829a3-144">ScriptBlock Element for ListItem (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="829a3-145">Het maken van een lijst weergeven</span><span class="sxs-lookup"><span data-stu-id="829a3-145">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="829a3-146">Schrijven van een Windows PowerShell opmaak en het bestand van het type</span><span class="sxs-lookup"><span data-stu-id="829a3-146">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
