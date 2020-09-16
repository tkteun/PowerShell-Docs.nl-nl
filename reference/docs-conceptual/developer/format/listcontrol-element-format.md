---
title: ListControl-element (Format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 0173b9797bffcca74f1a32903686f771366ebb1b
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785724"
---
# <a name="listcontrol-element-format"></a><span data-ttu-id="d7bf3-102">Het element ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="d7bf3-102">ListControl Element (Format)</span></span>

<span data-ttu-id="d7bf3-103">Hiermee definieert u een lijst indeling voor de weer gave.</span><span class="sxs-lookup"><span data-stu-id="d7bf3-103">Defines a list format for the view.</span></span>

<span data-ttu-id="d7bf3-104">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) ListControl-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="d7bf3-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d7bf3-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="d7bf3-105">Syntax</span></span>

```xml
<ListControl>
  <ListEntries>...</ListEntries>
</ListControl>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="d7bf3-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="d7bf3-106">Attributes and Elements</span></span>

<span data-ttu-id="d7bf3-107">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `ListControl` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="d7bf3-107">The following sections describe the attributes, child elements, and the parent element of the `ListControl` element.</span></span> <span data-ttu-id="d7bf3-108">Dit element mag slechts één onderliggend element bevatten.</span><span class="sxs-lookup"><span data-stu-id="d7bf3-108">This element must contain only a single child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d7bf3-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="d7bf3-109">Attributes</span></span>

<span data-ttu-id="d7bf3-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="d7bf3-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d7bf3-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="d7bf3-111">Child Elements</span></span>

|<span data-ttu-id="d7bf3-112">Element</span><span class="sxs-lookup"><span data-stu-id="d7bf3-112">Element</span></span>|<span data-ttu-id="d7bf3-113">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="d7bf3-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d7bf3-114">Element List Entries (indeling)</span><span class="sxs-lookup"><span data-stu-id="d7bf3-114">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)|<span data-ttu-id="d7bf3-115">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="d7bf3-115">Required element.</span></span><br /><br /> <span data-ttu-id="d7bf3-116">Biedt de definities van de lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="d7bf3-116">Provides the definitions of the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d7bf3-117">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="d7bf3-117">Parent Elements</span></span>

|<span data-ttu-id="d7bf3-118">Element</span><span class="sxs-lookup"><span data-stu-id="d7bf3-118">Element</span></span>|<span data-ttu-id="d7bf3-119">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="d7bf3-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d7bf3-120">Het element Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="d7bf3-120">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="d7bf3-121">Hiermee wordt een weer gave gedefinieerd die wordt gebruikt om de leden van een of meer objecten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="d7bf3-121">Defines a view that is used to display the members of one or more objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d7bf3-122">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="d7bf3-122">Remarks</span></span>

<span data-ttu-id="d7bf3-123">Zie [een lijst weergave maken](./creating-a-list-view.md)voor meer informatie over het maken van een lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="d7bf3-123">For more information about creating a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="d7bf3-124">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="d7bf3-124">Example</span></span>

<span data-ttu-id="d7bf3-125">In dit voor beeld ziet u een lijst weergave voor het object [System. ServiceProcess. servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) .</span><span class="sxs-lookup"><span data-stu-id="d7bf3-125">This example shows a list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d7bf3-126">Zie ook</span><span class="sxs-lookup"><span data-stu-id="d7bf3-126">See Also</span></span>

[<span data-ttu-id="d7bf3-127">Het element Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="d7bf3-127">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="d7bf3-128">Element List Entries (indeling)</span><span class="sxs-lookup"><span data-stu-id="d7bf3-128">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)

[<span data-ttu-id="d7bf3-129">Een lijstweergave maken</span><span class="sxs-lookup"><span data-stu-id="d7bf3-129">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="d7bf3-130">Een Windows Power shell-indeling en-type bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="d7bf3-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
