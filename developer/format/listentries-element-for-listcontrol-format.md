---
title: ListEntries-Element voor ListControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b62e81cc-4175-40fa-829f-634245b09f86
caps.latest.revision: 12
ms.openlocfilehash: aaf16702e485135b5299ccb43a2b62db2d9f5762
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847360"
---
# <a name="listentries-element-for-listcontrol-format"></a><span data-ttu-id="5aa19-102">Het element ListEntries voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="5aa19-102">ListEntries Element for ListControl (Format)</span></span>

<span data-ttu-id="5aa19-103">Bevat de definities van de lijstweergave.</span><span class="sxs-lookup"><span data-stu-id="5aa19-103">Provides the definitions of the list view.</span></span> <span data-ttu-id="5aa19-104">De lijstweergave moet een of meer netwerkdefinities opgeven.</span><span class="sxs-lookup"><span data-stu-id="5aa19-104">The list view must specify one or more definitions.</span></span>

<span data-ttu-id="5aa19-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format)</span><span class="sxs-lookup"><span data-stu-id="5aa19-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5aa19-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="5aa19-106">Syntax</span></span>

```xml
<ListEntries>
  <ListEntry>...</ListEntry>
</ListEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5aa19-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="5aa19-107">Attributes and Elements</span></span>

<span data-ttu-id="5aa19-108">De volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van de `ListEntries` element.</span><span class="sxs-lookup"><span data-stu-id="5aa19-108">The following sections describe the attributes, child elements, and the parent element of the `ListEntries` element.</span></span> <span data-ttu-id="5aa19-109">Ten minste één onderliggend element moet worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="5aa19-109">At least one child element must be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="5aa19-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="5aa19-110">Attributes</span></span>

<span data-ttu-id="5aa19-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="5aa19-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5aa19-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="5aa19-112">Child Elements</span></span>

|<span data-ttu-id="5aa19-113">Element</span><span class="sxs-lookup"><span data-stu-id="5aa19-113">Element</span></span>|<span data-ttu-id="5aa19-114">Description</span><span class="sxs-lookup"><span data-stu-id="5aa19-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5aa19-115">ListEntry-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="5aa19-115">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="5aa19-116">Bevat een definitie van de lijstweergave.</span><span class="sxs-lookup"><span data-stu-id="5aa19-116">Provides a definition of the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="5aa19-117">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="5aa19-117">Parent Elements</span></span>

|<span data-ttu-id="5aa19-118">Element</span><span class="sxs-lookup"><span data-stu-id="5aa19-118">Element</span></span>|<span data-ttu-id="5aa19-119">Description</span><span class="sxs-lookup"><span data-stu-id="5aa19-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5aa19-120">ListControl Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="5aa19-120">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)|<span data-ttu-id="5aa19-121">Hiermee definieert u een indeling voor de weergave heeft.</span><span class="sxs-lookup"><span data-stu-id="5aa19-121">Defines a list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5aa19-122">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="5aa19-122">Remarks</span></span>

<span data-ttu-id="5aa19-123">Zie voor meer informatie over lijstweergaven [lijstweergave](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="5aa19-123">For more information about list views, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="5aa19-124">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="5aa19-124">Example</span></span>

<span data-ttu-id="5aa19-125">In dit voorbeeld ziet u de XML-elementen die definiëren in de lijstweergave voor de [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span><span class="sxs-lookup"><span data-stu-id="5aa19-125">This example shows the XML elements that define the list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="5aa19-126">Zie ook</span><span class="sxs-lookup"><span data-stu-id="5aa19-126">See Also</span></span>

[<span data-ttu-id="5aa19-127">ListControl Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="5aa19-127">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)

[<span data-ttu-id="5aa19-128">ListEntry-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="5aa19-128">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="5aa19-129">Lijstweergave</span><span class="sxs-lookup"><span data-stu-id="5aa19-129">List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="5aa19-130">Schrijven van een Windows PowerShell opmaak en het bestand van het type</span><span class="sxs-lookup"><span data-stu-id="5aa19-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
