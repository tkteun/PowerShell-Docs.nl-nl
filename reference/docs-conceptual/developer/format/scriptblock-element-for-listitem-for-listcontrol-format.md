---
title: Script block-element voor lijst item voor ListControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 74e30938-00ef-46fd-84e5-f0a83706a50e
caps.latest.revision: 11
ms.openlocfilehash: 76b600256af3f957f7fe0578f9fef810262aa5d5
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355788"
---
# <a name="scriptblock-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="39f85-102">Het element ScriptBlock voor ListItem voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="39f85-102">ScriptBlock Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="39f85-103">Hiermee geeft u het script op waarvan de waarde wordt weer gegeven in de rij.</span><span class="sxs-lookup"><span data-stu-id="39f85-103">Specifies the script whose value is displayed in the row.</span></span>

<span data-ttu-id="39f85-104">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) bestand van ListControl element (indeling). element (Format) voor ListControl voor ListControl (Format) lijst item-element voor list items voor ListControl (Format) script block-element voor de lijst item voor ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="39f85-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ScriptBlock Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="39f85-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="39f85-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="39f85-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="39f85-106">Attributes and Elements</span></span>

<span data-ttu-id="39f85-107">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het element `ScriptBlock` beschreven.</span><span class="sxs-lookup"><span data-stu-id="39f85-107">The following sections describe the attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="39f85-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="39f85-108">Attributes</span></span>

<span data-ttu-id="39f85-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="39f85-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="39f85-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="39f85-110">Child Elements</span></span>

<span data-ttu-id="39f85-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="39f85-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="39f85-112">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="39f85-112">Parent Elements</span></span>

|<span data-ttu-id="39f85-113">Element</span><span class="sxs-lookup"><span data-stu-id="39f85-113">Element</span></span>|<span data-ttu-id="39f85-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="39f85-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="39f85-115">Lijst item-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="39f85-115">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="39f85-116">Hiermee wordt de eigenschap of het script gedefinieerd waarvan de waarde wordt weer gegeven in een rij van de lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="39f85-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="39f85-117">Tekst waarde</span><span class="sxs-lookup"><span data-stu-id="39f85-117">Text Value</span></span>

<span data-ttu-id="39f85-118">Geef het script op waarvan de waarde wordt weer gegeven in de rij.</span><span class="sxs-lookup"><span data-stu-id="39f85-118">Specify the script whose value is displayed in the row.</span></span>

## <a name="remarks"></a><span data-ttu-id="39f85-119">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="39f85-119">Remarks</span></span>

<span data-ttu-id="39f85-120">Als dit element is opgegeven, kunt u het kenmerk [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) niet opgeven.</span><span class="sxs-lookup"><span data-stu-id="39f85-120">When this element is specified, you cannot specify the [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element.</span></span>

<span data-ttu-id="39f85-121">Zie [lijst weergave](./creating-a-list-view.md)voor meer informatie over het opgeven van scripts in een lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="39f85-121">For more information about specifying scripts in a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="39f85-122">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="39f85-122">Example</span></span>

<span data-ttu-id="39f85-123">In het volgende voor beeld ziet u hoe u de eigenschap kunt opgeven waarvan de waarde wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="39f85-123">The following example shows how to specify the property whose value is displayed.</span></span>

```xml
<ListItem>
  <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="39f85-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="39f85-124">See Also</span></span>

[<span data-ttu-id="39f85-125">PropertyName-element voor lijst item voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="39f85-125">PropertyName Element for ListItem for ListControl (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="39f85-126">Een lijst weergave maken</span><span class="sxs-lookup"><span data-stu-id="39f85-126">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="39f85-127">Lijst item-element voor list items voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="39f85-127">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="39f85-128">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="39f85-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
