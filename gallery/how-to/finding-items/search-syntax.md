---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: Galerie, powershell, cmdlet, psgallery
title: Galerie Zoeksyntaxis
ms.openlocfilehash: 4c0e357957ef970826ee90868db78ac07a14c804
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.contentlocale: nl-NL
ms.lasthandoff: 05/10/2018
---
# <a name="gallery-search-syntax"></a><span data-ttu-id="71678-103">Galerie Zoeksyntaxis</span><span class="sxs-lookup"><span data-stu-id="71678-103">Gallery Search Syntax</span></span>

<span data-ttu-id="71678-104">PowerShell Gallery biedt een tekst searchbox waar u woorden, zinnen en sleutelwoord expressies gebruiken kunt om de zoekresultaten te beperken.</span><span class="sxs-lookup"><span data-stu-id="71678-104">PowerShell Gallery offers a text searchbox where you can use words, phrases and keyword expressions to narrow down search results.</span></span>

## <a name="search-by-keywords"></a><span data-ttu-id="71678-105">Zoeken met trefwoorden</span><span class="sxs-lookup"><span data-stu-id="71678-105">Search by Keywords</span></span>

    dsc azure sql

<span data-ttu-id="71678-106">Zoekopdracht doen haar uiterste best om relevante documenten met alle 3 trefwoorden te zoeken, en overeenkomende documenten retourneren.</span><span class="sxs-lookup"><span data-stu-id="71678-106">Search will do its best effort to find relevant documents containing all 3 keywords, and return matching documents.</span></span>

## <a name="search-using-phrases-and-keywords"></a><span data-ttu-id="71678-107">Zoeken met zinnen en trefwoorden</span><span class="sxs-lookup"><span data-stu-id="71678-107">Search using Phrases and keywords</span></span>

    "azure sql" deployment

<span data-ttu-id="71678-108">Een wachtwoordzin invoeren tussen aanhalingstekens ("") Wijzig de zoekopdracht op zoek naar de specifieke zinsdeel in plaats van afzonderlijke trefwoorden.</span><span class="sxs-lookup"><span data-stu-id="71678-108">Entering a phrase between quotation marks ("") change the search to look for the particular phrase instead of separate keywords.</span></span>
<span data-ttu-id="71678-109">Documenten die overeenkomt met moet de exacte woordgroep 'azure sql', met inbegrip van variaties op hoofdlettergebruik bijvoorbeeld meestal bevatten 'Azure SQL', en ook meestal het woord 'implementatie' bevatten.</span><span class="sxs-lookup"><span data-stu-id="71678-109">Matching documents should usually contain the exact phrase "azure sql", including variations on capitalization e.g. "Azure SQL", and also usually contain the word 'deployment'.</span></span>

## <a name="filtering-on-fields"></a><span data-ttu-id="71678-110">Filteren op velden</span><span class="sxs-lookup"><span data-stu-id="71678-110">Filtering on fields</span></span>

<span data-ttu-id="71678-111">U kunt zoeken naar een specifiek item-ID (of 'Id' of 'id') of bepaalde andere velden door Mining zoektermen met de naam van het veld.</span><span class="sxs-lookup"><span data-stu-id="71678-111">You can search for a specific item ID (or 'Id' or 'id'), or certain other fields by prefixing search terms with the field name.</span></span>

<span data-ttu-id="71678-112">De doorzoekbare velden zijn momenteel 'Id', 'Version', 'Labels', 'Auteur', 'Eigenaar', 'Functies', 'Cmdlets', 'DscResources' en 'PowerShellVersion'.</span><span class="sxs-lookup"><span data-stu-id="71678-112">Currently the searchable fields are 'Id', 'Version', 'Tags', 'Author', 'Owner', 'Functions', 'Cmdlets', 'DscResources' and 'PowerShellVersion'.</span></span>

