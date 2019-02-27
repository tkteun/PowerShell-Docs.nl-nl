---
title: ItemSelectionCondition-Element voor ExpressionBinding voor besturingselementen voor weergave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82c15014-2440-410d-b02d-b7f1a49240a0
caps.latest.revision: 7
ms.openlocfilehash: 80f375c53c205c793600655fa6031d114871618e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850902"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format"></a><span data-ttu-id="69b27-102">Het element ItemSelectionCondition voor ExpressionBinding voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="69b27-102">ItemSelectionCondition Element for ExpressionBinding for Controls for View (Format)</span></span>

<span data-ttu-id="69b27-103">Hiermee definieert u de voorwaarde die moet bestaan voor dit besturingselement moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="69b27-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="69b27-104">Dit element wordt gebruikt bij het definiëren van besturingselementen die kunnen worden gebruikt door een weergave.</span><span class="sxs-lookup"><span data-stu-id="69b27-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="69b27-105">Configuratie-Element (indeling) ViewDefinitions-Element (indeling) weergave-Element (indeling) besturingselementen Element (indeling) controle-Element voor besturingselementen voor weergave (indeling) CustomControl Element voor de controle voor besturingselementen voor weergave (indeling) CustomEntries Element voor CustomControl voor weergave (indeling) CustomEntry Element voor CustomEntries voor besturingselementen voor weergave (indeling) CustomItem Element voor CustomEntry voor besturingselementen voor weergave (indeling) ExpressionBinding Element voor CustomItem voor besturingselementen voor weergave (indeling) ItemSelectionCondition-Element van ExpressionBinding voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="69b27-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="69b27-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="69b27-106">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="69b27-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="69b27-107">Attributes and Elements</span></span>

<span data-ttu-id="69b27-108">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `ItemSelectionCondition` element.</span><span class="sxs-lookup"><span data-stu-id="69b27-108">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="69b27-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="69b27-109">Attributes</span></span>

<span data-ttu-id="69b27-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="69b27-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="69b27-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="69b27-111">Child Elements</span></span>

|<span data-ttu-id="69b27-112">Element</span><span class="sxs-lookup"><span data-stu-id="69b27-112">Element</span></span>|<span data-ttu-id="69b27-113">Description</span><span class="sxs-lookup"><span data-stu-id="69b27-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="69b27-114">PropertyName-Element voor ItemSelectionCondition voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="69b27-114">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="69b27-115">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="69b27-115">Optional element.</span></span><br /><br /> <span data-ttu-id="69b27-116">Hiermee geeft u de .NET-eigenschap die de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="69b27-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="69b27-117">ScriptBlock-Element voor ItemSelectionCondition voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="69b27-117">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="69b27-118">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="69b27-118">Optional element.</span></span><br /><br /> <span data-ttu-id="69b27-119">Hiermee geeft u het script dat de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="69b27-119">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="69b27-120">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="69b27-120">Parent Elements</span></span>

|<span data-ttu-id="69b27-121">Element</span><span class="sxs-lookup"><span data-stu-id="69b27-121">Element</span></span>|<span data-ttu-id="69b27-122">Description</span><span class="sxs-lookup"><span data-stu-id="69b27-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="69b27-123">ExpressionBinding-Element voor CustomItem voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="69b27-123">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="69b27-124">Definieert de gegevens die door het besturingselement wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="69b27-124">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="69b27-125">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="69b27-125">Remarks</span></span>

<span data-ttu-id="69b27-126">U kunt een naam van eigenschap of een script voor deze voorwaarde opgeven, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="69b27-126">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="69b27-127">Zie ook</span><span class="sxs-lookup"><span data-stu-id="69b27-127">See Also</span></span>

[<span data-ttu-id="69b27-128">PropertyName-Element voor ItemSelectionCondition voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="69b27-128">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="69b27-129">ScriptBlock-Element voor ItemSelectionCondition voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="69b27-129">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="69b27-130">ExpressionBinding-Element voor CustomItem voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="69b27-130">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="69b27-131">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="69b27-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
