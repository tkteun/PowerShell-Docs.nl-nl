---
title: ExpressionBinding-element voor CustomItem voor GroupBy (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 5b0017e487aab4ffcbf901cd44aad9b275b22832
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773722"
---
# <a name="expressionbinding-element-for-customitem-for-groupby-format"></a><span data-ttu-id="7e8ea-102">Het element ExpressionBinding voor CustomItem voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7e8ea-102">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>

<span data-ttu-id="7e8ea-103">Hiermee worden de gegevens gedefinieerd die door het besturings element worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="7e8ea-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="7e8ea-104">Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="7e8ea-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="7e8ea-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element van het type GroupBy-element (Format) voor weer gave (indeling) CustomControl-element voor het CustomEntries-element van GroupBy (Format) voor CustomControl voor het element GroupBy (Format) CustomEntry element voor CustomControl voor het object GroupBy (Format) voor CustomEntry voor het element GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="7e8ea-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7e8ea-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="7e8ea-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="7e8ea-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="7e8ea-107">Attributes and Elements</span></span>

<span data-ttu-id="7e8ea-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `ExpressionBinding` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="7e8ea-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7e8ea-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="7e8ea-109">Attributes</span></span>

<span data-ttu-id="7e8ea-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="7e8ea-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7e8ea-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="7e8ea-111">Child Elements</span></span>

|<span data-ttu-id="7e8ea-112">Element</span><span class="sxs-lookup"><span data-stu-id="7e8ea-112">Element</span></span>|<span data-ttu-id="7e8ea-113">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="7e8ea-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="7e8ea-114">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="7e8ea-114">Optional element.</span></span><br /><br /> <span data-ttu-id="7e8ea-115">Hiermee wordt een besturings element gedefinieerd dat door dit besturings element wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="7e8ea-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="7e8ea-116">Het element CustomControlName voor ExpressionBinding voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7e8ea-116">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="7e8ea-117">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="7e8ea-117">Optional element.</span></span><br /><br /> <span data-ttu-id="7e8ea-118">Hiermee geeft u de naam op van een algemeen besturings element of een weergave besturings element.</span><span class="sxs-lookup"><span data-stu-id="7e8ea-118">Specifies the name of a common control or a view control.</span></span>|
|<span data-ttu-id="7e8ea-119">[EnumerateCollection-element voor ExpressionBinding voor GroupBy (indeling)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md) EnumerateCollection-element voor ExpressionBinding voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="7e8ea-119">[EnumerateCollection Element for ExpressionBinding for GroupBy (Format)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)EnumerateCollection Element for ExpressionBinding for GroupBy (Format)</span></span>|<span data-ttu-id="7e8ea-120">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="7e8ea-120">Optional element.</span></span><br /><br /> <span data-ttu-id="7e8ea-121">Opgegeven dat de elementen van verzamelingen worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="7e8ea-121">Specified that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="7e8ea-122">Het element ItemSelectionCondition voor ExpressionBinding voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7e8ea-122">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="7e8ea-123">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="7e8ea-123">Optional element.</span></span><br /><br /> <span data-ttu-id="7e8ea-124">Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit besturings element.</span><span class="sxs-lookup"><span data-stu-id="7e8ea-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="7e8ea-125">Het element PropertyName voor ExpressionBinding voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7e8ea-125">PropertyName Element for ExpressionBinding for GroupBy (Format)</span></span>](./propertyname-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="7e8ea-126">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="7e8ea-126">Optional element.</span></span><br /><br /> <span data-ttu-id="7e8ea-127">Hiermee geeft u de .NET-eigenschap op waarvan de waarde wordt weer gegeven door het besturings element.</span><span class="sxs-lookup"><span data-stu-id="7e8ea-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="7e8ea-128">Het element ScriptBlock voor ExpressionBinding voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7e8ea-128">ScriptBlock Element for ExpressionBinding for GroupBy (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="7e8ea-129">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="7e8ea-129">Optional element.</span></span><br /><br /> <span data-ttu-id="7e8ea-130">Hiermee geeft u het script op waarvan de waarde wordt weer gegeven door het besturings element.</span><span class="sxs-lookup"><span data-stu-id="7e8ea-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="7e8ea-131">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="7e8ea-131">Parent Elements</span></span>

|<span data-ttu-id="7e8ea-132">Element</span><span class="sxs-lookup"><span data-stu-id="7e8ea-132">Element</span></span>|<span data-ttu-id="7e8ea-133">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="7e8ea-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7e8ea-134">Het element CustomItem voor CustomEntry voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7e8ea-134">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="7e8ea-135">Hiermee definieert u welke gegevens worden weer gegeven in de weer gave van het aangepaste besturings element en hoe deze worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="7e8ea-135">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="see-also"></a><span data-ttu-id="7e8ea-136">Zie ook</span><span class="sxs-lookup"><span data-stu-id="7e8ea-136">See Also</span></span>

[<span data-ttu-id="7e8ea-137">Het element CustomControlName voor ExpressionBinding voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7e8ea-137">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="7e8ea-138">Het element EnumerateCollection voor ExpressionBinding voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7e8ea-138">EnumerateCollection Element for ExpressionBinding for GroupBy (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="7e8ea-139">Het element ItemSelectionCondition voor ExpressionBinding voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7e8ea-139">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="7e8ea-140">Het element PropertyName voor ExpressionBinding voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7e8ea-140">PropertyName Element for ExpressionBinding for GroupBy (Format)</span></span>](./propertyname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="7e8ea-141">Het element ScriptBlock voor ExpressionBinding voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7e8ea-141">ScriptBlock Element for ExpressionBinding for GroupBy (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="7e8ea-142">Het element CustomItem voor CustomEntry voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7e8ea-142">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="7e8ea-143">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="7e8ea-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
