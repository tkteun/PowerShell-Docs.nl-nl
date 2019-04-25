---
title: PropertyName-Element voor ItemSeclectionCondition voor besturingselementen voor de configuratie (-indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ad8ab181-c559-492e-a0cf-299e381fdcc3
caps.latest.revision: 6
ms.openlocfilehash: ce25789bdfc2679372ca9e42f99dcc6a30ae2def
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064888"
---
# <a name="propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="969e6-102">Het element PropertyName voor ItemSelectionCondition voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="969e6-102">PropertyName Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="969e6-103">Hiermee geeft u de .NET-eigenschap die de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="969e6-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="969e6-104">Als deze eigenschap is aanwezig, of wanneer deze wordt geëvalueerd naar `true`, de voorwaarde wordt voldaan, en wordt het besturingselement gebruikt.</span><span class="sxs-lookup"><span data-stu-id="969e6-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="969e6-105">Dit element wordt gebruikt bij het definiëren van een algemene besturingselement dat kan worden gebruikt door alle weergaven in de opmaak-bestand.</span><span class="sxs-lookup"><span data-stu-id="969e6-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="969e6-106">Configuratie-Element (indeling) besturingselementen Element van configuratie (-indeling) besturingselement Element controles voor configuratie (-indeling) CustomControl-Element voor het besturingselement voor configuratie (-indeling) CustomEntries-Element voor CustomControl voor configuratie ( -Indeling) CustomEntry Element voor CustomControl controles voor configuratie (-indeling) CustomItem-Element voor CustomEntry voor besturingselementen voor ExpressionBinding, configuratie-Element voor CustomItem voor besturingselementen voor de configuratie (-indeling) ItemSelectionCondition-Element voor ExpressionBinding controles voor configuratie (-indeling) PropertyName-Element voor ItemSeclectionCondition voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="969e6-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format) PropertyName Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="969e6-107">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="969e6-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="969e6-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="969e6-108">Attributes and Elements</span></span>

<span data-ttu-id="969e6-109">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `PropertyName` element.</span><span class="sxs-lookup"><span data-stu-id="969e6-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="969e6-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="969e6-110">Attributes</span></span>

<span data-ttu-id="969e6-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="969e6-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="969e6-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="969e6-112">Child Elements</span></span>

<span data-ttu-id="969e6-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="969e6-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="969e6-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="969e6-114">Parent Elements</span></span>

|<span data-ttu-id="969e6-115">Element</span><span class="sxs-lookup"><span data-stu-id="969e6-115">Element</span></span>|<span data-ttu-id="969e6-116">Description</span><span class="sxs-lookup"><span data-stu-id="969e6-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="969e6-117">ItemSelectionCondition-Element voor ExpressionBinding voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="969e6-117">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="969e6-118">Hiermee definieert u de voorwaarde die moet bestaan voor dit besturingselement moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="969e6-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="969e6-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="969e6-119">Text Value</span></span>

<span data-ttu-id="969e6-120">Geef de naam van de .NET-eigenschap die de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="969e6-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="969e6-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="969e6-121">Remarks</span></span>

<span data-ttu-id="969e6-122">Als dit element wordt gebruikt, kunt u niet opgeven de [ScriptBlock](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) element bij het definiëren van de selectievoorwaarde.</span><span class="sxs-lookup"><span data-stu-id="969e6-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="969e6-123">Zie ook</span><span class="sxs-lookup"><span data-stu-id="969e6-123">See Also</span></span>

[<span data-ttu-id="969e6-124">ScriptBlock-Element voor ItemSeclectionCondition voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="969e6-124">ScriptBlock Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="969e6-125">ItemSelectionCondition-Element voor ExpressionBinding voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="969e6-125">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

[<span data-ttu-id="969e6-126">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="969e6-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
