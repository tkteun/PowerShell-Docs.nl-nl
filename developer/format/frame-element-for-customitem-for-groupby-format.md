---
title: Frame-Element voor CustomItem voor GroupBy (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ab2a5379-299d-4c97-86a2-b639ea890fae
caps.latest.revision: 6
ms.openlocfilehash: 7f9066c0fe0954fadff9dc8f0c35a62c6710f516
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065594"
---
# <a name="frame-element-for-customitem-for-groupby-format"></a><span data-ttu-id="ac515-102">Het element Frame voor CustomItem voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="ac515-102">Frame Element for CustomItem for GroupBy (Format)</span></span>

<span data-ttu-id="ac515-103">Hiermee definieert u hoe de gegevens worden weergegeven, zoals de gegevens verschuiving naar links of rechts.</span><span class="sxs-lookup"><span data-stu-id="ac515-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="ac515-104">Dit element wordt gebruikt bij het definiëren van hoe een nieuwe groep objecten worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="ac515-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="ac515-105">Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) GroupBy Element voor weergave (indeling) CustomControl Element voor GroupBy (indeling) CustomEntries Element voor CustomControl voor GroupBy (indeling) CustomEntry Element voor CustomControl voor GroupBy (indeling) CustomItem Element voor CustomEntry voor GroupBy (indeling) Frame-Element voor CustomItem voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="ac515-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) Frame Element for CustomItem for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ac515-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="ac515-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ac515-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="ac515-107">Attributes and Elements</span></span>

<span data-ttu-id="ac515-108">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `Frame` element.</span><span class="sxs-lookup"><span data-stu-id="ac515-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ac515-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="ac515-109">Attributes</span></span>

<span data-ttu-id="ac515-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="ac515-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ac515-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="ac515-111">Child Elements</span></span>

|<span data-ttu-id="ac515-112">Element</span><span class="sxs-lookup"><span data-stu-id="ac515-112">Element</span></span>|<span data-ttu-id="ac515-113">Description</span><span class="sxs-lookup"><span data-stu-id="ac515-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="ac515-114">Vereist Element</span><span class="sxs-lookup"><span data-stu-id="ac515-114">Required Element</span></span>|
|[<span data-ttu-id="ac515-115">FirstLineHanging-Element voor Frame voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="ac515-115">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>](./firstlinehanging-element-for-frame-for-groupby-format.md)|<span data-ttu-id="ac515-116">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="ac515-116">Optional element.</span></span><br /><br /> <span data-ttu-id="ac515-117">Hiermee geeft u het aantal tekens in de eerste regel van gegevens is verplaatst naar de linkerkant.</span><span class="sxs-lookup"><span data-stu-id="ac515-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="ac515-118">FirstLineIndent-Element voor Frame voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="ac515-118">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>](./firstlineindent-element-for-frame-for-groupby-format.md)|<span data-ttu-id="ac515-119">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="ac515-119">Optional element.</span></span><br /><br /> <span data-ttu-id="ac515-120">Hiermee geeft u het aantal tekens in de eerste regel van gegevens is verplaatst naar de rechterkant.</span><span class="sxs-lookup"><span data-stu-id="ac515-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="ac515-121">LeftIndent-Element voor Frame voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="ac515-121">LeftIndent Element for Frame for GroupBy (Format)</span></span>](./leftindent-element-for-frame-for-groupby-format.md)|<span data-ttu-id="ac515-122">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="ac515-122">Optional element.</span></span><br /><br /> <span data-ttu-id="ac515-123">Hiermee geeft u op hoeveel tekens de gegevens van de linkermarge is verplaatst.</span><span class="sxs-lookup"><span data-stu-id="ac515-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|<span data-ttu-id="ac515-124">[RightIndent-Element voor Frame voor GroupBy (indeling)](./rightindent-element-for-frame-for-groupby-format.md)RightIndent-Element</span><span class="sxs-lookup"><span data-stu-id="ac515-124">[RightIndent Element for Frame for GroupBy (Format)](./rightindent-element-for-frame-for-groupby-format.md)RightIndent Element</span></span>|<span data-ttu-id="ac515-125">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="ac515-125">Optional element.</span></span><br /><br /> <span data-ttu-id="ac515-126">Hiermee geeft u op hoeveel tekens de gegevens van de rechtermarge is verplaatst.</span><span class="sxs-lookup"><span data-stu-id="ac515-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ac515-127">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="ac515-127">Parent Elements</span></span>

|<span data-ttu-id="ac515-128">Element</span><span class="sxs-lookup"><span data-stu-id="ac515-128">Element</span></span>|<span data-ttu-id="ac515-129">Description</span><span class="sxs-lookup"><span data-stu-id="ac515-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ac515-130">CustomItem-Element voor CustomEntry voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="ac515-130">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="ac515-131">Bepaalt welke gegevens worden weergegeven door het besturingselement en hoe deze wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="ac515-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ac515-132">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="ac515-132">Remarks</span></span>

<span data-ttu-id="ac515-133">U kunt geen opgeven de [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) en de [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) elementen in dezelfde `Frame` element.</span><span class="sxs-lookup"><span data-stu-id="ac515-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="ac515-134">Zie ook</span><span class="sxs-lookup"><span data-stu-id="ac515-134">See Also</span></span>

[<span data-ttu-id="ac515-135">FirstLineHanging-Element voor Frame voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="ac515-135">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>](./firstlinehanging-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="ac515-136">FirstLineIndent-Element voor Frame voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="ac515-136">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>](./firstlineindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="ac515-137">LeftIndent-Element voor Frame voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="ac515-137">LeftIndent Element for Frame for GroupBy (Format)</span></span>](./leftindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="ac515-138">RightIndent-Element voor Frame voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="ac515-138">RightIndent Element for Frame for GroupBy (Format)</span></span>](./rightindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="ac515-139">CustomItem-Element voor CustomEntry voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="ac515-139">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="ac515-140">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="ac515-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
