---
title: ScriptBlock-Element voor ItemSelectionCondition voor besturingselementen voor weergave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b4191157-bf01-4831-b221-6f8cc581cd53
caps.latest.revision: 6
ms.openlocfilehash: 0cbefbb48427b56d4ae2a5ae27c7726dcfad7b84
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064710"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-controls-for-view-format"></a><span data-ttu-id="ecff4-102">Het element ScriptBlock voor ItemSelectionCondition voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="ecff4-102">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="ecff4-103">Hiermee geeft u het script dat de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="ecff4-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="ecff4-104">Wanneer dit script wordt geëvalueerd naar `true`, de voorwaarde wordt voldaan, en wordt het besturingselement gebruikt.</span><span class="sxs-lookup"><span data-stu-id="ecff4-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="ecff4-105">Dit element wordt gebruikt bij het definiëren van besturingselementen die kunnen worden gebruikt door een weergave.</span><span class="sxs-lookup"><span data-stu-id="ecff4-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="ecff4-106">Configuratie-Element (indeling) ViewDefinitions-Element (indeling) weergave-Element (indeling) besturingselementen Element (indeling) controle-Element voor besturingselementen voor weergave (indeling) CustomControl Element voor de controle voor besturingselementen voor weergave (indeling) CustomEntries Element voor CustomControl voor weergave (indeling) CustomEntry Element voor CustomEntries voor besturingselementen voor weergave (indeling) CustomItem Element voor CustomEntry voor besturingselementen voor weergave (indeling) ExpressionBinding Element voor CustomItem voor besturingselementen voor weergave (indeling) ItemSelectionCondition-Element van ExpressionBinding voor besturingselementen voor weergave (indeling) ScriptBlock Element voor ItemSelectionCondition voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="ecff4-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format) ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ecff4-107">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="ecff4-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ecff4-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="ecff4-108">Attributes and Elements</span></span>

<span data-ttu-id="ecff4-109">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `ScriptBlock` element.</span><span class="sxs-lookup"><span data-stu-id="ecff4-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ecff4-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="ecff4-110">Attributes</span></span>

<span data-ttu-id="ecff4-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="ecff4-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ecff4-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="ecff4-112">Child Elements</span></span>

<span data-ttu-id="ecff4-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="ecff4-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ecff4-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="ecff4-114">Parent Elements</span></span>

|<span data-ttu-id="ecff4-115">Element</span><span class="sxs-lookup"><span data-stu-id="ecff4-115">Element</span></span>|<span data-ttu-id="ecff4-116">Description</span><span class="sxs-lookup"><span data-stu-id="ecff4-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ecff4-117">ItemSelectionCondition-Element van ExpressionBinding voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="ecff4-117">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="ecff4-118">Hiermee definieert u de voorwaarde die moet bestaan voor dit besturingselement moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="ecff4-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ecff4-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="ecff4-119">Text Value</span></span>

<span data-ttu-id="ecff4-120">Geef het script dat wordt geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="ecff4-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="ecff4-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="ecff4-121">Remarks</span></span>

<span data-ttu-id="ecff4-122">Als dit element wordt gebruikt, kunt u niet opgeven de [PropertyName](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md) element bij het definiëren van de selectievoorwaarde.</span><span class="sxs-lookup"><span data-stu-id="ecff4-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="ecff4-123">Zie ook</span><span class="sxs-lookup"><span data-stu-id="ecff4-123">See Also</span></span>

[<span data-ttu-id="ecff4-124">PropertyName-Element voor ItemSelectionCondition voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="ecff4-124">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="ecff4-125">ItemSelectionCondition-Element van ExpressionBinding voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="ecff4-125">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="ecff4-126">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="ecff4-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
