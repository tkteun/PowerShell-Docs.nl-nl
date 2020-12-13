---
ms.date: 09/13/2016
ms.topic: reference
title: Het element Frame voor CustomItem voor CustomControl voor Weergave (opmaak)
description: Het element Frame voor CustomItem voor CustomControl voor Weergave (opmaak)
ms.openlocfilehash: 1ffe071bb6c4f590e4c79803a3faff2108c7b636
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652188"
---
# <a name="frame-element-for-customitem-for-customcontrol-for-view-format"></a><span data-ttu-id="cbc5c-103">Het element Frame voor CustomItem voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="cbc5c-103">Frame Element for CustomItem for CustomControl for View (Format)</span></span>

<span data-ttu-id="cbc5c-104">Hiermee definieert u hoe de gegevens worden weer gegeven, zoals de gegevens naar links of rechts verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="cbc5c-104">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="cbc5c-105">Dit element wordt gebruikt bij het definiëren van een aangepaste beheer weergave.</span><span class="sxs-lookup"><span data-stu-id="cbc5c-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="cbc5c-106">Configuratie-element (indeling) ViewDefinitions element (indeling) weer gave element (indeling) CustomControl element (Format) CustomEntries element voor CustomControl voor weer gave (Format) CustomEntry-element voor CustomEntries voor weer gave (Format) CustomItem element voor CustomEntry voor CustomControlView (Format) voor CustomItem voor de weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="cbc5c-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for CustomControlView (Format) Frame Element for CustomItem for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="cbc5c-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="cbc5c-107">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cbc5c-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="cbc5c-108">Attributes and Elements</span></span>

<span data-ttu-id="cbc5c-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `Frame` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="cbc5c-109">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="cbc5c-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="cbc5c-110">Attributes</span></span>

<span data-ttu-id="cbc5c-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="cbc5c-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="cbc5c-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="cbc5c-112">Child Elements</span></span>

|<span data-ttu-id="cbc5c-113">Element</span><span class="sxs-lookup"><span data-stu-id="cbc5c-113">Element</span></span>|<span data-ttu-id="cbc5c-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="cbc5c-114">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="cbc5c-115">Vereist element</span><span class="sxs-lookup"><span data-stu-id="cbc5c-115">Required Element</span></span>|
|[<span data-ttu-id="cbc5c-116">FirstLineHanging-element</span><span class="sxs-lookup"><span data-stu-id="cbc5c-116">FirstLineHanging Element</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="cbc5c-117">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="cbc5c-117">Optional element.</span></span><br /><br /> <span data-ttu-id="cbc5c-118">Geeft aan hoeveel tekens de eerste regel van de gegevens naar links verschuift.</span><span class="sxs-lookup"><span data-stu-id="cbc5c-118">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="cbc5c-119">FirstLineIndent-element</span><span class="sxs-lookup"><span data-stu-id="cbc5c-119">FirstLineIndent Element</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="cbc5c-120">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="cbc5c-120">Optional element.</span></span><br /><br /> <span data-ttu-id="cbc5c-121">Geeft aan hoeveel tekens de eerste regel van de gegevens naar rechts wordt geschoven.</span><span class="sxs-lookup"><span data-stu-id="cbc5c-121">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="cbc5c-122">LeftIndent-element</span><span class="sxs-lookup"><span data-stu-id="cbc5c-122">LeftIndent Element</span></span>](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="cbc5c-123">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="cbc5c-123">Optional element.</span></span><br /><br /> <span data-ttu-id="cbc5c-124">Hiermee geeft u op hoeveel tekens de gegevens van de linkermarge worden verplaatst.</span><span class="sxs-lookup"><span data-stu-id="cbc5c-124">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="cbc5c-125">RightIndent-element</span><span class="sxs-lookup"><span data-stu-id="cbc5c-125">RightIndent Element</span></span>](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="cbc5c-126">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="cbc5c-126">Optional element.</span></span><br /><br /> <span data-ttu-id="cbc5c-127">Hiermee geeft u op hoeveel tekens de gegevens van de rechter marge worden verplaatst.</span><span class="sxs-lookup"><span data-stu-id="cbc5c-127">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="cbc5c-128">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="cbc5c-128">Parent Elements</span></span>

|<span data-ttu-id="cbc5c-129">Element</span><span class="sxs-lookup"><span data-stu-id="cbc5c-129">Element</span></span>|<span data-ttu-id="cbc5c-130">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="cbc5c-130">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cbc5c-131">CustomItem-element voor CustomEntry voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="cbc5c-131">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="cbc5c-132">Hiermee definieert u welke gegevens worden weer gegeven door het besturings element en hoe deze worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="cbc5c-132">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="cbc5c-133">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="cbc5c-133">Remarks</span></span>

<span data-ttu-id="cbc5c-134">U kunt de [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) -en [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) -elementen in hetzelfde element niet opgeven `Frame` .</span><span class="sxs-lookup"><span data-stu-id="cbc5c-134">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="cbc5c-135">Zie ook</span><span class="sxs-lookup"><span data-stu-id="cbc5c-135">See Also</span></span>

[<span data-ttu-id="cbc5c-136">FirstLineHanging-element</span><span class="sxs-lookup"><span data-stu-id="cbc5c-136">FirstLineHanging Element</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="cbc5c-137">FirstLineIndent-element</span><span class="sxs-lookup"><span data-stu-id="cbc5c-137">FirstLineIndent Element</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="cbc5c-138">LeftIndent-element</span><span class="sxs-lookup"><span data-stu-id="cbc5c-138">LeftIndent Element</span></span>](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="cbc5c-139">RightIndent-element</span><span class="sxs-lookup"><span data-stu-id="cbc5c-139">RightIndent Element</span></span>](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="cbc5c-140">CustomItem-element voor CustomEntry voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="cbc5c-140">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="cbc5c-141">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="cbc5c-141">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
