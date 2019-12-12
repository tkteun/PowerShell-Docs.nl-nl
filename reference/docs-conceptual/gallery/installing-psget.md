---
ms.date: 09/19/2019
contributor: manikb
keywords: Galerie, Power shell, cmdlet, psget
title: PowerShellGet installeren
ms.openlocfilehash: 69dc851c54089b47fb19e5b32990d579d26effb9
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "71328978"
---
# <a name="installing-powershellget"></a><span data-ttu-id="26fc5-103">PowerShellGet installeren</span><span class="sxs-lookup"><span data-stu-id="26fc5-103">Installing PowerShellGet</span></span>

## <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a><span data-ttu-id="26fc5-104">PowerShellGet is een in-box-module in de volgende releases</span><span class="sxs-lookup"><span data-stu-id="26fc5-104">PowerShellGet is an in-box module in the following releases</span></span>

- <span data-ttu-id="26fc5-105">[Windows 10](https://www.microsoft.com/windows) of hoger</span><span class="sxs-lookup"><span data-stu-id="26fc5-105">[Windows 10](https://www.microsoft.com/windows) or newer</span></span>
- <span data-ttu-id="26fc5-106">[Windows Server 2016](/windows-server/windows-server) of hoger</span><span class="sxs-lookup"><span data-stu-id="26fc5-106">[Windows Server 2016](/windows-server/windows-server) or newer</span></span>
- <span data-ttu-id="26fc5-107">[Windows Management Framework (WMF) 5,0](https://www.microsoft.com/download/details.aspx?id=50395) of hoger</span><span class="sxs-lookup"><span data-stu-id="26fc5-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) or newer</span></span>
- [<span data-ttu-id="26fc5-108">Power shell 6</span><span class="sxs-lookup"><span data-stu-id="26fc5-108">PowerShell 6</span></span>](https://github.com/PowerShell/PowerShell/releases)

## <a name="get-the-latest-version-from-powershell-gallery"></a><span data-ttu-id="26fc5-109">De nieuwste versie van PowerShell Gallery ophalen</span><span class="sxs-lookup"><span data-stu-id="26fc5-109">Get the latest version from PowerShell Gallery</span></span>

<span data-ttu-id="26fc5-110">Voordat u **PowerShellGet**bijwerkt, moet u altijd de meest recente **NuGet** -provider installeren.</span><span class="sxs-lookup"><span data-stu-id="26fc5-110">Before updating **PowerShellGet**, you should always install the latest **NuGet** provider.</span></span> <span data-ttu-id="26fc5-111">Voer de volgende opdracht uit vanuit een Power shell-sessie met verhoogde bevoegdheden.</span><span class="sxs-lookup"><span data-stu-id="26fc5-111">From an elevated PowerShell session, run the following command.</span></span>

```powershell
Install-PackageProvider -Name NuGet -Force
Exit
```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a><span data-ttu-id="26fc5-112">Voor systemen met Power shell 5,0 (of hoger) kunt u de meest recente PowerShellGet installeren</span><span class="sxs-lookup"><span data-stu-id="26fc5-112">For systems with PowerShell 5.0 (or newer) you can install the latest PowerShellGet</span></span>

<span data-ttu-id="26fc5-113">Voer de volgende opdrachten uit vanuit een Power shell-sessie met verhoogde bevoegdheid om PowerShellGet te installeren op Windows 10, Windows Server 2016, een systeem met WMF 5,0 of 5,1 dat is geïnstalleerd of een systeem met Power shell 6.</span><span class="sxs-lookup"><span data-stu-id="26fc5-113">To install PowerShellGet on Windows 10, Windows Server 2016, any system with WMF 5.0 or 5.1 installed, or any system with PowerShell 6, run the following commands from an elevated PowerShell session.</span></span>

```powershell
Install-Module -Name PowerShellGet -Force
Exit
```

<span data-ttu-id="26fc5-114">Gebruik `Update-Module` om nieuwere versies op te halen.</span><span class="sxs-lookup"><span data-stu-id="26fc5-114">Use `Update-Module` to get newer versions.</span></span>

```powershell
Update-Module -Name PowerShellGet
Exit
```

### <a name="for-computers-running-powershell-30-or-powershell-40"></a><span data-ttu-id="26fc5-115">Voor computers met Power Shell 3,0 of Power Shell 4,0</span><span class="sxs-lookup"><span data-stu-id="26fc5-115">For computers running PowerShell 3.0 or PowerShell 4.0</span></span>

<span data-ttu-id="26fc5-116">Deze instructies zijn van toepassing op computers waarop de **Package Management-preview** is geïnstalleerd of waarvoor geen versie van **PowerShellGet** is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="26fc5-116">These instructions apply to computers that have the **PackageManagement Preview** installed or don't have any version of **PowerShellGet** installed.</span></span>

<span data-ttu-id="26fc5-117">De cmdlet `Save-Module` wordt gebruikt in beide sets instructies.</span><span class="sxs-lookup"><span data-stu-id="26fc5-117">The `Save-Module` cmdlet is used in both sets of instructions.</span></span> <span data-ttu-id="26fc5-118">`Save-Module` downloadt en slaat een module en eventuele afhankelijkheden op uit een geregistreerde opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="26fc5-118">`Save-Module` downloads and saves a module and any dependencies from a registered repository.</span></span> <span data-ttu-id="26fc5-119">De meest recente versie van de module wordt opgeslagen op een opgegeven pad op de lokale computer, maar is niet geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="26fc5-119">The module's most current version is saved to a specified path on the local computer, but isn't installed.</span></span> <span data-ttu-id="26fc5-120">Zie [Save-module](/powershell/module/PowershellGet/Save-Module)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="26fc5-120">For more information, see [Save-Module](/powershell/module/PowershellGet/Save-Module).</span></span>

#### <a name="computers-with-the-packagemanagement-preview-installed"></a><span data-ttu-id="26fc5-121">Computers waarop het package management-voor beeld is geïnstalleerd</span><span class="sxs-lookup"><span data-stu-id="26fc5-121">Computers with the PackageManagement Preview installed</span></span>

1. <span data-ttu-id="26fc5-122">Gebruik `Save-Module` uit een Power shell-sessie om de modules op te slaan in een lokale map.</span><span class="sxs-lookup"><span data-stu-id="26fc5-122">From a PowerShell session, use `Save-Module` to save the modules to a local directory.</span></span>

   ```powershell
   Save-Module -Name PowerShellGet -Path C:\LocalFolder -Repository PSGallery
   ```

1. <span data-ttu-id="26fc5-123">Zorg ervoor dat de **PowerShellGet** -en **Package Management** -modules niet zijn geladen in andere processen.</span><span class="sxs-lookup"><span data-stu-id="26fc5-123">Ensure that the **PowerShellGet** and **PackageManagement** modules aren't loaded in any other processes.</span></span>
1. <span data-ttu-id="26fc5-124">Verwijder de inhoud van de mappen: `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` en `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\`.</span><span class="sxs-lookup"><span data-stu-id="26fc5-124">Delete the contents of the folders: `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` and `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\`.</span></span>
1. <span data-ttu-id="26fc5-125">Open de Power shell-console opnieuw met verhoogde machtigingen en voer de volgende opdrachten uit.</span><span class="sxs-lookup"><span data-stu-id="26fc5-125">Reopen the PowerShell console with elevated permissions and run the following commands.</span></span>

   ```powershell
   Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
   Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force
   ```

#### <a name="computers-without-powershellget"></a><span data-ttu-id="26fc5-126">Computers zonder PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="26fc5-126">Computers without PowerShellGet</span></span>

<span data-ttu-id="26fc5-127">Voor computers waarop geen versie van **PowerShellGet** is geïnstalleerd, is een computer met **PowerShellGet** geïnstalleerd nodig om de modules te downloaden.</span><span class="sxs-lookup"><span data-stu-id="26fc5-127">For computer's without any version of **PowerShellGet** installed, a computer with **PowerShellGet** installed is needed to download the modules.</span></span>

1. <span data-ttu-id="26fc5-128">Gebruik `Save-Module` om de huidige versie van **PowerShellGet**te downloaden van de computer waarop **PowerShellGet** is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="26fc5-128">From the computer that has **PowerShellGet** installed, use `Save-Module` to download the current version of **PowerShellGet**.</span></span> <span data-ttu-id="26fc5-129">Er worden twee mappen gedownload: **PowerShellGet** en **Package Management**.</span><span class="sxs-lookup"><span data-stu-id="26fc5-129">Two folders are downloaded: **PowerShellGet** and **PackageManagement**.</span></span> <span data-ttu-id="26fc5-130">Elke map bevat een submap met een versie nummer.</span><span class="sxs-lookup"><span data-stu-id="26fc5-130">Each folder contains a subfolder with a version number.</span></span>

   ```powershell
   Save-Module -Name PowerShellGet -Path C:\LocalFolder -Repository PSGallery
   ```

1. <span data-ttu-id="26fc5-131">Kopieer de mappen **PowerShellGet** en **Package Management** naar de computer waarop geen **PowerShellGet** is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="26fc5-131">Copy the **PowerShellGet** and **PackageManagement** folders to the computer that doesn't have **PowerShellGet** installed.</span></span>

   <span data-ttu-id="26fc5-132">De doelmap is: `$env:ProgramFiles\WindowsPowerShell\Modules`</span><span class="sxs-lookup"><span data-stu-id="26fc5-132">The destination directory is: `$env:ProgramFiles\WindowsPowerShell\Modules`</span></span>
