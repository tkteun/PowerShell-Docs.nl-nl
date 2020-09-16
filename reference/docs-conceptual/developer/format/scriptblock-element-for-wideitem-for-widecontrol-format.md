---
title: Script block-element voor WideItem voor WideControl (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: be649d6de0d2dfa6bad14f2d7476cced9cd6cb6d
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787594"
---
# <a name="scriptblock-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="ccc5c-102">Het element ScriptBlock voor WideItem voor WideControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="ccc5c-102">ScriptBlock Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="ccc5c-103">Hiermee geeft u het script op waarvan de waarde wordt weer gegeven in de brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="ccc5c-103">Specifies the script whose value is displayed in the wide view.</span></span>

<span data-ttu-id="ccc5c-104">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) WideControl element (indeling) WideEntries element (indeling) WideEntry element (indeling) WideItem element (indeling) script block element (indeling)</span><span class="sxs-lookup"><span data-stu-id="ccc5c-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format) ScriptBlock Element for WideItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ccc5c-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="ccc5c-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToExecute</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ccc5c-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="ccc5c-106">Attributes and Elements</span></span>

<span data-ttu-id="ccc5c-107">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `ScriptBlock` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="ccc5c-107">The following sections describe the attributes, child elements, and parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ccc5c-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="ccc5c-108">Attributes</span></span>

<span data-ttu-id="ccc5c-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="ccc5c-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ccc5c-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="ccc5c-110">Child Elements</span></span>

<span data-ttu-id="ccc5c-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="ccc5c-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ccc5c-112">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="ccc5c-112">Parent Elements</span></span>

|<span data-ttu-id="ccc5c-113">Element</span><span class="sxs-lookup"><span data-stu-id="ccc5c-113">Element</span></span>|<span data-ttu-id="ccc5c-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="ccc5c-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ccc5c-115">WideItem-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="ccc5c-115">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="ccc5c-116">Hiermee wordt de eigenschap of het script blok gedefinieerd waarvan de waarde wordt weer gegeven in de brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="ccc5c-116">Defines the property or script block whose value is displayed in the wide view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ccc5c-117">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="ccc5c-117">Text Value</span></span>

<span data-ttu-id="ccc5c-118">Geef het script op waarvan de waarde wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="ccc5c-118">Specify the script whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="ccc5c-119">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="ccc5c-119">Remarks</span></span>

<span data-ttu-id="ccc5c-120">Zie [een brede weer gave maken](./creating-a-wide-view.md)voor meer informatie over de onderdelen van een brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="ccc5c-120">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="ccc5c-121">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="ccc5c-121">Example</span></span>

<span data-ttu-id="ccc5c-122">In dit voor beeld ziet u een- `WideItem` element dat een script definieert waarvan de waarde in de weer gave wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="ccc5c-122">This example shows a `WideItem` element that defines a script whose value is displayed in the view.</span></span>

```xml
<WideItem>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
</WideItem>
```

## <a name="see-also"></a><span data-ttu-id="ccc5c-123">Zie ook</span><span class="sxs-lookup"><span data-stu-id="ccc5c-123">See Also</span></span>

[<span data-ttu-id="ccc5c-124">WideItem-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="ccc5c-124">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="ccc5c-125">Een brede weergave maken</span><span class="sxs-lookup"><span data-stu-id="ccc5c-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="ccc5c-126">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="ccc5c-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
