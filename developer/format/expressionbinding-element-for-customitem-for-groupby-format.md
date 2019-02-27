---
title: ExpressionBinding-Element voor CustomItem voor GroupBy (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5eae5088-7605-4ef2-a703-faf3e5a5fc94
caps.latest.revision: 8
ms.openlocfilehash: 4714bfd1530585aa80aabc010b86d25bf0c7f9c4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846058"
---
# <a name="expressionbinding-element-for-customitem-for-groupby-format"></a><span data-ttu-id="04355-102">Het element ExpressionBinding voor CustomItem voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="04355-102">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>

<span data-ttu-id="04355-103">Definieert de gegevens die door het besturingselement wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="04355-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="04355-104">Dit element wordt gebruikt bij het definiëren van hoe een nieuwe groep objecten worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="04355-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="04355-105">Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) GroupBy Element voor weergave (indeling) CustomControl Element voor GroupBy (indeling) CustomEntries Element voor CustomControl voor GroupBy (indeling) CustomEntry Element voor CustomControl voor GroupBy (indeling) CustomItem Element voor CustomEntry voor GroupBy (indeling) ExpressionBinding Element voor CustomItem voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="04355-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="04355-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="04355-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="04355-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="04355-107">Attributes and Elements</span></span>

<span data-ttu-id="04355-108">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `ExpressionBinding` element.</span><span class="sxs-lookup"><span data-stu-id="04355-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="04355-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="04355-109">Attributes</span></span>

<span data-ttu-id="04355-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="04355-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="04355-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="04355-111">Child Elements</span></span>

|<span data-ttu-id="04355-112">Element</span><span class="sxs-lookup"><span data-stu-id="04355-112">Element</span></span>|<span data-ttu-id="04355-113">Description</span><span class="sxs-lookup"><span data-stu-id="04355-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="04355-114">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="04355-114">Optional element.</span></span><br /><br /> <span data-ttu-id="04355-115">Hiermee definieert u een besturingselement dat wordt gebruikt door dit besturingselement.</span><span class="sxs-lookup"><span data-stu-id="04355-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="04355-116">CustomControlName-Element voor ExpressionBinding voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="04355-116">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="04355-117">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="04355-117">Optional element.</span></span><br /><br /> <span data-ttu-id="04355-118">Hiermee geeft u de naam van een algemene besturingselement of een besturingselement voor lijstweergave.</span><span class="sxs-lookup"><span data-stu-id="04355-118">Specifies the name of a common control or a view control.</span></span>|
|<span data-ttu-id="04355-119">[EnumerateCollection-Element voor ExpressionBinding voor GroupBy (indeling)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)EnumerateCollection-Element voor ExpressionBinding voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="04355-119">[EnumerateCollection Element for ExpressionBinding for GroupBy (Format)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)EnumerateCollection Element for ExpressionBinding for GroupBy (Format)</span></span>|<span data-ttu-id="04355-120">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="04355-120">Optional element.</span></span><br /><br /> <span data-ttu-id="04355-121">Opgegeven dat de elementen van verzamelingen worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="04355-121">Specified that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="04355-122">ItemSelectionCondition-Element voor ExpressionBinding voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="04355-122">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="04355-123">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="04355-123">Optional element.</span></span><br /><br /> <span data-ttu-id="04355-124">Hiermee definieert u de voorwaarde die moet bestaan voor dit besturingselement moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="04355-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="04355-125">PropertyName-Element voor ExpressionBinding voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="04355-125">PropertyName Element for ExpressionBinding for GroupBy (Format)</span></span>](./propertyname-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="04355-126">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="04355-126">Optional element.</span></span><br /><br /> <span data-ttu-id="04355-127">Hiermee geeft u de .NET-eigenschap waarvan de waarde van het besturingselement wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="04355-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="04355-128">ScriptBlock-Element voor ExpressionBinding voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="04355-128">ScriptBlock Element for ExpressionBinding for GroupBy (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="04355-129">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="04355-129">Optional element.</span></span><br /><br /> <span data-ttu-id="04355-130">Hiermee geeft u het script waarvan de waarde van het besturingselement wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="04355-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="04355-131">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="04355-131">Parent Elements</span></span>

|<span data-ttu-id="04355-132">Element</span><span class="sxs-lookup"><span data-stu-id="04355-132">Element</span></span>|<span data-ttu-id="04355-133">Description</span><span class="sxs-lookup"><span data-stu-id="04355-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="04355-134">CustomItem-Element voor CustomEntry voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="04355-134">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="04355-135">Bepaalt welke gegevens worden weergegeven in de weergave van het aangepaste besturingselement en hoe deze wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="04355-135">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="see-also"></a><span data-ttu-id="04355-136">Zie ook</span><span class="sxs-lookup"><span data-stu-id="04355-136">See Also</span></span>

[<span data-ttu-id="04355-137">CustomControlName-Element voor ExpressionBinding voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="04355-137">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="04355-138">EnumerateCollection-Element voor ExpressionBinding voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="04355-138">EnumerateCollection Element for ExpressionBinding for GroupBy (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="04355-139">ItemSelectionCondition-Element voor ExpressionBinding voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="04355-139">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="04355-140">PropertyName-Element voor ExpressionBinding voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="04355-140">PropertyName Element for ExpressionBinding for GroupBy (Format)</span></span>](./propertyname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="04355-141">ScriptBlock-Element voor ExpressionBinding voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="04355-141">ScriptBlock Element for ExpressionBinding for GroupBy (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="04355-142">CustomItem-Element voor CustomEntry voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="04355-142">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="04355-143">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="04355-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
