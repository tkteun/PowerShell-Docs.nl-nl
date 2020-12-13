---
ms.date: 09/13/2016
ms.topic: reference
title: Het element Frame voor CustomItem voor Besturingselementen voor Weergave (opmaak)
description: Het element Frame voor CustomItem voor Besturingselementen voor Weergave (opmaak)
ms.openlocfilehash: 6f26e19a6894ac213b924108a56cb80f9ffd1143
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652200"
---
# <a name="frame-element-for-customitem-for-controls-for-view-format"></a><span data-ttu-id="32a1a-103">Het element Frame voor CustomItem voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="32a1a-103">Frame Element for CustomItem for Controls for View (Format)</span></span>

<span data-ttu-id="32a1a-104">Hiermee definieert u hoe de gegevens worden weer gegeven, zoals de gegevens naar links of rechts verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="32a1a-104">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="32a1a-105">Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.</span><span class="sxs-lookup"><span data-stu-id="32a1a-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="32a1a-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) Controls-element (Format) Control element (opmaak) voor besturings elementen voor weer gave (indeling) CustomControl-element voor besturings element voor besturings elementen voor de weer gave (Format) CustomEntries-element voor het CustomEntry-element (Format) voor CustomEntries voor besturings elementen voor de weer gave (Format) CustomItem-element voor CustomEntry voor besturings elementen voor de weer gave (Format)-frame-element voor CustomItem voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="32a1a-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) Frame Element for CustomItem for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="32a1a-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="32a1a-107">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="32a1a-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="32a1a-108">Attributes and Elements</span></span>

<span data-ttu-id="32a1a-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `Frame` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="32a1a-109">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="32a1a-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="32a1a-110">Attributes</span></span>

<span data-ttu-id="32a1a-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="32a1a-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="32a1a-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="32a1a-112">Child Elements</span></span>

|<span data-ttu-id="32a1a-113">Element</span><span class="sxs-lookup"><span data-stu-id="32a1a-113">Element</span></span>|<span data-ttu-id="32a1a-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="32a1a-114">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="32a1a-115">Vereist element</span><span class="sxs-lookup"><span data-stu-id="32a1a-115">Required Element</span></span>|
|[<span data-ttu-id="32a1a-116">FirstLineHanging-element van het frame van de besturings elementen van de weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="32a1a-116">FirstLineHanging Element of Frame of Controls of View (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="32a1a-117">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="32a1a-117">Optional element.</span></span><br /><br /> <span data-ttu-id="32a1a-118">Geeft aan hoeveel tekens de eerste regel naar links wordt verplaatst.</span><span class="sxs-lookup"><span data-stu-id="32a1a-118">Specifies how many characters the first line is shifted to the left.</span></span>|
|[<span data-ttu-id="32a1a-119">FirstLineIndent-element van het frame van de besturings elementen van de weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="32a1a-119">FirstLineIndent Element of Frame of Controls of View (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="32a1a-120">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="32a1a-120">Optional element.</span></span><br /><br /> <span data-ttu-id="32a1a-121">Geeft aan hoeveel tekens de eerste regel naar rechts wordt geschoven.</span><span class="sxs-lookup"><span data-stu-id="32a1a-121">Specifies how many characters the first line is shifted to the right.</span></span>|
|[<span data-ttu-id="32a1a-122">LeftIndent-element van het frame van de besturings elementen van de weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="32a1a-122">LeftIndent Element of Frame of Controls of View (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="32a1a-123">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="32a1a-123">Optional element.</span></span><br /><br /> <span data-ttu-id="32a1a-124">Hiermee geeft u op hoeveel tekens de gegevens van de linkermarge worden verplaatst.</span><span class="sxs-lookup"><span data-stu-id="32a1a-124">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="32a1a-125">RightIndent-element van het frame van de besturings elementen van de weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="32a1a-125">RightIndent Element of Frame of Controls of View (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="32a1a-126">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="32a1a-126">Optional element.</span></span><br /><br /> <span data-ttu-id="32a1a-127">Hiermee geeft u op hoeveel tekens de gegevens van de rechter marge worden verplaatst.</span><span class="sxs-lookup"><span data-stu-id="32a1a-127">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="32a1a-128">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="32a1a-128">Parent Elements</span></span>

|<span data-ttu-id="32a1a-129">Element</span><span class="sxs-lookup"><span data-stu-id="32a1a-129">Element</span></span>|<span data-ttu-id="32a1a-130">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="32a1a-130">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="32a1a-131">Het element CustomItem voor CustomEntry voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="32a1a-131">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="32a1a-132">Hiermee definieert u welke gegevens worden weer gegeven door het besturings element en hoe deze worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="32a1a-132">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="32a1a-133">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="32a1a-133">Remarks</span></span>

<span data-ttu-id="32a1a-134">U kunt de [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) -en [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) -elementen in hetzelfde element niet opgeven `Frame` .</span><span class="sxs-lookup"><span data-stu-id="32a1a-134">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="32a1a-135">Zie ook</span><span class="sxs-lookup"><span data-stu-id="32a1a-135">See Also</span></span>

[<span data-ttu-id="32a1a-136">FirstLineHanging-element van het frame van de besturings elementen van de weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="32a1a-136">FirstLineHanging Element of Frame of Controls of View (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="32a1a-137">FirstLineIndent-element van het frame van de besturings elementen van de weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="32a1a-137">FirstLineIndent Element of Frame of Controls of View (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="32a1a-138">LeftIndent-element van het frame van de besturings elementen van de weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="32a1a-138">LeftIndent Element of Frame of Controls of View (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="32a1a-139">RightIndent-element van het frame van de besturings elementen van de weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="32a1a-139">RightIndent Element of Frame of Controls of View (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="32a1a-140">Het element CustomItem voor CustomEntry voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="32a1a-140">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="32a1a-141">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="32a1a-141">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
