---
ms.date: 09/13/2016
ms.topic: reference
title: Het element ListControl (opmaak)
description: Het element ListControl (opmaak)
ms.openlocfilehash: cd5687ac8e94e2245d1ae2de8b2206185e5b8ca4
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666583"
---
# <a name="listcontrol-element-format"></a><span data-ttu-id="577e6-103">Het element ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="577e6-103">ListControl Element (Format)</span></span>

<span data-ttu-id="577e6-104">Hiermee definieert u een lijst indeling voor de weer gave.</span><span class="sxs-lookup"><span data-stu-id="577e6-104">Defines a list format for the view.</span></span>

<span data-ttu-id="577e6-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) ListControl-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="577e6-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="577e6-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="577e6-106">Syntax</span></span>

```xml
<ListControl>
  <ListEntries>...</ListEntries>
</ListControl>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="577e6-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="577e6-107">Attributes and Elements</span></span>

<span data-ttu-id="577e6-108">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `ListControl` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="577e6-108">The following sections describe the attributes, child elements, and the parent element of the `ListControl` element.</span></span> <span data-ttu-id="577e6-109">Dit element mag slechts één onderliggend element bevatten.</span><span class="sxs-lookup"><span data-stu-id="577e6-109">This element must contain only a single child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="577e6-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="577e6-110">Attributes</span></span>

<span data-ttu-id="577e6-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="577e6-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="577e6-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="577e6-112">Child Elements</span></span>

|<span data-ttu-id="577e6-113">Element</span><span class="sxs-lookup"><span data-stu-id="577e6-113">Element</span></span>|<span data-ttu-id="577e6-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="577e6-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="577e6-115">Element List Entries (indeling)</span><span class="sxs-lookup"><span data-stu-id="577e6-115">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)|<span data-ttu-id="577e6-116">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="577e6-116">Required element.</span></span><br /><br /> <span data-ttu-id="577e6-117">Biedt de definities van de lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="577e6-117">Provides the definitions of the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="577e6-118">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="577e6-118">Parent Elements</span></span>

|<span data-ttu-id="577e6-119">Element</span><span class="sxs-lookup"><span data-stu-id="577e6-119">Element</span></span>|<span data-ttu-id="577e6-120">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="577e6-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="577e6-121">Het element Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="577e6-121">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="577e6-122">Hiermee wordt een weer gave gedefinieerd die wordt gebruikt om de leden van een of meer objecten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="577e6-122">Defines a view that is used to display the members of one or more objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="577e6-123">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="577e6-123">Remarks</span></span>

<span data-ttu-id="577e6-124">Zie [een lijst weergave maken](./creating-a-list-view.md)voor meer informatie over het maken van een lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="577e6-124">For more information about creating a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="577e6-125">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="577e6-125">Example</span></span>

<span data-ttu-id="577e6-126">In dit voor beeld ziet u een lijst weergave voor het object [System. ServiceProcess. servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) .</span><span class="sxs-lookup"><span data-stu-id="577e6-126">This example shows a list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

```
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>...</ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="577e6-127">Zie ook</span><span class="sxs-lookup"><span data-stu-id="577e6-127">See Also</span></span>

[<span data-ttu-id="577e6-128">Het element Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="577e6-128">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="577e6-129">Element List Entries (indeling)</span><span class="sxs-lookup"><span data-stu-id="577e6-129">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)

[<span data-ttu-id="577e6-130">Een lijstweergave maken</span><span class="sxs-lookup"><span data-stu-id="577e6-130">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="577e6-131">Een Windows Power shell-indeling en-type bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="577e6-131">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
