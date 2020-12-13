---
ms.date: 09/13/2016
ms.topic: reference
title: Het element ScriptBlock voor ListItem voor ListControl (opmaak)
description: Het element ScriptBlock voor ListItem voor ListControl (opmaak)
ms.openlocfilehash: 0635ac2622cc203a2dc895873621901d956f87da
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92664975"
---
# <a name="scriptblock-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="bf094-103">Het element ScriptBlock voor ListItem voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="bf094-103">ScriptBlock Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="bf094-104">Hiermee geeft u het script op waarvan de waarde wordt weer gegeven in de rij.</span><span class="sxs-lookup"><span data-stu-id="bf094-104">Specifies the script whose value is displayed in the row.</span></span>

<span data-ttu-id="bf094-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) item type-element (indeling) van het element list item (Format) voor de ListControl (indeling) element list item voor ListControl (Format) List items element voor List entry voor ListControl (Format) lijst item element voor de ListControl (indeling) script block-element</span><span class="sxs-lookup"><span data-stu-id="bf094-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ScriptBlock Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="bf094-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="bf094-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="bf094-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="bf094-107">Attributes and Elements</span></span>

<span data-ttu-id="bf094-108">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `ScriptBlock` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="bf094-108">The following sections describe the attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="bf094-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="bf094-109">Attributes</span></span>

<span data-ttu-id="bf094-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="bf094-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="bf094-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="bf094-111">Child Elements</span></span>

<span data-ttu-id="bf094-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="bf094-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="bf094-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="bf094-113">Parent Elements</span></span>

|<span data-ttu-id="bf094-114">Element</span><span class="sxs-lookup"><span data-stu-id="bf094-114">Element</span></span>|<span data-ttu-id="bf094-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="bf094-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bf094-116">Lijst item-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="bf094-116">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="bf094-117">Hiermee wordt de eigenschap of het script gedefinieerd waarvan de waarde wordt weer gegeven in een rij van de lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="bf094-117">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="bf094-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="bf094-118">Text Value</span></span>

<span data-ttu-id="bf094-119">Geef het script op waarvan de waarde wordt weer gegeven in de rij.</span><span class="sxs-lookup"><span data-stu-id="bf094-119">Specify the script whose value is displayed in the row.</span></span>

## <a name="remarks"></a><span data-ttu-id="bf094-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="bf094-120">Remarks</span></span>

<span data-ttu-id="bf094-121">Als dit element is opgegeven, kunt u het kenmerk [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) niet opgeven.</span><span class="sxs-lookup"><span data-stu-id="bf094-121">When this element is specified, you cannot specify the [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element.</span></span>

<span data-ttu-id="bf094-122">Zie [lijst weergave](./creating-a-list-view.md)voor meer informatie over het opgeven van scripts in een lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="bf094-122">For more information about specifying scripts in a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="bf094-123">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="bf094-123">Example</span></span>

<span data-ttu-id="bf094-124">In het volgende voor beeld ziet u hoe u de eigenschap kunt opgeven waarvan de waarde wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="bf094-124">The following example shows how to specify the property whose value is displayed.</span></span>

```xml
<ListItem>
  <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="bf094-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="bf094-125">See Also</span></span>

[<span data-ttu-id="bf094-126">Het element PropertyName voor ListItem voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="bf094-126">PropertyName Element for ListItem for ListControl (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="bf094-127">Een lijstweergave maken</span><span class="sxs-lookup"><span data-stu-id="bf094-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="bf094-128">Het element ListItem voor ListItems voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="bf094-128">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="bf094-129">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="bf094-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
