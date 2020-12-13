---
ms.date: 09/13/2016
ms.topic: reference
title: Het element ListEntry voor ListControl (opmaak)
description: Het element ListEntry voor ListControl (opmaak)
ms.openlocfilehash: 96ae5fcdd837d2491d6c7ff6a375fef1d83ae3e9
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666566"
---
# <a name="listentry-element-for-listcontrol-format"></a><span data-ttu-id="f888f-103">Het element ListEntry voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="f888f-103">ListEntry Element for ListControl (Format)</span></span>

<span data-ttu-id="f888f-104">Geeft een definitie van de lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="f888f-104">Provides a definition of the list view.</span></span>

<span data-ttu-id="f888f-105">Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) bestand van ListControl-element (indeling) element (indeling) List item (Format)</span><span class="sxs-lookup"><span data-stu-id="f888f-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f888f-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="f888f-106">Syntax</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f888f-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="f888f-107">Attributes and Elements</span></span>

<span data-ttu-id="f888f-108">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `ListEntry` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="f888f-108">The following sections describe the attributes, child elements, and the parent element of the `ListEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f888f-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="f888f-109">Attributes</span></span>

<span data-ttu-id="f888f-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="f888f-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f888f-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="f888f-111">Child Elements</span></span>

|<span data-ttu-id="f888f-112">Element</span><span class="sxs-lookup"><span data-stu-id="f888f-112">Element</span></span>|<span data-ttu-id="f888f-113">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="f888f-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f888f-114">Element EntrySelectedBy voor List entry (indeling)</span><span class="sxs-lookup"><span data-stu-id="f888f-114">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="f888f-115">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="f888f-115">Optional element.</span></span><br /><br /> <span data-ttu-id="f888f-116">Hiermee definieert u de .NET-objecten die gebruikmaken van deze lijst weergave definitie of de voor waarde die voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="f888f-116">Defines the .NET objects that use this list view definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="f888f-117">List items-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="f888f-117">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="f888f-118">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="f888f-118">Required element.</span></span><br /><br /> <span data-ttu-id="f888f-119">Hiermee worden de eigenschappen en scripts gedefinieerd waarvan de waarden worden weer gegeven in de lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="f888f-119">Defines the properties and scripts whose values are displayed by the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f888f-120">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="f888f-120">Parent Elements</span></span>

|<span data-ttu-id="f888f-121">Element</span><span class="sxs-lookup"><span data-stu-id="f888f-121">Element</span></span>|<span data-ttu-id="f888f-122">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="f888f-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f888f-123">Element List Entries (indeling)</span><span class="sxs-lookup"><span data-stu-id="f888f-123">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)|<span data-ttu-id="f888f-124">Biedt de definities van de lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="f888f-124">Provides the definitions of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f888f-125">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="f888f-125">Remarks</span></span>

<span data-ttu-id="f888f-126">Een lijst weergave is een lijst indeling waarin eigenschapwaarden of script waarden voor elk object worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="f888f-126">A list view is a list format that displays property values or script values for each object.</span></span> <span data-ttu-id="f888f-127">Zie [een lijst weergave maken](./creating-a-list-view.md)voor meer informatie over lijst weergaven.</span><span class="sxs-lookup"><span data-stu-id="f888f-127">For more information about list views, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="f888f-128">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="f888f-128">Example</span></span>

<span data-ttu-id="f888f-129">In dit voor beeld worden de XML-elementen weer gegeven die de lijst weergave definiëren voor het object [System. ServiceProcess. servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) .</span><span class="sxs-lookup"><span data-stu-id="f888f-129">This example shows the XML elements that define the list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="f888f-130">Zie ook</span><span class="sxs-lookup"><span data-stu-id="f888f-130">See Also</span></span>

[<span data-ttu-id="f888f-131">Een lijstweergave maken</span><span class="sxs-lookup"><span data-stu-id="f888f-131">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="f888f-132">Element EntrySelectedBy voor List entry (indeling)</span><span class="sxs-lookup"><span data-stu-id="f888f-132">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="f888f-133">Element List Entries (indeling)</span><span class="sxs-lookup"><span data-stu-id="f888f-133">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)

[<span data-ttu-id="f888f-134">List items-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="f888f-134">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="f888f-135">Een Windows Power shell-indeling en-type bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="f888f-135">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
