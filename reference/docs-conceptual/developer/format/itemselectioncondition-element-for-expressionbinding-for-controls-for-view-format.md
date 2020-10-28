---
ms.date: 09/13/2016
ms.topic: reference
title: Het element ItemSelectionCondition voor ExpressionBinding voor Besturingselementen voor Weergave (opmaak)
description: Het element ItemSelectionCondition voor ExpressionBinding voor Besturingselementen voor Weergave (opmaak)
ms.openlocfilehash: adbe747bdb4f6c1d180e5b630247de0fd3d72b85
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92648060"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format"></a><span data-ttu-id="06c6f-103">Het element ItemSelectionCondition voor ExpressionBinding voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="06c6f-103">ItemSelectionCondition Element for ExpressionBinding for Controls for View (Format)</span></span>

<span data-ttu-id="06c6f-104">Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit besturings element.</span><span class="sxs-lookup"><span data-stu-id="06c6f-104">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="06c6f-105">Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.</span><span class="sxs-lookup"><span data-stu-id="06c6f-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="06c6f-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) Controls-element (Format) Control element (indeling) voor besturings elementen voor weer gave (indeling) CustomControl-element voor besturings elementen voor het element Control Format) CustomEntry-element voor CustomEntries voor besturings elementen voor de weer gave (indeling) CustomItem-element voor CustomEntry voor besturings elementen voor het ExpressionBinding-element van de CustomItem voor besturings elementen voor weer gave (opmaak) ItemSelectionCondition element van ExpressionBinding voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="06c6f-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="06c6f-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="06c6f-107">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="06c6f-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="06c6f-108">Attributes and Elements</span></span>

<span data-ttu-id="06c6f-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `ItemSelectionCondition` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="06c6f-109">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="06c6f-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="06c6f-110">Attributes</span></span>

<span data-ttu-id="06c6f-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="06c6f-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="06c6f-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="06c6f-112">Child Elements</span></span>

|<span data-ttu-id="06c6f-113">Element</span><span class="sxs-lookup"><span data-stu-id="06c6f-113">Element</span></span>|<span data-ttu-id="06c6f-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="06c6f-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="06c6f-115">Het element PropertyName voor ItemSelectionCondition voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="06c6f-115">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="06c6f-116">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="06c6f-116">Optional element.</span></span><br /><br /> <span data-ttu-id="06c6f-117">Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="06c6f-117">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="06c6f-118">Het element ScriptBlock voor ItemSelectionCondition voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="06c6f-118">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="06c6f-119">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="06c6f-119">Optional element.</span></span><br /><br /> <span data-ttu-id="06c6f-120">Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="06c6f-120">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="06c6f-121">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="06c6f-121">Parent Elements</span></span>

|<span data-ttu-id="06c6f-122">Element</span><span class="sxs-lookup"><span data-stu-id="06c6f-122">Element</span></span>|<span data-ttu-id="06c6f-123">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="06c6f-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="06c6f-124">Het element ExpressionBinding voor CustomItem voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="06c6f-124">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="06c6f-125">Hiermee worden de gegevens gedefinieerd die door het besturings element worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="06c6f-125">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="06c6f-126">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="06c6f-126">Remarks</span></span>

<span data-ttu-id="06c6f-127">U kunt voor dit probleem één eigenschaps naam of een script opgeven, maar niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="06c6f-127">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="06c6f-128">Zie ook</span><span class="sxs-lookup"><span data-stu-id="06c6f-128">See Also</span></span>

[<span data-ttu-id="06c6f-129">Het element PropertyName voor ItemSelectionCondition voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="06c6f-129">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="06c6f-130">Het element ScriptBlock voor ItemSelectionCondition voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="06c6f-130">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="06c6f-131">Het element ExpressionBinding voor CustomItem voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="06c6f-131">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="06c6f-132">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="06c6f-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
