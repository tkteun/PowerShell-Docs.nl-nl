---
title: Lijst item-element voor list items voor ListControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f96f4f5-8bd5-43ed-95e7-a7358115999a
caps.latest.revision: 11
ms.openlocfilehash: 1e0a1b2d20853650328b8cfd1513a08f7e167cd6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72356012"
---
# <a name="listitem-element-for-listitems-for-listcontrol-format"></a><span data-ttu-id="551d4-102">Het element ListItem voor ListItems voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="551d4-102">ListItem Element for ListItems for ListControl (Format)</span></span>

<span data-ttu-id="551d4-103">Hiermee wordt de eigenschap of het script gedefinieerd waarvan de waarde wordt weer gegeven in een rij van de lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="551d4-103">Defines the property or script whose value is displayed in a row of the list view.</span></span>

<span data-ttu-id="551d4-104">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) bestand van ListControl element (indeling) element (Format) List item voor ListControl (indeling) element entry View voor ListControl (Format) List items element voor ListControl Lijst item voor het element ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="551d4-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListControl (Format) ListItems Element for ListControl (Format) ListItem for ListControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="551d4-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="551d4-105">Syntax</span></span>

```xml
<ListItem>
  <PropertyName>PropertyToDisplay</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <Label>LabelToDisplay</Label>
  <FormatString>FormatPattern</FormatString>
  <ItemSelectionCondition>...</ItemSelectionCondition>
</ListItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="551d4-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="551d4-106">Attributes and Elements</span></span>

<span data-ttu-id="551d4-107">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het element `ListItem` beschreven.</span><span class="sxs-lookup"><span data-stu-id="551d4-107">The following sections describe the attributes, child elements, and parent element of the `ListItem` element.</span></span> <span data-ttu-id="551d4-108">Er kan slechts één eigenschap of script worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="551d4-108">Only one property or script can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="551d4-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="551d4-109">Attributes</span></span>

<span data-ttu-id="551d4-110">Geen</span><span class="sxs-lookup"><span data-stu-id="551d4-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="551d4-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="551d4-111">Child Elements</span></span>

|<span data-ttu-id="551d4-112">Element</span><span class="sxs-lookup"><span data-stu-id="551d4-112">Element</span></span>|<span data-ttu-id="551d4-113">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="551d4-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="551d4-114">Element formats Tring voor lijst item voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="551d4-114">FormatString Element for ListItem for ListControl (Format)</span></span>](./formatstring-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="551d4-115">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="551d4-115">Optional element.</span></span><br /><br /> <span data-ttu-id="551d4-116">Geeft een indelings teken reeks die definieert hoe de eigenschap of script waarde wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="551d4-116">Specifies a format string that defines how the property or script value is displayed.</span></span>|
|[<span data-ttu-id="551d4-117">ItemSelectionCondition-element voor lijst item voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="551d4-117">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="551d4-118">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="551d4-118">Optional element.</span></span><br /><br /> <span data-ttu-id="551d4-119">Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit lijst item.</span><span class="sxs-lookup"><span data-stu-id="551d4-119">Defines the condition that must exist for this list item to be used.</span></span>|
|[<span data-ttu-id="551d4-120">Element label voor lijst item voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="551d4-120">Label Element for ListItem for ListControl (Format)</span></span>](./label-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="551d4-121">Optioneel element</span><span class="sxs-lookup"><span data-stu-id="551d4-121">Optional element</span></span><br /><br /> <span data-ttu-id="551d4-122">Hiermee geeft u het label op dat links van de eigenschap of script waarde in de rij wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="551d4-122">Specifies the label that is displayed to the left of the property or script value in the row.</span></span>|
|[<span data-ttu-id="551d4-123">PropertyName-element voor lijst item voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="551d4-123">PropertyName Element for ListItem for ListControl (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="551d4-124">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="551d4-124">Optional element.</span></span><br /><br /> <span data-ttu-id="551d4-125">Hiermee geeft u de .NET-eigenschap op waarvan de waarde wordt weer gegeven in de rij.</span><span class="sxs-lookup"><span data-stu-id="551d4-125">Specifies the .NET property whose value is displayed in the row.</span></span>|
|[<span data-ttu-id="551d4-126">Script block-element voor lijst item voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="551d4-126">ScriptBlock Element for ListItem for ListControl (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="551d4-127">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="551d4-127">Optional element.</span></span><br /><br /> <span data-ttu-id="551d4-128">Hiermee geeft u het script op waarvan de waarde wordt weer gegeven in de rij.</span><span class="sxs-lookup"><span data-stu-id="551d4-128">Specifies the script whose value is displayed in the row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="551d4-129">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="551d4-129">Parent Elements</span></span>

|<span data-ttu-id="551d4-130">Element</span><span class="sxs-lookup"><span data-stu-id="551d4-130">Element</span></span>|<span data-ttu-id="551d4-131">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="551d4-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="551d4-132">List items-element voor lijst besturings element (indeling)</span><span class="sxs-lookup"><span data-stu-id="551d4-132">ListItems Element for List Control (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="551d4-133">Hiermee worden de eigenschappen en scripts gedefinieerd waarvan de waarden worden weer gegeven in de lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="551d4-133">Defines the properties and scripts whose values are displayed in the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="551d4-134">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="551d4-134">Remarks</span></span>

<span data-ttu-id="551d4-135">Zie [een lijst weergave maken](./creating-a-list-view.md)voor meer informatie over de onderdelen van een lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="551d4-135">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="551d4-136">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="551d4-136">Example</span></span>

<span data-ttu-id="551d4-137">In dit voor beeld worden de XML-elementen weer gegeven waarmee drie rijen van de lijst weergave worden gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="551d4-137">This example shows the XML elements that define three rows of the list view.</span></span> <span data-ttu-id="551d4-138">In de eerste twee rijen wordt de waarde van een .NET-eigenschap weer gegeven en in de laatste rij wordt een waarde weer gegeven die door een script is gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="551d4-138">The first two rows display the value of a .NET property, and the last row displays a value generated by a script.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="551d4-139">Zie ook</span><span class="sxs-lookup"><span data-stu-id="551d4-139">See Also</span></span>

[<span data-ttu-id="551d4-140">List items-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="551d4-140">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="551d4-141">Element formats Tring voor lijst item (indeling)</span><span class="sxs-lookup"><span data-stu-id="551d4-141">FormatString Element for ListItem (Format)</span></span>](./formatstring-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="551d4-142">Element label voor lijst item (indeling)</span><span class="sxs-lookup"><span data-stu-id="551d4-142">Label Element for ListItem (Format)</span></span>](./label-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="551d4-143">Het element PropertyName voor lijst item (indeling)</span><span class="sxs-lookup"><span data-stu-id="551d4-143">PropertyName Element for ListItem (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="551d4-144">Script block-element voor lijst item (indeling)</span><span class="sxs-lookup"><span data-stu-id="551d4-144">ScriptBlock Element for ListItem (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="551d4-145">Een lijst weergave maken</span><span class="sxs-lookup"><span data-stu-id="551d4-145">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="551d4-146">Een Windows Power shell-indeling en-type bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="551d4-146">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
