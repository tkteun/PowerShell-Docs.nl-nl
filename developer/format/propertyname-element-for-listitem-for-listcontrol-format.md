---
title: PropertyName-Element voor ListItem voor ListControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 01ae8cbe-acdc-4043-bd6e-1118a5691a55
caps.latest.revision: 12
ms.openlocfilehash: 405184f7bdbf1955f1df7766bf2723c244dcc27f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064900"
---
# <a name="propertyname-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="2d5fc-102">Het element PropertyName voor ListItem voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="2d5fc-102">PropertyName Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="2d5fc-103">Hiermee geeft u de .NET-eigenschap waarvan de waarde wordt weergegeven in de lijst.</span><span class="sxs-lookup"><span data-stu-id="2d5fc-103">Specifies the .NET property whose value is displayed in the list.</span></span>

<span data-ttu-id="2d5fc-104">Configuratie Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) ListControl Element (indeling) ListEntries-Element (indeling) ListEntry-Element (indeling) ListItems Element (indeling) ListItem-Element (indeling) PropertyName-Element voor ListItem (indeling)</span><span class="sxs-lookup"><span data-stu-id="2d5fc-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) ListItems Element (Format) ListItem Element (Format) PropertyName Element for ListItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2d5fc-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="2d5fc-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2d5fc-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="2d5fc-106">Attributes and Elements</span></span>

<span data-ttu-id="2d5fc-107">De volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van de `PropertyName` element.</span><span class="sxs-lookup"><span data-stu-id="2d5fc-107">The following sections describe the attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2d5fc-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="2d5fc-108">Attributes</span></span>

<span data-ttu-id="2d5fc-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="2d5fc-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2d5fc-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="2d5fc-110">Child Elements</span></span>

<span data-ttu-id="2d5fc-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="2d5fc-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2d5fc-112">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="2d5fc-112">Parent Elements</span></span>

|<span data-ttu-id="2d5fc-113">Element</span><span class="sxs-lookup"><span data-stu-id="2d5fc-113">Element</span></span>|<span data-ttu-id="2d5fc-114">Description</span><span class="sxs-lookup"><span data-stu-id="2d5fc-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2d5fc-115">ListItem Element (Format)</span><span class="sxs-lookup"><span data-stu-id="2d5fc-115">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="2d5fc-116">Hiermee definieert de eigenschap of het script waarvan de waarde wordt weergegeven in de rij van de lijstweergave.</span><span class="sxs-lookup"><span data-stu-id="2d5fc-116">Defines the property or script whose value is displayed in the row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="2d5fc-117">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="2d5fc-117">Text Value</span></span>

<span data-ttu-id="2d5fc-118">Geef de naam van de eigenschap waarvan de waarde wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="2d5fc-118">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="2d5fc-119">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="2d5fc-119">Remarks</span></span>

<span data-ttu-id="2d5fc-120">Wanneer dit element is opgegeven, wordt u niet opgeven de [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element.</span><span class="sxs-lookup"><span data-stu-id="2d5fc-120">When this element is specified, you cannot specify the [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element.</span></span>

<span data-ttu-id="2d5fc-121">Naast de waarde van de eigenschap weer te geven, kunt u ook een label voor de waarde of een opmaaktekenreeks die kan worden gebruikt voor het wijzigen van de weergave van de waarde opgeven.</span><span class="sxs-lookup"><span data-stu-id="2d5fc-121">In addition to displaying the property value, you can also specify a label for the value or a format string that can be used to change the display of the value.</span></span> <span data-ttu-id="2d5fc-122">Zie voor meer informatie over het opgeven van gegevens in een lijst weergeven [het maken van een lijstweergave](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="2d5fc-122">For more information about specifying data in a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="2d5fc-123">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="2d5fc-123">Example</span></span>

<span data-ttu-id="2d5fc-124">Het volgende voorbeeld ziet hoe u het label en de eigenschap waarvan de waarde wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="2d5fc-124">The following example shows how to specify the label and property whose value is displayed.</span></span>

```xml
ListItem>
  <Label>NameOfProperty</Label>
  <PropertyName>.NetTypeProperty</PropertyName>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="2d5fc-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="2d5fc-125">See Also</span></span>

[<span data-ttu-id="2d5fc-126">ScriptBlock-Element voor ListItem voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="2d5fc-126">ScriptBlock Element for ListItem for ListControl (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="2d5fc-127">Het maken van een lijst weergeven</span><span class="sxs-lookup"><span data-stu-id="2d5fc-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="2d5fc-128">Lijstitem-Element voor ListControl(Format)</span><span class="sxs-lookup"><span data-stu-id="2d5fc-128">ListItem Element for ListControl(Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="2d5fc-129">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="2d5fc-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
