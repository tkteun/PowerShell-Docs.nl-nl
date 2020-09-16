---
title: CustomItem-element voor CustomEntry voor CustomControl voor weer gave (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 25101c9c156ef91657f51db7044bf9a6653142a2
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785826"
---
# <a name="customitem-element-for-customentry-for-customcontrol-for-view-format"></a><span data-ttu-id="ef418-102">Het element CustomItem voor CustomEntry voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="ef418-102">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>

<span data-ttu-id="ef418-103">Hiermee definieert u welke gegevens worden weer gegeven in de weer gave van het aangepaste besturings element en hoe deze worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="ef418-103">Defines what data is displayed by the custom control view and how it is displayed.</span></span> <span data-ttu-id="ef418-104">Dit element wordt gebruikt bij het definiëren van een aangepaste beheer weergave.</span><span class="sxs-lookup"><span data-stu-id="ef418-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="ef418-105">Configuratie-element (indeling) ViewDefinitions element (indeling) weer gave element (indeling) CustomControl element (Format) CustomEntries element voor CustomControl voor weer gave (Format) CustomEntry-element voor CustomEntries voor weer gave (Format) CustomItem element voor CustomEntry voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="ef418-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ef418-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="ef418-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ef418-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="ef418-107">Attributes and Elements</span></span>

<span data-ttu-id="ef418-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `CustomItem` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="ef418-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ef418-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="ef418-109">Attributes</span></span>

<span data-ttu-id="ef418-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="ef418-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ef418-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="ef418-111">Child Elements</span></span>

|<span data-ttu-id="ef418-112">Element</span><span class="sxs-lookup"><span data-stu-id="ef418-112">Element</span></span>|<span data-ttu-id="ef418-113">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="ef418-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ef418-114">Het element ExpressionBinding voor CustomItem voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="ef418-114">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="ef418-115">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="ef418-115">Optional element.</span></span><br /><br /> <span data-ttu-id="ef418-116">Hiermee worden de gegevens gedefinieerd die door het besturings element worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="ef418-116">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="ef418-117">Het element Frame voor CustomItem voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="ef418-117">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="ef418-118">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="ef418-118">Optional element.</span></span><br /><br /> <span data-ttu-id="ef418-119">Hiermee definieert u welke gegevens worden weer gegeven in de weer gave van het aangepaste besturings element en hoe deze worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="ef418-119">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|
|[<span data-ttu-id="ef418-120">Element nieuwe regel voor CustomItem voor aangepast besturings element voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="ef418-120">NewLine Element for CustomItem for Custom Control for View (Format)</span></span>](./newline-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="ef418-121">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="ef418-121">Optional element.</span></span><br /><br /> <span data-ttu-id="ef418-122">Hiermee voegt u een lege regel toe aan de weer gave van het besturings element.</span><span class="sxs-lookup"><span data-stu-id="ef418-122">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="ef418-123">Tekst element voor CustomItem voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="ef418-123">Text Element for CustomItem for CustomControl for View (Format)</span></span>](./text-element-for-customitem-for-customview-for-view-format.md)|<span data-ttu-id="ef418-124">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="ef418-124">Optional element.</span></span><br /><br /> <span data-ttu-id="ef418-125">Hiermee geeft u aanvullende tekst op voor de gegevens die door het besturings element worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="ef418-125">Specifies additional text to the data displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ef418-126">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="ef418-126">Parent Elements</span></span>

|<span data-ttu-id="ef418-127">Element</span><span class="sxs-lookup"><span data-stu-id="ef418-127">Element</span></span>|<span data-ttu-id="ef418-128">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="ef418-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ef418-129">Het element CustomEntry voor CustomEntries voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="ef418-129">CustomEntry Element for CustomEntries for CustomControl for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="ef418-130">Biedt een definitie van de aangepaste beheer weergave.</span><span class="sxs-lookup"><span data-stu-id="ef418-130">Provides a definition of the custom control view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ef418-131">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="ef418-131">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="ef418-132">Zie ook</span><span class="sxs-lookup"><span data-stu-id="ef418-132">See Also</span></span>

[<span data-ttu-id="ef418-133">CustomEntry-element voor CustomEntries voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="ef418-133">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="ef418-134">Het element ExpressionBinding voor CustomItem voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="ef418-134">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="ef418-135">Het element Frame voor CustomItem voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="ef418-135">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="ef418-136">Het element NewLine voor CustomItem voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="ef418-136">NewLine Element for CustomItem for CustomControl for View (Format)</span></span>](./newline-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="ef418-137">Tekst element voor CustomItem voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="ef418-137">Text Element for CustomItem for CustomControl for View (Format)</span></span>](./text-element-for-customitem-for-customview-for-view-format.md)

[<span data-ttu-id="ef418-138">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="ef418-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
