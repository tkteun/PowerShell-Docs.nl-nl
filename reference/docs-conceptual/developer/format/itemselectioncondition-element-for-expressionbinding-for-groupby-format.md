---
ms.date: 09/13/2016
ms.topic: reference
title: Het element ItemSelectionCondition voor ExpressionBinding voor GroupBy (opmaak)
description: Het element ItemSelectionCondition voor ExpressionBinding voor GroupBy (opmaak)
ms.openlocfilehash: 92120ace5ed316fbfbf1d51422071c27d5a604cf
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92651980"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-groupby-format"></a><span data-ttu-id="f3255-103">Het element ItemSelectionCondition voor ExpressionBinding voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="f3255-103">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>

<span data-ttu-id="f3255-104">Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit besturings element.</span><span class="sxs-lookup"><span data-stu-id="f3255-104">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="f3255-105">Er is geen limiet voor het aantal selectie omstandigheden dat kan worden opgegeven voor een besturings element.</span><span class="sxs-lookup"><span data-stu-id="f3255-105">There is no limit to the number of selection conditions that can be specified for a control item.</span></span> <span data-ttu-id="f3255-106">Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="f3255-106">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="f3255-107">Configuratie-element (indeling) ViewDefinitions element (indeling) element van het type GroupBy-element (Format) voor weer gave (indeling) CustomControl-element voor het CustomEntries-element van GroupBy (Format) voor CustomControl voor het element GroupBy (Format) CustomEntry element voor CustomControl voor het object GroupBy (Format) voor CustomEntry voor het element GroupBy (Format) ExpressionBinding voor CustomItem voor GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="f3255-107">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f3255-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="f3255-108">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f3255-109">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="f3255-109">Attributes and Elements</span></span>

<span data-ttu-id="f3255-110">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `ItemSelectionCondition` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="f3255-110">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f3255-111">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="f3255-111">Attributes</span></span>

<span data-ttu-id="f3255-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="f3255-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f3255-113">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="f3255-113">Child Elements</span></span>

|<span data-ttu-id="f3255-114">Element</span><span class="sxs-lookup"><span data-stu-id="f3255-114">Element</span></span>|<span data-ttu-id="f3255-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="f3255-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f3255-116">Het element PropertyName voor ItemSelectionCondition voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="f3255-116">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)|<span data-ttu-id="f3255-117">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="f3255-117">Optional element.</span></span><br /><br /> <span data-ttu-id="f3255-118">Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="f3255-118">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="f3255-119">Het element ScriptBlock voor ItemSelectionCondition voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="f3255-119">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)|<span data-ttu-id="f3255-120">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="f3255-120">Optional element.</span></span><br /><br /> <span data-ttu-id="f3255-121">Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="f3255-121">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f3255-122">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="f3255-122">Parent Elements</span></span>

|<span data-ttu-id="f3255-123">Element</span><span class="sxs-lookup"><span data-stu-id="f3255-123">Element</span></span>|<span data-ttu-id="f3255-124">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="f3255-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f3255-125">Het element ExpressionBinding voor CustomItem voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="f3255-125">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="f3255-126">Hiermee worden de gegevens gedefinieerd die door het besturings element worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="f3255-126">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f3255-127">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="f3255-127">Remarks</span></span>

<span data-ttu-id="f3255-128">U kunt voor dit probleem één eigenschaps naam of een script opgeven, maar niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="f3255-128">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="f3255-129">Zie ook</span><span class="sxs-lookup"><span data-stu-id="f3255-129">See Also</span></span>

[<span data-ttu-id="f3255-130">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="f3255-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

[<span data-ttu-id="f3255-131">Het element ExpressionBinding voor CustomItem voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="f3255-131">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)
