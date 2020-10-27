---
ms.date: 09/13/2016
ms.topic: reference
title: Het element PropertyName voor ItemSelectionCondition voor Besturingselementen voor Weergave (opmaak)
description: Het element PropertyName voor ItemSelectionCondition voor Besturingselementen voor Weergave (opmaak)
ms.openlocfilehash: 9fb7a21e19338dbf59dab14291e1b02736835040
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92645820"
---
# <a name="propertyname-element-for-itemselectioncondition-for-controls-for-view-format"></a><span data-ttu-id="16627-103">Het element PropertyName voor ItemSelectionCondition voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="16627-103">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="16627-104">Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="16627-104">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="16627-105">Wanneer deze eigenschap aanwezig is of wanneer deze wordt geëvalueerd `true` , wordt voldaan aan de voor waarde en wordt het besturings element gebruikt.</span><span class="sxs-lookup"><span data-stu-id="16627-105">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="16627-106">Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.</span><span class="sxs-lookup"><span data-stu-id="16627-106">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="16627-107">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) Controls-element (indeling) Control element (Format) voor besturings elementen voor de weer gave (indeling) CustomControl-element voor besturings elementen voor Controls (Format) CustomEntries-element voor object voor weer gave (indeling) voor besturings elementen voor weer gave (indeling) CustomItem-element voor CustomEntry voor besturings elementen voor weer gave (Format) ExpressionBinding-element voor CustomItem voor besturings elementen voor de weer gave (indeling) ItemSelectionCondition element van ExpressionBinding voor besturings elementen voor de weer gave (indeling) eigenschap naam van ItemSelectionCondition voor Controls (indeling)</span><span class="sxs-lookup"><span data-stu-id="16627-107">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format) PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="16627-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="16627-108">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="16627-109">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="16627-109">Attributes and Elements</span></span>

<span data-ttu-id="16627-110">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `PropertyName` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="16627-110">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="16627-111">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="16627-111">Attributes</span></span>

<span data-ttu-id="16627-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="16627-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="16627-113">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="16627-113">Child Elements</span></span>

<span data-ttu-id="16627-114">Geen.</span><span class="sxs-lookup"><span data-stu-id="16627-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="16627-115">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="16627-115">Parent Elements</span></span>

|<span data-ttu-id="16627-116">Element</span><span class="sxs-lookup"><span data-stu-id="16627-116">Element</span></span>|<span data-ttu-id="16627-117">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="16627-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="16627-118">ItemSelectionCondition-element van ExpressionBinding voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="16627-118">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="16627-119">Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit besturings element.</span><span class="sxs-lookup"><span data-stu-id="16627-119">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="16627-120">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="16627-120">Text Value</span></span>

<span data-ttu-id="16627-121">Geef de naam op van de .NET-eigenschap waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="16627-121">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="16627-122">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="16627-122">Remarks</span></span>

<span data-ttu-id="16627-123">Als dit element wordt gebruikt, kunt u het [script Block](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md) -element niet opgeven wanneer u de selectie voorwaarde definieert.</span><span class="sxs-lookup"><span data-stu-id="16627-123">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="16627-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="16627-124">See Also</span></span>

[<span data-ttu-id="16627-125">Het element ScriptBlock voor ItemSelectionCondition voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="16627-125">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="16627-126">ItemSelectionCondition-element van ExpressionBinding voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="16627-126">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="16627-127">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="16627-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
