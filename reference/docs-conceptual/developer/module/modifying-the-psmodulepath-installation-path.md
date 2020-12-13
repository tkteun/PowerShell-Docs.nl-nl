---
ms.date: 09/13/2016
ms.topic: reference
title: Het PSModulePath-installatiepad wijzigen
description: Het PSModulePath-installatiepad wijzigen
ms.openlocfilehash: b802492bf9b49e8165e296817e3f80b9ae8265a6
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92661938"
---
# <a name="modifying-the-psmodulepath-installation-path"></a><span data-ttu-id="334f7-103">Het PSModulePath-installatiepad wijzigen</span><span class="sxs-lookup"><span data-stu-id="334f7-103">Modifying the PSModulePath Installation Path</span></span>

<span data-ttu-id="334f7-104">De `PSModulePath` omgevings variabele slaat de paden op naar de locaties van de modules die op schijf zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="334f7-104">The `PSModulePath` environment variable stores the paths to the locations of the modules that are installed on disk.</span></span> <span data-ttu-id="334f7-105">Power shell gebruikt deze variabele om modules te zoeken wanneer de gebruiker niet het volledige pad naar een module opgeeft.</span><span class="sxs-lookup"><span data-stu-id="334f7-105">PowerShell uses this variable to locate modules when the user does not specify the full path to a module.</span></span> <span data-ttu-id="334f7-106">De paden in deze variabele worden doorzocht in de volg orde waarin ze worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="334f7-106">The paths in this variable are searched in the order in which they appear.</span></span>

<span data-ttu-id="334f7-107">Wanneer Power shell wordt gestart, `PSModulePath` wordt gemaakt als een systeem omgevingsvariabele met de volgende standaard waarde: `$HOME\Documents\PowerShell\Modules; $PSHOME\Modules` in Windows en `$HOME/.local/share/powershell/Modules: usr/local/share/powershell/Modules` op Linux of Mac, en `$HOME\Documents\WindowsPowerShell\Modules; $PSHOME\Modules` voor Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="334f7-107">When PowerShell starts, `PSModulePath` is created as a system environment variable with the following default value: `$HOME\Documents\PowerShell\Modules; $PSHOME\Modules` on Windows and `$HOME/.local/share/powershell/Modules: usr/local/share/powershell/Modules` on Linux or Mac, and `$HOME\Documents\WindowsPowerShell\Modules; $PSHOME\Modules` for Windows PowerShell.</span></span>

> [!NOTE]
> <span data-ttu-id="334f7-108">De gebruikerspecifieke locatie van **CurrentUser** is de `WindowsPowerShell\Modules` map die zich bevindt op de locatie van **documenten** in uw gebruikers profiel.</span><span class="sxs-lookup"><span data-stu-id="334f7-108">The user-specific **CurrentUser** location is the `WindowsPowerShell\Modules` folder located in the **Documents** location in your user profile.</span></span> <span data-ttu-id="334f7-109">Het specifieke pad van die locatie is afhankelijk van de versie van Windows en of u nu Mapomleiding gebruikt.</span><span class="sxs-lookup"><span data-stu-id="334f7-109">The specific path of that location varies by version of Windows and whether or not you are using folder redirection.</span></span> <span data-ttu-id="334f7-110">Deze locatie is standaard op Windows 10 `$HOME\Documents\WindowsPowerShell\Modules` .</span><span class="sxs-lookup"><span data-stu-id="334f7-110">By default, on Windows 10, that location is `$HOME\Documents\WindowsPowerShell\Modules`.</span></span>

## <a name="to-view-the-psmodulepath-variable"></a><span data-ttu-id="334f7-111">De variabele PSModulePath weer geven</span><span class="sxs-lookup"><span data-stu-id="334f7-111">To view the PSModulePath variable</span></span>

<span data-ttu-id="334f7-112">Als u de opgegeven paden in de variabele wilt weer geven `PSModulePath` , typt u de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="334f7-112">To view the paths that are specified in the `PSModulePath` variable, type the following command:</span></span>

`$env:PSModulePath`

## <a name="to-add-locations-to-the-psmodulepath-variable"></a><span data-ttu-id="334f7-113">Locaties toevoegen aan de variabele PSModulePath</span><span class="sxs-lookup"><span data-stu-id="334f7-113">To add locations to the PSModulePath variable</span></span>

<span data-ttu-id="334f7-114">Gebruik een van de volgende methoden om paden aan deze variabele toe te voegen:</span><span class="sxs-lookup"><span data-stu-id="334f7-114">To add paths to this variable, use one of the following methods:</span></span>

