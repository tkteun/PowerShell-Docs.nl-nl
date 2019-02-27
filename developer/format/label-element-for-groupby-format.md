---
title: Element een label voor GroupBy (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3351d237-e8c2-4ec5-9500-4eceadb407c2
caps.latest.revision: 11
ms.openlocfilehash: e7158711c60d13c745bbdfab9b1b9fc7d98b34e2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851287"
---
# <a name="label-element-for-groupby-format"></a><span data-ttu-id="3bfda-102">Het element Label voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="3bfda-102">Label Element for GroupBy (Format)</span></span>

<span data-ttu-id="3bfda-103">Hiermee geeft u een label dat wordt weergegeven wanneer een nieuwe groep is opgetreden.</span><span class="sxs-lookup"><span data-stu-id="3bfda-103">Specifies a label that is displayed when a new group is encountered.</span></span>

<span data-ttu-id="3bfda-104">Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) GroupBy Element voor weergave (indeling) Label-Element voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="3bfda-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) Label Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3bfda-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="3bfda-105">Syntax</span></span>

```xml
<Label>DisplayedLabel</Label>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3bfda-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="3bfda-106">Attributes and Elements</span></span>

<span data-ttu-id="3bfda-107">De volgende secties worden de kenmerken, de onderliggende elementen en het bovenliggende element van de `Label` element.</span><span class="sxs-lookup"><span data-stu-id="3bfda-107">The following sections describe the attributes, child elements, and parent element of the `Label` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3bfda-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="3bfda-108">Attributes</span></span>

<span data-ttu-id="3bfda-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="3bfda-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3bfda-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="3bfda-110">Child Elements</span></span>

<span data-ttu-id="3bfda-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="3bfda-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="3bfda-112">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="3bfda-112">Parent Elements</span></span>

|<span data-ttu-id="3bfda-113">Element</span><span class="sxs-lookup"><span data-stu-id="3bfda-113">Element</span></span>|<span data-ttu-id="3bfda-114">Description</span><span class="sxs-lookup"><span data-stu-id="3bfda-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3bfda-115">GroupBy-Element voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="3bfda-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="3bfda-116">Hiermee definieert u hoe een nieuwe groep objecten worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="3bfda-116">Defines how a new group of objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="3bfda-117">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="3bfda-117">Text Value</span></span>

<span data-ttu-id="3bfda-118">Geef de tekst die wordt weergegeven als Windows PowerShell wordt een nieuwe eigenschap of Scriptwaarde aangetroffen.</span><span class="sxs-lookup"><span data-stu-id="3bfda-118">Specify the text that is displayed whenever Windows PowerShell encounters a new property or script value.</span></span>

## <a name="remarks"></a><span data-ttu-id="3bfda-119">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="3bfda-119">Remarks</span></span>

<span data-ttu-id="3bfda-120">Windows PowerShell bevat naast de tekst die is opgegeven door dit element, de nieuwe waarde die wordt gestart van de groep en voegt een lege regel voor en na de groep.</span><span class="sxs-lookup"><span data-stu-id="3bfda-120">In addition to the text specified by this element, Windows PowerShell displays the new value that starts the group, and adds a blank line before and after the group.</span></span>

## <a name="example"></a><span data-ttu-id="3bfda-121">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="3bfda-121">Example</span></span>

<span data-ttu-id="3bfda-122">Het volgende voorbeeld toont het label voor een nieuwe groep.</span><span class="sxs-lookup"><span data-stu-id="3bfda-122">The following example shows the label for a new group.</span></span> <span data-ttu-id="3bfda-123">Het weergegeven label zou er ongeveer als volgt: `Service Type: NewValueofProperty`</span><span class="sxs-lookup"><span data-stu-id="3bfda-123">The displayed label would look similar to this: `Service Type: NewValueofProperty`</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="3bfda-124">Zie voor een voorbeeld van een volledige opmaak bestand waarin dit element [brede weergave (GroupBy)](./wide-view-groupby.md).</span><span class="sxs-lookup"><span data-stu-id="3bfda-124">For an example of a complete formatting file that includes this element, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3bfda-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="3bfda-125">See Also</span></span>

[<span data-ttu-id="3bfda-126">GroupBy-Element voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="3bfda-126">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="3bfda-127">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="3bfda-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
