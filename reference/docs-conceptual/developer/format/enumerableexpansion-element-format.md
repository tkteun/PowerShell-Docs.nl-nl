---
title: EnumerableExpansion-element (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93d27173-9ae4-46e5-bb78-90525915cd70
caps.latest.revision: 9
ms.openlocfilehash: bc1e58c00ca8419f9204076f0a46050281e704db
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72358975"
---
# <a name="enumerableexpansion-element-format"></a><span data-ttu-id="5011f-102">Het element EnumerableExpansion (opmaak)</span><span class="sxs-lookup"><span data-stu-id="5011f-102">EnumerableExpansion Element (Format)</span></span>

<span data-ttu-id="5011f-103">Hiermee definieert u hoe specifieke .NET-verzamelings objecten worden uitgevouwen wanneer ze in een weer gave worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="5011f-103">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>

<span data-ttu-id="5011f-104">Configuratie-element (indeling) DefaultSettings element (indeling) EnumerableExpansions element (indeling) EnumerableExpansion element (indeling)</span><span class="sxs-lookup"><span data-stu-id="5011f-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5011f-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="5011f-105">Syntax</span></span>

```xml
<EnumerableExpansion>
  <EntrySelectedBy>...</EntrySelectedBy>
  <Expand>EnumOnly, CoreOnly, Both</Expand>
</EnumerableExpansion>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5011f-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="5011f-106">Attributes and Elements</span></span>

<span data-ttu-id="5011f-107">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `EnumerableExpansion` beschreven.</span><span class="sxs-lookup"><span data-stu-id="5011f-107">The following sections describe attributes, child elements, and the parent element of the `EnumerableExpansion` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5011f-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="5011f-108">Attributes</span></span>

<span data-ttu-id="5011f-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="5011f-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5011f-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="5011f-110">Child Elements</span></span>

|<span data-ttu-id="5011f-111">Element</span><span class="sxs-lookup"><span data-stu-id="5011f-111">Element</span></span>|<span data-ttu-id="5011f-112">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="5011f-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5011f-113">EntrySelectedBy-element voor EnumerableExpansion (indeling)</span><span class="sxs-lookup"><span data-stu-id="5011f-113">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="5011f-114">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="5011f-114">Optional element.</span></span><br /><br /> <span data-ttu-id="5011f-115">Hiermee definieert u welke .NET-verzamelings objecten worden uitgevouwen door deze definitie.</span><span class="sxs-lookup"><span data-stu-id="5011f-115">Defines which .NET collection objects are expanded by this definition.</span></span>|
|[<span data-ttu-id="5011f-116">Element uitbreiden (indeling)</span><span class="sxs-lookup"><span data-stu-id="5011f-116">Expand Element (Format)</span></span>](./expand-element-format.md)|<span data-ttu-id="5011f-117">Hiermee geeft u op hoe het verzamelings object voor deze definitie moet worden uitgebreid.</span><span class="sxs-lookup"><span data-stu-id="5011f-117">Specifies how the collection object is expanded for this definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="5011f-118">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="5011f-118">Parent Elements</span></span>

|<span data-ttu-id="5011f-119">Element</span><span class="sxs-lookup"><span data-stu-id="5011f-119">Element</span></span>|<span data-ttu-id="5011f-120">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="5011f-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5011f-121">EnumerableExpansions-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="5011f-121">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)|<span data-ttu-id="5011f-122">Definieert de verschillende manieren waarop .NET-verzamelings objecten worden uitgevouwen wanneer ze in een weer gave worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="5011f-122">Defines the different ways that .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5011f-123">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="5011f-123">Remarks</span></span>

<span data-ttu-id="5011f-124">Dit element wordt gebruikt om te definiëren hoe verzamelings objecten en de objecten in de verzameling worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="5011f-124">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="5011f-125">In dit geval verwijst een verzamelings object naar een object dat de interface **System. Collections. ICollection** ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="5011f-125">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

<span data-ttu-id="5011f-126">Het standaard gedrag is om alleen de eigenschappen van de objecten in de verzameling weer te geven.</span><span class="sxs-lookup"><span data-stu-id="5011f-126">The default behavior is to display only the properties of the objects in the collection.</span></span>

## <a name="see-also"></a><span data-ttu-id="5011f-127">Zie ook</span><span class="sxs-lookup"><span data-stu-id="5011f-127">See Also</span></span>

[<span data-ttu-id="5011f-128">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="5011f-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
