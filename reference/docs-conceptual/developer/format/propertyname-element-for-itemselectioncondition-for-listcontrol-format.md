---
ms.date: 09/13/2016
ms.topic: reference
title: Het element PropertyName voor ItemSelectionCondition voor ListControl (opmaak)
description: Het element PropertyName voor ItemSelectionCondition voor ListControl (opmaak)
ms.openlocfilehash: c515efe70afdb1c1186c0a07fe1f52dc49ad57b9
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665988"
---
# <a name="propertyname-element-for-itemselectioncondition-for-listcontrol-format"></a><span data-ttu-id="d7fa5-103">Het element PropertyName voor ItemSelectionCondition voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="d7fa5-103">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>

<span data-ttu-id="d7fa5-104">Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="d7fa5-104">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="d7fa5-105">Wanneer deze eigenschap aanwezig is of wanneer deze wordt geëvalueerd `true` , wordt voldaan aan de voor waarde en wordt de weer gave gebruikt.</span><span class="sxs-lookup"><span data-stu-id="d7fa5-105">When this property is present or when it evaluates to `true`, the condition is met, and the view is used.</span></span> <span data-ttu-id="d7fa5-106">Dit element wordt gebruikt bij het definiëren van een lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="d7fa5-106">This element is used when defining a list view.</span></span>

<span data-ttu-id="d7fa5-107">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) item type-element (indeling) (Format) List item (Format) element-element (indeling) List items element voor ListControl (Format) voor List entry voor ListControl (Format) lijst item-element voor list items voor ListControl (Format) ItemSelectionCondition-element voor ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="d7fa5-107">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ItemSelectionCondition Element for ListItem for ListControls PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d7fa5-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="d7fa5-108">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d7fa5-109">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="d7fa5-109">Attributes and Elements</span></span>

<span data-ttu-id="d7fa5-110">In de volgende secties worden kenmerken, onderliggende elementen en de bovenliggende elementen van het `PropertyName` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="d7fa5-110">The following sections describe attributes, child elements, and the parent elements of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d7fa5-111">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="d7fa5-111">Attributes</span></span>

<span data-ttu-id="d7fa5-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="d7fa5-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d7fa5-113">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="d7fa5-113">Child Elements</span></span>

<span data-ttu-id="d7fa5-114">Geen.</span><span class="sxs-lookup"><span data-stu-id="d7fa5-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d7fa5-115">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="d7fa5-115">Parent Elements</span></span>

|<span data-ttu-id="d7fa5-116">Element</span><span class="sxs-lookup"><span data-stu-id="d7fa5-116">Element</span></span>|<span data-ttu-id="d7fa5-117">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="d7fa5-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d7fa5-118">Het element ItemSelectionCondition voor ListItem voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="d7fa5-118">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)||

## <a name="text-value"></a><span data-ttu-id="d7fa5-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="d7fa5-119">Text Value</span></span>

<span data-ttu-id="d7fa5-120">Geef de naam op van de eigenschap waarvan de waarde wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="d7fa5-120">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="d7fa5-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="d7fa5-121">Remarks</span></span>

<span data-ttu-id="d7fa5-122">Als dit element wordt gebruikt, kunt u het [script Block](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) -element niet opgeven wanneer u de selectie voorwaarde definieert.</span><span class="sxs-lookup"><span data-stu-id="d7fa5-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="d7fa5-123">Zie ook</span><span class="sxs-lookup"><span data-stu-id="d7fa5-123">See Also</span></span>

[<span data-ttu-id="d7fa5-124">Script block-element voor ItemSelectionCondition voor ListIControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="d7fa5-124">ScriptBlock Element for ItemSelectionCondition for ListIControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="d7fa5-125">Het element ItemSelectionCondition voor ListItem voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="d7fa5-125">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="d7fa5-126">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="d7fa5-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
