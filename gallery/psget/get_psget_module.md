---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: Galerie, powershell, cmdlet, psget
title: PowerShellGet Module ophalen
ms.openlocfilehash: a5a323b17709e519ec57623a9dd7499e591bbed5
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2017
---
<a name="get-powershellget-module"></a><span data-ttu-id="7d84f-103">PowerShellGet Module ophalen</span><span class="sxs-lookup"><span data-stu-id="7d84f-103">Get PowerShellGet Module</span></span>
========================

### <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a><span data-ttu-id="7d84f-104">PowerShellGet is een module in het vak in de volgende versies</span><span class="sxs-lookup"><span data-stu-id="7d84f-104">PowerShellGet is an in-box module in the following releases</span></span>
- <span data-ttu-id="7d84f-105">[Windows 10](https://www.microsoft.com/en-us/windows/get-windows-10) of hoger</span><span class="sxs-lookup"><span data-stu-id="7d84f-105">[Windows 10](https://www.microsoft.com/en-us/windows/get-windows-10) or newer</span></span>
- <span data-ttu-id="7d84f-106">[Windows Server 2016](https://technet.microsoft.com/en-us/windows-server-docs/get-started/windows-server-2016) of hoger</span><span class="sxs-lookup"><span data-stu-id="7d84f-106">[Windows Server 2016](https://technet.microsoft.com/en-us/windows-server-docs/get-started/windows-server-2016) or newer</span></span>
- <span data-ttu-id="7d84f-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) of hoger</span><span class="sxs-lookup"><span data-stu-id="7d84f-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) or newer</span></span>
- [<span data-ttu-id="7d84f-108">PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="7d84f-108">PowerShell 6</span></span>](https://github.com/PowerShell/PowerShell/releases)

### <a name="get-powershellget-module-for-powershell-versions-30-and-40"></a><span data-ttu-id="7d84f-109">PowerShellGet module ophalen voor PowerShell versie 3.0 en 4.0</span><span class="sxs-lookup"><span data-stu-id="7d84f-109">Get PowerShellGet module for PowerShell versions 3.0 and 4.0</span></span>
- [<span data-ttu-id="7d84f-110">PackageManagement MSI</span><span class="sxs-lookup"><span data-stu-id="7d84f-110">PackageManagement MSI</span></span>](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409) 

### <a name="get-the-latest-version-from-powershell-gallery"></a><span data-ttu-id="7d84f-111">Ophalen van de meest recente versie van PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="7d84f-111">Get the latest version from PowerShell Gallery</span></span>

- <span data-ttu-id="7d84f-112">Voordat u PowerShellGet bijwerkt, moet u altijd de meest recente Nuget-provider installeren.</span><span class="sxs-lookup"><span data-stu-id="7d84f-112">Before updating PowerShellGet, you should always install the latest Nuget provider.</span></span> <span data-ttu-id="7d84f-113">Voer hiertoe de volgende in een PowerShell-sessie met verhoogde bevoegdheden.</span><span class="sxs-lookup"><span data-stu-id="7d84f-113">To do that, run the following in an elevated PowerShell session.</span></span>
```powershell
Install-PackageProvider Nuget –Force
Exit
```

#### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a><span data-ttu-id="7d84f-114">Voor systemen met PowerShell 5.0 (of nieuwer) kunt u de meest recente PowerShellGet installeren</span><span class="sxs-lookup"><span data-stu-id="7d84f-114">For systems with PowerShell 5.0 (or newer) you can install the latest PowerShellGet</span></span> 
- <span data-ttu-id="7d84f-115">Voer de volgende opdrachten vanuit een PowerShell-sessie met verhoogde bevoegdheden om dit te doen op Windows 10, Windows Server 2016, elk systeem met WMF 5.0 of 5.1 is geïnstalleerd of een systeem met PowerShell-6.</span><span class="sxs-lookup"><span data-stu-id="7d84f-115">To do this on Windows 10, Windows Server 2016, any system with WMF 5.0 or 5.1 installed, or any system with PowerShell 6, run the following commands from an elevated PowerShell session.</span></span>
```powershell
Install-Module –Name PowerShellGet –Force
Exit
```

- <span data-ttu-id="7d84f-116">Update-Module gebruiken om nieuwe versies.</span><span class="sxs-lookup"><span data-stu-id="7d84f-116">Use Update-Module to get newer versions.</span></span>
```powershell
Update-Module -Name PowerShellGet
Exit
```

#### <a name="for-systems-running-powershell-3-or-powershell-4-that-have-installed-the-packagemanagement-msihttpgomicrosoftcomfwlinklinkid746217clcid0x409"></a><span data-ttu-id="7d84f-117">Voor systemen met PowerShell 3 of 4 PowerShell, die beschikken over de [PackageManagement MSI](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)</span><span class="sxs-lookup"><span data-stu-id="7d84f-117">For systems running PowerShell 3 or PowerShell 4, that have installed the [PackageManagement MSI](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)</span></span>

- <span data-ttu-id="7d84f-118">Gebruik onderstaande PowerShellGet cmdlet vanuit een PowerShell-sessie met verhoogde bevoegdheid de modules opslaan naar een lokale map</span><span class="sxs-lookup"><span data-stu-id="7d84f-118">Use below PowerShellGet cmdlet from an elevated PowerShell session to save the modules to a local directory</span></span>

```powershell
Save-Module PowerShellGet -Path C:\LocalFolder
Exit
```

- <span data-ttu-id="7d84f-119">Zorg ervoor dat PowerShellGet en PackageManagment modules niet worden geladen in andere processen.</span><span class="sxs-lookup"><span data-stu-id="7d84f-119">Ensure that PowerShellGet and PackageManagment modules are not loaded in any other processes.</span></span>
- <span data-ttu-id="7d84f-120">Verwijderen van de inhoud van `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` en `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` mappen.</span><span class="sxs-lookup"><span data-stu-id="7d84f-120">Delete contents of `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` and  `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` folders.</span></span>
- <span data-ttu-id="7d84f-121">Open deze opnieuw de PS-Console met verhoogde bevoegdheden en voer vervolgens de volgende opdrachten.</span><span class="sxs-lookup"><span data-stu-id="7d84f-121">Re-open the PS Console with elevated permissions then run the following commands.</span></span>

```powershell
Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force