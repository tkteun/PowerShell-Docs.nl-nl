---
ms.date: 09/13/2016
ms.topic: reference
title: Het element EnumerableExpansions (opmaak)
description: Het element EnumerableExpansions (opmaak)
ms.openlocfilehash: 789599e6ff368b4685c7937d5b6eb38618752f9e
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660171"
---
# <a name="enumerableexpansions-element-format"></a><span data-ttu-id="d7146-103">Het element EnumerableExpansions (opmaak)</span><span class="sxs-lookup"><span data-stu-id="d7146-103">EnumerableExpansions Element (Format)</span></span>

<span data-ttu-id="d7146-104">Hiermee definieert u hoe .NET-verzamelings objecten worden uitgevouwen wanneer ze worden weer gegeven in een weer gave.</span><span class="sxs-lookup"><span data-stu-id="d7146-104">Defines how .NET collection objects are expanded when they are displayed in a view.</span></span>

<span data-ttu-id="d7146-105">Configuratie-element (indeling) DefaultSettings element (indeling) EnumerableExpansions element (indeling)</span><span class="sxs-lookup"><span data-stu-id="d7146-105">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d7146-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="d7146-106">Syntax</span></span>

```xml
<EnumerableExpansions>
  <EnumerableExpansion>...</EnumerableExpansion>
</EnumerableExpansions>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d7146-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="d7146-107">Attributes and Elements</span></span>

<span data-ttu-id="d7146-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `EnumerableExpansions` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="d7146-108">The following sections describe attributes, child elements, and the parent element of the `EnumerableExpansions` element.</span></span> <span data-ttu-id="d7146-109">Er is geen limiet voor het aantal onderliggende elementen dat u kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="d7146-109">There is no limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="d7146-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="d7146-110">Attributes</span></span>

<span data-ttu-id="d7146-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="d7146-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d7146-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="d7146-112">Child Elements</span></span>

|<span data-ttu-id="d7146-113">Element</span><span class="sxs-lookup"><span data-stu-id="d7146-113">Element</span></span>|<span data-ttu-id="d7146-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="d7146-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d7146-115">Het element EnumerableExpansion (opmaak)</span><span class="sxs-lookup"><span data-stu-id="d7146-115">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="d7146-116">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="d7146-116">Optional element.</span></span><br /><br /> <span data-ttu-id="d7146-117">Hiermee worden de specifieke .NET-verzamelings objecten gedefinieerd die worden uitgevouwen wanneer ze worden weer gegeven in een weer gave.</span><span class="sxs-lookup"><span data-stu-id="d7146-117">Defines the specific .NET collection objects that are expanded when they are displayed in a view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d7146-118">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="d7146-118">Parent Elements</span></span>

|<span data-ttu-id="d7146-119">Element</span><span class="sxs-lookup"><span data-stu-id="d7146-119">Element</span></span>|<span data-ttu-id="d7146-120">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="d7146-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d7146-121">Het element DefaultSettings (opmaak)</span><span class="sxs-lookup"><span data-stu-id="d7146-121">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="d7146-122">Hiermee definieert u algemene instellingen die van toepassing zijn op alle weer gaven van het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="d7146-122">Defines common settings that apply to all the views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d7146-123">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="d7146-123">Remarks</span></span>

<span data-ttu-id="d7146-124">Dit element wordt gebruikt om te definiëren hoe verzamelings objecten en de objecten in de verzameling worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="d7146-124">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="d7146-125">In dit geval verwijst een verzamelings object naar een object dat de interface  **System. Collections. ICollection** ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="d7146-125">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

## <a name="see-also"></a><span data-ttu-id="d7146-126">Zie ook</span><span class="sxs-lookup"><span data-stu-id="d7146-126">See Also</span></span>

[<span data-ttu-id="d7146-127">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="d7146-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
