---
ms.date: 09/13/2016
ms.topic: reference
title: Het element ScriptBlock voor ItemSelectionCondition voor GroupBy (opmaak)
description: Het element ScriptBlock voor ItemSelectionCondition voor GroupBy (opmaak)
ms.openlocfilehash: fe366fa31b93e8d69409cc49c3fe2c350d4d06d9
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665085"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-groupby-format"></a><span data-ttu-id="5b754-103">Het element ScriptBlock voor ItemSelectionCondition voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="5b754-103">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="5b754-104">Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="5b754-104">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="5b754-105">Wanneer dit script wordt geëvalueerd `true` , wordt voldaan aan de voor waarde en wordt het besturings element gebruikt.</span><span class="sxs-lookup"><span data-stu-id="5b754-105">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="5b754-106">Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="5b754-106">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="5b754-107">Configuratie-element (indeling) ViewDefinitions element (indeling) element voor weer gave (indeling) GroupBy-element (Format) voor weer gave (indeling) CustomControl-element voor het element GroupBy (indeling) CustomEntries voor CustomControl voor GroupBy (Format) CustomEntry voor het element GroupBy (Format) CustomItem voor CustomEntry voor de ExpressionBinding-element van GroupBy (Format) voor CustomItem voor het element GroupBy (Format) ItemSelectionCondition voor ExpressionBinding voor het element GroupBy (Format) script Block voor ItemSelectionCondition voor GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="5b754-107">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format) ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5b754-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="5b754-108">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5b754-109">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="5b754-109">Attributes and Elements</span></span>

<span data-ttu-id="5b754-110">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `ScriptBlock` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="5b754-110">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5b754-111">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="5b754-111">Attributes</span></span>

<span data-ttu-id="5b754-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="5b754-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5b754-113">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="5b754-113">Child Elements</span></span>

<span data-ttu-id="5b754-114">Geen.</span><span class="sxs-lookup"><span data-stu-id="5b754-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5b754-115">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="5b754-115">Parent Elements</span></span>

|<span data-ttu-id="5b754-116">Element</span><span class="sxs-lookup"><span data-stu-id="5b754-116">Element</span></span>|<span data-ttu-id="5b754-117">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="5b754-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5b754-118">Het element ItemSelectionCondition voor ExpressionBinding voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="5b754-118">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="5b754-119">Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit besturings element.</span><span class="sxs-lookup"><span data-stu-id="5b754-119">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="5b754-120">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="5b754-120">Text Value</span></span>

<span data-ttu-id="5b754-121">Geef het script op dat wordt geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="5b754-121">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="5b754-122">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="5b754-122">Remarks</span></span>

<span data-ttu-id="5b754-123">Als dit element wordt gebruikt, kunt u het kenmerk [PropertyName](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) niet opgeven bij het definiëren van de selectie voorwaarde.</span><span class="sxs-lookup"><span data-stu-id="5b754-123">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="5b754-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="5b754-124">See Also</span></span>

[<span data-ttu-id="5b754-125">Het element ItemSelectionCondition voor ExpressionBinding voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="5b754-125">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="5b754-126">Het element PropertyName voor ItemSelectionCondition voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="5b754-126">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)

[<span data-ttu-id="5b754-127">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="5b754-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
