---
ms.date: 09/13/2016
ms.topic: reference
title: Het element CustomItem voor CustomEntry voor Besturingselementen voor Configuratie (opmaak)
description: Het element CustomItem voor CustomEntry voor Besturingselementen voor Configuratie (opmaak)
ms.openlocfilehash: 06c399e982b6ac0fba9c11e20c468fe8bef6f694
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92666770"
---
# <a name="customitem-element-for-customentry-for-controls-for-configuration-format"></a><span data-ttu-id="522a5-103">Het element CustomItem voor CustomEntry voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="522a5-103">CustomItem Element for CustomEntry for Controls for Configuration (Format)</span></span>

<span data-ttu-id="522a5-104">Hiermee definieert u welke gegevens worden weer gegeven door het besturings element en hoe deze worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="522a5-104">Defines what data is displayed by the control and how it is displayed.</span></span> <span data-ttu-id="522a5-105">Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="522a5-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="522a5-106">Configuratie-element (Format) Controls element van configuratie (indeling) Control element voor besturings elementen voor configuratie (Format) CustomControl-element voor besturings element voor configuratie (indeling) CustomEntries element voor CustomControl voor configuratie (Format) CustomEntry-element voor het voor het configureren van configuratie (Format) CustomItem-element voor besturings elementen</span><span class="sxs-lookup"><span data-stu-id="522a5-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration</span></span>

## <a name="syntax"></a><span data-ttu-id="522a5-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="522a5-107">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...</Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="522a5-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="522a5-108">Attributes and Elements</span></span>

<span data-ttu-id="522a5-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `CustomItem` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="522a5-109">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span> <span data-ttu-id="522a5-110">Zie Opmerkingen voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="522a5-110">For more information, see Remarks.</span></span>

### <a name="attributes"></a><span data-ttu-id="522a5-111">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="522a5-111">Attributes</span></span>

<span data-ttu-id="522a5-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="522a5-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="522a5-113">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="522a5-113">Child Elements</span></span>

|<span data-ttu-id="522a5-114">Element</span><span class="sxs-lookup"><span data-stu-id="522a5-114">Element</span></span>|<span data-ttu-id="522a5-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="522a5-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="522a5-116">Het element ExpressionBinding voor CustomItem voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="522a5-116">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="522a5-117">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="522a5-117">Optional element.</span></span><br /><br /> <span data-ttu-id="522a5-118">Hiermee worden de gegevens gedefinieerd die door het besturings element worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="522a5-118">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="522a5-119">Het element Frame voor CustomItem voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="522a5-119">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="522a5-120">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="522a5-120">Optional element.</span></span><br /><br /> <span data-ttu-id="522a5-121">Hiermee definieert u hoe de gegevens worden weer gegeven, zoals de gegevens naar links of rechts verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="522a5-121">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|
|[<span data-ttu-id="522a5-122">Het element NewLine voor CustomItem voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="522a5-122">NewLine Element for CustomItem for Controls for Configuration (Format)</span></span>](./newline-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="522a5-123">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="522a5-123">Optional element.</span></span><br /><br /> <span data-ttu-id="522a5-124">Hiermee voegt u een lege regel toe aan de weer gave van het besturings element.</span><span class="sxs-lookup"><span data-stu-id="522a5-124">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="522a5-125">Het element Tekst voor CustomItem voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="522a5-125">Text Element for CustomItem for Controls for Configuration (Format)</span></span>](./text-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="522a5-126">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="522a5-126">Optional element.</span></span><br /><br /> <span data-ttu-id="522a5-127">Voegt tekst, zoals haakjes of haakjes, toe aan de weer gave van het besturings element.</span><span class="sxs-lookup"><span data-stu-id="522a5-127">Adds text, such as parentheses or brackets, to the display of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="522a5-128">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="522a5-128">Parent Elements</span></span>

|<span data-ttu-id="522a5-129">Element</span><span class="sxs-lookup"><span data-stu-id="522a5-129">Element</span></span>|<span data-ttu-id="522a5-130">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="522a5-130">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="522a5-131">Het element CustomEntry voor CustomControl voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="522a5-131">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="522a5-132">Biedt een definitie van het besturings element.</span><span class="sxs-lookup"><span data-stu-id="522a5-132">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="522a5-133">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="522a5-133">Remarks</span></span>

<span data-ttu-id="522a5-134">Wanneer u de onderliggende elementen van het `CustomItem` element opgeeft, houdt u het volgende in acht:</span><span class="sxs-lookup"><span data-stu-id="522a5-134">When specifying the child elements of the `CustomItem` element, keep the following in mind:</span></span>

- <span data-ttu-id="522a5-135">De onderliggende elementen moeten worden toegevoegd in de volgende volg orde:,, en `ExpressionBinding` `NewLine` `Text` `Frame` .</span><span class="sxs-lookup"><span data-stu-id="522a5-135">The child elements must be added in the following sequence: `ExpressionBinding`, `NewLine`, `Text`, and `Frame`.</span></span>

- <span data-ttu-id="522a5-136">Er is geen maximum limiet voor het aantal reeksen dat u kunt opgeven.</span><span class="sxs-lookup"><span data-stu-id="522a5-136">There is no maximum limit to the number of sequences that you can specify.</span></span>

- <span data-ttu-id="522a5-137">In elke reeks is er geen maximum limiet voor het aantal `ExpressionBinding` elementen dat u kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="522a5-137">In each sequence, there is no maximum limit to the number of `ExpressionBinding` elements that you can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="522a5-138">Zie ook</span><span class="sxs-lookup"><span data-stu-id="522a5-138">See Also</span></span>

[<span data-ttu-id="522a5-139">Het element ExpressionBinding voor CustomItem voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="522a5-139">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="522a5-140">Het element Frame voor CustomItem voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="522a5-140">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="522a5-141">Het element NewLine voor CustomItem voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="522a5-141">NewLine Element for CustomItem for Controls for Configuration (Format)</span></span>](./newline-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="522a5-142">Het element Tekst voor CustomItem voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="522a5-142">Text Element for CustomItem for Controls for Configuration (Format)</span></span>](./text-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="522a5-143">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="522a5-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
