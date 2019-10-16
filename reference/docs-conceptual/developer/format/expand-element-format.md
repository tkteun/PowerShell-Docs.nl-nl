---
title: Element uitbreiden (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: faa0314b-f6f1-44fd-ad2b-b00cbe38923f
caps.latest.revision: 9
ms.openlocfilehash: 8b924c989133b47e4d95d8429778003c76595d58
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72358971"
---
# <a name="expand-element-format"></a><span data-ttu-id="ed2a8-102">Het element Uitvouwen (opmaak)</span><span class="sxs-lookup"><span data-stu-id="ed2a8-102">Expand Element (Format)</span></span>

<span data-ttu-id="ed2a8-103">Hiermee geeft u op hoe het verzamelings object voor deze definitie moet worden uitgebreid.</span><span class="sxs-lookup"><span data-stu-id="ed2a8-103">Specifies how the collection object is expanded for this definition.</span></span>

<span data-ttu-id="ed2a8-104">Configuratie-element (indeling) DefaultSettings element (indeling) EnumerableExpansions element (indeling) EnumerableExpansion element (indeling) element uitbreiden (indeling)</span><span class="sxs-lookup"><span data-stu-id="ed2a8-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) Expand Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ed2a8-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="ed2a8-105">Syntax</span></span>

```xml
<Expand>EnumOnly, CoreOnly, Both</Expand>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ed2a8-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="ed2a8-106">Attributes and Elements</span></span>

<span data-ttu-id="ed2a8-107">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `Expand` beschreven.</span><span class="sxs-lookup"><span data-stu-id="ed2a8-107">The following sections describe attributes, child elements, and the parent element of the `Expand` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ed2a8-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="ed2a8-108">Attributes</span></span>

<span data-ttu-id="ed2a8-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="ed2a8-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ed2a8-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="ed2a8-110">Child Elements</span></span>

<span data-ttu-id="ed2a8-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="ed2a8-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ed2a8-112">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="ed2a8-112">Parent Elements</span></span>

|<span data-ttu-id="ed2a8-113">Element</span><span class="sxs-lookup"><span data-stu-id="ed2a8-113">Element</span></span>|<span data-ttu-id="ed2a8-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="ed2a8-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ed2a8-115">EnumerableExpansion-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="ed2a8-115">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="ed2a8-116">Hiermee definieert u hoe specifieke .NET-verzamelings objecten worden uitgevouwen wanneer ze in een weer gave worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="ed2a8-116">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ed2a8-117">Tekst waarde</span><span class="sxs-lookup"><span data-stu-id="ed2a8-117">Text Value</span></span>

<span data-ttu-id="ed2a8-118">Geef een van de volgende waarden op:</span><span class="sxs-lookup"><span data-stu-id="ed2a8-118">Specify one of the following values:</span></span>

- <span data-ttu-id="ed2a8-119">EnumOnly: alleen de eigenschappen van de objecten in de verzameling worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="ed2a8-119">EnumOnly: Displays only the properties of the objects in the collection.</span></span>

- <span data-ttu-id="ed2a8-120">CoreOnly: alleen de eigenschappen van het verzamelings object worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="ed2a8-120">CoreOnly: Displays only the properties of the collection object.</span></span>

- <span data-ttu-id="ed2a8-121">Beide: Hiermee worden de eigenschappen van de objecten in de verzameling en de eigenschappen van het verzamelings object weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="ed2a8-121">Both: Displays the properties of the objects in the collection and the properties of the collection object.</span></span>

## <a name="remarks"></a><span data-ttu-id="ed2a8-122">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="ed2a8-122">Remarks</span></span>

<span data-ttu-id="ed2a8-123">Dit element wordt gebruikt om te definiëren hoe verzamelings objecten en de objecten in de verzameling worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="ed2a8-123">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="ed2a8-124">In dit geval verwijst een verzamelings object naar een object dat de interface **System. Collections. ICollection** ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="ed2a8-124">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

<span data-ttu-id="ed2a8-125">Het standaard gedrag is om alleen de eigenschappen van de objecten in de verzameling weer te geven.</span><span class="sxs-lookup"><span data-stu-id="ed2a8-125">The default behavior is to display only the properties of the objects in the collection.</span></span>

## <a name="see-also"></a><span data-ttu-id="ed2a8-126">Zie ook</span><span class="sxs-lookup"><span data-stu-id="ed2a8-126">See Also</span></span>

[<span data-ttu-id="ed2a8-127">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="ed2a8-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
