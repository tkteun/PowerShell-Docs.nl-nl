---
ms.date: 09/13/2016
ms.topic: reference
title: Het element WideEntries voor WideControl (opmaak)
description: Het element WideEntries voor WideControl (opmaak)
ms.openlocfilehash: 567b8acdd0d2e8d5daaef2c31b4fe4ce38c23a47
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92651240"
---
# <a name="wideentries-element-for-widecontrol-format"></a><span data-ttu-id="d8f0e-103">Het element WideEntries voor WideControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="d8f0e-103">WideEntries Element for WideControl (Format)</span></span>

<span data-ttu-id="d8f0e-104">Biedt de definities van de brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="d8f0e-104">Provides the definitions of the wide view.</span></span> <span data-ttu-id="d8f0e-105">In de brede weer gave moeten een of meer definities worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="d8f0e-105">The wide view must specify one or more definitions.</span></span>

<span data-ttu-id="d8f0e-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) WideControl element (indeling) WideEntries element (indeling)</span><span class="sxs-lookup"><span data-stu-id="d8f0e-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d8f0e-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="d8f0e-107">Syntax</span></span>

```xml
<WideEntries>
  <WideEntry>...</WideEntry>
</WideEntries>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="d8f0e-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="d8f0e-108">Attributes and Elements</span></span>

<span data-ttu-id="d8f0e-109">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `WideEntries` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="d8f0e-109">The following sections describe the attributes, child elements, and parent element of the `WideEntries` element.</span></span> <span data-ttu-id="d8f0e-110">Er moet mini maal één onderliggend element worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="d8f0e-110">At least one child element must be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="d8f0e-111">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="d8f0e-111">Attributes</span></span>

<span data-ttu-id="d8f0e-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="d8f0e-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d8f0e-113">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="d8f0e-113">Child Elements</span></span>

|<span data-ttu-id="d8f0e-114">Element</span><span class="sxs-lookup"><span data-stu-id="d8f0e-114">Element</span></span>|<span data-ttu-id="d8f0e-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="d8f0e-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d8f0e-116">WideEntry-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="d8f0e-116">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="d8f0e-117">Biedt een definitie van de brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="d8f0e-117">Provides a definition of the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d8f0e-118">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="d8f0e-118">Parent Elements</span></span>

|<span data-ttu-id="d8f0e-119">Element</span><span class="sxs-lookup"><span data-stu-id="d8f0e-119">Element</span></span>|<span data-ttu-id="d8f0e-120">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="d8f0e-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d8f0e-121">Het element WideControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="d8f0e-121">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="d8f0e-122">Hiermee wordt een brede lijst indeling (enkelvoudige waarde) gedefinieerd voor de weer gave.</span><span class="sxs-lookup"><span data-stu-id="d8f0e-122">Defines a wide (single value) list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d8f0e-123">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="d8f0e-123">Remarks</span></span>

<span data-ttu-id="d8f0e-124">Een brede weer gave is een lijst indeling waarin één eigenschaps waarde of script waarde voor elk object wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="d8f0e-124">A wide view is a list format that displays a single property value or script value for each object.</span></span> <span data-ttu-id="d8f0e-125">Zie [Wide View-onderdelen](./creating-a-wide-view.md)voor meer informatie over de onderdelen van een brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="d8f0e-125">For more information about the components of a wide view, see [Wide View Components](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="d8f0e-126">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="d8f0e-126">Example</span></span>

<span data-ttu-id="d8f0e-127">In het volgende voor beeld ziet u een- `WideEntries` element dat één `WideEntry` element definieert.</span><span class="sxs-lookup"><span data-stu-id="d8f0e-127">The following example shows a `WideEntries` element that defines a single `WideEntry` element.</span></span> <span data-ttu-id="d8f0e-128">Het `WideEntry` element bevat één `WideItem` element waarmee wordt gedefinieerd welke eigenschap of script waarde wordt weer gegeven in de weer gave.</span><span class="sxs-lookup"><span data-stu-id="d8f0e-128">The `WideEntry` element contains a single `WideItem` element that defines what property or script value is displayed in the view.</span></span>

```xml
<WideControl>
  <WideEntries>
    <WideEntry>
      <WideItem>...</WideItem>
    <WideEntry>
  </WideEntries>
</WideControl>
```

<span data-ttu-id="d8f0e-129">Zie [Wide View (Basic)](./wide-view-basic.md)voor een volledig voor beeld van een brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="d8f0e-129">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d8f0e-130">Zie ook</span><span class="sxs-lookup"><span data-stu-id="d8f0e-130">See Also</span></span>

[<span data-ttu-id="d8f0e-131">Een brede weergave maken</span><span class="sxs-lookup"><span data-stu-id="d8f0e-131">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="d8f0e-132">Het element WideControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="d8f0e-132">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="d8f0e-133">WideEntry-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="d8f0e-133">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="d8f0e-134">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="d8f0e-134">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
