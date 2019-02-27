---
title: Vouw Element (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: faa0314b-f6f1-44fd-ad2b-b00cbe38923f
caps.latest.revision: 9
ms.openlocfilehash: 8b924c989133b47e4d95d8429778003c76595d58
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848613"
---
# <a name="expand-element-format"></a><span data-ttu-id="c14a9-102">Het element Uitvouwen (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c14a9-102">Expand Element (Format)</span></span>

<span data-ttu-id="c14a9-103">Hiermee geeft u op hoe het verzamelingsobject voor deze definitie is uitgevouwen.</span><span class="sxs-lookup"><span data-stu-id="c14a9-103">Specifies how the collection object is expanded for this definition.</span></span>

<span data-ttu-id="c14a9-104">Configuratie-Element (indeling) DefaultSettings-Element (indeling) EnumerableExpansions-Element (indeling) EnumerableExpansion Element (indeling) Vouw Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="c14a9-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) Expand Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c14a9-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="c14a9-105">Syntax</span></span>

```xml
<Expand>EnumOnly, CoreOnly, Both</Expand>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c14a9-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="c14a9-106">Attributes and Elements</span></span>

<span data-ttu-id="c14a9-107">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `Expand` element.</span><span class="sxs-lookup"><span data-stu-id="c14a9-107">The following sections describe attributes, child elements, and the parent element of the `Expand` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c14a9-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="c14a9-108">Attributes</span></span>

<span data-ttu-id="c14a9-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="c14a9-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c14a9-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="c14a9-110">Child Elements</span></span>

<span data-ttu-id="c14a9-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="c14a9-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c14a9-112">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="c14a9-112">Parent Elements</span></span>

|<span data-ttu-id="c14a9-113">Element</span><span class="sxs-lookup"><span data-stu-id="c14a9-113">Element</span></span>|<span data-ttu-id="c14a9-114">Description</span><span class="sxs-lookup"><span data-stu-id="c14a9-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c14a9-115">EnumerableExpansion-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="c14a9-115">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="c14a9-116">Hiermee definieert u hoe specifieke .NET-verzameling objecten worden uitgevouwen wanneer ze worden weergegeven in een weergave.</span><span class="sxs-lookup"><span data-stu-id="c14a9-116">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c14a9-117">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="c14a9-117">Text Value</span></span>

<span data-ttu-id="c14a9-118">Geef een van de volgende waarden:</span><span class="sxs-lookup"><span data-stu-id="c14a9-118">Specify one of the following values:</span></span>

- <span data-ttu-id="c14a9-119">EnumOnly: Geeft alleen de eigenschappen van de objecten in de verzameling.</span><span class="sxs-lookup"><span data-stu-id="c14a9-119">EnumOnly: Displays only the properties of the objects in the collection.</span></span>

- <span data-ttu-id="c14a9-120">CoreOnly: Geeft alleen de eigenschappen van het verzamelingsobject.</span><span class="sxs-lookup"><span data-stu-id="c14a9-120">CoreOnly: Displays only the properties of the collection object.</span></span>

- <span data-ttu-id="c14a9-121">Beide: Geeft de eigenschappen van de objecten in de verzameling en de eigenschappen van het verzamelingsobject.</span><span class="sxs-lookup"><span data-stu-id="c14a9-121">Both: Displays the properties of the objects in the collection and the properties of the collection object.</span></span>

## <a name="remarks"></a><span data-ttu-id="c14a9-122">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="c14a9-122">Remarks</span></span>

<span data-ttu-id="c14a9-123">Dit element wordt gebruikt om te definiëren hoe de verzameling en de objecten in de verzameling worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="c14a9-123">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="c14a9-124">In dit geval een verzamelingsobject verwijst naar objecten die ondersteuning biedt voor de **System.Collections.ICollection** interface.</span><span class="sxs-lookup"><span data-stu-id="c14a9-124">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

<span data-ttu-id="c14a9-125">Het standaardgedrag is om alleen de eigenschappen van de objecten in de verzameling weer te geven.</span><span class="sxs-lookup"><span data-stu-id="c14a9-125">The default behavior is to display only the properties of the objects in the collection.</span></span>

## <a name="see-also"></a><span data-ttu-id="c14a9-126">Zie ook</span><span class="sxs-lookup"><span data-stu-id="c14a9-126">See Also</span></span>

[<span data-ttu-id="c14a9-127">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="c14a9-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
