---
title: DefaultSettings-element (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 41c56499-ee20-4821-830a-478fdcc33f83
caps.latest.revision: 11
ms.openlocfilehash: bc95c62222eb2806f92499257a397c2e4ec5dbab
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355130"
---
# <a name="defaultsettings-element-format"></a><span data-ttu-id="56ae1-102">Het element DefaultSettings (opmaak)</span><span class="sxs-lookup"><span data-stu-id="56ae1-102">DefaultSettings Element (Format)</span></span>

<span data-ttu-id="56ae1-103">Hiermee definieert u algemene instellingen die van toepassing zijn op alle weer gaven van het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="56ae1-103">Defines common settings that apply to all the views of the formatting file.</span></span> <span data-ttu-id="56ae1-104">Algemene instellingen zijn onder meer het weer geven van fouten, tekst terugloop in tabellen, definiëren hoe verzamelingen worden uitgevouwen en meer.</span><span class="sxs-lookup"><span data-stu-id="56ae1-104">Common settings include displaying errors, wrapping text in tables, defining how collections are expanded, and more.</span></span>

<span data-ttu-id="56ae1-105">Configuratie-element (indeling) DefaultSettings element (indeling)</span><span class="sxs-lookup"><span data-stu-id="56ae1-105">Configuration Element (Format) DefaultSettings Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="56ae1-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="56ae1-106">Syntax</span></span>

```xml
<DefaultSettings>
  <ShowError/>
  <DisplayError/>
 <PropertyCountForTable>NumberOfProperties</PropertyCountFortable>
  <WrapTables/>
  <EnumerableExpansions>...</EnumerableExpansions>
</DefaultSettings>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="56ae1-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="56ae1-107">Attributes and Elements</span></span>

<span data-ttu-id="56ae1-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `DefaultSettings` beschreven.</span><span class="sxs-lookup"><span data-stu-id="56ae1-108">The following sections describe attributes, child elements, and the parent element of the `DefaultSettings` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="56ae1-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="56ae1-109">Attributes</span></span>

<span data-ttu-id="56ae1-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="56ae1-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="56ae1-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="56ae1-111">Child Elements</span></span>

|<span data-ttu-id="56ae1-112">Element</span><span class="sxs-lookup"><span data-stu-id="56ae1-112">Element</span></span>|<span data-ttu-id="56ae1-113">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="56ae1-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="56ae1-114">Display error-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="56ae1-114">DisplayError Element (Format)</span></span>](./displayerror-element-format.md)|<span data-ttu-id="56ae1-115">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="56ae1-115">Optional element.</span></span><br /><br /> <span data-ttu-id="56ae1-116">Hiermee geeft u op dat de teken reeks #ERR wordt weer gegeven als er een fout optreedt bij het weer geven van een stukje gegevens.</span><span class="sxs-lookup"><span data-stu-id="56ae1-116">Specifies that the string #ERR is displayed when an error occurs while displaying a piece of data.</span></span>|
|[<span data-ttu-id="56ae1-117">EnumerableExpansions-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="56ae1-117">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)|<span data-ttu-id="56ae1-118">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="56ae1-118">Optional element.</span></span><br /><br /> <span data-ttu-id="56ae1-119">Definieert de verschillende manieren waarop .NET-objecten worden uitgevouwen wanneer ze in een weer gave worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="56ae1-119">Defines the different ways that .NET objects are expanded when they are displayed in a view.</span></span>|
|[<span data-ttu-id="56ae1-120">PropertyCountForTable (indeling)</span><span class="sxs-lookup"><span data-stu-id="56ae1-120">PropertyCountForTable (Format)</span></span>](./propertycountfortable-element-format.md)|<span data-ttu-id="56ae1-121">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="56ae1-121">Optional element.</span></span><br /><br /> <span data-ttu-id="56ae1-122">Hiermee geeft u het minimum aantal eigenschappen op dat een object moet hebben om het object weer te geven in een tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="56ae1-122">Specifies the minimum number of properties that an object must have to display the object in a table view.</span></span>|
|[<span data-ttu-id="56ae1-123">Show Error-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="56ae1-123">ShowError Element (Format)</span></span>](./showerror-element-format.md)|<span data-ttu-id="56ae1-124">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="56ae1-124">Optional element.</span></span><br /><br /> <span data-ttu-id="56ae1-125">Hiermee geeft u op dat de volledige fout record wordt weer gegeven als er een fout optreedt bij het weer geven van een stukje gegevens.</span><span class="sxs-lookup"><span data-stu-id="56ae1-125">Specifies that the full error record is displayed when an error occurs while displaying a piece of data.</span></span>|
|[<span data-ttu-id="56ae1-126">WrapTables-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="56ae1-126">WrapTables Element (Format)</span></span>](./wraptables-element-format.md)|<span data-ttu-id="56ae1-127">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="56ae1-127">Optional element.</span></span><br /><br /> <span data-ttu-id="56ae1-128">Hiermee geeft u op dat de gegevens in een tabel naar de volgende regel worden verplaatst als deze niet in de kolom breedte passen.</span><span class="sxs-lookup"><span data-stu-id="56ae1-128">Specifies that data in a table is moved to the next line if it does not fit into the width of the column.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="56ae1-129">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="56ae1-129">Parent Elements</span></span>

|<span data-ttu-id="56ae1-130">Element</span><span class="sxs-lookup"><span data-stu-id="56ae1-130">Element</span></span>|<span data-ttu-id="56ae1-131">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="56ae1-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="56ae1-132">Configuratie-element</span><span class="sxs-lookup"><span data-stu-id="56ae1-132">Configuration Element</span></span>](./configuration-element-format.md)|<span data-ttu-id="56ae1-133">Vertegenwoordigt het element op het hoogste niveau van een opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="56ae1-133">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="56ae1-134">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="56ae1-134">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="56ae1-135">Zie ook</span><span class="sxs-lookup"><span data-stu-id="56ae1-135">See Also</span></span>

[<span data-ttu-id="56ae1-136">Configuratie-element</span><span class="sxs-lookup"><span data-stu-id="56ae1-136">Configuration Element</span></span>](./configuration-element-format.md)

[<span data-ttu-id="56ae1-137">Display error-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="56ae1-137">DisplayError Element (Format)</span></span>](./displayerror-element-format.md)

[<span data-ttu-id="56ae1-138">EnumerableExpansions-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="56ae1-138">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)

[<span data-ttu-id="56ae1-139">PropertyCountForTable (indeling)</span><span class="sxs-lookup"><span data-stu-id="56ae1-139">PropertyCountForTable (Format)</span></span>](./propertycountfortable-element-format.md)

[<span data-ttu-id="56ae1-140">Show Error-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="56ae1-140">ShowError Element (Format)</span></span>](./showerror-element-format.md)

[<span data-ttu-id="56ae1-141">WrapTables-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="56ae1-141">WrapTables Element (Format)</span></span>](./wraptables-element-format.md)

[<span data-ttu-id="56ae1-142">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="56ae1-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
