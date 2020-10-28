---
ms.date: 09/13/2016
ms.topic: reference
title: Het element CustomItem voor CustomEntry voor Besturingselementen voor Weergave (opmaak)
description: Het element CustomItem voor CustomEntry voor Besturingselementen voor Weergave (opmaak)
ms.openlocfilehash: 67bff97c27cfedf046b17eea438efcd66ae2ee4a
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92666753"
---
# <a name="customitem-element-for-customentry-for-controls-for-view-format"></a><span data-ttu-id="b5691-103">Het element CustomItem voor CustomEntry voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="b5691-103">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>

<span data-ttu-id="b5691-104">Hiermee definieert u welke gegevens worden weer gegeven door het besturings element en hoe deze worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="b5691-104">Defines what data is displayed by the control and how it is displayed.</span></span> <span data-ttu-id="b5691-105">Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.</span><span class="sxs-lookup"><span data-stu-id="b5691-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="b5691-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element (indeling) Controls element (Format) Controls-element voor besturings elementen voor weer gave (indeling) CustomControl-element voor besturings elementen voor de weer gave (Format) CustomEntries-element voor het element voor controle voor Controls voor de Control</span><span class="sxs-lookup"><span data-stu-id="b5691-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b5691-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="b5691-107">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...<Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b5691-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="b5691-108">Attributes and Elements</span></span>

<span data-ttu-id="b5691-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `CustomItem` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="b5691-109">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span> <span data-ttu-id="b5691-110">Zie Opmerkingen voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b5691-110">For more information, see Remarks.</span></span>

### <a name="attributes"></a><span data-ttu-id="b5691-111">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="b5691-111">Attributes</span></span>

<span data-ttu-id="b5691-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="b5691-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b5691-113">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="b5691-113">Child Elements</span></span>

|<span data-ttu-id="b5691-114">Element</span><span class="sxs-lookup"><span data-stu-id="b5691-114">Element</span></span>|<span data-ttu-id="b5691-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="b5691-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b5691-116">Het element ExpressionBinding voor CustomItem voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="b5691-116">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="b5691-117">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="b5691-117">Optional element.</span></span><br /><br /> <span data-ttu-id="b5691-118">Hiermee worden de gegevens gedefinieerd die door het besturings element worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="b5691-118">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="b5691-119">Het element Frame voor CustomItem voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="b5691-119">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="b5691-120">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="b5691-120">Optional element.</span></span><br /><br /> <span data-ttu-id="b5691-121">Hiermee definieert u hoe de gegevens worden weer gegeven, zoals de gegevens naar links of rechts verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="b5691-121">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|
|[<span data-ttu-id="b5691-122">Het element NewLine voor CustomItem voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="b5691-122">NewLine Element for CustomItem for Controls for View (Format)</span></span>](./newline-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="b5691-123">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="b5691-123">Optional element.</span></span><br /><br /> <span data-ttu-id="b5691-124">Hiermee voegt u een lege regel toe aan de weer gave van het besturings element.</span><span class="sxs-lookup"><span data-stu-id="b5691-124">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="b5691-125">Het element Tekst voor CustomItem voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="b5691-125">Text Element for CustomItem for Controls for View (Format)</span></span>](./text-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="b5691-126">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="b5691-126">Optional element.</span></span><br /><br /> <span data-ttu-id="b5691-127">Voegt tekst, zoals haakjes of haakjes, toe aan de weer gave van het besturings element.</span><span class="sxs-lookup"><span data-stu-id="b5691-127">Adds text, such as parentheses or brackets, to the display of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b5691-128">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="b5691-128">Parent Elements</span></span>

|<span data-ttu-id="b5691-129">Element</span><span class="sxs-lookup"><span data-stu-id="b5691-129">Element</span></span>|<span data-ttu-id="b5691-130">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="b5691-130">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b5691-131">Het element CustomEntry voor CustomEntries voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="b5691-131">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="b5691-132">Biedt een definitie van het besturings element.</span><span class="sxs-lookup"><span data-stu-id="b5691-132">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b5691-133">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="b5691-133">Remarks</span></span>

<span data-ttu-id="b5691-134">Wanneer u de onderliggende elementen van het `CustomItem` element opgeeft, houdt u het volgende in acht:</span><span class="sxs-lookup"><span data-stu-id="b5691-134">When specifying the child elements of the `CustomItem` element, keep the following in mind:</span></span>

- <span data-ttu-id="b5691-135">De onderliggende elementen moeten worden toegevoegd in de volgende volg orde:,, en `ExpressionBinding` `NewLine` `Text` `Frame` .</span><span class="sxs-lookup"><span data-stu-id="b5691-135">The child elements must be added in the following sequence: `ExpressionBinding`, `NewLine`, `Text`, and `Frame`.</span></span>

- <span data-ttu-id="b5691-136">Er is geen maximum limiet voor het aantal reeksen dat u kunt opgeven.</span><span class="sxs-lookup"><span data-stu-id="b5691-136">There is no maximum limit to the number of sequences that you can specify.</span></span>

- <span data-ttu-id="b5691-137">In elke reeks is er geen maximum limiet voor het aantal `ExpressionBinding` elementen dat u kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="b5691-137">In each sequence, there is no maximum limit to the number of `ExpressionBinding` elements that you can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="b5691-138">Zie ook</span><span class="sxs-lookup"><span data-stu-id="b5691-138">See Also</span></span>

[<span data-ttu-id="b5691-139">Het element ExpressionBinding voor CustomItem voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="b5691-139">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="b5691-140">Het element Frame voor CustomItem voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="b5691-140">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="b5691-141">Het element NewLine voor CustomItem voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="b5691-141">NewLine Element for CustomItem for Controls for View (Format)</span></span>](./newline-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="b5691-142">Het element Tekst voor CustomItem voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="b5691-142">Text Element for CustomItem for Controls for View (Format)</span></span>](./text-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="b5691-143">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="b5691-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
