---
title: List Entry-element voor ListControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6d16bca8-d025-432d-aa84-8b607b8af3ae
caps.latest.revision: 12
ms.openlocfilehash: 1a3bafd4ca94aee70e869c699f7a4ef8befc5511
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72354346"
---
# <a name="listentry-element-for-listcontrol-format"></a><span data-ttu-id="fb52f-102">Het element ListEntry voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="fb52f-102">ListEntry Element for ListControl (Format)</span></span>

<span data-ttu-id="fb52f-103">Geeft een definitie van de lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="fb52f-103">Provides a definition of the list view.</span></span>

<span data-ttu-id="fb52f-104">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) bestand van ListControl-element (indeling) element (indeling) List item (Format)</span><span class="sxs-lookup"><span data-stu-id="fb52f-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fb52f-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="fb52f-105">Syntax</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fb52f-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="fb52f-106">Attributes and Elements</span></span>

<span data-ttu-id="fb52f-107">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het element `ListEntry` beschreven.</span><span class="sxs-lookup"><span data-stu-id="fb52f-107">The following sections describe the attributes, child elements, and the parent element of the `ListEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="fb52f-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="fb52f-108">Attributes</span></span>

<span data-ttu-id="fb52f-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="fb52f-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fb52f-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="fb52f-110">Child Elements</span></span>

|<span data-ttu-id="fb52f-111">Element</span><span class="sxs-lookup"><span data-stu-id="fb52f-111">Element</span></span>|<span data-ttu-id="fb52f-112">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="fb52f-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fb52f-113">Element EntrySelectedBy voor List entry (indeling)</span><span class="sxs-lookup"><span data-stu-id="fb52f-113">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="fb52f-114">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="fb52f-114">Optional element.</span></span><br /><br /> <span data-ttu-id="fb52f-115">Hiermee definieert u de .NET-objecten die gebruikmaken van deze lijst weergave definitie of de voor waarde die voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="fb52f-115">Defines the .NET objects that use this list view definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="fb52f-116">List items-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="fb52f-116">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="fb52f-117">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="fb52f-117">Required element.</span></span><br /><br /> <span data-ttu-id="fb52f-118">Hiermee worden de eigenschappen en scripts gedefinieerd waarvan de waarden worden weer gegeven in de lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="fb52f-118">Defines the properties and scripts whose values are displayed by the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="fb52f-119">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="fb52f-119">Parent Elements</span></span>

|<span data-ttu-id="fb52f-120">Element</span><span class="sxs-lookup"><span data-stu-id="fb52f-120">Element</span></span>|<span data-ttu-id="fb52f-121">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="fb52f-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fb52f-122">Element List Entries (indeling)</span><span class="sxs-lookup"><span data-stu-id="fb52f-122">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)|<span data-ttu-id="fb52f-123">Biedt de definities van de lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="fb52f-123">Provides the definitions of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="fb52f-124">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="fb52f-124">Remarks</span></span>

<span data-ttu-id="fb52f-125">Een lijst weergave is een lijst indeling waarin eigenschapwaarden of script waarden voor elk object worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="fb52f-125">A list view is a list format that displays property values or script values for each object.</span></span> <span data-ttu-id="fb52f-126">Zie [een lijst weergave maken](./creating-a-list-view.md)voor meer informatie over lijst weergaven.</span><span class="sxs-lookup"><span data-stu-id="fb52f-126">For more information about list views, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="fb52f-127">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="fb52f-127">Example</span></span>

<span data-ttu-id="fb52f-128">In dit voor beeld worden de XML-elementen weer gegeven die de lijst weergave definiëren voor het object [System. ServiceProcess. servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) .</span><span class="sxs-lookup"><span data-stu-id="fb52f-128">This example shows the XML elements that define the list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="fb52f-129">Zie ook</span><span class="sxs-lookup"><span data-stu-id="fb52f-129">See Also</span></span>

[<span data-ttu-id="fb52f-130">Een lijst weergave maken</span><span class="sxs-lookup"><span data-stu-id="fb52f-130">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="fb52f-131">Element EntrySelectedBy voor List entry (indeling)</span><span class="sxs-lookup"><span data-stu-id="fb52f-131">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="fb52f-132">Element List Entries (indeling)</span><span class="sxs-lookup"><span data-stu-id="fb52f-132">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)

[<span data-ttu-id="fb52f-133">List items-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="fb52f-133">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="fb52f-134">Een Windows Power shell-indeling en-type bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="fb52f-134">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
