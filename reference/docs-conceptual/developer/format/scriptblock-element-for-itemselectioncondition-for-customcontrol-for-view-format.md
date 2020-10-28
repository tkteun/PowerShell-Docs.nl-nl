---
ms.date: 09/13/2016
ms.topic: reference
title: Het element ScriptBlock voor ItemSelectionCondition voor CustomControl voor Weergave (opmaak)
description: Het element ScriptBlock voor ItemSelectionCondition voor CustomControl voor Weergave (opmaak)
ms.openlocfilehash: d762f400f5bb52af314093079fe94223c56d3f31
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92665129"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="5a56d-103">Het element ScriptBlock voor ItemSelectionCondition voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="5a56d-103">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="5a56d-104">Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="5a56d-104">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="5a56d-105">Wanneer dit script wordt geëvalueerd `true` , wordt voldaan aan de voor waarde en wordt het besturings element gebruikt.</span><span class="sxs-lookup"><span data-stu-id="5a56d-105">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="5a56d-106">Dit element wordt gebruikt bij het definiëren van een aangepaste beheer weergave.</span><span class="sxs-lookup"><span data-stu-id="5a56d-106">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="5a56d-107">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) CustomControl-element (indeling) CustomEntries element voor CustomControl voor weer gave (Format) CustomEntry-element voor CustomEntries voor weer gave (Format) CustomItem element voor CustomEntry voor weer gave (Format) ExpressionBinding-element voor CustomItem voor CustomControl voor weer gave (Format) ItemSelectionCondition-element voor expressie binding voor CustomControl voor weer gave (Format) script block element voor ItemSelectionCondition voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="5a56d-107">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format) ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5a56d-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="5a56d-108">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5a56d-109">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="5a56d-109">Attributes and Elements</span></span>

<span data-ttu-id="5a56d-110">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `ScriptBlock` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="5a56d-110">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5a56d-111">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="5a56d-111">Attributes</span></span>

<span data-ttu-id="5a56d-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="5a56d-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5a56d-113">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="5a56d-113">Child Elements</span></span>

<span data-ttu-id="5a56d-114">Geen.</span><span class="sxs-lookup"><span data-stu-id="5a56d-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5a56d-115">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="5a56d-115">Parent Elements</span></span>

|<span data-ttu-id="5a56d-116">Element</span><span class="sxs-lookup"><span data-stu-id="5a56d-116">Element</span></span>|<span data-ttu-id="5a56d-117">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="5a56d-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5a56d-118">ItemSelectionCondition-element voor expressie binding voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="5a56d-118">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="5a56d-119">Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit besturings element.</span><span class="sxs-lookup"><span data-stu-id="5a56d-119">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="5a56d-120">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="5a56d-120">Text Value</span></span>

<span data-ttu-id="5a56d-121">Geef het script op dat wordt geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="5a56d-121">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="5a56d-122">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="5a56d-122">Remarks</span></span>

<span data-ttu-id="5a56d-123">Als dit element wordt gebruikt, kunt u het kenmerk [PropertyName](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) niet opgeven bij het definiëren van de selectie voorwaarde.</span><span class="sxs-lookup"><span data-stu-id="5a56d-123">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="5a56d-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="5a56d-124">See Also</span></span>

[<span data-ttu-id="5a56d-125">Het element PropertyName voor ItemSelectionCondition voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="5a56d-125">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="5a56d-126">ItemSelectionCondition-element voor expressie binding voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="5a56d-126">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="5a56d-127">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="5a56d-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
