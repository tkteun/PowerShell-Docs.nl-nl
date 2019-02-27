---
title: CustomItem-Element voor CustomEntry voor GroupBy (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f7c517aa-24f5-41ae-b82d-cb0fac81a245
caps.latest.revision: 7
ms.openlocfilehash: 2d821f5e3bc8d0f81ef8a8a040c6f9bcb1658bee
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847458"
---
# <a name="customitem-element-for-customentry-for-groupby-format"></a><span data-ttu-id="09741-102">Het element CustomItem voor CustomEntry voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="09741-102">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>

<span data-ttu-id="09741-103">Bepaalt welke gegevens worden weergegeven in de weergave van het aangepaste besturingselement en hoe deze wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="09741-103">Defines what data is displayed by the custom control view and how it is displayed.</span></span> <span data-ttu-id="09741-104">Dit element wordt gebruikt bij het definiëren van hoe een nieuwe groep objecten worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="09741-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="09741-105">Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) GroupBy Element voor weergave (indeling) CustomControl Element voor GroupBy (indeling) CustomEntries Element voor CustomControl voor GroupBy (indeling) CustomItem Element voor CustomEntry voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="09741-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="09741-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="09741-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="09741-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="09741-107">Attributes and Elements</span></span>

<span data-ttu-id="09741-108">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `CustomItem` element.</span><span class="sxs-lookup"><span data-stu-id="09741-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="09741-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="09741-109">Attributes</span></span>

<span data-ttu-id="09741-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="09741-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="09741-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="09741-111">Child Elements</span></span>

|<span data-ttu-id="09741-112">Element</span><span class="sxs-lookup"><span data-stu-id="09741-112">Element</span></span>|<span data-ttu-id="09741-113">Description</span><span class="sxs-lookup"><span data-stu-id="09741-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="09741-114">ExpressionBinding-Element voor CustomItem voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="09741-114">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="09741-115">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="09741-115">Optional element.</span></span><br /><br /> <span data-ttu-id="09741-116">Definieert de gegevens die door het besturingselement wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="09741-116">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="09741-117">Frame-Element voor CustomItem voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="09741-117">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="09741-118">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="09741-118">Optional element.</span></span><br /><br /> <span data-ttu-id="09741-119">Bepaalt welke gegevens worden weergegeven in de weergave van het aangepaste besturingselement en hoe deze wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="09741-119">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|
|[<span data-ttu-id="09741-120">Nieuwe regel-Element voor CustomItem voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="09741-120">NewLine Element for CustomItem for GroupBy (Format)</span></span>](./newline-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="09741-121">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="09741-121">Optional element.</span></span><br /><br /> <span data-ttu-id="09741-122">Voegt een lege regel toe aan de weergave van het besturingselement.</span><span class="sxs-lookup"><span data-stu-id="09741-122">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="09741-123">Tekstelement voor CustomItem voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="09741-123">Text Element for CustomItem for GroupBy (Format)</span></span>](./text-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="09741-124">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="09741-124">Optional element.</span></span><br /><br /> <span data-ttu-id="09741-125">Hiermee geeft u aanvullende tekst in de gegevens die worden weergegeven door het besturingselement.</span><span class="sxs-lookup"><span data-stu-id="09741-125">Specifies additional text to the data displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="09741-126">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="09741-126">Parent Elements</span></span>

|<span data-ttu-id="09741-127">Element</span><span class="sxs-lookup"><span data-stu-id="09741-127">Element</span></span>|<span data-ttu-id="09741-128">Description</span><span class="sxs-lookup"><span data-stu-id="09741-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="09741-129">CustomEntry-Element voor CustomControl voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="09741-129">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="09741-130">Bevat een definitie van de weergave van het aangepaste besturingselement.</span><span class="sxs-lookup"><span data-stu-id="09741-130">Provides a definition of the custom control view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="09741-131">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="09741-131">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="09741-132">Zie ook</span><span class="sxs-lookup"><span data-stu-id="09741-132">See Also</span></span>

[<span data-ttu-id="09741-133">CustomEntry-Element voor CustomControl voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="09741-133">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)

[<span data-ttu-id="09741-134">ExpressionBinding-Element voor CustomItem voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="09741-134">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="09741-135">Frame-Element voor CustomItem voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="09741-135">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="09741-136">Nieuwe regel-Element voor CustomItem voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="09741-136">NewLine Element for CustomItem for GroupBy (Format)</span></span>](./newline-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="09741-137">Tekstelement voor CustomItem voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="09741-137">Text Element for CustomItem for GroupBy (Format)</span></span>](./text-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="09741-138">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="09741-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
