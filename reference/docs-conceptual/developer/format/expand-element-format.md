---
ms.date: 09/13/2016
ms.topic: reference
title: Het element Uitvouwen (opmaak)
description: Het element Uitvouwen (opmaak)
ms.openlocfilehash: 518e132e3e74b921d4e51966fc60088a22ef63f1
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92667943"
---
# <a name="expand-element-format"></a><span data-ttu-id="ef9db-103">Het element Uitvouwen (opmaak)</span><span class="sxs-lookup"><span data-stu-id="ef9db-103">Expand Element (Format)</span></span>

<span data-ttu-id="ef9db-104">Hiermee geeft u op hoe het verzamelings object voor deze definitie moet worden uitgebreid.</span><span class="sxs-lookup"><span data-stu-id="ef9db-104">Specifies how the collection object is expanded for this definition.</span></span>

<span data-ttu-id="ef9db-105">Configuratie-element (indeling) DefaultSettings element (indeling) EnumerableExpansions element (indeling) EnumerableExpansion element (indeling) element uitbreiden (indeling)</span><span class="sxs-lookup"><span data-stu-id="ef9db-105">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) Expand Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ef9db-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="ef9db-106">Syntax</span></span>

```xml
<Expand>EnumOnly, CoreOnly, Both</Expand>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ef9db-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="ef9db-107">Attributes and Elements</span></span>

<span data-ttu-id="ef9db-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `Expand` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="ef9db-108">The following sections describe attributes, child elements, and the parent element of the `Expand` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ef9db-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="ef9db-109">Attributes</span></span>

<span data-ttu-id="ef9db-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="ef9db-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ef9db-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="ef9db-111">Child Elements</span></span>

<span data-ttu-id="ef9db-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="ef9db-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ef9db-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="ef9db-113">Parent Elements</span></span>

|<span data-ttu-id="ef9db-114">Element</span><span class="sxs-lookup"><span data-stu-id="ef9db-114">Element</span></span>|<span data-ttu-id="ef9db-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="ef9db-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ef9db-116">Het element EnumerableExpansion (opmaak)</span><span class="sxs-lookup"><span data-stu-id="ef9db-116">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="ef9db-117">Hiermee definieert u hoe specifieke .NET-verzamelings objecten worden uitgevouwen wanneer ze in een weer gave worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="ef9db-117">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ef9db-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="ef9db-118">Text Value</span></span>

<span data-ttu-id="ef9db-119">Geef een van de volgende waarden op:</span><span class="sxs-lookup"><span data-stu-id="ef9db-119">Specify one of the following values:</span></span>

- <span data-ttu-id="ef9db-120">EnumOnly: alleen de eigenschappen van de objecten in de verzameling worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="ef9db-120">EnumOnly: Displays only the properties of the objects in the collection.</span></span>

- <span data-ttu-id="ef9db-121">CoreOnly: alleen de eigenschappen van het verzamelings object worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="ef9db-121">CoreOnly: Displays only the properties of the collection object.</span></span>

- <span data-ttu-id="ef9db-122">Beide: Hiermee worden de eigenschappen van de objecten in de verzameling en de eigenschappen van het verzamelings object weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="ef9db-122">Both: Displays the properties of the objects in the collection and the properties of the collection object.</span></span>

## <a name="remarks"></a><span data-ttu-id="ef9db-123">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="ef9db-123">Remarks</span></span>

<span data-ttu-id="ef9db-124">Dit element wordt gebruikt om te definiëren hoe verzamelings objecten en de objecten in de verzameling worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="ef9db-124">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="ef9db-125">In dit geval verwijst een verzamelings object naar een object dat de interface  **System. Collections. ICollection** ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="ef9db-125">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

<span data-ttu-id="ef9db-126">Het standaard gedrag is om alleen de eigenschappen van de objecten in de verzameling weer te geven.</span><span class="sxs-lookup"><span data-stu-id="ef9db-126">The default behavior is to display only the properties of the objects in the collection.</span></span>

## <a name="see-also"></a><span data-ttu-id="ef9db-127">Zie ook</span><span class="sxs-lookup"><span data-stu-id="ef9db-127">See Also</span></span>

[<span data-ttu-id="ef9db-128">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="ef9db-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
