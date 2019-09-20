---
ms.date: 06/12/2017
contributor: manikb
keywords: Galerie, Power shell, cmdlet, psget
title: PowerShellGet installeren
ms.openlocfilehash: a0ef46a9ee4bbf668a58067256d098967bde48c5
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71143595"
---
# <a name="installing-powershellget"></a><span data-ttu-id="f1471-103">PowerShellGet installeren</span><span class="sxs-lookup"><span data-stu-id="f1471-103">Installing PowerShellGet</span></span>

## <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a><span data-ttu-id="f1471-104">PowerShellGet is een in-box-module in de volgende releases</span><span class="sxs-lookup"><span data-stu-id="f1471-104">PowerShellGet is an in-box module in the following releases</span></span>

- <span data-ttu-id="f1471-105">[Windows 10](https://www.microsoft.com/windows) of hoger</span><span class="sxs-lookup"><span data-stu-id="f1471-105">[Windows 10](https://www.microsoft.com/windows) or newer</span></span>
- <span data-ttu-id="f1471-106">[Windows Server 2016](/windows-server/windows-server) of hoger</span><span class="sxs-lookup"><span data-stu-id="f1471-106">[Windows Server 2016](/windows-server/windows-server) or newer</span></span>
- <span data-ttu-id="f1471-107">[Windows Management Framework (WMF) 5,0](https://www.microsoft.com/download/details.aspx?id=50395) of hoger</span><span class="sxs-lookup"><span data-stu-id="f1471-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) or newer</span></span>
- [<span data-ttu-id="f1471-108">Power shell 6</span><span class="sxs-lookup"><span data-stu-id="f1471-108">PowerShell 6</span></span>](https://github.com/PowerShell/PowerShell/releases)

## <a name="get-the-latest-version-from-powershell-gallery"></a><span data-ttu-id="f1471-109">De nieuwste versie van PowerShell Gallery ophalen</span><span class="sxs-lookup"><span data-stu-id="f1471-109">Get the latest version from PowerShell Gallery</span></span>

<span data-ttu-id="f1471-110">Voordat u **PowerShellGet**bijwerkt, moet u altijd de meest recente **NuGet** -provider installeren.</span><span class="sxs-lookup"><span data-stu-id="f1471-110">Before updating **PowerShellGet**, you should always install the latest **NuGet** provider.</span></span> <span data-ttu-id="f1471-111">Voer de volgende opdracht uit vanuit een Power shell-sessie met verhoogde bevoegdheden.</span><span class="sxs-lookup"><span data-stu-id="f1471-111">From an elevated PowerShell session, run the following command.</span></span>

```powershell
Install-PackageProvider -Name NuGet -Force
Exit
```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a><span data-ttu-id="f1471-112">Voor systemen met Power shell 5,0 (of hoger) kunt u de meest recente PowerShellGet installeren</span><span class="sxs-lookup"><span data-stu-id="f1471-112">For systems with PowerShell 5.0 (or newer) you can install the latest PowerShellGet</span></span>

<span data-ttu-id="f1471-113">Voer de volgende opdrachten uit vanuit een Power shell-sessie met verhoogde bevoegdheid om PowerShellGet te installeren op Windows 10, Windows Server 2016, een systeem met WMF 5,0 of 5,1 dat is geïnstalleerd of een systeem met Power shell 6.</span><span class="sxs-lookup"><span data-stu-id="f1471-113">To install PowerShellGet on Windows 10, Windows Server 2016, any system with WMF 5.0 or 5.1 installed, or any system with PowerShell 6, run the following commands from an elevated PowerShell session.</span></span>

```powershell
Install-Module -Name PowerShellGet -Force
Exit
```

<span data-ttu-id="f1471-114">Gebruiken `Update-Module` om nieuwere versies op te halen.</span><span class="sxs-lookup"><span data-stu-id="f1471-114">Use `Update-Module` to get newer versions.</span></span>

```powershell
Update-Module -Name PowerShellGet
Exit
```

### <a name="for-systems-running-powershell-3-or-powershell-4-that-have-installed-the-packagemanagement-preview"></a><span data-ttu-id="f1471-115">Voor systemen met Power Shell 3 of Power Shell 4 waarop de Package Management-preview is geïnstalleerd</span><span class="sxs-lookup"><span data-stu-id="f1471-115">For systems running PowerShell 3 or PowerShell 4, that have installed the PackageManagement Preview</span></span>

1. <span data-ttu-id="f1471-116">Gebruik `Save-Module` vanuit een Power shell-sessie met verhoogde bevoegdheid om de modules op te slaan in een lokale map.</span><span class="sxs-lookup"><span data-stu-id="f1471-116">From an elevated PowerShell session, use `Save-Module` to save the modules to a local directory.</span></span>

   ```powershell
   Save-Module -Name PowerShellGet -Path C:\LocalFolder
   Exit
   ```

1. <span data-ttu-id="f1471-117">Zorg ervoor dat de **PowerShellGet** -en **Package Management** -modules niet zijn geladen in andere processen.</span><span class="sxs-lookup"><span data-stu-id="f1471-117">Ensure that the **PowerShellGet** and **PackageManagement** modules aren't loaded in any other processes.</span></span>
1. <span data-ttu-id="f1471-118">Verwijder de inhoud van de mappen: `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` en `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\`.</span><span class="sxs-lookup"><span data-stu-id="f1471-118">Delete the contents of the folders: `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` and `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\`.</span></span>
1. <span data-ttu-id="f1471-119">Open de Power shell-console opnieuw met verhoogde machtigingen en voer de volgende opdrachten uit.</span><span class="sxs-lookup"><span data-stu-id="f1471-119">Reopen the PowerShell console with elevated permissions and run the following commands.</span></span>

   ```powershell
   Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
   Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force
   ```
