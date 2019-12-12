---
title: CustomItem-element voor CustomEntry voor besturings elementen voor configuratie (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 73fb11ee-0ebd-477a-ac36-acdfbb32e70d
caps.latest.revision: 7
ms.openlocfilehash: bd0cb69770817ec215ddb1862a43a838baddefcf
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72355242"
---
# <a name="customitem-element-for-customentry-for-controls-for-configuration-format"></a><span data-ttu-id="b7c7d-102">Het element CustomItem voor CustomEntry voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="b7c7d-102">CustomItem Element for CustomEntry for Controls for Configuration (Format)</span></span>

<span data-ttu-id="b7c7d-103">Hiermee definieert u welke gegevens worden weer gegeven door het besturings element en hoe deze worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="b7c7d-103">Defines what data is displayed by the control and how it is displayed.</span></span> <span data-ttu-id="b7c7d-104">Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="b7c7d-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="b7c7d-105">Configuratie-element (Format) Controls element van configuratie (Format) Control element voor besturings elementen voor configuratie (Format) CustomControl-element voor Control for Configuration (Format) CustomEntries element voor het configureren van een configuratie ( Format) CustomEntry element voor CustomControl voor besturings elementen voor configuratie (indeling) CustomItem-element voor CustomEntry voor configuratie besturings elementen</span><span class="sxs-lookup"><span data-stu-id="b7c7d-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration</span></span>

## <a name="syntax"></a><span data-ttu-id="b7c7d-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="b7c7d-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...</Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b7c7d-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="b7c7d-107">Attributes and Elements</span></span>

<span data-ttu-id="b7c7d-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `CustomItem` beschreven.</span><span class="sxs-lookup"><span data-stu-id="b7c7d-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span> <span data-ttu-id="b7c7d-109">Zie Opmerkingen voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b7c7d-109">For more information, see Remarks.</span></span>

### <a name="attributes"></a><span data-ttu-id="b7c7d-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="b7c7d-110">Attributes</span></span>

<span data-ttu-id="b7c7d-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="b7c7d-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b7c7d-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="b7c7d-112">Child Elements</span></span>

|<span data-ttu-id="b7c7d-113">Element</span><span class="sxs-lookup"><span data-stu-id="b7c7d-113">Element</span></span>|<span data-ttu-id="b7c7d-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="b7c7d-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b7c7d-115">ExpressionBinding-element voor CustomItem voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="b7c7d-115">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="b7c7d-116">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="b7c7d-116">Optional element.</span></span><br /><br /> <span data-ttu-id="b7c7d-117">Hiermee worden de gegevens gedefinieerd die door het besturings element worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="b7c7d-117">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="b7c7d-118">Frame-element voor CustomItem voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="b7c7d-118">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="b7c7d-119">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="b7c7d-119">Optional element.</span></span><br /><br /> <span data-ttu-id="b7c7d-120">Hiermee definieert u hoe de gegevens worden weer gegeven, zoals de gegevens naar links of rechts verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="b7c7d-120">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|
|[<span data-ttu-id="b7c7d-121">Element nieuwe regel voor CustomItem voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="b7c7d-121">NewLine Element for CustomItem for Controls for Configuration (Format)</span></span>](./newline-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="b7c7d-122">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="b7c7d-122">Optional element.</span></span><br /><br /> <span data-ttu-id="b7c7d-123">Hiermee voegt u een lege regel toe aan de weer gave van het besturings element.</span><span class="sxs-lookup"><span data-stu-id="b7c7d-123">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="b7c7d-124">Tekst element voor CustomItem voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="b7c7d-124">Text Element for CustomItem for Controls for Configuration (Format)</span></span>](./text-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="b7c7d-125">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="b7c7d-125">Optional element.</span></span><br /><br /> <span data-ttu-id="b7c7d-126">Voegt tekst, zoals haakjes of haakjes, toe aan de weer gave van het besturings element.</span><span class="sxs-lookup"><span data-stu-id="b7c7d-126">Adds text, such as parentheses or brackets, to the display of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b7c7d-127">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="b7c7d-127">Parent Elements</span></span>

|<span data-ttu-id="b7c7d-128">Element</span><span class="sxs-lookup"><span data-stu-id="b7c7d-128">Element</span></span>|<span data-ttu-id="b7c7d-129">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="b7c7d-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b7c7d-130">CustomEntry-element voor CustomControl voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="b7c7d-130">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="b7c7d-131">Biedt een definitie van het besturings element.</span><span class="sxs-lookup"><span data-stu-id="b7c7d-131">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b7c7d-132">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="b7c7d-132">Remarks</span></span>

<span data-ttu-id="b7c7d-133">Houd bij het opgeven van de onderliggende elementen van het element `CustomItem` het volgende in acht:</span><span class="sxs-lookup"><span data-stu-id="b7c7d-133">When specifying the child elements of the `CustomItem` element, keep the following in mind:</span></span>

- <span data-ttu-id="b7c7d-134">De onderliggende elementen moeten worden toegevoegd in de volgende volg orde: `ExpressionBinding`, `NewLine`, `Text`en `Frame`.</span><span class="sxs-lookup"><span data-stu-id="b7c7d-134">The child elements must be added in the following sequence: `ExpressionBinding`, `NewLine`, `Text`, and `Frame`.</span></span>

- <span data-ttu-id="b7c7d-135">Er is geen maximum limiet voor het aantal reeksen dat u kunt opgeven.</span><span class="sxs-lookup"><span data-stu-id="b7c7d-135">There is no maximum limit to the number of sequences that you can specify.</span></span>

- <span data-ttu-id="b7c7d-136">In elke reeks is er geen maximum limiet voor het aantal `ExpressionBinding` elementen dat u kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="b7c7d-136">In each sequence, there is no maximum limit to the number of `ExpressionBinding` elements that you can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="b7c7d-137">Zie ook</span><span class="sxs-lookup"><span data-stu-id="b7c7d-137">See Also</span></span>

[<span data-ttu-id="b7c7d-138">ExpressionBinding-element voor CustomItem voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="b7c7d-138">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="b7c7d-139">Frame-element voor CustomItem voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="b7c7d-139">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="b7c7d-140">Element nieuwe regel voor CustomItem voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="b7c7d-140">NewLine Element for CustomItem for Controls for Configuration (Format)</span></span>](./newline-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="b7c7d-141">Tekst element voor CustomItem voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="b7c7d-141">Text Element for CustomItem for Controls for Configuration (Format)</span></span>](./text-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="b7c7d-142">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="b7c7d-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
