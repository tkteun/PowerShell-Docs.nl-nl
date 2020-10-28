---
ms.date: 09/13/2016
ms.topic: reference
title: Het element WideItem voor WideControl (opmaak)
description: Het element WideItem voor WideControl (opmaak)
ms.openlocfilehash: b9c416bbe3befcd689b8a2c0b72a8ff1301b9659
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92647798"
---
# <a name="wideitem-element-for-widecontrol-format"></a><span data-ttu-id="6ca37-103">Het element WideItem voor WideControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="6ca37-103">WideItem Element for WideControl (Format)</span></span>

<span data-ttu-id="6ca37-104">Hiermee wordt de eigenschap of het script gedefinieerd waarvan de waarde wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="6ca37-104">Defines the property or script whose value is displayed.</span></span>

<span data-ttu-id="6ca37-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) WideControl element (indeling) WideEntries element (indeling) WideEntry element (indeling) WideItem element (indeling)</span><span class="sxs-lookup"><span data-stu-id="6ca37-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6ca37-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="6ca37-106">Syntax</span></span>

```xml
<WideItem>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <FormatString>FormatPattern</FormatString>
</WideItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6ca37-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="6ca37-107">Attributes and Elements</span></span>

<span data-ttu-id="6ca37-108">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `WideItem` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="6ca37-108">The following sections describe the attributes, child elements, and the parent element of the `WideItem` element.</span></span> <span data-ttu-id="6ca37-109">Het `FormatString` element is optioneel.</span><span class="sxs-lookup"><span data-stu-id="6ca37-109">The `FormatString` element is optional.</span></span> <span data-ttu-id="6ca37-110">U moet echter een or- `PropertyName` `ScriptBlock` element opgeven, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="6ca37-110">However, you must specify a `PropertyName` or `ScriptBlock` element, but you cannot specify both.</span></span>

### <a name="attributes"></a><span data-ttu-id="6ca37-111">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="6ca37-111">Attributes</span></span>

<span data-ttu-id="6ca37-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="6ca37-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6ca37-113">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="6ca37-113">Child Elements</span></span>

|<span data-ttu-id="6ca37-114">Element</span><span class="sxs-lookup"><span data-stu-id="6ca37-114">Element</span></span>|<span data-ttu-id="6ca37-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="6ca37-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6ca37-116">Het element FormatString voor WideItem voor WideControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="6ca37-116">FormatString Element for WideItem for WideControl (Format)</span></span>](./formatstring-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="6ca37-117">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="6ca37-117">Optional element.</span></span><br /><br /> <span data-ttu-id="6ca37-118">Geeft een indelings patroon aan dat definieert hoe de eigenschap of script waarde wordt weer gegeven in de weer gave.</span><span class="sxs-lookup"><span data-stu-id="6ca37-118">Specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>|
|[<span data-ttu-id="6ca37-119">Het element PropertyName voor WideItem (indeling)</span><span class="sxs-lookup"><span data-stu-id="6ca37-119">PropertyName Element for WideItem (Format)</span></span>](./propertyname-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="6ca37-120">Hiermee geeft u de eigenschap op van het object waarvan de waarde wordt weer gegeven in de brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="6ca37-120">Specifies the property of the object whose value is displayed in the wide view.</span></span>|
|[<span data-ttu-id="6ca37-121">Script block-element voor WideItem (indeling)</span><span class="sxs-lookup"><span data-stu-id="6ca37-121">ScriptBlock Element for WideItem (Format)</span></span>](./scriptblock-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="6ca37-122">Hiermee geeft u het script op waarvan de waarde wordt weer gegeven in de brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="6ca37-122">Specifies the script whose value is displayed in the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="6ca37-123">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="6ca37-123">Parent Elements</span></span>

|<span data-ttu-id="6ca37-124">Element</span><span class="sxs-lookup"><span data-stu-id="6ca37-124">Element</span></span>|<span data-ttu-id="6ca37-125">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="6ca37-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6ca37-126">WideEntry-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="6ca37-126">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="6ca37-127">Biedt een definitie van de brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="6ca37-127">Provides a definition of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6ca37-128">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="6ca37-128">Remarks</span></span>

<span data-ttu-id="6ca37-129">Zie [brede weer gave](./creating-a-wide-view.md)voor meer informatie over de onderdelen van een brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="6ca37-129">For more information about the components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="6ca37-130">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="6ca37-130">Example</span></span>

<span data-ttu-id="6ca37-131">In het volgende voor beeld ziet u een- `WideEntry` element dat één `WideItem` element definieert.</span><span class="sxs-lookup"><span data-stu-id="6ca37-131">The following example shows a `WideEntry` element that defines a single `WideItem` element.</span></span> <span data-ttu-id="6ca37-132">Het `WideItem` element definieert de eigenschap of het script waarvan de waarde wordt weer gegeven in de weer gave.</span><span class="sxs-lookup"><span data-stu-id="6ca37-132">The `WideItem` element defines the property or script whose value is displayed in the view.</span></span>

```xml
<WideEntry>
  <WideItem>
    <PropertyName>ProcessName</PropertyName>
  </WideItem>
</WideEntry>
```

<span data-ttu-id="6ca37-133">Zie [Wide View (Basic)](./wide-view-basic.md)voor een volledig voor beeld van een brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="6ca37-133">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6ca37-134">Zie ook</span><span class="sxs-lookup"><span data-stu-id="6ca37-134">See Also</span></span>

[<span data-ttu-id="6ca37-135">Het element FormatString voor WideItem voor WideControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="6ca37-135">FormatString Element for WideItem for WideControl (Format)</span></span>](./formatstring-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="6ca37-136">Het element PropertyName voor WideItem (indeling)</span><span class="sxs-lookup"><span data-stu-id="6ca37-136">PropertyName Element for WideItem (Format)</span></span>](./propertyname-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="6ca37-137">Script block-element voor WideItem (indeling)</span><span class="sxs-lookup"><span data-stu-id="6ca37-137">ScriptBlock Element for WideItem (Format)</span></span>](./scriptblock-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="6ca37-138">WideEntry-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="6ca37-138">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="6ca37-139">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="6ca37-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
