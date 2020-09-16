---
title: Element List entries voor ListControl (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 0fe07e739c2d2fec153599ec6c0c0b3ecc14df18
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785707"
---
# <a name="listentries-element-for-listcontrol-format"></a><span data-ttu-id="96042-102">Het element ListEntries voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="96042-102">ListEntries Element for ListControl (Format)</span></span>

<span data-ttu-id="96042-103">Biedt de definities van de lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="96042-103">Provides the definitions of the list view.</span></span> <span data-ttu-id="96042-104">In de lijst weergave moeten een of meer definities worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="96042-104">The list view must specify one or more definitions.</span></span>

<span data-ttu-id="96042-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer gave (indeling) ListControl element (indeling) element (indeling)</span><span class="sxs-lookup"><span data-stu-id="96042-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="96042-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="96042-106">Syntax</span></span>

```xml
<ListEntries>
  <ListEntry>...</ListEntry>
</ListEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="96042-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="96042-107">Attributes and Elements</span></span>

<span data-ttu-id="96042-108">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `ListEntries` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="96042-108">The following sections describe the attributes, child elements, and the parent element of the `ListEntries` element.</span></span> <span data-ttu-id="96042-109">Er moet mini maal één onderliggend element worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="96042-109">At least one child element must be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="96042-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="96042-110">Attributes</span></span>

<span data-ttu-id="96042-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="96042-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="96042-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="96042-112">Child Elements</span></span>

|<span data-ttu-id="96042-113">Element</span><span class="sxs-lookup"><span data-stu-id="96042-113">Element</span></span>|<span data-ttu-id="96042-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="96042-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="96042-115">Element List entry (indeling)</span><span class="sxs-lookup"><span data-stu-id="96042-115">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="96042-116">Geeft een definitie van de lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="96042-116">Provides a definition of the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="96042-117">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="96042-117">Parent Elements</span></span>

|<span data-ttu-id="96042-118">Element</span><span class="sxs-lookup"><span data-stu-id="96042-118">Element</span></span>|<span data-ttu-id="96042-119">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="96042-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="96042-120">Het element ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="96042-120">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)|<span data-ttu-id="96042-121">Hiermee definieert u een lijst indeling voor de weer gave.</span><span class="sxs-lookup"><span data-stu-id="96042-121">Defines a list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="96042-122">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="96042-122">Remarks</span></span>

<span data-ttu-id="96042-123">Zie [lijst weergave](./creating-a-list-view.md)voor meer informatie over lijst weergaven.</span><span class="sxs-lookup"><span data-stu-id="96042-123">For more information about list views, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="96042-124">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="96042-124">Example</span></span>

<span data-ttu-id="96042-125">In dit voor beeld worden de XML-elementen weer gegeven die de lijst weergave definiëren voor het object [System. ServiceProcess. servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) .</span><span class="sxs-lookup"><span data-stu-id="96042-125">This example shows the XML elements that define the list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="96042-126">Zie ook</span><span class="sxs-lookup"><span data-stu-id="96042-126">See Also</span></span>

[<span data-ttu-id="96042-127">Het element ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="96042-127">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)

[<span data-ttu-id="96042-128">Element List entry (indeling)</span><span class="sxs-lookup"><span data-stu-id="96042-128">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="96042-129">Lijst weergave</span><span class="sxs-lookup"><span data-stu-id="96042-129">List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="96042-130">Een Windows Power shell-indeling en-type bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="96042-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
