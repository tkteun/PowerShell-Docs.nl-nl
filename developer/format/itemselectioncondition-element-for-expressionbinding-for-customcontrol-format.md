---
title: ItemSelectionCondition-Element voor ExpressionBinding voor CustomControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f4bea9d8-27ad-410e-ad48-287f807d3e4e
caps.latest.revision: 7
ms.openlocfilehash: 18b0113c9b7b0895a1093cb0b56cd2d02c74a6c1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065815"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-customcontrol-format"></a><span data-ttu-id="cf7cd-102">Het element ItemSelectionCondition voor ExpressionBinding voor CustomControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="cf7cd-102">ItemSelectionCondition Element for ExpressionBinding for CustomControl (Format)</span></span>

<span data-ttu-id="cf7cd-103">Hiermee definieert u de voorwaarde die moet bestaan voor dit besturingselement moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="cf7cd-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="cf7cd-104">Er is geen limiet voor het aantal selectie voorwaarden die kan worden opgegeven voor een controle-item.</span><span class="sxs-lookup"><span data-stu-id="cf7cd-104">There is no limit to the number of selection conditions that can be specified for a control item.</span></span> <span data-ttu-id="cf7cd-105">Dit element wordt gebruikt bij het definiëren van een aangepast besturingselement-weergave.</span><span class="sxs-lookup"><span data-stu-id="cf7cd-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="cf7cd-106">Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) CustomControl Element (indeling) CustomEntries Element voor CustomControl voor weergave (indeling) CustomEntry Element voor CustomEntries voor weergave (indeling) CustomItem Element voor CustomEntry voor weergave (indeling) ExpressionBinding Element voor CustomItem voor CustomControl voor weergave (indeling) ItemSelectionCondition Element voor de Binding van de expressie voor CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="cf7cd-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="cf7cd-107">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="cf7cd-107">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cf7cd-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="cf7cd-108">Attributes and Elements</span></span>

<span data-ttu-id="cf7cd-109">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `ItemSelectionCondition` element.</span><span class="sxs-lookup"><span data-stu-id="cf7cd-109">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="cf7cd-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="cf7cd-110">Attributes</span></span>

<span data-ttu-id="cf7cd-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="cf7cd-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="cf7cd-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="cf7cd-112">Child Elements</span></span>

|<span data-ttu-id="cf7cd-113">Element</span><span class="sxs-lookup"><span data-stu-id="cf7cd-113">Element</span></span>|<span data-ttu-id="cf7cd-114">Description</span><span class="sxs-lookup"><span data-stu-id="cf7cd-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cf7cd-115">PropertyName-Element voor ItemSelectionCondition voor CustomControl voor weergave (indeling</span><span class="sxs-lookup"><span data-stu-id="cf7cd-115">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format</span></span>](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="cf7cd-116">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="cf7cd-116">Optional element.</span></span><br /><br /> <span data-ttu-id="cf7cd-117">Hiermee geeft u de .NET-eigenschap die de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="cf7cd-117">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="cf7cd-118">ScriptBlock-Element voor ItemSelectionCondition voor CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="cf7cd-118">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="cf7cd-119">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="cf7cd-119">Optional element.</span></span><br /><br /> <span data-ttu-id="cf7cd-120">Hiermee geeft u het script dat de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="cf7cd-120">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="cf7cd-121">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="cf7cd-121">Parent Elements</span></span>

|<span data-ttu-id="cf7cd-122">Element</span><span class="sxs-lookup"><span data-stu-id="cf7cd-122">Element</span></span>|<span data-ttu-id="cf7cd-123">Description</span><span class="sxs-lookup"><span data-stu-id="cf7cd-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cf7cd-124">ExpressionBinding-Element voor CustomItem voor CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="cf7cd-124">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="cf7cd-125">Definieert de gegevens die door het besturingselement wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="cf7cd-125">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="cf7cd-126">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="cf7cd-126">Remarks</span></span>

<span data-ttu-id="cf7cd-127">U kunt een naam van eigenschap of een script voor deze voorwaarde opgeven, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="cf7cd-127">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="cf7cd-128">Zie ook</span><span class="sxs-lookup"><span data-stu-id="cf7cd-128">See Also</span></span>

[<span data-ttu-id="cf7cd-129">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="cf7cd-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

[<span data-ttu-id="cf7cd-130">ExpressionBinding-Element voor CustomItem voor CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="cf7cd-130">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)
