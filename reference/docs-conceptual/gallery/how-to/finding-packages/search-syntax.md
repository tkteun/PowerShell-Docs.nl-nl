---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galerie, Power shell, cmdlet, psgallery
title: Galerie Zoek syntaxis
ms.openlocfilehash: 9eaabc22090655076dabe177f04130738e081179
ms.sourcegitcommit: d757d64ea8c8af4d92596e8fbe15f2f40d48d3ac
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/22/2020
ms.locfileid: "90846997"
---
# <a name="gallery-search-syntax"></a><span data-ttu-id="8be39-103">Galerie Zoek syntaxis</span><span class="sxs-lookup"><span data-stu-id="8be39-103">Gallery Search Syntax</span></span>

<span data-ttu-id="8be39-104">U kunt de PowerShell Gallery doorzoeken met behulp [van de website van PowerShell Gallery](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="8be39-104">You can search the PowerShell Gallery using the [PowerShell Gallery's web site](https://www.powershellgallery.com/).</span></span> <span data-ttu-id="8be39-105">PowerShell Gallery website biedt een tekst SearchBox waar u woorden, zinsdelen en trefwoord expressies kunt gebruiken om de zoek resultaten te beperken.</span><span class="sxs-lookup"><span data-stu-id="8be39-105">PowerShell Gallery web site offers a text searchbox where you can use words, phrases and keyword expressions to narrow down search results.</span></span>

## <a name="search-by-keywords"></a><span data-ttu-id="8be39-106">Zoeken op tref woorden</span><span class="sxs-lookup"><span data-stu-id="8be39-106">Search by Keywords</span></span>

```Syntax
dsc azure sql
```

<span data-ttu-id="8be39-107">Zoek pogingen om relevante documenten te vinden met alle drie tref woorden en retour neren overeenkomende documenten.</span><span class="sxs-lookup"><span data-stu-id="8be39-107">Search attempts to find relevant documents containing all 3 keywords, and return matching documents.</span></span>

## <a name="search-using-phrases-and-keywords"></a><span data-ttu-id="8be39-108">Zoeken met behulp van zinsdelen en tref woorden</span><span class="sxs-lookup"><span data-stu-id="8be39-108">Search using Phrases and keywords</span></span>

```Syntax
"azure sql" deployment
```

<span data-ttu-id="8be39-109">Als u een woord groep tussen aanhalings tekens ("") invoert, wijzigt u de zoek opdracht om te zoeken naar de specifieke woord groep in plaats van afzonderlijke tref woorden.</span><span class="sxs-lookup"><span data-stu-id="8be39-109">Entering a phrase between quotation marks ("") change the search to look for the particular phrase instead of separate keywords.</span></span> <span data-ttu-id="8be39-110">Overeenkomende documenten moeten doorgaans de exacte woord groep ' Azure SQL ' bevatten, met inbegrip van variaties op kapitalisatie zoals ' Azure SQL ', en bevatten meestal het woord ' implementatie '.</span><span class="sxs-lookup"><span data-stu-id="8be39-110">Matching documents should usually contain the exact phrase "azure sql", including variations on capitalization e.g. "Azure SQL", and also usually contain the word 'deployment'.</span></span>

## <a name="filtering-on-fields"></a><span data-ttu-id="8be39-111">Velden filteren</span><span class="sxs-lookup"><span data-stu-id="8be39-111">Filtering on fields</span></span>

<span data-ttu-id="8be39-112">U kunt zoeken naar een specifieke pakket-ID (of ' id ' of ' id '), of bepaalde andere velden door voor voegsel zoek termen voor te stellen met de veld naam.</span><span class="sxs-lookup"><span data-stu-id="8be39-112">You can search for a specific package ID (or 'Id' or 'id'), or certain other fields by prefixing search terms with the field name.</span></span>

<span data-ttu-id="8be39-113">Momenteel zijn de Doorzoek bare velden ' id ', ' versie ', ' Tags ', ' Auteur ', ' eigenaar ', ' functions ', ' cmdlets ', ' DscResources ' en ' PowerShellVersion '.</span><span class="sxs-lookup"><span data-stu-id="8be39-113">Currently the searchable fields are 'Id', 'Version', 'Tags', 'Author', 'Owner', 'Functions', 'Cmdlets', 'DscResources' and 'PowerShellVersion'.</span></span>

- <span data-ttu-id="8be39-114">ID is de naam die u in de-console gebruikt.</span><span class="sxs-lookup"><span data-stu-id="8be39-114">ID is the name you use in the console.</span></span>
- <span data-ttu-id="8be39-115">Titel is wat wordt weer gegeven aan de bovenkant van de pakket pagina in de zoek resultaten.</span><span class="sxs-lookup"><span data-stu-id="8be39-115">Title is what is shown at the top of the package page in search results.</span></span>

## <a name="examples"></a><span data-ttu-id="8be39-116">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="8be39-116">Examples</span></span>

```Syntax
ID:PSReadline
```

<span data-ttu-id="8be39-117">Hiermee zoekt u pakketten met een ID die ' PSReadline ' bevat.</span><span class="sxs-lookup"><span data-stu-id="8be39-117">finds packages with an ID containing "PSReadline".</span></span>

```Syntax
Id:"AzureRM.Profile"
```

<span data-ttu-id="8be39-118">is een andere manier om pakketten te vinden met ' AzureRM. profile ' in hun ID-veld.</span><span class="sxs-lookup"><span data-stu-id="8be39-118">is another way to find packages with "AzureRM.Profile" in their ID field.</span></span>

<span data-ttu-id="8be39-119">Het filter ' id ' is een overeenkomende subtekenreeks, dus als u zoekt naar het volgende:</span><span class="sxs-lookup"><span data-stu-id="8be39-119">The 'Id' filter is a substring match, so if you search for the following:</span></span>

```Syntax
Id:"azure"
```

<span data-ttu-id="8be39-120">Dit biedt resultaten die AzureRM. profile en Azure. Storage bevatten.</span><span class="sxs-lookup"><span data-stu-id="8be39-120">This provides results that include AzureRM.Profile' and 'Azure.Storage'.</span></span>

<span data-ttu-id="8be39-121">U kunt ook zoeken naar meerdere tref woorden in één veld.</span><span class="sxs-lookup"><span data-stu-id="8be39-121">You can also search for multiple keywords in a single field.</span></span>

```Syntax
id:azure tags:intellisense
```

<span data-ttu-id="8be39-122">En u kunt Zoek opdrachten voor zinsdelen uitvoeren met dubbele aanhalings tekens:</span><span class="sxs-lookup"><span data-stu-id="8be39-122">And you can perform phrase searches using double quotes:</span></span>

```Syntax
id:"azure.storage"
```

<span data-ttu-id="8be39-123">Om te zoeken in alle pakketten met DSC-tag.</span><span class="sxs-lookup"><span data-stu-id="8be39-123">To search all packages with DSC tag.</span></span>

```Syntax
Tags:DSC
```

<span data-ttu-id="8be39-124">Om te zoeken in alle pakketten met de opgegeven functie.</span><span class="sxs-lookup"><span data-stu-id="8be39-124">To search all packages with the specified function.</span></span>

```Syntax
Functions:Get-TreeSize
```

<span data-ttu-id="8be39-125">Om alle pakketten met de opgegeven cmdlet te doorzoeken.</span><span class="sxs-lookup"><span data-stu-id="8be39-125">To search all packages with the specified cmdlet.</span></span>

```Syntax
Cmdlets:Get-AzureRmEnvironment
```

<span data-ttu-id="8be39-126">Om te zoeken in alle pakketten met de opgegeven naam van de DSC-resource.</span><span class="sxs-lookup"><span data-stu-id="8be39-126">To search all packages with the specified DSC Resource name.</span></span>

```Syntax
DscResources:xArchive
```

<span data-ttu-id="8be39-127">Zoeken naar alle pakketten met de opgegeven PowerShellVersion</span><span class="sxs-lookup"><span data-stu-id="8be39-127">To search all packages with the specified PowerShellVersion</span></span>

```Syntax
PowerShellVersion:2.0
```

<span data-ttu-id="8be39-128">Ten slotte, als u een veld gebruikt dat niet wordt ondersteund, zoals opdrachten, worden deze alleen genegeerd en worden alle velden doorzocht.</span><span class="sxs-lookup"><span data-stu-id="8be39-128">Finally, if you use a field we don't support, such as 'commands', we'll just ignore it and search all the fields.</span></span> <span data-ttu-id="8be39-129">De volgende query</span><span class="sxs-lookup"><span data-stu-id="8be39-129">So the following query</span></span>

```Syntax
commands:blobs storage
```

<span data-ttu-id="8be39-130">Wordt precies hetzelfde geïnterpreteerd als deze query:</span><span class="sxs-lookup"><span data-stu-id="8be39-130">Is interpreted exactly the same as this query:</span></span>

```Syntax
blobs storage
```
