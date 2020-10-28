---
ms.date: 09/13/2016
ms.topic: reference
title: Het element ItemSelectionCondition voor ExpressionBinding voor CustomControl (opmaak)
description: Het element ItemSelectionCondition voor ExpressionBinding voor CustomControl (opmaak)
ms.openlocfilehash: 38c88ad47e57cd20902c6b8aabdb0b8e8b682ba4
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92648038"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-customcontrol-format"></a><span data-ttu-id="6479e-103">Het element ItemSelectionCondition voor ExpressionBinding voor CustomControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="6479e-103">ItemSelectionCondition Element for ExpressionBinding for CustomControl (Format)</span></span>

<span data-ttu-id="6479e-104">Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit besturings element.</span><span class="sxs-lookup"><span data-stu-id="6479e-104">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="6479e-105">Er is geen limiet voor het aantal selectie omstandigheden dat kan worden opgegeven voor een besturings element.</span><span class="sxs-lookup"><span data-stu-id="6479e-105">There is no limit to the number of selection conditions that can be specified for a control item.</span></span> <span data-ttu-id="6479e-106">Dit element wordt gebruikt bij het definiëren van een aangepaste beheer weergave.</span><span class="sxs-lookup"><span data-stu-id="6479e-106">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="6479e-107">Configuratie-element (indeling) ViewDefinitions element (indeling) weer gave element (indeling) CustomControl element (Format) CustomEntries element voor CustomControl voor weer gave (Format) CustomEntry-element voor CustomEntries voor weer gave (Format) CustomItem element voor CustomEntry voor weer gave (Format) ExpressionBinding element voor CustomItem voor weer gave (Format) voor expressie binding</span><span class="sxs-lookup"><span data-stu-id="6479e-107">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6479e-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="6479e-108">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6479e-109">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="6479e-109">Attributes and Elements</span></span>

<span data-ttu-id="6479e-110">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `ItemSelectionCondition` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="6479e-110">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6479e-111">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="6479e-111">Attributes</span></span>

<span data-ttu-id="6479e-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="6479e-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6479e-113">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="6479e-113">Child Elements</span></span>

|<span data-ttu-id="6479e-114">Element</span><span class="sxs-lookup"><span data-stu-id="6479e-114">Element</span></span>|<span data-ttu-id="6479e-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="6479e-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6479e-116">Het element PropertyName voor ItemSelectionCondition voor CustomControl voor weer gave (notatie</span><span class="sxs-lookup"><span data-stu-id="6479e-116">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format</span></span>](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="6479e-117">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="6479e-117">Optional element.</span></span><br /><br /> <span data-ttu-id="6479e-118">Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="6479e-118">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="6479e-119">Het element ScriptBlock voor ItemSelectionCondition voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="6479e-119">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="6479e-120">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="6479e-120">Optional element.</span></span><br /><br /> <span data-ttu-id="6479e-121">Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="6479e-121">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="6479e-122">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="6479e-122">Parent Elements</span></span>

|<span data-ttu-id="6479e-123">Element</span><span class="sxs-lookup"><span data-stu-id="6479e-123">Element</span></span>|<span data-ttu-id="6479e-124">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="6479e-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6479e-125">Het element ExpressionBinding voor CustomItem voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="6479e-125">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="6479e-126">Hiermee worden de gegevens gedefinieerd die door het besturings element worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="6479e-126">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6479e-127">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="6479e-127">Remarks</span></span>

<span data-ttu-id="6479e-128">U kunt voor dit probleem één eigenschaps naam of een script opgeven, maar niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="6479e-128">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="6479e-129">Zie ook</span><span class="sxs-lookup"><span data-stu-id="6479e-129">See Also</span></span>

[<span data-ttu-id="6479e-130">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="6479e-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

[<span data-ttu-id="6479e-131">Het element ExpressionBinding voor CustomItem voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="6479e-131">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)
