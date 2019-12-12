---
title: Element List entries voor ListControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b62e81cc-4175-40fa-829f-634245b09f86
caps.latest.revision: 12
ms.openlocfilehash: aaf16702e485135b5299ccb43a2b62db2d9f5762
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72354353"
---
# <a name="listentries-element-for-listcontrol-format"></a><span data-ttu-id="955ce-102">Het element ListEntries voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="955ce-102">ListEntries Element for ListControl (Format)</span></span>

<span data-ttu-id="955ce-103">Biedt de definities van de lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="955ce-103">Provides the definitions of the list view.</span></span> <span data-ttu-id="955ce-104">In de lijst weergave moeten een of meer definities worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="955ce-104">The list view must specify one or more definitions.</span></span>

<span data-ttu-id="955ce-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer gave (indeling) ListControl element (indeling) element (indeling)</span><span class="sxs-lookup"><span data-stu-id="955ce-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="955ce-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="955ce-106">Syntax</span></span>

```xml
<ListEntries>
  <ListEntry>...</ListEntry>
</ListEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="955ce-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="955ce-107">Attributes and Elements</span></span>

<span data-ttu-id="955ce-108">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het element `ListEntries` beschreven.</span><span class="sxs-lookup"><span data-stu-id="955ce-108">The following sections describe the attributes, child elements, and the parent element of the `ListEntries` element.</span></span> <span data-ttu-id="955ce-109">Er moet mini maal één onderliggend element worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="955ce-109">At least one child element must be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="955ce-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="955ce-110">Attributes</span></span>

<span data-ttu-id="955ce-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="955ce-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="955ce-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="955ce-112">Child Elements</span></span>

|<span data-ttu-id="955ce-113">Element</span><span class="sxs-lookup"><span data-stu-id="955ce-113">Element</span></span>|<span data-ttu-id="955ce-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="955ce-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="955ce-115">Element List entry (indeling)</span><span class="sxs-lookup"><span data-stu-id="955ce-115">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="955ce-116">Geeft een definitie van de lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="955ce-116">Provides a definition of the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="955ce-117">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="955ce-117">Parent Elements</span></span>

|<span data-ttu-id="955ce-118">Element</span><span class="sxs-lookup"><span data-stu-id="955ce-118">Element</span></span>|<span data-ttu-id="955ce-119">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="955ce-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="955ce-120">ListControl-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="955ce-120">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)|<span data-ttu-id="955ce-121">Hiermee definieert u een lijst indeling voor de weer gave.</span><span class="sxs-lookup"><span data-stu-id="955ce-121">Defines a list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="955ce-122">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="955ce-122">Remarks</span></span>

<span data-ttu-id="955ce-123">Zie [lijst weergave](./creating-a-list-view.md)voor meer informatie over lijst weergaven.</span><span class="sxs-lookup"><span data-stu-id="955ce-123">For more information about list views, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="955ce-124">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="955ce-124">Example</span></span>

<span data-ttu-id="955ce-125">In dit voor beeld worden de XML-elementen weer gegeven die de lijst weergave definiëren voor het object [System. ServiceProcess. servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) .</span><span class="sxs-lookup"><span data-stu-id="955ce-125">This example shows the XML elements that define the list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="955ce-126">Zie ook</span><span class="sxs-lookup"><span data-stu-id="955ce-126">See Also</span></span>

[<span data-ttu-id="955ce-127">ListControl-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="955ce-127">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)

[<span data-ttu-id="955ce-128">Element List entry (indeling)</span><span class="sxs-lookup"><span data-stu-id="955ce-128">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="955ce-129">Lijst weergave</span><span class="sxs-lookup"><span data-stu-id="955ce-129">List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="955ce-130">Een Windows Power shell-indeling en-type bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="955ce-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
