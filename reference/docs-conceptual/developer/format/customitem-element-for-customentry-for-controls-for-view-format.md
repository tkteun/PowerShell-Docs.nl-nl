---
title: CustomItem-element voor CustomEntry voor besturings elementen voor weer gave (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 747ea14e7118be62ebee00e7d80af2dccb5c8353
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785843"
---
# <a name="customitem-element-for-customentry-for-controls-for-view-format"></a><span data-ttu-id="73830-102">Het element CustomItem voor CustomEntry voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="73830-102">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>

<span data-ttu-id="73830-103">Hiermee definieert u welke gegevens worden weer gegeven door het besturings element en hoe deze worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="73830-103">Defines what data is displayed by the control and how it is displayed.</span></span> <span data-ttu-id="73830-104">Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.</span><span class="sxs-lookup"><span data-stu-id="73830-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="73830-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element (indeling) Controls element (Format) Controls-element voor besturings elementen voor weer gave (indeling) CustomControl-element voor besturings elementen voor de weer gave (Format) CustomEntries-element voor het element voor controle voor Controls voor de Control</span><span class="sxs-lookup"><span data-stu-id="73830-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="73830-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="73830-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...<Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="73830-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="73830-107">Attributes and Elements</span></span>

<span data-ttu-id="73830-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `CustomItem` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="73830-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span> <span data-ttu-id="73830-109">Zie Opmerkingen voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="73830-109">For more information, see Remarks.</span></span>

### <a name="attributes"></a><span data-ttu-id="73830-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="73830-110">Attributes</span></span>

<span data-ttu-id="73830-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="73830-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="73830-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="73830-112">Child Elements</span></span>

|<span data-ttu-id="73830-113">Element</span><span class="sxs-lookup"><span data-stu-id="73830-113">Element</span></span>|<span data-ttu-id="73830-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="73830-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="73830-115">Het element ExpressionBinding voor CustomItem voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="73830-115">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="73830-116">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="73830-116">Optional element.</span></span><br /><br /> <span data-ttu-id="73830-117">Hiermee worden de gegevens gedefinieerd die door het besturings element worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="73830-117">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="73830-118">Het element Frame voor CustomItem voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="73830-118">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="73830-119">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="73830-119">Optional element.</span></span><br /><br /> <span data-ttu-id="73830-120">Hiermee definieert u hoe de gegevens worden weer gegeven, zoals de gegevens naar links of rechts verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="73830-120">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|
|[<span data-ttu-id="73830-121">Het element NewLine voor CustomItem voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="73830-121">NewLine Element for CustomItem for Controls for View (Format)</span></span>](./newline-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="73830-122">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="73830-122">Optional element.</span></span><br /><br /> <span data-ttu-id="73830-123">Hiermee voegt u een lege regel toe aan de weer gave van het besturings element.</span><span class="sxs-lookup"><span data-stu-id="73830-123">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="73830-124">Het element Tekst voor CustomItem voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="73830-124">Text Element for CustomItem for Controls for View (Format)</span></span>](./text-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="73830-125">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="73830-125">Optional element.</span></span><br /><br /> <span data-ttu-id="73830-126">Voegt tekst, zoals haakjes of haakjes, toe aan de weer gave van het besturings element.</span><span class="sxs-lookup"><span data-stu-id="73830-126">Adds text, such as parentheses or brackets, to the display of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="73830-127">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="73830-127">Parent Elements</span></span>

|<span data-ttu-id="73830-128">Element</span><span class="sxs-lookup"><span data-stu-id="73830-128">Element</span></span>|<span data-ttu-id="73830-129">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="73830-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="73830-130">Het element CustomEntry voor CustomEntries voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="73830-130">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="73830-131">Biedt een definitie van het besturings element.</span><span class="sxs-lookup"><span data-stu-id="73830-131">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="73830-132">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="73830-132">Remarks</span></span>

<span data-ttu-id="73830-133">Wanneer u de onderliggende elementen van het `CustomItem` element opgeeft, houdt u het volgende in acht:</span><span class="sxs-lookup"><span data-stu-id="73830-133">When specifying the child elements of the `CustomItem` element, keep the following in mind:</span></span>

- <span data-ttu-id="73830-134">De onderliggende elementen moeten worden toegevoegd in de volgende volg orde:,, en `ExpressionBinding` `NewLine` `Text` `Frame` .</span><span class="sxs-lookup"><span data-stu-id="73830-134">The child elements must be added in the following sequence: `ExpressionBinding`, `NewLine`, `Text`, and `Frame`.</span></span>

- <span data-ttu-id="73830-135">Er is geen maximum limiet voor het aantal reeksen dat u kunt opgeven.</span><span class="sxs-lookup"><span data-stu-id="73830-135">There is no maximum limit to the number of sequences that you can specify.</span></span>

- <span data-ttu-id="73830-136">In elke reeks is er geen maximum limiet voor het aantal `ExpressionBinding` elementen dat u kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="73830-136">In each sequence, there is no maximum limit to the number of `ExpressionBinding` elements that you can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="73830-137">Zie ook</span><span class="sxs-lookup"><span data-stu-id="73830-137">See Also</span></span>

[<span data-ttu-id="73830-138">Het element ExpressionBinding voor CustomItem voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="73830-138">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="73830-139">Het element Frame voor CustomItem voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="73830-139">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="73830-140">Het element NewLine voor CustomItem voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="73830-140">NewLine Element for CustomItem for Controls for View (Format)</span></span>](./newline-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="73830-141">Het element Tekst voor CustomItem voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="73830-141">Text Element for CustomItem for Controls for View (Format)</span></span>](./text-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="73830-142">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="73830-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
