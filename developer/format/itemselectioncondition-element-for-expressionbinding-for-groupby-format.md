---
title: ItemSelectionCondition-Element voor ExpressionBinding voor GroupBy (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6af3be7d-921e-4cf7-bd5a-d87aa0b4efbd
caps.latest.revision: 7
ms.openlocfilehash: b2b0a0d1996392614807e08b820a72978e38a0cb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56844805"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-groupby-format"></a><span data-ttu-id="a674f-102">Het element ItemSelectionCondition voor ExpressionBinding voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="a674f-102">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>

<span data-ttu-id="a674f-103">Hiermee definieert u de voorwaarde die moet bestaan voor dit besturingselement moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="a674f-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="a674f-104">Er is geen limiet voor het aantal selectie voorwaarden die kan worden opgegeven voor een controle-item.</span><span class="sxs-lookup"><span data-stu-id="a674f-104">There is no limit to the number of selection conditions that can be specified for a control item.</span></span> <span data-ttu-id="a674f-105">Dit element wordt gebruikt bij het definiëren van hoe een nieuwe groep objecten worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="a674f-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="a674f-106">Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) GroupBy Element voor weergave (indeling) CustomControl Element voor GroupBy (indeling) CustomEntries Element voor CustomControl voor GroupBy (indeling) CustomEntry Element voor CustomControl voor GroupBy (indeling) CustomItem Element voor CustomEntry voor GroupBy (indeling) ExpressionBinding Element voor CustomItem voor GroupBy (indeling) ItemSelectionCondition Element voor ExpressionBinding voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="a674f-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a674f-107">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="a674f-107">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a674f-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="a674f-108">Attributes and Elements</span></span>

<span data-ttu-id="a674f-109">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `ItemSelectionCondition` element.</span><span class="sxs-lookup"><span data-stu-id="a674f-109">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a674f-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="a674f-110">Attributes</span></span>

<span data-ttu-id="a674f-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="a674f-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a674f-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="a674f-112">Child Elements</span></span>

|<span data-ttu-id="a674f-113">Element</span><span class="sxs-lookup"><span data-stu-id="a674f-113">Element</span></span>|<span data-ttu-id="a674f-114">Description</span><span class="sxs-lookup"><span data-stu-id="a674f-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a674f-115">PropertyName-Element voor ItemSelectionCondition voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="a674f-115">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)|<span data-ttu-id="a674f-116">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="a674f-116">Optional element.</span></span><br /><br /> <span data-ttu-id="a674f-117">Hiermee geeft u de .NET-eigenschap die de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="a674f-117">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="a674f-118">ScriptBlock-Element voor ItemSelectionCondition voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="a674f-118">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)|<span data-ttu-id="a674f-119">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="a674f-119">Optional element.</span></span><br /><br /> <span data-ttu-id="a674f-120">Hiermee geeft u het script dat de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="a674f-120">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a674f-121">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="a674f-121">Parent Elements</span></span>

|<span data-ttu-id="a674f-122">Element</span><span class="sxs-lookup"><span data-stu-id="a674f-122">Element</span></span>|<span data-ttu-id="a674f-123">Description</span><span class="sxs-lookup"><span data-stu-id="a674f-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a674f-124">ExpressionBinding-Element voor CustomItem voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="a674f-124">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="a674f-125">Definieert de gegevens die door het besturingselement wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="a674f-125">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a674f-126">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="a674f-126">Remarks</span></span>

<span data-ttu-id="a674f-127">U kunt een naam van eigenschap of een script voor deze voorwaarde opgeven, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="a674f-127">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="a674f-128">Zie ook</span><span class="sxs-lookup"><span data-stu-id="a674f-128">See Also</span></span>

[<span data-ttu-id="a674f-129">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="a674f-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

[<span data-ttu-id="a674f-130">ExpressionBinding-Element voor CustomItem voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="a674f-130">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)
