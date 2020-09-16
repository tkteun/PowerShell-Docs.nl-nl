---
title: Script block-element voor lijst item voor ListControl (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 249d3e36b4246b7baa410815122f8e30340f1862
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785452"
---
# <a name="scriptblock-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="0b063-102">Het element ScriptBlock voor ListItem voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="0b063-102">ScriptBlock Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="0b063-103">Hiermee geeft u het script op waarvan de waarde wordt weer gegeven in de rij.</span><span class="sxs-lookup"><span data-stu-id="0b063-103">Specifies the script whose value is displayed in the row.</span></span>

<span data-ttu-id="0b063-104">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) item type-element (indeling) van het element list item (Format) voor de ListControl (indeling) element list item voor ListControl (Format) List items element voor List entry voor ListControl (Format) lijst item element voor de ListControl (indeling) script block-element</span><span class="sxs-lookup"><span data-stu-id="0b063-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ScriptBlock Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0b063-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="0b063-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0b063-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="0b063-106">Attributes and Elements</span></span>

<span data-ttu-id="0b063-107">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `ScriptBlock` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="0b063-107">The following sections describe the attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0b063-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="0b063-108">Attributes</span></span>

<span data-ttu-id="0b063-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="0b063-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0b063-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="0b063-110">Child Elements</span></span>

<span data-ttu-id="0b063-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="0b063-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0b063-112">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="0b063-112">Parent Elements</span></span>

|<span data-ttu-id="0b063-113">Element</span><span class="sxs-lookup"><span data-stu-id="0b063-113">Element</span></span>|<span data-ttu-id="0b063-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="0b063-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0b063-115">Lijst item-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="0b063-115">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="0b063-116">Hiermee wordt de eigenschap of het script gedefinieerd waarvan de waarde wordt weer gegeven in een rij van de lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="0b063-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="0b063-117">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="0b063-117">Text Value</span></span>

<span data-ttu-id="0b063-118">Geef het script op waarvan de waarde wordt weer gegeven in de rij.</span><span class="sxs-lookup"><span data-stu-id="0b063-118">Specify the script whose value is displayed in the row.</span></span>

## <a name="remarks"></a><span data-ttu-id="0b063-119">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="0b063-119">Remarks</span></span>

<span data-ttu-id="0b063-120">Als dit element is opgegeven, kunt u het kenmerk [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) niet opgeven.</span><span class="sxs-lookup"><span data-stu-id="0b063-120">When this element is specified, you cannot specify the [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element.</span></span>

<span data-ttu-id="0b063-121">Zie [lijst weergave](./creating-a-list-view.md)voor meer informatie over het opgeven van scripts in een lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="0b063-121">For more information about specifying scripts in a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="0b063-122">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="0b063-122">Example</span></span>

<span data-ttu-id="0b063-123">In het volgende voor beeld ziet u hoe u de eigenschap kunt opgeven waarvan de waarde wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="0b063-123">The following example shows how to specify the property whose value is displayed.</span></span>

```xml
<ListItem>
  <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="0b063-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="0b063-124">See Also</span></span>

[<span data-ttu-id="0b063-125">Het element PropertyName voor ListItem voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="0b063-125">PropertyName Element for ListItem for ListControl (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="0b063-126">Een lijstweergave maken</span><span class="sxs-lookup"><span data-stu-id="0b063-126">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="0b063-127">Het element ListItem voor ListItems voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="0b063-127">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="0b063-128">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="0b063-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
