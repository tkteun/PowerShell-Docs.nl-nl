---
title: CustomItem-Element voor CustomEntry voor besturingselementen voor de configuratie (-indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 73fb11ee-0ebd-477a-ac36-acdfbb32e70d
caps.latest.revision: 7
ms.openlocfilehash: bd0cb69770817ec215ddb1862a43a838baddefcf
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066427"
---
# <a name="customitem-element-for-customentry-for-controls-for-configuration-format"></a><span data-ttu-id="31cff-102">Het element CustomItem voor CustomEntry voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="31cff-102">CustomItem Element for CustomEntry for Controls for Configuration (Format)</span></span>

<span data-ttu-id="31cff-103">Bepaalt welke gegevens worden weergegeven door het besturingselement en hoe deze wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="31cff-103">Defines what data is displayed by the control and how it is displayed.</span></span> <span data-ttu-id="31cff-104">Dit element wordt gebruikt bij het definiëren van een algemene besturingselement dat kan worden gebruikt door alle weergaven in de opmaak-bestand.</span><span class="sxs-lookup"><span data-stu-id="31cff-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="31cff-105">Configuratie-Element (indeling) besturingselementen Element van configuratie (-indeling) besturingselement Element controles voor configuratie (-indeling) CustomControl-Element voor het besturingselement voor configuratie (-indeling) CustomEntries-Element voor CustomControl voor configuratie ( -Indeling) CustomEntry Element voor CustomControl controles voor configuratie (-indeling) CustomItem-Element voor CustomEntry voor besturingselementen voor configuratie</span><span class="sxs-lookup"><span data-stu-id="31cff-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration</span></span>

## <a name="syntax"></a><span data-ttu-id="31cff-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="31cff-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...</Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="31cff-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="31cff-107">Attributes and Elements</span></span>

<span data-ttu-id="31cff-108">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `CustomItem` element.</span><span class="sxs-lookup"><span data-stu-id="31cff-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span> <span data-ttu-id="31cff-109">Zie Opmerkingen voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="31cff-109">For more information, see Remarks.</span></span>

### <a name="attributes"></a><span data-ttu-id="31cff-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="31cff-110">Attributes</span></span>

<span data-ttu-id="31cff-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="31cff-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="31cff-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="31cff-112">Child Elements</span></span>

|<span data-ttu-id="31cff-113">Element</span><span class="sxs-lookup"><span data-stu-id="31cff-113">Element</span></span>|<span data-ttu-id="31cff-114">Description</span><span class="sxs-lookup"><span data-stu-id="31cff-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="31cff-115">ExpressionBinding-Element voor CustomItem voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="31cff-115">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="31cff-116">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="31cff-116">Optional element.</span></span><br /><br /> <span data-ttu-id="31cff-117">Definieert de gegevens die door het besturingselement wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="31cff-117">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="31cff-118">Frame-Element voor CustomItem voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="31cff-118">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="31cff-119">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="31cff-119">Optional element.</span></span><br /><br /> <span data-ttu-id="31cff-120">Hiermee definieert u hoe de gegevens worden weergegeven, zoals de gegevens verschuiving naar links of rechts.</span><span class="sxs-lookup"><span data-stu-id="31cff-120">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|
|[<span data-ttu-id="31cff-121">Nieuwe regel-Element voor CustomItem voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="31cff-121">NewLine Element for CustomItem for Controls for Configuration (Format)</span></span>](./newline-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="31cff-122">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="31cff-122">Optional element.</span></span><br /><br /> <span data-ttu-id="31cff-123">Voegt een lege regel toe aan de weergave van het besturingselement.</span><span class="sxs-lookup"><span data-stu-id="31cff-123">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="31cff-124">Tekstelement voor CustomItem voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="31cff-124">Text Element for CustomItem for Controls for Configuration (Format)</span></span>](./text-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="31cff-125">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="31cff-125">Optional element.</span></span><br /><br /> <span data-ttu-id="31cff-126">Tekst, zoals tussen haakjes of vierkante haken, toegevoegd aan de weergave van het besturingselement.</span><span class="sxs-lookup"><span data-stu-id="31cff-126">Adds text, such as parentheses or brackets, to the display of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="31cff-127">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="31cff-127">Parent Elements</span></span>

|<span data-ttu-id="31cff-128">Element</span><span class="sxs-lookup"><span data-stu-id="31cff-128">Element</span></span>|<span data-ttu-id="31cff-129">Description</span><span class="sxs-lookup"><span data-stu-id="31cff-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="31cff-130">CustomEntry-Element voor CustomControl voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="31cff-130">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="31cff-131">Bevat een definitie van het besturingselement.</span><span class="sxs-lookup"><span data-stu-id="31cff-131">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="31cff-132">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="31cff-132">Remarks</span></span>

<span data-ttu-id="31cff-133">Bij het opgeven van de onderliggende elementen van de `CustomItem` -element, houd rekening met het volgende:</span><span class="sxs-lookup"><span data-stu-id="31cff-133">When specifying the child elements of the `CustomItem` element, keep the following in mind:</span></span>

- <span data-ttu-id="31cff-134">De onderliggende elementen moeten worden toegevoegd in de volgende volgorde: `ExpressionBinding`, `NewLine`, `Text`, en `Frame`.</span><span class="sxs-lookup"><span data-stu-id="31cff-134">The child elements must be added in the following sequence: `ExpressionBinding`, `NewLine`, `Text`, and `Frame`.</span></span>

- <span data-ttu-id="31cff-135">Er is geen maximale limiet voor het aantal reeksen die u kunt opgeven.</span><span class="sxs-lookup"><span data-stu-id="31cff-135">There is no maximum limit to the number of sequences that you can specify.</span></span>

- <span data-ttu-id="31cff-136">In elke volgorde hebben, er is geen maximale limiet voor het aantal `ExpressionBinding` elementen die u kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="31cff-136">In each sequence, there is no maximum limit to the number of `ExpressionBinding` elements that you can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="31cff-137">Zie ook</span><span class="sxs-lookup"><span data-stu-id="31cff-137">See Also</span></span>

[<span data-ttu-id="31cff-138">ExpressionBinding-Element voor CustomItem voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="31cff-138">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="31cff-139">Frame-Element voor CustomItem voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="31cff-139">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="31cff-140">Nieuwe regel-Element voor CustomItem voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="31cff-140">NewLine Element for CustomItem for Controls for Configuration (Format)</span></span>](./newline-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="31cff-141">Tekstelement voor CustomItem voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="31cff-141">Text Element for CustomItem for Controls for Configuration (Format)</span></span>](./text-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="31cff-142">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="31cff-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
