---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,installeren
title: Catalogus-cmdlets
ms.openlocfilehash: ec5fc866fe27a894b23b93d3ea46ad9c0cba288e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55687305"
---
# <a name="catalog-cmdlets"></a><span data-ttu-id="e52c4-103">Catalogus-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="e52c4-103">Catalog Cmdlets</span></span>

<span data-ttu-id="e52c4-104">Hebben we twee nieuwe cmdlets in toegevoegd [Microsoft.Powershell.Secuity](https://technet.microsoft.com/library/hh847877.aspx) module te genereren en bestanden van windows-catalogus te valideren.</span><span class="sxs-lookup"><span data-stu-id="e52c4-104">We have added two new cmdlets in [Microsoft.Powershell.Secuity](https://technet.microsoft.com/library/hh847877.aspx) module to generate and validate windows catalog files.</span></span>

## <a name="new-filecatalog"></a><span data-ttu-id="e52c4-105">Nieuwe FileCatalog</span><span class="sxs-lookup"><span data-stu-id="e52c4-105">New-FileCatalog</span></span>
--------------------------------

<span data-ttu-id="e52c4-106">`New-FileCatalog` Hiermee maakt u een windows-catalogusbestand voor set van bestanden en mappen.</span><span class="sxs-lookup"><span data-stu-id="e52c4-106">`New-FileCatalog` creates a windows catalog file for set of folders and files.</span></span> <span data-ttu-id="e52c4-107">Een catalogusbestand bevat-hashes voor alle bestanden in de opgegeven paden.</span><span class="sxs-lookup"><span data-stu-id="e52c4-107">A catalog file contains hashes for all files in specified paths.</span></span> <span data-ttu-id="e52c4-108">Gebruikers kunnen de set van mappen, samen met de catalogusbestand met deze mappen overeenkomt distribueren.</span><span class="sxs-lookup"><span data-stu-id="e52c4-108">Users can distribute the set of folders along with corresponding the catalog file that represents those folders.</span></span> <span data-ttu-id="e52c4-109">Een catalogusbestand kan worden gebruikt door de ontvanger van inhoud te valideren of eventuele wijzigingen zijn aangebracht in de mappen nadat de catalogus is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="e52c4-109">A catalog file can be used by the recipient of content to validate whether any changes were made to the folders after the catalog was created.</span></span>

```powershell
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
<span data-ttu-id="e52c4-110">We ondersteuning voor het maken van het catalogusversie 1 en 2.</span><span class="sxs-lookup"><span data-stu-id="e52c4-110">We support creating catalog version 1 and 2.</span></span> <span data-ttu-id="e52c4-111">Versie 1 maakt gebruik van SHA1-hash-algoritme om bestands-hashes en versie 2 gebruikt SHA256 te maken.</span><span class="sxs-lookup"><span data-stu-id="e52c4-111">Version 1 uses SHA1 hashing algorithm to create file hashes and version 2 uses SHA256.</span></span> <span data-ttu-id="e52c4-112">Catalogusversie 2 wordt niet ondersteund op *Windows Server 2008 R2* en *Windows 7*.</span><span class="sxs-lookup"><span data-stu-id="e52c4-112">Catalog version 2 is not supported on *Windows Server 2008 R2* and *Windows 7*.</span></span> <span data-ttu-id="e52c4-113">Het verdient aanbeveling catalogusversie 2 gebruiken als platforms *Windows 8*, *Windows Server 2012* en hoger.</span><span class="sxs-lookup"><span data-stu-id="e52c4-113">It is recommended to use catalog version 2 if using platforms *Windows 8*, *Windows Server 2012* and above.</span></span>

<span data-ttu-id="e52c4-114">Geef de CatalogFilePath en het pad variabelen zodat deze overeenkomt met de locatie van de module-manifest voor het gebruik van deze opdracht op een bestaande module.</span><span class="sxs-lookup"><span data-stu-id="e52c4-114">To use this command on an existing module, specify the CatalogFilePath and Path variables to match the location of the module manifest.</span></span> <span data-ttu-id="e52c4-115">In het onderstaande voorbeeld is de module-manifest in C:\Program Files\Windows PowerShell\Modules\Pester.</span><span class="sxs-lookup"><span data-stu-id="e52c4-115">In the example below, the module manifest is in C:\Program Files\Windows PowerShell\Modules\Pester.</span></span>

![](../images/NewFileCatalog.jpg)

<span data-ttu-id="e52c4-116">Hiermee maakt u het catalogusbestand.</span><span class="sxs-lookup"><span data-stu-id="e52c4-116">This creates the catalog file.</span></span>

![](../images/CatalogFile1.jpg)

![](../images/CatalogFile2.jpg)

<span data-ttu-id="e52c4-117">Om te controleren of de integriteit van een catalogusbestand (Pester.cat in bovenstaande voorbeeld) moet het worden ondertekend met behulp van de [Set AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e52c4-117">To verify the integrity of a catalog file (Pester.cat in above exmaple) it should be signed using the [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) cmdlet.</span></span>


## <a name="test-filecatalog"></a><span data-ttu-id="e52c4-118">Test-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="e52c4-118">Test-FileCatalog</span></span>
--------------------------------

<span data-ttu-id="e52c4-119">`Test-FileCatalog` Hiermee valideert u de catalogus voor een set van mappen.</span><span class="sxs-lookup"><span data-stu-id="e52c4-119">`Test-FileCatalog` validates the catalog representing a set of folders.</span></span>

```powershell
Test-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-Detailed] [-FilesToSkip <string[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

![](../images/TestFileCatalog.jpg)

<span data-ttu-id="e52c4-120">Deze cmdlet vergelijkt de hashes van alle bestanden en hun relatieve paden gevonden in het catalogusbestand met resources op schijf opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="e52c4-120">This cmdlet compares the hashes of all files and their relative paths found in the catalog file with ones saved to disk.</span></span> <span data-ttu-id="e52c4-121">Als er overeenkomende bestands-hashes en paden gedetecteerd wordt de status van `ValidationFailed`.</span><span class="sxs-lookup"><span data-stu-id="e52c4-121">If it detects any mismatch between file hashes and paths it returns a status of `ValidationFailed`.</span></span>
<span data-ttu-id="e52c4-122">Gebruikers kunnen ophalen van alle deze informatie met behulp van de `Detailed` overschakelen.</span><span class="sxs-lookup"><span data-stu-id="e52c4-122">Users can retrieve all this information using the `Detailed` switch.</span></span> <span data-ttu-id="e52c4-123">De status van de ondertekening van de catalogus wordt weergegeven als de `Signature` veld, die hetzelfde is als het aanroepen de [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx) cmdlet uit op de catalog-bestand.</span><span class="sxs-lookup"><span data-stu-id="e52c4-123">The signing status of the catalog is displayed as the `Signature` field, which is same as calling the [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx) cmdlet on the catalog file.</span></span>
<span data-ttu-id="e52c4-124">Gebruikers kunnen ook een bestand tijdens de validatie overslaan met behulp van de `FilesToSkip` parameter.</span><span class="sxs-lookup"><span data-stu-id="e52c4-124">Users can also skip any file during validation by using the `FilesToSkip` parameter.</span></span>
