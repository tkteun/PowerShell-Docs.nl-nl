---
ms.date: 09/13/2016
ms.topic: reference
title: Het element ItemSelectionCondition voor ExpressionBinding voor Besturingselementen voor Configuratie (opmaak)
description: Het element ItemSelectionCondition voor ExpressionBinding voor Besturingselementen voor Configuratie (opmaak)
ms.openlocfilehash: 6bd3d386ba64b33a1744fcc9e602cf13404765a0
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92648086"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format"></a><span data-ttu-id="986ea-103">Het element ItemSelectionCondition voor ExpressionBinding voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="986ea-103">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>

<span data-ttu-id="986ea-104">Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit besturings element.</span><span class="sxs-lookup"><span data-stu-id="986ea-104">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="986ea-105">Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="986ea-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="986ea-106">Configuratie-element (Format) Controls element van configuratie (Format) Control element voor besturings elementen voor configuratie (Format) CustomControl-element voor Control for Configuration (Format) CustomEntries element voor CustomControl voor Configuration (Format) CustomEntry element voor het CustomItem-element van de configuratie (indeling) voor CustomEntry voor besturings elementen voor de configuratie ExpressionBinding-element voor CustomItem voor besturings elementen voor configuratie (indeling) ItemSelectionCondition-element voor ExpressionBinding voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="986ea-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="986ea-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="986ea-107">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="986ea-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="986ea-108">Attributes and Elements</span></span>

<span data-ttu-id="986ea-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `ItemSelectionCondition` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="986ea-109">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="986ea-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="986ea-110">Attributes</span></span>

<span data-ttu-id="986ea-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="986ea-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="986ea-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="986ea-112">Child Elements</span></span>

|<span data-ttu-id="986ea-113">Element</span><span class="sxs-lookup"><span data-stu-id="986ea-113">Element</span></span>|<span data-ttu-id="986ea-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="986ea-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="986ea-115">Het element PropertyName voor ItemSelectionCondition voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="986ea-115">PropertyName Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="986ea-116">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="986ea-116">Optional element.</span></span><br /><br /> <span data-ttu-id="986ea-117">Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="986ea-117">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="986ea-118">Script block-element voor ItemSelectionCondition voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="986ea-118">ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="986ea-119">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="986ea-119">Optional element.</span></span><br /><br /> <span data-ttu-id="986ea-120">Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="986ea-120">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="986ea-121">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="986ea-121">Parent Elements</span></span>

|<span data-ttu-id="986ea-122">Element</span><span class="sxs-lookup"><span data-stu-id="986ea-122">Element</span></span>|<span data-ttu-id="986ea-123">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="986ea-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="986ea-124">Het element ExpressionBinding voor CustomItem voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="986ea-124">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="986ea-125">Hiermee worden de gegevens gedefinieerd die door het besturings element worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="986ea-125">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="986ea-126">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="986ea-126">Remarks</span></span>

<span data-ttu-id="986ea-127">U kunt voor dit probleem één eigenschaps naam of een script opgeven, maar niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="986ea-127">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="986ea-128">Zie ook</span><span class="sxs-lookup"><span data-stu-id="986ea-128">See Also</span></span>

[<span data-ttu-id="986ea-129">Het element PropertyName voor ItemSelectionCondition voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="986ea-129">PropertyName Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="986ea-130">Script block-element voor ItemSelectionCondition voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="986ea-130">ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="986ea-131">Het element ExpressionBinding voor CustomItem voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="986ea-131">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="986ea-132">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="986ea-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
