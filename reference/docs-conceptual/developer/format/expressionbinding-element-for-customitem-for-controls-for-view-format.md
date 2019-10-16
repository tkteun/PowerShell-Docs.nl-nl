---
title: ExpressionBinding-element voor CustomItem voor besturings elementen voor weer gave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b9da6c5-548b-480f-86ae-6de6fecabaca
caps.latest.revision: 8
ms.openlocfilehash: 06089730008839f18c471711a4b4411722f99c38
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355067"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-view-format"></a><span data-ttu-id="d6e1c-102">Het element ExpressionBinding voor CustomItem voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="d6e1c-102">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>

<span data-ttu-id="d6e1c-103">Hiermee worden de gegevens gedefinieerd die door het besturings element worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="d6e1c-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="d6e1c-104">Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.</span><span class="sxs-lookup"><span data-stu-id="d6e1c-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="d6e1c-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) Controls-element (Format) Control element (opmaak) voor besturings elementen voor de weer gave (indeling) CustomControl-element voor besturings elementen voor Controls (Format) CustomEntries element voor CustomControl voor View (Format) CustomEntry-element voor CustomEntries voor besturings elementen voor weer gave (Format) CustomItem-element voor CustomEntry voor besturings elementen voor de weer gave (Format) ExpressionBinding-element voor CustomItem voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="d6e1c-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d6e1c-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="d6e1c-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="d6e1c-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="d6e1c-107">Attributes and Elements</span></span>

<span data-ttu-id="d6e1c-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `ExpressionBinding` beschreven.</span><span class="sxs-lookup"><span data-stu-id="d6e1c-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d6e1c-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="d6e1c-109">Attributes</span></span>

<span data-ttu-id="d6e1c-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="d6e1c-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d6e1c-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="d6e1c-111">Child Elements</span></span>

|<span data-ttu-id="d6e1c-112">Element</span><span class="sxs-lookup"><span data-stu-id="d6e1c-112">Element</span></span>|<span data-ttu-id="d6e1c-113">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="d6e1c-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="d6e1c-114">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="d6e1c-114">Optional element.</span></span><br /><br /> <span data-ttu-id="d6e1c-115">Hiermee wordt een besturings element gedefinieerd dat door dit besturings element wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="d6e1c-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="d6e1c-116">CustomControlName-element voor ExpressionBinding voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="d6e1c-116">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="d6e1c-117">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="d6e1c-117">Optional element.</span></span><br /><br /> <span data-ttu-id="d6e1c-118">Hiermee geeft u de naam op van een algemeen besturings element of een weergave besturings element.</span><span class="sxs-lookup"><span data-stu-id="d6e1c-118">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="d6e1c-119">EnumerateCollection-element voor ExpressionBinding voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="d6e1c-119">EnumerateCollection Element for ExpressionBinding for Controls for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="d6e1c-120">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="d6e1c-120">Optional element.</span></span><br /><br /> <span data-ttu-id="d6e1c-121">Hiermee geeft u op dat de elementen van verzamelingen worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="d6e1c-121">Specifies that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="d6e1c-122">ItemSelectionCondition-element van ExpressionBinding voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="d6e1c-122">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="d6e1c-123">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="d6e1c-123">Optional element.</span></span><br /><br /> <span data-ttu-id="d6e1c-124">Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit besturings element.</span><span class="sxs-lookup"><span data-stu-id="d6e1c-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="d6e1c-125">Het element PropertyName voor ExpressionBinding voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="d6e1c-125">PropertyName Element for ExpressionBinding for Controls for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="d6e1c-126">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="d6e1c-126">Optional element.</span></span><br /><br /> <span data-ttu-id="d6e1c-127">Hiermee geeft u de .NET-eigenschap op waarvan de waarde wordt weer gegeven door het besturings element.</span><span class="sxs-lookup"><span data-stu-id="d6e1c-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="d6e1c-128">Script block-element voor ExpressionBinding voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="d6e1c-128">ScriptBlock Element for ExpressionBinding for Controls for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="d6e1c-129">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="d6e1c-129">Optional element.</span></span><br /><br /> <span data-ttu-id="d6e1c-130">Hiermee geeft u het script op waarvan de waarde wordt weer gegeven door het besturings element.</span><span class="sxs-lookup"><span data-stu-id="d6e1c-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d6e1c-131">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="d6e1c-131">Parent Elements</span></span>

|<span data-ttu-id="d6e1c-132">Element</span><span class="sxs-lookup"><span data-stu-id="d6e1c-132">Element</span></span>|<span data-ttu-id="d6e1c-133">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="d6e1c-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d6e1c-134">CustomItem-element voor CustomEntry voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="d6e1c-134">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="d6e1c-135">Hiermee definieert u welke gegevens worden weer gegeven door het besturings element en hoe deze worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="d6e1c-135">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d6e1c-136">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="d6e1c-136">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="d6e1c-137">Zie ook</span><span class="sxs-lookup"><span data-stu-id="d6e1c-137">See Also</span></span>

[<span data-ttu-id="d6e1c-138">CustomItem-element voor CustomEntry voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="d6e1c-138">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="d6e1c-139">CustomControlName-element voor ExpressionBinding voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="d6e1c-139">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="d6e1c-140">EnumerateCollection-element voor ExpressionBinding voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="d6e1c-140">EnumerateCollection Element for ExpressionBinding for Controls for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="d6e1c-141">ItemSelectionCondition-element van ExpressionBinding voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="d6e1c-141">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="d6e1c-142">Het element PropertyName voor ExpressionBinding voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="d6e1c-142">PropertyName Element for ExpressionBinding for Controls for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="d6e1c-143">Script block-element voor ExpressionBinding voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="d6e1c-143">ScriptBlock Element for ExpressionBinding for Controls for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="d6e1c-144">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="d6e1c-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
