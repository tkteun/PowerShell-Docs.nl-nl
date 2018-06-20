---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,installeren
title: Catalogus-cmdlets
ms.openlocfilehash: 7eaca09667af0eb5d719f23e987bb112e8514978
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189064"
---
# <a name="catalog-cmdlets"></a><span data-ttu-id="99c98-103">Catalogus-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="99c98-103">Catalog Cmdlets</span></span>

<span data-ttu-id="99c98-104">We hebben twee nieuwe cmdlets in toegevoegd [Microsoft.Powershell.Secuity](https://technet.microsoft.com/en-us/library/hh847877.aspx) module die u wilt genereren en bestanden voor windows-catalogus te valideren.</span><span class="sxs-lookup"><span data-stu-id="99c98-104">We have added two new cmdlets in [Microsoft.Powershell.Secuity](https://technet.microsoft.com/en-us/library/hh847877.aspx) module to generate and validate windows catalog files.</span></span>

## <a name="new-filecatalog"></a><span data-ttu-id="99c98-105">Nieuwe FileCatalog</span><span class="sxs-lookup"><span data-stu-id="99c98-105">New-FileCatalog</span></span>
--------------------------------

<span data-ttu-id="99c98-106">`New-FileCatalog` maakt een windows-catalogusbestand voor mappen en bestanden.</span><span class="sxs-lookup"><span data-stu-id="99c98-106">`New-FileCatalog` creates a windows catalog file for set of folders and files.</span></span> <span data-ttu-id="99c98-107">Een catalogusbestand bevat hashes voor alle bestanden in de opgegeven paden.</span><span class="sxs-lookup"><span data-stu-id="99c98-107">A catalog file contains hashes for all files in specified paths.</span></span> <span data-ttu-id="99c98-108">De set mappen samen met het catalogusbestand die deze mappen vertegenwoordigt overeenkomt, kunnen gebruikers distribueren.</span><span class="sxs-lookup"><span data-stu-id="99c98-108">Users can distribute the set of folders along with corresponding the catalog file that represents those folders.</span></span> <span data-ttu-id="99c98-109">Een catalogusbestand kan worden gebruikt door de ontvanger van inhoud wilt controleren of er wijzigingen zijn aangebracht in de mappen nadat de catalogus is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="99c98-109">A catalog file can be used by the recipient of content to validate whether any changes were made to the folders after the catalog was created.</span></span>

```powershell
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
<span data-ttu-id="99c98-110">Wij ondersteunen maken catalogusversie 1 en 2.</span><span class="sxs-lookup"><span data-stu-id="99c98-110">We support creating catalog version 1 and 2.</span></span> <span data-ttu-id="99c98-111">Versie 1 maakt gebruik van SHA1-hash-algoritme voor het maken van bestands-hashes en versie 2 SHA256 gebruikt.</span><span class="sxs-lookup"><span data-stu-id="99c98-111">Version 1 uses SHA1 hashing algorithm to create file hashes and version 2 uses SHA256.</span></span> <span data-ttu-id="99c98-112">Catalogusversie 2 van de wordt niet ondersteund op *Windows Server 2008 R2* en *Windows 7*.</span><span class="sxs-lookup"><span data-stu-id="99c98-112">Catalog version 2 is not supported on *Windows Server 2008 R2* and *Windows 7*.</span></span> <span data-ttu-id="99c98-113">Het is raadzaam om catalogusversie 2 van de gebruiken als platforms *Windows 8*, *Windows Server 2012* en hoger.</span><span class="sxs-lookup"><span data-stu-id="99c98-113">It is recommended to use catalog version 2 if using platforms *Windows 8*, *Windows Server 2012* and above.</span></span>

<span data-ttu-id="99c98-114">Geef de CatalogFilePath en het pad variabelen zodat deze overeenkomen met de locatie van de module-manifest voor het gebruik van deze opdracht op een bestaande module.</span><span class="sxs-lookup"><span data-stu-id="99c98-114">To use this command on an existing module, specify the CatalogFilePath and Path variables to match the location of the module manifest.</span></span> <span data-ttu-id="99c98-115">In het onderstaande voorbeeld is de module-manifest in C:\Program Files\Windows PowerShell\Modules\Pester.</span><span class="sxs-lookup"><span data-stu-id="99c98-115">In the example below, the module manifest is in C:\Program Files\Windows PowerShell\Modules\Pester.</span></span>

![](../images/NewFileCatalog.jpg)

<span data-ttu-id="99c98-116">Hiermee maakt u het catalogusbestand.</span><span class="sxs-lookup"><span data-stu-id="99c98-116">This creates the catalog file.</span></span>

![](../images/CatalogFile1.jpg)

![](../images/CatalogFile2.jpg)

<span data-ttu-id="99c98-117">Om te controleren of de integriteit van een catalogusbestand (Pester.cat in bovenstaande voorbeeld) moet het worden ondertekend met behulp van de [Set AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="99c98-117">To verify the integrity of a catalog file (Pester.cat in above exmaple) it should be signed using the [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) cmdlet.</span></span>


## <a name="test-filecatalog"></a><span data-ttu-id="99c98-118">Test-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="99c98-118">Test-FileCatalog</span></span>
--------------------------------

<span data-ttu-id="99c98-119">`Test-FileCatalog` valideert de catalogus die vertegenwoordigt een reeks mappen.</span><span class="sxs-lookup"><span data-stu-id="99c98-119">`Test-FileCatalog` validates the catalog representing a set of folders.</span></span>

```powershell
Test-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-Detailed] [-FilesToSkip <string[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

![](../images/TestFileCatalog.jpg)

<span data-ttu-id="99c98-120">Deze cmdlet vergelijkt de hashes van alle bestanden en hun relatieve paden gevonden in het catalogusbestand met zijn opgeslagen op schijf.</span><span class="sxs-lookup"><span data-stu-id="99c98-120">This cmdlet compares the hashes of all files and their relative paths found in the catalog file with ones saved to disk.</span></span> <span data-ttu-id="99c98-121">Als er een discrepantie tussen het bestands-hashes en paden gedetecteerd wordt de status van `ValidationFailed`.</span><span class="sxs-lookup"><span data-stu-id="99c98-121">If it detects any mismatch between file hashes and paths it returns a status of `ValidationFailed`.</span></span>
<span data-ttu-id="99c98-122">Gebruikers kunnen ophalen met alle deze informatie met behulp van de `Detailed` overschakelen.</span><span class="sxs-lookup"><span data-stu-id="99c98-122">Users can retrieve all this information using the `Detailed` switch.</span></span> <span data-ttu-id="99c98-123">De status van de ondertekening van de catalogus wordt weergegeven als de `Signature` veld hetzelfde als het aanroepen is de [Get-AuthenticodeSignature](https://technet.microsoft.com/en-us/library/hh849805.aspx) cmdlet uit op het catalogusbestand.</span><span class="sxs-lookup"><span data-stu-id="99c98-123">The signing status of the catalog is displayed as the `Signature` field, which is same as calling the [Get-AuthenticodeSignature](https://technet.microsoft.com/en-us/library/hh849805.aspx) cmdlet on the catalog file.</span></span>
<span data-ttu-id="99c98-124">Gebruikers kunnen ook een bestand tijdens de validatie overslaan met behulp van de `FilesToSkip` parameter.</span><span class="sxs-lookup"><span data-stu-id="99c98-124">Users can also skip any file during validation by using the `FilesToSkip` parameter.</span></span>
