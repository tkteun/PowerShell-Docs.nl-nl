---
title: DefaultSettings-Element (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 41c56499-ee20-4821-830a-478fdcc33f83
caps.latest.revision: 11
ms.openlocfilehash: 59cc0514087cc52438e0d1271b8b77a7799eb32c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846576"
---
# <a name="defaultsettings-element-format"></a><span data-ttu-id="b97d7-102">Het element DefaultSettings (opmaak)</span><span class="sxs-lookup"><span data-stu-id="b97d7-102">DefaultSettings Element (Format)</span></span>

<span data-ttu-id="b97d7-103">Algemene instellingen die betrekking hebben op alle weergaven van de opmaak bestand definieert.</span><span class="sxs-lookup"><span data-stu-id="b97d7-103">Defines common settings that apply to all the views of the formatting file.</span></span> <span data-ttu-id="b97d7-104">Algemene instellingen omvatten weergeven van fouten, tekstterugloop in tabellen, definiëren hoe verzamelingen zijn uitgevouwen, en meer.</span><span class="sxs-lookup"><span data-stu-id="b97d7-104">Common settings include displaying errors, wrapping text in tables, defining how collections are expanded, and more.</span></span>

<span data-ttu-id="b97d7-105">Configuratie-Element (indeling)-DefaultSettings Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="b97d7-105">Configuration Element (Format) DefaultSettings Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b97d7-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="b97d7-106">Syntax</span></span>

```xml
<DefaultSettings>
  <ShowError/>
  <DisplayError/>
 <PropertyCountForTable>NumberOfProperties</PropertyCountFortable>
  <WrapTables/>
  <EnumerableExpansions>...</EnumerableExpansions>
</DefaultSettings>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b97d7-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="b97d7-107">Attributes and Elements</span></span>

<span data-ttu-id="b97d7-108">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `DefaultSettings` element.</span><span class="sxs-lookup"><span data-stu-id="b97d7-108">The following sections describe attributes, child elements, and the parent element of the `DefaultSettings` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b97d7-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="b97d7-109">Attributes</span></span>

<span data-ttu-id="b97d7-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="b97d7-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b97d7-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="b97d7-111">Child Elements</span></span>

|<span data-ttu-id="b97d7-112">Element</span><span class="sxs-lookup"><span data-stu-id="b97d7-112">Element</span></span>|<span data-ttu-id="b97d7-113">Description</span><span class="sxs-lookup"><span data-stu-id="b97d7-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b97d7-114">DisplayError-Element (Frmat)</span><span class="sxs-lookup"><span data-stu-id="b97d7-114">DisplayError Element (Frmat)</span></span>](./displayerror-element-format.md)|<span data-ttu-id="b97d7-115">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="b97d7-115">Optional element.</span></span><br /><br /> <span data-ttu-id="b97d7-116">Hiermee geeft u op dat de tekenreeks #ERR wordt weergegeven wanneer een fout optreedt bij het weergeven van een hoeveelheid gegevens.</span><span class="sxs-lookup"><span data-stu-id="b97d7-116">Specifies that the string #ERR is displayed when an error occurs while displaying a piece of data.</span></span>|
|[<span data-ttu-id="b97d7-117">EnumerableExpansions-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="b97d7-117">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)|<span data-ttu-id="b97d7-118">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="b97d7-118">Optional element.</span></span><br /><br /> <span data-ttu-id="b97d7-119">Hiermee definieert u de verschillende manieren waarop .NET-worden uitgevouwen objecten wanneer ze worden weergegeven in een weergave.</span><span class="sxs-lookup"><span data-stu-id="b97d7-119">Defines the different ways that .NET objects are expanded when they are displayed in a view.</span></span>|
|[<span data-ttu-id="b97d7-120">PropertyCountForTable (Format)</span><span class="sxs-lookup"><span data-stu-id="b97d7-120">PropertyCountForTable (Format)</span></span>](./propertycountfortable-element-format.md)|<span data-ttu-id="b97d7-121">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="b97d7-121">Optional element.</span></span><br /><br /> <span data-ttu-id="b97d7-122">Hiermee geeft u het minimum aantal eigenschappen die een object hebben moet om het object in een tabel weer te geven.</span><span class="sxs-lookup"><span data-stu-id="b97d7-122">Specifies the minimum number of properties that an object must have to display the object in a table view.</span></span>|
|[<span data-ttu-id="b97d7-123">ShowError Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="b97d7-123">ShowError Element (Format)</span></span>](./showerror-element-format.md)|<span data-ttu-id="b97d7-124">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="b97d7-124">Optional element.</span></span><br /><br /> <span data-ttu-id="b97d7-125">Hiermee geeft u op dat de volledige foutrecord wordt weergegeven wanneer een fout optreedt bij het weergeven van een hoeveelheid gegevens.</span><span class="sxs-lookup"><span data-stu-id="b97d7-125">Specifies that the full error record is displayed when an error occurs while displaying a piece of data.</span></span>|
|[<span data-ttu-id="b97d7-126">WrapTables-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="b97d7-126">WrapTables Element (Format)</span></span>](./wraptables-element-format.md)|<span data-ttu-id="b97d7-127">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="b97d7-127">Optional element.</span></span><br /><br /> <span data-ttu-id="b97d7-128">Hiermee geeft u op dat de gegevens in een tabel is verplaatst naar de volgende regel als niet in de breedte van de kolom past.</span><span class="sxs-lookup"><span data-stu-id="b97d7-128">Specifies that data in a table is moved to the next line if it does not fit into the width of the column.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b97d7-129">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="b97d7-129">Parent Elements</span></span>

|<span data-ttu-id="b97d7-130">Element</span><span class="sxs-lookup"><span data-stu-id="b97d7-130">Element</span></span>|<span data-ttu-id="b97d7-131">Description</span><span class="sxs-lookup"><span data-stu-id="b97d7-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b97d7-132">Configuratie-Element</span><span class="sxs-lookup"><span data-stu-id="b97d7-132">Configuration Element</span></span>](./configuration-element-format.md)|<span data-ttu-id="b97d7-133">Hiermee geeft u het element op het hoogste niveau van een bestand met opmaak.</span><span class="sxs-lookup"><span data-stu-id="b97d7-133">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b97d7-134">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="b97d7-134">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="b97d7-135">Zie ook</span><span class="sxs-lookup"><span data-stu-id="b97d7-135">See Also</span></span>

[<span data-ttu-id="b97d7-136">Configuratie-Element</span><span class="sxs-lookup"><span data-stu-id="b97d7-136">Configuration Element</span></span>](./configuration-element-format.md)

[<span data-ttu-id="b97d7-137">DisplayError-Element (Frmat)</span><span class="sxs-lookup"><span data-stu-id="b97d7-137">DisplayError Element (Frmat)</span></span>](./displayerror-element-format.md)

[<span data-ttu-id="b97d7-138">EnumerableExpansions-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="b97d7-138">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)

[<span data-ttu-id="b97d7-139">PropertyCountForTable (Format)</span><span class="sxs-lookup"><span data-stu-id="b97d7-139">PropertyCountForTable (Format)</span></span>](./propertycountfortable-element-format.md)

[<span data-ttu-id="b97d7-140">ShowError Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="b97d7-140">ShowError Element (Format)</span></span>](./showerror-element-format.md)

[<span data-ttu-id="b97d7-141">WrapTables-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="b97d7-141">WrapTables Element (Format)</span></span>](./wraptables-element-format.md)

[<span data-ttu-id="b97d7-142">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="b97d7-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
