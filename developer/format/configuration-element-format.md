---
title: Configuratie-Element (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d46df0cb-50b7-4b81-82ba-37186a7b7a7f
caps.latest.revision: 28
ms.openlocfilehash: 296c63d0c774a0bf56e90dbaa32f2c221d4c3dbd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066818"
---
# <a name="configuration-element-format"></a><span data-ttu-id="69fa8-102">Het element Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="69fa8-102">Configuration Element (Format)</span></span>

<span data-ttu-id="69fa8-103">Hiermee geeft u het element op het hoogste niveau van een bestand met opmaak.</span><span class="sxs-lookup"><span data-stu-id="69fa8-103">Represents the top-level element of a formatting file.</span></span>

<span data-ttu-id="69fa8-104">Configuratie-Element</span><span class="sxs-lookup"><span data-stu-id="69fa8-104">Configuration Element</span></span>

## <a name="syntax"></a><span data-ttu-id="69fa8-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="69fa8-105">Syntax</span></span>

```xml
<Configuration>
  <DefaultSettings>...</DefaultSettings>
  <SelectionSets>...</SelectionSets>
  <Controls>...</Controls>
  <ViewDefinitions>...</ViewDefinitions>
</Configuration>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="69fa8-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="69fa8-106">Attributes and Elements</span></span>

<span data-ttu-id="69fa8-107">De volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van de `Configuration` element.</span><span class="sxs-lookup"><span data-stu-id="69fa8-107">The following sections describe the attributes, child elements, and the parent element of the `Configuration` element.</span></span> <span data-ttu-id="69fa8-108">Dit element moet het root-element voor elk bestand opmaak, en dit element moet ten minste één onderliggend element bevatten.</span><span class="sxs-lookup"><span data-stu-id="69fa8-108">This element must be the root element for each formatting file, and this element must contain at least one child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="69fa8-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="69fa8-109">Attributes</span></span>

<span data-ttu-id="69fa8-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="69fa8-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="69fa8-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="69fa8-111">Child Elements</span></span>

|<span data-ttu-id="69fa8-112">Element</span><span class="sxs-lookup"><span data-stu-id="69fa8-112">Element</span></span>|<span data-ttu-id="69fa8-113">Description</span><span class="sxs-lookup"><span data-stu-id="69fa8-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="69fa8-114">Besturingselementen-Element voor configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="69fa8-114">Controls Element for Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)|<span data-ttu-id="69fa8-115">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="69fa8-115">Optional element.</span></span><br /><br /> <span data-ttu-id="69fa8-116">Hiermee definieert u de algemene besturingselementen die kunnen worden gebruikt door alle weergaven van de opmaak-bestand.</span><span class="sxs-lookup"><span data-stu-id="69fa8-116">Defines the common controls that can be used by all views of the formatting file.</span></span>|
|[<span data-ttu-id="69fa8-117">DefaultSettings-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="69fa8-117">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="69fa8-118">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="69fa8-118">Optional element.</span></span><br /><br /> <span data-ttu-id="69fa8-119">Algemene instellingen die betrekking hebben op alle weergaven van de opmaak bestand definieert.</span><span class="sxs-lookup"><span data-stu-id="69fa8-119">Defines common settings that apply to all the views of the formatting file.</span></span>|
|[<span data-ttu-id="69fa8-120">SelectionSets Element opmaken</span><span class="sxs-lookup"><span data-stu-id="69fa8-120">SelectionSets Element Format</span></span>](./selectionsets-element-format.md)|<span data-ttu-id="69fa8-121">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="69fa8-121">Optional element.</span></span><br /><br /> <span data-ttu-id="69fa8-122">Hiermee definieert u de algemene sets met .NET-objecten die kunnen worden gebruikt door alle weergaven van de opmaak-bestand.</span><span class="sxs-lookup"><span data-stu-id="69fa8-122">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span>|
|[<span data-ttu-id="69fa8-123">ViewDefinitions-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="69fa8-123">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)|<span data-ttu-id="69fa8-124">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="69fa8-124">Optional element.</span></span><br /><br /> <span data-ttu-id="69fa8-125">Definieert de weergaven die wordt gebruikt om objecten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="69fa8-125">Defines the views used to display objects.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="69fa8-126">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="69fa8-126">Parent Elements</span></span>

<span data-ttu-id="69fa8-127">Geen.</span><span class="sxs-lookup"><span data-stu-id="69fa8-127">None.</span></span>

## <a name="remarks"></a><span data-ttu-id="69fa8-128">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="69fa8-128">Remarks</span></span>

<span data-ttu-id="69fa8-129">Opmaak bestanden definiëren hoe objecten worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="69fa8-129">Formatting files define how objects are displayed.</span></span> <span data-ttu-id="69fa8-130">In de meeste gevallen deze root-element bevat een [ViewDefinitions](./viewdefinitions-element-format.md) element dat de tabel, lijst en breed weergaven van de opmaak bestand definieert.</span><span class="sxs-lookup"><span data-stu-id="69fa8-130">In most cases, this root element contains a [ViewDefinitions](./viewdefinitions-element-format.md) element that defines the table, list, and wide views of the formatting file.</span></span> <span data-ttu-id="69fa8-131">Het opmaak-bestand kunt naast de weergavedefinities definiëren algemene selectiesets, instellingen en besturingselementen die deze weergaven kunnen gebruiken.</span><span class="sxs-lookup"><span data-stu-id="69fa8-131">In addition to the view definitions, the formatting file can define common selection sets, settings, and controls that those views can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="69fa8-132">Zie ook</span><span class="sxs-lookup"><span data-stu-id="69fa8-132">See Also</span></span>

[<span data-ttu-id="69fa8-133">Besturingselementen-Element voor configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="69fa8-133">Controls Element for Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)

[<span data-ttu-id="69fa8-134">DefaultSettings-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="69fa8-134">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)

[<span data-ttu-id="69fa8-135">SelectionSets-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="69fa8-135">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="69fa8-136">ViewDefinitions-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="69fa8-136">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)

[<span data-ttu-id="69fa8-137">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="69fa8-137">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
