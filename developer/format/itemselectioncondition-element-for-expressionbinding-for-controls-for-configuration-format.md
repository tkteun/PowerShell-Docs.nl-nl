---
title: ItemSelectionCondition-Element voor ExpressionBinding voor besturingselementen voor de configuratie (-indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd3ddc33-b21c-4464-b3f2-a78dbe0062a8
caps.latest.revision: 8
ms.openlocfilehash: 4865d716ebe0460b662253a3019e93e82428b882
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065498"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format"></a><span data-ttu-id="6874a-102">Het element ItemSelectionCondition voor ExpressionBinding voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="6874a-102">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>

<span data-ttu-id="6874a-103">Hiermee definieert u de voorwaarde die moet bestaan voor dit besturingselement moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="6874a-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="6874a-104">Dit element wordt gebruikt bij het definiëren van een algemene besturingselement dat kan worden gebruikt door alle weergaven in de opmaak-bestand.</span><span class="sxs-lookup"><span data-stu-id="6874a-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="6874a-105">Configuratie-Element (indeling) besturingselementen Element van configuratie (-indeling) besturingselement Element controles voor configuratie (-indeling) CustomControl-Element voor het besturingselement voor configuratie (-indeling) CustomEntries-Element voor CustomControl voor configuratie ( -Indeling) CustomEntry Element voor CustomControl controles voor configuratie (-indeling) CustomItem-Element voor CustomEntry voor besturingselementen voor ExpressionBinding, configuratie-Element voor CustomItem voor besturingselementen voor de configuratie (-indeling) ItemSelectionCondition-Element voor ExpressionBinding voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="6874a-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6874a-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="6874a-106">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6874a-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="6874a-107">Attributes and Elements</span></span>

<span data-ttu-id="6874a-108">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `ItemSelectionCondition` element.</span><span class="sxs-lookup"><span data-stu-id="6874a-108">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6874a-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="6874a-109">Attributes</span></span>

<span data-ttu-id="6874a-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="6874a-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6874a-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="6874a-111">Child Elements</span></span>

|<span data-ttu-id="6874a-112">Element</span><span class="sxs-lookup"><span data-stu-id="6874a-112">Element</span></span>|<span data-ttu-id="6874a-113">Description</span><span class="sxs-lookup"><span data-stu-id="6874a-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6874a-114">PropertyName-Element voor ItemSelectionCondition voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="6874a-114">PropertyName Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="6874a-115">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="6874a-115">Optional element.</span></span><br /><br /> <span data-ttu-id="6874a-116">Hiermee geeft u de .NET-eigenschap die de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="6874a-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="6874a-117">ScriptBlock-Element voor ItemSelectionCondition voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="6874a-117">ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="6874a-118">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="6874a-118">Optional element.</span></span><br /><br /> <span data-ttu-id="6874a-119">Hiermee geeft u het script dat de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="6874a-119">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="6874a-120">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="6874a-120">Parent Elements</span></span>

|<span data-ttu-id="6874a-121">Element</span><span class="sxs-lookup"><span data-stu-id="6874a-121">Element</span></span>|<span data-ttu-id="6874a-122">Description</span><span class="sxs-lookup"><span data-stu-id="6874a-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6874a-123">ExpressionBinding-Element voor CustomItem voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="6874a-123">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="6874a-124">Definieert de gegevens die door het besturingselement wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="6874a-124">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6874a-125">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="6874a-125">Remarks</span></span>

<span data-ttu-id="6874a-126">U kunt een naam van eigenschap of een script voor deze voorwaarde opgeven, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="6874a-126">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="6874a-127">Zie ook</span><span class="sxs-lookup"><span data-stu-id="6874a-127">See Also</span></span>

[<span data-ttu-id="6874a-128">PropertyName-Element voor ItemSelectionCondition voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="6874a-128">PropertyName Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="6874a-129">ScriptBlock-Element voor ItemSelectionCondition voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="6874a-129">ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="6874a-130">ExpressionBinding-Element voor CustomItem voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="6874a-130">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="6874a-131">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="6874a-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
