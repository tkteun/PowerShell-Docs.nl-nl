---
title: DefaultSettings-element (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 7da7948fc0814e38a8f3910596e223470ec27d75
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787730"
---
# <a name="defaultsettings-element-format"></a><span data-ttu-id="38487-102">Het element DefaultSettings (opmaak)</span><span class="sxs-lookup"><span data-stu-id="38487-102">DefaultSettings Element (Format)</span></span>

<span data-ttu-id="38487-103">Hiermee definieert u algemene instellingen die van toepassing zijn op alle weer gaven van het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="38487-103">Defines common settings that apply to all the views of the formatting file.</span></span> <span data-ttu-id="38487-104">Algemene instellingen zijn onder meer het weer geven van fouten, tekst terugloop in tabellen, definiëren hoe verzamelingen worden uitgevouwen en meer.</span><span class="sxs-lookup"><span data-stu-id="38487-104">Common settings include displaying errors, wrapping text in tables, defining how collections are expanded, and more.</span></span>

<span data-ttu-id="38487-105">Configuratie-element (indeling) DefaultSettings element (indeling)</span><span class="sxs-lookup"><span data-stu-id="38487-105">Configuration Element (Format) DefaultSettings Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="38487-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="38487-106">Syntax</span></span>

```xml
<DefaultSettings>
  <ShowError/>
  <DisplayError/>
 <PropertyCountForTable>NumberOfProperties</PropertyCountFortable>
  <WrapTables/>
  <EnumerableExpansions>...</EnumerableExpansions>
</DefaultSettings>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="38487-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="38487-107">Attributes and Elements</span></span>

<span data-ttu-id="38487-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `DefaultSettings` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="38487-108">The following sections describe attributes, child elements, and the parent element of the `DefaultSettings` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="38487-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="38487-109">Attributes</span></span>

<span data-ttu-id="38487-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="38487-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="38487-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="38487-111">Child Elements</span></span>

|<span data-ttu-id="38487-112">Element</span><span class="sxs-lookup"><span data-stu-id="38487-112">Element</span></span>|<span data-ttu-id="38487-113">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="38487-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="38487-114">Het element DisplayError (opmaak)</span><span class="sxs-lookup"><span data-stu-id="38487-114">DisplayError Element (Format)</span></span>](./displayerror-element-format.md)|<span data-ttu-id="38487-115">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="38487-115">Optional element.</span></span><br /><br /> <span data-ttu-id="38487-116">Hiermee geeft u op dat de teken reeks #ERR wordt weer gegeven als er een fout optreedt bij het weer geven van een stukje gegevens.</span><span class="sxs-lookup"><span data-stu-id="38487-116">Specifies that the string #ERR is displayed when an error occurs while displaying a piece of data.</span></span>|
|[<span data-ttu-id="38487-117">Het element EnumerableExpansions (opmaak)</span><span class="sxs-lookup"><span data-stu-id="38487-117">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)|<span data-ttu-id="38487-118">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="38487-118">Optional element.</span></span><br /><br /> <span data-ttu-id="38487-119">Definieert de verschillende manieren waarop .NET-objecten worden uitgevouwen wanneer ze in een weer gave worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="38487-119">Defines the different ways that .NET objects are expanded when they are displayed in a view.</span></span>|
|[<span data-ttu-id="38487-120">PropertyCountForTable (indeling)</span><span class="sxs-lookup"><span data-stu-id="38487-120">PropertyCountForTable (Format)</span></span>](./propertycountfortable-element-format.md)|<span data-ttu-id="38487-121">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="38487-121">Optional element.</span></span><br /><br /> <span data-ttu-id="38487-122">Hiermee geeft u het minimum aantal eigenschappen op dat een object moet hebben om het object weer te geven in een tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="38487-122">Specifies the minimum number of properties that an object must have to display the object in a table view.</span></span>|
|[<span data-ttu-id="38487-123">Het element ShowError (opmaak)</span><span class="sxs-lookup"><span data-stu-id="38487-123">ShowError Element (Format)</span></span>](./showerror-element-format.md)|<span data-ttu-id="38487-124">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="38487-124">Optional element.</span></span><br /><br /> <span data-ttu-id="38487-125">Hiermee geeft u op dat de volledige fout record wordt weer gegeven als er een fout optreedt bij het weer geven van een stukje gegevens.</span><span class="sxs-lookup"><span data-stu-id="38487-125">Specifies that the full error record is displayed when an error occurs while displaying a piece of data.</span></span>|
|[<span data-ttu-id="38487-126">Het element WrapTables (opmaak)</span><span class="sxs-lookup"><span data-stu-id="38487-126">WrapTables Element (Format)</span></span>](./wraptables-element-format.md)|<span data-ttu-id="38487-127">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="38487-127">Optional element.</span></span><br /><br /> <span data-ttu-id="38487-128">Hiermee geeft u op dat de gegevens in een tabel naar de volgende regel worden verplaatst als deze niet in de kolom breedte passen.</span><span class="sxs-lookup"><span data-stu-id="38487-128">Specifies that data in a table is moved to the next line if it does not fit into the width of the column.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="38487-129">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="38487-129">Parent Elements</span></span>

|<span data-ttu-id="38487-130">Element</span><span class="sxs-lookup"><span data-stu-id="38487-130">Element</span></span>|<span data-ttu-id="38487-131">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="38487-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="38487-132">Configuratie-element</span><span class="sxs-lookup"><span data-stu-id="38487-132">Configuration Element</span></span>](./configuration-element-format.md)|<span data-ttu-id="38487-133">Vertegenwoordigt het element op het hoogste niveau van een opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="38487-133">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="38487-134">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="38487-134">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="38487-135">Zie ook</span><span class="sxs-lookup"><span data-stu-id="38487-135">See Also</span></span>

[<span data-ttu-id="38487-136">Configuratie-element</span><span class="sxs-lookup"><span data-stu-id="38487-136">Configuration Element</span></span>](./configuration-element-format.md)

[<span data-ttu-id="38487-137">Het element DisplayError (opmaak)</span><span class="sxs-lookup"><span data-stu-id="38487-137">DisplayError Element (Format)</span></span>](./displayerror-element-format.md)

[<span data-ttu-id="38487-138">Het element EnumerableExpansions (opmaak)</span><span class="sxs-lookup"><span data-stu-id="38487-138">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)

[<span data-ttu-id="38487-139">PropertyCountForTable (indeling)</span><span class="sxs-lookup"><span data-stu-id="38487-139">PropertyCountForTable (Format)</span></span>](./propertycountfortable-element-format.md)

[<span data-ttu-id="38487-140">Het element ShowError (opmaak)</span><span class="sxs-lookup"><span data-stu-id="38487-140">ShowError Element (Format)</span></span>](./showerror-element-format.md)

[<span data-ttu-id="38487-141">Het element WrapTables (opmaak)</span><span class="sxs-lookup"><span data-stu-id="38487-141">WrapTables Element (Format)</span></span>](./wraptables-element-format.md)

[<span data-ttu-id="38487-142">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="38487-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
