---
title: Display error-element (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 5d46c2fbd48f592db5ba1b33eb6cead8dc1c4698
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774283"
---
# <a name="displayerror-element-format"></a><span data-ttu-id="d749f-102">Het element DisplayError (opmaak)</span><span class="sxs-lookup"><span data-stu-id="d749f-102">DisplayError Element (Format)</span></span>

<span data-ttu-id="d749f-103">Hiermee geeft u op dat de teken reeks #ERR wordt weer gegeven wanneer een fout optreedt bij het weer geven van een stukje gegevens.</span><span class="sxs-lookup"><span data-stu-id="d749f-103">Specifies that the string #ERR is displayed when an error occurs displaying a piece of data.</span></span>

<span data-ttu-id="d749f-104">Configuratie-element (indeling) DefaultSettings element (indeling) Display error element (indeling)</span><span class="sxs-lookup"><span data-stu-id="d749f-104">Configuration Element (Format) DefaultSettings Element (Format) DisplayError Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d749f-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="d749f-105">Syntax</span></span>

```xml
<DisplayError/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d749f-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="d749f-106">Attributes and Elements</span></span>

<span data-ttu-id="d749f-107">In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `DisplayError` element beschreven.</span><span class="sxs-lookup"><span data-stu-id="d749f-107">The following sections describe attributes, child elements, and the parent element of the `DisplayError` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d749f-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="d749f-108">Attributes</span></span>

<span data-ttu-id="d749f-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="d749f-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d749f-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="d749f-110">Child Elements</span></span>

<span data-ttu-id="d749f-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="d749f-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d749f-112">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="d749f-112">Parent Elements</span></span>

|<span data-ttu-id="d749f-113">Element</span><span class="sxs-lookup"><span data-stu-id="d749f-113">Element</span></span>|<span data-ttu-id="d749f-114">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="d749f-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d749f-115">Het element DefaultSettings (opmaak)</span><span class="sxs-lookup"><span data-stu-id="d749f-115">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="d749f-116">Hiermee definieert u algemene instellingen die van toepassing zijn op alle weer gaven van het opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="d749f-116">Defines common settings that apply to all the views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d749f-117">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="d749f-117">Remarks</span></span>

<span data-ttu-id="d749f-118">Wanneer er een fout optreedt tijdens het weer geven van een stukje gegevens, blijft de locatie van de gegevens standaard leeg.</span><span class="sxs-lookup"><span data-stu-id="d749f-118">By default, when an error occurs while trying to display a piece of data, the location of the data is left blank.</span></span> <span data-ttu-id="d749f-119">Als dit element is ingesteld op True, wordt de #ERR teken reeks weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="d749f-119">When this element is set to true, the #ERR string will be displayed.</span></span>

## <a name="see-also"></a><span data-ttu-id="d749f-120">Zie ook</span><span class="sxs-lookup"><span data-stu-id="d749f-120">See Also</span></span>

[<span data-ttu-id="d749f-121">Het element DefaultSettings (opmaak)</span><span class="sxs-lookup"><span data-stu-id="d749f-121">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)

[<span data-ttu-id="d749f-122">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="d749f-122">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
