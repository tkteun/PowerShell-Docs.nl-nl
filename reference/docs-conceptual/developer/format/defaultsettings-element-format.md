---
ms.date: 09/13/2016
ms.topic: reference
title: Het element DefaultSettings (opmaak)
description: Het element DefaultSettings (opmaak)
ms.openlocfilehash: 1c2055b38a416fe2d75fa20c6c87e92d9eed4285
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92666719"
---
# <a name="defaultsettings-element-format"></a><span data-ttu-id="80ac3-103">Het element DefaultSettings (opmaak)</span><span class="sxs-lookup"><span data-stu-id="80ac3-103">DefaultSettings Element (Format)</span></span>

<span data-ttu-id="80ac3-104">Hiermee definieert u algemene instellingen die van toepassing zijn op alle weer gaven van het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="80ac3-104">Defines common settings that apply to all the views of the formatting file.</span></span> <span data-ttu-id="80ac3-105">Algemene instellingen zijn onder meer het weer geven van fouten, tekst terugloop in tabellen, definiëren hoe verzamelingen worden uitgevouwen en meer.</span><span class="sxs-lookup"><span data-stu-id="80ac3-105">Common settings include displaying errors, wrapping text in tables, defining how collections are expanded, and more.</span></span>

<span data-ttu-id="80ac3-106">Configuratie-element (indeling) DefaultSettings element (indeling)</span><span class="sxs-lookup"><span data-stu-id="80ac3-106">Configuration Element (Format) DefaultSettings Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="80ac3-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="80ac3-107">Syntax</span></span>

