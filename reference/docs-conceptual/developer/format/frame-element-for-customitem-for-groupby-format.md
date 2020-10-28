---
ms.date: 09/13/2016
ms.topic: reference
title: Het element Frame voor CustomItem voor GroupBy (opmaak)
description: Het element Frame voor CustomItem voor GroupBy (opmaak)
ms.openlocfilehash: 86b51766974ebfcae06583ade237a77c6db92866
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92652175"
---
# <a name="frame-element-for-customitem-for-groupby-format"></a><span data-ttu-id="c65ae-103">Het element Frame voor CustomItem voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c65ae-103">Frame Element for CustomItem for GroupBy (Format)</span></span>

<span data-ttu-id="c65ae-104">Hiermee definieert u hoe de gegevens worden weer gegeven, zoals de gegevens naar links of rechts verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="c65ae-104">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="c65ae-105">Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c65ae-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="c65ae-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element van het type GroupBy-element (Format) voor weer gave (indeling) CustomControl-element voor het CustomEntries-element van GroupBy (Format) voor CustomControl voor het element GroupBy (Format) CustomEntry element voor CustomControl voor het object GroupBy (Format) voor CustomEntry voor het element GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="c65ae-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) Frame Element for CustomItem for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c65ae-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="c65ae-107">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c65ae-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="c65ae-108">Attributes and Elements</span></span>

<span data-ttu-id="c65ae-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `Frame` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="c65ae-109">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c65ae-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="c65ae-110">Attributes</span></span>

<span data-ttu-id="c65ae-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="c65ae-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c65ae-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="c65ae-112">Child Elements</span></span>

|<span data-ttu-id="c65ae-113">Element</span><span class="sxs-lookup"><span data-stu-id="c65ae-113">Element</span></span>|<span data-ttu-id="c65ae-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="c65ae-114">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="c65ae-115">Vereist element</span><span class="sxs-lookup"><span data-stu-id="c65ae-115">Required Element</span></span>|
|[<span data-ttu-id="c65ae-116">Het element FirstLineHanging voor Frame voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c65ae-116">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>](./firstlinehanging-element-for-frame-for-groupby-format.md)|<span data-ttu-id="c65ae-117">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="c65ae-117">Optional element.</span></span><br /><br /> <span data-ttu-id="c65ae-118">Geeft aan hoeveel tekens de eerste regel van de gegevens naar links verschuift.</span><span class="sxs-lookup"><span data-stu-id="c65ae-118">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="c65ae-119">Het element FirstLineIndent voor Frame voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c65ae-119">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>](./firstlineindent-element-for-frame-for-groupby-format.md)|<span data-ttu-id="c65ae-120">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="c65ae-120">Optional element.</span></span><br /><br /> <span data-ttu-id="c65ae-121">Geeft aan hoeveel tekens de eerste regel van de gegevens naar rechts wordt geschoven.</span><span class="sxs-lookup"><span data-stu-id="c65ae-121">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="c65ae-122">Het element LeftIndent voor Frame voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c65ae-122">LeftIndent Element for Frame for GroupBy (Format)</span></span>](./leftindent-element-for-frame-for-groupby-format.md)|<span data-ttu-id="c65ae-123">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="c65ae-123">Optional element.</span></span><br /><br /> <span data-ttu-id="c65ae-124">Hiermee geeft u op hoeveel tekens de gegevens van de linkermarge worden verplaatst.</span><span class="sxs-lookup"><span data-stu-id="c65ae-124">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|<span data-ttu-id="c65ae-125">[RightIndent-element voor frame voor GroupBy (indeling)](./rightindent-element-for-frame-for-groupby-format.md) RightIndent-element</span><span class="sxs-lookup"><span data-stu-id="c65ae-125">[RightIndent Element for Frame for GroupBy (Format)](./rightindent-element-for-frame-for-groupby-format.md)RightIndent Element</span></span>|<span data-ttu-id="c65ae-126">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="c65ae-126">Optional element.</span></span><br /><br /> <span data-ttu-id="c65ae-127">Hiermee geeft u op hoeveel tekens de gegevens van de rechter marge worden verplaatst.</span><span class="sxs-lookup"><span data-stu-id="c65ae-127">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c65ae-128">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="c65ae-128">Parent Elements</span></span>

|<span data-ttu-id="c65ae-129">Element</span><span class="sxs-lookup"><span data-stu-id="c65ae-129">Element</span></span>|<span data-ttu-id="c65ae-130">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="c65ae-130">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c65ae-131">Het element CustomItem voor CustomEntry voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c65ae-131">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="c65ae-132">Hiermee definieert u welke gegevens worden weer gegeven door het besturings element en hoe deze worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c65ae-132">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c65ae-133">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="c65ae-133">Remarks</span></span>

<span data-ttu-id="c65ae-134">U kunt de [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) -en [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) -elementen in hetzelfde element niet opgeven `Frame` .</span><span class="sxs-lookup"><span data-stu-id="c65ae-134">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="c65ae-135">Zie ook</span><span class="sxs-lookup"><span data-stu-id="c65ae-135">See Also</span></span>

[<span data-ttu-id="c65ae-136">Het element FirstLineHanging voor Frame voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c65ae-136">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>](./firstlinehanging-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="c65ae-137">Het element FirstLineIndent voor Frame voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c65ae-137">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>](./firstlineindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="c65ae-138">Het element LeftIndent voor Frame voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c65ae-138">LeftIndent Element for Frame for GroupBy (Format)</span></span>](./leftindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="c65ae-139">Het element RightIndent voor Frame voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c65ae-139">RightIndent Element for Frame for GroupBy (Format)</span></span>](./rightindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="c65ae-140">Het element CustomItem voor CustomEntry voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c65ae-140">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="c65ae-141">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="c65ae-141">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
