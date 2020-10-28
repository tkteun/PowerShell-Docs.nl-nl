---
ms.date: 09/13/2016
ms.topic: reference
title: Het element ScriptBlock voor WideItem voor WideControl (opmaak)
description: Het element ScriptBlock voor WideItem voor WideControl (opmaak)
ms.openlocfilehash: 68e47926e5e6b846c8a0a3dbc16d1f0d59f11dee
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92659871"
---
# <a name="scriptblock-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="1a557-103">Het element ScriptBlock voor WideItem voor WideControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="1a557-103">ScriptBlock Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="1a557-104">Hiermee geeft u het script op waarvan de waarde wordt weer gegeven in de brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="1a557-104">Specifies the script whose value is displayed in the wide view.</span></span>

<span data-ttu-id="1a557-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) WideControl element (indeling) WideEntries element (indeling) WideEntry element (indeling) WideItem element (indeling) script block element (indeling)</span><span class="sxs-lookup"><span data-stu-id="1a557-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format) ScriptBlock Element for WideItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1a557-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="1a557-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToExecute</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1a557-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="1a557-107">Attributes and Elements</span></span>

<span data-ttu-id="1a557-108">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `ScriptBlock` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="1a557-108">The following sections describe the attributes, child elements, and parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1a557-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="1a557-109">Attributes</span></span>

<span data-ttu-id="1a557-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="1a557-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1a557-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="1a557-111">Child Elements</span></span>

<span data-ttu-id="1a557-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="1a557-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1a557-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="1a557-113">Parent Elements</span></span>

|<span data-ttu-id="1a557-114">Element</span><span class="sxs-lookup"><span data-stu-id="1a557-114">Element</span></span>|<span data-ttu-id="1a557-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="1a557-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1a557-116">WideItem-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="1a557-116">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="1a557-117">Hiermee wordt de eigenschap of het script blok gedefinieerd waarvan de waarde wordt weer gegeven in de brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="1a557-117">Defines the property or script block whose value is displayed in the wide view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1a557-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="1a557-118">Text Value</span></span>

<span data-ttu-id="1a557-119">Geef het script op waarvan de waarde wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="1a557-119">Specify the script whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="1a557-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="1a557-120">Remarks</span></span>

<span data-ttu-id="1a557-121">Zie [een brede weer gave maken](./creating-a-wide-view.md)voor meer informatie over de onderdelen van een brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="1a557-121">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="1a557-122">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="1a557-122">Example</span></span>

<span data-ttu-id="1a557-123">In dit voor beeld ziet u een- `WideItem` element dat een script definieert waarvan de waarde in de weer gave wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="1a557-123">This example shows a `WideItem` element that defines a script whose value is displayed in the view.</span></span>

```xml
<WideItem>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
</WideItem>
```

## <a name="see-also"></a><span data-ttu-id="1a557-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="1a557-124">See Also</span></span>

[<span data-ttu-id="1a557-125">WideItem-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="1a557-125">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="1a557-126">Een brede weergave maken</span><span class="sxs-lookup"><span data-stu-id="1a557-126">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="1a557-127">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="1a557-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
