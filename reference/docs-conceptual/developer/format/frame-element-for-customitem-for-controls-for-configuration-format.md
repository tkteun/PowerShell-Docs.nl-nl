---
ms.date: 09/13/2016
ms.topic: reference
title: Het element Frame voor CustomItem voor Besturingselementen voor Configuratie (opmaak)
description: Het element Frame voor CustomItem voor Besturingselementen voor Configuratie (opmaak)
ms.openlocfilehash: 85d095b9b0c25b68b2353bce56b85333aff91b98
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652246"
---
# <a name="frame-element-for-customitem-for-controls-for-configuration-format"></a><span data-ttu-id="a4fb5-103">Het element Frame voor CustomItem voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="a4fb5-103">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>

<span data-ttu-id="a4fb5-104">Hiermee definieert u hoe de gegevens worden weer gegeven, zoals de gegevens naar links of rechts verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="a4fb5-104">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="a4fb5-105">Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="a4fb5-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="a4fb5-106">Configuratie-element (Format) Controls element van configuratie (indeling) Control element voor besturings elementen voor configuratie (Format) CustomControl-element voor besturings element voor configuratie (indeling) CustomEntries element voor CustomControl voor configuratie (indeling) CustomEntry element voor CustomControl voor besturings elementen voor configuratie frame-element voor CustomItem voor besturings elementen voor configuratie van het type configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="a4fb5-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration Frame Element for CustomItem for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a4fb5-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="a4fb5-107">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a4fb5-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="a4fb5-108">Attributes and Elements</span></span>

<span data-ttu-id="a4fb5-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `Frame` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="a4fb5-109">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a4fb5-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="a4fb5-110">Attributes</span></span>

<span data-ttu-id="a4fb5-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="a4fb5-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a4fb5-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="a4fb5-112">Child Elements</span></span>

|<span data-ttu-id="a4fb5-113">Element</span><span class="sxs-lookup"><span data-stu-id="a4fb5-113">Element</span></span>|<span data-ttu-id="a4fb5-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="a4fb5-114">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="a4fb5-115">Vereist element</span><span class="sxs-lookup"><span data-stu-id="a4fb5-115">Required Element</span></span>|
|[<span data-ttu-id="a4fb5-116">Het element FirstLineHanging voor Frame voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="a4fb5-116">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="a4fb5-117">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="a4fb5-117">Optional element.</span></span><br /><br /> <span data-ttu-id="a4fb5-118">Geeft aan hoeveel tekens de eerste regel van de gegevens naar links verschuift.</span><span class="sxs-lookup"><span data-stu-id="a4fb5-118">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="a4fb5-119">Het element FirstLineIndent voor Frame voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="a4fb5-119">FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="a4fb5-120">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="a4fb5-120">Optional element.</span></span><br /><br /> <span data-ttu-id="a4fb5-121">Geeft aan hoeveel tekens de eerste regel van de gegevens naar rechts wordt geschoven.</span><span class="sxs-lookup"><span data-stu-id="a4fb5-121">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="a4fb5-122">Het element LeftIndent voor Frame voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="a4fb5-122">LeftIndent Element for Frame for Controls for Configuration (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="a4fb5-123">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="a4fb5-123">Optional element.</span></span><br /><br /> <span data-ttu-id="a4fb5-124">Hiermee geeft u op hoeveel tekens de gegevens van de linkermarge worden verplaatst.</span><span class="sxs-lookup"><span data-stu-id="a4fb5-124">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="a4fb5-125">Het element RightIndent voor Frame voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="a4fb5-125">RightIndent Element for Frame for Controls for Configuration (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="a4fb5-126">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="a4fb5-126">Optional element.</span></span><br /><br /> <span data-ttu-id="a4fb5-127">Hiermee geeft u op hoeveel tekens de gegevens van de rechter marge worden verplaatst.</span><span class="sxs-lookup"><span data-stu-id="a4fb5-127">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a4fb5-128">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="a4fb5-128">Parent Elements</span></span>

|<span data-ttu-id="a4fb5-129">Element</span><span class="sxs-lookup"><span data-stu-id="a4fb5-129">Element</span></span>|<span data-ttu-id="a4fb5-130">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="a4fb5-130">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a4fb5-131">CustomItem-element voor CustomEntry voor besturings elementen voor configuratie</span><span class="sxs-lookup"><span data-stu-id="a4fb5-131">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="a4fb5-132">Hiermee definieert u welke gegevens worden weer gegeven door het besturings element en hoe deze worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="a4fb5-132">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a4fb5-133">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="a4fb5-133">Remarks</span></span>

<span data-ttu-id="a4fb5-134">U kunt de [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) -en [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) -elementen in hetzelfde element niet opgeven `Frame` .</span><span class="sxs-lookup"><span data-stu-id="a4fb5-134">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="a4fb5-135">Zie ook</span><span class="sxs-lookup"><span data-stu-id="a4fb5-135">See Also</span></span>

[<span data-ttu-id="a4fb5-136">Het element FirstLineHanging voor Frame voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="a4fb5-136">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="a4fb5-137">Het element FirstLineIndent voor Frame voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="a4fb5-137">FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="a4fb5-138">Het element LeftIndent voor Frame voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="a4fb5-138">LeftIndent Element for Frame for Controls for Configuration (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="a4fb5-139">Het element RightIndent voor Frame voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="a4fb5-139">RightIndent Element for Frame for Controls for Configuration (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="a4fb5-140">CustomItem-element voor CustomEntry voor besturings elementen voor configuratie</span><span class="sxs-lookup"><span data-stu-id="a4fb5-140">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="a4fb5-141">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="a4fb5-141">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
