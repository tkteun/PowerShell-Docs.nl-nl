---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: Galerie, powershell, cmdlet, psget
title: Update-Module
ms.openlocfilehash: 89b0111eda4421606843f108dca90519b2c9379e
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="update-module"></a><span data-ttu-id="10b28-103">Update-Module</span><span class="sxs-lookup"><span data-stu-id="10b28-103">Update-Module</span></span>

<span data-ttu-id="10b28-104">Downloadt en installeert de nieuwste versie van de opgegeven modules vanuit een online-galerie op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="10b28-104">Downloads and installs the newest version of specified modules from an online gallery to the local computer.</span></span>

## <a name="description"></a><span data-ttu-id="10b28-105">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="10b28-105">Description</span></span>

<span data-ttu-id="10b28-106">De cmdlet Update-Module installeert een nieuwere versie van een Windows PowerShell-module die is geïnstalleerd vanaf de on line galerie door het uitvoeren van Install-Module op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="10b28-106">The Update-Module cmdlet installs a newer version of a Windows PowerShell module that was installed from the online gallery by running Install-Module on the local computer.</span></span>

<span data-ttu-id="10b28-107">De nieuwste versie van de opgegeven module in online galerie is standaard geïnstalleerd, tenzij u een vereiste versie opgeeft.</span><span class="sxs-lookup"><span data-stu-id="10b28-107">By default, the newest version of the specified module available in online gallery is installed, unless you specify a required version.</span></span> <span data-ttu-id="10b28-108">U kunt een bestaande, geïnstalleerde module bijwerken door op te geven van de naam van de module. Update-Module zoekt $env: PSModulePath voor de module die u wilt bijwerken.</span><span class="sxs-lookup"><span data-stu-id="10b28-108">You can update an existing, installed module by specifying the name of the module; Update-Module searches $env:PSModulePath for the module that you want to update.</span></span>

<span data-ttu-id="10b28-109">Update-Module uitgevoerd zonder de parameter Name updates alle modules weer die kunnen worden bijgewerkt op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="10b28-109">Running Update-Module without the Name parameter updates all modules that can be updated on the local computer.</span></span>

### <a name="notes"></a><span data-ttu-id="10b28-110">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="10b28-110">Notes</span></span>

- <span data-ttu-id="10b28-111">Deze cmdlet wordt uitgevoerd op Windows PowerShell 3.0 of latere versies van Windows PowerShell op Windows 7 of Windows 2008 R2 en latere versies van Windows.</span><span class="sxs-lookup"><span data-stu-id="10b28-111">This cmdlet runs on Windows PowerShell 3.0 or later releases of Windows PowerShell, on Windows 7 or Windows 2008 R2 and later releases of Windows.</span></span>
- <span data-ttu-id="10b28-112">Als de module die u met de parameter Name opgeeft niet met behulp van Install-Module is geïnstalleerd, wordt er een fout optreedt.</span><span class="sxs-lookup"><span data-stu-id="10b28-112">If the module that you specify with the Name parameter was not installed by using Install-Module, an error occurs.</span></span> <span data-ttu-id="10b28-113">U kunt de Update-Module alleen uitvoeren op de modules die u hebt geïnstalleerd vanuit de on line galerie door het uitvoeren van de installatie-Module.</span><span class="sxs-lookup"><span data-stu-id="10b28-113">You can only run Update-Module on modules that you installed from the online gallery by running Install-Module.</span></span>
- <span data-ttu-id="10b28-114">Als de Update-Module probeert bij te werken van de binaire bestanden die gebruikt worden, foutmelding Update-Module een die identificeert de processen van het probleem en wordt de gebruiker om opnieuw te proberen Update-Module na het stoppen van de processen geïnformeerd.</span><span class="sxs-lookup"><span data-stu-id="10b28-114">If Update-Module attempts to update binaries that are in use, Update-Module returns an error that identifies the problem processes, and informs the user to retry Update-Module after stopping the processes.</span></span>
- <span data-ttu-id="10b28-115">In PowerShell 5.0 of nieuwere versies, wanneer een module-Update-Module updates worden toegevoegd de meest recente (of opgegeven) versie van de module zodat de oudere en nieuwere versies nu side-by-side in dezelfde map zijn.</span><span class="sxs-lookup"><span data-stu-id="10b28-115">On PowerShell 5.0 or newer versions, when Update-Module updates a module, it adds the latest (or specified) version of the module, so the older and newer versions are now side-by-side in the same directory.</span></span> <span data-ttu-id="10b28-116">Het normaal zou zijn handig om te zeggen dat en om een voorbeeld van de uitvoer van deze opdrachten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="10b28-116">It would be useful to say so and to show an example of the output from these commands.</span></span>


