---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galerie, powershell, cmdlet, psgallery
title: Galerie Zoeksyntaxis
ms.openlocfilehash: 9aadb6771c85845cc3fa05cb56f0194b060d1c1b
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50004040"
---
# <a name="gallery-search-syntax"></a><span data-ttu-id="61137-103">Galerie Zoeksyntaxis</span><span class="sxs-lookup"><span data-stu-id="61137-103">Gallery Search Syntax</span></span>

<span data-ttu-id="61137-104">PowerShell-galerie biedt een tekst searchbox waar u woorden, zinnen en sleutelwoord expressies zoekresultaten verfijnen kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="61137-104">PowerShell Gallery offers a text searchbox where you can use words, phrases and keyword expressions to narrow down search results.</span></span>

## <a name="search-by-keywords"></a><span data-ttu-id="61137-105">Zoeken op trefwoorden</span><span class="sxs-lookup"><span data-stu-id="61137-105">Search by Keywords</span></span>

    dsc azure sql

<span data-ttu-id="61137-106">Zoeken wordt de aanbevolen inspanningen om te zoeken naar relevante documenten met alle 3 trefwoorden doen en overeenkomende documenten retourneren.</span><span class="sxs-lookup"><span data-stu-id="61137-106">Search will do its best effort to find relevant documents containing all 3 keywords, and return matching documents.</span></span>

## <a name="search-using-phrases-and-keywords"></a><span data-ttu-id="61137-107">Zoeken met behulp van zinnen en trefwoorden</span><span class="sxs-lookup"><span data-stu-id="61137-107">Search using Phrases and keywords</span></span>

    "azure sql" deployment

<span data-ttu-id="61137-108">Een zin invoeren tussen aanhalingstekens ("") Wijzig de zoekopdracht om te zoeken naar de specifieke woordgroep in plaats van afzonderlijke trefwoorden.</span><span class="sxs-lookup"><span data-stu-id="61137-108">Entering a phrase between quotation marks ("") change the search to look for the particular phrase instead of separate keywords.</span></span>
<span data-ttu-id="61137-109">Overeenkomende documenten, moet de exacte woordgroep 'azure sql', met inbegrip van variaties op hoofdlettergebruik bijvoorbeeld gewoonlijk bevatten 'Azure SQL', en ook meestal het woord 'implementatie' bevatten.</span><span class="sxs-lookup"><span data-stu-id="61137-109">Matching documents should usually contain the exact phrase "azure sql", including variations on capitalization e.g. "Azure SQL", and also usually contain the word 'deployment'.</span></span>

## <a name="filtering-on-fields"></a><span data-ttu-id="61137-110">Filteren op velden</span><span class="sxs-lookup"><span data-stu-id="61137-110">Filtering on fields</span></span>

<span data-ttu-id="61137-111">U kunt zoeken naar een specifieke pakket-ID (of 'Id' of 'id') of bepaalde andere velden door het voorvoegsel zoektermen met de veldnaam.</span><span class="sxs-lookup"><span data-stu-id="61137-111">You can search for a specific package ID (or 'Id' or 'id'), or certain other fields by prefixing search terms with the field name.</span></span>

<span data-ttu-id="61137-112">De doorzoekbare velden zijn momenteel 'Id', 'Version', 'Tags', 'Auteur', 'Eigenaar', 'Functies', 'Cmdlets', 'DscResources' en 'PowerShellVersion'.</span><span class="sxs-lookup"><span data-stu-id="61137-112">Currently the searchable fields are 'Id', 'Version', 'Tags', 'Author', 'Owner', 'Functions', 'Cmdlets', 'DscResources' and 'PowerShellVersion'.</span></span>

