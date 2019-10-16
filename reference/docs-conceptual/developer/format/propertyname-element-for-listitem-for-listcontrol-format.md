---
title: PropertyName-element voor lijst item voor ListControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 01ae8cbe-acdc-4043-bd6e-1118a5691a55
caps.latest.revision: 12
ms.openlocfilehash: 405184f7bdbf1955f1df7766bf2723c244dcc27f
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72354087"
---
# <a name="propertyname-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="e30a9-102">Het element PropertyName voor ListItem voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="e30a9-102">PropertyName Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="e30a9-103">Hiermee geeft u de .NET-eigenschap op waarvan de waarde wordt weer gegeven in de lijst.</span><span class="sxs-lookup"><span data-stu-id="e30a9-103">Specifies the .NET property whose value is displayed in the list.</span></span>

<span data-ttu-id="e30a9-104">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) bestand van ListControl-element (indeling) element (indeling) List item (Format) element (notatie) List items element (Format) lijst item element (indeling) eigenschap naam Lijst item (indeling)</span><span class="sxs-lookup"><span data-stu-id="e30a9-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) ListItems Element (Format) ListItem Element (Format) PropertyName Element for ListItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e30a9-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="e30a9-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e30a9-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="e30a9-106">Attributes and Elements</span></span>

<span data-ttu-id="e30a9-107">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het element `PropertyName` beschreven.</span><span class="sxs-lookup"><span data-stu-id="e30a9-107">The following sections describe the attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e30a9-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="e30a9-108">Attributes</span></span>

<span data-ttu-id="e30a9-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="e30a9-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e30a9-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="e30a9-110">Child Elements</span></span>

<span data-ttu-id="e30a9-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="e30a9-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e30a9-112">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="e30a9-112">Parent Elements</span></span>

|<span data-ttu-id="e30a9-113">Element</span><span class="sxs-lookup"><span data-stu-id="e30a9-113">Element</span></span>|<span data-ttu-id="e30a9-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e30a9-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e30a9-115">Lijst item-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="e30a9-115">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="e30a9-116">Hiermee wordt de eigenschap of het script gedefinieerd waarvan de waarde wordt weer gegeven in de rij van de lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="e30a9-116">Defines the property or script whose value is displayed in the row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e30a9-117">Tekst waarde</span><span class="sxs-lookup"><span data-stu-id="e30a9-117">Text Value</span></span>

<span data-ttu-id="e30a9-118">Geef de naam op van de eigenschap waarvan de waarde wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="e30a9-118">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="e30a9-119">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="e30a9-119">Remarks</span></span>

<span data-ttu-id="e30a9-120">Als dit element is opgegeven, kunt u het [script Block](./scriptblock-element-for-listitem-for-listcontrol-format.md) -element niet opgeven.</span><span class="sxs-lookup"><span data-stu-id="e30a9-120">When this element is specified, you cannot specify the [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element.</span></span>

<span data-ttu-id="e30a9-121">Naast het weer geven van de eigenschaps waarde, kunt u ook een label opgeven voor de waarde of een opmaak teken reeks die kan worden gebruikt om de weer gave van de waarde te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="e30a9-121">In addition to displaying the property value, you can also specify a label for the value or a format string that can be used to change the display of the value.</span></span> <span data-ttu-id="e30a9-122">Zie [een lijst weergave maken](./creating-a-list-view.md)voor meer informatie over het opgeven van gegevens in een lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="e30a9-122">For more information about specifying data in a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="e30a9-123">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="e30a9-123">Example</span></span>

<span data-ttu-id="e30a9-124">In het volgende voor beeld ziet u hoe u het label en de eigenschap opgeeft waarvan de waarde wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="e30a9-124">The following example shows how to specify the label and property whose value is displayed.</span></span>

```xml
ListItem>
  <Label>NameOfProperty</Label>
  <PropertyName>.NetTypeProperty</PropertyName>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="e30a9-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="e30a9-125">See Also</span></span>

[<span data-ttu-id="e30a9-126">Script block-element voor lijst item voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="e30a9-126">ScriptBlock Element for ListItem for ListControl (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="e30a9-127">Een lijst weergave maken</span><span class="sxs-lookup"><span data-stu-id="e30a9-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="e30a9-128">Lijst item-element voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="e30a9-128">ListItem Element for ListControl(Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="e30a9-129">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="e30a9-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