<span data-ttu-id="71678-113">[Wat is het verschil tussen ID en titel?</span><span class="sxs-lookup"><span data-stu-id="71678-113">[What's the difference between ID and Title?</span></span> <span data-ttu-id="71678-114">ID is de naam die u in de console gebruikt.</span><span class="sxs-lookup"><span data-stu-id="71678-114">ID is the name you use in the console.</span></span> <span data-ttu-id="71678-115">Titel is wat wordt weergegeven boven aan de pagina item in de zoekresultaten.]</span><span class="sxs-lookup"><span data-stu-id="71678-115">Title is what is shown at the top of the item page in search results.]</span></span>

## <a name="examples"></a><span data-ttu-id="71678-116">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="71678-116">Examples</span></span>

    ID:"PSReadline"
    id:"AzureRM.Profile"

<span data-ttu-id="71678-117">zoekt respectievelijk artikelen met 'PSReadline' of 'AzureRM.Profile' in het id-veld.</span><span class="sxs-lookup"><span data-stu-id="71678-117">finds items with "PSReadline" or "AzureRM.Profile" in their ID field respectively.</span></span>

    Id:"AzureRM.Profile"

<span data-ttu-id="71678-118">is een andere manier om items met 'AzureRM.Profile' niet vinden in het id-veld.</span><span class="sxs-lookup"><span data-stu-id="71678-118">is another way to find items with "AzureRM.Profile" in their ID field.</span></span>

<span data-ttu-id="71678-119">Het filter 'Id' is een subtekenreeks, dus als u zoekt naar het volgende:</span><span class="sxs-lookup"><span data-stu-id="71678-119">The 'Id' filter is a substring match, so if you search for the following:</span></span>

    Id:"azure"

<span data-ttu-id="71678-120">U krijgt resultaten zoals 'AzureRM.Profile' en 'Azure.Storage'.</span><span class="sxs-lookup"><span data-stu-id="71678-120">You'll get results like 'AzureRM.Profile' and 'Azure.Storage'.</span></span>

<span data-ttu-id="71678-121">U kunt ook zoeken naar meerdere trefwoorden in één veld.</span><span class="sxs-lookup"><span data-stu-id="71678-121">You can also search for multiple keywords in a single field.</span></span> <span data-ttu-id="71678-122">Of meng en velden overeenkomen.</span><span class="sxs-lookup"><span data-stu-id="71678-122">Or mix and match fields.</span></span>

    id:azure tags:intellisense
    id:azure id:storage

<span data-ttu-id="71678-123">En u kunt woordgroep zoekopdrachten uitvoeren:</span><span class="sxs-lookup"><span data-stu-id="71678-123">And you can perform phrase searches:</span></span>

    id:"azure.storage"


<span data-ttu-id="71678-124">Om te zoeken in alle items met DSC-tag.</span><span class="sxs-lookup"><span data-stu-id="71678-124">To search all items with DSC tag.</span></span>

    Tags:"DSC"

<span data-ttu-id="71678-125">Om te zoeken in alle items met de opgegeven functie.</span><span class="sxs-lookup"><span data-stu-id="71678-125">To search all items with the specified function.</span></span>

    Functions:"Update-AzureRM"

<span data-ttu-id="71678-126">Om te zoeken in alle items met de opgegeven cmdlet.</span><span class="sxs-lookup"><span data-stu-id="71678-126">To search all items with the specified cmdlet.</span></span>

    Cmdlets:"Get-AzureRmEnvironment"

<span data-ttu-id="71678-127">Om te zoeken in alle items met de opgegeven naam van de DSC-Resource.</span><span class="sxs-lookup"><span data-stu-id="71678-127">To search all items with the specified DSC Resource name.</span></span>

    DscResources:"xArchive"

<span data-ttu-id="71678-128">Alle items met de opgegeven PowerShellVersion zoeken</span><span class="sxs-lookup"><span data-stu-id="71678-128">To search all items with the specified PowerShellVersion</span></span>

    PowerShellVersion:"5.0"
    PowerShellVersion:"3.0"
    PowerShellVersion:"2.0"


<span data-ttu-id="71678-129">Ten slotte, als u een veld die wordt niet ondersteund, zoals 'opdrachten', gebruiken we net negeren, en zoeken van alle velden.</span><span class="sxs-lookup"><span data-stu-id="71678-129">Finally, if you use a field we don't support, such as 'commands', we'll just ignore it and search all the fields.</span></span> <span data-ttu-id="71678-130">Zodat de volgende query</span><span class="sxs-lookup"><span data-stu-id="71678-130">So the following query</span></span>

    commands:blobs storage

<span data-ttu-id="71678-131">Is geïnterpreteerd exact hetzelfde zijn als deze query:</span><span class="sxs-lookup"><span data-stu-id="71678-131">Is interpreted exactly the same as this query:</span></span>

    blobs storage