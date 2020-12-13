---
ms.date: 09/13/2016
ms.topic: reference
title: Het element ExpressionBinding voor CustomItem voor GroupBy (opmaak)
description: Het element ExpressionBinding voor CustomItem voor GroupBy (opmaak)
ms.openlocfilehash: 742d9f081a674dc3ee4c84d600933aaf57b2aa6b
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655297"
---
# <a name="expressionbinding-element-for-customitem-for-groupby-format"></a><span data-ttu-id="db702-103">Het element ExpressionBinding voor CustomItem voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="db702-103">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>

<span data-ttu-id="db702-104">Hiermee worden de gegevens gedefinieerd die door het besturings element worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="db702-104">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="db702-105">Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="db702-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="db702-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element van het type GroupBy-element (Format) voor weer gave (indeling) CustomControl-element voor het CustomEntries-element van GroupBy (Format) voor CustomControl voor het element GroupBy (Format) CustomEntry element voor CustomControl voor het object GroupBy (Format) voor CustomEntry voor het element GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="db702-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="db702-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="db702-107">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="db702-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="db702-108">Attributes and Elements</span></span>

<span data-ttu-id="db702-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `ExpressionBinding` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="db702-109">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="db702-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="db702-110">Attributes</span></span>

<span data-ttu-id="db702-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="db702-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="db702-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="db702-112">Child Elements</span></span>

|<span data-ttu-id="db702-113">Element</span><span class="sxs-lookup"><span data-stu-id="db702-113">Element</span></span>|<span data-ttu-id="db702-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="db702-114">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="db702-115">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="db702-115">Optional element.</span></span><br /><br /> <span data-ttu-id="db702-116">Hiermee wordt een besturings element gedefinieerd dat door dit besturings element wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="db702-116">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="db702-117">Het element CustomControlName voor ExpressionBinding voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="db702-117">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="db702-118">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="db702-118">Optional element.</span></span><br /><br /> <span data-ttu-id="db702-119">Hiermee geeft u de naam op van een algemeen besturings element of een weergave besturings element.</span><span class="sxs-lookup"><span data-stu-id="db702-119">Specifies the name of a common control or a view control.</span></span>|
|<span data-ttu-id="db702-120">[EnumerateCollection-element voor ExpressionBinding voor GroupBy (indeling)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md) EnumerateCollection-element voor ExpressionBinding voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="db702-120">[EnumerateCollection Element for ExpressionBinding for GroupBy (Format)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)EnumerateCollection Element for ExpressionBinding for GroupBy (Format)</span></span>|<span data-ttu-id="db702-121">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="db702-121">Optional element.</span></span><br /><br /> <span data-ttu-id="db702-122">Opgegeven dat de elementen van verzamelingen worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="db702-122">Specified that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="db702-123">Het element ItemSelectionCondition voor ExpressionBinding voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="db702-123">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="db702-124">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="db702-124">Optional element.</span></span><br /><br /> <span data-ttu-id="db702-125">Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit besturings element.</span><span class="sxs-lookup"><span data-stu-id="db702-125">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="db702-126">Het element PropertyName voor ExpressionBinding voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="db702-126">PropertyName Element for ExpressionBinding for GroupBy (Format)</span></span>](./propertyname-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="db702-127">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="db702-127">Optional element.</span></span><br /><br /> <span data-ttu-id="db702-128">Hiermee geeft u de .NET-eigenschap op waarvan de waarde wordt weer gegeven door het besturings element.</span><span class="sxs-lookup"><span data-stu-id="db702-128">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="db702-129">Het element ScriptBlock voor ExpressionBinding voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="db702-129">ScriptBlock Element for ExpressionBinding for GroupBy (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="db702-130">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="db702-130">Optional element.</span></span><br /><br /> <span data-ttu-id="db702-131">Hiermee geeft u het script op waarvan de waarde wordt weer gegeven door het besturings element.</span><span class="sxs-lookup"><span data-stu-id="db702-131">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="db702-132">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="db702-132">Parent Elements</span></span>

|<span data-ttu-id="db702-133">Element</span><span class="sxs-lookup"><span data-stu-id="db702-133">Element</span></span>|<span data-ttu-id="db702-134">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="db702-134">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="db702-135">Het element CustomItem voor CustomEntry voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="db702-135">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="db702-136">Hiermee definieert u welke gegevens worden weer gegeven in de weer gave van het aangepaste besturings element en hoe deze worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="db702-136">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="see-also"></a><span data-ttu-id="db702-137">Zie ook</span><span class="sxs-lookup"><span data-stu-id="db702-137">See Also</span></span>

[<span data-ttu-id="db702-138">Het element CustomControlName voor ExpressionBinding voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="db702-138">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="db702-139">Het element EnumerateCollection voor ExpressionBinding voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="db702-139">EnumerateCollection Element for ExpressionBinding for GroupBy (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="db702-140">Het element ItemSelectionCondition voor ExpressionBinding voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="db702-140">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="db702-141">Het element PropertyName voor ExpressionBinding voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="db702-141">PropertyName Element for ExpressionBinding for GroupBy (Format)</span></span>](./propertyname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="db702-142">Het element ScriptBlock voor ExpressionBinding voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="db702-142">ScriptBlock Element for ExpressionBinding for GroupBy (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="db702-143">Het element CustomItem voor CustomEntry voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="db702-143">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="db702-144">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="db702-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
