---
title: TypeName-Element voor SelectionCondition voor EntrySelectedBy voor ListControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bd025a3a-3780-40db-a068-873e7df38015
caps.latest.revision: 9
ms.openlocfilehash: 2b76b040b39088cc9c3b9d6890c38df3c533b39f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083855"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="9de83-102">Het element TypeName voor SelectionCondition voor EntrySelectedBy voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="9de83-102">TypeName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="9de83-103">Hiermee geeft u een .NET-type dat de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="9de83-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="9de83-104">Wanneer dit type aanwezig is, wordt de vermelding in de lijst gebruikt.</span><span class="sxs-lookup"><span data-stu-id="9de83-104">When this type is present, the list entry is used.</span></span>

<span data-ttu-id="9de83-105">Configuratie Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) ListControl Element (indeling) ListEntries Element voor ListControl (indeling) ListEntry-Element voor ListEntries voor ListControl (indeling) EntrySelectedBy Element voor ListEntry voor ListControl (indeling) SelectionCondition Element voor EntrySelectedBy voor ListControl (indeling) TypeName Element voor SelectionCondition voor EntrySelectedBy voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="9de83-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) EntrySelectedBy Element for ListEntry for ListControl (Format) SelectionCondition Element for EntrySelectedBy for ListControl (Format) TypeName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9de83-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="9de83-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9de83-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="9de83-107">Attributes and Elements</span></span>

<span data-ttu-id="9de83-108">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `TypeName` element.</span><span class="sxs-lookup"><span data-stu-id="9de83-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9de83-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="9de83-109">Attributes</span></span>

<span data-ttu-id="9de83-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="9de83-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9de83-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="9de83-111">Child Elements</span></span>

<span data-ttu-id="9de83-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="9de83-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9de83-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="9de83-113">Parent Elements</span></span>

|<span data-ttu-id="9de83-114">Element</span><span class="sxs-lookup"><span data-stu-id="9de83-114">Element</span></span>|<span data-ttu-id="9de83-115">Description</span><span class="sxs-lookup"><span data-stu-id="9de83-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9de83-116">SelectionCondition-Element voor EntrySelectedBy voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="9de83-116">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="9de83-117">Hiermee definieert u de voorwaarde die moet bestaan voor deze vermelding lijst moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="9de83-117">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="9de83-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="9de83-118">Text Value</span></span>

<span data-ttu-id="9de83-119">Geef de volledig gekwalificeerde naam van het .NET-type, bijvoorbeeld `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="9de83-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="9de83-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="9de83-120">Remarks</span></span>

<span data-ttu-id="9de83-121">De selectievoorwaarde een willekeurig aantal .NET-typen kunt opgeven of de selectie wordt ingesteld, maar niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="9de83-121">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span> <span data-ttu-id="9de83-122">Zie voor meer informatie over het gebruik van de voorwaarden van de selectie [definiëren voorwaarden voor wanneer gegevens worden weergegeven](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="9de83-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="9de83-123">Zie voor meer informatie over andere onderdelen van een lijstweergave [het maken van een lijstweergave](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="9de83-123">For more information about other the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9de83-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="9de83-124">See Also</span></span>

[<span data-ttu-id="9de83-125">Het maken van een lijst weergeven</span><span class="sxs-lookup"><span data-stu-id="9de83-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="9de83-126">Voorwaarden voor wanneer gegevens worden weergegeven definiëren</span><span class="sxs-lookup"><span data-stu-id="9de83-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="9de83-127">SelectionCondition-Element voor EntrySelectedBy voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="9de83-127">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="9de83-128">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="9de83-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
