---
ms.date: 09/13/2016
ms.topic: reference
title: Het element Configuratie (opmaak)
description: Het element Configuratie (opmaak)
ms.openlocfilehash: 0524736d40dd7a7acb0b6fb61d1438b75672c240
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92655686"
---
# <a name="configuration-element-format"></a><span data-ttu-id="e76f6-103">Het element Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="e76f6-103">Configuration Element (Format)</span></span>

<span data-ttu-id="e76f6-104">Vertegenwoordigt het element op het hoogste niveau van een opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="e76f6-104">Represents the top-level element of a formatting file.</span></span>

<span data-ttu-id="e76f6-105">Configuratie-element</span><span class="sxs-lookup"><span data-stu-id="e76f6-105">Configuration Element</span></span>

## <a name="syntax"></a><span data-ttu-id="e76f6-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="e76f6-106">Syntax</span></span>

```xml
<Configuration>
  <DefaultSettings>...</DefaultSettings>
  <SelectionSets>...</SelectionSets>
  <Controls>...</Controls>
  <ViewDefinitions>...</ViewDefinitions>
</Configuration>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="e76f6-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="e76f6-107">Attributes and Elements</span></span>

<span data-ttu-id="e76f6-108">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `Configuration` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="e76f6-108">The following sections describe the attributes, child elements, and the parent element of the `Configuration` element.</span></span> <span data-ttu-id="e76f6-109">Dit element moet het hoofd element voor elk opmaak bestand zijn en dit element moet ten minste één onderliggend element bevatten.</span><span class="sxs-lookup"><span data-stu-id="e76f6-109">This element must be the root element for each formatting file, and this element must contain at least one child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e76f6-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="e76f6-110">Attributes</span></span>

<span data-ttu-id="e76f6-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="e76f6-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e76f6-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="e76f6-112">Child Elements</span></span>

|<span data-ttu-id="e76f6-113">Element</span><span class="sxs-lookup"><span data-stu-id="e76f6-113">Element</span></span>|<span data-ttu-id="e76f6-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e76f6-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e76f6-115">Het element Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="e76f6-115">Controls Element for Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)|<span data-ttu-id="e76f6-116">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="e76f6-116">Optional element.</span></span><br /><br /> <span data-ttu-id="e76f6-117">Hiermee definieert u de algemene besturings elementen die kunnen worden gebruikt door alle weer gaven van het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="e76f6-117">Defines the common controls that can be used by all views of the formatting file.</span></span>|
|[<span data-ttu-id="e76f6-118">Het element DefaultSettings (opmaak)</span><span class="sxs-lookup"><span data-stu-id="e76f6-118">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="e76f6-119">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="e76f6-119">Optional element.</span></span><br /><br /> <span data-ttu-id="e76f6-120">Hiermee definieert u algemene instellingen die van toepassing zijn op alle weer gaven van het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="e76f6-120">Defines common settings that apply to all the views of the formatting file.</span></span>|
|[<span data-ttu-id="e76f6-121">SelectionSets element indeling</span><span class="sxs-lookup"><span data-stu-id="e76f6-121">SelectionSets Element Format</span></span>](./selectionsets-element-format.md)|<span data-ttu-id="e76f6-122">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="e76f6-122">Optional element.</span></span><br /><br /> <span data-ttu-id="e76f6-123">Hiermee worden de algemene sets van .NET-objecten gedefinieerd die kunnen worden gebruikt door alle weer gaven van het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="e76f6-123">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span>|
|[<span data-ttu-id="e76f6-124">Het element ViewDefinitions (opmaak)</span><span class="sxs-lookup"><span data-stu-id="e76f6-124">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)|<span data-ttu-id="e76f6-125">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="e76f6-125">Optional element.</span></span><br /><br /> <span data-ttu-id="e76f6-126">Hiermee worden de weer gaven gedefinieerd waarmee objecten worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="e76f6-126">Defines the views used to display objects.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e76f6-127">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="e76f6-127">Parent Elements</span></span>

<span data-ttu-id="e76f6-128">Geen.</span><span class="sxs-lookup"><span data-stu-id="e76f6-128">None.</span></span>

## <a name="remarks"></a><span data-ttu-id="e76f6-129">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="e76f6-129">Remarks</span></span>

<span data-ttu-id="e76f6-130">Het format teren van bestanden bepaalt hoe objecten worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="e76f6-130">Formatting files define how objects are displayed.</span></span> <span data-ttu-id="e76f6-131">In de meeste gevallen bevat dit hoofd element een [ViewDefinitions](./viewdefinitions-element-format.md) -element dat de tabel, lijst en brede weer gave van het opmaak bestand definieert.</span><span class="sxs-lookup"><span data-stu-id="e76f6-131">In most cases, this root element contains a [ViewDefinitions](./viewdefinitions-element-format.md) element that defines the table, list, and wide views of the formatting file.</span></span> <span data-ttu-id="e76f6-132">Naast de weergave definities kan het opmaak bestand algemene selectie sets, instellingen en besturings elementen definiëren die door die weer gaven kunnen worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="e76f6-132">In addition to the view definitions, the formatting file can define common selection sets, settings, and controls that those views can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="e76f6-133">Zie ook</span><span class="sxs-lookup"><span data-stu-id="e76f6-133">See Also</span></span>

[<span data-ttu-id="e76f6-134">Het element Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="e76f6-134">Controls Element for Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)

[<span data-ttu-id="e76f6-135">Het element DefaultSettings (opmaak)</span><span class="sxs-lookup"><span data-stu-id="e76f6-135">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)

[<span data-ttu-id="e76f6-136">Het element SelectionSets (opmaak)</span><span class="sxs-lookup"><span data-stu-id="e76f6-136">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="e76f6-137">Het element ViewDefinitions (opmaak)</span><span class="sxs-lookup"><span data-stu-id="e76f6-137">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)

[<span data-ttu-id="e76f6-138">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="e76f6-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
