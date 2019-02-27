---
title: ExpressionBinding-Element voor CustomItem voor besturingselementen voor weergave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b9da6c5-548b-480f-86ae-6de6fecabaca
caps.latest.revision: 8
ms.openlocfilehash: 06089730008839f18c471711a4b4411722f99c38
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848417"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-view-format"></a><span data-ttu-id="357dd-102">Het element ExpressionBinding voor CustomItem voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="357dd-102">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>

<span data-ttu-id="357dd-103">Definieert de gegevens die door het besturingselement wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="357dd-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="357dd-104">Dit element wordt gebruikt bij het definiëren van besturingselementen die kunnen worden gebruikt door een weergave.</span><span class="sxs-lookup"><span data-stu-id="357dd-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="357dd-105">Configuratie-Element (indeling) ViewDefinitions-Element (indeling) weergave-Element (indeling) besturingselementen Element (indeling) controle-Element voor besturingselementen voor weergave (indeling) CustomControl Element voor de controle voor besturingselementen voor weergave (indeling) CustomEntries Element voor CustomControl voor weergave (indeling) CustomEntry Element voor CustomEntries voor besturingselementen voor weergave (indeling) CustomItem Element voor CustomEntry voor besturingselementen voor weergave (indeling) ExpressionBinding Element voor CustomItem voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="357dd-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="357dd-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="357dd-106">Syntax</span></span>

```xml
<ExpressionBinding>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameofCommonCustomControl</CustomControlName>
  <EnumerateCollection/>
  <ItemSelectionCondition>...</ItemSelectionCondition>
  <PropertyName>Nameof.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate></ScriptBlock>
</ExpressionBinding>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="357dd-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="357dd-107">Attributes and Elements</span></span>

<span data-ttu-id="357dd-108">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `ExpressionBinding` element.</span><span class="sxs-lookup"><span data-stu-id="357dd-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="357dd-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="357dd-109">Attributes</span></span>

<span data-ttu-id="357dd-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="357dd-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="357dd-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="357dd-111">Child Elements</span></span>

|<span data-ttu-id="357dd-112">Element</span><span class="sxs-lookup"><span data-stu-id="357dd-112">Element</span></span>|<span data-ttu-id="357dd-113">Description</span><span class="sxs-lookup"><span data-stu-id="357dd-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="357dd-114">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="357dd-114">Optional element.</span></span><br /><br /> <span data-ttu-id="357dd-115">Hiermee definieert u een besturingselement dat wordt gebruikt door dit besturingselement.</span><span class="sxs-lookup"><span data-stu-id="357dd-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="357dd-116">CustomControlName-Element voor ExpressionBinding voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="357dd-116">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="357dd-117">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="357dd-117">Optional element.</span></span><br /><br /> <span data-ttu-id="357dd-118">Hiermee geeft u de naam van een algemene besturingselement of een besturingselement voor lijstweergave.</span><span class="sxs-lookup"><span data-stu-id="357dd-118">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="357dd-119">EnumerateCollection-Element voor ExpressionBinding voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="357dd-119">EnumerateCollection Element for ExpressionBinding for Controls for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="357dd-120">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="357dd-120">Optional element.</span></span><br /><br /> <span data-ttu-id="357dd-121">Hiermee geeft u op dat de elementen van verzamelingen worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="357dd-121">Specifies that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="357dd-122">ItemSelectionCondition-Element van ExpressionBinding voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="357dd-122">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="357dd-123">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="357dd-123">Optional element.</span></span><br /><br /> <span data-ttu-id="357dd-124">Hiermee definieert u de voorwaarde die moet bestaan voor dit besturingselement moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="357dd-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="357dd-125">PropertyName-Element voor ExpressionBinding voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="357dd-125">PropertyName Element for ExpressionBinding for Controls for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="357dd-126">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="357dd-126">Optional element.</span></span><br /><br /> <span data-ttu-id="357dd-127">Hiermee geeft u de .NET-eigenschap waarvan de waarde van het besturingselement wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="357dd-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="357dd-128">ScriptBlock-Element voor ExpressionBinding voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="357dd-128">ScriptBlock Element for ExpressionBinding for Controls for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="357dd-129">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="357dd-129">Optional element.</span></span><br /><br /> <span data-ttu-id="357dd-130">Hiermee geeft u het script waarvan de waarde van het besturingselement wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="357dd-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="357dd-131">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="357dd-131">Parent Elements</span></span>

|<span data-ttu-id="357dd-132">Element</span><span class="sxs-lookup"><span data-stu-id="357dd-132">Element</span></span>|<span data-ttu-id="357dd-133">Description</span><span class="sxs-lookup"><span data-stu-id="357dd-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="357dd-134">CustomItem-Element voor CustomEntry voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="357dd-134">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="357dd-135">Bepaalt welke gegevens worden weergegeven door het besturingselement en hoe deze wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="357dd-135">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="357dd-136">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="357dd-136">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="357dd-137">Zie ook</span><span class="sxs-lookup"><span data-stu-id="357dd-137">See Also</span></span>

[<span data-ttu-id="357dd-138">CustomItem-Element voor CustomEntry voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="357dd-138">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="357dd-139">CustomControlName-Element voor ExpressionBinding voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="357dd-139">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="357dd-140">EnumerateCollection-Element voor ExpressionBinding voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="357dd-140">EnumerateCollection Element for ExpressionBinding for Controls for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="357dd-141">ItemSelectionCondition-Element van ExpressionBinding voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="357dd-141">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="357dd-142">PropertyName-Element voor ExpressionBinding voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="357dd-142">PropertyName Element for ExpressionBinding for Controls for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="357dd-143">ScriptBlock-Element voor ExpressionBinding voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="357dd-143">ScriptBlock Element for ExpressionBinding for Controls for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="357dd-144">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="357dd-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
