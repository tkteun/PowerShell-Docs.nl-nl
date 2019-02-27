---
title: ScriptBlock-Element voor ItemSeclectionCondition voor besturingselementen voor de configuratie (-indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 51f7aec9-7b01-4370-84f4-1e58508a851f
caps.latest.revision: 6
ms.openlocfilehash: e92b2dfff07358132c480c47c34279e5365fe400
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850909"
---
# <a name="scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="19223-102">Het element ScriptBlock voor ItemSelectionCondition voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="19223-102">ScriptBlock Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="19223-103">Hiermee geeft u het script dat de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="19223-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="19223-104">Wanneer dit script wordt geëvalueerd naar `true`, de voorwaarde wordt voldaan, en wordt het besturingselement gebruikt.</span><span class="sxs-lookup"><span data-stu-id="19223-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="19223-105">Dit element wordt gebruikt bij het definiëren van een algemene besturingselement dat kan worden gebruikt door alle weergaven in de opmaak-bestand.</span><span class="sxs-lookup"><span data-stu-id="19223-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="19223-106">Configuratie-Element (indeling) besturingselementen Element van configuratie (-indeling) besturingselement Element controles voor configuratie (-indeling) CustomControl-Element voor het besturingselement voor configuratie (-indeling) CustomEntries-Element voor CustomControl voor configuratie ( -Indeling) CustomEntry Element voor CustomControl controles voor configuratie (-indeling) CustomItem-Element voor CustomEntry voor besturingselementen voor ExpressionBinding, configuratie-Element voor CustomItem voor besturingselementen voor de configuratie (-indeling) ItemSelectionCondition-Element voor ExpressionBinding controles voor configuratie (-indeling) ScriptBlock-Element voor ItemSelectionCondition voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="19223-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format) ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="19223-107">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="19223-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="19223-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="19223-108">Attributes and Elements</span></span>

<span data-ttu-id="19223-109">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `ScriptBlock` element.</span><span class="sxs-lookup"><span data-stu-id="19223-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="19223-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="19223-110">Attributes</span></span>

<span data-ttu-id="19223-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="19223-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="19223-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="19223-112">Child Elements</span></span>

<span data-ttu-id="19223-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="19223-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="19223-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="19223-114">Parent Elements</span></span>

|<span data-ttu-id="19223-115">Element</span><span class="sxs-lookup"><span data-stu-id="19223-115">Element</span></span>|<span data-ttu-id="19223-116">Description</span><span class="sxs-lookup"><span data-stu-id="19223-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="19223-117">ItemSelectionCondition-Element voor ExpressionBinding voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="19223-117">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="19223-118">Hiermee definieert u de voorwaarde die moet bestaan voor dit besturingselement moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="19223-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="19223-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="19223-119">Text Value</span></span>

<span data-ttu-id="19223-120">Geef het script dat wordt geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="19223-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="19223-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="19223-121">Remarks</span></span>

<span data-ttu-id="19223-122">Als dit element wordt gebruikt, kunt u niet opgeven de [PropertyName](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) element bij het definiëren van de selectievoorwaarde.</span><span class="sxs-lookup"><span data-stu-id="19223-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="19223-123">Zie ook</span><span class="sxs-lookup"><span data-stu-id="19223-123">See Also</span></span>

[<span data-ttu-id="19223-124">PropertyName-Element voor ItemSeclectionCondition voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="19223-124">PropertyName Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="19223-125">ItemSelectionCondition-Element voor ExpressionBinding voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="19223-125">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

[<span data-ttu-id="19223-126">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="19223-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
