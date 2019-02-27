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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846940"
---
# <a name="customitem-element-for-customentry-for-customcontrol-for-view-format"></a><span data-ttu-id="022e9-102">Het element CustomItem voor CustomEntry voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="022e9-102">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>

<span data-ttu-id="022e9-103">Bepaalt welke gegevens worden weergegeven in de weergave van het aangepaste besturingselement en hoe deze wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="022e9-103">Defines what data is displayed by the custom control view and how it is displayed.</span></span> <span data-ttu-id="022e9-104">Dit element wordt gebruikt bij het definiëren van een aangepast besturingselement-weergave.</span><span class="sxs-lookup"><span data-stu-id="022e9-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="022e9-105">Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) CustomControl Element (indeling) CustomEntries Element voor CustomControl voor weergave (indeling) CustomEntry Element voor CustomEntries voor weergave (indeling) CustomItem Element voor CustomEntry voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="022e9-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="022e9-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="022e9-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="022e9-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="022e9-107">Attributes and Elements</span></span>

<span data-ttu-id="022e9-108">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `CustomItem` element.</span><span class="sxs-lookup"><span data-stu-id="022e9-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="022e9-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="022e9-109">Attributes</span></span>

<span data-ttu-id="022e9-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="022e9-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="022e9-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="022e9-111">Child Elements</span></span>

|<span data-ttu-id="022e9-112">Element</span><span class="sxs-lookup"><span data-stu-id="022e9-112">Element</span></span>|<span data-ttu-id="022e9-113">Description</span><span class="sxs-lookup"><span data-stu-id="022e9-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="022e9-114">ExpressionBinding-Element voor CustomItem voor CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="022e9-114">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="022e9-115">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="022e9-115">Optional element.</span></span><br /><br /> <span data-ttu-id="022e9-116">Definieert de gegevens die door het besturingselement wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="022e9-116">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="022e9-117">Frame-Element voor CustomItem voor CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="022e9-117">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="022e9-118">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="022e9-118">Optional element.</span></span><br /><br /> <span data-ttu-id="022e9-119">Bepaalt welke gegevens worden weergegeven in de weergave van het aangepaste besturingselement en hoe deze wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="022e9-119">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|
|[<span data-ttu-id="022e9-120">Nieuwe regel-Element voor CustomItem voor aangepaste besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="022e9-120">NewLine Element for CustomItem for Custom Control for View (Format)</span></span>](./newline-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="022e9-121">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="022e9-121">Optional element.</span></span><br /><br /> <span data-ttu-id="022e9-122">Voegt een lege regel toe aan de weergave van het besturingselement.</span><span class="sxs-lookup"><span data-stu-id="022e9-122">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="022e9-123">Tekstelement voor CustomItem voor CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="022e9-123">Text Element for CustomItem for CustomControl for View (Format)</span></span>](./text-element-for-customitem-for-customview-for-view-format.md)|<span data-ttu-id="022e9-124">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="022e9-124">Optional element.</span></span><br /><br /> <span data-ttu-id="022e9-125">Hiermee geeft u aanvullende tekst in de gegevens die worden weergegeven door het besturingselement.</span><span class="sxs-lookup"><span data-stu-id="022e9-125">Specifies additional text to the data displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="022e9-126">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="022e9-126">Parent Elements</span></span>

|<span data-ttu-id="022e9-127">Element</span><span class="sxs-lookup"><span data-stu-id="022e9-127">Element</span></span>|<span data-ttu-id="022e9-128">Description</span><span class="sxs-lookup"><span data-stu-id="022e9-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="022e9-129">CustomEntry-Element voor CustomEntries voor CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="022e9-129">CustomEntry Element for CustomEntries for CustomControl for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="022e9-130">Bevat een definitie van de weergave van het aangepaste besturingselement.</span><span class="sxs-lookup"><span data-stu-id="022e9-130">Provides a definition of the custom control view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="022e9-131">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="022e9-131">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="022e9-132">Zie ook</span><span class="sxs-lookup"><span data-stu-id="022e9-132">See Also</span></span>

[<span data-ttu-id="022e9-133">CustomEntry-Element voor CustomEntries voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="022e9-133">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="022e9-134">ExpressionBinding-Element voor CustomItem voor CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="022e9-134">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="022e9-135">Frame-Element voor CustomItem voor CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="022e9-135">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="022e9-136">Nieuwe regel-Element voor CustomItem voor CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="022e9-136">NewLine Element for CustomItem for CustomControl for View (Format)</span></span>](./newline-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="022e9-137">Tekstelement voor CustomItem voor CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="022e9-137">Text Element for CustomItem for CustomControl for View (Format)</span></span>](./text-element-for-customitem-for-customview-for-view-format.md)

[<span data-ttu-id="022e9-138">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="022e9-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
