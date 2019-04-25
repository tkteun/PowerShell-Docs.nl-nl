---
title: Frame-Element voor CustomItem voor CustomControl voor weergave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e1a13100-41a4-4847-9f07-458c85783505
caps.latest.revision: 6
ms.openlocfilehash: 925ef86e61801f5a66f89dd25e0756f00dd35155
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065577"
---
# <a name="frame-element-for-customitem-for-customcontrol-for-view-format"></a><span data-ttu-id="5e0d9-102">Het element Frame voor CustomItem voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="5e0d9-102">Frame Element for CustomItem for CustomControl for View (Format)</span></span>

<span data-ttu-id="5e0d9-103">Hiermee definieert u hoe de gegevens worden weergegeven, zoals de gegevens verschuiving naar links of rechts.</span><span class="sxs-lookup"><span data-stu-id="5e0d9-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="5e0d9-104">Dit element wordt gebruikt bij het definiëren van een aangepast besturingselement-weergave.</span><span class="sxs-lookup"><span data-stu-id="5e0d9-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="5e0d9-105">Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) CustomControl Element (indeling) CustomEntries Element voor CustomControl voor weergave (indeling) CustomEntry Element voor CustomEntries voor weergave (indeling) CustomItem Element voor CustomEntry voor CustomControlView (indeling) Frame-Element voor CustomItem voor CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="5e0d9-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for CustomControlView (Format) Frame Element for CustomItem for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5e0d9-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="5e0d9-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5e0d9-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="5e0d9-107">Attributes and Elements</span></span>

<span data-ttu-id="5e0d9-108">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `Frame` element.</span><span class="sxs-lookup"><span data-stu-id="5e0d9-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5e0d9-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="5e0d9-109">Attributes</span></span>

<span data-ttu-id="5e0d9-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="5e0d9-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5e0d9-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="5e0d9-111">Child Elements</span></span>

|<span data-ttu-id="5e0d9-112">Element</span><span class="sxs-lookup"><span data-stu-id="5e0d9-112">Element</span></span>|<span data-ttu-id="5e0d9-113">Description</span><span class="sxs-lookup"><span data-stu-id="5e0d9-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="5e0d9-114">Vereist Element</span><span class="sxs-lookup"><span data-stu-id="5e0d9-114">Required Element</span></span>|
|[<span data-ttu-id="5e0d9-115">FirstLineHanging-Element</span><span class="sxs-lookup"><span data-stu-id="5e0d9-115">FirstLineHanging Element</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="5e0d9-116">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="5e0d9-116">Optional element.</span></span><br /><br /> <span data-ttu-id="5e0d9-117">Hiermee geeft u het aantal tekens in de eerste regel van gegevens is verplaatst naar de linkerkant.</span><span class="sxs-lookup"><span data-stu-id="5e0d9-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="5e0d9-118">FirstLineIndent Element</span><span class="sxs-lookup"><span data-stu-id="5e0d9-118">FirstLineIndent Element</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="5e0d9-119">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="5e0d9-119">Optional element.</span></span><br /><br /> <span data-ttu-id="5e0d9-120">Hiermee geeft u het aantal tekens in de eerste regel van gegevens is verplaatst naar de rechterkant.</span><span class="sxs-lookup"><span data-stu-id="5e0d9-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="5e0d9-121">LeftIndent Element</span><span class="sxs-lookup"><span data-stu-id="5e0d9-121">LeftIndent Element</span></span>](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="5e0d9-122">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="5e0d9-122">Optional element.</span></span><br /><br /> <span data-ttu-id="5e0d9-123">Hiermee geeft u op hoeveel tekens de gegevens van de linkermarge is verplaatst.</span><span class="sxs-lookup"><span data-stu-id="5e0d9-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="5e0d9-124">RightIndent Element</span><span class="sxs-lookup"><span data-stu-id="5e0d9-124">RightIndent Element</span></span>](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="5e0d9-125">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="5e0d9-125">Optional element.</span></span><br /><br /> <span data-ttu-id="5e0d9-126">Hiermee geeft u op hoeveel tekens de gegevens van de rechtermarge is verplaatst.</span><span class="sxs-lookup"><span data-stu-id="5e0d9-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="5e0d9-127">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="5e0d9-127">Parent Elements</span></span>

|<span data-ttu-id="5e0d9-128">Element</span><span class="sxs-lookup"><span data-stu-id="5e0d9-128">Element</span></span>|<span data-ttu-id="5e0d9-129">Description</span><span class="sxs-lookup"><span data-stu-id="5e0d9-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5e0d9-130">CustomItem-Element voor CustomEntry voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="5e0d9-130">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="5e0d9-131">Bepaalt welke gegevens worden weergegeven door het besturingselement en hoe deze wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="5e0d9-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5e0d9-132">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="5e0d9-132">Remarks</span></span>

<span data-ttu-id="5e0d9-133">U kunt geen opgeven de [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) en de [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) elementen in dezelfde `Frame` element.</span><span class="sxs-lookup"><span data-stu-id="5e0d9-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="5e0d9-134">Zie ook</span><span class="sxs-lookup"><span data-stu-id="5e0d9-134">See Also</span></span>

[<span data-ttu-id="5e0d9-135">FirstLineHanging-Element</span><span class="sxs-lookup"><span data-stu-id="5e0d9-135">FirstLineHanging Element</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="5e0d9-136">FirstLineIndent Element</span><span class="sxs-lookup"><span data-stu-id="5e0d9-136">FirstLineIndent Element</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="5e0d9-137">LeftIndent Element</span><span class="sxs-lookup"><span data-stu-id="5e0d9-137">LeftIndent Element</span></span>](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="5e0d9-138">RightIndent Element</span><span class="sxs-lookup"><span data-stu-id="5e0d9-138">RightIndent Element</span></span>](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="5e0d9-139">CustomItem-Element voor CustomEntry voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="5e0d9-139">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="5e0d9-140">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="5e0d9-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
