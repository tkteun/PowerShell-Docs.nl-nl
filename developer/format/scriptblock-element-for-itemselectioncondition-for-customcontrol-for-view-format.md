---
title: ScriptBlock-Element voor ItemSelectionCondition voor CustomControl voor weergave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 946cd2b5-ac37-4a13-bb49-29fbc70ec8d7
caps.latest.revision: 6
ms.openlocfilehash: 0c07ab0e5d04c4056a7e7215bfa55773bfccb41d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851175"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="0d075-102">Het element ScriptBlock voor ItemSelectionCondition voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="0d075-102">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="0d075-103">Hiermee geeft u het script dat de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="0d075-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="0d075-104">Wanneer dit script wordt geëvalueerd naar `true`, de voorwaarde wordt voldaan, en wordt het besturingselement gebruikt.</span><span class="sxs-lookup"><span data-stu-id="0d075-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="0d075-105">Dit element wordt gebruikt bij het definiëren van een aangepast besturingselement-weergave.</span><span class="sxs-lookup"><span data-stu-id="0d075-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="0d075-106">Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) CustomControl Element (indeling) CustomEntries Element voor CustomControl voor weergave (indeling) CustomEntry Element voor CustomEntries voor weergave (indeling) CustomItem Element voor CustomEntry voor weergave (indeling) ExpressionBinding Element voor CustomItem voor CustomControl voor weergave (indeling) ItemSelectionCondition Element voor de Binding van de expressie voor CustomControl voor ScriptBlock-Element voor ItemSelectionCondition voor weergave (indeling) CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="0d075-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format) ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0d075-107">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="0d075-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0d075-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="0d075-108">Attributes and Elements</span></span>

<span data-ttu-id="0d075-109">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `ScriptBlock` element.</span><span class="sxs-lookup"><span data-stu-id="0d075-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0d075-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="0d075-110">Attributes</span></span>

<span data-ttu-id="0d075-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="0d075-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0d075-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="0d075-112">Child Elements</span></span>

<span data-ttu-id="0d075-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="0d075-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0d075-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="0d075-114">Parent Elements</span></span>

|<span data-ttu-id="0d075-115">Element</span><span class="sxs-lookup"><span data-stu-id="0d075-115">Element</span></span>|<span data-ttu-id="0d075-116">Description</span><span class="sxs-lookup"><span data-stu-id="0d075-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0d075-117">ItemSelectionCondition-Element voor de Binding van de expressie voor CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="0d075-117">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="0d075-118">Hiermee definieert u de voorwaarde die moet bestaan voor dit besturingselement moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="0d075-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="0d075-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="0d075-119">Text Value</span></span>

<span data-ttu-id="0d075-120">Geef het script dat wordt geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="0d075-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="0d075-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="0d075-121">Remarks</span></span>

<span data-ttu-id="0d075-122">Als dit element wordt gebruikt, kunt u niet opgeven de [PropertyName](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) element bij het definiëren van de selectievoorwaarde.</span><span class="sxs-lookup"><span data-stu-id="0d075-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="0d075-123">Zie ook</span><span class="sxs-lookup"><span data-stu-id="0d075-123">See Also</span></span>

[<span data-ttu-id="0d075-124">PropertyName-Element voor ItemSelectionCondition voor CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="0d075-124">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="0d075-125">ItemSelectionCondition-Element voor de Binding van de expressie voor CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="0d075-125">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="0d075-126">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="0d075-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
