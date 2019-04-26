---
title: EnumerableExpansion-Element (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93d27173-9ae4-46e5-bb78-90525915cd70
caps.latest.revision: 9
ms.openlocfilehash: bc1e58c00ca8419f9204076f0a46050281e704db
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066138"
---
# <a name="enumerableexpansion-element-format"></a><span data-ttu-id="aed0e-102">Het element EnumerableExpansion (opmaak)</span><span class="sxs-lookup"><span data-stu-id="aed0e-102">EnumerableExpansion Element (Format)</span></span>

<span data-ttu-id="aed0e-103">Hiermee definieert u hoe specifieke .NET-verzameling objecten worden uitgevouwen wanneer ze worden weergegeven in een weergave.</span><span class="sxs-lookup"><span data-stu-id="aed0e-103">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>

<span data-ttu-id="aed0e-104">Configuratie-Element (indeling) DefaultSettings-Element (indeling) EnumerableExpansions-Element (indeling) EnumerableExpansion Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="aed0e-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="aed0e-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="aed0e-105">Syntax</span></span>

```xml
<EnumerableExpansion>
  <EntrySelectedBy>...</EntrySelectedBy>
  <Expand>EnumOnly, CoreOnly, Both</Expand>
</EnumerableExpansion>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="aed0e-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="aed0e-106">Attributes and Elements</span></span>

<span data-ttu-id="aed0e-107">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `EnumerableExpansion` element.</span><span class="sxs-lookup"><span data-stu-id="aed0e-107">The following sections describe attributes, child elements, and the parent element of the `EnumerableExpansion` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="aed0e-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="aed0e-108">Attributes</span></span>

<span data-ttu-id="aed0e-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="aed0e-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="aed0e-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="aed0e-110">Child Elements</span></span>

|<span data-ttu-id="aed0e-111">Element</span><span class="sxs-lookup"><span data-stu-id="aed0e-111">Element</span></span>|<span data-ttu-id="aed0e-112">Description</span><span class="sxs-lookup"><span data-stu-id="aed0e-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="aed0e-113">EntrySelectedBy-Element voor EnumerableExpansion (indeling)</span><span class="sxs-lookup"><span data-stu-id="aed0e-113">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="aed0e-114">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="aed0e-114">Optional element.</span></span><br /><br /> <span data-ttu-id="aed0e-115">Hiermee definieert u welke .NET verzameling objecten worden uitgebreid door deze definitie.</span><span class="sxs-lookup"><span data-stu-id="aed0e-115">Defines which .NET collection objects are expanded by this definition.</span></span>|
|[<span data-ttu-id="aed0e-116">Vouw Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="aed0e-116">Expand Element (Format)</span></span>](./expand-element-format.md)|<span data-ttu-id="aed0e-117">Hiermee geeft u op hoe het verzamelingsobject voor deze definitie is uitgevouwen.</span><span class="sxs-lookup"><span data-stu-id="aed0e-117">Specifies how the collection object is expanded for this definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="aed0e-118">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="aed0e-118">Parent Elements</span></span>

|<span data-ttu-id="aed0e-119">Element</span><span class="sxs-lookup"><span data-stu-id="aed0e-119">Element</span></span>|<span data-ttu-id="aed0e-120">Description</span><span class="sxs-lookup"><span data-stu-id="aed0e-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="aed0e-121">EnumerableExpansions-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="aed0e-121">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)|<span data-ttu-id="aed0e-122">Hiermee definieert u de verschillende manieren die .NET-verzameling objecten worden uitgevouwen wanneer ze worden weergegeven in een weergave.</span><span class="sxs-lookup"><span data-stu-id="aed0e-122">Defines the different ways that .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="aed0e-123">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="aed0e-123">Remarks</span></span>

<span data-ttu-id="aed0e-124">Dit element wordt gebruikt om te definiëren hoe de verzameling en de objecten in de verzameling worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="aed0e-124">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="aed0e-125">In dit geval een verzamelingsobject verwijst naar objecten die ondersteuning biedt voor de **System.Collections.ICollection** interface.</span><span class="sxs-lookup"><span data-stu-id="aed0e-125">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

<span data-ttu-id="aed0e-126">Het standaardgedrag is om alleen de eigenschappen van de objecten in de verzameling weer te geven.</span><span class="sxs-lookup"><span data-stu-id="aed0e-126">The default behavior is to display only the properties of the objects in the collection.</span></span>

## <a name="see-also"></a><span data-ttu-id="aed0e-127">Zie ook</span><span class="sxs-lookup"><span data-stu-id="aed0e-127">See Also</span></span>

[<span data-ttu-id="aed0e-128">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="aed0e-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
