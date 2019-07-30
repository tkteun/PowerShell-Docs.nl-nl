---
ms.date: 06/12/2017
contributor: manikb
keywords: Galerie, Power shell, cmdlet, psget
title: PowerShellGet installeren
ms.openlocfilehash: 2d3ba8c4d4d4c7ee023c7e6a948a29d8f47ea242
ms.sourcegitcommit: 8d47eb41445ffaf10fcd68874e397c9a1703d898
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/29/2019
ms.locfileid: "68601418"
---
# <a name="installing-powershellget"></a><span data-ttu-id="7dda4-103">PowerShellGet installeren</span><span class="sxs-lookup"><span data-stu-id="7dda4-103">Installing PowerShellGet</span></span>

## <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a><span data-ttu-id="7dda4-104">PowerShellGet is een in-box-module in de volgende releases</span><span class="sxs-lookup"><span data-stu-id="7dda4-104">PowerShellGet is an in-box module in the following releases</span></span>

- <span data-ttu-id="7dda4-105">[Windows 10](https://www.microsoft.com/windows) of hoger</span><span class="sxs-lookup"><span data-stu-id="7dda4-105">[Windows 10](https://www.microsoft.com/windows) or newer</span></span>
- <span data-ttu-id="7dda4-106">[Windows Server 2016](/windows-server/windows-server) of hoger</span><span class="sxs-lookup"><span data-stu-id="7dda4-106">[Windows Server 2016](/windows-server/windows-server) or newer</span></span>
- <span data-ttu-id="7dda4-107">[Windows Management Framework (WMF) 5,0](https://www.microsoft.com/download/details.aspx?id=50395) of hoger</span><span class="sxs-lookup"><span data-stu-id="7dda4-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) or newer</span></span>
- [<span data-ttu-id="7dda4-108">Power shell 6</span><span class="sxs-lookup"><span data-stu-id="7dda4-108">PowerShell 6</span></span>](https://github.com/PowerShell/PowerShell/releases)

## <a name="get-powershellget-module-for-powershell-versions-30-and-40"></a><span data-ttu-id="7dda4-109">De PowerShellGet-module ophalen voor de Power shell-versie 3,0 en 4,0</span><span class="sxs-lookup"><span data-stu-id="7dda4-109">Get PowerShellGet module for PowerShell versions 3.0 and 4.0</span></span>

- [<span data-ttu-id="7dda4-110">Package Management MSI</span><span class="sxs-lookup"><span data-stu-id="7dda4-110">PackageManagement MSI</span></span>](https://www.microsoft.com/download/details.aspx?id=51451)

## <a name="get-the-latest-version-from-powershell-gallery"></a><span data-ttu-id="7dda4-111">De nieuwste versie van PowerShell Gallery ophalen</span><span class="sxs-lookup"><span data-stu-id="7dda4-111">Get the latest version from PowerShell Gallery</span></span>

- <span data-ttu-id="7dda4-112">Voordat u PowerShellGet bijwerkt, moet u altijd de meest recente Nuget-provider installeren.</span><span class="sxs-lookup"><span data-stu-id="7dda4-112">Before updating PowerShellGet, you should always install the latest Nuget provider.</span></span> <span data-ttu-id="7dda4-113">Voer hiertoe de volgende opdracht uit in een Power shell-sessie met verhoogde bevoegdheden.</span><span class="sxs-lookup"><span data-stu-id="7dda4-113">To do that, run the following in an elevated PowerShell session.</span></span>

  ```powershell
  Install-PackageProvider Nuget -Force
  Exit
  ```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a><span data-ttu-id="7dda4-114">Voor systemen met Power shell 5,0 (of hoger) kunt u de meest recente PowerShellGet installeren</span><span class="sxs-lookup"><span data-stu-id="7dda4-114">For systems with PowerShell 5.0 (or newer) you can install the latest PowerShellGet</span></span>

- <span data-ttu-id="7dda4-115">Hiervoor voert u de volgende opdrachten uit vanuit een Power shell-sessie met verhoogde bevoegdheden voor Windows 10, Windows Server 2016, een systeem met WMF 5,0 of 5,1 dat is geïnstalleerd of een systeem met Power shell 6.</span><span class="sxs-lookup"><span data-stu-id="7dda4-115">To do this on Windows 10, Windows Server 2016, any system with WMF 5.0 or 5.1 installed, or any system with PowerShell 6, run the following commands from an elevated PowerShell session.</span></span>

  ```powershell
  Install-Module -Name PowerShellGet -Force
  Exit
  ```

- <span data-ttu-id="7dda4-116">Gebruiken `Update-Module` om nieuwere versies op te halen.</span><span class="sxs-lookup"><span data-stu-id="7dda4-116">Use `Update-Module` to get newer versions.</span></span>

  ```powershell
  Update-Module -Name PowerShellGet
  Exit
  ```

### <a name="for-systems-running-powershell-3-or-powershell-4-that-have-installed-the-packagemanagement-msihttpswwwmicrosoftcomdownloaddetailsaspxid51451"></a><span data-ttu-id="7dda4-117">Voor systemen met Power Shell 3 of Power Shell 4 waarop de [Package Management MSI](https://www.microsoft.com/download/details.aspx?id=51451) is geïnstalleerd</span><span class="sxs-lookup"><span data-stu-id="7dda4-117">For systems running PowerShell 3 or PowerShell 4, that have installed the [PackageManagement MSI](https://www.microsoft.com/download/details.aspx?id=51451)</span></span>

- <span data-ttu-id="7dda4-118">Gebruik de onderstaande PowerShellGet-cmdlet van een Power shell-sessie met verhoogde bevoegdheid om de modules op te slaan in een lokale map</span><span class="sxs-lookup"><span data-stu-id="7dda4-118">Use below PowerShellGet cmdlet from an elevated PowerShell session to save the modules to a local directory</span></span>

  ```powershell
  Save-Module PowerShellGet -Path C:\LocalFolder
  Exit
  ```

- <span data-ttu-id="7dda4-119">Zorg ervoor dat de PowerShellGet-en package management-modules niet worden geladen in andere processen.</span><span class="sxs-lookup"><span data-stu-id="7dda4-119">Ensure that PowerShellGet and PackageManagement modules are not loaded in any other processes.</span></span>
- <span data-ttu-id="7dda4-120">Inhoud van `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` en `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` mappen verwijderen.</span><span class="sxs-lookup"><span data-stu-id="7dda4-120">Delete contents of `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` and  `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` folders.</span></span>
- <span data-ttu-id="7dda4-121">Open de PS-console opnieuw met verhoogde machtigingen en voer de volgende opdrachten uit.</span><span class="sxs-lookup"><span data-stu-id="7dda4-121">Re-open the PS Console with elevated permissions then run the following commands.</span></span>

  ```powershell
  Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
  Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force
  ```
