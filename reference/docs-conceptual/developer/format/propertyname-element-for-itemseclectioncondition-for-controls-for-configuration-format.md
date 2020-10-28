---
ms.date: 09/13/2016
ms.topic: reference
title: Het element PropertyName voor ItemSelectionCondition voor Besturingselementen voor Configuratie (opmaak)
description: Het element PropertyName voor ItemSelectionCondition voor Besturingselementen voor Configuratie (opmaak)
ms.openlocfilehash: 860683eb54b2a3579767640c1d3f0937897b8f8e
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92655125"
---
# <a name="propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="b2221-103">Het element PropertyName voor ItemSelectionCondition voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="b2221-103">PropertyName Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="b2221-104">Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="b2221-104">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="b2221-105">Wanneer deze eigenschap aanwezig is of wanneer deze wordt geëvalueerd `true` , wordt voldaan aan de voor waarde en wordt het besturings element gebruikt.</span><span class="sxs-lookup"><span data-stu-id="b2221-105">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="b2221-106">Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="b2221-106">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="b2221-107">Configuratie-element (Format) Controls element van configuratie (indeling) Control element voor besturings elementen voor configuratie (indeling) CustomControl-element voor besturings element voor configuratie (indeling) CustomEntries element voor het object CustomControl voor configuratie (indeling) CustomEntry (Format) CustomItem-element voor CustomEntry voor besturings elementen voor de configuratie ExpressionBinding-element voor CustomItem voor besturings elementen voor configuratie (indeling) ItemSelectionCondition-element voor ExpressionBinding voor besturings elementen voor de configuratie (Format) eigenschap naam voor ItemSeclectionCondition voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="b2221-107">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format) PropertyName Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b2221-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="b2221-108">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b2221-109">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="b2221-109">Attributes and Elements</span></span>

<span data-ttu-id="b2221-110">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `PropertyName` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="b2221-110">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b2221-111">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="b2221-111">Attributes</span></span>

<span data-ttu-id="b2221-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="b2221-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b2221-113">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="b2221-113">Child Elements</span></span>

<span data-ttu-id="b2221-114">Geen.</span><span class="sxs-lookup"><span data-stu-id="b2221-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b2221-115">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="b2221-115">Parent Elements</span></span>

|<span data-ttu-id="b2221-116">Element</span><span class="sxs-lookup"><span data-stu-id="b2221-116">Element</span></span>|<span data-ttu-id="b2221-117">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="b2221-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b2221-118">Het element ItemSelectionCondition voor ExpressionBinding voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="b2221-118">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="b2221-119">Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit besturings element.</span><span class="sxs-lookup"><span data-stu-id="b2221-119">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b2221-120">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="b2221-120">Text Value</span></span>

<span data-ttu-id="b2221-121">Geef de naam op van de .NET-eigenschap waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="b2221-121">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="b2221-122">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="b2221-122">Remarks</span></span>

<span data-ttu-id="b2221-123">Als dit element wordt gebruikt, kunt u het [script Block](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) -element niet opgeven wanneer u de selectie voorwaarde definieert.</span><span class="sxs-lookup"><span data-stu-id="b2221-123">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="b2221-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="b2221-124">See Also</span></span>

[<span data-ttu-id="b2221-125">Het element ScriptBlock voor ItemSelectionCondition voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="b2221-125">ScriptBlock Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="b2221-126">Het element ItemSelectionCondition voor ExpressionBinding voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="b2221-126">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

[<span data-ttu-id="b2221-127">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="b2221-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
