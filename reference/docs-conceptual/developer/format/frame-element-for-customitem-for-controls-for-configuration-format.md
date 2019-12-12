---
title: Frame-element voor CustomItem voor besturings elementen voor configuratie (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d879c8ce-679d-4622-bc43-c207f6413871
caps.latest.revision: 9
ms.openlocfilehash: b11b154a94daccead57bdfb5e579e1de2c190c09
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72354983"
---
# <a name="frame-element-for-customitem-for-controls-for-configuration-format"></a><span data-ttu-id="6490e-102">Het element Frame voor CustomItem voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="6490e-102">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>

<span data-ttu-id="6490e-103">Hiermee definieert u hoe de gegevens worden weer gegeven, zoals de gegevens naar links of rechts verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="6490e-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="6490e-104">Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="6490e-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="6490e-105">Configuratie-element (Format) Controls element van configuratie (Format) Control element voor besturings elementen voor configuratie (Format) CustomControl-element voor Control for Configuration (Format) CustomEntries element voor het configureren van een configuratie ( Format) CustomEntry element voor CustomControl voor besturings elementen voor configuratie (indeling) CustomItem-element voor CustomEntry voor besturings elementen voor het element configuratie frame voor CustomItem voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="6490e-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration Frame Element for CustomItem for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6490e-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="6490e-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6490e-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="6490e-107">Attributes and Elements</span></span>

<span data-ttu-id="6490e-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `Frame` beschreven.</span><span class="sxs-lookup"><span data-stu-id="6490e-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6490e-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="6490e-109">Attributes</span></span>

<span data-ttu-id="6490e-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="6490e-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6490e-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="6490e-111">Child Elements</span></span>

|<span data-ttu-id="6490e-112">Element</span><span class="sxs-lookup"><span data-stu-id="6490e-112">Element</span></span>|<span data-ttu-id="6490e-113">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="6490e-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="6490e-114">Vereist element</span><span class="sxs-lookup"><span data-stu-id="6490e-114">Required Element</span></span>|
|[<span data-ttu-id="6490e-115">FirstLineHanging-element voor frame voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="6490e-115">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="6490e-116">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="6490e-116">Optional element.</span></span><br /><br /> <span data-ttu-id="6490e-117">Geeft aan hoeveel tekens de eerste regel van de gegevens naar links verschuift.</span><span class="sxs-lookup"><span data-stu-id="6490e-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="6490e-118">FirstLineIndent-element voor frame voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="6490e-118">FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="6490e-119">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="6490e-119">Optional element.</span></span><br /><br /> <span data-ttu-id="6490e-120">Geeft aan hoeveel tekens de eerste regel van de gegevens naar rechts wordt geschoven.</span><span class="sxs-lookup"><span data-stu-id="6490e-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="6490e-121">LeftIndent-element voor frame voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="6490e-121">LeftIndent Element for Frame for Controls for Configuration (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="6490e-122">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="6490e-122">Optional element.</span></span><br /><br /> <span data-ttu-id="6490e-123">Hiermee geeft u op hoeveel tekens de gegevens van de linkermarge worden verplaatst.</span><span class="sxs-lookup"><span data-stu-id="6490e-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="6490e-124">RightIndent-element voor frame voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="6490e-124">RightIndent Element for Frame for Controls for Configuration (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="6490e-125">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="6490e-125">Optional element.</span></span><br /><br /> <span data-ttu-id="6490e-126">Hiermee geeft u op hoeveel tekens de gegevens van de rechter marge worden verplaatst.</span><span class="sxs-lookup"><span data-stu-id="6490e-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="6490e-127">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="6490e-127">Parent Elements</span></span>

|<span data-ttu-id="6490e-128">Element</span><span class="sxs-lookup"><span data-stu-id="6490e-128">Element</span></span>|<span data-ttu-id="6490e-129">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="6490e-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6490e-130">CustomItem-element voor CustomEntry voor besturings elementen voor configuratie</span><span class="sxs-lookup"><span data-stu-id="6490e-130">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="6490e-131">Hiermee definieert u welke gegevens worden weer gegeven door het besturings element en hoe deze worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="6490e-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6490e-132">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="6490e-132">Remarks</span></span>

<span data-ttu-id="6490e-133">U kunt de [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) -en [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) -elementen niet opgeven in hetzelfde `Frame` element.</span><span class="sxs-lookup"><span data-stu-id="6490e-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="6490e-134">Zie ook</span><span class="sxs-lookup"><span data-stu-id="6490e-134">See Also</span></span>

[<span data-ttu-id="6490e-135">FirstLineHanging-element voor frame voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="6490e-135">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="6490e-136">FirstLineIndent-element voor frame voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="6490e-136">FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="6490e-137">LeftIndent-element voor frame voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="6490e-137">LeftIndent Element for Frame for Controls for Configuration (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="6490e-138">RightIndent-element voor frame voor besturings elementen voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="6490e-138">RightIndent Element for Frame for Controls for Configuration (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="6490e-139">CustomItem-element voor CustomEntry voor besturings elementen voor configuratie</span><span class="sxs-lookup"><span data-stu-id="6490e-139">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="6490e-140">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="6490e-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
