---
ms.date: 04/19/2021
ms.topic: reference
title: Het PSModulePath-installatiepad wijzigen
description: Het PSModulePath-installatiepad wijzigen
ms.openlocfilehash: 9ea72d9d9188876e5d9503f50a00332410e1ef90
ms.sourcegitcommit: 2ad76cd528338f8c2cc10a84c5c56c0e25b93436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/19/2021
ms.locfileid: "107729740"
---
# <a name="modifying-the-psmodulepath-installation-path"></a><span data-ttu-id="394c9-103">Het PSModulePath-installatiepad wijzigen</span><span class="sxs-lookup"><span data-stu-id="394c9-103">Modifying the PSModulePath Installation Path</span></span>

<span data-ttu-id="394c9-104">De `PSModulePath` omgevingsvariabele slaat de paden op naar de locaties van de modules die op schijf zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="394c9-104">The `PSModulePath` environment variable stores the paths to the locations of the modules that are installed on disk.</span></span> <span data-ttu-id="394c9-105">PowerShell gebruikt deze variabele om modules te zoeken wanneer de gebruiker niet het volledige pad naar een module opgeeft.</span><span class="sxs-lookup"><span data-stu-id="394c9-105">PowerShell uses this variable to locate modules when the user does not specify the full path to a module.</span></span> <span data-ttu-id="394c9-106">De paden in deze variabele worden doorzocht in de volgorde waarin ze worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="394c9-106">The paths in this variable are searched in the order in which they appear.</span></span>

<span data-ttu-id="394c9-107">Wanneer PowerShell wordt gestart, wordt gemaakt als een systeemomgevingsvariabele met de volgende standaardwaarde: in Windows en op Linux of Mac, en `PSModulePath` `$HOME\Documents\PowerShell\Modules; $PSHOME\Modules` voor `$HOME/.local/share/powershell/Modules: usr/local/share/powershell/Modules` `$HOME\Documents\WindowsPowerShell\Modules; $PSHOME\Modules` Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="394c9-107">When PowerShell starts, `PSModulePath` is created as a system environment variable with the following default value: `$HOME\Documents\PowerShell\Modules; $PSHOME\Modules` on Windows and `$HOME/.local/share/powershell/Modules: usr/local/share/powershell/Modules` on Linux or Mac, and `$HOME\Documents\WindowsPowerShell\Modules; $PSHOME\Modules` for Windows PowerShell.</span></span>

> [!NOTE]
> <span data-ttu-id="394c9-108">De gebruikersspecifieke **CurrentUser-locatie** is de map die zich `WindowsPowerShell\Modules` bevindt op de locatie **Documenten** in uw gebruikersprofiel.</span><span class="sxs-lookup"><span data-stu-id="394c9-108">The user-specific **CurrentUser** location is the `WindowsPowerShell\Modules` folder located in the **Documents** location in your user profile.</span></span> <span data-ttu-id="394c9-109">Het specifieke pad van die locatie varieert per versie van Windows en of u mapomleiding gebruikt.</span><span class="sxs-lookup"><span data-stu-id="394c9-109">The specific path of that location varies by version of Windows and whether or not you are using folder redirection.</span></span> <span data-ttu-id="394c9-110">Standaard is Windows 10 locatie `$HOME\Documents\WindowsPowerShell\Modules` .</span><span class="sxs-lookup"><span data-stu-id="394c9-110">By default, on Windows 10, that location is `$HOME\Documents\WindowsPowerShell\Modules`.</span></span>

## <a name="to-view-the-psmodulepath-variable"></a><span data-ttu-id="394c9-111">De variabele PSModulePath weergeven</span><span class="sxs-lookup"><span data-stu-id="394c9-111">To view the PSModulePath variable</span></span>

<span data-ttu-id="394c9-112">Als u de paden die zijn opgegeven in de variabele `PSModulePath` wilt weergeven, typt u de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="394c9-112">To view the paths that are specified in the `PSModulePath` variable, type the following command:</span></span>

`$env:PSModulePath`

## <a name="to-add-locations-to-the-psmodulepath-variable"></a><span data-ttu-id="394c9-113">Locaties toevoegen aan de variabele PSModulePath</span><span class="sxs-lookup"><span data-stu-id="394c9-113">To add locations to the PSModulePath variable</span></span>

<span data-ttu-id="394c9-114">Als u paden wilt toevoegen aan deze variabele, gebruikt u een van de volgende methoden:</span><span class="sxs-lookup"><span data-stu-id="394c9-114">To add paths to this variable, use one of the following methods:</span></span>

- <span data-ttu-id="394c9-115">Als u een tijdelijke waarde wilt toevoegen die alleen beschikbaar is voor de huidige sessie, moet u de volgende opdracht uitvoeren op de opdrachtregel:</span><span class="sxs-lookup"><span data-stu-id="394c9-115">To add a temporary value that is available only for the current session, run the following command at the command line:</span></span>

  `$env:PSModulePath = $env:PSModulePath + "$([System.IO.Path]::PathSeparator)$MyModulePath"`

