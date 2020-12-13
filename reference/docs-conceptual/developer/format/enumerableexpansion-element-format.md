---
ms.date: 09/13/2016
ms.topic: reference
title: Het element EnumerableExpansion (opmaak)
description: Het element EnumerableExpansion (opmaak)
ms.openlocfilehash: 207ad99d5335e99701660159ab77279b55b0b6b5
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92668011"
---
# <a name="enumerableexpansion-element-format"></a><span data-ttu-id="dfa1d-103">Het element EnumerableExpansion (opmaak)</span><span class="sxs-lookup"><span data-stu-id="dfa1d-103">EnumerableExpansion Element (Format)</span></span>

<span data-ttu-id="dfa1d-104">Hiermee definieert u hoe specifieke .NET-verzamelings objecten worden uitgevouwen wanneer ze in een weer gave worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="dfa1d-104">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>

<span data-ttu-id="dfa1d-105">Configuratie-element (indeling) DefaultSettings element (indeling) EnumerableExpansions element (indeling) EnumerableExpansion element (indeling)</span><span class="sxs-lookup"><span data-stu-id="dfa1d-105">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="dfa1d-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="dfa1d-106">Syntax</span></span>

```xml
<EnumerableExpansion>
  <EntrySelectedBy>...</EntrySelectedBy>
  <Expand>EnumOnly, CoreOnly, Both</Expand>
</EnumerableExpansion>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="dfa1d-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="dfa1d-107">Attributes and Elements</span></span>

<span data-ttu-id="dfa1d-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `EnumerableExpansion` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="dfa1d-108">The following sections describe attributes, child elements, and the parent element of the `EnumerableExpansion` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="dfa1d-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="dfa1d-109">Attributes</span></span>

<span data-ttu-id="dfa1d-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="dfa1d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="dfa1d-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="dfa1d-111">Child Elements</span></span>

|<span data-ttu-id="dfa1d-112">Element</span><span class="sxs-lookup"><span data-stu-id="dfa1d-112">Element</span></span>|<span data-ttu-id="dfa1d-113">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="dfa1d-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dfa1d-114">Het element EntrySelectedBy voor EnumerableExpansion (opmaak)</span><span class="sxs-lookup"><span data-stu-id="dfa1d-114">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="dfa1d-115">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="dfa1d-115">Optional element.</span></span><br /><br /> <span data-ttu-id="dfa1d-116">Hiermee definieert u welke .NET-verzamelings objecten worden uitgevouwen door deze definitie.</span><span class="sxs-lookup"><span data-stu-id="dfa1d-116">Defines which .NET collection objects are expanded by this definition.</span></span>|
|[<span data-ttu-id="dfa1d-117">Het element Uitvouwen (opmaak)</span><span class="sxs-lookup"><span data-stu-id="dfa1d-117">Expand Element (Format)</span></span>](./expand-element-format.md)|<span data-ttu-id="dfa1d-118">Hiermee geeft u op hoe het verzamelings object voor deze definitie moet worden uitgebreid.</span><span class="sxs-lookup"><span data-stu-id="dfa1d-118">Specifies how the collection object is expanded for this definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="dfa1d-119">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="dfa1d-119">Parent Elements</span></span>

|<span data-ttu-id="dfa1d-120">Element</span><span class="sxs-lookup"><span data-stu-id="dfa1d-120">Element</span></span>|<span data-ttu-id="dfa1d-121">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="dfa1d-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dfa1d-122">Het element EnumerableExpansions (opmaak)</span><span class="sxs-lookup"><span data-stu-id="dfa1d-122">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)|<span data-ttu-id="dfa1d-123">Definieert de verschillende manieren waarop .NET-verzamelings objecten worden uitgevouwen wanneer ze in een weer gave worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="dfa1d-123">Defines the different ways that .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="dfa1d-124">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="dfa1d-124">Remarks</span></span>

<span data-ttu-id="dfa1d-125">Dit element wordt gebruikt om te definiëren hoe verzamelings objecten en de objecten in de verzameling worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="dfa1d-125">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="dfa1d-126">In dit geval verwijst een verzamelings object naar een object dat de interface  **System. Collections. ICollection** ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="dfa1d-126">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

<span data-ttu-id="dfa1d-127">Het standaard gedrag is om alleen de eigenschappen van de objecten in de verzameling weer te geven.</span><span class="sxs-lookup"><span data-stu-id="dfa1d-127">The default behavior is to display only the properties of the objects in the collection.</span></span>

## <a name="see-also"></a><span data-ttu-id="dfa1d-128">Zie ook</span><span class="sxs-lookup"><span data-stu-id="dfa1d-128">See Also</span></span>

[<span data-ttu-id="dfa1d-129">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="dfa1d-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
