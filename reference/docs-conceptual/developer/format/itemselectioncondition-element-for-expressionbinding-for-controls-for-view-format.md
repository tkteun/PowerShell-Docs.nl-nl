---
title: ItemSelectionCondition-element voor ExpressionBinding voor besturings elementen voor weer gave (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e8e3ea64fd947fbb2b98c410ac08533f386c9505
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781202"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format"></a><span data-ttu-id="fde4f-102">Het element ItemSelectionCondition voor ExpressionBinding voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="fde4f-102">ItemSelectionCondition Element for ExpressionBinding for Controls for View (Format)</span></span>

<span data-ttu-id="fde4f-103">Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit besturings element.</span><span class="sxs-lookup"><span data-stu-id="fde4f-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="fde4f-104">Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.</span><span class="sxs-lookup"><span data-stu-id="fde4f-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="fde4f-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) Controls-element (Format) Control element (indeling) voor besturings elementen voor weer gave (indeling) CustomControl-element voor besturings elementen voor het element Control Format) CustomEntry-element voor CustomEntries voor besturings elementen voor de weer gave (indeling) CustomItem-element voor CustomEntry voor besturings elementen voor het ExpressionBinding-element van de CustomItem voor besturings elementen voor weer gave (opmaak) ItemSelectionCondition element van ExpressionBinding voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="fde4f-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fde4f-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="fde4f-106">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fde4f-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="fde4f-107">Attributes and Elements</span></span>

<span data-ttu-id="fde4f-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `ItemSelectionCondition` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="fde4f-108">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="fde4f-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="fde4f-109">Attributes</span></span>

<span data-ttu-id="fde4f-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="fde4f-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fde4f-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="fde4f-111">Child Elements</span></span>

|<span data-ttu-id="fde4f-112">Element</span><span class="sxs-lookup"><span data-stu-id="fde4f-112">Element</span></span>|<span data-ttu-id="fde4f-113">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="fde4f-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fde4f-114">Het element PropertyName voor ItemSelectionCondition voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="fde4f-114">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="fde4f-115">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="fde4f-115">Optional element.</span></span><br /><br /> <span data-ttu-id="fde4f-116">Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="fde4f-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="fde4f-117">Het element ScriptBlock voor ItemSelectionCondition voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="fde4f-117">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="fde4f-118">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="fde4f-118">Optional element.</span></span><br /><br /> <span data-ttu-id="fde4f-119">Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="fde4f-119">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="fde4f-120">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="fde4f-120">Parent Elements</span></span>

|<span data-ttu-id="fde4f-121">Element</span><span class="sxs-lookup"><span data-stu-id="fde4f-121">Element</span></span>|<span data-ttu-id="fde4f-122">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="fde4f-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fde4f-123">Het element ExpressionBinding voor CustomItem voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="fde4f-123">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="fde4f-124">Hiermee worden de gegevens gedefinieerd die door het besturings element worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="fde4f-124">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="fde4f-125">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="fde4f-125">Remarks</span></span>

<span data-ttu-id="fde4f-126">U kunt voor dit probleem één eigenschaps naam of een script opgeven, maar niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="fde4f-126">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="fde4f-127">Zie ook</span><span class="sxs-lookup"><span data-stu-id="fde4f-127">See Also</span></span>

[<span data-ttu-id="fde4f-128">Het element PropertyName voor ItemSelectionCondition voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="fde4f-128">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="fde4f-129">Het element ScriptBlock voor ItemSelectionCondition voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="fde4f-129">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="fde4f-130">Het element ExpressionBinding voor CustomItem voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="fde4f-130">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="fde4f-131">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="fde4f-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
