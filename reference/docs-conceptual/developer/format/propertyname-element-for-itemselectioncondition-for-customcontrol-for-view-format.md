---
title: Het element PropertyName voor ItemSelectionCondition voor CustomControl voor weer gave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2b12006-8d52-486b-91a3-e6224ca80e56
caps.latest.revision: 6
ms.openlocfilehash: 52d0b0816eaef6752220e0c3b1249e5a0e44a3ee
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72354129"
---
# <a name="propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="d8a09-102">Het element PropertyName voor ItemSelectionCondition voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="d8a09-102">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="d8a09-103">Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="d8a09-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="d8a09-104">Wanneer deze eigenschap aanwezig is of wordt geëvalueerd als `true`, wordt aan de voor waarde voldaan en wordt het besturings element gebruikt.</span><span class="sxs-lookup"><span data-stu-id="d8a09-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="d8a09-105">Dit element wordt gebruikt bij het definiëren van een aangepaste beheer weergave.</span><span class="sxs-lookup"><span data-stu-id="d8a09-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="d8a09-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) CustomControl-element (indeling) CustomEntries element voor CustomControl voor weer gave (Format) CustomEntry-element voor CustomEntries voor weer gave (Format) CustomItem element voor CustomEntry voor weer gave (Format) ExpressionBinding-element voor CustomItem voor CustomControl voor weer gave (indeling) ItemSelectionCondition element voor expressie binding voor een CustomControl-element voor de eigenschap voor weer gave (Format) voor ItemSelectionCondition voor CustomControl voor weer gave (notatie</span><span class="sxs-lookup"><span data-stu-id="d8a09-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format) PropertyName Element for ItemSelectionCondition for CustomControl for View (Format</span></span>

## <a name="syntax"></a><span data-ttu-id="d8a09-107">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="d8a09-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d8a09-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="d8a09-108">Attributes and Elements</span></span>

<span data-ttu-id="d8a09-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `PropertyName` beschreven.</span><span class="sxs-lookup"><span data-stu-id="d8a09-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d8a09-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="d8a09-110">Attributes</span></span>

<span data-ttu-id="d8a09-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="d8a09-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d8a09-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="d8a09-112">Child Elements</span></span>

<span data-ttu-id="d8a09-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="d8a09-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d8a09-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="d8a09-114">Parent Elements</span></span>

|<span data-ttu-id="d8a09-115">Element</span><span class="sxs-lookup"><span data-stu-id="d8a09-115">Element</span></span>|<span data-ttu-id="d8a09-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="d8a09-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d8a09-117">ItemSelectionCondition-element voor expressie binding voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="d8a09-117">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="d8a09-118">Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit besturings element.</span><span class="sxs-lookup"><span data-stu-id="d8a09-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d8a09-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="d8a09-119">Text Value</span></span>

<span data-ttu-id="d8a09-120">Geef de naam op van de .NET-eigenschap waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="d8a09-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="d8a09-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="d8a09-121">Remarks</span></span>

<span data-ttu-id="d8a09-122">Als dit element wordt gebruikt, kunt u het [script Block](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) -element niet opgeven wanneer u de selectie voorwaarde definieert.</span><span class="sxs-lookup"><span data-stu-id="d8a09-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="d8a09-123">Zie ook</span><span class="sxs-lookup"><span data-stu-id="d8a09-123">See Also</span></span>

[<span data-ttu-id="d8a09-124">Script block-element voor ItemSelectionCondition voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="d8a09-124">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="d8a09-125">ItemSelectionCondition-element voor expressie binding voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="d8a09-125">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="d8a09-126">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="d8a09-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
