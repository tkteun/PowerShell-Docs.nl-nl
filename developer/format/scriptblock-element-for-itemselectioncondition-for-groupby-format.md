---
title: ScriptBlock-Element voor ItemSelectionCondition voor GroupBy (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 58d25835-4636-4c58-9f6c-0332b9318051
caps.latest.revision: 6
ms.openlocfilehash: 4045196e306e766cd805b3e7ae31bfcb3de184ee
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850272"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-groupby-format"></a><span data-ttu-id="97da1-102">Het element ScriptBlock voor ItemSelectionCondition voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="97da1-102">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="97da1-103">Hiermee geeft u het script dat de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="97da1-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="97da1-104">Wanneer dit script wordt geëvalueerd naar `true`, de voorwaarde wordt voldaan, en wordt het besturingselement gebruikt.</span><span class="sxs-lookup"><span data-stu-id="97da1-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="97da1-105">Dit element wordt gebruikt bij het definiëren van hoe een nieuwe groep objecten worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="97da1-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="97da1-106">Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) GroupBy Element voor weergave (indeling) CustomControl Element voor GroupBy (indeling) CustomEntries Element voor CustomControl voor GroupBy (indeling) CustomEntry Element voor CustomControl voor GroupBy (indeling) CustomItem Element voor CustomEntry voor ExpressionBinding-Element voor CustomItem voor GroupBy (indeling) ItemSelectionCondition Element voor ExpressionBinding voor GroupBy (indeling) ScriptBlock Element voor GroupBy (indeling) ItemSelectionCondition voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="97da1-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format) ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="97da1-107">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="97da1-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="97da1-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="97da1-108">Attributes and Elements</span></span>

<span data-ttu-id="97da1-109">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `ScriptBlock` element.</span><span class="sxs-lookup"><span data-stu-id="97da1-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="97da1-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="97da1-110">Attributes</span></span>

<span data-ttu-id="97da1-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="97da1-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="97da1-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="97da1-112">Child Elements</span></span>

<span data-ttu-id="97da1-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="97da1-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="97da1-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="97da1-114">Parent Elements</span></span>

|<span data-ttu-id="97da1-115">Element</span><span class="sxs-lookup"><span data-stu-id="97da1-115">Element</span></span>|<span data-ttu-id="97da1-116">Description</span><span class="sxs-lookup"><span data-stu-id="97da1-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="97da1-117">ItemSelectionCondition-Element voor ExpressionBinding voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="97da1-117">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="97da1-118">Hiermee definieert u de voorwaarde die moet bestaan voor dit besturingselement moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="97da1-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="97da1-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="97da1-119">Text Value</span></span>

<span data-ttu-id="97da1-120">Geef het script dat wordt geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="97da1-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="97da1-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="97da1-121">Remarks</span></span>

<span data-ttu-id="97da1-122">Als dit element wordt gebruikt, kunt u niet opgeven de [PropertyName](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) element bij het definiëren van de selectievoorwaarde.</span><span class="sxs-lookup"><span data-stu-id="97da1-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="97da1-123">Zie ook</span><span class="sxs-lookup"><span data-stu-id="97da1-123">See Also</span></span>

[<span data-ttu-id="97da1-124">ItemSelectionCondition-Element voor ExpressionBinding voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="97da1-124">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="97da1-125">PropertyName-Element voor ItemSelectionCondition voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="97da1-125">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)

[<span data-ttu-id="97da1-126">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="97da1-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
