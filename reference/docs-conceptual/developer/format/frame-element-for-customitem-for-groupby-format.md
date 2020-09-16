---
title: Frame-element voor CustomItem voor GroupBy (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 1568236ff7b6142f7e41be70a3ae5e28307cf790
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785758"
---
# <a name="frame-element-for-customitem-for-groupby-format"></a><span data-ttu-id="82a24-102">Het element Frame voor CustomItem voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="82a24-102">Frame Element for CustomItem for GroupBy (Format)</span></span>

<span data-ttu-id="82a24-103">Hiermee definieert u hoe de gegevens worden weer gegeven, zoals de gegevens naar links of rechts verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="82a24-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="82a24-104">Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="82a24-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="82a24-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element van het type GroupBy-element (Format) voor weer gave (indeling) CustomControl-element voor het CustomEntries-element van GroupBy (Format) voor CustomControl voor het element GroupBy (Format) CustomEntry element voor CustomControl voor het object GroupBy (Format) voor CustomEntry voor het element GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="82a24-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) Frame Element for CustomItem for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="82a24-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="82a24-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="82a24-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="82a24-107">Attributes and Elements</span></span>

<span data-ttu-id="82a24-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `Frame` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="82a24-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="82a24-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="82a24-109">Attributes</span></span>

<span data-ttu-id="82a24-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="82a24-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="82a24-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="82a24-111">Child Elements</span></span>

|<span data-ttu-id="82a24-112">Element</span><span class="sxs-lookup"><span data-stu-id="82a24-112">Element</span></span>|<span data-ttu-id="82a24-113">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="82a24-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="82a24-114">Vereist element</span><span class="sxs-lookup"><span data-stu-id="82a24-114">Required Element</span></span>|
|[<span data-ttu-id="82a24-115">Het element FirstLineHanging voor Frame voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="82a24-115">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>](./firstlinehanging-element-for-frame-for-groupby-format.md)|<span data-ttu-id="82a24-116">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="82a24-116">Optional element.</span></span><br /><br /> <span data-ttu-id="82a24-117">Geeft aan hoeveel tekens de eerste regel van de gegevens naar links verschuift.</span><span class="sxs-lookup"><span data-stu-id="82a24-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="82a24-118">Het element FirstLineIndent voor Frame voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="82a24-118">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>](./firstlineindent-element-for-frame-for-groupby-format.md)|<span data-ttu-id="82a24-119">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="82a24-119">Optional element.</span></span><br /><br /> <span data-ttu-id="82a24-120">Geeft aan hoeveel tekens de eerste regel van de gegevens naar rechts wordt geschoven.</span><span class="sxs-lookup"><span data-stu-id="82a24-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="82a24-121">Het element LeftIndent voor Frame voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="82a24-121">LeftIndent Element for Frame for GroupBy (Format)</span></span>](./leftindent-element-for-frame-for-groupby-format.md)|<span data-ttu-id="82a24-122">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="82a24-122">Optional element.</span></span><br /><br /> <span data-ttu-id="82a24-123">Hiermee geeft u op hoeveel tekens de gegevens van de linkermarge worden verplaatst.</span><span class="sxs-lookup"><span data-stu-id="82a24-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|<span data-ttu-id="82a24-124">[RightIndent-element voor frame voor GroupBy (indeling)](./rightindent-element-for-frame-for-groupby-format.md) RightIndent-element</span><span class="sxs-lookup"><span data-stu-id="82a24-124">[RightIndent Element for Frame for GroupBy (Format)](./rightindent-element-for-frame-for-groupby-format.md)RightIndent Element</span></span>|<span data-ttu-id="82a24-125">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="82a24-125">Optional element.</span></span><br /><br /> <span data-ttu-id="82a24-126">Hiermee geeft u op hoeveel tekens de gegevens van de rechter marge worden verplaatst.</span><span class="sxs-lookup"><span data-stu-id="82a24-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="82a24-127">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="82a24-127">Parent Elements</span></span>

|<span data-ttu-id="82a24-128">Element</span><span class="sxs-lookup"><span data-stu-id="82a24-128">Element</span></span>|<span data-ttu-id="82a24-129">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="82a24-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="82a24-130">Het element CustomItem voor CustomEntry voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="82a24-130">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="82a24-131">Hiermee definieert u welke gegevens worden weer gegeven door het besturings element en hoe deze worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="82a24-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="82a24-132">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="82a24-132">Remarks</span></span>

<span data-ttu-id="82a24-133">U kunt de [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) -en [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) -elementen in hetzelfde element niet opgeven `Frame` .</span><span class="sxs-lookup"><span data-stu-id="82a24-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="82a24-134">Zie ook</span><span class="sxs-lookup"><span data-stu-id="82a24-134">See Also</span></span>

[<span data-ttu-id="82a24-135">Het element FirstLineHanging voor Frame voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="82a24-135">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>](./firstlinehanging-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="82a24-136">Het element FirstLineIndent voor Frame voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="82a24-136">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>](./firstlineindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="82a24-137">Het element LeftIndent voor Frame voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="82a24-137">LeftIndent Element for Frame for GroupBy (Format)</span></span>](./leftindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="82a24-138">Het element RightIndent voor Frame voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="82a24-138">RightIndent Element for Frame for GroupBy (Format)</span></span>](./rightindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="82a24-139">Het element CustomItem voor CustomEntry voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="82a24-139">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="82a24-140">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="82a24-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
