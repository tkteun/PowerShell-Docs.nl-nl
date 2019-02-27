---
title: WideItem-Element voor WideControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17352fc4-ba83-4f04-86bc-f591765d85a8
caps.latest.revision: 18
ms.openlocfilehash: fa9eda3ea1028c27dbfb3eb04747af3b817c1a81
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851448"
---
# <a name="wideitem-element-for-widecontrol-format"></a><span data-ttu-id="a3601-102">Het element WideItem voor WideControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="a3601-102">WideItem Element for WideControl (Format)</span></span>

<span data-ttu-id="a3601-103">Hiermee definieert de eigenschap of het script waarvan de waarde wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="a3601-103">Defines the property or script whose value is displayed.</span></span>

<span data-ttu-id="a3601-104">Configuratie Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) WideControl-Element (indeling) WideEntries-Element (indeling) WideEntry-Element (indeling) WideItem-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="a3601-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a3601-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="a3601-105">Syntax</span></span>

```xml
<WideItem>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <FormatString>FormatPattern</FormatString>
</WideItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a3601-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="a3601-106">Attributes and Elements</span></span>

<span data-ttu-id="a3601-107">De volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van de `WideItem` element.</span><span class="sxs-lookup"><span data-stu-id="a3601-107">The following sections describe the attributes, child elements, and the parent element of the `WideItem` element.</span></span> <span data-ttu-id="a3601-108">De `FormatString` element is optioneel.</span><span class="sxs-lookup"><span data-stu-id="a3601-108">The `FormatString` element is optional.</span></span> <span data-ttu-id="a3601-109">Echter, moet u een `PropertyName` of `ScriptBlock` element, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="a3601-109">However, you must specify a `PropertyName` or `ScriptBlock` element, but you cannot specify both.</span></span>

### <a name="attributes"></a><span data-ttu-id="a3601-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="a3601-110">Attributes</span></span>

<span data-ttu-id="a3601-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="a3601-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a3601-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="a3601-112">Child Elements</span></span>

|<span data-ttu-id="a3601-113">Element</span><span class="sxs-lookup"><span data-stu-id="a3601-113">Element</span></span>|<span data-ttu-id="a3601-114">Description</span><span class="sxs-lookup"><span data-stu-id="a3601-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a3601-115">FormatString-Element voor WideItem voor WideControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="a3601-115">FormatString Element for WideItem for WideControl (Format)</span></span>](./formatstring-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="a3601-116">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="a3601-116">Optional element.</span></span><br /><br /> <span data-ttu-id="a3601-117">Hiermee geeft u een indeling patroon waarmee wordt gedefinieerd hoe de waarde voor eigenschap of het script wordt weergegeven in de weergave.</span><span class="sxs-lookup"><span data-stu-id="a3601-117">Specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>|
|[<span data-ttu-id="a3601-118">PropertyName-Element voor WideItem (indeling)</span><span class="sxs-lookup"><span data-stu-id="a3601-118">PropertyName Element for WideItem (Format)</span></span>](./propertyname-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="a3601-119">Hiermee geeft u de eigenschap van het object waarvan de waarde wordt weergegeven in de brede weergave.</span><span class="sxs-lookup"><span data-stu-id="a3601-119">Specifies the property of the object whose value is displayed in the wide view.</span></span>|
|[<span data-ttu-id="a3601-120">ScriptBlock-Element voor WideItem (indeling)</span><span class="sxs-lookup"><span data-stu-id="a3601-120">ScriptBlock Element for WideItem (Format)</span></span>](./scriptblock-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="a3601-121">Hiermee geeft u het script waarvan de waarde wordt weergegeven in de brede weergave.</span><span class="sxs-lookup"><span data-stu-id="a3601-121">Specifies the script whose value is displayed in the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a3601-122">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="a3601-122">Parent Elements</span></span>

|<span data-ttu-id="a3601-123">Element</span><span class="sxs-lookup"><span data-stu-id="a3601-123">Element</span></span>|<span data-ttu-id="a3601-124">Description</span><span class="sxs-lookup"><span data-stu-id="a3601-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a3601-125">WideEntry-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="a3601-125">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="a3601-126">Bevat een definitie van de brede weergave.</span><span class="sxs-lookup"><span data-stu-id="a3601-126">Provides a definition of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a3601-127">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="a3601-127">Remarks</span></span>

<span data-ttu-id="a3601-128">Zie voor meer informatie over de onderdelen van een brede weergave [brede weergave](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="a3601-128">For more information about the components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="a3601-129">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="a3601-129">Example</span></span>

<span data-ttu-id="a3601-130">Het volgende voorbeeld wordt een `WideEntry` element waarin één `WideItem` element.</span><span class="sxs-lookup"><span data-stu-id="a3601-130">The following example shows a `WideEntry` element that defines a single `WideItem` element.</span></span> <span data-ttu-id="a3601-131">De `WideItem` element wordt gedefinieerd voor de eigenschap of het script waarvan de waarde wordt weergegeven in de weergave.</span><span class="sxs-lookup"><span data-stu-id="a3601-131">The `WideItem` element defines the property or script whose value is displayed in the view.</span></span>

```xml
<WideEntry>
  <WideItem>
    <PropertyName>ProcessName</PropertyName>
  </WideItem>
</WideEntry>
```

<span data-ttu-id="a3601-132">Zie voor een compleet voorbeeld van een brede weergave, [brede weergave (basis)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="a3601-132">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a3601-133">Zie ook</span><span class="sxs-lookup"><span data-stu-id="a3601-133">See Also</span></span>

[<span data-ttu-id="a3601-134">FormatString-Element voor WideItem voor WideControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="a3601-134">FormatString Element for WideItem for WideControl (Format)</span></span>](./formatstring-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="a3601-135">PropertyName-Element voor WideItem (indeling)</span><span class="sxs-lookup"><span data-stu-id="a3601-135">PropertyName Element for WideItem (Format)</span></span>](./propertyname-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="a3601-136">ScriptBlock-Element voor WideItem (indeling)</span><span class="sxs-lookup"><span data-stu-id="a3601-136">ScriptBlock Element for WideItem (Format)</span></span>](./scriptblock-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="a3601-137">WideEntry-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="a3601-137">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="a3601-138">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="a3601-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
