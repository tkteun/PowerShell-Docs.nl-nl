---
ms.date: 2017-10-17
contributor: keithb
ms.topic: reference
keywords: Galerie, powershell, cmdlet, psget
title: Opslaan-Script
ms.openlocfilehash: b54e8ba074b7cadd52df781c9021332ccc90f9fd
ms.sourcegitcommit: 58371abe9db4b9a0e4e1eb82d39a9f9e187355f9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2017
---
# <a name="save-script"></a><span data-ttu-id="bd7e2-103">Opslaan-Script</span><span class="sxs-lookup"><span data-stu-id="bd7e2-103">Save-Script</span></span>

<span data-ttu-id="bd7e2-104">Opslaan Script cmdlet kunt u het scriptbestand bekijken door op een opgegeven locatie op te slaan.</span><span class="sxs-lookup"><span data-stu-id="bd7e2-104">Save-Script cmdlet lets you to review the script file by saving it to a specified location.</span></span>

## <a name="description"></a><span data-ttu-id="bd7e2-105">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="bd7e2-105">Description</span></span>

<span data-ttu-id="bd7e2-106">Het opgegeven script Hiermee slaat u de cmdlet opslaan-Script.</span><span class="sxs-lookup"><span data-stu-id="bd7e2-106">The Save-Script cmdlet saves the specified script.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="bd7e2-107">De syntaxis van cmdlet</span><span class="sxs-lookup"><span data-stu-id="bd7e2-107">Cmdlet syntax</span></span>

```powershell
Get-Command -Name Save-Script -Module PowerShellGet -Syntax
```
## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="bd7e2-108">Verwijzing naar het online help van cmdlet</span><span class="sxs-lookup"><span data-stu-id="bd7e2-108">Cmdlet online help reference</span></span>

[<span data-ttu-id="bd7e2-109">Opslaan-Script</span><span class="sxs-lookup"><span data-stu-id="bd7e2-109">Save-Script</span></span>](http://go.microsoft.com/fwlink/?LinkId=619786)

## <a name="example-commands"></a><span data-ttu-id="bd7e2-110">Voorbeeldopdrachten</span><span class="sxs-lookup"><span data-stu-id="bd7e2-110">Example commands</span></span>

### <a name="example-1-save-a-script-from-a-repository"></a><span data-ttu-id="bd7e2-111">Voorbeeld 1: Een script uit een bibliotheek opslaan</span><span class="sxs-lookup"><span data-stu-id="bd7e2-111">Example 1: Save a script from a repository</span></span>
<span data-ttu-id="bd7e2-112">Deze opdracht slaat u de nieuwste versie van het script Fabrikam-ClientScript vanuit GalleryINT opslagplaats naar de lokale map C:\ScriptSharingDemo</span><span class="sxs-lookup"><span data-stu-id="bd7e2-112">This command saves the latest version of the script Fabrikam-ClientScript from GalleryINT repository to the local folder C:\ScriptSharingDemo</span></span>

```powershell
Save-Script -Name Fabrikam-ClientScript -Repository GalleryINT -Path C:\ScriptSharingDemo
```

### <a name="example-2-save-a-version-of-a-script-by-piping-from-the-find-script-cmdlet"></a><span data-ttu-id="bd7e2-113">Voorbeeld 2: Een versie van een script opslaan door piping van de cmdlet Find-Script</span><span class="sxs-lookup"><span data-stu-id="bd7e2-113">Example 2: Save a version of a script by piping from the Find-Script cmdlet</span></span>

<span data-ttu-id="bd7e2-114">De eerste opdracht Zoeken naar versie 1.5 van Fabrikam-ClientScript vanuit de opslagplaats GalleryINT en opgeslagen in de map C:\ScriptSharingDemo</span><span class="sxs-lookup"><span data-stu-id="bd7e2-114">The first command finds version 1.5 of Fabrikam-ClientScript from the repository GalleryINT and saves it to the folder C:\ScriptSharingDemo</span></span>

<span data-ttu-id="bd7e2-115">De tweede opdracht valideert de metagegevens van de opgeslagen script.</span><span class="sxs-lookup"><span data-stu-id="bd7e2-115">The second command validates the saved script metadata.</span></span>

```powershell
Find-Script -Name Fabrikam-ClientScript -Repository GalleryINT -RequiredVersion 1.5 | Save-Script -Path C:\\ScriptSharingDemo
Test-ScriptFileInfo C:\\ScriptSharingDemo\\Fabrikam-ClientScript.ps1

Version Name Author Description
------- ---- ------ -----------
1.5 Fabrikam-ClientScript manikb Description for the Fabrikam-ClientScript script
```

### <a name="example-3-save-a-prerelease-version-of-a-script-from-a-repository"></a><span data-ttu-id="bd7e2-116">Voorbeeld 3: Een voorlopige versie van een script uit een bibliotheek opslaan</span><span class="sxs-lookup"><span data-stu-id="bd7e2-116">Example 3: Save a prerelease version of a script from a repository</span></span>
<span data-ttu-id="bd7e2-117">Deze opdracht slaat u de nieuwste versie van het script Fabrikam-ClientScript vanuit GalleryINT opslagplaats naar de lokale map C:\ScriptSharingDemo</span><span class="sxs-lookup"><span data-stu-id="bd7e2-117">This command saves the latest version of the script Fabrikam-ClientScript from GalleryINT repository to the local folder C:\ScriptSharingDemo</span></span>

```powershell
Save-Script -Name Fabrikam-ClientScript -Path C:\ScriptSharingDemo -AllowPrerelease
```

