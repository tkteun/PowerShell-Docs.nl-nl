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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064472"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="49226-102">Het element ScriptBlock voor ItemSelectionCondition voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="49226-102">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="49226-103">Hiermee geeft u het script dat de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="49226-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="49226-104">Wanneer dit script wordt geëvalueerd naar `true`, de voorwaarde wordt voldaan, en wordt het besturingselement gebruikt.</span><span class="sxs-lookup"><span data-stu-id="49226-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="49226-105">Dit element wordt gebruikt bij het definiëren van een aangepast besturingselement-weergave.</span><span class="sxs-lookup"><span data-stu-id="49226-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="49226-106">Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) CustomControl Element (indeling) CustomEntries Element voor CustomControl voor weergave (indeling) CustomEntry Element voor CustomEntries voor weergave (indeling) CustomItem Element voor CustomEntry voor weergave (indeling) ExpressionBinding Element voor CustomItem voor CustomControl voor weergave (indeling) ItemSelectionCondition Element voor de Binding van de expressie voor CustomControl voor ScriptBlock-Element voor ItemSelectionCondition voor weergave (indeling) CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="49226-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format) ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="49226-107">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="49226-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="49226-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="49226-108">Attributes and Elements</span></span>

<span data-ttu-id="49226-109">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `ScriptBlock` element.</span><span class="sxs-lookup"><span data-stu-id="49226-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="49226-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="49226-110">Attributes</span></span>

<span data-ttu-id="49226-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="49226-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="49226-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="49226-112">Child Elements</span></span>

<span data-ttu-id="49226-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="49226-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="49226-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="49226-114">Parent Elements</span></span>

|<span data-ttu-id="49226-115">Element</span><span class="sxs-lookup"><span data-stu-id="49226-115">Element</span></span>|<span data-ttu-id="49226-116">Description</span><span class="sxs-lookup"><span data-stu-id="49226-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="49226-117">ItemSelectionCondition-Element voor de Binding van de expressie voor CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="49226-117">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="49226-118">Hiermee definieert u de voorwaarde die moet bestaan voor dit besturingselement moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="49226-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="49226-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="49226-119">Text Value</span></span>

<span data-ttu-id="49226-120">Geef het script dat wordt geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="49226-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="49226-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="49226-121">Remarks</span></span>

<span data-ttu-id="49226-122">Als dit element wordt gebruikt, kunt u niet opgeven de [PropertyName](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) element bij het definiëren van de selectievoorwaarde.</span><span class="sxs-lookup"><span data-stu-id="49226-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="49226-123">Zie ook</span><span class="sxs-lookup"><span data-stu-id="49226-123">See Also</span></span>

[<span data-ttu-id="49226-124">PropertyName-Element voor ItemSelectionCondition voor CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="49226-124">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="49226-125">ItemSelectionCondition-Element voor de Binding van de expressie voor CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="49226-125">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="49226-126">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="49226-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
