---
ms.date: 09/13/2016
ms.topic: reference
title: Het element ViewDefinitions (opmaak)
description: Het element ViewDefinitions (opmaak)
ms.openlocfilehash: fceef0e5ec91e8c59a7b2b90fd31ca422ff0c94d
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92664584"
---
# <a name="viewdefinitions-element-format"></a><span data-ttu-id="b1060-103">Het element ViewDefinitions (opmaak)</span><span class="sxs-lookup"><span data-stu-id="b1060-103">ViewDefinitions Element (Format)</span></span>

<span data-ttu-id="b1060-104">Hiermee worden de weer gaven gedefinieerd die worden gebruikt om .NET-objecten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="b1060-104">Defines the views used to display .NET objects.</span></span> <span data-ttu-id="b1060-105">Deze weer gaven kunnen de eigenschappen en script waarden van een object in tabel indeling, lijst opmaak, brede indeling en aangepaste besturings elementen weer geven.</span><span class="sxs-lookup"><span data-stu-id="b1060-105">These views can display the properties and script values of an object  in a table format, list format, wide format, and custom control format.</span></span>

<span data-ttu-id="b1060-106">Element configuratie-element (indeling) ViewDefinitions (XML-indeling)</span><span class="sxs-lookup"><span data-stu-id="b1060-106">Configuration Element (Format) ViewDefinitions (Format XML) Element</span></span>

## <a name="syntax"></a><span data-ttu-id="b1060-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="b1060-107">Syntax</span></span>

```xml

<ViewDefinitions>
  <View>...</View>
</ViewDefinitions>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b1060-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="b1060-108">Attributes and Elements</span></span>

<span data-ttu-id="b1060-109">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `ViewDefinitions` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="b1060-109">The following sections describe the attributes, child elements, and parent element of the `ViewDefinitions` element.</span></span> <span data-ttu-id="b1060-110">Er is geen limiet voor het aantal weer gaven dat kan worden gedefinieerd in een opmaak bestand en ze kunnen in elke wille keurige volg orde worden toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="b1060-110">There is no limit to the number of views that can be defined in a formatting file, and they can be added in any order.</span></span>

### <a name="attributes"></a><span data-ttu-id="b1060-111">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="b1060-111">Attributes</span></span>

<span data-ttu-id="b1060-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="b1060-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b1060-113">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="b1060-113">Child Elements</span></span>

|<span data-ttu-id="b1060-114">Element</span><span class="sxs-lookup"><span data-stu-id="b1060-114">Element</span></span>|<span data-ttu-id="b1060-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="b1060-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b1060-116">Het element Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="b1060-116">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="b1060-117">Hiermee wordt een weer gave gedefinieerd die wordt gebruikt om een of meer .NET-objecten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="b1060-117">Defines a view that is used to display one or more .NET objects.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b1060-118">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="b1060-118">Parent Elements</span></span>

|<span data-ttu-id="b1060-119">Element</span><span class="sxs-lookup"><span data-stu-id="b1060-119">Element</span></span>|<span data-ttu-id="b1060-120">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="b1060-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b1060-121">Het element Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="b1060-121">Configuration Element (Format)</span></span>](./configuration-element-format.md)|<span data-ttu-id="b1060-122">Vertegenwoordigt het element op het hoogste niveau van een opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="b1060-122">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b1060-123">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="b1060-123">Remarks</span></span>

<span data-ttu-id="b1060-124">Zie de volgende onderwerpen voor meer informatie over de onderdelen van de verschillende typen weer gaven:</span><span class="sxs-lookup"><span data-stu-id="b1060-124">For more information about the components of the different types of views, see the following topics:</span></span>

- [<span data-ttu-id="b1060-125">Een tabelweergave maken</span><span class="sxs-lookup"><span data-stu-id="b1060-125">Creating a Table View</span></span>](./creating-a-table-view.md)

- [<span data-ttu-id="b1060-126">Een lijstweergave maken</span><span class="sxs-lookup"><span data-stu-id="b1060-126">Creating a List View</span></span>](./creating-a-list-view.md)

- [<span data-ttu-id="b1060-127">Een brede weergave maken</span><span class="sxs-lookup"><span data-stu-id="b1060-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

- [<span data-ttu-id="b1060-128">Aangepaste besturings elementen</span><span class="sxs-lookup"><span data-stu-id="b1060-128">Custom Controls</span></span>](./creating-custom-controls.md)

## <a name="example"></a><span data-ttu-id="b1060-129">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="b1060-129">Example</span></span>

<span data-ttu-id="b1060-130">In dit voor beeld ziet u een- `ViewDefinitions` element dat de bovenliggende elementen bevat voor een tabel weergave en een lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="b1060-130">This example shows a `ViewDefinitions` element that contains the parent elements for a table view and a list view.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="b1060-131">Zie ook</span><span class="sxs-lookup"><span data-stu-id="b1060-131">See Also</span></span>

[<span data-ttu-id="b1060-132">Het element Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="b1060-132">Configuration Element (Format)</span></span>](./configuration-element-format.md)

[<span data-ttu-id="b1060-133">Het element Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="b1060-133">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="b1060-134">Een tabelweergave maken</span><span class="sxs-lookup"><span data-stu-id="b1060-134">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="b1060-135">Een lijstweergave maken</span><span class="sxs-lookup"><span data-stu-id="b1060-135">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="b1060-136">Een brede weergave maken</span><span class="sxs-lookup"><span data-stu-id="b1060-136">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="b1060-137">Aangepaste besturings elementen</span><span class="sxs-lookup"><span data-stu-id="b1060-137">Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="b1060-138">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="b1060-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
