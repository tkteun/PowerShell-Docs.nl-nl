---
ms.date: 09/13/2016
ms.topic: reference
title: Het element ItemSelectionCondition voor ListItem voor ListControl (opmaak)
description: Het element ItemSelectionCondition voor ListItem voor ListControl (opmaak)
ms.openlocfilehash: 13d925da10c2386123983d52b109c03a0c3c63ab
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667807"
---
# <a name="itemselectioncondition-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="f912f-103">Het element ItemSelectionCondition voor ListItem voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="f912f-103">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="f912f-104">Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit lijst item.</span><span class="sxs-lookup"><span data-stu-id="f912f-104">Defines the condition that must exist for this list item to be used.</span></span>

<span data-ttu-id="f912f-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) item type-element (indeling) van het element list item (Format) voor de ListControl (indeling) element list item voor ListControl (Format) List items element voor List entry voor ListControl (Format) lijst item element voor de ListControl (indeling) ItemSelectionCondition-element</span><span class="sxs-lookup"><span data-stu-id="f912f-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f912f-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="f912f-106">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f912f-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="f912f-107">Attributes and Elements</span></span>

<span data-ttu-id="f912f-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `ItemSelectionCondition` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="f912f-108">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f912f-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="f912f-109">Attributes</span></span>

<span data-ttu-id="f912f-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="f912f-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f912f-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="f912f-111">Child Elements</span></span>

|<span data-ttu-id="f912f-112">Element</span><span class="sxs-lookup"><span data-stu-id="f912f-112">Element</span></span>|<span data-ttu-id="f912f-113">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="f912f-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f912f-114">Het element PropertyName voor ItemSelectionCondition voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="f912f-114">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)|<span data-ttu-id="f912f-115">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="f912f-115">Optional element.</span></span><br /><br /> <span data-ttu-id="f912f-116">Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="f912f-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="f912f-117">Het element ScriptBlock voor ItemSelectionCondition voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="f912f-117">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)|<span data-ttu-id="f912f-118">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="f912f-118">Optional element.</span></span><br /><br /> <span data-ttu-id="f912f-119">Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="f912f-119">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f912f-120">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="f912f-120">Parent Elements</span></span>

|<span data-ttu-id="f912f-121">Element</span><span class="sxs-lookup"><span data-stu-id="f912f-121">Element</span></span>|<span data-ttu-id="f912f-122">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="f912f-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f912f-123">Het element ListItem voor ListItems voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="f912f-123">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="f912f-124">Hiermee wordt de eigenschap of het script gedefinieerd waarvan de waarde wordt weer gegeven in een rij van de lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="f912f-124">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f912f-125">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="f912f-125">Remarks</span></span>

<span data-ttu-id="f912f-126">U kunt voor dit probleem één eigenschaps naam of een script opgeven, maar niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="f912f-126">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="f912f-127">Zie ook</span><span class="sxs-lookup"><span data-stu-id="f912f-127">See Also</span></span>

[<span data-ttu-id="f912f-128">Het element ListItem voor ListItems voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="f912f-128">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="f912f-129">Het element PropertyName voor ItemSelectionCondition voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="f912f-129">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="f912f-130">Het element ScriptBlock voor ItemSelectionCondition voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="f912f-130">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="f912f-131">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="f912f-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
