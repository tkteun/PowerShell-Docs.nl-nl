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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72355130"
---
# <a name="defaultsettings-element-format"></a><span data-ttu-id="c7f07-102">Het element DefaultSettings (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c7f07-102">DefaultSettings Element (Format)</span></span>

<span data-ttu-id="c7f07-103">Hiermee definieert u algemene instellingen die van toepassing zijn op alle weer gaven van het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="c7f07-103">Defines common settings that apply to all the views of the formatting file.</span></span> <span data-ttu-id="c7f07-104">Algemene instellingen zijn onder meer het weer geven van fouten, tekst terugloop in tabellen, definiëren hoe verzamelingen worden uitgevouwen en meer.</span><span class="sxs-lookup"><span data-stu-id="c7f07-104">Common settings include displaying errors, wrapping text in tables, defining how collections are expanded, and more.</span></span>

<span data-ttu-id="c7f07-105">Configuratie-element (indeling) DefaultSettings element (indeling)</span><span class="sxs-lookup"><span data-stu-id="c7f07-105">Configuration Element (Format) DefaultSettings Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c7f07-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="c7f07-106">Syntax</span></span>

```xml
<DefaultSettings>
  <ShowError/>
  <DisplayError/>
 <PropertyCountForTable>NumberOfProperties</PropertyCountFortable>
  <WrapTables/>
  <EnumerableExpansions>...</EnumerableExpansions>
</DefaultSettings>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c7f07-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="c7f07-107">Attributes and Elements</span></span>

<span data-ttu-id="c7f07-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `DefaultSettings` beschreven.</span><span class="sxs-lookup"><span data-stu-id="c7f07-108">The following sections describe attributes, child elements, and the parent element of the `DefaultSettings` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c7f07-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="c7f07-109">Attributes</span></span>

<span data-ttu-id="c7f07-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="c7f07-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c7f07-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="c7f07-111">Child Elements</span></span>

|<span data-ttu-id="c7f07-112">Element</span><span class="sxs-lookup"><span data-stu-id="c7f07-112">Element</span></span>|<span data-ttu-id="c7f07-113">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="c7f07-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c7f07-114">Display error-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="c7f07-114">DisplayError Element (Format)</span></span>](./displayerror-element-format.md)|<span data-ttu-id="c7f07-115">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="c7f07-115">Optional element.</span></span><br /><br /> <span data-ttu-id="c7f07-116">Hiermee geeft u op dat de teken reeks #ERR wordt weer gegeven als er een fout optreedt bij het weer geven van een stukje gegevens.</span><span class="sxs-lookup"><span data-stu-id="c7f07-116">Specifies that the string #ERR is displayed when an error occurs while displaying a piece of data.</span></span>|
|[<span data-ttu-id="c7f07-117">EnumerableExpansions-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="c7f07-117">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)|<span data-ttu-id="c7f07-118">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="c7f07-118">Optional element.</span></span><br /><br /> <span data-ttu-id="c7f07-119">Definieert de verschillende manieren waarop .NET-objecten worden uitgevouwen wanneer ze in een weer gave worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c7f07-119">Defines the different ways that .NET objects are expanded when they are displayed in a view.</span></span>|
|[<span data-ttu-id="c7f07-120">PropertyCountForTable (indeling)</span><span class="sxs-lookup"><span data-stu-id="c7f07-120">PropertyCountForTable (Format)</span></span>](./propertycountfortable-element-format.md)|<span data-ttu-id="c7f07-121">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="c7f07-121">Optional element.</span></span><br /><br /> <span data-ttu-id="c7f07-122">Hiermee geeft u het minimum aantal eigenschappen op dat een object moet hebben om het object weer te geven in een tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="c7f07-122">Specifies the minimum number of properties that an object must have to display the object in a table view.</span></span>|
|[<span data-ttu-id="c7f07-123">Show Error-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="c7f07-123">ShowError Element (Format)</span></span>](./showerror-element-format.md)|<span data-ttu-id="c7f07-124">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="c7f07-124">Optional element.</span></span><br /><br /> <span data-ttu-id="c7f07-125">Hiermee geeft u op dat de volledige fout record wordt weer gegeven als er een fout optreedt bij het weer geven van een stukje gegevens.</span><span class="sxs-lookup"><span data-stu-id="c7f07-125">Specifies that the full error record is displayed when an error occurs while displaying a piece of data.</span></span>|
|[<span data-ttu-id="c7f07-126">WrapTables-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="c7f07-126">WrapTables Element (Format)</span></span>](./wraptables-element-format.md)|<span data-ttu-id="c7f07-127">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="c7f07-127">Optional element.</span></span><br /><br /> <span data-ttu-id="c7f07-128">Hiermee geeft u op dat de gegevens in een tabel naar de volgende regel worden verplaatst als deze niet in de kolom breedte passen.</span><span class="sxs-lookup"><span data-stu-id="c7f07-128">Specifies that data in a table is moved to the next line if it does not fit into the width of the column.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c7f07-129">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="c7f07-129">Parent Elements</span></span>

|<span data-ttu-id="c7f07-130">Element</span><span class="sxs-lookup"><span data-stu-id="c7f07-130">Element</span></span>|<span data-ttu-id="c7f07-131">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="c7f07-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c7f07-132">Configuratie-element</span><span class="sxs-lookup"><span data-stu-id="c7f07-132">Configuration Element</span></span>](./configuration-element-format.md)|<span data-ttu-id="c7f07-133">Vertegenwoordigt het element op het hoogste niveau van een opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="c7f07-133">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c7f07-134">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="c7f07-134">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="c7f07-135">Zie ook</span><span class="sxs-lookup"><span data-stu-id="c7f07-135">See Also</span></span>

[<span data-ttu-id="c7f07-136">Configuratie-element</span><span class="sxs-lookup"><span data-stu-id="c7f07-136">Configuration Element</span></span>](./configuration-element-format.md)

[<span data-ttu-id="c7f07-137">Display error-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="c7f07-137">DisplayError Element (Format)</span></span>](./displayerror-element-format.md)

[<span data-ttu-id="c7f07-138">EnumerableExpansions-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="c7f07-138">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)

[<span data-ttu-id="c7f07-139">PropertyCountForTable (indeling)</span><span class="sxs-lookup"><span data-stu-id="c7f07-139">PropertyCountForTable (Format)</span></span>](./propertycountfortable-element-format.md)

[<span data-ttu-id="c7f07-140">Show Error-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="c7f07-140">ShowError Element (Format)</span></span>](./showerror-element-format.md)

[<span data-ttu-id="c7f07-141">WrapTables-element (indeling)</span><span class="sxs-lookup"><span data-stu-id="c7f07-141">WrapTables Element (Format)</span></span>](./wraptables-element-format.md)

[<span data-ttu-id="c7f07-142">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="c7f07-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
