---
title: ItemSelectionCondition-element voor ExpressionBinding voor CustomControl (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 6a5c66a63c02980b16c2d2d9dd689410c8aec51c
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781185"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-customcontrol-format"></a><span data-ttu-id="4fa99-102">Het element ItemSelectionCondition voor ExpressionBinding voor CustomControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="4fa99-102">ItemSelectionCondition Element for ExpressionBinding for CustomControl (Format)</span></span>

<span data-ttu-id="4fa99-103">Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit besturings element.</span><span class="sxs-lookup"><span data-stu-id="4fa99-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="4fa99-104">Er is geen limiet voor het aantal selectie omstandigheden dat kan worden opgegeven voor een besturings element.</span><span class="sxs-lookup"><span data-stu-id="4fa99-104">There is no limit to the number of selection conditions that can be specified for a control item.</span></span> <span data-ttu-id="4fa99-105">Dit element wordt gebruikt bij het definiëren van een aangepaste beheer weergave.</span><span class="sxs-lookup"><span data-stu-id="4fa99-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="4fa99-106">Configuratie-element (indeling) ViewDefinitions element (indeling) weer gave element (indeling) CustomControl element (Format) CustomEntries element voor CustomControl voor weer gave (Format) CustomEntry-element voor CustomEntries voor weer gave (Format) CustomItem element voor CustomEntry voor weer gave (Format) ExpressionBinding element voor CustomItem voor weer gave (Format) voor expressie binding</span><span class="sxs-lookup"><span data-stu-id="4fa99-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4fa99-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="4fa99-107">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4fa99-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="4fa99-108">Attributes and Elements</span></span>

<span data-ttu-id="4fa99-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `ItemSelectionCondition` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="4fa99-109">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4fa99-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="4fa99-110">Attributes</span></span>

<span data-ttu-id="4fa99-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="4fa99-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4fa99-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="4fa99-112">Child Elements</span></span>

|<span data-ttu-id="4fa99-113">Element</span><span class="sxs-lookup"><span data-stu-id="4fa99-113">Element</span></span>|<span data-ttu-id="4fa99-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="4fa99-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4fa99-115">Het element PropertyName voor ItemSelectionCondition voor CustomControl voor weer gave (notatie</span><span class="sxs-lookup"><span data-stu-id="4fa99-115">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format</span></span>](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="4fa99-116">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="4fa99-116">Optional element.</span></span><br /><br /> <span data-ttu-id="4fa99-117">Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="4fa99-117">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="4fa99-118">Het element ScriptBlock voor ItemSelectionCondition voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="4fa99-118">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="4fa99-119">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="4fa99-119">Optional element.</span></span><br /><br /> <span data-ttu-id="4fa99-120">Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="4fa99-120">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="4fa99-121">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="4fa99-121">Parent Elements</span></span>

|<span data-ttu-id="4fa99-122">Element</span><span class="sxs-lookup"><span data-stu-id="4fa99-122">Element</span></span>|<span data-ttu-id="4fa99-123">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="4fa99-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4fa99-124">Het element ExpressionBinding voor CustomItem voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="4fa99-124">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="4fa99-125">Hiermee worden de gegevens gedefinieerd die door het besturings element worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="4fa99-125">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4fa99-126">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="4fa99-126">Remarks</span></span>

<span data-ttu-id="4fa99-127">U kunt voor dit probleem één eigenschaps naam of een script opgeven, maar niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="4fa99-127">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="4fa99-128">Zie ook</span><span class="sxs-lookup"><span data-stu-id="4fa99-128">See Also</span></span>

[<span data-ttu-id="4fa99-129">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="4fa99-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

[<span data-ttu-id="4fa99-130">Het element ExpressionBinding voor CustomItem voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="4fa99-130">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)
