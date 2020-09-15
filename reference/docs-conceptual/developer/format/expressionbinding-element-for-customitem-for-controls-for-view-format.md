---
title: ExpressionBinding-element voor CustomItem voor besturings elementen voor weer gave (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 6760bf17be58411948ecb3437bf18bce40073954
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773807"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-view-format"></a><span data-ttu-id="4e9b4-102">Het element ExpressionBinding voor CustomItem voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="4e9b4-102">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>

<span data-ttu-id="4e9b4-103">Hiermee worden de gegevens gedefinieerd die door het besturings element worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="4e9b4-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="4e9b4-104">Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.</span><span class="sxs-lookup"><span data-stu-id="4e9b4-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="4e9b4-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) Controls-element (Format) Control element (opmaak) voor besturings elementen voor weer gave (indeling) CustomControl-element voor besturings element voor besturings elementen voor de weer gave (Format) CustomEntries-element voor het weer geven van het element CustomEntry (Format) voor CustomEntries voor besturings elementen voor de weer gave (Format) CustomItem-element voor CustomEntry voor besturings elementen voor weer gave (Format) ExpressionBinding-element voor CustomItem voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="4e9b4-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4e9b4-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="4e9b4-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="4e9b4-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="4e9b4-107">Attributes and Elements</span></span>

<span data-ttu-id="4e9b4-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `ExpressionBinding` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="4e9b4-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4e9b4-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="4e9b4-109">Attributes</span></span>

<span data-ttu-id="4e9b4-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="4e9b4-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4e9b4-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="4e9b4-111">Child Elements</span></span>

|<span data-ttu-id="4e9b4-112">Element</span><span class="sxs-lookup"><span data-stu-id="4e9b4-112">Element</span></span>|<span data-ttu-id="4e9b4-113">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="4e9b4-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="4e9b4-114">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="4e9b4-114">Optional element.</span></span><br /><br /> <span data-ttu-id="4e9b4-115">Hiermee wordt een besturings element gedefinieerd dat door dit besturings element wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="4e9b4-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="4e9b4-116">Het element CustomControlName voor ExpressionBinding voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="4e9b4-116">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="4e9b4-117">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="4e9b4-117">Optional element.</span></span><br /><br /> <span data-ttu-id="4e9b4-118">Hiermee geeft u de naam op van een algemeen besturings element of een weergave besturings element.</span><span class="sxs-lookup"><span data-stu-id="4e9b4-118">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="4e9b4-119">Het element EnumerateCollection voor ExpressionBinding voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="4e9b4-119">EnumerateCollection Element for ExpressionBinding for Controls for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="4e9b4-120">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="4e9b4-120">Optional element.</span></span><br /><br /> <span data-ttu-id="4e9b4-121">Hiermee geeft u op dat de elementen van verzamelingen worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="4e9b4-121">Specifies that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="4e9b4-122">ItemSelectionCondition-element van ExpressionBinding voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="4e9b4-122">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="4e9b4-123">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="4e9b4-123">Optional element.</span></span><br /><br /> <span data-ttu-id="4e9b4-124">Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit besturings element.</span><span class="sxs-lookup"><span data-stu-id="4e9b4-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="4e9b4-125">Het element PropertyName voor ExpressionBinding voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="4e9b4-125">PropertyName Element for ExpressionBinding for Controls for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="4e9b4-126">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="4e9b4-126">Optional element.</span></span><br /><br /> <span data-ttu-id="4e9b4-127">Hiermee geeft u de .NET-eigenschap op waarvan de waarde wordt weer gegeven door het besturings element.</span><span class="sxs-lookup"><span data-stu-id="4e9b4-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="4e9b4-128">Het element ScriptBlock voor ExpressionBinding voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="4e9b4-128">ScriptBlock Element for ExpressionBinding for Controls for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="4e9b4-129">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="4e9b4-129">Optional element.</span></span><br /><br /> <span data-ttu-id="4e9b4-130">Hiermee geeft u het script op waarvan de waarde wordt weer gegeven door het besturings element.</span><span class="sxs-lookup"><span data-stu-id="4e9b4-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="4e9b4-131">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="4e9b4-131">Parent Elements</span></span>

|<span data-ttu-id="4e9b4-132">Element</span><span class="sxs-lookup"><span data-stu-id="4e9b4-132">Element</span></span>|<span data-ttu-id="4e9b4-133">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="4e9b4-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4e9b4-134">Het element CustomItem voor CustomEntry voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="4e9b4-134">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="4e9b4-135">Hiermee definieert u welke gegevens worden weer gegeven door het besturings element en hoe deze worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="4e9b4-135">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4e9b4-136">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="4e9b4-136">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="4e9b4-137">Zie ook</span><span class="sxs-lookup"><span data-stu-id="4e9b4-137">See Also</span></span>

[<span data-ttu-id="4e9b4-138">Het element CustomItem voor CustomEntry voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="4e9b4-138">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="4e9b4-139">Het element CustomControlName voor ExpressionBinding voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="4e9b4-139">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="4e9b4-140">Het element EnumerateCollection voor ExpressionBinding voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="4e9b4-140">EnumerateCollection Element for ExpressionBinding for Controls for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="4e9b4-141">ItemSelectionCondition-element van ExpressionBinding voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="4e9b4-141">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="4e9b4-142">Het element PropertyName voor ExpressionBinding voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="4e9b4-142">PropertyName Element for ExpressionBinding for Controls for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="4e9b4-143">Het element ScriptBlock voor ExpressionBinding voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="4e9b4-143">ScriptBlock Element for ExpressionBinding for Controls for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="4e9b4-144">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="4e9b4-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
