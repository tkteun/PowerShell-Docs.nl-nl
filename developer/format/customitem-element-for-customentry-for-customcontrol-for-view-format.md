---
title: CustomItem-Element voor CustomEntry voor CustomControl voor weergave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 98708c1d-6f39-4a76-b454-31153a6ade8c
caps.latest.revision: 12
ms.openlocfilehash: 3c110bd5fe3ef2f790ef136556afa7c29d0b5b29
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066410"
---
# <a name="customitem-element-for-customentry-for-customcontrol-for-view-format"></a><span data-ttu-id="fa71d-102">Het element CustomItem voor CustomEntry voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="fa71d-102">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>

<span data-ttu-id="fa71d-103">Bepaalt welke gegevens worden weergegeven in de weergave van het aangepaste besturingselement en hoe deze wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="fa71d-103">Defines what data is displayed by the custom control view and how it is displayed.</span></span> <span data-ttu-id="fa71d-104">Dit element wordt gebruikt bij het definiëren van een aangepast besturingselement-weergave.</span><span class="sxs-lookup"><span data-stu-id="fa71d-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="fa71d-105">Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) CustomControl Element (indeling) CustomEntries Element voor CustomControl voor weergave (indeling) CustomEntry Element voor CustomEntries voor weergave (indeling) CustomItem Element voor CustomEntry voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="fa71d-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fa71d-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="fa71d-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fa71d-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="fa71d-107">Attributes and Elements</span></span>

<span data-ttu-id="fa71d-108">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `CustomItem` element.</span><span class="sxs-lookup"><span data-stu-id="fa71d-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="fa71d-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="fa71d-109">Attributes</span></span>

<span data-ttu-id="fa71d-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="fa71d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fa71d-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="fa71d-111">Child Elements</span></span>

|<span data-ttu-id="fa71d-112">Element</span><span class="sxs-lookup"><span data-stu-id="fa71d-112">Element</span></span>|<span data-ttu-id="fa71d-113">Description</span><span class="sxs-lookup"><span data-stu-id="fa71d-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fa71d-114">ExpressionBinding-Element voor CustomItem voor CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="fa71d-114">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="fa71d-115">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="fa71d-115">Optional element.</span></span><br /><br /> <span data-ttu-id="fa71d-116">Definieert de gegevens die door het besturingselement wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="fa71d-116">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="fa71d-117">Frame-Element voor CustomItem voor CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="fa71d-117">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="fa71d-118">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="fa71d-118">Optional element.</span></span><br /><br /> <span data-ttu-id="fa71d-119">Bepaalt welke gegevens worden weergegeven in de weergave van het aangepaste besturingselement en hoe deze wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="fa71d-119">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|
|[<span data-ttu-id="fa71d-120">Nieuwe regel-Element voor CustomItem voor aangepaste besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="fa71d-120">NewLine Element for CustomItem for Custom Control for View (Format)</span></span>](./newline-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="fa71d-121">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="fa71d-121">Optional element.</span></span><br /><br /> <span data-ttu-id="fa71d-122">Voegt een lege regel toe aan de weergave van het besturingselement.</span><span class="sxs-lookup"><span data-stu-id="fa71d-122">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="fa71d-123">Tekstelement voor CustomItem voor CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="fa71d-123">Text Element for CustomItem for CustomControl for View (Format)</span></span>](./text-element-for-customitem-for-customview-for-view-format.md)|<span data-ttu-id="fa71d-124">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="fa71d-124">Optional element.</span></span><br /><br /> <span data-ttu-id="fa71d-125">Hiermee geeft u aanvullende tekst in de gegevens die worden weergegeven door het besturingselement.</span><span class="sxs-lookup"><span data-stu-id="fa71d-125">Specifies additional text to the data displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="fa71d-126">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="fa71d-126">Parent Elements</span></span>

|<span data-ttu-id="fa71d-127">Element</span><span class="sxs-lookup"><span data-stu-id="fa71d-127">Element</span></span>|<span data-ttu-id="fa71d-128">Description</span><span class="sxs-lookup"><span data-stu-id="fa71d-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fa71d-129">CustomEntry-Element voor CustomEntries voor CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="fa71d-129">CustomEntry Element for CustomEntries for CustomControl for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="fa71d-130">Bevat een definitie van de weergave van het aangepaste besturingselement.</span><span class="sxs-lookup"><span data-stu-id="fa71d-130">Provides a definition of the custom control view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="fa71d-131">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="fa71d-131">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="fa71d-132">Zie ook</span><span class="sxs-lookup"><span data-stu-id="fa71d-132">See Also</span></span>

[<span data-ttu-id="fa71d-133">CustomEntry-Element voor CustomEntries voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="fa71d-133">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="fa71d-134">ExpressionBinding-Element voor CustomItem voor CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="fa71d-134">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="fa71d-135">Frame-Element voor CustomItem voor CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="fa71d-135">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="fa71d-136">Nieuwe regel-Element voor CustomItem voor CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="fa71d-136">NewLine Element for CustomItem for CustomControl for View (Format)</span></span>](./newline-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="fa71d-137">Tekstelement voor CustomItem voor CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="fa71d-137">Text Element for CustomItem for CustomControl for View (Format)</span></span>](./text-element-for-customitem-for-customview-for-view-format.md)

[<span data-ttu-id="fa71d-138">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="fa71d-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
