---
title: ScriptBlock-Element voor WideItem voor WideControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e00e8f36-76f2-49a0-9b02-3a2a7fceb2dd
caps.latest.revision: 8
ms.openlocfilehash: 6534e9dbfbe0dedf60dadd6467cff9ad9b447ba4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064200"
---
# <a name="scriptblock-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="e5399-102">Het element ScriptBlock voor WideItem voor WideControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="e5399-102">ScriptBlock Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="e5399-103">Hiermee geeft u het script waarvan de waarde wordt weergegeven in de brede weergave.</span><span class="sxs-lookup"><span data-stu-id="e5399-103">Specifies the script whose value is displayed in the wide view.</span></span>

<span data-ttu-id="e5399-104">Configuratie Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) WideControl-Element (indeling) WideEntries-Element (indeling) WideEntry-Element (indeling) WideItem Element (indeling) ScriptBlock-Element voor WideItem (indeling)</span><span class="sxs-lookup"><span data-stu-id="e5399-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format) ScriptBlock Element for WideItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e5399-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="e5399-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToExecute</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e5399-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="e5399-106">Attributes and Elements</span></span>

<span data-ttu-id="e5399-107">De volgende secties worden de kenmerken, de onderliggende elementen en het bovenliggende element van de `ScriptBlock` element.</span><span class="sxs-lookup"><span data-stu-id="e5399-107">The following sections describe the attributes, child elements, and parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e5399-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="e5399-108">Attributes</span></span>

<span data-ttu-id="e5399-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="e5399-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e5399-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="e5399-110">Child Elements</span></span>

<span data-ttu-id="e5399-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="e5399-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e5399-112">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="e5399-112">Parent Elements</span></span>

|<span data-ttu-id="e5399-113">Element</span><span class="sxs-lookup"><span data-stu-id="e5399-113">Element</span></span>|<span data-ttu-id="e5399-114">Description</span><span class="sxs-lookup"><span data-stu-id="e5399-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e5399-115">WideItem-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="e5399-115">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="e5399-116">Hiermee definieert u de eigenschap of script blok waarvan de waarde wordt weergegeven in de brede weergave.</span><span class="sxs-lookup"><span data-stu-id="e5399-116">Defines the property or script block whose value is displayed in the wide view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e5399-117">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="e5399-117">Text Value</span></span>

<span data-ttu-id="e5399-118">Geef het script waarvan de waarde wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="e5399-118">Specify the script whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="e5399-119">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="e5399-119">Remarks</span></span>

<span data-ttu-id="e5399-120">Zie voor meer informatie over de onderdelen van een brede weergave [het maken van een brede weergave](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="e5399-120">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="e5399-121">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="e5399-121">Example</span></span>

<span data-ttu-id="e5399-122">In dit voorbeeld ziet u een `WideItem` element dat een script waarvan de waarde wordt weergegeven in de weergave wordt gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="e5399-122">This example shows a `WideItem` element that defines a script whose value is displayed in the view.</span></span>

```xml
<WideItem>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
</WideItem>
```

## <a name="see-also"></a><span data-ttu-id="e5399-123">Zie ook</span><span class="sxs-lookup"><span data-stu-id="e5399-123">See Also</span></span>

[<span data-ttu-id="e5399-124">WideItem-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="e5399-124">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="e5399-125">Het maken van een brede weergave</span><span class="sxs-lookup"><span data-stu-id="e5399-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="e5399-126">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="e5399-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
