---
title: Element voor CustomItem kader voor controles voor configuratie (-indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d879c8ce-679d-4622-bc43-c207f6413871
caps.latest.revision: 9
ms.openlocfilehash: b11b154a94daccead57bdfb5e579e1de2c190c09
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851693"
---
# <a name="frame-element-for-customitem-for-controls-for-configuration-format"></a><span data-ttu-id="f643a-102">Het element Frame voor CustomItem voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="f643a-102">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>

<span data-ttu-id="f643a-103">Hiermee definieert u hoe de gegevens worden weergegeven, zoals de gegevens verschuiving naar links of rechts.</span><span class="sxs-lookup"><span data-stu-id="f643a-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="f643a-104">Dit element wordt gebruikt bij het definiëren van een algemene besturingselement dat kan worden gebruikt door alle weergaven in de opmaak-bestand.</span><span class="sxs-lookup"><span data-stu-id="f643a-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="f643a-105">Configuratie-Element (indeling) besturingselementen Element van configuratie (-indeling) besturingselement Element controles voor configuratie (-indeling) CustomControl-Element voor het besturingselement voor configuratie (-indeling) CustomEntries-Element voor CustomControl voor configuratie ( -Indeling) CustomEntry Element voor CustomControl controles voor configuratie (-indeling) CustomItem-Element voor CustomEntry voor besturingselementen voor het kader, configuratie-Element voor CustomItem voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="f643a-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration Frame Element for CustomItem for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f643a-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="f643a-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f643a-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="f643a-107">Attributes and Elements</span></span>

<span data-ttu-id="f643a-108">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `Frame` element.</span><span class="sxs-lookup"><span data-stu-id="f643a-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f643a-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="f643a-109">Attributes</span></span>

<span data-ttu-id="f643a-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="f643a-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f643a-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="f643a-111">Child Elements</span></span>

|<span data-ttu-id="f643a-112">Element</span><span class="sxs-lookup"><span data-stu-id="f643a-112">Element</span></span>|<span data-ttu-id="f643a-113">Description</span><span class="sxs-lookup"><span data-stu-id="f643a-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="f643a-114">Vereist Element</span><span class="sxs-lookup"><span data-stu-id="f643a-114">Required Element</span></span>|
|[<span data-ttu-id="f643a-115">FirstLineHanging-Element voor kader voor controles voor configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="f643a-115">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="f643a-116">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="f643a-116">Optional element.</span></span><br /><br /> <span data-ttu-id="f643a-117">Hiermee geeft u het aantal tekens in de eerste regel van gegevens is verplaatst naar de linkerkant.</span><span class="sxs-lookup"><span data-stu-id="f643a-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="f643a-118">FirstLineIndent-Element voor kader voor controles voor configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="f643a-118">FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="f643a-119">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="f643a-119">Optional element.</span></span><br /><br /> <span data-ttu-id="f643a-120">Hiermee geeft u het aantal tekens in de eerste regel van gegevens is verplaatst naar de rechterkant.</span><span class="sxs-lookup"><span data-stu-id="f643a-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="f643a-121">LeftIndent-Element voor kader voor controles voor configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="f643a-121">LeftIndent Element for Frame for Controls for Configuration (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="f643a-122">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="f643a-122">Optional element.</span></span><br /><br /> <span data-ttu-id="f643a-123">Hiermee geeft u op hoeveel tekens de gegevens van de linkermarge is verplaatst.</span><span class="sxs-lookup"><span data-stu-id="f643a-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="f643a-124">RightIndent-Element voor kader voor controles voor configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="f643a-124">RightIndent Element for Frame for Controls for Configuration (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="f643a-125">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="f643a-125">Optional element.</span></span><br /><br /> <span data-ttu-id="f643a-126">Hiermee geeft u op hoeveel tekens de gegevens van de rechtermarge is verplaatst.</span><span class="sxs-lookup"><span data-stu-id="f643a-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f643a-127">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="f643a-127">Parent Elements</span></span>

|<span data-ttu-id="f643a-128">Element</span><span class="sxs-lookup"><span data-stu-id="f643a-128">Element</span></span>|<span data-ttu-id="f643a-129">Description</span><span class="sxs-lookup"><span data-stu-id="f643a-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f643a-130">CustomItem-Element voor CustomEntry voor besturingselementen voor configuratie</span><span class="sxs-lookup"><span data-stu-id="f643a-130">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="f643a-131">Bepaalt welke gegevens worden weergegeven door het besturingselement en hoe deze wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="f643a-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f643a-132">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="f643a-132">Remarks</span></span>

<span data-ttu-id="f643a-133">U kunt geen opgeven de [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) en de [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) elementen in dezelfde `Frame` element.</span><span class="sxs-lookup"><span data-stu-id="f643a-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="f643a-134">Zie ook</span><span class="sxs-lookup"><span data-stu-id="f643a-134">See Also</span></span>

[<span data-ttu-id="f643a-135">FirstLineHanging-Element voor kader voor controles voor configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="f643a-135">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="f643a-136">FirstLineIndent-Element voor kader voor controles voor configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="f643a-136">FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="f643a-137">LeftIndent-Element voor kader voor controles voor configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="f643a-137">LeftIndent Element for Frame for Controls for Configuration (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="f643a-138">RightIndent-Element voor kader voor controles voor configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="f643a-138">RightIndent Element for Frame for Controls for Configuration (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="f643a-139">CustomItem-Element voor CustomEntry voor besturingselementen voor configuratie</span><span class="sxs-lookup"><span data-stu-id="f643a-139">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="f643a-140">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="f643a-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
