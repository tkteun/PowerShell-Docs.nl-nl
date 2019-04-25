---
title: PropertyName-Element voor ItemSelectionCondition voor CustomControl voor weergave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2b12006-8d52-486b-91a3-e6224ca80e56
caps.latest.revision: 6
ms.openlocfilehash: 52d0b0816eaef6752220e0c3b1249e5a0e44a3ee
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064863"
---
# <a name="propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="de5b9-102">Het element PropertyName voor ItemSelectionCondition voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="de5b9-102">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="de5b9-103">Hiermee geeft u de .NET-eigenschap die de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="de5b9-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="de5b9-104">Als deze eigenschap is aanwezig, of wanneer deze wordt geëvalueerd naar `true`, de voorwaarde wordt voldaan, en wordt het besturingselement gebruikt.</span><span class="sxs-lookup"><span data-stu-id="de5b9-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="de5b9-105">Dit element wordt gebruikt bij het definiëren van een aangepast besturingselement-weergave.</span><span class="sxs-lookup"><span data-stu-id="de5b9-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="de5b9-106">Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) CustomControl Element (indeling) CustomEntries Element voor CustomControl voor weergave (indeling) CustomEntry Element voor CustomEntries voor weergave (indeling) CustomItem Element voor CustomEntry voor weergave (indeling) ExpressionBinding Element voor CustomItem voor CustomControl voor weergave (indeling) ItemSelectionCondition Element voor de Binding van de expressie voor CustomControl voor PropertyName-Element voor ItemSelectionCondition voor weergave (indeling) CustomControl voor weergave (indeling</span><span class="sxs-lookup"><span data-stu-id="de5b9-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format) PropertyName Element for ItemSelectionCondition for CustomControl for View (Format</span></span>

## <a name="syntax"></a><span data-ttu-id="de5b9-107">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="de5b9-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="de5b9-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="de5b9-108">Attributes and Elements</span></span>

<span data-ttu-id="de5b9-109">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `PropertyName` element.</span><span class="sxs-lookup"><span data-stu-id="de5b9-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="de5b9-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="de5b9-110">Attributes</span></span>

<span data-ttu-id="de5b9-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="de5b9-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="de5b9-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="de5b9-112">Child Elements</span></span>

<span data-ttu-id="de5b9-113">Geen.</span><span class="sxs-lookup"><span data-stu-id="de5b9-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="de5b9-114">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="de5b9-114">Parent Elements</span></span>

|<span data-ttu-id="de5b9-115">Element</span><span class="sxs-lookup"><span data-stu-id="de5b9-115">Element</span></span>|<span data-ttu-id="de5b9-116">Description</span><span class="sxs-lookup"><span data-stu-id="de5b9-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="de5b9-117">ItemSelectionCondition-Element voor de Binding van de expressie voor CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="de5b9-117">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="de5b9-118">Hiermee definieert u de voorwaarde die moet bestaan voor dit besturingselement moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="de5b9-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="de5b9-119">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="de5b9-119">Text Value</span></span>

<span data-ttu-id="de5b9-120">Geef de naam van de .NET-eigenschap die de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="de5b9-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="de5b9-121">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="de5b9-121">Remarks</span></span>

<span data-ttu-id="de5b9-122">Als dit element wordt gebruikt, kunt u niet opgeven de [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) element bij het definiëren van de selectievoorwaarde.</span><span class="sxs-lookup"><span data-stu-id="de5b9-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="de5b9-123">Zie ook</span><span class="sxs-lookup"><span data-stu-id="de5b9-123">See Also</span></span>

[<span data-ttu-id="de5b9-124">ScriptBlock-Element voor ItemSelectionCondition voor CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="de5b9-124">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="de5b9-125">ItemSelectionCondition-Element voor de Binding van de expressie voor CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="de5b9-125">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="de5b9-126">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="de5b9-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
