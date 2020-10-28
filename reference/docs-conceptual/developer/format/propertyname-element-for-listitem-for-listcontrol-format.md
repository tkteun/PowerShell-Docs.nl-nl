---
ms.date: 09/13/2016
ms.topic: reference
title: Het element PropertyName voor ListItem voor ListControl (opmaak)
description: Het element PropertyName voor ListItem voor ListControl (opmaak)
ms.openlocfilehash: 30cd48f9549e1a091776cd5f8395e1a71314ea1b
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92665971"
---
# <a name="propertyname-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="3ceae-103">Het element PropertyName voor ListItem voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="3ceae-103">PropertyName Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="3ceae-104">Hiermee geeft u de .NET-eigenschap op waarvan de waarde wordt weer gegeven in de lijst.</span><span class="sxs-lookup"><span data-stu-id="3ceae-104">Specifies the .NET property whose value is displayed in the list.</span></span>

<span data-ttu-id="3ceae-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element van weer gave (indeling) ListControl element (indeling) (Format) List item (Format) element Entry element (indeling) List items element (Format) lijst item element (indeling) eigenschap Naam element voor lijst item (indeling)</span><span class="sxs-lookup"><span data-stu-id="3ceae-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) ListItems Element (Format) ListItem Element (Format) PropertyName Element for ListItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3ceae-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="3ceae-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3ceae-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="3ceae-107">Attributes and Elements</span></span>

<span data-ttu-id="3ceae-108">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `PropertyName` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="3ceae-108">The following sections describe the attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3ceae-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="3ceae-109">Attributes</span></span>

<span data-ttu-id="3ceae-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="3ceae-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3ceae-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="3ceae-111">Child Elements</span></span>

<span data-ttu-id="3ceae-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="3ceae-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="3ceae-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="3ceae-113">Parent Elements</span></span>

|<span data-ttu-id="3ceae-114">Element</span><span class="sxs-lookup"><span data-stu-id="3ceae-114">Element</span></span>|<span data-ttu-id="3ceae-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="3ceae-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3ceae-116">Lijst item-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="3ceae-116">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="3ceae-117">Hiermee wordt de eigenschap of het script gedefinieerd waarvan de waarde wordt weer gegeven in de rij van de lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="3ceae-117">Defines the property or script whose value is displayed in the row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="3ceae-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="3ceae-118">Text Value</span></span>

<span data-ttu-id="3ceae-119">Geef de naam op van de eigenschap waarvan de waarde wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="3ceae-119">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="3ceae-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="3ceae-120">Remarks</span></span>

<span data-ttu-id="3ceae-121">Als dit element is opgegeven, kunt u het [script Block](./scriptblock-element-for-listitem-for-listcontrol-format.md) -element niet opgeven.</span><span class="sxs-lookup"><span data-stu-id="3ceae-121">When this element is specified, you cannot specify the [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element.</span></span>

<span data-ttu-id="3ceae-122">Naast het weer geven van de eigenschaps waarde, kunt u ook een label opgeven voor de waarde of een opmaak teken reeks die kan worden gebruikt om de weer gave van de waarde te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="3ceae-122">In addition to displaying the property value, you can also specify a label for the value or a format string that can be used to change the display of the value.</span></span> <span data-ttu-id="3ceae-123">Zie [een lijst weergave maken](./creating-a-list-view.md)voor meer informatie over het opgeven van gegevens in een lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="3ceae-123">For more information about specifying data in a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="3ceae-124">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="3ceae-124">Example</span></span>

<span data-ttu-id="3ceae-125">In het volgende voor beeld ziet u hoe u het label en de eigenschap opgeeft waarvan de waarde wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="3ceae-125">The following example shows how to specify the label and property whose value is displayed.</span></span>

```xml
ListItem>
  <Label>NameOfProperty</Label>
  <PropertyName>.NetTypeProperty</PropertyName>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="3ceae-126">Zie ook</span><span class="sxs-lookup"><span data-stu-id="3ceae-126">See Also</span></span>

[<span data-ttu-id="3ceae-127">Het element ScriptBlock voor ListItem voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="3ceae-127">ScriptBlock Element for ListItem for ListControl (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="3ceae-128">Een lijstweergave maken</span><span class="sxs-lookup"><span data-stu-id="3ceae-128">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="3ceae-129">Lijst item-element voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="3ceae-129">ListItem Element for ListControl(Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="3ceae-130">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="3ceae-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
