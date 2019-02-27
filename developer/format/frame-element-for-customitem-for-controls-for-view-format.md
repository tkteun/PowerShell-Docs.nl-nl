---
title: Frame-Element voor CustomItem voor besturingselementen voor weergave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a5729091-78a9-4bc1-abac-210bc20c6dbe
caps.latest.revision: 7
ms.openlocfilehash: f93dc20a9c5f87c14605578062b1e60f5a3d25cf
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849481"
---
# <a name="frame-element-for-customitem-for-controls-for-view-format"></a><span data-ttu-id="525ef-102">Het element Frame voor CustomItem voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="525ef-102">Frame Element for CustomItem for Controls for View (Format)</span></span>

<span data-ttu-id="525ef-103">Hiermee definieert u hoe de gegevens worden weergegeven, zoals de gegevens verschuiving naar links of rechts.</span><span class="sxs-lookup"><span data-stu-id="525ef-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="525ef-104">Dit element wordt gebruikt bij het definiëren van besturingselementen die kunnen worden gebruikt door een weergave.</span><span class="sxs-lookup"><span data-stu-id="525ef-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="525ef-105">Configuratie-Element (indeling) ViewDefinitions-Element (indeling) weergave-Element (indeling) besturingselementen Element (indeling) controle-Element voor besturingselementen voor weergave (indeling) CustomControl Element voor de controle voor besturingselementen voor weergave (indeling) CustomEntries Element voor CustomControl voor weergave (indeling) CustomEntry Element voor CustomEntries voor besturingselementen voor weergave (indeling) CustomItem Element voor CustomEntry voor besturingselementen voor weergave (indeling) Frame-Element voor CustomItem voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="525ef-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) Frame Element for CustomItem for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="525ef-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="525ef-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="525ef-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="525ef-107">Attributes and Elements</span></span>

<span data-ttu-id="525ef-108">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `Frame` element.</span><span class="sxs-lookup"><span data-stu-id="525ef-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="525ef-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="525ef-109">Attributes</span></span>

<span data-ttu-id="525ef-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="525ef-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="525ef-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="525ef-111">Child Elements</span></span>

|<span data-ttu-id="525ef-112">Element</span><span class="sxs-lookup"><span data-stu-id="525ef-112">Element</span></span>|<span data-ttu-id="525ef-113">Description</span><span class="sxs-lookup"><span data-stu-id="525ef-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="525ef-114">Vereist Element</span><span class="sxs-lookup"><span data-stu-id="525ef-114">Required Element</span></span>|
|[<span data-ttu-id="525ef-115">FirstLineHanging-Element van het kader van besturingselementen van weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="525ef-115">FirstLineHanging Element of Frame of Controls of View (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="525ef-116">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="525ef-116">Optional element.</span></span><br /><br /> <span data-ttu-id="525ef-117">Hiermee geeft u het aantal tekens in de eerste regel wordt verplaatst naar de linkerkant.</span><span class="sxs-lookup"><span data-stu-id="525ef-117">Specifies how many characters the first line is shifted to the left.</span></span>|
|[<span data-ttu-id="525ef-118">FirstLineIndent Element van het kader van besturingselementen van weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="525ef-118">FirstLineIndent Element of Frame of Controls of View (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="525ef-119">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="525ef-119">Optional element.</span></span><br /><br /> <span data-ttu-id="525ef-120">Hiermee geeft u het aantal tekens in de eerste regel wordt verplaatst naar de rechterkant.</span><span class="sxs-lookup"><span data-stu-id="525ef-120">Specifies how many characters the first line is shifted to the right.</span></span>|
|[<span data-ttu-id="525ef-121">LeftIndent Element van het kader van besturingselementen van weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="525ef-121">LeftIndent Element of Frame of Controls of View (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="525ef-122">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="525ef-122">Optional element.</span></span><br /><br /> <span data-ttu-id="525ef-123">Hiermee geeft u op hoeveel tekens de gegevens van de linkermarge is verplaatst.</span><span class="sxs-lookup"><span data-stu-id="525ef-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="525ef-124">RightIndent Element van het kader van besturingselementen van weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="525ef-124">RightIndent Element of Frame of Controls of View (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="525ef-125">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="525ef-125">Optional element.</span></span><br /><br /> <span data-ttu-id="525ef-126">Hiermee geeft u op hoeveel tekens de gegevens van de rechtermarge is verplaatst.</span><span class="sxs-lookup"><span data-stu-id="525ef-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="525ef-127">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="525ef-127">Parent Elements</span></span>

|<span data-ttu-id="525ef-128">Element</span><span class="sxs-lookup"><span data-stu-id="525ef-128">Element</span></span>|<span data-ttu-id="525ef-129">Description</span><span class="sxs-lookup"><span data-stu-id="525ef-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="525ef-130">CustomItem-Element voor CustomEntry voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="525ef-130">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="525ef-131">Bepaalt welke gegevens worden weergegeven door het besturingselement en hoe deze wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="525ef-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="525ef-132">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="525ef-132">Remarks</span></span>

<span data-ttu-id="525ef-133">U kunt geen opgeven de [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) en de [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) elementen in dezelfde `Frame` element.</span><span class="sxs-lookup"><span data-stu-id="525ef-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="525ef-134">Zie ook</span><span class="sxs-lookup"><span data-stu-id="525ef-134">See Also</span></span>

[<span data-ttu-id="525ef-135">FirstLineHanging-Element van het kader van besturingselementen van weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="525ef-135">FirstLineHanging Element of Frame of Controls of View (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="525ef-136">FirstLineIndent Element van het kader van besturingselementen van weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="525ef-136">FirstLineIndent Element of Frame of Controls of View (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="525ef-137">LeftIndent Element van het kader van besturingselementen van weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="525ef-137">LeftIndent Element of Frame of Controls of View (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="525ef-138">RightIndent Element van het kader van besturingselementen van weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="525ef-138">RightIndent Element of Frame of Controls of View (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="525ef-139">CustomItem-Element voor CustomEntry voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="525ef-139">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="525ef-140">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="525ef-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
