---
ms.date: 10/17/2017
contributor: keithb
ms.topic: reference
keywords: Galerie, powershell, cmdlet, psget
title: Save-Script
ms.openlocfilehash: 67697fc0e70fb31cad9ad5ae7ce01debef160b81
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="save-script"></a><span data-ttu-id="2cad5-103">Save-Script</span><span class="sxs-lookup"><span data-stu-id="2cad5-103">Save-Script</span></span>

<span data-ttu-id="2cad5-104">Opslaan Script cmdlet kunt u het scriptbestand bekijken door op een opgegeven locatie op te slaan.</span><span class="sxs-lookup"><span data-stu-id="2cad5-104">Save-Script cmdlet lets you to review the script file by saving it to a specified location.</span></span>

## <a name="description"></a><span data-ttu-id="2cad5-105">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="2cad5-105">Description</span></span>

<span data-ttu-id="2cad5-106">Het opgegeven script Hiermee slaat u de cmdlet opslaan-Script.</span><span class="sxs-lookup"><span data-stu-id="2cad5-106">The Save-Script cmdlet saves the specified script.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="2cad5-107">De syntaxis van cmdlet</span><span class="sxs-lookup"><span data-stu-id="2cad5-107">Cmdlet syntax</span></span>

```powershell
Get-Command -Name Save-Script -Module PowerShellGet -Syntax
```
## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="2cad5-108">Verwijzing naar het online help van cmdlet</span><span class="sxs-lookup"><span data-stu-id="2cad5-108">Cmdlet online help reference</span></span>

[<span data-ttu-id="2cad5-109">Save-Script</span><span class="sxs-lookup"><span data-stu-id="2cad5-109">Save-Script</span></span>](http://go.microsoft.com/fwlink/?LinkId=619786)

## <a name="example-commands"></a><span data-ttu-id="2cad5-110">Voorbeeldopdrachten</span><span class="sxs-lookup"><span data-stu-id="2cad5-110">Example commands</span></span>

### <a name="example-1-save-a-script-from-a-repository"></a><span data-ttu-id="2cad5-111">Voorbeeld 1: Een script uit een bibliotheek opslaan</span><span class="sxs-lookup"><span data-stu-id="2cad5-111">Example 1: Save a script from a repository</span></span>
<span data-ttu-id="2cad5-112">Deze opdracht slaat u de nieuwste versie van het script Fabrikam-ClientScript vanuit GalleryINT opslagplaats naar de lokale map C:\ScriptSharingDemo</span><span class="sxs-lookup"><span data-stu-id="2cad5-112">This command saves the latest version of the script Fabrikam-ClientScript from GalleryINT repository to the local folder C:\ScriptSharingDemo</span></span>

```powershell
Save-Script -Name Fabrikam-ClientScript -Repository GalleryINT -Path C:\ScriptSharingDemo
```

### <a name="example-2-save-a-version-of-a-script-by-piping-from-the-find-script-cmdlet"></a><span data-ttu-id="2cad5-113">Voorbeeld 2: Een versie van een script opslaan door piping van de cmdlet Find-Script</span><span class="sxs-lookup"><span data-stu-id="2cad5-113">Example 2: Save a version of a script by piping from the Find-Script cmdlet</span></span>

<span data-ttu-id="2cad5-114">De eerste opdracht Zoeken naar versie 1.5 van Fabrikam-ClientScript vanuit de opslagplaats GalleryINT en opgeslagen in de map C:\ScriptSharingDemo</span><span class="sxs-lookup"><span data-stu-id="2cad5-114">The first command finds version 1.5 of Fabrikam-ClientScript from the repository GalleryINT and saves it to the folder C:\ScriptSharingDemo</span></span>

<span data-ttu-id="2cad5-115">De tweede opdracht valideert de metagegevens van de opgeslagen script.</span><span class="sxs-lookup"><span data-stu-id="2cad5-115">The second command validates the saved script metadata.</span></span>

```powershell
Find-Script -Name Fabrikam-ClientScript -Repository GalleryINT -RequiredVersion 1.5 | Save-Script -Path C:\\ScriptSharingDemo
Test-ScriptFileInfo C:\\ScriptSharingDemo\\Fabrikam-ClientScript.ps1

Version Name Author Description
------- ---- ------ -----------
1.5 Fabrikam-ClientScript manikb Description for the Fabrikam-ClientScript script
```

### <a name="example-3-save-a-prerelease-version-of-a-script-from-a-repository"></a><span data-ttu-id="2cad5-116">Voorbeeld 3: Een voorlopige versie van een script uit een bibliotheek opslaan</span><span class="sxs-lookup"><span data-stu-id="2cad5-116">Example 3: Save a prerelease version of a script from a repository</span></span>
<span data-ttu-id="2cad5-117">Deze opdracht slaat u de nieuwste versie van het script Fabrikam-ClientScript vanuit GalleryINT opslagplaats naar de lokale map C:\ScriptSharingDemo</span><span class="sxs-lookup"><span data-stu-id="2cad5-117">This command saves the latest version of the script Fabrikam-ClientScript from GalleryINT repository to the local folder C:\ScriptSharingDemo</span></span>

```powershell
Save-Script -Name Fabrikam-ClientScript -Path C:\ScriptSharingDemo -AllowPrerelease
```