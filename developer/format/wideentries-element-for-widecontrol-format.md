---
title: WideEntries-Element voor WideControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c4bff45-0960-4b3a-95e7-47f2cee03ac5
caps.latest.revision: 12
ms.openlocfilehash: 083f3c8df8136858e32778ed231943ef983e47aa
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56844903"
---
# <a name="wideentries-element-for-widecontrol-format"></a><span data-ttu-id="747f7-102">Het element WideEntries voor WideControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="747f7-102">WideEntries Element for WideControl (Format)</span></span>

<span data-ttu-id="747f7-103">Bevat de definities van de brede weergave.</span><span class="sxs-lookup"><span data-stu-id="747f7-103">Provides the definitions of the wide view.</span></span> <span data-ttu-id="747f7-104">De brede weergave moet een of meer netwerkdefinities opgeven.</span><span class="sxs-lookup"><span data-stu-id="747f7-104">The wide view must specify one or more definitions.</span></span>

<span data-ttu-id="747f7-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format)</span><span class="sxs-lookup"><span data-stu-id="747f7-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="747f7-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="747f7-106">Syntax</span></span>

```xml
<WideEntries>
  <WideEntry>...</WideEntry>
</WideEntries>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="747f7-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="747f7-107">Attributes and Elements</span></span>

<span data-ttu-id="747f7-108">De volgende secties worden de kenmerken, de onderliggende elementen en het bovenliggende element van de `WideEntries` element.</span><span class="sxs-lookup"><span data-stu-id="747f7-108">The following sections describe the attributes, child elements, and parent element of the `WideEntries` element.</span></span> <span data-ttu-id="747f7-109">Ten minste één onderliggend element moet worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="747f7-109">At least one child element must be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="747f7-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="747f7-110">Attributes</span></span>

<span data-ttu-id="747f7-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="747f7-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="747f7-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="747f7-112">Child Elements</span></span>

|<span data-ttu-id="747f7-113">Element</span><span class="sxs-lookup"><span data-stu-id="747f7-113">Element</span></span>|<span data-ttu-id="747f7-114">Description</span><span class="sxs-lookup"><span data-stu-id="747f7-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="747f7-115">WideEntry-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="747f7-115">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="747f7-116">Bevat een definitie van de brede weergave.</span><span class="sxs-lookup"><span data-stu-id="747f7-116">Provides a definition of the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="747f7-117">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="747f7-117">Parent Elements</span></span>

|<span data-ttu-id="747f7-118">Element</span><span class="sxs-lookup"><span data-stu-id="747f7-118">Element</span></span>|<span data-ttu-id="747f7-119">Description</span><span class="sxs-lookup"><span data-stu-id="747f7-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="747f7-120">WideControl-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="747f7-120">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="747f7-121">Definieert een breed (één waarde) lijstweergave voor de weergave.</span><span class="sxs-lookup"><span data-stu-id="747f7-121">Defines a wide (single value) list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="747f7-122">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="747f7-122">Remarks</span></span>

<span data-ttu-id="747f7-123">Een brede weergave wordt een lijst met-indeling die een waarde van één eigenschap of Scriptwaarde voor elk object wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="747f7-123">A wide view is a list format that displays a single property value or script value for each object.</span></span> <span data-ttu-id="747f7-124">Zie voor meer informatie over de onderdelen van een brede weergave [brede weergave onderdelen](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="747f7-124">For more information about the components of a wide view, see [Wide View Components](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="747f7-125">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="747f7-125">Example</span></span>

<span data-ttu-id="747f7-126">Het volgende voorbeeld wordt een `WideEntries` element waarin één `WideEntry` element.</span><span class="sxs-lookup"><span data-stu-id="747f7-126">The following example shows a `WideEntries` element that defines a single `WideEntry` element.</span></span> <span data-ttu-id="747f7-127">De `WideEntry` element bevat één `WideItem` element waarmee wordt gedefinieerd welke waarde voor eigenschap of het script wordt weergegeven in de weergave.</span><span class="sxs-lookup"><span data-stu-id="747f7-127">The `WideEntry` element contains a single `WideItem` element that defines what property or script value is displayed in the view.</span></span>

```xml
<WideControl>
  <WideEntries>
    <WideEntry>
      <WideItem>...</WideItem>
    <WideEntry>
  </WideEntries>
</WideControl>
```

<span data-ttu-id="747f7-128">Zie voor een compleet voorbeeld van een brede weergave, [brede weergave (basis)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="747f7-128">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="747f7-129">Zie ook</span><span class="sxs-lookup"><span data-stu-id="747f7-129">See Also</span></span>

[<span data-ttu-id="747f7-130">Het maken van een brede weergave</span><span class="sxs-lookup"><span data-stu-id="747f7-130">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="747f7-131">WideControl-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="747f7-131">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="747f7-132">WideEntry-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="747f7-132">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="747f7-133">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="747f7-133">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
