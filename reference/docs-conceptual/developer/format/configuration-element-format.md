---
title: Configuratie-element (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d46df0cb-50b7-4b81-82ba-37186a7b7a7f
caps.latest.revision: 28
ms.openlocfilehash: 296c63d0c774a0bf56e90dbaa32f2c221d4c3dbd
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72354871"
---
# <a name="configuration-element-format"></a><span data-ttu-id="af403-102">Het element Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="af403-102">Configuration Element (Format)</span></span>

<span data-ttu-id="af403-103">Vertegenwoordigt het element op het hoogste niveau van een opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="af403-103">Represents the top-level element of a formatting file.</span></span>

<span data-ttu-id="af403-104">Configuratie-element</span><span class="sxs-lookup"><span data-stu-id="af403-104">Configuration Element</span></span>

## <a name="syntax"></a><span data-ttu-id="af403-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="af403-105">Syntax</span></span>

```xml
<Configuration>
  <DefaultSettings>...</DefaultSettings>
  <SelectionSets>...</SelectionSets>
  <Controls>...</Controls>
  <ViewDefinitions>...</ViewDefinitions>
</Configuration>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="af403-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="af403-106">Attributes and Elements</span></span>

<span data-ttu-id="af403-107">In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het element `Configuration` beschreven.</span><span class="sxs-lookup"><span data-stu-id="af403-107">The following sections describe the attributes, child elements, and the parent element of the `Configuration` element.</span></span> <span data-ttu-id="af403-108">Dit element moet het hoofd element voor elk opmaak bestand zijn en dit element moet ten minste één onderliggend element bevatten.</span><span class="sxs-lookup"><span data-stu-id="af403-108">This element must be the root element for each formatting file, and this element must contain at least one child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="af403-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="af403-109">Attributes</span></span>

<span data-ttu-id="af403-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="af403-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="af403-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="af403-111">Child Elements</span></span>

|<span data-ttu-id="af403-112">Element</span><span class="sxs-lookup"><span data-stu-id="af403-112">Element</span></span>|<span data-ttu-id="af403-113">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="af403-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="af403-114">Controls-element voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="af403-114">Controls Element for Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)|<span data-ttu-id="af403-115">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="af403-115">Optional element.</span></span><br /><br /> <span data-ttu-id="af403-116">Hiermee definieert u de algemene besturings elementen die kunnen worden gebruikt door alle weer gaven van het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="af403-116">Defines the common controls that can be used by all views of the formatting file.</span></span>|
|[<span data-ttu-id="af403-117">DefaultSettings-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="af403-117">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="af403-118">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="af403-118">Optional element.</span></span><br /><br /> <span data-ttu-id="af403-119">Hiermee definieert u algemene instellingen die van toepassing zijn op alle weer gaven van het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="af403-119">Defines common settings that apply to all the views of the formatting file.</span></span>|
|[<span data-ttu-id="af403-120">SelectionSets element indeling</span><span class="sxs-lookup"><span data-stu-id="af403-120">SelectionSets Element Format</span></span>](./selectionsets-element-format.md)|<span data-ttu-id="af403-121">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="af403-121">Optional element.</span></span><br /><br /> <span data-ttu-id="af403-122">Hiermee worden de algemene sets van .NET-objecten gedefinieerd die kunnen worden gebruikt door alle weer gaven van het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="af403-122">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span>|
|[<span data-ttu-id="af403-123">ViewDefinitions-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="af403-123">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)|<span data-ttu-id="af403-124">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="af403-124">Optional element.</span></span><br /><br /> <span data-ttu-id="af403-125">Hiermee worden de weer gaven gedefinieerd waarmee objecten worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="af403-125">Defines the views used to display objects.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="af403-126">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="af403-126">Parent Elements</span></span>

<span data-ttu-id="af403-127">Geen.</span><span class="sxs-lookup"><span data-stu-id="af403-127">None.</span></span>

## <a name="remarks"></a><span data-ttu-id="af403-128">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="af403-128">Remarks</span></span>

<span data-ttu-id="af403-129">Het format teren van bestanden bepaalt hoe objecten worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="af403-129">Formatting files define how objects are displayed.</span></span> <span data-ttu-id="af403-130">In de meeste gevallen bevat dit hoofd element een [ViewDefinitions](./viewdefinitions-element-format.md) -element dat de tabel, lijst en brede weer gave van het opmaak bestand definieert.</span><span class="sxs-lookup"><span data-stu-id="af403-130">In most cases, this root element contains a [ViewDefinitions](./viewdefinitions-element-format.md) element that defines the table, list, and wide views of the formatting file.</span></span> <span data-ttu-id="af403-131">Naast de weergave definities kan het opmaak bestand algemene selectie sets, instellingen en besturings elementen definiëren die door die weer gaven kunnen worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="af403-131">In addition to the view definitions, the formatting file can define common selection sets, settings, and controls that those views can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="af403-132">Zie ook</span><span class="sxs-lookup"><span data-stu-id="af403-132">See Also</span></span>

[<span data-ttu-id="af403-133">Controls-element voor configuratie (indeling)</span><span class="sxs-lookup"><span data-stu-id="af403-133">Controls Element for Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)

[<span data-ttu-id="af403-134">DefaultSettings-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="af403-134">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)

[<span data-ttu-id="af403-135">SelectionSets-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="af403-135">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="af403-136">ViewDefinitions-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="af403-136">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)

[<span data-ttu-id="af403-137">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="af403-137">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
