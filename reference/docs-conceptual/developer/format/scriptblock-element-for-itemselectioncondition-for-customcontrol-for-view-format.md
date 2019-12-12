---
title: Script block-element voor ItemSelectionCondition voor CustomControl voor weer gave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 946cd2b5-ac37-4a13-bb49-29fbc70ec8d7
caps.latest.revision: 6
ms.openlocfilehash: 0c07ab0e5d04c4056a7e7215bfa55773bfccb41d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72353870"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="666f9-102">Het element ScriptBlock voor ItemSelectionCondition voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="666f9-102">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="666f9-103">Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="666f9-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="666f9-104">Wanneer dit script wordt geëvalueerd om `true`, wordt aan de voor waarde voldaan en wordt het besturings element gebruikt.</span><span class="sxs-lookup"><span data-stu-id="666f9-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="666f9-105">Dit element wordt gebruikt bij het definiëren van een aangepaste beheer weergave.</span><span class="sxs-lookup"><span data-stu-id="666f9-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="666f9-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) CustomControl-element (indeling) CustomEntries element voor CustomControl voor weer gave (Format) CustomEntry-element voor CustomEntries voor weer gave (Format) CustomItem element voor CustomEntry voor weer gave (Format) ExpressionBinding-element voor CustomItem voor CustomControl voor weer gave (Format) ItemSelectionCondition-element voor expressie binding voor CustomControl voor weer gave (Format) script block-element voor ItemSelectionCondition voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="666f9-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format) ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="666f9-107">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="666f9-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="666f9-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="666f9-108">Attributes and Elements</span></span>

<span data-ttu-id="666f9-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `ScriptBlock` beschreven.</span><span class="sxs-lookup"><span data-stu-id="666f9-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="666f9-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="666f9-110">Attributes</span></span>

<span data-ttu-id="666f9-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="666f9-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="666f9-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="666f9-112">Child Elements</span></span>

<span data-ttu-id="666f9-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="666f9-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="666f9-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="666f9-114">Parent Elements</span></span>

|<span data-ttu-id="666f9-115">Element</span><span class="sxs-lookup"><span data-stu-id="666f9-115">Element</span></span>|<span data-ttu-id="666f9-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="666f9-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="666f9-117">ItemSelectionCondition-element voor expressie binding voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="666f9-117">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="666f9-118">Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit besturings element.</span><span class="sxs-lookup"><span data-stu-id="666f9-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="666f9-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="666f9-119">Text Value</span></span>

<span data-ttu-id="666f9-120">Geef het script op dat wordt geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="666f9-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="666f9-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="666f9-121">Remarks</span></span>

<span data-ttu-id="666f9-122">Als dit element wordt gebruikt, kunt u het kenmerk [PropertyName](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) niet opgeven bij het definiëren van de selectie voorwaarde.</span><span class="sxs-lookup"><span data-stu-id="666f9-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="666f9-123">Zie ook</span><span class="sxs-lookup"><span data-stu-id="666f9-123">See Also</span></span>

[<span data-ttu-id="666f9-124">Het element PropertyName voor ItemSelectionCondition voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="666f9-124">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="666f9-125">ItemSelectionCondition-element voor expressie binding voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="666f9-125">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="666f9-126">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="666f9-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
