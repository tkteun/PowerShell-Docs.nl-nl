---
ms.date: 09/13/2016
ms.topic: reference
title: Het element DisplayError (opmaak)
description: Het element DisplayError (opmaak)
ms.openlocfilehash: fb54df86a3558263687a8c417870495b7066f563
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92649930"
---
# <a name="displayerror-element-format"></a><span data-ttu-id="41995-103">Het element DisplayError (opmaak)</span><span class="sxs-lookup"><span data-stu-id="41995-103">DisplayError Element (Format)</span></span>

<span data-ttu-id="41995-104">Hiermee geeft u op dat de teken reeks #ERR wordt weer gegeven wanneer een fout optreedt bij het weer geven van een stukje gegevens.</span><span class="sxs-lookup"><span data-stu-id="41995-104">Specifies that the string #ERR is displayed when an error occurs displaying a piece of data.</span></span>

<span data-ttu-id="41995-105">Configuratie-element (indeling) DefaultSettings element (indeling) Display error element (indeling)</span><span class="sxs-lookup"><span data-stu-id="41995-105">Configuration Element (Format) DefaultSettings Element (Format) DisplayError Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="41995-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="41995-106">Syntax</span></span>

```xml
<DisplayError/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="41995-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="41995-107">Attributes and Elements</span></span>

<span data-ttu-id="41995-108">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `DisplayError` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="41995-108">The following sections describe attributes, child elements, and the parent element of the `DisplayError` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="41995-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="41995-109">Attributes</span></span>

<span data-ttu-id="41995-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="41995-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="41995-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="41995-111">Child Elements</span></span>

<span data-ttu-id="41995-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="41995-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="41995-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="41995-113">Parent Elements</span></span>

|<span data-ttu-id="41995-114">Element</span><span class="sxs-lookup"><span data-stu-id="41995-114">Element</span></span>|<span data-ttu-id="41995-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="41995-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="41995-116">Het element DefaultSettings (opmaak)</span><span class="sxs-lookup"><span data-stu-id="41995-116">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="41995-117">Hiermee definieert u algemene instellingen die van toepassing zijn op alle weer gaven van het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="41995-117">Defines common settings that apply to all the views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="41995-118">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="41995-118">Remarks</span></span>

<span data-ttu-id="41995-119">Wanneer er een fout optreedt tijdens het weer geven van een stukje gegevens, blijft de locatie van de gegevens standaard leeg.</span><span class="sxs-lookup"><span data-stu-id="41995-119">By default, when an error occurs while trying to display a piece of data, the location of the data is left blank.</span></span> <span data-ttu-id="41995-120">Als dit element is ingesteld op True, wordt de #ERR teken reeks weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="41995-120">When this element is set to true, the #ERR string will be displayed.</span></span>

## <a name="see-also"></a><span data-ttu-id="41995-121">Zie ook</span><span class="sxs-lookup"><span data-stu-id="41995-121">See Also</span></span>

[<span data-ttu-id="41995-122">Het element DefaultSettings (opmaak)</span><span class="sxs-lookup"><span data-stu-id="41995-122">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)

[<span data-ttu-id="41995-123">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="41995-123">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
