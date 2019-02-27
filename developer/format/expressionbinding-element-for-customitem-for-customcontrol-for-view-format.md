---
title: ExpressionBinding-Element voor CustomItem voor CustomControl voor weergave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7f5ebea5-ee9c-4b90-a116-12a1daa28fc7
caps.latest.revision: 7
ms.openlocfilehash: 226bbea1d7613ad3099e05e8caa9817ff16c1f42
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850090"
---
# <a name="expressionbinding-element-for-customitem-for-customcontrol-for-view-format"></a><span data-ttu-id="23041-102">Het element ExpressionBinding voor CustomItem voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="23041-102">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>

<span data-ttu-id="23041-103">Definieert de gegevens die door het besturingselement wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="23041-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="23041-104">Dit element wordt gebruikt bij het definiëren van een aangepast besturingselement-weergave.</span><span class="sxs-lookup"><span data-stu-id="23041-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="23041-105">Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) CustomControl Element voor weergave (indeling) CustomEntries-Element voor CustomControl voor weergave (indeling) CustomEntry Element voor CustomEntries voor CustomControl voor weergave ( -Indeling) CustomItem Element voor CustomEntry voor CustomControl voor weergave (indeling) ExpressionBinding Element voor CustomItem voor CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="23041-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="23041-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="23041-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="23041-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="23041-107">Attributes and Elements</span></span>

<span data-ttu-id="23041-108">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `ExpressionBinding` element.</span><span class="sxs-lookup"><span data-stu-id="23041-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="23041-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="23041-109">Attributes</span></span>

<span data-ttu-id="23041-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="23041-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="23041-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="23041-111">Child Elements</span></span>

|<span data-ttu-id="23041-112">Element</span><span class="sxs-lookup"><span data-stu-id="23041-112">Element</span></span>|<span data-ttu-id="23041-113">Description</span><span class="sxs-lookup"><span data-stu-id="23041-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="23041-114">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="23041-114">Optional element.</span></span><br /><br /> <span data-ttu-id="23041-115">Hiermee definieert u een besturingselement dat wordt gebruikt door dit besturingselement.</span><span class="sxs-lookup"><span data-stu-id="23041-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="23041-116">CustomControlName-Element voor ExpressionBinding voor CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="23041-116">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="23041-117">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="23041-117">Optional element.</span></span><br /><br /> <span data-ttu-id="23041-118">Hiermee geeft u de naam van een algemene besturingselement of een besturingselement voor lijstweergave.</span><span class="sxs-lookup"><span data-stu-id="23041-118">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="23041-119">EnumerateCollection-Element voor ExpressionBinding voor CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="23041-119">EnumerateCollection Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="23041-120">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="23041-120">Optional element.</span></span><br /><br /> <span data-ttu-id="23041-121">Opgegeven dat de elementen van verzamelingen worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="23041-121">Specified that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="23041-122">ItemSelectionCondition-Element voor ExpressionBinding voor CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="23041-122">ItemSelectionCondition Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="23041-123">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="23041-123">Optional element.</span></span><br /><br /> <span data-ttu-id="23041-124">Hiermee definieert u de voorwaarde die moet bestaan voor dit besturingselement moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="23041-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="23041-125">PropertyName-Element voor ExpressionBinding voor CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="23041-125">PropertyName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="23041-126">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="23041-126">Optional element.</span></span><br /><br /> <span data-ttu-id="23041-127">Hiermee geeft u de .NET-eigenschap waarvan de waarde van het besturingselement wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="23041-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="23041-128">ScriptBlock-Element voor ExpressionBinding voor CustomCustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="23041-128">ScriptBlock Element for ExpressionBinding for CustomCustomControl for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="23041-129">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="23041-129">Optional element.</span></span><br /><br /> <span data-ttu-id="23041-130">Hiermee geeft u het script waarvan de waarde van het besturingselement wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="23041-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="23041-131">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="23041-131">Parent Elements</span></span>

|<span data-ttu-id="23041-132">Element</span><span class="sxs-lookup"><span data-stu-id="23041-132">Element</span></span>|<span data-ttu-id="23041-133">Description</span><span class="sxs-lookup"><span data-stu-id="23041-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="23041-134">CustomItem-Element voor CustomEntry voor CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="23041-134">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="23041-135">Bepaalt welke gegevens worden weergegeven in de weergave van het aangepaste besturingselement en hoe deze wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="23041-135">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="23041-136">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="23041-136">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="23041-137">Zie ook</span><span class="sxs-lookup"><span data-stu-id="23041-137">See Also</span></span>

[<span data-ttu-id="23041-138">CustomControlName-Element voor ExpressionBinding voor CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="23041-138">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="23041-139">EnumerateCollection-Element voor ExpressionBinding voor CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="23041-139">EnumerateCollection Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="23041-140">ItemSelectionCondition-Element voor ExpressionBinding voor CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="23041-140">ItemSelectionCondition Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="23041-141">PropertyName-Element voor ExpressionBinding voor CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="23041-141">PropertyName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="23041-142">ScriptBlock-Element voor ExpressionBinding voor CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="23041-142">ScriptBlock Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="23041-143">CustomItem-Element voor CustomEntry voor CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="23041-143">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="23041-144">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="23041-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
