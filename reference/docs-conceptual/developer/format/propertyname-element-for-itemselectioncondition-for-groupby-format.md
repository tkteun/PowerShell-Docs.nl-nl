---
ms.date: 09/13/2016
ms.topic: reference
title: Het element PropertyName voor ItemSelectionCondition voor GroupBy (opmaak)
description: Het element PropertyName voor ItemSelectionCondition voor GroupBy (opmaak)
ms.openlocfilehash: 9667a389ded33d0744f0f7f8d739635a8b21d98b
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666107"
---
# <a name="propertyname-element-for-itemselectioncondition-for-groupby-format"></a><span data-ttu-id="9c7eb-103">Het element PropertyName voor ItemSelectionCondition voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="9c7eb-103">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="9c7eb-104">Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="9c7eb-104">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="9c7eb-105">Wanneer deze eigenschap aanwezig is of wanneer deze wordt geëvalueerd `true` , wordt voldaan aan de voor waarde en wordt het besturings element gebruikt.</span><span class="sxs-lookup"><span data-stu-id="9c7eb-105">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="9c7eb-106">Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="9c7eb-106">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="9c7eb-107">Configuratie-element (indeling) ViewDefinitions element (indeling) element voor weer gave (indeling) GroupBy-element voor weer gave (indeling) CustomControl-element voor het element GroupBy (indeling) CustomEntries voor CustomControl voor het element GroupBy (Format) CustomEntry voor CustomControl voor GroupBy (Format) CustomItem-element voor CustomEntry voor het element GroupBy (Format) ExpressionBinding voor CustomItem voor het element GroupBy (Format) ItemSelectionCondition voor ExpressionBinding voor het element GroupBy (Format) voor ItemSelectionCondition voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="9c7eb-107">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format) PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9c7eb-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="9c7eb-108">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9c7eb-109">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="9c7eb-109">Attributes and Elements</span></span>

<span data-ttu-id="9c7eb-110">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `PropertyName` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="9c7eb-110">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9c7eb-111">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="9c7eb-111">Attributes</span></span>

<span data-ttu-id="9c7eb-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="9c7eb-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9c7eb-113">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="9c7eb-113">Child Elements</span></span>

<span data-ttu-id="9c7eb-114">Geen.</span><span class="sxs-lookup"><span data-stu-id="9c7eb-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9c7eb-115">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="9c7eb-115">Parent Elements</span></span>

|<span data-ttu-id="9c7eb-116">Element</span><span class="sxs-lookup"><span data-stu-id="9c7eb-116">Element</span></span>|<span data-ttu-id="9c7eb-117">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="9c7eb-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9c7eb-118">Het element ItemSelectionCondition voor ExpressionBinding voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="9c7eb-118">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="9c7eb-119">Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit besturings element.</span><span class="sxs-lookup"><span data-stu-id="9c7eb-119">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="9c7eb-120">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="9c7eb-120">Text Value</span></span>

<span data-ttu-id="9c7eb-121">Geef de naam op van de .NET-eigenschap waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="9c7eb-121">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="9c7eb-122">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="9c7eb-122">Remarks</span></span>

<span data-ttu-id="9c7eb-123">Als dit element wordt gebruikt, kunt u het [script Block](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md) -element niet opgeven wanneer u de selectie voorwaarde definieert.</span><span class="sxs-lookup"><span data-stu-id="9c7eb-123">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="9c7eb-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="9c7eb-124">See Also</span></span>

[<span data-ttu-id="9c7eb-125">Het element ScriptBlock voor ItemSelectionCondition voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="9c7eb-125">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)

[<span data-ttu-id="9c7eb-126">Het element ItemSelectionCondition voor ExpressionBinding voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="9c7eb-126">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="9c7eb-127">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="9c7eb-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
