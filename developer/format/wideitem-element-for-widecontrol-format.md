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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083634"
---
# <a name="wideitem-element-for-widecontrol-format"></a><span data-ttu-id="19f5a-102">Het element WideItem voor WideControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="19f5a-102">WideItem Element for WideControl (Format)</span></span>

<span data-ttu-id="19f5a-103">Hiermee definieert de eigenschap of het script waarvan de waarde wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="19f5a-103">Defines the property or script whose value is displayed.</span></span>

<span data-ttu-id="19f5a-104">Configuratie Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) WideControl-Element (indeling) WideEntries-Element (indeling) WideEntry-Element (indeling) WideItem-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="19f5a-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="19f5a-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="19f5a-105">Syntax</span></span>

```xml
<WideItem>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <FormatString>FormatPattern</FormatString>
</WideItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="19f5a-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="19f5a-106">Attributes and Elements</span></span>

<span data-ttu-id="19f5a-107">De volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van de `WideItem` element.</span><span class="sxs-lookup"><span data-stu-id="19f5a-107">The following sections describe the attributes, child elements, and the parent element of the `WideItem` element.</span></span> <span data-ttu-id="19f5a-108">De `FormatString` element is optioneel.</span><span class="sxs-lookup"><span data-stu-id="19f5a-108">The `FormatString` element is optional.</span></span> <span data-ttu-id="19f5a-109">Echter, moet u een `PropertyName` of `ScriptBlock` element, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="19f5a-109">However, you must specify a `PropertyName` or `ScriptBlock` element, but you cannot specify both.</span></span>

### <a name="attributes"></a><span data-ttu-id="19f5a-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="19f5a-110">Attributes</span></span>

<span data-ttu-id="19f5a-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="19f5a-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="19f5a-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="19f5a-112">Child Elements</span></span>

|<span data-ttu-id="19f5a-113">Element</span><span class="sxs-lookup"><span data-stu-id="19f5a-113">Element</span></span>|<span data-ttu-id="19f5a-114">Description</span><span class="sxs-lookup"><span data-stu-id="19f5a-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="19f5a-115">FormatString-Element voor WideItem voor WideControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="19f5a-115">FormatString Element for WideItem for WideControl (Format)</span></span>](./formatstring-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="19f5a-116">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="19f5a-116">Optional element.</span></span><br /><br /> <span data-ttu-id="19f5a-117">Hiermee geeft u een indeling patroon waarmee wordt gedefinieerd hoe de waarde voor eigenschap of het script wordt weergegeven in de weergave.</span><span class="sxs-lookup"><span data-stu-id="19f5a-117">Specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>|
|[<span data-ttu-id="19f5a-118">PropertyName-Element voor WideItem (indeling)</span><span class="sxs-lookup"><span data-stu-id="19f5a-118">PropertyName Element for WideItem (Format)</span></span>](./propertyname-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="19f5a-119">Hiermee geeft u de eigenschap van het object waarvan de waarde wordt weergegeven in de brede weergave.</span><span class="sxs-lookup"><span data-stu-id="19f5a-119">Specifies the property of the object whose value is displayed in the wide view.</span></span>|
|[<span data-ttu-id="19f5a-120">ScriptBlock-Element voor WideItem (indeling)</span><span class="sxs-lookup"><span data-stu-id="19f5a-120">ScriptBlock Element for WideItem (Format)</span></span>](./scriptblock-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="19f5a-121">Hiermee geeft u het script waarvan de waarde wordt weergegeven in de brede weergave.</span><span class="sxs-lookup"><span data-stu-id="19f5a-121">Specifies the script whose value is displayed in the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="19f5a-122">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="19f5a-122">Parent Elements</span></span>

|<span data-ttu-id="19f5a-123">Element</span><span class="sxs-lookup"><span data-stu-id="19f5a-123">Element</span></span>|<span data-ttu-id="19f5a-124">Description</span><span class="sxs-lookup"><span data-stu-id="19f5a-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="19f5a-125">WideEntry-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="19f5a-125">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="19f5a-126">Bevat een definitie van de brede weergave.</span><span class="sxs-lookup"><span data-stu-id="19f5a-126">Provides a definition of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="19f5a-127">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="19f5a-127">Remarks</span></span>

<span data-ttu-id="19f5a-128">Zie voor meer informatie over de onderdelen van een brede weergave [brede weergave](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="19f5a-128">For more information about the components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="19f5a-129">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="19f5a-129">Example</span></span>

<span data-ttu-id="19f5a-130">Het volgende voorbeeld wordt een `WideEntry` element waarin één `WideItem` element.</span><span class="sxs-lookup"><span data-stu-id="19f5a-130">The following example shows a `WideEntry` element that defines a single `WideItem` element.</span></span> <span data-ttu-id="19f5a-131">De `WideItem` element wordt gedefinieerd voor de eigenschap of het script waarvan de waarde wordt weergegeven in de weergave.</span><span class="sxs-lookup"><span data-stu-id="19f5a-131">The `WideItem` element defines the property or script whose value is displayed in the view.</span></span>

```xml
<WideEntry>
  <WideItem>
    <PropertyName>ProcessName</PropertyName>
  </WideItem>
</WideEntry>
```

<span data-ttu-id="19f5a-132">Zie voor een compleet voorbeeld van een brede weergave, [brede weergave (basis)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="19f5a-132">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="19f5a-133">Zie ook</span><span class="sxs-lookup"><span data-stu-id="19f5a-133">See Also</span></span>

[<span data-ttu-id="19f5a-134">FormatString-Element voor WideItem voor WideControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="19f5a-134">FormatString Element for WideItem for WideControl (Format)</span></span>](./formatstring-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="19f5a-135">PropertyName-Element voor WideItem (indeling)</span><span class="sxs-lookup"><span data-stu-id="19f5a-135">PropertyName Element for WideItem (Format)</span></span>](./propertyname-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="19f5a-136">ScriptBlock-Element voor WideItem (indeling)</span><span class="sxs-lookup"><span data-stu-id="19f5a-136">ScriptBlock Element for WideItem (Format)</span></span>](./scriptblock-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="19f5a-137">WideEntry-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="19f5a-137">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="19f5a-138">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="19f5a-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
