---
ms.date: 09/13/2016
ms.topic: reference
title: Het element Label voor ListItem voor ListControl (opmaak)
description: Het element Label voor ListItem voor ListControl (opmaak)
ms.openlocfilehash: 01ff34c4129abe2c76a0a21794e756b77bff12bf
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666651"
---
# <a name="label-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="39816-103">Het element Label voor ListItem voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="39816-103">Label Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="39816-104">Hiermee geeft u het label op dat links van de eigenschap of script waarde in de rij wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="39816-104">Specifies the label that is displayed to the left of the property or script value in the row.</span></span>

<span data-ttu-id="39816-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) bestand van ListControl element (indeling). element (Format) List item voor ListControl (Format) element Entry List voor ListControl (Format) List items voor List entry voor ListControl element (Format) lijst item-element voor list items voor ListControl (Format) label-element (Format)</span><span class="sxs-lookup"><span data-stu-id="39816-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListControl (Format) ListItems for ListEntry for ListControl Element (Format) ListItem Element for ListItems for ListControl (Format) Label Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="39816-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="39816-106">Syntax</span></span>

```xml
<Label>Label for displayed value</Label>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="39816-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="39816-107">Attributes and Elements</span></span>

<span data-ttu-id="39816-108">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `Label` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="39816-108">The following sections describe the attributes, child elements, and the parent element of the `Label` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="39816-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="39816-109">Attributes</span></span>

<span data-ttu-id="39816-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="39816-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="39816-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="39816-111">Child Elements</span></span>

<span data-ttu-id="39816-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="39816-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="39816-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="39816-113">Parent Elements</span></span>

|<span data-ttu-id="39816-114">Element</span><span class="sxs-lookup"><span data-stu-id="39816-114">Element</span></span>|<span data-ttu-id="39816-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="39816-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="39816-116">Het element ListItem voor ListItems voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="39816-116">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="39816-117">Hiermee wordt de eigenschap of het script gedefinieerd waarvan de waarde wordt weer gegeven in een rij van de lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="39816-117">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="39816-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="39816-118">Text Value</span></span>

<span data-ttu-id="39816-119">Geef het label op dat links van de eigenschap of script waarde moet worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="39816-119">Specify the label to be display to the left of the property or script value.</span></span>

## <a name="remarks"></a><span data-ttu-id="39816-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="39816-120">Remarks</span></span>

<span data-ttu-id="39816-121">Als er geen label is opgegeven, wordt de naam van de eigenschap of het script weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="39816-121">If a label is not specified, the name of the property or the script is displayed.</span></span> <span data-ttu-id="39816-122">Zie [een lijst weergave maken](./creating-a-list-view.md)voor meer informatie over het gebruik van labels in een lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="39816-122">For more information about using labels in a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="39816-123">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="39816-123">Example</span></span>

<span data-ttu-id="39816-124">In het volgende voor beeld ziet u hoe u een label aan een rij toevoegt.</span><span class="sxs-lookup"><span data-stu-id="39816-124">The following example shows how to add a label to a row.</span></span>

```xml
<ListItem>
  <Label>Property1: </Label>
  <PropertyName>DotNetProperty1</PropertyName>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="39816-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="39816-125">See Also</span></span>

[<span data-ttu-id="39816-126">Een lijstweergave maken</span><span class="sxs-lookup"><span data-stu-id="39816-126">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="39816-127">Lijst item-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="39816-127">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="39816-128">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="39816-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
