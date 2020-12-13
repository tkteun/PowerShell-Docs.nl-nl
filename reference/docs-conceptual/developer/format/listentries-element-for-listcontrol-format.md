---
ms.date: 09/13/2016
ms.topic: reference
title: Het element ListEntries voor ListControl (opmaak)
description: Het element ListEntries voor ListControl (opmaak)
ms.openlocfilehash: d4d6625bb92ea27863fc30d5bf5625f9275e4f69
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666600"
---
# <a name="listentries-element-for-listcontrol-format"></a><span data-ttu-id="a309c-103">Het element ListEntries voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="a309c-103">ListEntries Element for ListControl (Format)</span></span>

<span data-ttu-id="a309c-104">Biedt de definities van de lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="a309c-104">Provides the definitions of the list view.</span></span> <span data-ttu-id="a309c-105">In de lijst weergave moeten een of meer definities worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="a309c-105">The list view must specify one or more definitions.</span></span>

<span data-ttu-id="a309c-106">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer gave (indeling) ListControl element (indeling) element (indeling)</span><span class="sxs-lookup"><span data-stu-id="a309c-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a309c-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="a309c-107">Syntax</span></span>

```xml
<ListEntries>
  <ListEntry>...</ListEntry>
</ListEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a309c-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="a309c-108">Attributes and Elements</span></span>

<span data-ttu-id="a309c-109">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `ListEntries` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="a309c-109">The following sections describe the attributes, child elements, and the parent element of the `ListEntries` element.</span></span> <span data-ttu-id="a309c-110">Er moet mini maal één onderliggend element worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="a309c-110">At least one child element must be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="a309c-111">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="a309c-111">Attributes</span></span>

<span data-ttu-id="a309c-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="a309c-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a309c-113">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="a309c-113">Child Elements</span></span>

|<span data-ttu-id="a309c-114">Element</span><span class="sxs-lookup"><span data-stu-id="a309c-114">Element</span></span>|<span data-ttu-id="a309c-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="a309c-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a309c-116">Element List entry (indeling)</span><span class="sxs-lookup"><span data-stu-id="a309c-116">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="a309c-117">Geeft een definitie van de lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="a309c-117">Provides a definition of the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a309c-118">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="a309c-118">Parent Elements</span></span>

|<span data-ttu-id="a309c-119">Element</span><span class="sxs-lookup"><span data-stu-id="a309c-119">Element</span></span>|<span data-ttu-id="a309c-120">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="a309c-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a309c-121">Het element ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="a309c-121">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)|<span data-ttu-id="a309c-122">Hiermee definieert u een lijst indeling voor de weer gave.</span><span class="sxs-lookup"><span data-stu-id="a309c-122">Defines a list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a309c-123">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="a309c-123">Remarks</span></span>

<span data-ttu-id="a309c-124">Zie [lijst weergave](./creating-a-list-view.md)voor meer informatie over lijst weergaven.</span><span class="sxs-lookup"><span data-stu-id="a309c-124">For more information about list views, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="a309c-125">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="a309c-125">Example</span></span>

<span data-ttu-id="a309c-126">In dit voor beeld worden de XML-elementen weer gegeven die de lijst weergave definiëren voor het object [System. ServiceProcess. servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) .</span><span class="sxs-lookup"><span data-stu-id="a309c-126">This example shows the XML elements that define the list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>...</ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="a309c-127">Zie ook</span><span class="sxs-lookup"><span data-stu-id="a309c-127">See Also</span></span>

[<span data-ttu-id="a309c-128">Het element ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="a309c-128">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)

[<span data-ttu-id="a309c-129">Element List entry (indeling)</span><span class="sxs-lookup"><span data-stu-id="a309c-129">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="a309c-130">Lijst weergave</span><span class="sxs-lookup"><span data-stu-id="a309c-130">List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="a309c-131">Een Windows Power shell-indeling en-type bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="a309c-131">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
