---
title: WideEntries-element voor WideControl (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 74383b288c945008c1d7b5119363a166c04802ae
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785044"
---
# <a name="wideentries-element-for-widecontrol-format"></a><span data-ttu-id="9ec90-102">Het element WideEntries voor WideControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="9ec90-102">WideEntries Element for WideControl (Format)</span></span>

<span data-ttu-id="9ec90-103">Biedt de definities van de brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="9ec90-103">Provides the definitions of the wide view.</span></span> <span data-ttu-id="9ec90-104">In de brede weer gave moeten een of meer definities worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="9ec90-104">The wide view must specify one or more definitions.</span></span>

<span data-ttu-id="9ec90-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) WideControl element (indeling) WideEntries element (indeling)</span><span class="sxs-lookup"><span data-stu-id="9ec90-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9ec90-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="9ec90-106">Syntax</span></span>

```xml
<WideEntries>
  <WideEntry>...</WideEntry>
</WideEntries>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="9ec90-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="9ec90-107">Attributes and Elements</span></span>

<span data-ttu-id="9ec90-108">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `WideEntries` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="9ec90-108">The following sections describe the attributes, child elements, and parent element of the `WideEntries` element.</span></span> <span data-ttu-id="9ec90-109">Er moet mini maal één onderliggend element worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="9ec90-109">At least one child element must be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="9ec90-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="9ec90-110">Attributes</span></span>

<span data-ttu-id="9ec90-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="9ec90-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9ec90-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="9ec90-112">Child Elements</span></span>

|<span data-ttu-id="9ec90-113">Element</span><span class="sxs-lookup"><span data-stu-id="9ec90-113">Element</span></span>|<span data-ttu-id="9ec90-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="9ec90-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9ec90-115">WideEntry-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="9ec90-115">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="9ec90-116">Biedt een definitie van de brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="9ec90-116">Provides a definition of the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="9ec90-117">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="9ec90-117">Parent Elements</span></span>

|<span data-ttu-id="9ec90-118">Element</span><span class="sxs-lookup"><span data-stu-id="9ec90-118">Element</span></span>|<span data-ttu-id="9ec90-119">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="9ec90-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9ec90-120">Het element WideControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="9ec90-120">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="9ec90-121">Hiermee wordt een brede lijst indeling (enkelvoudige waarde) gedefinieerd voor de weer gave.</span><span class="sxs-lookup"><span data-stu-id="9ec90-121">Defines a wide (single value) list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9ec90-122">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="9ec90-122">Remarks</span></span>

<span data-ttu-id="9ec90-123">Een brede weer gave is een lijst indeling waarin één eigenschaps waarde of script waarde voor elk object wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="9ec90-123">A wide view is a list format that displays a single property value or script value for each object.</span></span> <span data-ttu-id="9ec90-124">Zie [Wide View-onderdelen](./creating-a-wide-view.md)voor meer informatie over de onderdelen van een brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="9ec90-124">For more information about the components of a wide view, see [Wide View Components](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="9ec90-125">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="9ec90-125">Example</span></span>

<span data-ttu-id="9ec90-126">In het volgende voor beeld ziet u een- `WideEntries` element dat één `WideEntry` element definieert.</span><span class="sxs-lookup"><span data-stu-id="9ec90-126">The following example shows a `WideEntries` element that defines a single `WideEntry` element.</span></span> <span data-ttu-id="9ec90-127">Het `WideEntry` element bevat één `WideItem` element waarmee wordt gedefinieerd welke eigenschap of script waarde wordt weer gegeven in de weer gave.</span><span class="sxs-lookup"><span data-stu-id="9ec90-127">The `WideEntry` element contains a single `WideItem` element that defines what property or script value is displayed in the view.</span></span>

```xml
<WideControl>
  <WideEntries>
    <WideEntry>
      <WideItem>...</WideItem>
    <WideEntry>
  </WideEntries>
</WideControl>
```

<span data-ttu-id="9ec90-128">Zie [Wide View (Basic)](./wide-view-basic.md)voor een volledig voor beeld van een brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="9ec90-128">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9ec90-129">Zie ook</span><span class="sxs-lookup"><span data-stu-id="9ec90-129">See Also</span></span>

[<span data-ttu-id="9ec90-130">Een brede weergave maken</span><span class="sxs-lookup"><span data-stu-id="9ec90-130">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="9ec90-131">Het element WideControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="9ec90-131">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="9ec90-132">WideEntry-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="9ec90-132">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="9ec90-133">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="9ec90-133">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