- <span data-ttu-id="394c9-116">Als u een permanente waarde wilt toevoegen die beschikbaar is wanneer een sessie wordt geopend, voegt u de bovenstaande opdracht toe aan een PowerShell-profielbestand ( `$PROFILE` )></span><span class="sxs-lookup"><span data-stu-id="394c9-116">To add a persistent value that is available whenever a session is opened, add the above command to a PowerShell profile file (`$PROFILE`)></span></span>

  <span data-ttu-id="394c9-117">Zie voor meer informatie over [profielen about_Profiles.](/powershell/module/microsoft.powershell.core/about/about_profiles)</span><span class="sxs-lookup"><span data-stu-id="394c9-117">For more information about profiles, see [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles).</span></span>

- <span data-ttu-id="394c9-118">Als u een permanente variabele wilt toevoegen aan het register, maakt u een nieuwe gebruikersomgevingsvariabele met de naam met behulp van de Editor voor `PSModulePath` omgevingsvariabelen in **het** dialoogvenster Systeemeigenschappen.</span><span class="sxs-lookup"><span data-stu-id="394c9-118">To add a persistent variable to the registry, create a new user environment variable called `PSModulePath` using the Environment Variables Editor in the **System Properties** dialog box.</span></span>

- <span data-ttu-id="394c9-119">Als u een permanente variabele wilt toevoegen met behulp van een script, gebruikt u de .NET-methode [SetEnvironmentVariable](/dotnet/api/system.environment.setenvironmentvariable) in de [klasse System.Environment.](/dotnet/api/system.environment)</span><span class="sxs-lookup"><span data-stu-id="394c9-119">To add a persistent variable using a script, use the .NET method [SetEnvironmentVariable](/dotnet/api/system.environment.setenvironmentvariable) on the [System.Environment](/dotnet/api/system.environment) class.</span></span> <span data-ttu-id="394c9-120">Met het volgende script wordt bijvoorbeeld het `C:\Program Files\Fabrikam\Module` pad toegevoegd aan de waarde van de `PSModulePath` omgevingsvariabele voor de computer.</span><span class="sxs-lookup"><span data-stu-id="394c9-120">For example, the following script adds the `C:\Program Files\Fabrikam\Module` path to the value of the `PSModulePath` environment variable for the computer.</span></span> <span data-ttu-id="394c9-121">Als u het pad wilt toevoegen aan de `PSModulePath` omgevingsvariabele van de gebruiker, stelt u het doel in op 'Gebruiker'.</span><span class="sxs-lookup"><span data-stu-id="394c9-121">To add the path to the user `PSModulePath` environment variable, set the target to "User".</span></span>

  ```powershell
  $CurrentValue = [Environment]::GetEnvironmentVariable("PSModulePath", "Machine")
  [Environment]::SetEnvironmentVariable("PSModulePath", $CurrentValue + [System.IO.Path]::PathSeparator + "C:\Program Files\Fabrikam\Modules", "Machine")
  ```

<span data-ttu-id="394c9-122">U kunt ook de waarden `PSModulePath` in het `powershell.config.json` configuratiebestand instellen.</span><span class="sxs-lookup"><span data-stu-id="394c9-122">You may also set the `PSModulePath` values in the `powershell.config.json` configuration file.</span></span> <span data-ttu-id="394c9-123">Zie voor meer informatie [about_PowerShell_Config](/powershell/module/microsoft.powershell.core/about/about_powershell_config#psmodulepath).</span><span class="sxs-lookup"><span data-stu-id="394c9-123">For more information, see [about_PowerShell_Config](/powershell/module/microsoft.powershell.core/about/about_powershell_config#psmodulepath).</span></span>

## <a name="to-remove-locations-from-the-psmodulepath"></a><span data-ttu-id="394c9-124">Locaties verwijderen uit het PSModulePath</span><span class="sxs-lookup"><span data-stu-id="394c9-124">To remove locations from the PSModulePath</span></span>

<span data-ttu-id="394c9-125">U kunt paden uit de variabele verwijderen met behulp van vergelijkbare methoden.</span><span class="sxs-lookup"><span data-stu-id="394c9-125">You can remove paths from the variable using similar methods.</span></span> <span data-ttu-id="394c9-126">In het volgende voorbeeld wordt het `C:\ModulePath` pad uit de huidige sessie verwijderd.</span><span class="sxs-lookup"><span data-stu-id="394c9-126">The following example removes the `C:\ModulePath` path from the current session.</span></span>

```powershell
$env:PSModulePath = $env:PSModulePath -replace "$([System.IO.Path]::PathSeparator)c:\\ModulePath"`
```

<span data-ttu-id="394c9-127">Als u deze wijziging permanent wilt maken voor alle PowerShell-sessies, gebruikt u de .NET-methode zoals eerder is uitgelegd.</span><span class="sxs-lookup"><span data-stu-id="394c9-127">To make this change persistent for all PowerShell sessions, use the .NET method as explained previously.</span></span>

```powershell
[Environment]::SetEnvironmentVariable("PSModulePath", $env:PSModulePath, "Machine")
```

## <a name="see-also"></a><span data-ttu-id="394c9-128">Zie ook</span><span class="sxs-lookup"><span data-stu-id="394c9-128">See Also</span></span>

[<span data-ttu-id="394c9-129">Een Windows PowerShell-module schrijven</span><span class="sxs-lookup"><span data-stu-id="394c9-129">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)

[<span data-ttu-id="394c9-130">about_Modules</span><span class="sxs-lookup"><span data-stu-id="394c9-130">about_Modules</span></span>](/powershell/module/microsoft.powershell.core/about/about_modules)