<span data-ttu-id="61137-113">[Wat is het verschil tussen ID en titel?</span><span class="sxs-lookup"><span data-stu-id="61137-113">[What's the difference between ID and Title?</span></span> <span data-ttu-id="61137-114">-ID is de naam die u in de console gebruikt.</span><span class="sxs-lookup"><span data-stu-id="61137-114">ID is the name you use in the console.</span></span> <span data-ttu-id="61137-115">De titel is wat wordt weergegeven aan de bovenkant van de pakketpagina in de lijst met zoekresultaten.]</span><span class="sxs-lookup"><span data-stu-id="61137-115">Title is what is shown at the top of the package page in search results.]</span></span>

## <a name="examples"></a><span data-ttu-id="61137-116">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="61137-116">Examples</span></span>

    ID:"PSReadline"
    id:"AzureRM.Profile"

<span data-ttu-id="61137-117">zoekt naar pakketten met 'PSReadline' of 'AzureRM.Profile' in het id-veld respectievelijk.</span><span class="sxs-lookup"><span data-stu-id="61137-117">finds packages with "PSReadline" or "AzureRM.Profile" in their ID field respectively.</span></span>

    Id:"AzureRM.Profile"

<span data-ttu-id="61137-118">is een andere manier om pakketten met 'AzureRM.Profile' niet vinden in het id-veld.</span><span class="sxs-lookup"><span data-stu-id="61137-118">is another way to find packages with "AzureRM.Profile" in their ID field.</span></span>

<span data-ttu-id="61137-119">Het filter 'Id' is een subtekenreeks, dus als u zoekt voor het volgende:</span><span class="sxs-lookup"><span data-stu-id="61137-119">The 'Id' filter is a substring match, so if you search for the following:</span></span>

    Id:"azure"

<span data-ttu-id="61137-120">U krijgt de resultaten, zoals 'AzureRM.Profile' en 'Azure.Storage'.</span><span class="sxs-lookup"><span data-stu-id="61137-120">You'll get results like 'AzureRM.Profile' and 'Azure.Storage'.</span></span>

<span data-ttu-id="61137-121">U kunt ook zoeken naar meerdere trefwoorden in één veld.</span><span class="sxs-lookup"><span data-stu-id="61137-121">You can also search for multiple keywords in a single field.</span></span> <span data-ttu-id="61137-122">Of Combineer en velden overeen laten komen.</span><span class="sxs-lookup"><span data-stu-id="61137-122">Or mix and match fields.</span></span>

    id:azure tags:intellisense
    id:azure id:storage

<span data-ttu-id="61137-123">En u kunt woordgroep zoekopdrachten uitvoeren:</span><span class="sxs-lookup"><span data-stu-id="61137-123">And you can perform phrase searches:</span></span>

    id:"azure.storage"


<span data-ttu-id="61137-124">Om te zoeken naar alle pakketten zoekt met DSC-tag.</span><span class="sxs-lookup"><span data-stu-id="61137-124">To search all packages with DSC tag.</span></span>

    Tags:"DSC"

<span data-ttu-id="61137-125">Om te zoeken naar alle pakketten zoekt met de opgegeven functie.</span><span class="sxs-lookup"><span data-stu-id="61137-125">To search all packages with the specified function.</span></span>

    Functions:"Update-AzureRM"

<span data-ttu-id="61137-126">Om te zoeken naar alle pakketten met de opgegeven cmdlet.</span><span class="sxs-lookup"><span data-stu-id="61137-126">To search all packages with the specified cmdlet.</span></span>

    Cmdlets:"Get-AzureRmEnvironment"

<span data-ttu-id="61137-127">Om te zoeken naar alle pakketten met de opgegeven naam van de DSC-Resource.</span><span class="sxs-lookup"><span data-stu-id="61137-127">To search all packages with the specified DSC Resource name.</span></span>

    DscResources:"xArchive"

<span data-ttu-id="61137-128">Om te zoeken naar alle pakketten zoekt met de opgegeven PowerShellVersion</span><span class="sxs-lookup"><span data-stu-id="61137-128">To search all packages with the specified PowerShellVersion</span></span>

    PowerShellVersion:"5.0"
    PowerShellVersion:"3.0"
    PowerShellVersion:"2.0"


<span data-ttu-id="61137-129">Ten slotte, als u een veld die wordt niet ondersteund, zoals 'opdrachten', gebruiken we net negeren en zoeken naar alle velden.</span><span class="sxs-lookup"><span data-stu-id="61137-129">Finally, if you use a field we don't support, such as 'commands', we'll just ignore it and search all the fields.</span></span> <span data-ttu-id="61137-130">De volgende query uit</span><span class="sxs-lookup"><span data-stu-id="61137-130">So the following query</span></span>

    commands:blobs storage

<span data-ttu-id="61137-131">Wordt geïnterpreteerd precies hetzelfde als deze query:</span><span class="sxs-lookup"><span data-stu-id="61137-131">Is interpreted exactly the same as this query:</span></span>

    blobs storage
