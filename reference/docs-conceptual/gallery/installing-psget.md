---
ms.date: 09/19/2019
title: PowerShellGet installeren
description: In dit artikel wordt uitgelegd hoe u de PowerShellGet-module installeert in verschillende versies van Power shell.
ms.openlocfilehash: 06ec331446849784bb8464912fbce0e5a940823f
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92662143"
---
# <a name="installing-powershellget"></a><span data-ttu-id="1f7f9-103">PowerShellGet installeren</span><span class="sxs-lookup"><span data-stu-id="1f7f9-103">Installing PowerShellGet</span></span>

## <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a><span data-ttu-id="1f7f9-104">PowerShellGet is een in-box-module in de volgende releases</span><span class="sxs-lookup"><span data-stu-id="1f7f9-104">PowerShellGet is an in-box module in the following releases</span></span>

- <span data-ttu-id="1f7f9-105">[Windows 10](https://www.microsoft.com/windows) of hoger</span><span class="sxs-lookup"><span data-stu-id="1f7f9-105">[Windows 10](https://www.microsoft.com/windows) or newer</span></span>
- <span data-ttu-id="1f7f9-106">[Windows Server 2016](/windows-server/windows-server) of hoger</span><span class="sxs-lookup"><span data-stu-id="1f7f9-106">[Windows Server 2016](/windows-server/windows-server) or newer</span></span>
- <span data-ttu-id="1f7f9-107">[Windows Management Framework (WMF) 5,0](https://www.microsoft.com/download/details.aspx?id=50395) of hoger</span><span class="sxs-lookup"><span data-stu-id="1f7f9-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) or newer</span></span>
- [<span data-ttu-id="1f7f9-108">Power shell 6</span><span class="sxs-lookup"><span data-stu-id="1f7f9-108">PowerShell 6</span></span>](https://github.com/PowerShell/PowerShell/releases)

## <a name="get-the-latest-version-from-powershell-gallery"></a><span data-ttu-id="1f7f9-109">De nieuwste versie van PowerShell Gallery ophalen</span><span class="sxs-lookup"><span data-stu-id="1f7f9-109">Get the latest version from PowerShell Gallery</span></span>

<span data-ttu-id="1f7f9-110">Voordat u **PowerShellGet** bijwerkt, moet u altijd de meest recente **NuGet** -provider installeren.</span><span class="sxs-lookup"><span data-stu-id="1f7f9-110">Before updating **PowerShellGet** , you should always install the latest **NuGet** provider.</span></span> <span data-ttu-id="1f7f9-111">Voer de volgende opdracht uit vanuit een Power shell-sessie met verhoogde bevoegdheden.</span><span class="sxs-lookup"><span data-stu-id="1f7f9-111">From an elevated PowerShell session, run the following command.</span></span>

```powershell
Install-PackageProvider -Name NuGet -Force
```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a><span data-ttu-id="1f7f9-112">Voor systemen met Power shell 5,0 (of hoger) kunt u de meest recente PowerShellGet installeren</span><span class="sxs-lookup"><span data-stu-id="1f7f9-112">For systems with PowerShell 5.0 (or newer) you can install the latest PowerShellGet</span></span>

<span data-ttu-id="1f7f9-113">Voer de volgende opdrachten uit vanuit een Power shell-sessie met verhoogde bevoegdheid om PowerShellGet te installeren op Windows 10, Windows Server 2016, een systeem met WMF 5,0 of 5,1 dat is geïnstalleerd of een systeem met Power shell 6.</span><span class="sxs-lookup"><span data-stu-id="1f7f9-113">To install PowerShellGet on Windows 10, Windows Server 2016, any system with WMF 5.0 or 5.1 installed, or any system with PowerShell 6, run the following commands from an elevated PowerShell session.</span></span>

```powershell
Install-Module -Name PowerShellGet -Force
```

<span data-ttu-id="1f7f9-114">Gebruiken `Update-Module` om nieuwere versies op te halen.</span><span class="sxs-lookup"><span data-stu-id="1f7f9-114">Use `Update-Module` to get newer versions.</span></span>

```powershell
Update-Module -Name PowerShellGet
Exit
```

### <a name="for-computers-running-powershell-30-or-powershell-40"></a><span data-ttu-id="1f7f9-115">Voor computers met Power Shell 3,0 of Power Shell 4,0</span><span class="sxs-lookup"><span data-stu-id="1f7f9-115">For computers running PowerShell 3.0 or PowerShell 4.0</span></span>

<span data-ttu-id="1f7f9-116">Deze instructies zijn van toepassing op computers waarop de **Package Management-preview** is geïnstalleerd of waarvoor geen versie van **PowerShellGet** is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="1f7f9-116">These instructions apply to computers that have the **PackageManagement Preview** installed or don't have any version of **PowerShellGet** installed.</span></span>

<span data-ttu-id="1f7f9-117">De `Save-Module` cmdlet wordt gebruikt in beide sets instructies.</span><span class="sxs-lookup"><span data-stu-id="1f7f9-117">The `Save-Module` cmdlet is used in both sets of instructions.</span></span> <span data-ttu-id="1f7f9-118">`Save-Module` Hiermee worden een module en eventuele afhankelijkheden uit een geregistreerde opslag plaats gedownload en opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="1f7f9-118">`Save-Module` downloads and saves a module and any dependencies from a registered repository.</span></span> <span data-ttu-id="1f7f9-119">De meest recente versie van de module wordt opgeslagen op een opgegeven pad op de lokale computer, maar is niet geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="1f7f9-119">The module's most current version is saved to a specified path on the local computer, but isn't installed.</span></span> <span data-ttu-id="1f7f9-120">Als u de modules in Power Shell 3,0 of 4,0 wilt installeren, kopieert u de mappen in de module opgeslagen naar `$env:ProgramFiles\WindowsPowerShell\Modules` .</span><span class="sxs-lookup"><span data-stu-id="1f7f9-120">To install the modules in PowerShell 3.0 or 4.0, copy the module saved folders to `$env:ProgramFiles\WindowsPowerShell\Modules`.</span></span>

<span data-ttu-id="1f7f9-121">Zie [Save-module](/powershell/module/PowershellGet/Save-Module)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="1f7f9-121">For more information, see [Save-Module](/powershell/module/PowershellGet/Save-Module).</span></span>

> [!NOTE]
> <span data-ttu-id="1f7f9-122">Power Shell 3,0 en Power Shell 4,0 ondersteunen slechts één versie van een module.</span><span class="sxs-lookup"><span data-stu-id="1f7f9-122">PowerShell 3.0 and PowerShell 4.0 only supported one version of a module.</span></span> <span data-ttu-id="1f7f9-123">Vanaf Power shell 5,0 worden modules geïnstalleerd in `<modulename>\<version>` .</span><span class="sxs-lookup"><span data-stu-id="1f7f9-123">Starting in PowerShell 5.0, modules are installed in `<modulename>\<version>`.</span></span> <span data-ttu-id="1f7f9-124">Zo kunt u meerdere versies naast elkaar installeren.</span><span class="sxs-lookup"><span data-stu-id="1f7f9-124">This allows you to install multiple versions side-by-side.</span></span> <span data-ttu-id="1f7f9-125">Nadat u de module hebt gedownload met behulp `Save-Module` van, moet u de bestanden kopiëren van de `<modulename>\<version>` naar de `<modulename>` map op de doel computer, zoals wordt weer gegeven in de onderstaande instructies.</span><span class="sxs-lookup"><span data-stu-id="1f7f9-125">After downloading the module using `Save-Module` you must copy the files from the `<modulename>\<version>` to the `<modulename>` folder on the destination machine, as shown in the instructions below.</span></span>

#### <a name="preparatory-step-on-computers-running-powershell-30"></a><span data-ttu-id="1f7f9-126">Voorbereidende stap op computers met Power Shell 3,0</span><span class="sxs-lookup"><span data-stu-id="1f7f9-126">Preparatory Step on computers running PowerShell 3.0</span></span>

<span data-ttu-id="1f7f9-127">Met de instructies in de volgende secties worden de modules in Directory geïnstalleerd `$env:ProgramFiles\WindowsPowerShell\Modules` .</span><span class="sxs-lookup"><span data-stu-id="1f7f9-127">The instructions in the sections below install the modules in directory `$env:ProgramFiles\WindowsPowerShell\Modules`.</span></span>
<span data-ttu-id="1f7f9-128">In Power Shell 3,0 wordt deze map niet `$env:PSModulePath` standaard vermeld, dus moet u deze toevoegen om de modules automatisch te laden.</span><span class="sxs-lookup"><span data-stu-id="1f7f9-128">In PowerShell 3.0, this directory isn't listed in `$env:PSModulePath` by default, so you'll need to add it in order for the modules to be auto-loaded.</span></span>

<span data-ttu-id="1f7f9-129">Open een Power shell-sessie met verhoogde bevoegdheden en voer de volgende opdracht uit (die wordt toegepast tijdens toekomstige sessies):</span><span class="sxs-lookup"><span data-stu-id="1f7f9-129">Open an elevated PowerShell session and run the following command (which will take effect in future sessions):</span></span>

```powershell
[Environment]::SetEnvironmentVariable(
  'PSModulePath',
  ((([Environment]::GetEnvironmentVariable('PSModulePath', 'Machine') -split ';') + "$env:ProgramFiles\WindowsPowerShell\Modules") -join ';'),
  'Machine'
)
```

#### <a name="computers-with-the-packagemanagement-preview-installed"></a><span data-ttu-id="1f7f9-130">Computers waarop het package management-voor beeld is geïnstalleerd</span><span class="sxs-lookup"><span data-stu-id="1f7f9-130">Computers with the PackageManagement Preview installed</span></span>

> [!NOTE]
> <span data-ttu-id="1f7f9-131">De preview-versie van Package Management is een downloadbaar onderdeel dat PowerShellGet beschikbaar maakte voor Power shell-versie 3 en 4, maar niet langer beschikbaar is.</span><span class="sxs-lookup"><span data-stu-id="1f7f9-131">PackageManagement Preview was a downloadable component that made PowerShellGet available to PowerShell versions 3 and 4, but it is no longer available.</span></span>
> <span data-ttu-id="1f7f9-132">Voer uit om te testen of het op een bepaalde computer is geïnstalleerd `Get-Module -ListAvailable PowerShellGet` .</span><span class="sxs-lookup"><span data-stu-id="1f7f9-132">To test if it was installed on a given computer, run `Get-Module -ListAvailable PowerShellGet`.</span></span>

1. <span data-ttu-id="1f7f9-133">Gebruik vanuit een Power shell-sessie `Save-Module` om de huidige versie van **PowerShellGet** te downloaden.</span><span class="sxs-lookup"><span data-stu-id="1f7f9-133">From a PowerShell session, use `Save-Module` to download the current version of **PowerShellGet** .</span></span> <span data-ttu-id="1f7f9-134">Er worden twee mappen gedownload: **PowerShellGet** en **Package Management** .</span><span class="sxs-lookup"><span data-stu-id="1f7f9-134">Two folders are downloaded: **PowerShellGet** and **PackageManagement** .</span></span> <span data-ttu-id="1f7f9-135">Elke map bevat een submap met een versie nummer.</span><span class="sxs-lookup"><span data-stu-id="1f7f9-135">Each folder contains a subfolder with a version number.</span></span>

   ```powershell
   Save-Module -Name PowerShellGet -Path C:\LocalFolder -Repository PSGallery
   ```

1. <span data-ttu-id="1f7f9-136">Zorg ervoor dat de **PowerShellGet** -en **Package Management** -modules niet zijn geladen in andere processen.</span><span class="sxs-lookup"><span data-stu-id="1f7f9-136">Ensure that the **PowerShellGet** and **PackageManagement** modules aren't loaded in any other processes.</span></span>

1. <span data-ttu-id="1f7f9-137">Open de Power shell-console opnieuw met verhoogde machtigingen en voer de volgende opdracht uit.</span><span class="sxs-lookup"><span data-stu-id="1f7f9-137">Reopen the PowerShell console with elevated permissions and run the following command.</span></span>

   ```powershell
   'PowerShellGet', 'PackageManagement' | % {
     $targetDir = "$env:ProgramFiles\WindowsPowerShell\Modules\$_"
     Remove-Item $targetDir\* -Recurse -Force
     Copy-Item C:\LocalFolder\$_\*\* $targetDir\ -Recurse -Force
   }
   ```

#### <a name="computers-without-powershellget"></a><span data-ttu-id="1f7f9-138">Computers zonder PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="1f7f9-138">Computers without PowerShellGet</span></span>

<span data-ttu-id="1f7f9-139">Voor computers waarop geen versie van **PowerShellGet** is geïnstalleerd (testen met `Get-Module -ListAvailable PowerShellGet` ), is een computer met **PowerShellGet** geïnstalleerd nodig om de modules te downloaden.</span><span class="sxs-lookup"><span data-stu-id="1f7f9-139">For computers without any version of **PowerShellGet** installed (test with `Get-Module -ListAvailable PowerShellGet`), a computer with **PowerShellGet** installed is needed to download the modules.</span></span>

1. <span data-ttu-id="1f7f9-140">Op de computer waarop **PowerShellGet** is geïnstalleerd, gebruikt `Save-Module` u om de huidige versie van **PowerShellGet** te downloaden.</span><span class="sxs-lookup"><span data-stu-id="1f7f9-140">From the computer that has **PowerShellGet** installed, use `Save-Module` to download the current version of **PowerShellGet** .</span></span> <span data-ttu-id="1f7f9-141">Er worden twee mappen gedownload: **PowerShellGet** en **Package Management** .</span><span class="sxs-lookup"><span data-stu-id="1f7f9-141">Two folders are downloaded: **PowerShellGet** and **PackageManagement** .</span></span> <span data-ttu-id="1f7f9-142">Elke map bevat een submap met een versie nummer.</span><span class="sxs-lookup"><span data-stu-id="1f7f9-142">Each folder contains a subfolder with a version number.</span></span>

   ```powershell
   Save-Module -Name PowerShellGet -Path C:\LocalFolder -Repository PSGallery
   ```

1. <span data-ttu-id="1f7f9-143">Kopieer de desbetreffende `<version>` submap in de **PowerShellGet** -en **Package Management** -mappen naar de computer waarop geen **PowerShellGet** is geïnstalleerd, naar mappen `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` en `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` een verhoogde sessie.</span><span class="sxs-lookup"><span data-stu-id="1f7f9-143">Copy the respective `<version>` subfolder in the **PowerShellGet** and **PackageManagement** folders to the computer that doesn't have **PowerShellGet** installed, into folders `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` and `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` respectively, which requires an elevated session.</span></span>

1. <span data-ttu-id="1f7f9-144">Als u bijvoorbeeld toegang hebt tot de downloadmap op de andere computer, zegt u `ws1` , vanaf de doel computer via een UNC-pad, `\\ws1\C$\LocalFolder` een Power shell-console openen met verhoogde machtigingen en voert u de volgende opdracht uit:</span><span class="sxs-lookup"><span data-stu-id="1f7f9-144">For instance, if you can access the download folder on the other computer, say `ws1`, from the target computer via a UNC path, say `\\ws1\C$\LocalFolder`, open a PowerShell console with elevated permissions and run the following command:</span></span>

   ```powershell
   'PowerShellGet', 'PackageManagement' | % {
     $targetDir = "$env:ProgramFiles\WindowsPowerShell\Modules\$_"
     $null = New-Item -Type Directory -Force $targetDir
     $fromComputer = 'ws1'  # Specify the name of the other computer here.
     Copy-Item \\$fromComputer\C$\LocalFolder\$_\*\* $targetDir -Recurse -Force
     if (-not (Get-ChildItem $targetDir)) { Throw "Copying failed." }
   }
   ```
