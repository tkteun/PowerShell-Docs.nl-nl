---
title: Frame-element voor CustomItem voor CustomControl voor weer gave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e1a13100-41a4-4847-9f07-458c85783505
caps.latest.revision: 6
ms.openlocfilehash: 925ef86e61801f5a66f89dd25e0756f00dd35155
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72354969"
---
# <a name="frame-element-for-customitem-for-customcontrol-for-view-format"></a><span data-ttu-id="2d1e5-102">Het element Frame voor CustomItem voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="2d1e5-102">Frame Element for CustomItem for CustomControl for View (Format)</span></span>

<span data-ttu-id="2d1e5-103">Hiermee definieert u hoe de gegevens worden weer gegeven, zoals de gegevens naar links of rechts verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="2d1e5-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="2d1e5-104">Dit element wordt gebruikt bij het definiëren van een aangepaste beheer weergave.</span><span class="sxs-lookup"><span data-stu-id="2d1e5-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="2d1e5-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) CustomControl-element (indeling) CustomEntries element voor CustomControl voor weer gave (Format) CustomEntry-element voor CustomEntries voor weer gave (Format) CustomItem element voor CustomEntry voor CustomControlView (Format) frame-element voor CustomItem voor CustomControl voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="2d1e5-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for CustomControlView (Format) Frame Element for CustomItem for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2d1e5-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="2d1e5-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2d1e5-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="2d1e5-107">Attributes and Elements</span></span>

<span data-ttu-id="2d1e5-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `Frame` beschreven.</span><span class="sxs-lookup"><span data-stu-id="2d1e5-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2d1e5-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="2d1e5-109">Attributes</span></span>

<span data-ttu-id="2d1e5-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="2d1e5-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2d1e5-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="2d1e5-111">Child Elements</span></span>

|<span data-ttu-id="2d1e5-112">Element</span><span class="sxs-lookup"><span data-stu-id="2d1e5-112">Element</span></span>|<span data-ttu-id="2d1e5-113">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="2d1e5-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="2d1e5-114">Vereist element</span><span class="sxs-lookup"><span data-stu-id="2d1e5-114">Required Element</span></span>|
|[<span data-ttu-id="2d1e5-115">FirstLineHanging-element</span><span class="sxs-lookup"><span data-stu-id="2d1e5-115">FirstLineHanging Element</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="2d1e5-116">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="2d1e5-116">Optional element.</span></span><br /><br /> <span data-ttu-id="2d1e5-117">Geeft aan hoeveel tekens de eerste regel van de gegevens naar links verschuift.</span><span class="sxs-lookup"><span data-stu-id="2d1e5-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="2d1e5-118">FirstLineIndent-element</span><span class="sxs-lookup"><span data-stu-id="2d1e5-118">FirstLineIndent Element</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="2d1e5-119">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="2d1e5-119">Optional element.</span></span><br /><br /> <span data-ttu-id="2d1e5-120">Geeft aan hoeveel tekens de eerste regel van de gegevens naar rechts wordt geschoven.</span><span class="sxs-lookup"><span data-stu-id="2d1e5-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="2d1e5-121">LeftIndent-element</span><span class="sxs-lookup"><span data-stu-id="2d1e5-121">LeftIndent Element</span></span>](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="2d1e5-122">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="2d1e5-122">Optional element.</span></span><br /><br /> <span data-ttu-id="2d1e5-123">Hiermee geeft u op hoeveel tekens de gegevens van de linkermarge worden verplaatst.</span><span class="sxs-lookup"><span data-stu-id="2d1e5-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="2d1e5-124">RightIndent-element</span><span class="sxs-lookup"><span data-stu-id="2d1e5-124">RightIndent Element</span></span>](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="2d1e5-125">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="2d1e5-125">Optional element.</span></span><br /><br /> <span data-ttu-id="2d1e5-126">Hiermee geeft u op hoeveel tekens de gegevens van de rechter marge worden verplaatst.</span><span class="sxs-lookup"><span data-stu-id="2d1e5-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="2d1e5-127">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="2d1e5-127">Parent Elements</span></span>

|<span data-ttu-id="2d1e5-128">Element</span><span class="sxs-lookup"><span data-stu-id="2d1e5-128">Element</span></span>|<span data-ttu-id="2d1e5-129">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="2d1e5-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2d1e5-130">CustomItem-element voor CustomEntry voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="2d1e5-130">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="2d1e5-131">Hiermee definieert u welke gegevens worden weer gegeven door het besturings element en hoe deze worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="2d1e5-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2d1e5-132">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="2d1e5-132">Remarks</span></span>

<span data-ttu-id="2d1e5-133">U kunt de [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) -en [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) -elementen niet opgeven in hetzelfde element `Frame`.</span><span class="sxs-lookup"><span data-stu-id="2d1e5-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="2d1e5-134">Zie ook</span><span class="sxs-lookup"><span data-stu-id="2d1e5-134">See Also</span></span>

[<span data-ttu-id="2d1e5-135">FirstLineHanging-element</span><span class="sxs-lookup"><span data-stu-id="2d1e5-135">FirstLineHanging Element</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="2d1e5-136">FirstLineIndent-element</span><span class="sxs-lookup"><span data-stu-id="2d1e5-136">FirstLineIndent Element</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="2d1e5-137">LeftIndent-element</span><span class="sxs-lookup"><span data-stu-id="2d1e5-137">LeftIndent Element</span></span>](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="2d1e5-138">RightIndent-element</span><span class="sxs-lookup"><span data-stu-id="2d1e5-138">RightIndent Element</span></span>](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="2d1e5-139">CustomItem-element voor CustomEntry voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="2d1e5-139">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="2d1e5-140">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="2d1e5-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
