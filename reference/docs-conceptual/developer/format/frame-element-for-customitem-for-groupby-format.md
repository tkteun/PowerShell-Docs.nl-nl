---
title: Frame-element voor CustomItem voor GroupBy (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ab2a5379-299d-4c97-86a2-b639ea890fae
caps.latest.revision: 6
ms.openlocfilehash: 7f9066c0fe0954fadff9dc8f0c35a62c6710f516
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72354486"
---
# <a name="frame-element-for-customitem-for-groupby-format"></a><span data-ttu-id="e5f69-102">Het element Frame voor CustomItem voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="e5f69-102">Frame Element for CustomItem for GroupBy (Format)</span></span>

<span data-ttu-id="e5f69-103">Hiermee definieert u hoe de gegevens worden weer gegeven, zoals de gegevens naar links of rechts verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="e5f69-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="e5f69-104">Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="e5f69-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="e5f69-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element voor weer gave (indeling) GroupBy-element (Format) voor weer gave (indeling) CustomControl-element voor het element GroupBy (indeling) CustomEntries voor CustomControl voor het element GroupBy (Format) CustomEntry voor CustomControl voor het CustomItem-element van GroupBy (Format) voor CustomEntry voor het element GroupBy (Format) voor CustomItem voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="e5f69-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) Frame Element for CustomItem for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e5f69-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="e5f69-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e5f69-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="e5f69-107">Attributes and Elements</span></span>

<span data-ttu-id="e5f69-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `Frame` beschreven.</span><span class="sxs-lookup"><span data-stu-id="e5f69-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e5f69-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="e5f69-109">Attributes</span></span>

<span data-ttu-id="e5f69-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="e5f69-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e5f69-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="e5f69-111">Child Elements</span></span>

|<span data-ttu-id="e5f69-112">Element</span><span class="sxs-lookup"><span data-stu-id="e5f69-112">Element</span></span>|<span data-ttu-id="e5f69-113">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e5f69-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="e5f69-114">Vereist element</span><span class="sxs-lookup"><span data-stu-id="e5f69-114">Required Element</span></span>|
|[<span data-ttu-id="e5f69-115">FirstLineHanging-element voor frame voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="e5f69-115">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>](./firstlinehanging-element-for-frame-for-groupby-format.md)|<span data-ttu-id="e5f69-116">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="e5f69-116">Optional element.</span></span><br /><br /> <span data-ttu-id="e5f69-117">Geeft aan hoeveel tekens de eerste regel van de gegevens naar links verschuift.</span><span class="sxs-lookup"><span data-stu-id="e5f69-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="e5f69-118">FirstLineIndent-element voor frame voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="e5f69-118">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>](./firstlineindent-element-for-frame-for-groupby-format.md)|<span data-ttu-id="e5f69-119">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="e5f69-119">Optional element.</span></span><br /><br /> <span data-ttu-id="e5f69-120">Geeft aan hoeveel tekens de eerste regel van de gegevens naar rechts wordt geschoven.</span><span class="sxs-lookup"><span data-stu-id="e5f69-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="e5f69-121">LeftIndent-element voor frame voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="e5f69-121">LeftIndent Element for Frame for GroupBy (Format)</span></span>](./leftindent-element-for-frame-for-groupby-format.md)|<span data-ttu-id="e5f69-122">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="e5f69-122">Optional element.</span></span><br /><br /> <span data-ttu-id="e5f69-123">Hiermee geeft u op hoeveel tekens de gegevens van de linkermarge worden verplaatst.</span><span class="sxs-lookup"><span data-stu-id="e5f69-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|<span data-ttu-id="e5f69-124">[RightIndent-element voor frame voor GroupBy (indeling)](./rightindent-element-for-frame-for-groupby-format.md) RightIndent-element</span><span class="sxs-lookup"><span data-stu-id="e5f69-124">[RightIndent Element for Frame for GroupBy (Format)](./rightindent-element-for-frame-for-groupby-format.md)RightIndent Element</span></span>|<span data-ttu-id="e5f69-125">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="e5f69-125">Optional element.</span></span><br /><br /> <span data-ttu-id="e5f69-126">Hiermee geeft u op hoeveel tekens de gegevens van de rechter marge worden verplaatst.</span><span class="sxs-lookup"><span data-stu-id="e5f69-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e5f69-127">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="e5f69-127">Parent Elements</span></span>

|<span data-ttu-id="e5f69-128">Element</span><span class="sxs-lookup"><span data-stu-id="e5f69-128">Element</span></span>|<span data-ttu-id="e5f69-129">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e5f69-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e5f69-130">CustomItem-element voor CustomEntry voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="e5f69-130">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="e5f69-131">Hiermee definieert u welke gegevens worden weer gegeven door het besturings element en hoe deze worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="e5f69-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e5f69-132">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="e5f69-132">Remarks</span></span>

<span data-ttu-id="e5f69-133">U kunt de [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) -en [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) -elementen niet opgeven in hetzelfde `Frame` element.</span><span class="sxs-lookup"><span data-stu-id="e5f69-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="e5f69-134">Zie ook</span><span class="sxs-lookup"><span data-stu-id="e5f69-134">See Also</span></span>

[<span data-ttu-id="e5f69-135">FirstLineHanging-element voor frame voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="e5f69-135">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>](./firstlinehanging-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="e5f69-136">FirstLineIndent-element voor frame voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="e5f69-136">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>](./firstlineindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="e5f69-137">LeftIndent-element voor frame voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="e5f69-137">LeftIndent Element for Frame for GroupBy (Format)</span></span>](./leftindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="e5f69-138">RightIndent-element voor frame voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="e5f69-138">RightIndent Element for Frame for GroupBy (Format)</span></span>](./rightindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="e5f69-139">CustomItem-element voor CustomEntry voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="e5f69-139">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="e5f69-140">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="e5f69-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
