---
title: PropertyName-Element voor ItemSelectionCondition voor GroupBy (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 221cbdc2-f794-4f3a-9d40-bfdd8cba1013
caps.latest.revision: 6
ms.openlocfilehash: aae65789cf5572cbcc9251eca802a2d43065e49f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064761"
---
# <a name="propertyname-element-for-itemselectioncondition-for-groupby-format"></a><span data-ttu-id="23eeb-102">Het element PropertyName voor ItemSelectionCondition voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="23eeb-102">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="23eeb-103">Hiermee geeft u de .NET-eigenschap die de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="23eeb-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="23eeb-104">Als deze eigenschap is aanwezig, of wanneer deze wordt geëvalueerd naar `true`, de voorwaarde wordt voldaan, en wordt het besturingselement gebruikt.</span><span class="sxs-lookup"><span data-stu-id="23eeb-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="23eeb-105">Dit element wordt gebruikt bij het definiëren van hoe een nieuwe groep objecten worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="23eeb-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="23eeb-106">Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) GroupBy Element voor weergave (indeling) CustomControl Element voor GroupBy (indeling) CustomEntries Element voor CustomControl voor GroupBy (indeling) CustomEntry Element voor CustomControl voor GroupBy (indeling) CustomItem Element voor CustomEntry voor GroupBy (indeling) ExpressionBinding Element voor CustomItem voor GroupBy (indeling) ItemSelectionCondition Element voor ExpressionBinding voor PropertyName-Element voor GroupBy (indeling) ItemSelectionCondition voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="23eeb-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format) PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="23eeb-107">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="23eeb-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="23eeb-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="23eeb-108">Attributes and Elements</span></span>

<span data-ttu-id="23eeb-109">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `PropertyName` element.</span><span class="sxs-lookup"><span data-stu-id="23eeb-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="23eeb-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="23eeb-110">Attributes</span></span>

<span data-ttu-id="23eeb-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="23eeb-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="23eeb-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="23eeb-112">Child Elements</span></span>

<span data-ttu-id="23eeb-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="23eeb-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="23eeb-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="23eeb-114">Parent Elements</span></span>

|<span data-ttu-id="23eeb-115">Element</span><span class="sxs-lookup"><span data-stu-id="23eeb-115">Element</span></span>|<span data-ttu-id="23eeb-116">Description</span><span class="sxs-lookup"><span data-stu-id="23eeb-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="23eeb-117">ItemSelectionCondition-Element voor ExpressionBinding voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="23eeb-117">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="23eeb-118">Hiermee definieert u de voorwaarde die moet bestaan voor dit besturingselement moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="23eeb-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="23eeb-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="23eeb-119">Text Value</span></span>

<span data-ttu-id="23eeb-120">Geef de naam van de .NET-eigenschap die de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="23eeb-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="23eeb-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="23eeb-121">Remarks</span></span>

<span data-ttu-id="23eeb-122">Als dit element wordt gebruikt, kunt u niet opgeven de [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md) element bij het definiëren van de selectievoorwaarde.</span><span class="sxs-lookup"><span data-stu-id="23eeb-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="23eeb-123">Zie ook</span><span class="sxs-lookup"><span data-stu-id="23eeb-123">See Also</span></span>

[<span data-ttu-id="23eeb-124">ScriptBlock-Element voor ItemSelectionCondition voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="23eeb-124">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)

[<span data-ttu-id="23eeb-125">ItemSelectionCondition-Element voor ExpressionBinding voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="23eeb-125">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="23eeb-126">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="23eeb-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
