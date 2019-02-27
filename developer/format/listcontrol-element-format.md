---
title: ListControl Element (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 37beeb0b-7a81-4747-becb-e309e17278fb
caps.latest.revision: 12
ms.openlocfilehash: 7a117c25b0d117dc846ba8e060e31e838b5edd52
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847829"
---
# <a name="listcontrol-element-format"></a><span data-ttu-id="751c5-102">Het element ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="751c5-102">ListControl Element (Format)</span></span>

<span data-ttu-id="751c5-103">Hiermee definieert u een indeling voor de weergave heeft.</span><span class="sxs-lookup"><span data-stu-id="751c5-103">Defines a list format for the view.</span></span>

<span data-ttu-id="751c5-104">Configuratie Element (indeling) ViewDefinitions-Element (indeling) weergave-Element (indeling) ListControl Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="751c5-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="751c5-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="751c5-105">Syntax</span></span>

```xml
<ListControl>
  <ListEntries>...</ListEntries>
</ListControl>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="751c5-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="751c5-106">Attributes and Elements</span></span>

<span data-ttu-id="751c5-107">De volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van de `ListControl` element.</span><span class="sxs-lookup"><span data-stu-id="751c5-107">The following sections describe the attributes, child elements, and the parent element of the `ListControl` element.</span></span> <span data-ttu-id="751c5-108">Dit element moet slechts één onderliggend element bevatten.</span><span class="sxs-lookup"><span data-stu-id="751c5-108">This element must contain only a single child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="751c5-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="751c5-109">Attributes</span></span>

<span data-ttu-id="751c5-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="751c5-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="751c5-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="751c5-111">Child Elements</span></span>

|<span data-ttu-id="751c5-112">Element</span><span class="sxs-lookup"><span data-stu-id="751c5-112">Element</span></span>|<span data-ttu-id="751c5-113">Description</span><span class="sxs-lookup"><span data-stu-id="751c5-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="751c5-114">ListEntries Element (Format)</span><span class="sxs-lookup"><span data-stu-id="751c5-114">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)|<span data-ttu-id="751c5-115">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="751c5-115">Required element.</span></span><br /><br /> <span data-ttu-id="751c5-116">Bevat de definities van de lijstweergave.</span><span class="sxs-lookup"><span data-stu-id="751c5-116">Provides the definitions of the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="751c5-117">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="751c5-117">Parent Elements</span></span>

|<span data-ttu-id="751c5-118">Element</span><span class="sxs-lookup"><span data-stu-id="751c5-118">Element</span></span>|<span data-ttu-id="751c5-119">Description</span><span class="sxs-lookup"><span data-stu-id="751c5-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="751c5-120">Weergave-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="751c5-120">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="751c5-121">Hiermee definieert u een weergave die wordt gebruikt om de leden van een of meer objecten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="751c5-121">Defines a view that is used to display the members of one or more objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="751c5-122">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="751c5-122">Remarks</span></span>

<span data-ttu-id="751c5-123">Zie voor meer informatie over het maken van een lijstweergave [het maken van een lijstweergave](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="751c5-123">For more information about creating a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="751c5-124">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="751c5-124">Example</span></span>

<span data-ttu-id="751c5-125">In dit voorbeeld ziet u een lijst weergeven voor de [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span><span class="sxs-lookup"><span data-stu-id="751c5-125">This example shows a list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="751c5-126">Zie ook</span><span class="sxs-lookup"><span data-stu-id="751c5-126">See Also</span></span>

[<span data-ttu-id="751c5-127">Weergave-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="751c5-127">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="751c5-128">ListEntries Element (Format)</span><span class="sxs-lookup"><span data-stu-id="751c5-128">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)

[<span data-ttu-id="751c5-129">Het maken van een lijst weergeven</span><span class="sxs-lookup"><span data-stu-id="751c5-129">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="751c5-130">Schrijven van een Windows PowerShell opmaak en het bestand van het type</span><span class="sxs-lookup"><span data-stu-id="751c5-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
