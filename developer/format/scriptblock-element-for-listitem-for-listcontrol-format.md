---
title: ScriptBlock-Element voor ListItem voor ListControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 74e30938-00ef-46fd-84e5-f0a83706a50e
caps.latest.revision: 11
ms.openlocfilehash: 76b600256af3f957f7fe0578f9fef810262aa5d5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846499"
---
# <a name="scriptblock-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="3faec-102">Het element ScriptBlock voor ListItem voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="3faec-102">ScriptBlock Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="3faec-103">Hiermee geeft u het script waarvan de waarde wordt weergegeven in de rij.</span><span class="sxs-lookup"><span data-stu-id="3faec-103">Specifies the script whose value is displayed in the row.</span></span>

<span data-ttu-id="3faec-104">Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) ListControl Element (indeling) ListEntries Element voor ListControl (indeling) ListEntry-Element voor ListEntries voor ListControl (indeling) ListItems Element voor ListEntry voor ListControl (indeling) ListItem Element voor ListItems voor ListControl (indeling) ScriptBlock Element voor ListItem voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="3faec-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ScriptBlock Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3faec-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="3faec-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3faec-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="3faec-106">Attributes and Elements</span></span>

<span data-ttu-id="3faec-107">De volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van de `ScriptBlock` element.</span><span class="sxs-lookup"><span data-stu-id="3faec-107">The following sections describe the attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3faec-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="3faec-108">Attributes</span></span>

<span data-ttu-id="3faec-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="3faec-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3faec-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="3faec-110">Child Elements</span></span>

<span data-ttu-id="3faec-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="3faec-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="3faec-112">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="3faec-112">Parent Elements</span></span>

|<span data-ttu-id="3faec-113">Element</span><span class="sxs-lookup"><span data-stu-id="3faec-113">Element</span></span>|<span data-ttu-id="3faec-114">Description</span><span class="sxs-lookup"><span data-stu-id="3faec-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3faec-115">ListItem Element (Format)</span><span class="sxs-lookup"><span data-stu-id="3faec-115">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="3faec-116">Hiermee definieert de eigenschap of het script waarvan de waarde wordt weergegeven in een rij in de lijstweergave.</span><span class="sxs-lookup"><span data-stu-id="3faec-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="3faec-117">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="3faec-117">Text Value</span></span>

<span data-ttu-id="3faec-118">Geef het script waarvan de waarde wordt weergegeven in de rij.</span><span class="sxs-lookup"><span data-stu-id="3faec-118">Specify the script whose value is displayed in the row.</span></span>

## <a name="remarks"></a><span data-ttu-id="3faec-119">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="3faec-119">Remarks</span></span>

<span data-ttu-id="3faec-120">Wanneer dit element is opgegeven, wordt u niet opgeven de [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element.</span><span class="sxs-lookup"><span data-stu-id="3faec-120">When this element is specified, you cannot specify the [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element.</span></span>

<span data-ttu-id="3faec-121">Zie voor meer informatie over het opgeven van scripts in een lijst weergeven [lijstweergave](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="3faec-121">For more information about specifying scripts in a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="3faec-122">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="3faec-122">Example</span></span>

<span data-ttu-id="3faec-123">Het volgende voorbeeld ziet hoe u de eigenschap waarvan de waarde wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="3faec-123">The following example shows how to specify the property whose value is displayed.</span></span>

```xml
<ListItem>
  <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="3faec-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="3faec-124">See Also</span></span>

[<span data-ttu-id="3faec-125">PropertyName-Element voor ListItem voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="3faec-125">PropertyName Element for ListItem for ListControl (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="3faec-126">Het maken van een lijst weergeven</span><span class="sxs-lookup"><span data-stu-id="3faec-126">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="3faec-127">Lijstitem-Element voor ListItems voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="3faec-127">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="3faec-128">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="3faec-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
