---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galerie, powershell, cmdlet, psgallery
title: Galerie Zoeksyntaxis
ms.openlocfilehash: aabcaa1f1b5b641ab5033c9ba2e358477c84a23b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684834"
---
# <a name="gallery-search-syntax"></a><span data-ttu-id="fcbee-103">Galerie Zoeksyntaxis</span><span class="sxs-lookup"><span data-stu-id="fcbee-103">Gallery Search Syntax</span></span>

<span data-ttu-id="fcbee-104">U kunt zoeken naar de PowerShell Gallery met behulp van de [van PowerShell Gallery website](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="fcbee-104">You can search the PowerShell Gallery using the [PowerShell Gallery's web site](https://www.powershellgallery.com/).</span></span>
<span data-ttu-id="fcbee-105">PowerShell Gallery-website biedt een tekst searchbox waar u woorden, zinnen en sleutelwoord expressies zoekresultaten verfijnen kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="fcbee-105">PowerShell Gallery web site offers a text searchbox where you can use words, phrases and keyword expressions to narrow down search results.</span></span>

## <a name="search-by-keywords"></a><span data-ttu-id="fcbee-106">Zoeken op trefwoorden</span><span class="sxs-lookup"><span data-stu-id="fcbee-106">Search by Keywords</span></span>

    dsc azure sql

<span data-ttu-id="fcbee-107">Search probeert te zoeken naar relevante documenten met alle 3 trefwoorden en overeenkomende documenten retourneren.</span><span class="sxs-lookup"><span data-stu-id="fcbee-107">Search attempts to find relevant documents containing all 3 keywords, and return matching documents.</span></span>

## <a name="search-using-phrases-and-keywords"></a><span data-ttu-id="fcbee-108">Zoeken met behulp van zinnen en trefwoorden</span><span class="sxs-lookup"><span data-stu-id="fcbee-108">Search using Phrases and keywords</span></span>

    "azure sql" deployment

<span data-ttu-id="fcbee-109">Een zin invoeren tussen aanhalingstekens ("") Wijzig de zoekopdracht om te zoeken naar de specifieke woordgroep in plaats van afzonderlijke trefwoorden.</span><span class="sxs-lookup"><span data-stu-id="fcbee-109">Entering a phrase between quotation marks ("") change the search to look for the particular phrase instead of separate keywords.</span></span>
<span data-ttu-id="fcbee-110">Overeenkomende documenten, moet de exacte woordgroep 'azure sql', met inbegrip van variaties op hoofdlettergebruik bijvoorbeeld gewoonlijk bevatten 'Azure SQL', en ook meestal het woord 'implementatie' bevatten.</span><span class="sxs-lookup"><span data-stu-id="fcbee-110">Matching documents should usually contain the exact phrase "azure sql", including variations on capitalization e.g. "Azure SQL", and also usually contain the word 'deployment'.</span></span>

## <a name="filtering-on-fields"></a><span data-ttu-id="fcbee-111">Filteren op velden</span><span class="sxs-lookup"><span data-stu-id="fcbee-111">Filtering on fields</span></span>

<span data-ttu-id="fcbee-112">U kunt zoeken naar een specifieke pakket-ID (of 'Id' of 'id') of bepaalde andere velden door het voorvoegsel zoektermen met de veldnaam.</span><span class="sxs-lookup"><span data-stu-id="fcbee-112">You can search for a specific package ID (or 'Id' or 'id'), or certain other fields by prefixing search terms with the field name.</span></span>

<span data-ttu-id="fcbee-113">De doorzoekbare velden zijn momenteel 'Id', 'Version', 'Tags', 'Auteur', 'Eigenaar', 'Functies', 'Cmdlets', 'DscResources' en 'PowerShellVersion'.</span><span class="sxs-lookup"><span data-stu-id="fcbee-113">Currently the searchable fields are 'Id', 'Version', 'Tags', 'Author', 'Owner', 'Functions', 'Cmdlets', 'DscResources' and 'PowerShellVersion'.</span></span>

<span data-ttu-id="fcbee-114">[Wat is het verschil tussen ID en titel?</span><span class="sxs-lookup"><span data-stu-id="fcbee-114">[What's the difference between ID and Title?</span></span> <span data-ttu-id="fcbee-115">-ID is de naam die u in de console gebruikt.</span><span class="sxs-lookup"><span data-stu-id="fcbee-115">ID is the name you use in the console.</span></span> <span data-ttu-id="fcbee-116">De titel is wat wordt weergegeven aan de bovenkant van de pakketpagina in de lijst met zoekresultaten.]</span><span class="sxs-lookup"><span data-stu-id="fcbee-116">Title is what is shown at the top of the package page in search results.]</span></span>

## <a name="examples"></a><span data-ttu-id="fcbee-117">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="fcbee-117">Examples</span></span>

    ID:PSReadline
    
<span data-ttu-id="fcbee-118">zoekt naar pakketten met een ID die met 'PSReadline'.</span><span class="sxs-lookup"><span data-stu-id="fcbee-118">finds packages with an ID containing "PSReadline".</span></span>

    Id:"AzureRM.Profile"

<span data-ttu-id="fcbee-119">is een andere manier om pakketten met 'AzureRM.Profile' niet vinden in het id-veld.</span><span class="sxs-lookup"><span data-stu-id="fcbee-119">is another way to find packages with "AzureRM.Profile" in their ID field.</span></span>

<span data-ttu-id="fcbee-120">Het filter 'Id' is een subtekenreeks, dus als u zoekt voor het volgende:</span><span class="sxs-lookup"><span data-stu-id="fcbee-120">The 'Id' filter is a substring match, so if you search for the following:</span></span>

    Id:"azure"

<span data-ttu-id="fcbee-121">Dit biedt AzureRM.Profile omvatten de resultaten ' en 'Azure.Storage'.</span><span class="sxs-lookup"><span data-stu-id="fcbee-121">This provides results that include AzureRM.Profile' and 'Azure.Storage'.</span></span>

<span data-ttu-id="fcbee-122">U kunt ook zoeken naar meerdere trefwoorden in één veld.</span><span class="sxs-lookup"><span data-stu-id="fcbee-122">You can also search for multiple keywords in a single field.</span></span> 

    id:azure tags:intellisense

<span data-ttu-id="fcbee-123">En u woordgroep zoeken met behulp van dubbele aanhalingstekens kunt uitvoeren:</span><span class="sxs-lookup"><span data-stu-id="fcbee-123">And you can perform phrase searches using double quotes:</span></span>

    id:"azure.storage"

<span data-ttu-id="fcbee-124">Om te zoeken naar alle pakketten zoekt met DSC-tag.</span><span class="sxs-lookup"><span data-stu-id="fcbee-124">To search all packages with DSC tag.</span></span>

    Tags:DSC

<span data-ttu-id="fcbee-125">Om te zoeken naar alle pakketten zoekt met de opgegeven functie.</span><span class="sxs-lookup"><span data-stu-id="fcbee-125">To search all packages with the specified function.</span></span>

    Functions:Get-TreeSize

<span data-ttu-id="fcbee-126">Om te zoeken naar alle pakketten met de opgegeven cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fcbee-126">To search all packages with the specified cmdlet.</span></span>

    Cmdlets:Get-AzureRmEnvironment

<span data-ttu-id="fcbee-127">Om te zoeken naar alle pakketten met de opgegeven naam van de DSC-Resource.</span><span class="sxs-lookup"><span data-stu-id="fcbee-127">To search all packages with the specified DSC Resource name.</span></span>

    DscResources:xArchive

<span data-ttu-id="fcbee-128">Om te zoeken naar alle pakketten zoekt met de opgegeven PowerShellVersion</span><span class="sxs-lookup"><span data-stu-id="fcbee-128">To search all packages with the specified PowerShellVersion</span></span>

    PowerShellVersion:2.0

<span data-ttu-id="fcbee-129">Ten slotte, als u een veld die wordt niet ondersteund, zoals 'opdrachten', gebruiken we net negeren en zoeken naar alle velden.</span><span class="sxs-lookup"><span data-stu-id="fcbee-129">Finally, if you use a field we don't support, such as 'commands', we'll just ignore it and search all the fields.</span></span> <span data-ttu-id="fcbee-130">De volgende query uit</span><span class="sxs-lookup"><span data-stu-id="fcbee-130">So the following query</span></span>

    commands:blobs storage

<span data-ttu-id="fcbee-131">Wordt geïnterpreteerd precies hetzelfde als deze query:</span><span class="sxs-lookup"><span data-stu-id="fcbee-131">Is interpreted exactly the same as this query:</span></span>

    blobs storage
