---
title: ItemSelectionCondition-element voor ExpressionBinding voor GroupBy (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6af3be7d-921e-4cf7-bd5a-d87aa0b4efbd
caps.latest.revision: 7
ms.openlocfilehash: b2b0a0d1996392614807e08b820a72978e38a0cb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72356124"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-groupby-format"></a><span data-ttu-id="076ab-102">Het element ItemSelectionCondition voor ExpressionBinding voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="076ab-102">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>

<span data-ttu-id="076ab-103">Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit besturings element.</span><span class="sxs-lookup"><span data-stu-id="076ab-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="076ab-104">Er is geen limiet voor het aantal selectie omstandigheden dat kan worden opgegeven voor een besturings element.</span><span class="sxs-lookup"><span data-stu-id="076ab-104">There is no limit to the number of selection conditions that can be specified for a control item.</span></span> <span data-ttu-id="076ab-105">Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="076ab-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="076ab-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element voor weer gave (indeling) GroupBy-element (Format) voor weer gave (indeling) CustomControl-element voor het element GroupBy (indeling) CustomEntries voor CustomControl voor het element GroupBy (Format) CustomEntry voor CustomControl voor het element GroupBy (Format) CustomItem voor CustomEntry voor het element GroupBy (Format) ExpressionBinding voor CustomItem voor het element GroupBy (Format) ItemSelectionCondition voor ExpressionBinding voor GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="076ab-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="076ab-107">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="076ab-107">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="076ab-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="076ab-108">Attributes and Elements</span></span>

<span data-ttu-id="076ab-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `ItemSelectionCondition` beschreven.</span><span class="sxs-lookup"><span data-stu-id="076ab-109">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="076ab-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="076ab-110">Attributes</span></span>

<span data-ttu-id="076ab-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="076ab-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="076ab-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="076ab-112">Child Elements</span></span>

|<span data-ttu-id="076ab-113">Element</span><span class="sxs-lookup"><span data-stu-id="076ab-113">Element</span></span>|<span data-ttu-id="076ab-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="076ab-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="076ab-115">Het element PropertyName voor ItemSelectionCondition voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="076ab-115">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)|<span data-ttu-id="076ab-116">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="076ab-116">Optional element.</span></span><br /><br /> <span data-ttu-id="076ab-117">Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="076ab-117">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="076ab-118">Script block-element voor ItemSelectionCondition voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="076ab-118">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)|<span data-ttu-id="076ab-119">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="076ab-119">Optional element.</span></span><br /><br /> <span data-ttu-id="076ab-120">Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="076ab-120">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="076ab-121">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="076ab-121">Parent Elements</span></span>

|<span data-ttu-id="076ab-122">Element</span><span class="sxs-lookup"><span data-stu-id="076ab-122">Element</span></span>|<span data-ttu-id="076ab-123">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="076ab-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="076ab-124">ExpressionBinding-element voor CustomItem voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="076ab-124">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="076ab-125">Hiermee worden de gegevens gedefinieerd die door het besturings element worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="076ab-125">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="076ab-126">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="076ab-126">Remarks</span></span>

<span data-ttu-id="076ab-127">U kunt voor dit probleem één eigenschaps naam of een script opgeven, maar niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="076ab-127">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="076ab-128">Zie ook</span><span class="sxs-lookup"><span data-stu-id="076ab-128">See Also</span></span>

[<span data-ttu-id="076ab-129">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="076ab-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

[<span data-ttu-id="076ab-130">ExpressionBinding-element voor CustomItem voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="076ab-130">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)
