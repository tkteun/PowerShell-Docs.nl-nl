---
ms.date: 09/13/2016
ms.topic: reference
title: Het element PropertyName voor ItemSelectionCondition voor ListControl (opmaak)
description: Het element PropertyName voor ItemSelectionCondition voor ListControl (opmaak)
ms.openlocfilehash: c515efe70afdb1c1186c0a07fe1f52dc49ad57b9
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92665988"
---
# <a name="propertyname-element-for-itemselectioncondition-for-listcontrol-format"></a><span data-ttu-id="f5566-103">Het element PropertyName voor ItemSelectionCondition voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="f5566-103">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>

<span data-ttu-id="f5566-104">Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="f5566-104">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="f5566-105">Wanneer deze eigenschap aanwezig is of wanneer deze wordt geëvalueerd `true` , wordt voldaan aan de voor waarde en wordt de weer gave gebruikt.</span><span class="sxs-lookup"><span data-stu-id="f5566-105">When this property is present or when it evaluates to `true`, the condition is met, and the view is used.</span></span> <span data-ttu-id="f5566-106">Dit element wordt gebruikt bij het definiëren van een lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="f5566-106">This element is used when defining a list view.</span></span>

<span data-ttu-id="f5566-107">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) item type-element (indeling) (Format) List item (Format) element-element (indeling) List items element voor ListControl (Format) voor List entry voor ListControl (Format) lijst item-element voor list items voor ListControl (Format) ItemSelectionCondition-element voor ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="f5566-107">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ItemSelectionCondition Element for ListItem for ListControls PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f5566-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="f5566-108">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f5566-109">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="f5566-109">Attributes and Elements</span></span>

<span data-ttu-id="f5566-110">In de volgende secties worden kenmerken, onderliggende elementen en de bovenliggende elementen van het `PropertyName` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="f5566-110">The following sections describe attributes, child elements, and the parent elements of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f5566-111">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="f5566-111">Attributes</span></span>

<span data-ttu-id="f5566-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="f5566-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f5566-113">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="f5566-113">Child Elements</span></span>

<span data-ttu-id="f5566-114">Geen.</span><span class="sxs-lookup"><span data-stu-id="f5566-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f5566-115">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="f5566-115">Parent Elements</span></span>

|<span data-ttu-id="f5566-116">Element</span><span class="sxs-lookup"><span data-stu-id="f5566-116">Element</span></span>|<span data-ttu-id="f5566-117">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="f5566-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f5566-118">Het element ItemSelectionCondition voor ListItem voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="f5566-118">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)||

## <a name="text-value"></a><span data-ttu-id="f5566-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="f5566-119">Text Value</span></span>

<span data-ttu-id="f5566-120">Geef de naam op van de eigenschap waarvan de waarde wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="f5566-120">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="f5566-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="f5566-121">Remarks</span></span>

<span data-ttu-id="f5566-122">Als dit element wordt gebruikt, kunt u het [script Block](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) -element niet opgeven wanneer u de selectie voorwaarde definieert.</span><span class="sxs-lookup"><span data-stu-id="f5566-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="f5566-123">Zie ook</span><span class="sxs-lookup"><span data-stu-id="f5566-123">See Also</span></span>

[<span data-ttu-id="f5566-124">Script block-element voor ItemSelectionCondition voor ListIControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="f5566-124">ScriptBlock Element for ItemSelectionCondition for ListIControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="f5566-125">Het element ItemSelectionCondition voor ListItem voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="f5566-125">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="f5566-126">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="f5566-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
