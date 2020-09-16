---
title: CustomItem-element voor CustomEntry voor GroupBy (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e8086c5330b6644f83316ad4ae33c33ba40d9eee
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783718"
---
# <a name="customitem-element-for-customentry-for-groupby-format"></a><span data-ttu-id="5550a-102">Het element CustomItem voor CustomEntry voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="5550a-102">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>

<span data-ttu-id="5550a-103">Hiermee definieert u welke gegevens worden weer gegeven in de weer gave van het aangepaste besturings element en hoe deze worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="5550a-103">Defines what data is displayed by the custom control view and how it is displayed.</span></span> <span data-ttu-id="5550a-104">Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="5550a-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="5550a-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element voor weer gave (indeling) GroupBy-element voor weer gave (opmaak) CustomControl-element voor het element GroupBy (indeling) CustomEntries voor CustomControl voor GroupBy (Format) CustomItem-element voor de CustomEntry voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="5550a-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5550a-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="5550a-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5550a-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="5550a-107">Attributes and Elements</span></span>

<span data-ttu-id="5550a-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `CustomItem` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="5550a-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5550a-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="5550a-109">Attributes</span></span>

<span data-ttu-id="5550a-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="5550a-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5550a-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="5550a-111">Child Elements</span></span>

|<span data-ttu-id="5550a-112">Element</span><span class="sxs-lookup"><span data-stu-id="5550a-112">Element</span></span>|<span data-ttu-id="5550a-113">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="5550a-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5550a-114">Het element ExpressionBinding voor CustomItem voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="5550a-114">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="5550a-115">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="5550a-115">Optional element.</span></span><br /><br /> <span data-ttu-id="5550a-116">Hiermee worden de gegevens gedefinieerd die door het besturings element worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="5550a-116">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="5550a-117">Het element Frame voor CustomItem voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="5550a-117">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="5550a-118">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="5550a-118">Optional element.</span></span><br /><br /> <span data-ttu-id="5550a-119">Hiermee definieert u welke gegevens worden weer gegeven in de weer gave van het aangepaste besturings element en hoe deze worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="5550a-119">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|
|[<span data-ttu-id="5550a-120">Het element NewLine voor CustomItem voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="5550a-120">NewLine Element for CustomItem for GroupBy (Format)</span></span>](./newline-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="5550a-121">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="5550a-121">Optional element.</span></span><br /><br /> <span data-ttu-id="5550a-122">Hiermee voegt u een lege regel toe aan de weer gave van het besturings element.</span><span class="sxs-lookup"><span data-stu-id="5550a-122">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="5550a-123">Het element Tekst voor CustomItem voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="5550a-123">Text Element for CustomItem for GroupBy (Format)</span></span>](./text-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="5550a-124">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="5550a-124">Optional element.</span></span><br /><br /> <span data-ttu-id="5550a-125">Hiermee geeft u aanvullende tekst op voor de gegevens die door het besturings element worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="5550a-125">Specifies additional text to the data displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="5550a-126">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="5550a-126">Parent Elements</span></span>

|<span data-ttu-id="5550a-127">Element</span><span class="sxs-lookup"><span data-stu-id="5550a-127">Element</span></span>|<span data-ttu-id="5550a-128">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="5550a-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5550a-129">Het element CustomEntry voor CustomControl voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="5550a-129">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="5550a-130">Biedt een definitie van de aangepaste beheer weergave.</span><span class="sxs-lookup"><span data-stu-id="5550a-130">Provides a definition of the custom control view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5550a-131">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="5550a-131">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="5550a-132">Zie ook</span><span class="sxs-lookup"><span data-stu-id="5550a-132">See Also</span></span>

[<span data-ttu-id="5550a-133">Het element CustomEntry voor CustomControl voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="5550a-133">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)

[<span data-ttu-id="5550a-134">Het element ExpressionBinding voor CustomItem voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="5550a-134">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="5550a-135">Het element Frame voor CustomItem voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="5550a-135">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="5550a-136">Het element NewLine voor CustomItem voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="5550a-136">NewLine Element for CustomItem for GroupBy (Format)</span></span>](./newline-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="5550a-137">Het element Tekst voor CustomItem voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="5550a-137">Text Element for CustomItem for GroupBy (Format)</span></span>](./text-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="5550a-138">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="5550a-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
