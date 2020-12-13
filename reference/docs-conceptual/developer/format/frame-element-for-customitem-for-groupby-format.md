---
ms.date: 09/13/2016
ms.topic: reference
title: Het element Frame voor CustomItem voor GroupBy (opmaak)
description: Het element Frame voor CustomItem voor GroupBy (opmaak)
ms.openlocfilehash: 86b51766974ebfcae06583ade237a77c6db92866
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652175"
---
# <a name="frame-element-for-customitem-for-groupby-format"></a><span data-ttu-id="73a5d-103">Het element Frame voor CustomItem voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="73a5d-103">Frame Element for CustomItem for GroupBy (Format)</span></span>

<span data-ttu-id="73a5d-104">Hiermee definieert u hoe de gegevens worden weer gegeven, zoals de gegevens naar links of rechts verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="73a5d-104">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="73a5d-105">Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="73a5d-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="73a5d-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element van het type GroupBy-element (Format) voor weer gave (indeling) CustomControl-element voor het CustomEntries-element van GroupBy (Format) voor CustomControl voor het element GroupBy (Format) CustomEntry element voor CustomControl voor het object GroupBy (Format) voor CustomEntry voor het element GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="73a5d-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) Frame Element for CustomItem for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="73a5d-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="73a5d-107">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="73a5d-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="73a5d-108">Attributes and Elements</span></span>

<span data-ttu-id="73a5d-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `Frame` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="73a5d-109">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="73a5d-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="73a5d-110">Attributes</span></span>

<span data-ttu-id="73a5d-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="73a5d-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="73a5d-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="73a5d-112">Child Elements</span></span>

|<span data-ttu-id="73a5d-113">Element</span><span class="sxs-lookup"><span data-stu-id="73a5d-113">Element</span></span>|<span data-ttu-id="73a5d-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="73a5d-114">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="73a5d-115">Vereist element</span><span class="sxs-lookup"><span data-stu-id="73a5d-115">Required Element</span></span>|
|[<span data-ttu-id="73a5d-116">Het element FirstLineHanging voor Frame voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="73a5d-116">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>](./firstlinehanging-element-for-frame-for-groupby-format.md)|<span data-ttu-id="73a5d-117">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="73a5d-117">Optional element.</span></span><br /><br /> <span data-ttu-id="73a5d-118">Geeft aan hoeveel tekens de eerste regel van de gegevens naar links verschuift.</span><span class="sxs-lookup"><span data-stu-id="73a5d-118">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="73a5d-119">Het element FirstLineIndent voor Frame voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="73a5d-119">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>](./firstlineindent-element-for-frame-for-groupby-format.md)|<span data-ttu-id="73a5d-120">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="73a5d-120">Optional element.</span></span><br /><br /> <span data-ttu-id="73a5d-121">Geeft aan hoeveel tekens de eerste regel van de gegevens naar rechts wordt geschoven.</span><span class="sxs-lookup"><span data-stu-id="73a5d-121">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="73a5d-122">Het element LeftIndent voor Frame voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="73a5d-122">LeftIndent Element for Frame for GroupBy (Format)</span></span>](./leftindent-element-for-frame-for-groupby-format.md)|<span data-ttu-id="73a5d-123">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="73a5d-123">Optional element.</span></span><br /><br /> <span data-ttu-id="73a5d-124">Hiermee geeft u op hoeveel tekens de gegevens van de linkermarge worden verplaatst.</span><span class="sxs-lookup"><span data-stu-id="73a5d-124">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|<span data-ttu-id="73a5d-125">[RightIndent-element voor frame voor GroupBy (indeling)](./rightindent-element-for-frame-for-groupby-format.md) RightIndent-element</span><span class="sxs-lookup"><span data-stu-id="73a5d-125">[RightIndent Element for Frame for GroupBy (Format)](./rightindent-element-for-frame-for-groupby-format.md)RightIndent Element</span></span>|<span data-ttu-id="73a5d-126">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="73a5d-126">Optional element.</span></span><br /><br /> <span data-ttu-id="73a5d-127">Hiermee geeft u op hoeveel tekens de gegevens van de rechter marge worden verplaatst.</span><span class="sxs-lookup"><span data-stu-id="73a5d-127">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="73a5d-128">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="73a5d-128">Parent Elements</span></span>

|<span data-ttu-id="73a5d-129">Element</span><span class="sxs-lookup"><span data-stu-id="73a5d-129">Element</span></span>|<span data-ttu-id="73a5d-130">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="73a5d-130">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="73a5d-131">Het element CustomItem voor CustomEntry voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="73a5d-131">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="73a5d-132">Hiermee definieert u welke gegevens worden weer gegeven door het besturings element en hoe deze worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="73a5d-132">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="73a5d-133">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="73a5d-133">Remarks</span></span>

<span data-ttu-id="73a5d-134">U kunt de [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) -en [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) -elementen in hetzelfde element niet opgeven `Frame` .</span><span class="sxs-lookup"><span data-stu-id="73a5d-134">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="73a5d-135">Zie ook</span><span class="sxs-lookup"><span data-stu-id="73a5d-135">See Also</span></span>

[<span data-ttu-id="73a5d-136">Het element FirstLineHanging voor Frame voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="73a5d-136">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>](./firstlinehanging-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="73a5d-137">Het element FirstLineIndent voor Frame voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="73a5d-137">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>](./firstlineindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="73a5d-138">Het element LeftIndent voor Frame voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="73a5d-138">LeftIndent Element for Frame for GroupBy (Format)</span></span>](./leftindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="73a5d-139">Het element RightIndent voor Frame voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="73a5d-139">RightIndent Element for Frame for GroupBy (Format)</span></span>](./rightindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="73a5d-140">Het element CustomItem voor CustomEntry voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="73a5d-140">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="73a5d-141">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="73a5d-141">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
