---
title: CustomItem-element voor CustomEntry voor GroupBy (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f7c517aa-24f5-41ae-b82d-cb0fac81a245
caps.latest.revision: 7
ms.openlocfilehash: 2d821f5e3bc8d0f81ef8a8a040c6f9bcb1658bee
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72355137"
---
# <a name="customitem-element-for-customentry-for-groupby-format"></a><span data-ttu-id="c7941-102">Het element CustomItem voor CustomEntry voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c7941-102">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>

<span data-ttu-id="c7941-103">Hiermee definieert u welke gegevens worden weer gegeven in de weer gave van het aangepaste besturings element en hoe deze worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c7941-103">Defines what data is displayed by the custom control view and how it is displayed.</span></span> <span data-ttu-id="c7941-104">Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c7941-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="c7941-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element voor weer gave (indeling) GroupBy-element (Format) voor weer gave (indeling) CustomControl-element voor het element GroupBy (indeling) CustomEntries voor CustomControl voor het element GroupBy (Format) CustomItem voor CustomEntry voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="c7941-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c7941-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="c7941-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c7941-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="c7941-107">Attributes and Elements</span></span>

<span data-ttu-id="c7941-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `CustomItem` beschreven.</span><span class="sxs-lookup"><span data-stu-id="c7941-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c7941-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="c7941-109">Attributes</span></span>

<span data-ttu-id="c7941-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="c7941-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c7941-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="c7941-111">Child Elements</span></span>

|<span data-ttu-id="c7941-112">Element</span><span class="sxs-lookup"><span data-stu-id="c7941-112">Element</span></span>|<span data-ttu-id="c7941-113">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="c7941-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c7941-114">ExpressionBinding-element voor CustomItem voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="c7941-114">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="c7941-115">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="c7941-115">Optional element.</span></span><br /><br /> <span data-ttu-id="c7941-116">Hiermee worden de gegevens gedefinieerd die door het besturings element worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c7941-116">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="c7941-117">Frame-element voor CustomItem voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="c7941-117">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="c7941-118">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="c7941-118">Optional element.</span></span><br /><br /> <span data-ttu-id="c7941-119">Hiermee definieert u welke gegevens worden weer gegeven in de weer gave van het aangepaste besturings element en hoe deze worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c7941-119">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|
|[<span data-ttu-id="c7941-120">Element nieuwe regel voor CustomItem voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="c7941-120">NewLine Element for CustomItem for GroupBy (Format)</span></span>](./newline-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="c7941-121">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="c7941-121">Optional element.</span></span><br /><br /> <span data-ttu-id="c7941-122">Hiermee voegt u een lege regel toe aan de weer gave van het besturings element.</span><span class="sxs-lookup"><span data-stu-id="c7941-122">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="c7941-123">Tekst element voor CustomItem voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="c7941-123">Text Element for CustomItem for GroupBy (Format)</span></span>](./text-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="c7941-124">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="c7941-124">Optional element.</span></span><br /><br /> <span data-ttu-id="c7941-125">Hiermee geeft u aanvullende tekst op voor de gegevens die door het besturings element worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c7941-125">Specifies additional text to the data displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c7941-126">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="c7941-126">Parent Elements</span></span>

|<span data-ttu-id="c7941-127">Element</span><span class="sxs-lookup"><span data-stu-id="c7941-127">Element</span></span>|<span data-ttu-id="c7941-128">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="c7941-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c7941-129">CustomEntry-element voor CustomControl voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="c7941-129">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="c7941-130">Biedt een definitie van de aangepaste beheer weergave.</span><span class="sxs-lookup"><span data-stu-id="c7941-130">Provides a definition of the custom control view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c7941-131">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="c7941-131">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="c7941-132">Zie ook</span><span class="sxs-lookup"><span data-stu-id="c7941-132">See Also</span></span>

[<span data-ttu-id="c7941-133">CustomEntry-element voor CustomControl voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="c7941-133">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)

[<span data-ttu-id="c7941-134">ExpressionBinding-element voor CustomItem voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="c7941-134">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="c7941-135">Frame-element voor CustomItem voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="c7941-135">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="c7941-136">Element nieuwe regel voor CustomItem voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="c7941-136">NewLine Element for CustomItem for GroupBy (Format)</span></span>](./newline-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="c7941-137">Tekst element voor CustomItem voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="c7941-137">Text Element for CustomItem for GroupBy (Format)</span></span>](./text-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="c7941-138">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="c7941-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
