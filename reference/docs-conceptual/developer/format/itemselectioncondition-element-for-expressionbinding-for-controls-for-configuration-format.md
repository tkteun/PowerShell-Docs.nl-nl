---
title: ItemSelectionCondition-element voor ExpressionBinding voor besturings elementen voor configuratie (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd3ddc33-b21c-4464-b3f2-a78dbe0062a8
caps.latest.revision: 8
ms.openlocfilehash: 4865d716ebe0460b662253a3019e93e82428b882
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72354465"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format"></a><span data-ttu-id="b2de2-102">Het element ItemSelectionCondition voor ExpressionBinding voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="b2de2-102">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>

<span data-ttu-id="b2de2-103">Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit besturings element.</span><span class="sxs-lookup"><span data-stu-id="b2de2-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="b2de2-104">Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="b2de2-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="b2de2-105">Configuratie-element (Format) Controls element van configuratie (Format) Control element voor besturings elementen voor configuratie (Format) CustomControl-element voor Control for Configuration (Format) CustomEntries element voor het configureren van een configuratie ( Format) CustomEntry element voor CustomControl voor besturings elementen voor configuratie (indeling) CustomItem-element voor CustomEntry voor besturings elementen voor configuratie ExpressionBinding-element voor CustomItem voor besturings elementen voor configuratie (indeling) ItemSelectionCondition-element voor ExpressionBinding voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="b2de2-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b2de2-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="b2de2-106">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b2de2-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="b2de2-107">Attributes and Elements</span></span>

<span data-ttu-id="b2de2-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `ItemSelectionCondition` beschreven.</span><span class="sxs-lookup"><span data-stu-id="b2de2-108">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b2de2-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="b2de2-109">Attributes</span></span>

<span data-ttu-id="b2de2-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="b2de2-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b2de2-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="b2de2-111">Child Elements</span></span>

|<span data-ttu-id="b2de2-112">Element</span><span class="sxs-lookup"><span data-stu-id="b2de2-112">Element</span></span>|<span data-ttu-id="b2de2-113">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="b2de2-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b2de2-114">Het element PropertyName voor ItemSelectionCondition voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="b2de2-114">PropertyName Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="b2de2-115">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="b2de2-115">Optional element.</span></span><br /><br /> <span data-ttu-id="b2de2-116">Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="b2de2-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="b2de2-117">Script block-element voor ItemSelectionCondition voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="b2de2-117">ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="b2de2-118">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="b2de2-118">Optional element.</span></span><br /><br /> <span data-ttu-id="b2de2-119">Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="b2de2-119">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b2de2-120">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="b2de2-120">Parent Elements</span></span>

|<span data-ttu-id="b2de2-121">Element</span><span class="sxs-lookup"><span data-stu-id="b2de2-121">Element</span></span>|<span data-ttu-id="b2de2-122">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="b2de2-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b2de2-123">ExpressionBinding-element voor CustomItem voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="b2de2-123">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="b2de2-124">Hiermee worden de gegevens gedefinieerd die door het besturings element worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="b2de2-124">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b2de2-125">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="b2de2-125">Remarks</span></span>

<span data-ttu-id="b2de2-126">U kunt voor dit probleem één eigenschaps naam of een script opgeven, maar niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="b2de2-126">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="b2de2-127">Zie ook</span><span class="sxs-lookup"><span data-stu-id="b2de2-127">See Also</span></span>

[<span data-ttu-id="b2de2-128">Het element PropertyName voor ItemSelectionCondition voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="b2de2-128">PropertyName Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="b2de2-129">Script block-element voor ItemSelectionCondition voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="b2de2-129">ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="b2de2-130">ExpressionBinding-element voor CustomItem voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="b2de2-130">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="b2de2-131">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="b2de2-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
