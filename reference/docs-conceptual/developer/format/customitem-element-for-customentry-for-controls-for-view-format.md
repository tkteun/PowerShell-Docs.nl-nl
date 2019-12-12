---
title: CustomItem-element voor CustomEntry voor besturings elementen voor weer gave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33cb5350-73ef-4b79-a879-0edf051869e4
caps.latest.revision: 7
ms.openlocfilehash: 174ba6a14819f823ec39f72e49a626e781221d8c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72355179"
---
# <a name="customitem-element-for-customentry-for-controls-for-view-format"></a><span data-ttu-id="c953a-102">Het element CustomItem voor CustomEntry voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c953a-102">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>

<span data-ttu-id="c953a-103">Hiermee definieert u welke gegevens worden weer gegeven door het besturings element en hoe deze worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c953a-103">Defines what data is displayed by the control and how it is displayed.</span></span> <span data-ttu-id="c953a-104">Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.</span><span class="sxs-lookup"><span data-stu-id="c953a-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="c953a-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) Controls-element (Format) Control element (opmaak) voor besturings elementen voor de weer gave (indeling) CustomControl-element voor besturings elementen voor Controls (Format) CustomEntries element voor CustomControl voor View (Format) CustomEntry-element voor CustomEntries voor besturings elementen voor de weer gave (Format) CustomItem-element voor CustomEntry voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="c953a-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c953a-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="c953a-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...<Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c953a-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="c953a-107">Attributes and Elements</span></span>

<span data-ttu-id="c953a-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `CustomItem` beschreven.</span><span class="sxs-lookup"><span data-stu-id="c953a-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span> <span data-ttu-id="c953a-109">Zie Opmerkingen voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c953a-109">For more information, see Remarks.</span></span>

### <a name="attributes"></a><span data-ttu-id="c953a-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="c953a-110">Attributes</span></span>

<span data-ttu-id="c953a-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="c953a-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c953a-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="c953a-112">Child Elements</span></span>

|<span data-ttu-id="c953a-113">Element</span><span class="sxs-lookup"><span data-stu-id="c953a-113">Element</span></span>|<span data-ttu-id="c953a-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="c953a-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c953a-115">ExpressionBinding-element voor CustomItem voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="c953a-115">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="c953a-116">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="c953a-116">Optional element.</span></span><br /><br /> <span data-ttu-id="c953a-117">Hiermee worden de gegevens gedefinieerd die door het besturings element worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c953a-117">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="c953a-118">Frame-element voor CustomItem voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="c953a-118">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="c953a-119">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="c953a-119">Optional element.</span></span><br /><br /> <span data-ttu-id="c953a-120">Hiermee definieert u hoe de gegevens worden weer gegeven, zoals de gegevens naar links of rechts verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="c953a-120">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|
|[<span data-ttu-id="c953a-121">Element nieuwe regel voor CustomItem voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="c953a-121">NewLine Element for CustomItem for Controls for View (Format)</span></span>](./newline-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="c953a-122">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="c953a-122">Optional element.</span></span><br /><br /> <span data-ttu-id="c953a-123">Hiermee voegt u een lege regel toe aan de weer gave van het besturings element.</span><span class="sxs-lookup"><span data-stu-id="c953a-123">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="c953a-124">Tekst element voor CustomItem voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="c953a-124">Text Element for CustomItem for Controls for View (Format)</span></span>](./text-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="c953a-125">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="c953a-125">Optional element.</span></span><br /><br /> <span data-ttu-id="c953a-126">Voegt tekst, zoals haakjes of haakjes, toe aan de weer gave van het besturings element.</span><span class="sxs-lookup"><span data-stu-id="c953a-126">Adds text, such as parentheses or brackets, to the display of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c953a-127">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="c953a-127">Parent Elements</span></span>

|<span data-ttu-id="c953a-128">Element</span><span class="sxs-lookup"><span data-stu-id="c953a-128">Element</span></span>|<span data-ttu-id="c953a-129">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="c953a-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c953a-130">CustomEntry-element voor CustomEntries voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="c953a-130">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="c953a-131">Biedt een definitie van het besturings element.</span><span class="sxs-lookup"><span data-stu-id="c953a-131">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c953a-132">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="c953a-132">Remarks</span></span>

<span data-ttu-id="c953a-133">Houd bij het opgeven van de onderliggende elementen van het element `CustomItem` het volgende in acht:</span><span class="sxs-lookup"><span data-stu-id="c953a-133">When specifying the child elements of the `CustomItem` element, keep the following in mind:</span></span>

- <span data-ttu-id="c953a-134">De onderliggende elementen moeten worden toegevoegd in de volgende volg orde: `ExpressionBinding`, `NewLine`, `Text`en `Frame`.</span><span class="sxs-lookup"><span data-stu-id="c953a-134">The child elements must be added in the following sequence: `ExpressionBinding`, `NewLine`, `Text`, and `Frame`.</span></span>

- <span data-ttu-id="c953a-135">Er is geen maximum limiet voor het aantal reeksen dat u kunt opgeven.</span><span class="sxs-lookup"><span data-stu-id="c953a-135">There is no maximum limit to the number of sequences that you can specify.</span></span>

- <span data-ttu-id="c953a-136">In elke reeks is er geen maximum limiet voor het aantal `ExpressionBinding` elementen dat u kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="c953a-136">In each sequence, there is no maximum limit to the number of `ExpressionBinding` elements that you can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="c953a-137">Zie ook</span><span class="sxs-lookup"><span data-stu-id="c953a-137">See Also</span></span>

[<span data-ttu-id="c953a-138">ExpressionBinding-element voor CustomItem voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="c953a-138">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="c953a-139">Frame-element voor CustomItem voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="c953a-139">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="c953a-140">Element nieuwe regel voor CustomItem voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="c953a-140">NewLine Element for CustomItem for Controls for View (Format)</span></span>](./newline-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="c953a-141">Tekst element voor CustomItem voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="c953a-141">Text Element for CustomItem for Controls for View (Format)</span></span>](./text-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="c953a-142">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="c953a-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