- <span data-ttu-id="334f7-115">Als u een tijdelijke waarde wilt toevoegen die alleen beschikbaar is voor de huidige sessie, voert u de volgende opdracht uit op de opdracht regel:</span><span class="sxs-lookup"><span data-stu-id="334f7-115">To add a temporary value that is available only for the current session, run the following command at the command line:</span></span>

  `$env:PSModulePath = $env:PSModulePath + "$([System.IO.Path]::PathSeparator)$MyModulePath"`

- <span data-ttu-id="334f7-116">Als u een permanente waarde wilt toevoegen die beschikbaar is wanneer een sessie wordt geopend, voegt u de bovenstaande opdracht toe aan een Power shell-profiel bestand ( `$PROFILE` ) ></span><span class="sxs-lookup"><span data-stu-id="334f7-116">To add a persistent value that is available whenever a session is opened, add the above command to a PowerShell profile file (`$PROFILE`)></span></span>

  <span data-ttu-id="334f7-117">Zie [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles)voor meer informatie over profielen.</span><span class="sxs-lookup"><span data-stu-id="334f7-117">For more information about profiles, see [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles).</span></span>

- <span data-ttu-id="334f7-118">Als u een permanente variabele wilt toevoegen aan het REGI ster, maakt u een nieuwe gebruikers omgevings variabele `PSModulePath` met de naam met behulp van de editor voor omgevings variabelen in het dialoog venster **systeem eigenschappen** .</span><span class="sxs-lookup"><span data-stu-id="334f7-118">To add a persistent variable to the registry, create a new user environment variable called `PSModulePath` using the Environment Variables Editor in the **System Properties** dialog box.</span></span>

- <span data-ttu-id="334f7-119">Als u een permanente variabele wilt toevoegen met behulp van een script, gebruikt u de .net-methode [SetEnvironmentVariable](/dotnet/api/system.environment.setenvironmentvariable) in de klasse [System. Environment](/dotnet/api/system.environment) .</span><span class="sxs-lookup"><span data-stu-id="334f7-119">To add a persistent variable by using a script, use the .Net method [SetEnvironmentVariable](/dotnet/api/system.environment.setenvironmentvariable) on the [System.Environment](/dotnet/api/system.environment) class.</span></span> <span data-ttu-id="334f7-120">Het volgende script voegt bijvoorbeeld het `C:\Program Files\Fabrikam\Module` pad toe aan de waarde van de `PSModulePath` omgevings variabele voor de computer.</span><span class="sxs-lookup"><span data-stu-id="334f7-120">For example, the following script adds the `C:\Program Files\Fabrikam\Module` path to the value of the `PSModulePath` environment variable for the computer.</span></span> <span data-ttu-id="334f7-121">Als u het pad wilt toevoegen aan de variabele voor de gebruikers `PSModulePath` omgeving, stelt u het doel in op ' gebruiker '.</span><span class="sxs-lookup"><span data-stu-id="334f7-121">To add the path to the user `PSModulePath` environment variable, set the target to "User".</span></span>

  ```powershell
  $CurrentValue = [Environment]::GetEnvironmentVariable("PSModulePath", "Machine")
  [Environment]::SetEnvironmentVariable("PSModulePath", $CurrentValue + [System.IO.Path]::PathSeparator + "C:\Program Files\Fabrikam\Modules", "Machine")

  ```

## <a name="to-remove-locations-from-the-psmodulepath"></a><span data-ttu-id="334f7-122">Locaties verwijderen uit de PSModulePath</span><span class="sxs-lookup"><span data-stu-id="334f7-122">To remove locations from the PSModulePath</span></span>

<span data-ttu-id="334f7-123">U kunt paden uit de variabele verwijderen met soort gelijke methoden: als u bijvoorbeeld `$env:PSModulePath = $env:PSModulePath -replace "$([System.IO.Path]::PathSeparator)c:\\ModulePath"` het pad **c:\ModulePath** verwijdert uit de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="334f7-123">You can remove paths from the variable using similar methods: for example, `$env:PSModulePath = $env:PSModulePath -replace "$([System.IO.Path]::PathSeparator)c:\\ModulePath"` will remove the **c:\ModulePath** path from the current session.</span></span>

## <a name="see-also"></a><span data-ttu-id="334f7-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="334f7-124">See Also</span></span>

[<span data-ttu-id="334f7-125">Een Windows PowerShell-module schrijven</span><span class="sxs-lookup"><span data-stu-id="334f7-125">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)

[<span data-ttu-id="334f7-126">about_Modules</span><span class="sxs-lookup"><span data-stu-id="334f7-126">about_Modules</span></span>](/powershell/module/microsoft.powershell.core/about/about_modules)
