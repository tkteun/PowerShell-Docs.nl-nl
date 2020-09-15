---
title: ItemSelectionCondition-element voor ExpressionBinding voor GroupBy (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: a9b74f1882efc578f7d9ab27b8cd2f8a52833ab8
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773433"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-groupby-format"></a><span data-ttu-id="83ee7-102">Het element ItemSelectionCondition voor ExpressionBinding voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="83ee7-102">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>

<span data-ttu-id="83ee7-103">Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit besturings element.</span><span class="sxs-lookup"><span data-stu-id="83ee7-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="83ee7-104">Er is geen limiet voor het aantal selectie omstandigheden dat kan worden opgegeven voor een besturings element.</span><span class="sxs-lookup"><span data-stu-id="83ee7-104">There is no limit to the number of selection conditions that can be specified for a control item.</span></span> <span data-ttu-id="83ee7-105">Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="83ee7-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="83ee7-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element van het type GroupBy-element (Format) voor weer gave (indeling) CustomControl-element voor het CustomEntries-element van GroupBy (Format) voor CustomControl voor het element GroupBy (Format) CustomEntry element voor CustomControl voor het object GroupBy (Format) voor CustomEntry voor het element GroupBy (Format) ExpressionBinding voor CustomItem voor GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="83ee7-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="83ee7-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="83ee7-107">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="83ee7-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="83ee7-108">Attributes and Elements</span></span>

<span data-ttu-id="83ee7-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `ItemSelectionCondition` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="83ee7-109">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="83ee7-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="83ee7-110">Attributes</span></span>

<span data-ttu-id="83ee7-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="83ee7-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="83ee7-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="83ee7-112">Child Elements</span></span>

|<span data-ttu-id="83ee7-113">Element</span><span class="sxs-lookup"><span data-stu-id="83ee7-113">Element</span></span>|<span data-ttu-id="83ee7-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="83ee7-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="83ee7-115">Het element PropertyName voor ItemSelectionCondition voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="83ee7-115">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)|<span data-ttu-id="83ee7-116">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="83ee7-116">Optional element.</span></span><br /><br /> <span data-ttu-id="83ee7-117">Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="83ee7-117">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="83ee7-118">Het element ScriptBlock voor ItemSelectionCondition voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="83ee7-118">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)|<span data-ttu-id="83ee7-119">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="83ee7-119">Optional element.</span></span><br /><br /> <span data-ttu-id="83ee7-120">Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="83ee7-120">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="83ee7-121">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="83ee7-121">Parent Elements</span></span>

|<span data-ttu-id="83ee7-122">Element</span><span class="sxs-lookup"><span data-stu-id="83ee7-122">Element</span></span>|<span data-ttu-id="83ee7-123">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="83ee7-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="83ee7-124">Het element ExpressionBinding voor CustomItem voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="83ee7-124">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="83ee7-125">Hiermee worden de gegevens gedefinieerd die door het besturings element worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="83ee7-125">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="83ee7-126">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="83ee7-126">Remarks</span></span>

<span data-ttu-id="83ee7-127">U kunt voor dit probleem één eigenschaps naam of een script opgeven, maar niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="83ee7-127">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="83ee7-128">Zie ook</span><span class="sxs-lookup"><span data-stu-id="83ee7-128">See Also</span></span>

[<span data-ttu-id="83ee7-129">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="83ee7-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

[<span data-ttu-id="83ee7-130">Het element ExpressionBinding voor CustomItem voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="83ee7-130">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)
