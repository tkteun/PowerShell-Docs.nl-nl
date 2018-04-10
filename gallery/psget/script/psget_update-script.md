---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: Galerie, powershell, cmdlet, psget
title: Update-Script
ms.openlocfilehash: 23e558a063689d263f68d34ec3b154be1c77ae89
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="update-script"></a><span data-ttu-id="132a8-103">Update-Script</span><span class="sxs-lookup"><span data-stu-id="132a8-103">Update-Script</span></span>

<span data-ttu-id="132a8-104">Updatescript cmdlet kunt u in-place bijwerken van de scriptbestanden die zijn geïnstalleerd met de cmdlet Install-Script.</span><span class="sxs-lookup"><span data-stu-id="132a8-104">Update-Script cmdlet lets you to do in-place update of the script files which were installed using Install-Script cmdlet.</span></span>

## <a name="description"></a><span data-ttu-id="132a8-105">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="132a8-105">Description</span></span>

<span data-ttu-id="132a8-106">De cmdlet updatescript werkt het opgegeven script uit de opslagplaats waaruit deze eerder was geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="132a8-106">The Update-Script cmdlet updates the specified script from the repository from which it was previously installed.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="132a8-107">De syntaxis van cmdlet</span><span class="sxs-lookup"><span data-stu-id="132a8-107">Cmdlet syntax</span></span>

```powershell
Get-Command -Name Update-Script -Module PowerShellGet -Syntax
```
## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="132a8-108">Verwijzing naar het online help van cmdlet</span><span class="sxs-lookup"><span data-stu-id="132a8-108">Cmdlet online help reference</span></span>

[<span data-ttu-id="132a8-109">Update-Script</span><span class="sxs-lookup"><span data-stu-id="132a8-109">Update-Script</span></span>](http://go.microsoft.com/fwlink/?LinkId=619787)

## <a name="example-commands"></a><span data-ttu-id="132a8-110">Voorbeeldopdrachten</span><span class="sxs-lookup"><span data-stu-id="132a8-110">Example commands</span></span>
```powershell
Install-Script -Name Fabrikam-Script -RequiredVersion 1.0 -Repository GalleryINT -Scope
Get-InstalledScript -Name Fabrikam-Script
Version Name Type Repository Description
------- ---- ---- ---------- -----------
1.0 Fabrikam-Script Script GalleryINT Description for the Fabrikam-Script script

# Update a specific script to the required version
Update-Script -Name Fabrikam-Script -RequiredVersion 1.5
Get-InstalledScript -Name Fabrikam-Script
Version Name Type Repository Description
------- ---- ---- ---------- -----------
1.5 Fabrikam-Script Script GalleryINT Description for the Fabrikam-Script script

# Update a specific script to the required prerelease version
Update-Script -Name Fabrikam-Script -RequiredVersion 1.5.0-alpha -AllowPrerelease
Get-InstalledScript -Name Fabrikam-Script
Version Name Type Repository Description
------- ---- ---- ---------- -----------
1.5.0-alpha Fabrikam-Script Script GalleryINT Description for the Fabrikam-Script script

# Update all installed scripts
Install-Script -Name Fabrikam-ServerScript -RequiredVersion 1.0 -Repository GalleryINT -Scope CurrentUser
Get-InstalledScript
Version Name Type Repository Description
------- ---- ---- ---------- -----------
2.0 Required-Script3 Script GalleryINT Description for the Required-Script3 script
1.0 Demo-Script Script LocalRepo1 Script file description goes here
1.5 Fabrikam-Script Script GalleryINT Description for the Fabrikam-Script script
1.0 Fabrikam-ServerScript Script GalleryINT Description for the Fabrikam-ServerScript script
2.5 Required-Script1 Script GalleryINT Description for the Required-Script1 script
2.5 Required-Script2 Script GalleryINT Description for the Required-Script2 script
2.0 Script-WithDependencies2 Script GalleryINT Description for the Script-WithDependencies2 script

Update-Script
Get-InstalledScript
Version Name Type Repository Description
------- ---- ---- ---------- -----------
2.5 Required-Script3 Script GalleryINT Description for the Required-Script3 script
1.0 Demo-Script Script LocalRepo1 Script file description goes here
2.5 Fabrikam-Script Script GalleryINT Description for the Fabrikam-Script script
2.5 Fabrikam-ServerScript Script GalleryINT Description for the Fabrikam-ServerScript script
2.5 Required-Script1 Script GalleryINT Description for the Required-Script1 script
2.5 Required-Script2 Script GalleryINT Description for the Required-Script2 script
2.0 Script-WithDependencies2 Script GalleryINT Description for the Script-WithDependencies2 script
```