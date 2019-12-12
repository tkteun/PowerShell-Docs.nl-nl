---
title: ItemSelectionCondition-element voor ExpressionBinding voor CustomControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f4bea9d8-27ad-410e-ad48-287f807d3e4e
caps.latest.revision: 7
ms.openlocfilehash: 18b0113c9b7b0895a1093cb0b56cd2d02c74a6c1
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72354458"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-customcontrol-format"></a><span data-ttu-id="20e47-102">Het element ItemSelectionCondition voor ExpressionBinding voor CustomControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="20e47-102">ItemSelectionCondition Element for ExpressionBinding for CustomControl (Format)</span></span>

<span data-ttu-id="20e47-103">Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit besturings element.</span><span class="sxs-lookup"><span data-stu-id="20e47-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="20e47-104">Er is geen limiet voor het aantal selectie omstandigheden dat kan worden opgegeven voor een besturings element.</span><span class="sxs-lookup"><span data-stu-id="20e47-104">There is no limit to the number of selection conditions that can be specified for a control item.</span></span> <span data-ttu-id="20e47-105">Dit element wordt gebruikt bij het definiëren van een aangepaste beheer weergave.</span><span class="sxs-lookup"><span data-stu-id="20e47-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="20e47-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) CustomControl-element (indeling) CustomEntries element voor CustomControl voor weer gave (Format) CustomEntry-element voor CustomEntries voor weer gave (Format) CustomItem element voor CustomEntry voor View (Format) ExpressionBinding-element voor CustomItem voor CustomControl voor weer gave (indeling) ItemSelectionCondition element voor expressie binding voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="20e47-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="20e47-107">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="20e47-107">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="20e47-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="20e47-108">Attributes and Elements</span></span>

<span data-ttu-id="20e47-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `ItemSelectionCondition` beschreven.</span><span class="sxs-lookup"><span data-stu-id="20e47-109">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="20e47-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="20e47-110">Attributes</span></span>

<span data-ttu-id="20e47-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="20e47-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="20e47-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="20e47-112">Child Elements</span></span>

|<span data-ttu-id="20e47-113">Element</span><span class="sxs-lookup"><span data-stu-id="20e47-113">Element</span></span>|<span data-ttu-id="20e47-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="20e47-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="20e47-115">Het element PropertyName voor ItemSelectionCondition voor CustomControl voor weer gave (notatie</span><span class="sxs-lookup"><span data-stu-id="20e47-115">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format</span></span>](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="20e47-116">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="20e47-116">Optional element.</span></span><br /><br /> <span data-ttu-id="20e47-117">Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="20e47-117">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="20e47-118">Script block-element voor ItemSelectionCondition voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="20e47-118">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="20e47-119">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="20e47-119">Optional element.</span></span><br /><br /> <span data-ttu-id="20e47-120">Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="20e47-120">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="20e47-121">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="20e47-121">Parent Elements</span></span>

|<span data-ttu-id="20e47-122">Element</span><span class="sxs-lookup"><span data-stu-id="20e47-122">Element</span></span>|<span data-ttu-id="20e47-123">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="20e47-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="20e47-124">ExpressionBinding-element voor CustomItem voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="20e47-124">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="20e47-125">Hiermee worden de gegevens gedefinieerd die door het besturings element worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="20e47-125">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="20e47-126">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="20e47-126">Remarks</span></span>

<span data-ttu-id="20e47-127">U kunt voor dit probleem één eigenschaps naam of een script opgeven, maar niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="20e47-127">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="20e47-128">Zie ook</span><span class="sxs-lookup"><span data-stu-id="20e47-128">See Also</span></span>

[<span data-ttu-id="20e47-129">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="20e47-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

[<span data-ttu-id="20e47-130">ExpressionBinding-element voor CustomItem voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="20e47-130">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)
