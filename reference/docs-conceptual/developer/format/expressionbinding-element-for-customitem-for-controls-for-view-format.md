---
ms.date: 09/13/2016
ms.topic: reference
title: Het element ExpressionBinding voor CustomItem voor Besturingselementen voor Weergave (opmaak)
description: Het element ExpressionBinding voor CustomItem voor Besturingselementen voor Weergave (opmaak)
ms.openlocfilehash: da87bb26d21dcb051871e67997cc3fba7ce73c74
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92649886"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-view-format"></a><span data-ttu-id="7bdf0-103">Het element ExpressionBinding voor CustomItem voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7bdf0-103">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>

<span data-ttu-id="7bdf0-104">Hiermee worden de gegevens gedefinieerd die door het besturings element worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="7bdf0-104">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="7bdf0-105">Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.</span><span class="sxs-lookup"><span data-stu-id="7bdf0-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="7bdf0-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) Controls-element (Format) Control element (opmaak) voor besturings elementen voor weer gave (indeling) CustomControl-element voor besturings element voor besturings elementen voor de weer gave (Format) CustomEntries-element voor het weer geven van het element CustomEntry (Format) voor CustomEntries voor besturings elementen voor de weer gave (Format) CustomItem-element voor CustomEntry voor besturings elementen voor weer gave (Format) ExpressionBinding-element voor CustomItem voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="7bdf0-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7bdf0-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="7bdf0-107">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="7bdf0-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="7bdf0-108">Attributes and Elements</span></span>

<span data-ttu-id="7bdf0-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `ExpressionBinding` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="7bdf0-109">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7bdf0-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="7bdf0-110">Attributes</span></span>

<span data-ttu-id="7bdf0-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="7bdf0-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7bdf0-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="7bdf0-112">Child Elements</span></span>

|<span data-ttu-id="7bdf0-113">Element</span><span class="sxs-lookup"><span data-stu-id="7bdf0-113">Element</span></span>|<span data-ttu-id="7bdf0-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="7bdf0-114">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="7bdf0-115">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="7bdf0-115">Optional element.</span></span><br /><br /> <span data-ttu-id="7bdf0-116">Hiermee wordt een besturings element gedefinieerd dat door dit besturings element wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="7bdf0-116">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="7bdf0-117">Het element CustomControlName voor ExpressionBinding voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7bdf0-117">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="7bdf0-118">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="7bdf0-118">Optional element.</span></span><br /><br /> <span data-ttu-id="7bdf0-119">Hiermee geeft u de naam op van een algemeen besturings element of een weergave besturings element.</span><span class="sxs-lookup"><span data-stu-id="7bdf0-119">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="7bdf0-120">Het element EnumerateCollection voor ExpressionBinding voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7bdf0-120">EnumerateCollection Element for ExpressionBinding for Controls for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="7bdf0-121">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="7bdf0-121">Optional element.</span></span><br /><br /> <span data-ttu-id="7bdf0-122">Hiermee geeft u op dat de elementen van verzamelingen worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="7bdf0-122">Specifies that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="7bdf0-123">ItemSelectionCondition-element van ExpressionBinding voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="7bdf0-123">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="7bdf0-124">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="7bdf0-124">Optional element.</span></span><br /><br /> <span data-ttu-id="7bdf0-125">Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit besturings element.</span><span class="sxs-lookup"><span data-stu-id="7bdf0-125">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="7bdf0-126">Het element PropertyName voor ExpressionBinding voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7bdf0-126">PropertyName Element for ExpressionBinding for Controls for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="7bdf0-127">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="7bdf0-127">Optional element.</span></span><br /><br /> <span data-ttu-id="7bdf0-128">Hiermee geeft u de .NET-eigenschap op waarvan de waarde wordt weer gegeven door het besturings element.</span><span class="sxs-lookup"><span data-stu-id="7bdf0-128">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="7bdf0-129">Het element ScriptBlock voor ExpressionBinding voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7bdf0-129">ScriptBlock Element for ExpressionBinding for Controls for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="7bdf0-130">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="7bdf0-130">Optional element.</span></span><br /><br /> <span data-ttu-id="7bdf0-131">Hiermee geeft u het script op waarvan de waarde wordt weer gegeven door het besturings element.</span><span class="sxs-lookup"><span data-stu-id="7bdf0-131">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="7bdf0-132">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="7bdf0-132">Parent Elements</span></span>

|<span data-ttu-id="7bdf0-133">Element</span><span class="sxs-lookup"><span data-stu-id="7bdf0-133">Element</span></span>|<span data-ttu-id="7bdf0-134">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="7bdf0-134">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7bdf0-135">Het element CustomItem voor CustomEntry voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7bdf0-135">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="7bdf0-136">Hiermee definieert u welke gegevens worden weer gegeven door het besturings element en hoe deze worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="7bdf0-136">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7bdf0-137">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="7bdf0-137">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="7bdf0-138">Zie ook</span><span class="sxs-lookup"><span data-stu-id="7bdf0-138">See Also</span></span>

[<span data-ttu-id="7bdf0-139">Het element CustomItem voor CustomEntry voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7bdf0-139">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="7bdf0-140">Het element CustomControlName voor ExpressionBinding voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7bdf0-140">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="7bdf0-141">Het element EnumerateCollection voor ExpressionBinding voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7bdf0-141">EnumerateCollection Element for ExpressionBinding for Controls for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="7bdf0-142">ItemSelectionCondition-element van ExpressionBinding voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="7bdf0-142">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="7bdf0-143">Het element PropertyName voor ExpressionBinding voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7bdf0-143">PropertyName Element for ExpressionBinding for Controls for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="7bdf0-144">Het element ScriptBlock voor ExpressionBinding voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7bdf0-144">ScriptBlock Element for ExpressionBinding for Controls for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="7bdf0-145">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="7bdf0-145">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
