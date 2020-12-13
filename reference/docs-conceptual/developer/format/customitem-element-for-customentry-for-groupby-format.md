---
ms.date: 09/13/2016
ms.topic: reference
title: Het element CustomItem voor CustomEntry voor GroupBy (opmaak)
description: Het element CustomItem voor CustomEntry voor GroupBy (opmaak)
ms.openlocfilehash: 5db23ad4dad5bd66ea64b9c6e91b8224a4aa4eca
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645991"
---
# <a name="customitem-element-for-customentry-for-groupby-format"></a><span data-ttu-id="606a2-103">Het element CustomItem voor CustomEntry voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="606a2-103">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>

<span data-ttu-id="606a2-104">Hiermee definieert u welke gegevens worden weer gegeven in de weer gave van het aangepaste besturings element en hoe deze worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="606a2-104">Defines what data is displayed by the custom control view and how it is displayed.</span></span> <span data-ttu-id="606a2-105">Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="606a2-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="606a2-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element voor weer gave (indeling) GroupBy-element voor weer gave (opmaak) CustomControl-element voor het element GroupBy (indeling) CustomEntries voor CustomControl voor GroupBy (Format) CustomItem-element voor de CustomEntry voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="606a2-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="606a2-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="606a2-107">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="606a2-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="606a2-108">Attributes and Elements</span></span>

<span data-ttu-id="606a2-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `CustomItem` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="606a2-109">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="606a2-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="606a2-110">Attributes</span></span>

<span data-ttu-id="606a2-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="606a2-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="606a2-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="606a2-112">Child Elements</span></span>

|<span data-ttu-id="606a2-113">Element</span><span class="sxs-lookup"><span data-stu-id="606a2-113">Element</span></span>|<span data-ttu-id="606a2-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="606a2-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="606a2-115">Het element ExpressionBinding voor CustomItem voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="606a2-115">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="606a2-116">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="606a2-116">Optional element.</span></span><br /><br /> <span data-ttu-id="606a2-117">Hiermee worden de gegevens gedefinieerd die door het besturings element worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="606a2-117">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="606a2-118">Het element Frame voor CustomItem voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="606a2-118">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="606a2-119">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="606a2-119">Optional element.</span></span><br /><br /> <span data-ttu-id="606a2-120">Hiermee definieert u welke gegevens worden weer gegeven in de weer gave van het aangepaste besturings element en hoe deze worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="606a2-120">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|
|[<span data-ttu-id="606a2-121">Het element NewLine voor CustomItem voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="606a2-121">NewLine Element for CustomItem for GroupBy (Format)</span></span>](./newline-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="606a2-122">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="606a2-122">Optional element.</span></span><br /><br /> <span data-ttu-id="606a2-123">Hiermee voegt u een lege regel toe aan de weer gave van het besturings element.</span><span class="sxs-lookup"><span data-stu-id="606a2-123">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="606a2-124">Het element Tekst voor CustomItem voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="606a2-124">Text Element for CustomItem for GroupBy (Format)</span></span>](./text-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="606a2-125">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="606a2-125">Optional element.</span></span><br /><br /> <span data-ttu-id="606a2-126">Hiermee geeft u aanvullende tekst op voor de gegevens die door het besturings element worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="606a2-126">Specifies additional text to the data displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="606a2-127">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="606a2-127">Parent Elements</span></span>

|<span data-ttu-id="606a2-128">Element</span><span class="sxs-lookup"><span data-stu-id="606a2-128">Element</span></span>|<span data-ttu-id="606a2-129">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="606a2-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="606a2-130">Het element CustomEntry voor CustomControl voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="606a2-130">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="606a2-131">Biedt een definitie van de aangepaste beheer weergave.</span><span class="sxs-lookup"><span data-stu-id="606a2-131">Provides a definition of the custom control view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="606a2-132">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="606a2-132">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="606a2-133">Zie ook</span><span class="sxs-lookup"><span data-stu-id="606a2-133">See Also</span></span>

[<span data-ttu-id="606a2-134">Het element CustomEntry voor CustomControl voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="606a2-134">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)

[<span data-ttu-id="606a2-135">Het element ExpressionBinding voor CustomItem voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="606a2-135">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="606a2-136">Het element Frame voor CustomItem voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="606a2-136">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="606a2-137">Het element NewLine voor CustomItem voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="606a2-137">NewLine Element for CustomItem for GroupBy (Format)</span></span>](./newline-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="606a2-138">Het element Tekst voor CustomItem voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="606a2-138">Text Element for CustomItem for GroupBy (Format)</span></span>](./text-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="606a2-139">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="606a2-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
