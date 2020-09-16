---
title: Configuratie-element (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 90be02f8e27c0bd391e01da1a08ecd8eeb29b84c
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783837"
---
# <a name="configuration-element-format"></a><span data-ttu-id="dfada-102">Het element Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="dfada-102">Configuration Element (Format)</span></span>

<span data-ttu-id="dfada-103">Vertegenwoordigt het element op het hoogste niveau van een opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="dfada-103">Represents the top-level element of a formatting file.</span></span>

<span data-ttu-id="dfada-104">Configuratie-element</span><span class="sxs-lookup"><span data-stu-id="dfada-104">Configuration Element</span></span>

## <a name="syntax"></a><span data-ttu-id="dfada-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="dfada-105">Syntax</span></span>

```xml
<Configuration>
  <DefaultSettings>...</DefaultSettings>
  <SelectionSets>...</SelectionSets>
  <Controls>...</Controls>
  <ViewDefinitions>...</ViewDefinitions>
</Configuration>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="dfada-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="dfada-106">Attributes and Elements</span></span>

<span data-ttu-id="dfada-107">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `Configuration` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="dfada-107">The following sections describe the attributes, child elements, and the parent element of the `Configuration` element.</span></span> <span data-ttu-id="dfada-108">Dit element moet het hoofd element voor elk opmaak bestand zijn en dit element moet ten minste één onderliggend element bevatten.</span><span class="sxs-lookup"><span data-stu-id="dfada-108">This element must be the root element for each formatting file, and this element must contain at least one child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="dfada-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="dfada-109">Attributes</span></span>

<span data-ttu-id="dfada-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="dfada-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="dfada-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="dfada-111">Child Elements</span></span>

|<span data-ttu-id="dfada-112">Element</span><span class="sxs-lookup"><span data-stu-id="dfada-112">Element</span></span>|<span data-ttu-id="dfada-113">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="dfada-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dfada-114">Het element Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="dfada-114">Controls Element for Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)|<span data-ttu-id="dfada-115">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="dfada-115">Optional element.</span></span><br /><br /> <span data-ttu-id="dfada-116">Hiermee definieert u de algemene besturings elementen die kunnen worden gebruikt door alle weer gaven van het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="dfada-116">Defines the common controls that can be used by all views of the formatting file.</span></span>|
|[<span data-ttu-id="dfada-117">Het element DefaultSettings (opmaak)</span><span class="sxs-lookup"><span data-stu-id="dfada-117">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="dfada-118">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="dfada-118">Optional element.</span></span><br /><br /> <span data-ttu-id="dfada-119">Hiermee definieert u algemene instellingen die van toepassing zijn op alle weer gaven van het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="dfada-119">Defines common settings that apply to all the views of the formatting file.</span></span>|
|[<span data-ttu-id="dfada-120">SelectionSets element indeling</span><span class="sxs-lookup"><span data-stu-id="dfada-120">SelectionSets Element Format</span></span>](./selectionsets-element-format.md)|<span data-ttu-id="dfada-121">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="dfada-121">Optional element.</span></span><br /><br /> <span data-ttu-id="dfada-122">Hiermee worden de algemene sets van .NET-objecten gedefinieerd die kunnen worden gebruikt door alle weer gaven van het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="dfada-122">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span>|
|[<span data-ttu-id="dfada-123">Het element ViewDefinitions (opmaak)</span><span class="sxs-lookup"><span data-stu-id="dfada-123">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)|<span data-ttu-id="dfada-124">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="dfada-124">Optional element.</span></span><br /><br /> <span data-ttu-id="dfada-125">Hiermee worden de weer gaven gedefinieerd waarmee objecten worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="dfada-125">Defines the views used to display objects.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="dfada-126">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="dfada-126">Parent Elements</span></span>

<span data-ttu-id="dfada-127">Geen.</span><span class="sxs-lookup"><span data-stu-id="dfada-127">None.</span></span>

## <a name="remarks"></a><span data-ttu-id="dfada-128">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="dfada-128">Remarks</span></span>

<span data-ttu-id="dfada-129">Het format teren van bestanden bepaalt hoe objecten worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="dfada-129">Formatting files define how objects are displayed.</span></span> <span data-ttu-id="dfada-130">In de meeste gevallen bevat dit hoofd element een [ViewDefinitions](./viewdefinitions-element-format.md) -element dat de tabel, lijst en brede weer gave van het opmaak bestand definieert.</span><span class="sxs-lookup"><span data-stu-id="dfada-130">In most cases, this root element contains a [ViewDefinitions](./viewdefinitions-element-format.md) element that defines the table, list, and wide views of the formatting file.</span></span> <span data-ttu-id="dfada-131">Naast de weergave definities kan het opmaak bestand algemene selectie sets, instellingen en besturings elementen definiëren die door die weer gaven kunnen worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="dfada-131">In addition to the view definitions, the formatting file can define common selection sets, settings, and controls that those views can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="dfada-132">Zie ook</span><span class="sxs-lookup"><span data-stu-id="dfada-132">See Also</span></span>

[<span data-ttu-id="dfada-133">Het element Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="dfada-133">Controls Element for Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)

[<span data-ttu-id="dfada-134">Het element DefaultSettings (opmaak)</span><span class="sxs-lookup"><span data-stu-id="dfada-134">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)

[<span data-ttu-id="dfada-135">Het element SelectionSets (opmaak)</span><span class="sxs-lookup"><span data-stu-id="dfada-135">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="dfada-136">Het element ViewDefinitions (opmaak)</span><span class="sxs-lookup"><span data-stu-id="dfada-136">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)

[<span data-ttu-id="dfada-137">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="dfada-137">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
