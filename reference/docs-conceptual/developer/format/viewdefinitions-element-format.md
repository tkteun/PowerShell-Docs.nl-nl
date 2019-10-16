---
title: ViewDefinitions-element (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 29840c10-2b30-4bb1-a8a0-ddf84d19c2d0
caps.latest.revision: 18
ms.openlocfilehash: c5ec80350c7707ccd41112ab5e1952e5dc198cca
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72353415"
---
# <a name="viewdefinitions-element-format"></a><span data-ttu-id="e4d7e-102">Het element ViewDefinitions (opmaak)</span><span class="sxs-lookup"><span data-stu-id="e4d7e-102">ViewDefinitions Element (Format)</span></span>

<span data-ttu-id="e4d7e-103">Hiermee worden de weer gaven gedefinieerd die worden gebruikt om .NET-objecten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="e4d7e-103">Defines the views used to display .NET objects.</span></span> <span data-ttu-id="e4d7e-104">Deze weer gaven kunnen de eigenschappen en script waarden van een object in tabel indeling, lijst opmaak, brede indeling en aangepaste besturings elementen weer geven.</span><span class="sxs-lookup"><span data-stu-id="e4d7e-104">These views can display the properties and script values of an object  in a table format, list format, wide format, and custom control format.</span></span>

<span data-ttu-id="e4d7e-105">Element configuratie-element (indeling) ViewDefinitions (XML-indeling)</span><span class="sxs-lookup"><span data-stu-id="e4d7e-105">Configuration Element (Format) ViewDefinitions (Format XML) Element</span></span>

## <a name="syntax"></a><span data-ttu-id="e4d7e-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="e4d7e-106">Syntax</span></span>

```xml

<ViewDefinitions>
  <View>...</View>
</ViewDefinitions>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e4d7e-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="e4d7e-107">Attributes and Elements</span></span>

<span data-ttu-id="e4d7e-108">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het element `ViewDefinitions` beschreven.</span><span class="sxs-lookup"><span data-stu-id="e4d7e-108">The following sections describe the attributes, child elements, and parent element of the `ViewDefinitions` element.</span></span> <span data-ttu-id="e4d7e-109">Er is geen limiet voor het aantal weer gaven dat kan worden gedefinieerd in een opmaak bestand en ze kunnen in elke wille keurige volg orde worden toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="e4d7e-109">There is no limit to the number of views that can be defined in a formatting file, and they can be added in any order.</span></span>

### <a name="attributes"></a><span data-ttu-id="e4d7e-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="e4d7e-110">Attributes</span></span>

<span data-ttu-id="e4d7e-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="e4d7e-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e4d7e-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="e4d7e-112">Child Elements</span></span>

|<span data-ttu-id="e4d7e-113">Element</span><span class="sxs-lookup"><span data-stu-id="e4d7e-113">Element</span></span>|<span data-ttu-id="e4d7e-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e4d7e-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e4d7e-115">Element weer geven (indeling)</span><span class="sxs-lookup"><span data-stu-id="e4d7e-115">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="e4d7e-116">Hiermee wordt een weer gave gedefinieerd die wordt gebruikt om een of meer .NET-objecten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="e4d7e-116">Defines a view that is used to display one or more .NET objects.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e4d7e-117">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="e4d7e-117">Parent Elements</span></span>

|<span data-ttu-id="e4d7e-118">Element</span><span class="sxs-lookup"><span data-stu-id="e4d7e-118">Element</span></span>|<span data-ttu-id="e4d7e-119">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e4d7e-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e4d7e-120">Configuratie-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="e4d7e-120">Configuration Element (Format)</span></span>](./configuration-element-format.md)|<span data-ttu-id="e4d7e-121">Vertegenwoordigt het element op het hoogste niveau van een opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="e4d7e-121">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e4d7e-122">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="e4d7e-122">Remarks</span></span>

<span data-ttu-id="e4d7e-123">Zie de volgende onderwerpen voor meer informatie over de onderdelen van de verschillende typen weer gaven:</span><span class="sxs-lookup"><span data-stu-id="e4d7e-123">For more information about the components of the different types of views, see the following topics:</span></span>

- [<span data-ttu-id="e4d7e-124">Een tabel weergave maken</span><span class="sxs-lookup"><span data-stu-id="e4d7e-124">Creating a Table View</span></span>](./creating-a-table-view.md)

- [<span data-ttu-id="e4d7e-125">Een lijst weergave maken</span><span class="sxs-lookup"><span data-stu-id="e4d7e-125">Creating a List View</span></span>](./creating-a-list-view.md)

- [<span data-ttu-id="e4d7e-126">Een brede weer gave maken</span><span class="sxs-lookup"><span data-stu-id="e4d7e-126">Creating a Wide View</span></span>](./creating-a-wide-view.md)

- [<span data-ttu-id="e4d7e-127">Aangepaste besturings elementen</span><span class="sxs-lookup"><span data-stu-id="e4d7e-127">Custom Controls</span></span>](./creating-custom-controls.md)

## <a name="example"></a><span data-ttu-id="e4d7e-128">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="e4d7e-128">Example</span></span>

<span data-ttu-id="e4d7e-129">In dit voor beeld wordt een element `ViewDefinitions` weer gegeven dat de bovenliggende elementen voor een tabel weergave en een lijst weergave bevat.</span><span class="sxs-lookup"><span data-stu-id="e4d7e-129">This example shows a `ViewDefinitions` element that contains the parent elements for a table view and a list view.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="e4d7e-130">Zie ook</span><span class="sxs-lookup"><span data-stu-id="e4d7e-130">See Also</span></span>

[<span data-ttu-id="e4d7e-131">Configuratie-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="e4d7e-131">Configuration Element (Format)</span></span>](./configuration-element-format.md)

[<span data-ttu-id="e4d7e-132">Element weer geven (indeling)</span><span class="sxs-lookup"><span data-stu-id="e4d7e-132">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="e4d7e-133">Een tabel weergave maken</span><span class="sxs-lookup"><span data-stu-id="e4d7e-133">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="e4d7e-134">Een lijst weergave maken</span><span class="sxs-lookup"><span data-stu-id="e4d7e-134">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="e4d7e-135">Een brede weer gave maken</span><span class="sxs-lookup"><span data-stu-id="e4d7e-135">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="e4d7e-136">Aangepaste besturings elementen</span><span class="sxs-lookup"><span data-stu-id="e4d7e-136">Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="e4d7e-137">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="e4d7e-137">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
