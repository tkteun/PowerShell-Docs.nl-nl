---
title: PropertyName-element voor ItemSelectionCondition voor ListControl (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 8bdbb05326f7ff5ccffa46215631a5c954080dc1
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780862"
---
# <a name="propertyname-element-for-itemselectioncondition-for-listcontrol-format"></a><span data-ttu-id="1b5b5-102">Het element PropertyName voor ItemSelectionCondition voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="1b5b5-102">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>

<span data-ttu-id="1b5b5-103">Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="1b5b5-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="1b5b5-104">Wanneer deze eigenschap aanwezig is of wanneer deze wordt geëvalueerd `true` , wordt voldaan aan de voor waarde en wordt de weer gave gebruikt.</span><span class="sxs-lookup"><span data-stu-id="1b5b5-104">When this property is present or when it evaluates to `true`, the condition is met, and the view is used.</span></span> <span data-ttu-id="1b5b5-105">Dit element wordt gebruikt bij het definiëren van een lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="1b5b5-105">This element is used when defining a list view.</span></span>

<span data-ttu-id="1b5b5-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) item type-element (indeling) (Format) List item (Format) element-element (indeling) List items element voor ListControl (Format) voor List entry voor ListControl (Format) lijst item-element voor list items voor ListControl (Format) ItemSelectionCondition-element voor ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="1b5b5-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ItemSelectionCondition Element for ListItem for ListControls PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1b5b5-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="1b5b5-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1b5b5-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="1b5b5-108">Attributes and Elements</span></span>

<span data-ttu-id="1b5b5-109">In de volgende secties worden kenmerken, onderliggende elementen en de bovenliggende elementen van het `PropertyName` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="1b5b5-109">The following sections describe attributes, child elements, and the parent elements of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1b5b5-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="1b5b5-110">Attributes</span></span>

<span data-ttu-id="1b5b5-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="1b5b5-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1b5b5-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="1b5b5-112">Child Elements</span></span>

<span data-ttu-id="1b5b5-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="1b5b5-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1b5b5-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="1b5b5-114">Parent Elements</span></span>

|<span data-ttu-id="1b5b5-115">Element</span><span class="sxs-lookup"><span data-stu-id="1b5b5-115">Element</span></span>|<span data-ttu-id="1b5b5-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="1b5b5-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1b5b5-117">Het element ItemSelectionCondition voor ListItem voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="1b5b5-117">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)||

## <a name="text-value"></a><span data-ttu-id="1b5b5-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="1b5b5-118">Text Value</span></span>

<span data-ttu-id="1b5b5-119">Geef de naam op van de eigenschap waarvan de waarde wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="1b5b5-119">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="1b5b5-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="1b5b5-120">Remarks</span></span>

<span data-ttu-id="1b5b5-121">Als dit element wordt gebruikt, kunt u het [script Block](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) -element niet opgeven wanneer u de selectie voorwaarde definieert.</span><span class="sxs-lookup"><span data-stu-id="1b5b5-121">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="1b5b5-122">Zie ook</span><span class="sxs-lookup"><span data-stu-id="1b5b5-122">See Also</span></span>

[<span data-ttu-id="1b5b5-123">Script block-element voor ItemSelectionCondition voor ListIControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="1b5b5-123">ScriptBlock Element for ItemSelectionCondition for ListIControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="1b5b5-124">Het element ItemSelectionCondition voor ListItem voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="1b5b5-124">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="1b5b5-125">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="1b5b5-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
