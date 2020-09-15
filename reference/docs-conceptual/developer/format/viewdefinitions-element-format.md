---
title: ViewDefinitions-element (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: a108c4f8b03e3dec3905181b390aee2c82ab0028
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87772481"
---
# <a name="viewdefinitions-element-format"></a><span data-ttu-id="ef874-102">Het element ViewDefinitions (opmaak)</span><span class="sxs-lookup"><span data-stu-id="ef874-102">ViewDefinitions Element (Format)</span></span>

<span data-ttu-id="ef874-103">Hiermee worden de weer gaven gedefinieerd die worden gebruikt om .NET-objecten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="ef874-103">Defines the views used to display .NET objects.</span></span> <span data-ttu-id="ef874-104">Deze weer gaven kunnen de eigenschappen en script waarden van een object in tabel indeling, lijst opmaak, brede indeling en aangepaste besturings elementen weer geven.</span><span class="sxs-lookup"><span data-stu-id="ef874-104">These views can display the properties and script values of an object  in a table format, list format, wide format, and custom control format.</span></span>

<span data-ttu-id="ef874-105">Element configuratie-element (indeling) ViewDefinitions (XML-indeling)</span><span class="sxs-lookup"><span data-stu-id="ef874-105">Configuration Element (Format) ViewDefinitions (Format XML) Element</span></span>

## <a name="syntax"></a><span data-ttu-id="ef874-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="ef874-106">Syntax</span></span>

```xml

<ViewDefinitions>
  <View>...</View>
</ViewDefinitions>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ef874-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="ef874-107">Attributes and Elements</span></span>

<span data-ttu-id="ef874-108">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `ViewDefinitions` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="ef874-108">The following sections describe the attributes, child elements, and parent element of the `ViewDefinitions` element.</span></span> <span data-ttu-id="ef874-109">Er is geen limiet voor het aantal weer gaven dat kan worden gedefinieerd in een opmaak bestand en ze kunnen in elke wille keurige volg orde worden toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="ef874-109">There is no limit to the number of views that can be defined in a formatting file, and they can be added in any order.</span></span>

### <a name="attributes"></a><span data-ttu-id="ef874-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="ef874-110">Attributes</span></span>

<span data-ttu-id="ef874-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="ef874-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ef874-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="ef874-112">Child Elements</span></span>

|<span data-ttu-id="ef874-113">Element</span><span class="sxs-lookup"><span data-stu-id="ef874-113">Element</span></span>|<span data-ttu-id="ef874-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="ef874-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ef874-115">Het element Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="ef874-115">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="ef874-116">Hiermee wordt een weer gave gedefinieerd die wordt gebruikt om een of meer .NET-objecten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="ef874-116">Defines a view that is used to display one or more .NET objects.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ef874-117">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="ef874-117">Parent Elements</span></span>

|<span data-ttu-id="ef874-118">Element</span><span class="sxs-lookup"><span data-stu-id="ef874-118">Element</span></span>|<span data-ttu-id="ef874-119">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="ef874-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ef874-120">Het element Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="ef874-120">Configuration Element (Format)</span></span>](./configuration-element-format.md)|<span data-ttu-id="ef874-121">Vertegenwoordigt het element op het hoogste niveau van een opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="ef874-121">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ef874-122">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="ef874-122">Remarks</span></span>

<span data-ttu-id="ef874-123">Zie de volgende onderwerpen voor meer informatie over de onderdelen van de verschillende typen weer gaven:</span><span class="sxs-lookup"><span data-stu-id="ef874-123">For more information about the components of the different types of views, see the following topics:</span></span>

- [<span data-ttu-id="ef874-124">Een tabelweergave maken</span><span class="sxs-lookup"><span data-stu-id="ef874-124">Creating a Table View</span></span>](./creating-a-table-view.md)

- [<span data-ttu-id="ef874-125">Een lijstweergave maken</span><span class="sxs-lookup"><span data-stu-id="ef874-125">Creating a List View</span></span>](./creating-a-list-view.md)

- [<span data-ttu-id="ef874-126">Een brede weergave maken</span><span class="sxs-lookup"><span data-stu-id="ef874-126">Creating a Wide View</span></span>](./creating-a-wide-view.md)

- [<span data-ttu-id="ef874-127">Aangepaste besturings elementen</span><span class="sxs-lookup"><span data-stu-id="ef874-127">Custom Controls</span></span>](./creating-custom-controls.md)

## <a name="example"></a><span data-ttu-id="ef874-128">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="ef874-128">Example</span></span>

<span data-ttu-id="ef874-129">In dit voor beeld ziet u een- `ViewDefinitions` element dat de bovenliggende elementen bevat voor een tabel weergave en een lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="ef874-129">This example shows a `ViewDefinitions` element that contains the parent elements for a table view and a list view.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ef874-130">Zie ook</span><span class="sxs-lookup"><span data-stu-id="ef874-130">See Also</span></span>

[<span data-ttu-id="ef874-131">Het element Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="ef874-131">Configuration Element (Format)</span></span>](./configuration-element-format.md)

[<span data-ttu-id="ef874-132">Het element Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="ef874-132">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="ef874-133">Een tabelweergave maken</span><span class="sxs-lookup"><span data-stu-id="ef874-133">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="ef874-134">Een lijstweergave maken</span><span class="sxs-lookup"><span data-stu-id="ef874-134">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="ef874-135">Een brede weergave maken</span><span class="sxs-lookup"><span data-stu-id="ef874-135">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="ef874-136">Aangepaste besturings elementen</span><span class="sxs-lookup"><span data-stu-id="ef874-136">Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="ef874-137">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="ef874-137">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
