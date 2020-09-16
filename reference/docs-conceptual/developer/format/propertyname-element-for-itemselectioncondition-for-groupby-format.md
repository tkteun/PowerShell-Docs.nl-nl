---
title: Het element PropertyName voor ItemSelectionCondition voor GroupBy (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: f6d671035bfd2ef6323b638fdd951bb020bd6548
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780879"
---
# <a name="propertyname-element-for-itemselectioncondition-for-groupby-format"></a><span data-ttu-id="c1213-102">Het element PropertyName voor ItemSelectionCondition voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c1213-102">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="c1213-103">Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="c1213-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="c1213-104">Wanneer deze eigenschap aanwezig is of wanneer deze wordt geëvalueerd `true` , wordt voldaan aan de voor waarde en wordt het besturings element gebruikt.</span><span class="sxs-lookup"><span data-stu-id="c1213-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="c1213-105">Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c1213-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="c1213-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element voor weer gave (indeling) GroupBy-element voor weer gave (indeling) CustomControl-element voor het element GroupBy (indeling) CustomEntries voor CustomControl voor het element GroupBy (Format) CustomEntry voor CustomControl voor GroupBy (Format) CustomItem-element voor CustomEntry voor het element GroupBy (Format) ExpressionBinding voor CustomItem voor het element GroupBy (Format) ItemSelectionCondition voor ExpressionBinding voor het element GroupBy (Format) voor ItemSelectionCondition voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="c1213-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format) PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c1213-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="c1213-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c1213-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="c1213-108">Attributes and Elements</span></span>

<span data-ttu-id="c1213-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `PropertyName` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="c1213-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c1213-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="c1213-110">Attributes</span></span>

<span data-ttu-id="c1213-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="c1213-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c1213-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="c1213-112">Child Elements</span></span>

<span data-ttu-id="c1213-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="c1213-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c1213-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="c1213-114">Parent Elements</span></span>

|<span data-ttu-id="c1213-115">Element</span><span class="sxs-lookup"><span data-stu-id="c1213-115">Element</span></span>|<span data-ttu-id="c1213-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="c1213-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c1213-117">Het element ItemSelectionCondition voor ExpressionBinding voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c1213-117">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="c1213-118">Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit besturings element.</span><span class="sxs-lookup"><span data-stu-id="c1213-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c1213-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="c1213-119">Text Value</span></span>

<span data-ttu-id="c1213-120">Geef de naam op van de .NET-eigenschap waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="c1213-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="c1213-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="c1213-121">Remarks</span></span>

<span data-ttu-id="c1213-122">Als dit element wordt gebruikt, kunt u het [script Block](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md) -element niet opgeven wanneer u de selectie voorwaarde definieert.</span><span class="sxs-lookup"><span data-stu-id="c1213-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="c1213-123">Zie ook</span><span class="sxs-lookup"><span data-stu-id="c1213-123">See Also</span></span>

[<span data-ttu-id="c1213-124">Het element ScriptBlock voor ItemSelectionCondition voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c1213-124">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)

[<span data-ttu-id="c1213-125">Het element ItemSelectionCondition voor ExpressionBinding voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c1213-125">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="c1213-126">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="c1213-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
