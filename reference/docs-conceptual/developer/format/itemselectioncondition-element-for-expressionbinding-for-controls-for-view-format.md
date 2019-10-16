---
title: ItemSelectionCondition-element voor ExpressionBinding voor besturings elementen voor weer gave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82c15014-2440-410d-b02d-b7f1a49240a0
caps.latest.revision: 7
ms.openlocfilehash: 80f375c53c205c793600655fa6031d114871618e
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72354479"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format"></a><span data-ttu-id="9b722-102">Het element ItemSelectionCondition voor ExpressionBinding voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="9b722-102">ItemSelectionCondition Element for ExpressionBinding for Controls for View (Format)</span></span>

<span data-ttu-id="9b722-103">Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit besturings element.</span><span class="sxs-lookup"><span data-stu-id="9b722-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="9b722-104">Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.</span><span class="sxs-lookup"><span data-stu-id="9b722-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="9b722-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) Controls-element (Format) Control element (opmaak) voor besturings elementen voor de weer gave (indeling) CustomControl-element voor besturings elementen voor Controls (Format) CustomEntries element voor CustomControl voor View (Format) CustomEntry-element voor CustomEntries voor besturings elementen voor weer gave (Format) CustomItem-element voor CustomEntry voor besturings elementen voor de weer gave (Format) ExpressionBinding-element voor CustomItem voor besturings elementen voor weer gave (indeling) ItemSelectionCondition-element van ExpressionBinding voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="9b722-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9b722-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="9b722-106">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9b722-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="9b722-107">Attributes and Elements</span></span>

<span data-ttu-id="9b722-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `ItemSelectionCondition` beschreven.</span><span class="sxs-lookup"><span data-stu-id="9b722-108">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9b722-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="9b722-109">Attributes</span></span>

<span data-ttu-id="9b722-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="9b722-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9b722-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="9b722-111">Child Elements</span></span>

|<span data-ttu-id="9b722-112">Element</span><span class="sxs-lookup"><span data-stu-id="9b722-112">Element</span></span>|<span data-ttu-id="9b722-113">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="9b722-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9b722-114">Het element PropertyName voor ItemSelectionCondition voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="9b722-114">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="9b722-115">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="9b722-115">Optional element.</span></span><br /><br /> <span data-ttu-id="9b722-116">Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="9b722-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="9b722-117">Script block-element voor ItemSelectionCondition voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="9b722-117">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="9b722-118">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="9b722-118">Optional element.</span></span><br /><br /> <span data-ttu-id="9b722-119">Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="9b722-119">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="9b722-120">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="9b722-120">Parent Elements</span></span>

|<span data-ttu-id="9b722-121">Element</span><span class="sxs-lookup"><span data-stu-id="9b722-121">Element</span></span>|<span data-ttu-id="9b722-122">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="9b722-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9b722-123">ExpressionBinding-element voor CustomItem voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="9b722-123">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="9b722-124">Hiermee worden de gegevens gedefinieerd die door het besturings element worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="9b722-124">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9b722-125">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="9b722-125">Remarks</span></span>

<span data-ttu-id="9b722-126">U kunt voor dit probleem één eigenschaps naam of een script opgeven, maar niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="9b722-126">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="9b722-127">Zie ook</span><span class="sxs-lookup"><span data-stu-id="9b722-127">See Also</span></span>

[<span data-ttu-id="9b722-128">Het element PropertyName voor ItemSelectionCondition voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="9b722-128">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="9b722-129">Script block-element voor ItemSelectionCondition voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="9b722-129">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="9b722-130">ExpressionBinding-element voor CustomItem voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="9b722-130">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="9b722-131">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="9b722-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
