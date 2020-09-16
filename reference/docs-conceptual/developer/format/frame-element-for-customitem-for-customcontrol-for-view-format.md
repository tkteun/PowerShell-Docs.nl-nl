---
title: Frame-element voor CustomItem voor CustomControl voor weer gave (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 4864ea1a865f77c9de6e495d7e8296e81c19b366
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781440"
---
# <a name="frame-element-for-customitem-for-customcontrol-for-view-format"></a><span data-ttu-id="f3ea6-102">Het element Frame voor CustomItem voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="f3ea6-102">Frame Element for CustomItem for CustomControl for View (Format)</span></span>

<span data-ttu-id="f3ea6-103">Hiermee definieert u hoe de gegevens worden weer gegeven, zoals de gegevens naar links of rechts verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="f3ea6-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="f3ea6-104">Dit element wordt gebruikt bij het definiëren van een aangepaste beheer weergave.</span><span class="sxs-lookup"><span data-stu-id="f3ea6-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="f3ea6-105">Configuratie-element (indeling) ViewDefinitions element (indeling) weer gave element (indeling) CustomControl element (Format) CustomEntries element voor CustomControl voor weer gave (Format) CustomEntry-element voor CustomEntries voor weer gave (Format) CustomItem element voor CustomEntry voor CustomControlView (Format) voor CustomItem voor de weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="f3ea6-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for CustomControlView (Format) Frame Element for CustomItem for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f3ea6-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="f3ea6-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f3ea6-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="f3ea6-107">Attributes and Elements</span></span>

<span data-ttu-id="f3ea6-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `Frame` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="f3ea6-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f3ea6-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="f3ea6-109">Attributes</span></span>

<span data-ttu-id="f3ea6-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="f3ea6-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f3ea6-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="f3ea6-111">Child Elements</span></span>

|<span data-ttu-id="f3ea6-112">Element</span><span class="sxs-lookup"><span data-stu-id="f3ea6-112">Element</span></span>|<span data-ttu-id="f3ea6-113">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="f3ea6-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="f3ea6-114">Vereist element</span><span class="sxs-lookup"><span data-stu-id="f3ea6-114">Required Element</span></span>|
|[<span data-ttu-id="f3ea6-115">FirstLineHanging-element</span><span class="sxs-lookup"><span data-stu-id="f3ea6-115">FirstLineHanging Element</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="f3ea6-116">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="f3ea6-116">Optional element.</span></span><br /><br /> <span data-ttu-id="f3ea6-117">Geeft aan hoeveel tekens de eerste regel van de gegevens naar links verschuift.</span><span class="sxs-lookup"><span data-stu-id="f3ea6-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="f3ea6-118">FirstLineIndent-element</span><span class="sxs-lookup"><span data-stu-id="f3ea6-118">FirstLineIndent Element</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="f3ea6-119">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="f3ea6-119">Optional element.</span></span><br /><br /> <span data-ttu-id="f3ea6-120">Geeft aan hoeveel tekens de eerste regel van de gegevens naar rechts wordt geschoven.</span><span class="sxs-lookup"><span data-stu-id="f3ea6-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="f3ea6-121">LeftIndent-element</span><span class="sxs-lookup"><span data-stu-id="f3ea6-121">LeftIndent Element</span></span>](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="f3ea6-122">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="f3ea6-122">Optional element.</span></span><br /><br /> <span data-ttu-id="f3ea6-123">Hiermee geeft u op hoeveel tekens de gegevens van de linkermarge worden verplaatst.</span><span class="sxs-lookup"><span data-stu-id="f3ea6-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="f3ea6-124">RightIndent-element</span><span class="sxs-lookup"><span data-stu-id="f3ea6-124">RightIndent Element</span></span>](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="f3ea6-125">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="f3ea6-125">Optional element.</span></span><br /><br /> <span data-ttu-id="f3ea6-126">Hiermee geeft u op hoeveel tekens de gegevens van de rechter marge worden verplaatst.</span><span class="sxs-lookup"><span data-stu-id="f3ea6-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f3ea6-127">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="f3ea6-127">Parent Elements</span></span>

|<span data-ttu-id="f3ea6-128">Element</span><span class="sxs-lookup"><span data-stu-id="f3ea6-128">Element</span></span>|<span data-ttu-id="f3ea6-129">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="f3ea6-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f3ea6-130">CustomItem-element voor CustomEntry voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="f3ea6-130">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="f3ea6-131">Hiermee definieert u welke gegevens worden weer gegeven door het besturings element en hoe deze worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="f3ea6-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f3ea6-132">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="f3ea6-132">Remarks</span></span>

<span data-ttu-id="f3ea6-133">U kunt de [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) -en [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) -elementen in hetzelfde element niet opgeven `Frame` .</span><span class="sxs-lookup"><span data-stu-id="f3ea6-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="f3ea6-134">Zie ook</span><span class="sxs-lookup"><span data-stu-id="f3ea6-134">See Also</span></span>

[<span data-ttu-id="f3ea6-135">FirstLineHanging-element</span><span class="sxs-lookup"><span data-stu-id="f3ea6-135">FirstLineHanging Element</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="f3ea6-136">FirstLineIndent-element</span><span class="sxs-lookup"><span data-stu-id="f3ea6-136">FirstLineIndent Element</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="f3ea6-137">LeftIndent-element</span><span class="sxs-lookup"><span data-stu-id="f3ea6-137">LeftIndent Element</span></span>](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="f3ea6-138">RightIndent-element</span><span class="sxs-lookup"><span data-stu-id="f3ea6-138">RightIndent Element</span></span>](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="f3ea6-139">CustomItem-element voor CustomEntry voor weer gave (indeling)</span><span class="sxs-lookup"><span data-stu-id="f3ea6-139">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="f3ea6-140">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="f3ea6-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
