---
ms.date: 09/13/2016
ms.topic: reference
title: Het element ScriptBlock voor ItemSelectionCondition voor Besturingselementen voor Configuratie (opmaak)
description: Het element ScriptBlock voor ItemSelectionCondition voor Besturingselementen voor Configuratie (opmaak)
ms.openlocfilehash: 853130da4489e571d7f4026a8d65d029d1889f9b
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665234"
---
# <a name="scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="57401-103">Het element ScriptBlock voor ItemSelectionCondition voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="57401-103">ScriptBlock Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="57401-104">Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="57401-104">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="57401-105">Wanneer dit script wordt geëvalueerd `true` , wordt voldaan aan de voor waarde en wordt het besturings element gebruikt.</span><span class="sxs-lookup"><span data-stu-id="57401-105">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="57401-106">Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="57401-106">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="57401-107">Configuratie-element (Format) Controls element van configuratie (indeling) Control element voor besturings elementen voor configuratie (indeling) CustomControl-element voor besturings element voor configuratie (indeling) CustomEntries element voor het object CustomControl voor configuratie (indeling) CustomEntry configuratie (Format) CustomItem-element voor CustomEntry voor besturings elementen voor configuratie ExpressionBinding-element voor CustomItem voor besturings elementen voor configuratie (indeling) ItemSelectionCondition element voor ExpressionBinding voor besturings elementen voor configuratie (indeling) script block element voor ItemSelectionCondition voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="57401-107">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format) ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="57401-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="57401-108">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="57401-109">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="57401-109">Attributes and Elements</span></span>

<span data-ttu-id="57401-110">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `ScriptBlock` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="57401-110">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="57401-111">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="57401-111">Attributes</span></span>

<span data-ttu-id="57401-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="57401-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="57401-113">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="57401-113">Child Elements</span></span>

<span data-ttu-id="57401-114">Geen.</span><span class="sxs-lookup"><span data-stu-id="57401-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="57401-115">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="57401-115">Parent Elements</span></span>

|<span data-ttu-id="57401-116">Element</span><span class="sxs-lookup"><span data-stu-id="57401-116">Element</span></span>|<span data-ttu-id="57401-117">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="57401-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="57401-118">Het element ItemSelectionCondition voor ExpressionBinding voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="57401-118">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="57401-119">Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit besturings element.</span><span class="sxs-lookup"><span data-stu-id="57401-119">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="57401-120">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="57401-120">Text Value</span></span>

<span data-ttu-id="57401-121">Geef het script op dat wordt geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="57401-121">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="57401-122">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="57401-122">Remarks</span></span>

<span data-ttu-id="57401-123">Als dit element wordt gebruikt, kunt u het kenmerk [PropertyName](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) niet opgeven bij het definiëren van de selectie voorwaarde.</span><span class="sxs-lookup"><span data-stu-id="57401-123">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="57401-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="57401-124">See Also</span></span>

[<span data-ttu-id="57401-125">Het element PropertyName voor ItemSelectionCondition voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="57401-125">PropertyName Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="57401-126">Het element ItemSelectionCondition voor ExpressionBinding voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="57401-126">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

[<span data-ttu-id="57401-127">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="57401-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
