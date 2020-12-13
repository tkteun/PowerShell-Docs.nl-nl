---
ms.date: 09/13/2016
ms.topic: reference
title: Het element PropertyName voor ItemSelectionCondition voor CustomControl voor Weergave (opmaak)
description: Het element PropertyName voor ItemSelectionCondition voor CustomControl voor Weergave (opmaak)
ms.openlocfilehash: 5687bb781ce2db27b875f829147ee8b436f04adc
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666124"
---
# <a name="propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="a89a7-103">Het element PropertyName voor ItemSelectionCondition voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="a89a7-103">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="a89a7-104">Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="a89a7-104">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="a89a7-105">Wanneer deze eigenschap aanwezig is of wanneer deze wordt geëvalueerd `true` , wordt voldaan aan de voor waarde en wordt het besturings element gebruikt.</span><span class="sxs-lookup"><span data-stu-id="a89a7-105">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="a89a7-106">Dit element wordt gebruikt bij het definiëren van een aangepaste beheer weergave.</span><span class="sxs-lookup"><span data-stu-id="a89a7-106">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="a89a7-107">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) CustomControl-element (indeling) CustomEntries element voor CustomControl voor weer gave (Format) CustomEntry-element voor CustomEntries voor weer gave (Format) CustomItem element voor CustomEntry voor weer gave (Format) ExpressionBinding-element voor CustomItem voor CustomControl voor weer gave (Format) ItemSelectionCondition-element voor expressie binding voor CustomControl voor weer gave (indeling) eigenschaps element voor ItemSelectionCondition voor CustomControl voor weer gave (Format</span><span class="sxs-lookup"><span data-stu-id="a89a7-107">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format) PropertyName Element for ItemSelectionCondition for CustomControl for View (Format</span></span>

## <a name="syntax"></a><span data-ttu-id="a89a7-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="a89a7-108">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a89a7-109">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="a89a7-109">Attributes and Elements</span></span>

<span data-ttu-id="a89a7-110">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `PropertyName` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="a89a7-110">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a89a7-111">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="a89a7-111">Attributes</span></span>

<span data-ttu-id="a89a7-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="a89a7-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a89a7-113">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="a89a7-113">Child Elements</span></span>

<span data-ttu-id="a89a7-114">Geen.</span><span class="sxs-lookup"><span data-stu-id="a89a7-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a89a7-115">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="a89a7-115">Parent Elements</span></span>

|<span data-ttu-id="a89a7-116">Element</span><span class="sxs-lookup"><span data-stu-id="a89a7-116">Element</span></span>|<span data-ttu-id="a89a7-117">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="a89a7-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a89a7-118">ItemSelectionCondition-element voor expressie binding voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="a89a7-118">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="a89a7-119">Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit besturings element.</span><span class="sxs-lookup"><span data-stu-id="a89a7-119">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a89a7-120">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="a89a7-120">Text Value</span></span>

<span data-ttu-id="a89a7-121">Geef de naam op van de .NET-eigenschap waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="a89a7-121">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="a89a7-122">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="a89a7-122">Remarks</span></span>

<span data-ttu-id="a89a7-123">Als dit element wordt gebruikt, kunt u het [script Block](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) -element niet opgeven wanneer u de selectie voorwaarde definieert.</span><span class="sxs-lookup"><span data-stu-id="a89a7-123">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="a89a7-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="a89a7-124">See Also</span></span>

[<span data-ttu-id="a89a7-125">Het element ScriptBlock voor ItemSelectionCondition voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="a89a7-125">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="a89a7-126">ItemSelectionCondition-element voor expressie binding voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="a89a7-126">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="a89a7-127">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="a89a7-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
