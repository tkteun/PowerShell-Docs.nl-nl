---
title: Lijst item-element voor list items voor ListControl (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e72a887e8bd1f93bacb663e3079eeaec34bdfa51
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785673"
---
# <a name="listitem-element-for-listitems-for-listcontrol-format"></a><span data-ttu-id="86dc0-102">Het element ListItem voor ListItems voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="86dc0-102">ListItem Element for ListItems for ListControl (Format)</span></span>

<span data-ttu-id="86dc0-103">Hiermee wordt de eigenschap of het script gedefinieerd waarvan de waarde wordt weer gegeven in een rij van de lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="86dc0-103">Defines the property or script whose value is displayed in a row of the list view.</span></span>

<span data-ttu-id="86dc0-104">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) bestand van ListControl element (indeling) element (Format) List item voor ListControl (Format) element list item voor ListControl (Format) List items element voor ListControl (Format) lijst item voor ListControl-element (Format)</span><span class="sxs-lookup"><span data-stu-id="86dc0-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListControl (Format) ListItems Element for ListControl (Format) ListItem for ListControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="86dc0-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="86dc0-105">Syntax</span></span>

```xml
<ListItem>
  <PropertyName>PropertyToDisplay</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <Label>LabelToDisplay</Label>
  <FormatString>FormatPattern</FormatString>
  <ItemSelectionCondition>...</ItemSelectionCondition>
</ListItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="86dc0-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="86dc0-106">Attributes and Elements</span></span>

<span data-ttu-id="86dc0-107">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `ListItem` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="86dc0-107">The following sections describe the attributes, child elements, and parent element of the `ListItem` element.</span></span> <span data-ttu-id="86dc0-108">Er kan slechts één eigenschap of script worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="86dc0-108">Only one property or script can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="86dc0-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="86dc0-109">Attributes</span></span>

<span data-ttu-id="86dc0-110">Geen</span><span class="sxs-lookup"><span data-stu-id="86dc0-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="86dc0-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="86dc0-111">Child Elements</span></span>

|<span data-ttu-id="86dc0-112">Element</span><span class="sxs-lookup"><span data-stu-id="86dc0-112">Element</span></span>|<span data-ttu-id="86dc0-113">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="86dc0-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="86dc0-114">Element formats Tring voor lijst item voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="86dc0-114">FormatString Element for ListItem for ListControl (Format)</span></span>](./formatstring-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="86dc0-115">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="86dc0-115">Optional element.</span></span><br /><br /> <span data-ttu-id="86dc0-116">Geeft een indelings teken reeks die definieert hoe de eigenschap of script waarde wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="86dc0-116">Specifies a format string that defines how the property or script value is displayed.</span></span>|
|[<span data-ttu-id="86dc0-117">Het element ItemSelectionCondition voor ListItem voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="86dc0-117">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="86dc0-118">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="86dc0-118">Optional element.</span></span><br /><br /> <span data-ttu-id="86dc0-119">Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit lijst item.</span><span class="sxs-lookup"><span data-stu-id="86dc0-119">Defines the condition that must exist for this list item to be used.</span></span>|
|[<span data-ttu-id="86dc0-120">Het element Label voor ListItem voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="86dc0-120">Label Element for ListItem for ListControl (Format)</span></span>](./label-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="86dc0-121">Optioneel element</span><span class="sxs-lookup"><span data-stu-id="86dc0-121">Optional element</span></span><br /><br /> <span data-ttu-id="86dc0-122">Hiermee geeft u het label op dat links van de eigenschap of script waarde in de rij wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="86dc0-122">Specifies the label that is displayed to the left of the property or script value in the row.</span></span>|
|[<span data-ttu-id="86dc0-123">Het element PropertyName voor ListItem voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="86dc0-123">PropertyName Element for ListItem for ListControl (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="86dc0-124">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="86dc0-124">Optional element.</span></span><br /><br /> <span data-ttu-id="86dc0-125">Hiermee geeft u de .NET-eigenschap op waarvan de waarde wordt weer gegeven in de rij.</span><span class="sxs-lookup"><span data-stu-id="86dc0-125">Specifies the .NET property whose value is displayed in the row.</span></span>|
|[<span data-ttu-id="86dc0-126">Het element ScriptBlock voor ListItem voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="86dc0-126">ScriptBlock Element for ListItem for ListControl (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="86dc0-127">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="86dc0-127">Optional element.</span></span><br /><br /> <span data-ttu-id="86dc0-128">Hiermee geeft u het script op waarvan de waarde wordt weer gegeven in de rij.</span><span class="sxs-lookup"><span data-stu-id="86dc0-128">Specifies the script whose value is displayed in the row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="86dc0-129">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="86dc0-129">Parent Elements</span></span>

|<span data-ttu-id="86dc0-130">Element</span><span class="sxs-lookup"><span data-stu-id="86dc0-130">Element</span></span>|<span data-ttu-id="86dc0-131">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="86dc0-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="86dc0-132">List items-element voor lijst besturings element (indeling)</span><span class="sxs-lookup"><span data-stu-id="86dc0-132">ListItems Element for List Control (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="86dc0-133">Hiermee worden de eigenschappen en scripts gedefinieerd waarvan de waarden worden weer gegeven in de lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="86dc0-133">Defines the properties and scripts whose values are displayed in the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="86dc0-134">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="86dc0-134">Remarks</span></span>

<span data-ttu-id="86dc0-135">Zie [een lijst weergave maken](./creating-a-list-view.md)voor meer informatie over de onderdelen van een lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="86dc0-135">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="86dc0-136">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="86dc0-136">Example</span></span>

<span data-ttu-id="86dc0-137">In dit voor beeld worden de XML-elementen weer gegeven waarmee drie rijen van de lijst weergave worden gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="86dc0-137">This example shows the XML elements that define three rows of the list view.</span></span> <span data-ttu-id="86dc0-138">In de eerste twee rijen wordt de waarde van een .NET-eigenschap weer gegeven en in de laatste rij wordt een waarde weer gegeven die door een script is gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="86dc0-138">The first two rows display the value of a .NET property, and the last row displays a value generated by a script.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="86dc0-139">Zie ook</span><span class="sxs-lookup"><span data-stu-id="86dc0-139">See Also</span></span>

[<span data-ttu-id="86dc0-140">List items-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="86dc0-140">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="86dc0-141">Element formats Tring voor lijst item (indeling)</span><span class="sxs-lookup"><span data-stu-id="86dc0-141">FormatString Element for ListItem (Format)</span></span>](./formatstring-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="86dc0-142">Element label voor lijst item (indeling)</span><span class="sxs-lookup"><span data-stu-id="86dc0-142">Label Element for ListItem (Format)</span></span>](./label-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="86dc0-143">Het element PropertyName voor lijst item (indeling)</span><span class="sxs-lookup"><span data-stu-id="86dc0-143">PropertyName Element for ListItem (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="86dc0-144">Script block-element voor lijst item (indeling)</span><span class="sxs-lookup"><span data-stu-id="86dc0-144">ScriptBlock Element for ListItem (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="86dc0-145">Een lijstweergave maken</span><span class="sxs-lookup"><span data-stu-id="86dc0-145">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="86dc0-146">Een Windows Power shell-indeling en-type bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="86dc0-146">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
