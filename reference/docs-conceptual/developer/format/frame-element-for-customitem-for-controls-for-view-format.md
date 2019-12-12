---
title: Frame-element voor CustomItem voor besturings elementen voor weer gave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a5729091-78a9-4bc1-abac-210bc20c6dbe
caps.latest.revision: 7
ms.openlocfilehash: f93dc20a9c5f87c14605578062b1e60f5a3d25cf
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72354976"
---
# <a name="frame-element-for-customitem-for-controls-for-view-format"></a><span data-ttu-id="c4b98-102">Het element Frame voor CustomItem voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c4b98-102">Frame Element for CustomItem for Controls for View (Format)</span></span>

<span data-ttu-id="c4b98-103">Hiermee definieert u hoe de gegevens worden weer gegeven, zoals de gegevens naar links of rechts verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="c4b98-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="c4b98-104">Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.</span><span class="sxs-lookup"><span data-stu-id="c4b98-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="c4b98-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) Controls-element (Format) Control element (opmaak) voor besturings elementen voor de weer gave (indeling) CustomControl-element voor besturings elementen voor Controls (Format) CustomEntries element voor CustomControl voor View (Format) CustomEntry-element voor CustomEntries voor besturings elementen voor weer gave (Format) CustomItem-element voor CustomEntry voor besturings elementen voor de weer gave (Format)-frame-element voor CustomItem voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="c4b98-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) Frame Element for CustomItem for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c4b98-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="c4b98-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c4b98-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="c4b98-107">Attributes and Elements</span></span>

<span data-ttu-id="c4b98-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `Frame` beschreven.</span><span class="sxs-lookup"><span data-stu-id="c4b98-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c4b98-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="c4b98-109">Attributes</span></span>

<span data-ttu-id="c4b98-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="c4b98-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c4b98-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="c4b98-111">Child Elements</span></span>

|<span data-ttu-id="c4b98-112">Element</span><span class="sxs-lookup"><span data-stu-id="c4b98-112">Element</span></span>|<span data-ttu-id="c4b98-113">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="c4b98-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="c4b98-114">Vereist element</span><span class="sxs-lookup"><span data-stu-id="c4b98-114">Required Element</span></span>|
|[<span data-ttu-id="c4b98-115">FirstLineHanging-element van het frame van de besturings elementen van de weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="c4b98-115">FirstLineHanging Element of Frame of Controls of View (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="c4b98-116">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="c4b98-116">Optional element.</span></span><br /><br /> <span data-ttu-id="c4b98-117">Geeft aan hoeveel tekens de eerste regel naar links wordt verplaatst.</span><span class="sxs-lookup"><span data-stu-id="c4b98-117">Specifies how many characters the first line is shifted to the left.</span></span>|
|[<span data-ttu-id="c4b98-118">FirstLineIndent-element van het frame van de besturings elementen van de weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="c4b98-118">FirstLineIndent Element of Frame of Controls of View (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="c4b98-119">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="c4b98-119">Optional element.</span></span><br /><br /> <span data-ttu-id="c4b98-120">Geeft aan hoeveel tekens de eerste regel naar rechts wordt geschoven.</span><span class="sxs-lookup"><span data-stu-id="c4b98-120">Specifies how many characters the first line is shifted to the right.</span></span>|
|[<span data-ttu-id="c4b98-121">LeftIndent-element van het frame van de besturings elementen van de weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="c4b98-121">LeftIndent Element of Frame of Controls of View (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="c4b98-122">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="c4b98-122">Optional element.</span></span><br /><br /> <span data-ttu-id="c4b98-123">Hiermee geeft u op hoeveel tekens de gegevens van de linkermarge worden verplaatst.</span><span class="sxs-lookup"><span data-stu-id="c4b98-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="c4b98-124">RightIndent-element van het frame van de besturings elementen van de weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="c4b98-124">RightIndent Element of Frame of Controls of View (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="c4b98-125">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="c4b98-125">Optional element.</span></span><br /><br /> <span data-ttu-id="c4b98-126">Hiermee geeft u op hoeveel tekens de gegevens van de rechter marge worden verplaatst.</span><span class="sxs-lookup"><span data-stu-id="c4b98-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c4b98-127">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="c4b98-127">Parent Elements</span></span>

|<span data-ttu-id="c4b98-128">Element</span><span class="sxs-lookup"><span data-stu-id="c4b98-128">Element</span></span>|<span data-ttu-id="c4b98-129">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="c4b98-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c4b98-130">CustomItem-element voor CustomEntry voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="c4b98-130">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="c4b98-131">Hiermee definieert u welke gegevens worden weer gegeven door het besturings element en hoe deze worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c4b98-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c4b98-132">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="c4b98-132">Remarks</span></span>

<span data-ttu-id="c4b98-133">U kunt de [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) -en [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) -elementen niet opgeven in hetzelfde `Frame` element.</span><span class="sxs-lookup"><span data-stu-id="c4b98-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="c4b98-134">Zie ook</span><span class="sxs-lookup"><span data-stu-id="c4b98-134">See Also</span></span>

[<span data-ttu-id="c4b98-135">FirstLineHanging-element van het frame van de besturings elementen van de weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="c4b98-135">FirstLineHanging Element of Frame of Controls of View (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="c4b98-136">FirstLineIndent-element van het frame van de besturings elementen van de weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="c4b98-136">FirstLineIndent Element of Frame of Controls of View (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="c4b98-137">LeftIndent-element van het frame van de besturings elementen van de weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="c4b98-137">LeftIndent Element of Frame of Controls of View (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="c4b98-138">RightIndent-element van het frame van de besturings elementen van de weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="c4b98-138">RightIndent Element of Frame of Controls of View (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="c4b98-139">CustomItem-element voor CustomEntry voor besturings elementen voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="c4b98-139">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="c4b98-140">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="c4b98-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
