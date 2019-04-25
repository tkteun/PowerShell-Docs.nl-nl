---
title: ListEntry-Element voor ListControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6d16bca8-d025-432d-aa84-8b607b8af3ae
caps.latest.revision: 12
ms.openlocfilehash: 1a3bafd4ca94aee70e869c699f7a4ef8befc5511
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065220"
---
# <a name="listentry-element-for-listcontrol-format"></a><span data-ttu-id="62f98-102">Het element ListEntry voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="62f98-102">ListEntry Element for ListControl (Format)</span></span>

<span data-ttu-id="62f98-103">Bevat een definitie van de lijstweergave.</span><span class="sxs-lookup"><span data-stu-id="62f98-103">Provides a definition of the list view.</span></span>

<span data-ttu-id="62f98-104">Configuratie Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) ListControl Element (indeling) ListEntries-Element (indeling) ListEntry-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="62f98-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="62f98-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="62f98-105">Syntax</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="62f98-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="62f98-106">Attributes and Elements</span></span>

<span data-ttu-id="62f98-107">De volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van de `ListEntry` element.</span><span class="sxs-lookup"><span data-stu-id="62f98-107">The following sections describe the attributes, child elements, and the parent element of the `ListEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="62f98-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="62f98-108">Attributes</span></span>

<span data-ttu-id="62f98-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="62f98-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="62f98-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="62f98-110">Child Elements</span></span>

|<span data-ttu-id="62f98-111">Element</span><span class="sxs-lookup"><span data-stu-id="62f98-111">Element</span></span>|<span data-ttu-id="62f98-112">Description</span><span class="sxs-lookup"><span data-stu-id="62f98-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="62f98-113">EntrySelectedBy-Element voor ListEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="62f98-113">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="62f98-114">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="62f98-114">Optional element.</span></span><br /><br /> <span data-ttu-id="62f98-115">Hiermee definieert u de .NET-objecten die gebruikmaken van de definitie van deze lijst weergeven of de voorwaarde die moet bestaan voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="62f98-115">Defines the .NET objects that use this list view definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="62f98-116">ListItems Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="62f98-116">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="62f98-117">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="62f98-117">Required element.</span></span><br /><br /> <span data-ttu-id="62f98-118">Definieert de eigenschappen en -scripts waarvan de waarden worden weergegeven door de lijstweergave.</span><span class="sxs-lookup"><span data-stu-id="62f98-118">Defines the properties and scripts whose values are displayed by the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="62f98-119">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="62f98-119">Parent Elements</span></span>

|<span data-ttu-id="62f98-120">Element</span><span class="sxs-lookup"><span data-stu-id="62f98-120">Element</span></span>|<span data-ttu-id="62f98-121">Description</span><span class="sxs-lookup"><span data-stu-id="62f98-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="62f98-122">ListEntries Element (Format)</span><span class="sxs-lookup"><span data-stu-id="62f98-122">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)|<span data-ttu-id="62f98-123">Bevat de definities van de lijstweergave.</span><span class="sxs-lookup"><span data-stu-id="62f98-123">Provides the definitions of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="62f98-124">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="62f98-124">Remarks</span></span>

<span data-ttu-id="62f98-125">Een lijst weergeven is een lijstindeling eigenschapswaarden of script waarden voor elk object wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="62f98-125">A list view is a list format that displays property values or script values for each object.</span></span> <span data-ttu-id="62f98-126">Zie voor meer informatie over lijstweergaven [het maken van een lijstweergave](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="62f98-126">For more information about list views, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="62f98-127">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="62f98-127">Example</span></span>

<span data-ttu-id="62f98-128">In dit voorbeeld ziet u de XML-elementen die definiëren in de lijstweergave voor de [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span><span class="sxs-lookup"><span data-stu-id="62f98-128">This example shows the XML elements that define the list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="62f98-129">Zie ook</span><span class="sxs-lookup"><span data-stu-id="62f98-129">See Also</span></span>

[<span data-ttu-id="62f98-130">Het maken van een lijst weergeven</span><span class="sxs-lookup"><span data-stu-id="62f98-130">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="62f98-131">EntrySelectedBy-Element voor ListEntry (indeling)</span><span class="sxs-lookup"><span data-stu-id="62f98-131">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="62f98-132">ListEntries Element (Format)</span><span class="sxs-lookup"><span data-stu-id="62f98-132">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)

[<span data-ttu-id="62f98-133">ListItems Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="62f98-133">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="62f98-134">Schrijven van een Windows PowerShell opmaak en het bestand van het type</span><span class="sxs-lookup"><span data-stu-id="62f98-134">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
