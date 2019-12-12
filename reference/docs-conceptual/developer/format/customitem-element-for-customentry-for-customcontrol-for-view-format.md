---
title: CustomItem-element voor CustomEntry voor CustomControl voor weer gave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 98708c1d-6f39-4a76-b454-31153a6ade8c
caps.latest.revision: 12
ms.openlocfilehash: 3c110bd5fe3ef2f790ef136556afa7c29d0b5b29
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72355186"
---
# <a name="customitem-element-for-customentry-for-customcontrol-for-view-format"></a><span data-ttu-id="06651-102">Het element CustomItem voor CustomEntry voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="06651-102">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>

<span data-ttu-id="06651-103">Hiermee definieert u welke gegevens worden weer gegeven in de weer gave van het aangepaste besturings element en hoe deze worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="06651-103">Defines what data is displayed by the custom control view and how it is displayed.</span></span> <span data-ttu-id="06651-104">Dit element wordt gebruikt bij het definiëren van een aangepaste beheer weergave.</span><span class="sxs-lookup"><span data-stu-id="06651-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="06651-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) CustomControl-element (indeling) CustomEntries element voor CustomControl voor weer gave (Format) CustomEntry-element voor CustomEntries voor weer gave (Format) CustomItem element voor CustomEntry voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="06651-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="06651-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="06651-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="06651-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="06651-107">Attributes and Elements</span></span>

<span data-ttu-id="06651-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `CustomItem` beschreven.</span><span class="sxs-lookup"><span data-stu-id="06651-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="06651-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="06651-109">Attributes</span></span>

<span data-ttu-id="06651-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="06651-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="06651-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="06651-111">Child Elements</span></span>

|<span data-ttu-id="06651-112">Element</span><span class="sxs-lookup"><span data-stu-id="06651-112">Element</span></span>|<span data-ttu-id="06651-113">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="06651-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="06651-114">ExpressionBinding-element voor CustomItem voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="06651-114">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="06651-115">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="06651-115">Optional element.</span></span><br /><br /> <span data-ttu-id="06651-116">Hiermee worden de gegevens gedefinieerd die door het besturings element worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="06651-116">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="06651-117">Frame-element voor CustomItem voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="06651-117">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="06651-118">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="06651-118">Optional element.</span></span><br /><br /> <span data-ttu-id="06651-119">Hiermee definieert u welke gegevens worden weer gegeven in de weer gave van het aangepaste besturings element en hoe deze worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="06651-119">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|
|[<span data-ttu-id="06651-120">Element nieuwe regel voor CustomItem voor aangepast besturings element voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="06651-120">NewLine Element for CustomItem for Custom Control for View (Format)</span></span>](./newline-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="06651-121">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="06651-121">Optional element.</span></span><br /><br /> <span data-ttu-id="06651-122">Hiermee voegt u een lege regel toe aan de weer gave van het besturings element.</span><span class="sxs-lookup"><span data-stu-id="06651-122">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="06651-123">Tekst element voor CustomItem voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="06651-123">Text Element for CustomItem for CustomControl for View (Format)</span></span>](./text-element-for-customitem-for-customview-for-view-format.md)|<span data-ttu-id="06651-124">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="06651-124">Optional element.</span></span><br /><br /> <span data-ttu-id="06651-125">Hiermee geeft u aanvullende tekst op voor de gegevens die door het besturings element worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="06651-125">Specifies additional text to the data displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="06651-126">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="06651-126">Parent Elements</span></span>

|<span data-ttu-id="06651-127">Element</span><span class="sxs-lookup"><span data-stu-id="06651-127">Element</span></span>|<span data-ttu-id="06651-128">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="06651-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="06651-129">CustomEntry-element voor CustomEntries voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="06651-129">CustomEntry Element for CustomEntries for CustomControl for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="06651-130">Biedt een definitie van de aangepaste beheer weergave.</span><span class="sxs-lookup"><span data-stu-id="06651-130">Provides a definition of the custom control view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="06651-131">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="06651-131">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="06651-132">Zie ook</span><span class="sxs-lookup"><span data-stu-id="06651-132">See Also</span></span>

[<span data-ttu-id="06651-133">CustomEntry-element voor CustomEntries voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="06651-133">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="06651-134">ExpressionBinding-element voor CustomItem voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="06651-134">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="06651-135">Frame-element voor CustomItem voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="06651-135">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="06651-136">Element nieuwe regel voor CustomItem voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="06651-136">NewLine Element for CustomItem for CustomControl for View (Format)</span></span>](./newline-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="06651-137">Tekst element voor CustomItem voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="06651-137">Text Element for CustomItem for CustomControl for View (Format)</span></span>](./text-element-for-customitem-for-customview-for-view-format.md)

[<span data-ttu-id="06651-138">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="06651-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
