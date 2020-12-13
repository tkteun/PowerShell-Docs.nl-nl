---
ms.date: 09/13/2016
ms.topic: reference
title: Het element ListItem voor ListItems voor ListControl (opmaak)
description: Het element ListItem voor ListItems voor ListControl (opmaak)
ms.openlocfilehash: 999491b7851aa4fa21667ad376d7e9853500ca08
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666549"
---
# <a name="listitem-element-for-listitems-for-listcontrol-format"></a><span data-ttu-id="071f8-103">Het element ListItem voor ListItems voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="071f8-103">ListItem Element for ListItems for ListControl (Format)</span></span>

<span data-ttu-id="071f8-104">Hiermee wordt de eigenschap of het script gedefinieerd waarvan de waarde wordt weer gegeven in een rij van de lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="071f8-104">Defines the property or script whose value is displayed in a row of the list view.</span></span>

<span data-ttu-id="071f8-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) bestand van ListControl element (indeling) element (Format) List item voor ListControl (Format) element list item voor ListControl (Format) List items element voor ListControl (Format) lijst item voor ListControl-element (Format)</span><span class="sxs-lookup"><span data-stu-id="071f8-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListControl (Format) ListItems Element for ListControl (Format) ListItem for ListControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="071f8-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="071f8-106">Syntax</span></span>

```xml
<ListItem>
  <PropertyName>PropertyToDisplay</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <Label>LabelToDisplay</Label>
  <FormatString>FormatPattern</FormatString>
  <ItemSelectionCondition>...</ItemSelectionCondition>
</ListItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="071f8-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="071f8-107">Attributes and Elements</span></span>

<span data-ttu-id="071f8-108">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `ListItem` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="071f8-108">The following sections describe the attributes, child elements, and parent element of the `ListItem` element.</span></span> <span data-ttu-id="071f8-109">Er kan slechts één eigenschap of script worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="071f8-109">Only one property or script can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="071f8-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="071f8-110">Attributes</span></span>

<span data-ttu-id="071f8-111">Geen</span><span class="sxs-lookup"><span data-stu-id="071f8-111">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="071f8-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="071f8-112">Child Elements</span></span>

|<span data-ttu-id="071f8-113">Element</span><span class="sxs-lookup"><span data-stu-id="071f8-113">Element</span></span>|<span data-ttu-id="071f8-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="071f8-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="071f8-115">Element formats Tring voor lijst item voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="071f8-115">FormatString Element for ListItem for ListControl (Format)</span></span>](./formatstring-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="071f8-116">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="071f8-116">Optional element.</span></span><br /><br /> <span data-ttu-id="071f8-117">Geeft een indelings teken reeks die definieert hoe de eigenschap of script waarde wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="071f8-117">Specifies a format string that defines how the property or script value is displayed.</span></span>|
|[<span data-ttu-id="071f8-118">Het element ItemSelectionCondition voor ListItem voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="071f8-118">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="071f8-119">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="071f8-119">Optional element.</span></span><br /><br /> <span data-ttu-id="071f8-120">Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit lijst item.</span><span class="sxs-lookup"><span data-stu-id="071f8-120">Defines the condition that must exist for this list item to be used.</span></span>|
|[<span data-ttu-id="071f8-121">Het element Label voor ListItem voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="071f8-121">Label Element for ListItem for ListControl (Format)</span></span>](./label-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="071f8-122">Optioneel element</span><span class="sxs-lookup"><span data-stu-id="071f8-122">Optional element</span></span><br /><br /> <span data-ttu-id="071f8-123">Hiermee geeft u het label op dat links van de eigenschap of script waarde in de rij wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="071f8-123">Specifies the label that is displayed to the left of the property or script value in the row.</span></span>|
|[<span data-ttu-id="071f8-124">Het element PropertyName voor ListItem voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="071f8-124">PropertyName Element for ListItem for ListControl (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="071f8-125">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="071f8-125">Optional element.</span></span><br /><br /> <span data-ttu-id="071f8-126">Hiermee geeft u de .NET-eigenschap op waarvan de waarde wordt weer gegeven in de rij.</span><span class="sxs-lookup"><span data-stu-id="071f8-126">Specifies the .NET property whose value is displayed in the row.</span></span>|
|[<span data-ttu-id="071f8-127">Het element ScriptBlock voor ListItem voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="071f8-127">ScriptBlock Element for ListItem for ListControl (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="071f8-128">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="071f8-128">Optional element.</span></span><br /><br /> <span data-ttu-id="071f8-129">Hiermee geeft u het script op waarvan de waarde wordt weer gegeven in de rij.</span><span class="sxs-lookup"><span data-stu-id="071f8-129">Specifies the script whose value is displayed in the row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="071f8-130">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="071f8-130">Parent Elements</span></span>

|<span data-ttu-id="071f8-131">Element</span><span class="sxs-lookup"><span data-stu-id="071f8-131">Element</span></span>|<span data-ttu-id="071f8-132">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="071f8-132">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="071f8-133">List items-element voor lijst besturings element (indeling)</span><span class="sxs-lookup"><span data-stu-id="071f8-133">ListItems Element for List Control (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="071f8-134">Hiermee worden de eigenschappen en scripts gedefinieerd waarvan de waarden worden weer gegeven in de lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="071f8-134">Defines the properties and scripts whose values are displayed in the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="071f8-135">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="071f8-135">Remarks</span></span>

<span data-ttu-id="071f8-136">Zie [een lijst weergave maken](./creating-a-list-view.md)voor meer informatie over de onderdelen van een lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="071f8-136">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="071f8-137">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="071f8-137">Example</span></span>

<span data-ttu-id="071f8-138">In dit voor beeld worden de XML-elementen weer gegeven waarmee drie rijen van de lijst weergave worden gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="071f8-138">This example shows the XML elements that define three rows of the list view.</span></span> <span data-ttu-id="071f8-139">In de eerste twee rijen wordt de waarde van een .NET-eigenschap weer gegeven en in de laatste rij wordt een waarde weer gegeven die door een script is gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="071f8-139">The first two rows display the value of a .NET property, and the last row displays a value generated by a script.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="071f8-140">Zie ook</span><span class="sxs-lookup"><span data-stu-id="071f8-140">See Also</span></span>

[<span data-ttu-id="071f8-141">List items-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="071f8-141">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="071f8-142">Element formats Tring voor lijst item (indeling)</span><span class="sxs-lookup"><span data-stu-id="071f8-142">FormatString Element for ListItem (Format)</span></span>](./formatstring-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="071f8-143">Element label voor lijst item (indeling)</span><span class="sxs-lookup"><span data-stu-id="071f8-143">Label Element for ListItem (Format)</span></span>](./label-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="071f8-144">Het element PropertyName voor lijst item (indeling)</span><span class="sxs-lookup"><span data-stu-id="071f8-144">PropertyName Element for ListItem (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="071f8-145">Script block-element voor lijst item (indeling)</span><span class="sxs-lookup"><span data-stu-id="071f8-145">ScriptBlock Element for ListItem (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="071f8-146">Een lijstweergave maken</span><span class="sxs-lookup"><span data-stu-id="071f8-146">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="071f8-147">Een Windows Power shell-indeling en-type bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="071f8-147">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