## <a name="cmdlet-syntax"></a><span data-ttu-id="10b28-117">De syntaxis van cmdlet</span><span class="sxs-lookup"><span data-stu-id="10b28-117">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Update-Module -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="10b28-118">Verwijzing naar het online help van cmdlet</span><span class="sxs-lookup"><span data-stu-id="10b28-118">Cmdlet online help reference</span></span>

[<span data-ttu-id="10b28-119">Update-Module</span><span class="sxs-lookup"><span data-stu-id="10b28-119">Update-Module</span></span>](http://go.microsoft.com/fwlink/?LinkID=398576)


## <a name="example-commands"></a><span data-ttu-id="10b28-120">Voorbeeldopdrachten</span><span class="sxs-lookup"><span data-stu-id="10b28-120">Example commands</span></span>

```powershell
PS C:\windows\system32> Update-Module -Name ContosoServer -RequiredVersion 1.5
PS C:\windows\system32> Get-Module -ListAvailable -Name ContosoServer | Format-List Name,Version,ModuleBase
Name : ContosoServer
Version : 2.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\2.0
Name : ContosoServer
Version : 1.5
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\1.5
Name : ContosoServer
Version : 1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\1.0
PS C:\windows\system32> Get-InstalledModule
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer MSPSGallery ContosoServer module
1.5 ContosoServer MSPSGallery ContosoServer module
2.0 ContosoServer MSPSGallery ContosoServer module
PS C:\windows\system32> Update-Module -Name ContosoServer
PS C:\windows\system32> Get-Module -ListAvailable -Name ContosoServer | Format-List Name,Version,ModuleBase
Name : ContosoServer
Version : 2.8.1
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\2.8.1
Name : ContosoServer
Version : 2.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\2.0
Name : ContosoServer
Version : 1.5
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\1.5
Name : ContosoServer
Version : 1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\1.0
PS C:\windows\system32> Get-InstalledModule
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer MSPSGallery ContosoServer module
1.5 ContosoServer MSPSGallery ContosoServer module
2.0 ContosoServer MSPSGallery ContosoServer module
2.8.1 ContosoServer MSPSGallery ContosoServer module
```

### <a name="update-the-module-with-a-prerelease-version-requires--allowprerelease-flag"></a><span data-ttu-id="10b28-121">Bijwerken van de module met een prerelease-versie, vlag - AllowPrerelease vereist</span><span class="sxs-lookup"><span data-stu-id="10b28-121">Update the module with a prerelease version, requires -AllowPrerelease flag</span></span>
```powershell
PS C:\windows\system32> Get-InstalledModule
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer MSPSGallery ContosoServer module
1.5 ContosoServer MSPSGallery ContosoServer module
2.0 ContosoServer MSPSGallery ContosoServer module
2.8.1 ContosoServer MSPSGallery ContosoServer module

PS C:\windows\system32> Find-Module ContosoServer -AllowPrerelease

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
3.0.0-alpha    ConstosoServer                      MSPSGallery          The PowerShell Contoso Server deployment tools...

PS C:\windows\system32> Update-Module -Name ContosoServer -AllowPrerelease
PS C:\windows\system32> Get-InstalledModule
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer MSPSGallery ContosoServer module
1.5 ContosoServer MSPSGallery ContosoServer module
2.0 ContosoServer MSPSGallery ContosoServer module
2.8.1 ContosoServer MSPSGallery ContosoServer module
3.0.0-alpha ContosoServer MSPSGallery ContosoServer module

```


### <a name="update-the-testdepwithnestedrequiredmodules1-module-with-dependencies"></a><span data-ttu-id="10b28-122">De module TestDepWithNestedRequiredModules1 bijwerken met afhankelijkheden.</span><span class="sxs-lookup"><span data-stu-id="10b28-122">Update the TestDepWithNestedRequiredModules1 module with dependencies.</span></span>
```powershell
Find-Module -Name TestDepWithNestedRequiredModules1 -Repository LocalRepo -AllVersions

Version    Name                                Repository  Description
-------    ----                                ----------  -----------
1.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module
2.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module

Update-Module -Name TestDepWithNestedRequiredModules1 -RequiredVersion 2.0
Get-InstalledModule

Version    Name                                Repository  Description
-------    ----                                ----------  -----------
1.0        NestedRequiredModule1               LocalRepo   NestedRequiredModule1 module
2.5        NestedRequiredModule2               LocalRepo   NestedRequiredModule2 module
2.0        NestedRequiredModule3               LocalRepo   NestedRequiredModule3 module
2.5        NestedRequiredModule3               LocalRepo   NestedRequiredModule3 module
1.0        RequiredModule1                     LocalRepo   RequiredModule1 module
2.5        RequiredModule2                     LocalRepo   RequiredModule2 module
2.0        RequiredModule3                     LocalRepo   RequiredModule3 module
2.5        RequiredModule3                     LocalRepo   RequiredModule3 module
1.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module
2.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module



```