---
title: ExpressionBinding-element voor CustomItem voor CustomControl voor weer gave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7f5ebea5-ee9c-4b90-a116-12a1daa28fc7
caps.latest.revision: 7
ms.openlocfilehash: 226bbea1d7613ad3099e05e8caa9817ff16c1f42
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72354626"
---
# <a name="expressionbinding-element-for-customitem-for-customcontrol-for-view-format"></a><span data-ttu-id="d5ffc-102">Het element ExpressionBinding voor CustomItem voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="d5ffc-102">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>

<span data-ttu-id="d5ffc-103">Hiermee worden de gegevens gedefinieerd die door het besturings element worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="d5ffc-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="d5ffc-104">Dit element wordt gebruikt bij het definiëren van een aangepaste beheer weergave.</span><span class="sxs-lookup"><span data-stu-id="d5ffc-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="d5ffc-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) CustomControl-element voor weer gave (indeling) CustomEntries element voor CustomControl voor weer gave (Format) CustomEntry-element voor CustomEntries voor CustomControl voor weer gave ( Format) CustomItem-element voor CustomEntry voor CustomControl voor weer gave (Format) ExpressionBinding-element voor CustomItem voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="d5ffc-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d5ffc-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="d5ffc-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="d5ffc-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="d5ffc-107">Attributes and Elements</span></span>

<span data-ttu-id="d5ffc-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `ExpressionBinding` beschreven.</span><span class="sxs-lookup"><span data-stu-id="d5ffc-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d5ffc-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="d5ffc-109">Attributes</span></span>

<span data-ttu-id="d5ffc-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="d5ffc-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d5ffc-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="d5ffc-111">Child Elements</span></span>

|<span data-ttu-id="d5ffc-112">Element</span><span class="sxs-lookup"><span data-stu-id="d5ffc-112">Element</span></span>|<span data-ttu-id="d5ffc-113">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="d5ffc-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="d5ffc-114">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="d5ffc-114">Optional element.</span></span><br /><br /> <span data-ttu-id="d5ffc-115">Hiermee wordt een besturings element gedefinieerd dat door dit besturings element wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="d5ffc-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="d5ffc-116">CustomControlName-element voor ExpressionBinding voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="d5ffc-116">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="d5ffc-117">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="d5ffc-117">Optional element.</span></span><br /><br /> <span data-ttu-id="d5ffc-118">Hiermee geeft u de naam op van een algemeen besturings element of een weergave besturings element.</span><span class="sxs-lookup"><span data-stu-id="d5ffc-118">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="d5ffc-119">EnumerateCollection-element voor ExpressionBinding voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="d5ffc-119">EnumerateCollection Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="d5ffc-120">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="d5ffc-120">Optional element.</span></span><br /><br /> <span data-ttu-id="d5ffc-121">Opgegeven dat de elementen van verzamelingen worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="d5ffc-121">Specified that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="d5ffc-122">ItemSelectionCondition-element voor ExpressionBinding voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="d5ffc-122">ItemSelectionCondition Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="d5ffc-123">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="d5ffc-123">Optional element.</span></span><br /><br /> <span data-ttu-id="d5ffc-124">Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit besturings element.</span><span class="sxs-lookup"><span data-stu-id="d5ffc-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="d5ffc-125">Het element PropertyName voor ExpressionBinding voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="d5ffc-125">PropertyName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="d5ffc-126">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="d5ffc-126">Optional element.</span></span><br /><br /> <span data-ttu-id="d5ffc-127">Hiermee geeft u de .NET-eigenschap op waarvan de waarde wordt weer gegeven door het besturings element.</span><span class="sxs-lookup"><span data-stu-id="d5ffc-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="d5ffc-128">Script block-element voor ExpressionBinding voor CustomCustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="d5ffc-128">ScriptBlock Element for ExpressionBinding for CustomCustomControl for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="d5ffc-129">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="d5ffc-129">Optional element.</span></span><br /><br /> <span data-ttu-id="d5ffc-130">Hiermee geeft u het script op waarvan de waarde wordt weer gegeven door het besturings element.</span><span class="sxs-lookup"><span data-stu-id="d5ffc-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d5ffc-131">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="d5ffc-131">Parent Elements</span></span>

|<span data-ttu-id="d5ffc-132">Element</span><span class="sxs-lookup"><span data-stu-id="d5ffc-132">Element</span></span>|<span data-ttu-id="d5ffc-133">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="d5ffc-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d5ffc-134">CustomItem-element voor CustomEntry voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="d5ffc-134">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="d5ffc-135">Hiermee definieert u welke gegevens worden weer gegeven in de weer gave van het aangepaste besturings element en hoe deze worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="d5ffc-135">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d5ffc-136">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="d5ffc-136">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="d5ffc-137">Zie ook</span><span class="sxs-lookup"><span data-stu-id="d5ffc-137">See Also</span></span>

[<span data-ttu-id="d5ffc-138">CustomControlName-element voor ExpressionBinding voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="d5ffc-138">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="d5ffc-139">EnumerateCollection-element voor ExpressionBinding voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="d5ffc-139">EnumerateCollection Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="d5ffc-140">ItemSelectionCondition-element voor ExpressionBinding voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="d5ffc-140">ItemSelectionCondition Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="d5ffc-141">Het element PropertyName voor ExpressionBinding voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="d5ffc-141">PropertyName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="d5ffc-142">Script block-element voor ExpressionBinding voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="d5ffc-142">ScriptBlock Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="d5ffc-143">CustomItem-element voor CustomEntry voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="d5ffc-143">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="d5ffc-144">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="d5ffc-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
