---
title: PropertyName-Element voor ItemSelectionCondition voor besturingselementen voor weergave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ba3955bc-f3a1-4ef6-86ac-80ffc133ad1b
caps.latest.revision: 6
ms.openlocfilehash: 28ad31be4be7be20f1f43ea1b69ad5d294de86f6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075848"
---
# <a name="propertyname-element-for-itemselectioncondition-for-controls-for-view-format"></a><span data-ttu-id="06d23-102">Het element PropertyName voor ItemSelectionCondition voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="06d23-102">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="06d23-103">Hiermee geeft u de .NET-eigenschap die de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="06d23-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="06d23-104">Als deze eigenschap is aanwezig, of wanneer deze wordt geëvalueerd naar `true`, de voorwaarde wordt voldaan, en wordt het besturingselement gebruikt.</span><span class="sxs-lookup"><span data-stu-id="06d23-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="06d23-105">Dit element wordt gebruikt bij het definiëren van besturingselementen die kunnen worden gebruikt door een weergave.</span><span class="sxs-lookup"><span data-stu-id="06d23-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="06d23-106">Configuratie-Element (indeling) ViewDefinitions-Element (indeling) weergave-Element (indeling) besturingselementen Element (indeling) controle-Element voor besturingselementen voor weergave (indeling) CustomControl Element voor de controle voor besturingselementen voor weergave (indeling) CustomEntries Element voor CustomControl voor weergave (indeling) CustomEntry Element voor CustomEntries voor besturingselementen voor weergave (indeling) CustomItem Element voor CustomEntry voor besturingselementen voor weergave (indeling) ExpressionBinding Element voor CustomItem voor besturingselementen voor weergave (indeling) ItemSelectionCondition-Element van ExpressionBinding voor besturingselementen voor weergave (indeling) PropertyName-Element voor ItemSelectionCondition voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="06d23-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format) PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="06d23-107">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="06d23-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="06d23-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="06d23-108">Attributes and Elements</span></span>

<span data-ttu-id="06d23-109">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `PropertyName` element.</span><span class="sxs-lookup"><span data-stu-id="06d23-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="06d23-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="06d23-110">Attributes</span></span>

<span data-ttu-id="06d23-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="06d23-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="06d23-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="06d23-112">Child Elements</span></span>

<span data-ttu-id="06d23-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="06d23-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="06d23-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="06d23-114">Parent Elements</span></span>

|<span data-ttu-id="06d23-115">Element</span><span class="sxs-lookup"><span data-stu-id="06d23-115">Element</span></span>|<span data-ttu-id="06d23-116">Description</span><span class="sxs-lookup"><span data-stu-id="06d23-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="06d23-117">ItemSelectionCondition-Element van ExpressionBinding voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="06d23-117">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="06d23-118">Hiermee definieert u de voorwaarde die moet bestaan voor dit besturingselement moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="06d23-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="06d23-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="06d23-119">Text Value</span></span>

<span data-ttu-id="06d23-120">Geef de naam van de .NET-eigenschap die de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="06d23-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="06d23-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="06d23-121">Remarks</span></span>

<span data-ttu-id="06d23-122">Als dit element wordt gebruikt, kunt u niet opgeven de [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md) element bij het definiëren van de selectievoorwaarde.</span><span class="sxs-lookup"><span data-stu-id="06d23-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="06d23-123">Zie ook</span><span class="sxs-lookup"><span data-stu-id="06d23-123">See Also</span></span>

[<span data-ttu-id="06d23-124">ScriptBlock-Element voor ItemSelectionCondition voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="06d23-124">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="06d23-125">ItemSelectionCondition-Element van ExpressionBinding voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="06d23-125">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="06d23-126">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="06d23-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
