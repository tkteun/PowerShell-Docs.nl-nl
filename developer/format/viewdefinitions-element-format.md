---
title: ViewDefinitions-Element (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 29840c10-2b30-4bb1-a8a0-ddf84d19c2d0
caps.latest.revision: 18
ms.openlocfilehash: c5ec80350c7707ccd41112ab5e1952e5dc198cca
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083702"
---
# <a name="viewdefinitions-element-format"></a><span data-ttu-id="6df0e-102">Het element ViewDefinitions (opmaak)</span><span class="sxs-lookup"><span data-stu-id="6df0e-102">ViewDefinitions Element (Format)</span></span>

<span data-ttu-id="6df0e-103">Definieert de weergaven die wordt gebruikt om .NET-objecten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="6df0e-103">Defines the views used to display .NET objects.</span></span> <span data-ttu-id="6df0e-104">Deze weergaven kunnen de eigenschappen en waarden van script van een object in een tabelindeling, lijstweergave, beeldschermen en indeling van aangepast besturingselement weergegeven.</span><span class="sxs-lookup"><span data-stu-id="6df0e-104">These views can display the properties and script values of an object  in a table format, list format, wide format, and custom control format.</span></span>

<span data-ttu-id="6df0e-105">Configuration Element (Format) ViewDefinitions (Format XML) Element</span><span class="sxs-lookup"><span data-stu-id="6df0e-105">Configuration Element (Format) ViewDefinitions (Format XML) Element</span></span>

## <a name="syntax"></a><span data-ttu-id="6df0e-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="6df0e-106">Syntax</span></span>

```xml

<ViewDefinitions>
  <View>...</View>
</ViewDefinitions>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6df0e-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="6df0e-107">Attributes and Elements</span></span>

<span data-ttu-id="6df0e-108">De volgende secties worden de kenmerken, de onderliggende elementen en het bovenliggende element van de `ViewDefinitions` element.</span><span class="sxs-lookup"><span data-stu-id="6df0e-108">The following sections describe the attributes, child elements, and parent element of the `ViewDefinitions` element.</span></span> <span data-ttu-id="6df0e-109">Er is geen limiet voor het aantal weergaven die kunnen worden gedefinieerd in een bestand met opmaak, en ze kunnen in willekeurige volgorde worden toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="6df0e-109">There is no limit to the number of views that can be defined in a formatting file, and they can be added in any order.</span></span>

### <a name="attributes"></a><span data-ttu-id="6df0e-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="6df0e-110">Attributes</span></span>

<span data-ttu-id="6df0e-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="6df0e-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6df0e-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="6df0e-112">Child Elements</span></span>

|<span data-ttu-id="6df0e-113">Element</span><span class="sxs-lookup"><span data-stu-id="6df0e-113">Element</span></span>|<span data-ttu-id="6df0e-114">Description</span><span class="sxs-lookup"><span data-stu-id="6df0e-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6df0e-115">Weergave-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="6df0e-115">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="6df0e-116">Hiermee definieert u een weergave die wordt gebruikt om een of meer .NET-objecten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="6df0e-116">Defines a view that is used to display one or more .NET objects.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="6df0e-117">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="6df0e-117">Parent Elements</span></span>

|<span data-ttu-id="6df0e-118">Element</span><span class="sxs-lookup"><span data-stu-id="6df0e-118">Element</span></span>|<span data-ttu-id="6df0e-119">Description</span><span class="sxs-lookup"><span data-stu-id="6df0e-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6df0e-120">Configuratie-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="6df0e-120">Configuration Element (Format)</span></span>](./configuration-element-format.md)|<span data-ttu-id="6df0e-121">Hiermee geeft u het element op het hoogste niveau van een bestand met opmaak.</span><span class="sxs-lookup"><span data-stu-id="6df0e-121">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6df0e-122">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="6df0e-122">Remarks</span></span>

<span data-ttu-id="6df0e-123">Zie de volgende onderwerpen voor meer informatie over de onderdelen van de verschillende typen weergaven:</span><span class="sxs-lookup"><span data-stu-id="6df0e-123">For more information about the components of the different types of views, see the following topics:</span></span>

- [<span data-ttu-id="6df0e-124">Het maken van een tabelweergave</span><span class="sxs-lookup"><span data-stu-id="6df0e-124">Creating a Table View</span></span>](./creating-a-table-view.md)

- [<span data-ttu-id="6df0e-125">Het maken van een lijst weergeven</span><span class="sxs-lookup"><span data-stu-id="6df0e-125">Creating a List View</span></span>](./creating-a-list-view.md)

- [<span data-ttu-id="6df0e-126">Het maken van een brede weergave</span><span class="sxs-lookup"><span data-stu-id="6df0e-126">Creating a Wide View</span></span>](./creating-a-wide-view.md)

- [<span data-ttu-id="6df0e-127">Aangepaste besturingselementen</span><span class="sxs-lookup"><span data-stu-id="6df0e-127">Custom Controls</span></span>](./creating-custom-controls.md)

## <a name="example"></a><span data-ttu-id="6df0e-128">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="6df0e-128">Example</span></span>

<span data-ttu-id="6df0e-129">In dit voorbeeld ziet u een `ViewDefinitions` element met de bovenliggende elementen voor een overzicht van de tabel en een lijst weergeven.</span><span class="sxs-lookup"><span data-stu-id="6df0e-129">This example shows a `ViewDefinitions` element that contains the parent elements for a table view and a list view.</span></span>

```xml
<Configuration>
  <ViewDefinitions>
    <View>
      <TableControl>...</TableControl>
    </View>
    <View>
      <ListControl>...</ListControl>
    </View>
  </ViewDefinitions>
</Configuration>
```

## <a name="see-also"></a><span data-ttu-id="6df0e-130">Zie ook</span><span class="sxs-lookup"><span data-stu-id="6df0e-130">See Also</span></span>

[<span data-ttu-id="6df0e-131">Configuratie-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="6df0e-131">Configuration Element (Format)</span></span>](./configuration-element-format.md)

[<span data-ttu-id="6df0e-132">Weergave-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="6df0e-132">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="6df0e-133">Het maken van een tabelweergave</span><span class="sxs-lookup"><span data-stu-id="6df0e-133">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="6df0e-134">Het maken van een lijst weergeven</span><span class="sxs-lookup"><span data-stu-id="6df0e-134">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="6df0e-135">Het maken van een brede weergave</span><span class="sxs-lookup"><span data-stu-id="6df0e-135">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="6df0e-136">Aangepaste besturingselementen</span><span class="sxs-lookup"><span data-stu-id="6df0e-136">Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="6df0e-137">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="6df0e-137">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
