---
title: Het element PropertyName voor ItemSelectionCondition voor besturings elementen voor weer gave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ba3955bc-f3a1-4ef6-86ac-80ffc133ad1b
caps.latest.revision: 6
ms.openlocfilehash: 28ad31be4be7be20f1f43ea1b69ad5d294de86f6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72354157"
---
# <a name="propertyname-element-for-itemselectioncondition-for-controls-for-view-format"></a><span data-ttu-id="353cc-102">Het element PropertyName voor ItemSelectionCondition voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="353cc-102">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="353cc-103">Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="353cc-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="353cc-104">Wanneer deze eigenschap aanwezig is of wordt geëvalueerd als `true`, wordt aan de voor waarde voldaan en wordt het besturings element gebruikt.</span><span class="sxs-lookup"><span data-stu-id="353cc-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="353cc-105">Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.</span><span class="sxs-lookup"><span data-stu-id="353cc-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="353cc-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) Controls-element (Format) Control element (opmaak) voor besturings elementen voor de weer gave (indeling) CustomControl-element voor besturings elementen voor Controls (Format) CustomEntries element voor CustomControl voor View (Format) CustomEntry-element voor CustomEntries voor besturings elementen voor weer gave (Format) CustomItem-element voor CustomEntry voor besturings elementen voor de weer gave (Format) ExpressionBinding-element voor CustomItem voor besturings elementen voor weer gave (indeling) ItemSelectionCondition-element van ExpressionBinding voor besturings elementen voor de eigenschap element van de weer gave (Format) voor ItemSelectionCondition voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="353cc-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format) PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="353cc-107">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="353cc-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="353cc-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="353cc-108">Attributes and Elements</span></span>

<span data-ttu-id="353cc-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `PropertyName` beschreven.</span><span class="sxs-lookup"><span data-stu-id="353cc-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="353cc-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="353cc-110">Attributes</span></span>

<span data-ttu-id="353cc-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="353cc-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="353cc-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="353cc-112">Child Elements</span></span>

<span data-ttu-id="353cc-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="353cc-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="353cc-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="353cc-114">Parent Elements</span></span>

|<span data-ttu-id="353cc-115">Element</span><span class="sxs-lookup"><span data-stu-id="353cc-115">Element</span></span>|<span data-ttu-id="353cc-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="353cc-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="353cc-117">ItemSelectionCondition-element van ExpressionBinding voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="353cc-117">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="353cc-118">Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit besturings element.</span><span class="sxs-lookup"><span data-stu-id="353cc-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="353cc-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="353cc-119">Text Value</span></span>

<span data-ttu-id="353cc-120">Geef de naam op van de .NET-eigenschap waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="353cc-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="353cc-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="353cc-121">Remarks</span></span>

<span data-ttu-id="353cc-122">Als dit element wordt gebruikt, kunt u het [script Block](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md) -element niet opgeven wanneer u de selectie voorwaarde definieert.</span><span class="sxs-lookup"><span data-stu-id="353cc-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="353cc-123">Zie ook</span><span class="sxs-lookup"><span data-stu-id="353cc-123">See Also</span></span>

[<span data-ttu-id="353cc-124">Script block-element voor ItemSelectionCondition voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="353cc-124">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="353cc-125">ItemSelectionCondition-element van ExpressionBinding voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="353cc-125">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="353cc-126">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="353cc-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
