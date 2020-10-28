---
ms.date: 09/13/2016
ms.topic: reference
title: Het element CustomItem voor CustomEntry voor CustomControl voor Weergave (opmaak)
description: Het element CustomItem voor CustomEntry voor CustomControl voor Weergave (opmaak)
ms.openlocfilehash: 9090a3ada5316ba5ddb4a9c46eee37c11982ae6e
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92666736"
---
# <a name="customitem-element-for-customentry-for-customcontrol-for-view-format"></a><span data-ttu-id="063c7-103">Het element CustomItem voor CustomEntry voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="063c7-103">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>

<span data-ttu-id="063c7-104">Hiermee definieert u welke gegevens worden weer gegeven in de weer gave van het aangepaste besturings element en hoe deze worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="063c7-104">Defines what data is displayed by the custom control view and how it is displayed.</span></span> <span data-ttu-id="063c7-105">Dit element wordt gebruikt bij het definiëren van een aangepaste beheer weergave.</span><span class="sxs-lookup"><span data-stu-id="063c7-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="063c7-106">Configuratie-element (indeling) ViewDefinitions element (indeling) weer gave element (indeling) CustomControl element (Format) CustomEntries element voor CustomControl voor weer gave (Format) CustomEntry-element voor CustomEntries voor weer gave (Format) CustomItem element voor CustomEntry voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="063c7-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="063c7-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="063c7-107">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="063c7-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="063c7-108">Attributes and Elements</span></span>

<span data-ttu-id="063c7-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `CustomItem` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="063c7-109">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="063c7-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="063c7-110">Attributes</span></span>

<span data-ttu-id="063c7-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="063c7-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="063c7-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="063c7-112">Child Elements</span></span>

|<span data-ttu-id="063c7-113">Element</span><span class="sxs-lookup"><span data-stu-id="063c7-113">Element</span></span>|<span data-ttu-id="063c7-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="063c7-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="063c7-115">Het element ExpressionBinding voor CustomItem voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="063c7-115">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="063c7-116">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="063c7-116">Optional element.</span></span><br /><br /> <span data-ttu-id="063c7-117">Hiermee worden de gegevens gedefinieerd die door het besturings element worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="063c7-117">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="063c7-118">Het element Frame voor CustomItem voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="063c7-118">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="063c7-119">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="063c7-119">Optional element.</span></span><br /><br /> <span data-ttu-id="063c7-120">Hiermee definieert u welke gegevens worden weer gegeven in de weer gave van het aangepaste besturings element en hoe deze worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="063c7-120">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|
|[<span data-ttu-id="063c7-121">Element nieuwe regel voor CustomItem voor aangepast besturings element voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="063c7-121">NewLine Element for CustomItem for Custom Control for View (Format)</span></span>](./newline-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="063c7-122">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="063c7-122">Optional element.</span></span><br /><br /> <span data-ttu-id="063c7-123">Hiermee voegt u een lege regel toe aan de weer gave van het besturings element.</span><span class="sxs-lookup"><span data-stu-id="063c7-123">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="063c7-124">Tekst element voor CustomItem voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="063c7-124">Text Element for CustomItem for CustomControl for View (Format)</span></span>](./text-element-for-customitem-for-customview-for-view-format.md)|<span data-ttu-id="063c7-125">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="063c7-125">Optional element.</span></span><br /><br /> <span data-ttu-id="063c7-126">Hiermee geeft u aanvullende tekst op voor de gegevens die door het besturings element worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="063c7-126">Specifies additional text to the data displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="063c7-127">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="063c7-127">Parent Elements</span></span>

|<span data-ttu-id="063c7-128">Element</span><span class="sxs-lookup"><span data-stu-id="063c7-128">Element</span></span>|<span data-ttu-id="063c7-129">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="063c7-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="063c7-130">Het element CustomEntry voor CustomEntries voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="063c7-130">CustomEntry Element for CustomEntries for CustomControl for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="063c7-131">Biedt een definitie van de aangepaste beheer weergave.</span><span class="sxs-lookup"><span data-stu-id="063c7-131">Provides a definition of the custom control view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="063c7-132">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="063c7-132">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="063c7-133">Zie ook</span><span class="sxs-lookup"><span data-stu-id="063c7-133">See Also</span></span>

[<span data-ttu-id="063c7-134">CustomEntry-element voor CustomEntries voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="063c7-134">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="063c7-135">Het element ExpressionBinding voor CustomItem voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="063c7-135">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="063c7-136">Het element Frame voor CustomItem voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="063c7-136">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="063c7-137">Het element NewLine voor CustomItem voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="063c7-137">NewLine Element for CustomItem for CustomControl for View (Format)</span></span>](./newline-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="063c7-138">Tekst element voor CustomItem voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="063c7-138">Text Element for CustomItem for CustomControl for View (Format)</span></span>](./text-element-for-customitem-for-customview-for-view-format.md)

[<span data-ttu-id="063c7-139">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="063c7-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
