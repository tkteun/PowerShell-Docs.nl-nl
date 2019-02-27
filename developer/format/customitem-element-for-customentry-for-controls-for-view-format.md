---
title: CustomItem-Element voor CustomEntry voor besturingselementen voor weergave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33cb5350-73ef-4b79-a879-0edf051869e4
caps.latest.revision: 7
ms.openlocfilehash: 174ba6a14819f823ec39f72e49a626e781221d8c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846534"
---
# <a name="customitem-element-for-customentry-for-controls-for-view-format"></a><span data-ttu-id="b9218-102">Het element CustomItem voor CustomEntry voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="b9218-102">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>

<span data-ttu-id="b9218-103">Bepaalt welke gegevens worden weergegeven door het besturingselement en hoe deze wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="b9218-103">Defines what data is displayed by the control and how it is displayed.</span></span> <span data-ttu-id="b9218-104">Dit element wordt gebruikt bij het definiëren van besturingselementen die kunnen worden gebruikt door een weergave.</span><span class="sxs-lookup"><span data-stu-id="b9218-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="b9218-105">Configuratie-Element (indeling) ViewDefinitions-Element (indeling) weergave-Element (indeling) besturingselementen Element (indeling) controle-Element voor besturingselementen voor weergave (indeling) CustomControl Element voor de controle voor besturingselementen voor weergave (indeling) CustomEntries Element voor CustomControl voor weergave (indeling) CustomEntry Element voor CustomEntries voor besturingselementen voor weergave (indeling) CustomItem Element voor CustomEntry voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="b9218-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b9218-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="b9218-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...<Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b9218-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="b9218-107">Attributes and Elements</span></span>

<span data-ttu-id="b9218-108">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `CustomItem` element.</span><span class="sxs-lookup"><span data-stu-id="b9218-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span> <span data-ttu-id="b9218-109">Zie Opmerkingen voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b9218-109">For more information, see Remarks.</span></span>

### <a name="attributes"></a><span data-ttu-id="b9218-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="b9218-110">Attributes</span></span>

<span data-ttu-id="b9218-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="b9218-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b9218-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="b9218-112">Child Elements</span></span>

|<span data-ttu-id="b9218-113">Element</span><span class="sxs-lookup"><span data-stu-id="b9218-113">Element</span></span>|<span data-ttu-id="b9218-114">Description</span><span class="sxs-lookup"><span data-stu-id="b9218-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b9218-115">ExpressionBinding-Element voor CustomItem voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="b9218-115">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="b9218-116">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="b9218-116">Optional element.</span></span><br /><br /> <span data-ttu-id="b9218-117">Definieert de gegevens die door het besturingselement wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="b9218-117">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="b9218-118">Frame-Element voor CustomItem voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="b9218-118">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="b9218-119">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="b9218-119">Optional element.</span></span><br /><br /> <span data-ttu-id="b9218-120">Hiermee definieert u hoe de gegevens worden weergegeven, zoals de gegevens verschuiving naar links of rechts.</span><span class="sxs-lookup"><span data-stu-id="b9218-120">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|
|[<span data-ttu-id="b9218-121">Nieuwe regel-Element voor CustomItem voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="b9218-121">NewLine Element for CustomItem for Controls for View (Format)</span></span>](./newline-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="b9218-122">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="b9218-122">Optional element.</span></span><br /><br /> <span data-ttu-id="b9218-123">Voegt een lege regel toe aan de weergave van het besturingselement.</span><span class="sxs-lookup"><span data-stu-id="b9218-123">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="b9218-124">Tekstelement voor CustomItem voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="b9218-124">Text Element for CustomItem for Controls for View (Format)</span></span>](./text-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="b9218-125">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="b9218-125">Optional element.</span></span><br /><br /> <span data-ttu-id="b9218-126">Tekst, zoals tussen haakjes of vierkante haken, toegevoegd aan de weergave van het besturingselement.</span><span class="sxs-lookup"><span data-stu-id="b9218-126">Adds text, such as parentheses or brackets, to the display of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b9218-127">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="b9218-127">Parent Elements</span></span>

|<span data-ttu-id="b9218-128">Element</span><span class="sxs-lookup"><span data-stu-id="b9218-128">Element</span></span>|<span data-ttu-id="b9218-129">Description</span><span class="sxs-lookup"><span data-stu-id="b9218-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b9218-130">CustomEntry-Element voor CustomEntries voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="b9218-130">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="b9218-131">Bevat een definitie van het besturingselement.</span><span class="sxs-lookup"><span data-stu-id="b9218-131">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b9218-132">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="b9218-132">Remarks</span></span>

<span data-ttu-id="b9218-133">Bij het opgeven van de onderliggende elementen van de `CustomItem` -element, houd rekening met het volgende:</span><span class="sxs-lookup"><span data-stu-id="b9218-133">When specifying the child elements of the `CustomItem` element, keep the following in mind:</span></span>

- <span data-ttu-id="b9218-134">De onderliggende elementen moeten worden toegevoegd in de volgende volgorde: `ExpressionBinding`, `NewLine`, `Text`, en `Frame`.</span><span class="sxs-lookup"><span data-stu-id="b9218-134">The child elements must be added in the following sequence: `ExpressionBinding`, `NewLine`, `Text`, and `Frame`.</span></span>

- <span data-ttu-id="b9218-135">Er is geen maximale limiet voor het aantal reeksen die u kunt opgeven.</span><span class="sxs-lookup"><span data-stu-id="b9218-135">There is no maximum limit to the number of sequences that you can specify.</span></span>

- <span data-ttu-id="b9218-136">In elke volgorde hebben, er is geen maximale limiet voor het aantal `ExpressionBinding` elementen die u kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="b9218-136">In each sequence, there is no maximum limit to the number of `ExpressionBinding` elements that you can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="b9218-137">Zie ook</span><span class="sxs-lookup"><span data-stu-id="b9218-137">See Also</span></span>

[<span data-ttu-id="b9218-138">ExpressionBinding-Element voor CustomItem voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="b9218-138">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="b9218-139">Frame-Element voor CustomItem voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="b9218-139">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="b9218-140">Nieuwe regel-Element voor CustomItem voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="b9218-140">NewLine Element for CustomItem for Controls for View (Format)</span></span>](./newline-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="b9218-141">Tekstelement voor CustomItem voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="b9218-141">Text Element for CustomItem for Controls for View (Format)</span></span>](./text-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="b9218-142">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="b9218-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
