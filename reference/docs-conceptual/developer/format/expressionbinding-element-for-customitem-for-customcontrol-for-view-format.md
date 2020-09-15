---
title: ExpressionBinding-element voor CustomItem voor CustomControl voor weer gave (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 1885a2820c0cb250aa6fda80544f58d06136cfeb
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773790"
---
# <a name="expressionbinding-element-for-customitem-for-customcontrol-for-view-format"></a><span data-ttu-id="0a45e-102">Het element ExpressionBinding voor CustomItem voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="0a45e-102">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>

<span data-ttu-id="0a45e-103">Hiermee worden de gegevens gedefinieerd die door het besturings element worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="0a45e-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="0a45e-104">Dit element wordt gebruikt bij het definiëren van een aangepaste beheer weergave.</span><span class="sxs-lookup"><span data-stu-id="0a45e-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="0a45e-105">Configuratie-element (indeling) ViewDefinitions element (indeling) weer gave element (indeling) CustomControl-element voor weer gave (Format) CustomEntries-element voor CustomControl voor weer gave (Format) CustomEntry-element voor CustomEntries voor CustomControl voor weer gave (Format) CustomItem-element voor CustomEntry voor de weer gave (Format)</span><span class="sxs-lookup"><span data-stu-id="0a45e-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0a45e-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="0a45e-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="0a45e-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="0a45e-107">Attributes and Elements</span></span>

<span data-ttu-id="0a45e-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `ExpressionBinding` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="0a45e-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0a45e-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="0a45e-109">Attributes</span></span>

<span data-ttu-id="0a45e-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="0a45e-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0a45e-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="0a45e-111">Child Elements</span></span>

|<span data-ttu-id="0a45e-112">Element</span><span class="sxs-lookup"><span data-stu-id="0a45e-112">Element</span></span>|<span data-ttu-id="0a45e-113">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="0a45e-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="0a45e-114">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="0a45e-114">Optional element.</span></span><br /><br /> <span data-ttu-id="0a45e-115">Hiermee wordt een besturings element gedefinieerd dat door dit besturings element wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="0a45e-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="0a45e-116">Het element CustomControlName voor ExpressionBinding voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="0a45e-116">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="0a45e-117">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="0a45e-117">Optional element.</span></span><br /><br /> <span data-ttu-id="0a45e-118">Hiermee geeft u de naam op van een algemeen besturings element of een weergave besturings element.</span><span class="sxs-lookup"><span data-stu-id="0a45e-118">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="0a45e-119">Het element EnumerateCollection voor ExpressionBinding voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="0a45e-119">EnumerateCollection Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="0a45e-120">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="0a45e-120">Optional element.</span></span><br /><br /> <span data-ttu-id="0a45e-121">Opgegeven dat de elementen van verzamelingen worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="0a45e-121">Specified that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="0a45e-122">ItemSelectionCondition-element voor ExpressionBinding voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="0a45e-122">ItemSelectionCondition Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="0a45e-123">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="0a45e-123">Optional element.</span></span><br /><br /> <span data-ttu-id="0a45e-124">Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit besturings element.</span><span class="sxs-lookup"><span data-stu-id="0a45e-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="0a45e-125">Het element PropertyName voor ExpressionBinding voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="0a45e-125">PropertyName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="0a45e-126">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="0a45e-126">Optional element.</span></span><br /><br /> <span data-ttu-id="0a45e-127">Hiermee geeft u de .NET-eigenschap op waarvan de waarde wordt weer gegeven door het besturings element.</span><span class="sxs-lookup"><span data-stu-id="0a45e-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="0a45e-128">Script block-element voor ExpressionBinding voor CustomCustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="0a45e-128">ScriptBlock Element for ExpressionBinding for CustomCustomControl for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="0a45e-129">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="0a45e-129">Optional element.</span></span><br /><br /> <span data-ttu-id="0a45e-130">Hiermee geeft u het script op waarvan de waarde wordt weer gegeven door het besturings element.</span><span class="sxs-lookup"><span data-stu-id="0a45e-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="0a45e-131">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="0a45e-131">Parent Elements</span></span>

|<span data-ttu-id="0a45e-132">Element</span><span class="sxs-lookup"><span data-stu-id="0a45e-132">Element</span></span>|<span data-ttu-id="0a45e-133">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="0a45e-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0a45e-134">Het element CustomItem voor CustomEntry voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="0a45e-134">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="0a45e-135">Hiermee definieert u welke gegevens worden weer gegeven in de weer gave van het aangepaste besturings element en hoe deze worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="0a45e-135">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0a45e-136">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="0a45e-136">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="0a45e-137">Zie ook</span><span class="sxs-lookup"><span data-stu-id="0a45e-137">See Also</span></span>

[<span data-ttu-id="0a45e-138">Het element CustomControlName voor ExpressionBinding voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="0a45e-138">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="0a45e-139">Het element EnumerateCollection voor ExpressionBinding voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="0a45e-139">EnumerateCollection Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="0a45e-140">ItemSelectionCondition-element voor ExpressionBinding voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="0a45e-140">ItemSelectionCondition Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="0a45e-141">Het element PropertyName voor ExpressionBinding voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="0a45e-141">PropertyName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="0a45e-142">Het element ScriptBlock voor ExpressionBinding voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="0a45e-142">ScriptBlock Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="0a45e-143">Het element CustomItem voor CustomEntry voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="0a45e-143">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="0a45e-144">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="0a45e-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
