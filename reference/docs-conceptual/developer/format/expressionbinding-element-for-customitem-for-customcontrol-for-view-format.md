---
ms.date: 09/13/2016
ms.topic: reference
title: Het element ExpressionBinding voor CustomItem voor CustomControl voor Weergave (opmaak)
description: Het element ExpressionBinding voor CustomItem voor CustomControl voor Weergave (opmaak)
ms.openlocfilehash: 8f4bfef4f6c65c6dabc7a776dda1083bac11fdf7
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92648197"
---
# <a name="expressionbinding-element-for-customitem-for-customcontrol-for-view-format"></a><span data-ttu-id="915ef-103">Het element ExpressionBinding voor CustomItem voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="915ef-103">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>

<span data-ttu-id="915ef-104">Hiermee worden de gegevens gedefinieerd die door het besturings element worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="915ef-104">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="915ef-105">Dit element wordt gebruikt bij het definiëren van een aangepaste beheer weergave.</span><span class="sxs-lookup"><span data-stu-id="915ef-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="915ef-106">Configuratie-element (indeling) ViewDefinitions element (indeling) weer gave element (indeling) CustomControl-element voor weer gave (Format) CustomEntries-element voor CustomControl voor weer gave (Format) CustomEntry-element voor CustomEntries voor CustomControl voor weer gave (Format) CustomItem-element voor CustomEntry voor de weer gave (Format)</span><span class="sxs-lookup"><span data-stu-id="915ef-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="915ef-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="915ef-107">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="915ef-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="915ef-108">Attributes and Elements</span></span>

<span data-ttu-id="915ef-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `ExpressionBinding` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="915ef-109">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="915ef-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="915ef-110">Attributes</span></span>

<span data-ttu-id="915ef-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="915ef-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="915ef-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="915ef-112">Child Elements</span></span>

|<span data-ttu-id="915ef-113">Element</span><span class="sxs-lookup"><span data-stu-id="915ef-113">Element</span></span>|<span data-ttu-id="915ef-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="915ef-114">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="915ef-115">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="915ef-115">Optional element.</span></span><br /><br /> <span data-ttu-id="915ef-116">Hiermee wordt een besturings element gedefinieerd dat door dit besturings element wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="915ef-116">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="915ef-117">Het element CustomControlName voor ExpressionBinding voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="915ef-117">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="915ef-118">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="915ef-118">Optional element.</span></span><br /><br /> <span data-ttu-id="915ef-119">Hiermee geeft u de naam op van een algemeen besturings element of een weergave besturings element.</span><span class="sxs-lookup"><span data-stu-id="915ef-119">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="915ef-120">Het element EnumerateCollection voor ExpressionBinding voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="915ef-120">EnumerateCollection Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="915ef-121">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="915ef-121">Optional element.</span></span><br /><br /> <span data-ttu-id="915ef-122">Opgegeven dat de elementen van verzamelingen worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="915ef-122">Specified that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="915ef-123">ItemSelectionCondition-element voor ExpressionBinding voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="915ef-123">ItemSelectionCondition Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="915ef-124">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="915ef-124">Optional element.</span></span><br /><br /> <span data-ttu-id="915ef-125">Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit besturings element.</span><span class="sxs-lookup"><span data-stu-id="915ef-125">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="915ef-126">Het element PropertyName voor ExpressionBinding voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="915ef-126">PropertyName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="915ef-127">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="915ef-127">Optional element.</span></span><br /><br /> <span data-ttu-id="915ef-128">Hiermee geeft u de .NET-eigenschap op waarvan de waarde wordt weer gegeven door het besturings element.</span><span class="sxs-lookup"><span data-stu-id="915ef-128">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="915ef-129">Script block-element voor ExpressionBinding voor CustomCustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="915ef-129">ScriptBlock Element for ExpressionBinding for CustomCustomControl for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="915ef-130">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="915ef-130">Optional element.</span></span><br /><br /> <span data-ttu-id="915ef-131">Hiermee geeft u het script op waarvan de waarde wordt weer gegeven door het besturings element.</span><span class="sxs-lookup"><span data-stu-id="915ef-131">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="915ef-132">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="915ef-132">Parent Elements</span></span>

|<span data-ttu-id="915ef-133">Element</span><span class="sxs-lookup"><span data-stu-id="915ef-133">Element</span></span>|<span data-ttu-id="915ef-134">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="915ef-134">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="915ef-135">Het element CustomItem voor CustomEntry voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="915ef-135">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="915ef-136">Hiermee definieert u welke gegevens worden weer gegeven in de weer gave van het aangepaste besturings element en hoe deze worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="915ef-136">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="915ef-137">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="915ef-137">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="915ef-138">Zie ook</span><span class="sxs-lookup"><span data-stu-id="915ef-138">See Also</span></span>

[<span data-ttu-id="915ef-139">Het element CustomControlName voor ExpressionBinding voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="915ef-139">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="915ef-140">Het element EnumerateCollection voor ExpressionBinding voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="915ef-140">EnumerateCollection Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="915ef-141">ItemSelectionCondition-element voor ExpressionBinding voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="915ef-141">ItemSelectionCondition Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="915ef-142">Het element PropertyName voor ExpressionBinding voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="915ef-142">PropertyName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="915ef-143">Het element ScriptBlock voor ExpressionBinding voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="915ef-143">ScriptBlock Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="915ef-144">Het element CustomItem voor CustomEntry voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="915ef-144">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="915ef-145">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="915ef-145">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