```xml
<DefaultSettings>
  <ShowError/>
  <DisplayError/>
 <PropertyCountForTable>NumberOfProperties</PropertyCountFortable>
  <WrapTables/>
  <EnumerableExpansions>...</EnumerableExpansions>
</DefaultSettings>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="80ac3-108">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="80ac3-108">Attributes and Elements</span></span>

<span data-ttu-id="80ac3-109">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `DefaultSettings` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="80ac3-109">The following sections describe attributes, child elements, and the parent element of the `DefaultSettings` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="80ac3-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="80ac3-110">Attributes</span></span>

<span data-ttu-id="80ac3-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="80ac3-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="80ac3-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="80ac3-112">Child Elements</span></span>

|<span data-ttu-id="80ac3-113">Element</span><span class="sxs-lookup"><span data-stu-id="80ac3-113">Element</span></span>|<span data-ttu-id="80ac3-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="80ac3-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="80ac3-115">Het element DisplayError (opmaak)</span><span class="sxs-lookup"><span data-stu-id="80ac3-115">DisplayError Element (Format)</span></span>](./displayerror-element-format.md)|<span data-ttu-id="80ac3-116">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="80ac3-116">Optional element.</span></span><br /><br /> <span data-ttu-id="80ac3-117">Hiermee geeft u op dat de teken reeks #ERR wordt weer gegeven als er een fout optreedt bij het weer geven van een stukje gegevens.</span><span class="sxs-lookup"><span data-stu-id="80ac3-117">Specifies that the string #ERR is displayed when an error occurs while displaying a piece of data.</span></span>|
|[<span data-ttu-id="80ac3-118">Het element EnumerableExpansions (opmaak)</span><span class="sxs-lookup"><span data-stu-id="80ac3-118">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)|<span data-ttu-id="80ac3-119">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="80ac3-119">Optional element.</span></span><br /><br /> <span data-ttu-id="80ac3-120">Definieert de verschillende manieren waarop .NET-objecten worden uitgevouwen wanneer ze in een weer gave worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="80ac3-120">Defines the different ways that .NET objects are expanded when they are displayed in a view.</span></span>|
|[<span data-ttu-id="80ac3-121">PropertyCountForTable (indeling)</span><span class="sxs-lookup"><span data-stu-id="80ac3-121">PropertyCountForTable (Format)</span></span>](./propertycountfortable-element-format.md)|<span data-ttu-id="80ac3-122">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="80ac3-122">Optional element.</span></span><br /><br /> <span data-ttu-id="80ac3-123">Hiermee geeft u het minimum aantal eigenschappen op dat een object moet hebben om het object weer te geven in een tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="80ac3-123">Specifies the minimum number of properties that an object must have to display the object in a table view.</span></span>|
|[<span data-ttu-id="80ac3-124">Het element ShowError (opmaak)</span><span class="sxs-lookup"><span data-stu-id="80ac3-124">ShowError Element (Format)</span></span>](./showerror-element-format.md)|<span data-ttu-id="80ac3-125">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="80ac3-125">Optional element.</span></span><br /><br /> <span data-ttu-id="80ac3-126">Hiermee geeft u op dat de volledige fout record wordt weer gegeven als er een fout optreedt bij het weer geven van een stukje gegevens.</span><span class="sxs-lookup"><span data-stu-id="80ac3-126">Specifies that the full error record is displayed when an error occurs while displaying a piece of data.</span></span>|
|[<span data-ttu-id="80ac3-127">Het element WrapTables (opmaak)</span><span class="sxs-lookup"><span data-stu-id="80ac3-127">WrapTables Element (Format)</span></span>](./wraptables-element-format.md)|<span data-ttu-id="80ac3-128">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="80ac3-128">Optional element.</span></span><br /><br /> <span data-ttu-id="80ac3-129">Hiermee geeft u op dat de gegevens in een tabel naar de volgende regel worden verplaatst als deze niet in de kolom breedte passen.</span><span class="sxs-lookup"><span data-stu-id="80ac3-129">Specifies that data in a table is moved to the next line if it does not fit into the width of the column.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="80ac3-130">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="80ac3-130">Parent Elements</span></span>

|<span data-ttu-id="80ac3-131">Element</span><span class="sxs-lookup"><span data-stu-id="80ac3-131">Element</span></span>|<span data-ttu-id="80ac3-132">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="80ac3-132">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="80ac3-133">Configuratie-element</span><span class="sxs-lookup"><span data-stu-id="80ac3-133">Configuration Element</span></span>](./configuration-element-format.md)|<span data-ttu-id="80ac3-134">Vertegenwoordigt het element op het hoogste niveau van een opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="80ac3-134">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="80ac3-135">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="80ac3-135">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="80ac3-136">Zie ook</span><span class="sxs-lookup"><span data-stu-id="80ac3-136">See Also</span></span>

[<span data-ttu-id="80ac3-137">Configuratie-element</span><span class="sxs-lookup"><span data-stu-id="80ac3-137">Configuration Element</span></span>](./configuration-element-format.md)

[<span data-ttu-id="80ac3-138">Het element DisplayError (opmaak)</span><span class="sxs-lookup"><span data-stu-id="80ac3-138">DisplayError Element (Format)</span></span>](./displayerror-element-format.md)

[<span data-ttu-id="80ac3-139">Het element EnumerableExpansions (opmaak)</span><span class="sxs-lookup"><span data-stu-id="80ac3-139">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)

[<span data-ttu-id="80ac3-140">PropertyCountForTable (indeling)</span><span class="sxs-lookup"><span data-stu-id="80ac3-140">PropertyCountForTable (Format)</span></span>](./propertycountfortable-element-format.md)

[<span data-ttu-id="80ac3-141">Het element ShowError (opmaak)</span><span class="sxs-lookup"><span data-stu-id="80ac3-141">ShowError Element (Format)</span></span>](./showerror-element-format.md)

[<span data-ttu-id="80ac3-142">Het element WrapTables (opmaak)</span><span class="sxs-lookup"><span data-stu-id="80ac3-142">WrapTables Element (Format)</span></span>](./wraptables-element-format.md)

[<span data-ttu-id="80ac3-143">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="80ac3-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
