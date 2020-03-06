---
title: Het installatiepad van PSModulePath wijzigen | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dc5ce5a2-50e9-4c88-abf1-ac148a8a6b7b
caps.latest.revision: 15
ms.openlocfilehash: b176d8439025ac132962859f79e72ae6f9703e82
ms.sourcegitcommit: 4a26c05f162c4fa347a9d67e339f8a33e230b9ba
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78405037"
---
# <a name="modifying-the-psmodulepath-installation-path"></a><span data-ttu-id="744a8-102">Het PSModulePath-installatiepad wijzigen</span><span class="sxs-lookup"><span data-stu-id="744a8-102">Modifying the PSModulePath Installation Path</span></span>

<span data-ttu-id="744a8-103">De variabele `PSModulePath` omgeving slaat de paden op naar de locaties van de modules die op schijf zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="744a8-103">The `PSModulePath` environment variable stores the paths to the locations of the modules that are installed on disk.</span></span> <span data-ttu-id="744a8-104">Power shell gebruikt deze variabele om modules te zoeken wanneer de gebruiker niet het volledige pad naar een module opgeeft.</span><span class="sxs-lookup"><span data-stu-id="744a8-104">PowerShell uses this variable to locate modules when the user does not specify the full path to a module.</span></span> <span data-ttu-id="744a8-105">De paden in deze variabele worden doorzocht in de volg orde waarin ze worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="744a8-105">The paths in this variable are searched in the order in which they appear.</span></span>

<span data-ttu-id="744a8-106">Wanneer Power shell wordt gestart, wordt `PSModulePath` gemaakt als een systeem omgevingsvariabele met de volgende standaard waarde: `$HOME\Documents\PowerShell\Modules; $PSHOME\Modules` op Windows en `$HOME/.local/share/powershell/Modules: usr/local/share/powershell/Modules` in Linux of Mac en `$HOME\Documents\WindowsPowerShell\Modules; $PSHOME\Modules` voor Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="744a8-106">When PowerShell starts, `PSModulePath` is created as a system environment variable with the following default value: `$HOME\Documents\PowerShell\Modules; $PSHOME\Modules` on Windows and `$HOME/.local/share/powershell/Modules: usr/local/share/powershell/Modules` on Linux or Mac, and `$HOME\Documents\WindowsPowerShell\Modules; $PSHOME\Modules` for Windows PowerShell.</span></span>

> [!NOTE]
> <span data-ttu-id="744a8-107">De gebruikerspecifieke locatie van **CurrentUser** is de `WindowsPowerShell\Modules` map die zich op de locatie van het **document** in uw gebruikers profiel bevindt.</span><span class="sxs-lookup"><span data-stu-id="744a8-107">The user-specific **CurrentUser** location is the `WindowsPowerShell\Modules` folder located in the **Documents** location in your user profile.</span></span> <span data-ttu-id="744a8-108">Het specifieke pad van die locatie is afhankelijk van de versie van Windows en of u nu Mapomleiding gebruikt.</span><span class="sxs-lookup"><span data-stu-id="744a8-108">The specific path of that location varies by version of Windows and whether or not you are using folder redirection.</span></span> <span data-ttu-id="744a8-109">Op Windows 10 is deze locatie standaard `$HOME\Documents\WindowsPowerShell\Modules`.</span><span class="sxs-lookup"><span data-stu-id="744a8-109">By default, on Windows 10, that location is `$HOME\Documents\WindowsPowerShell\Modules`.</span></span>

## <a name="to-view-the-psmodulepath-variable"></a><span data-ttu-id="744a8-110">De variabele PSModulePath weer geven</span><span class="sxs-lookup"><span data-stu-id="744a8-110">To view the PSModulePath variable</span></span>

<span data-ttu-id="744a8-111">Als u de paden wilt weer geven die zijn opgegeven in de variabele `PSModulePath`, typt u de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="744a8-111">To view the paths that are specified in the `PSModulePath` variable, type the following command:</span></span>

`$env:PSModulePath`

## <a name="to-add-locations-to-the-psmodulepath-variable"></a><span data-ttu-id="744a8-112">Locaties toevoegen aan de variabele PSModulePath</span><span class="sxs-lookup"><span data-stu-id="744a8-112">To add locations to the PSModulePath variable</span></span>

<span data-ttu-id="744a8-113">Gebruik een van de volgende methoden om paden aan deze variabele toe te voegen:</span><span class="sxs-lookup"><span data-stu-id="744a8-113">To add paths to this variable, use one of the following methods:</span></span>

- <span data-ttu-id="744a8-114">Als u een tijdelijke waarde wilt toevoegen die alleen beschikbaar is voor de huidige sessie, voert u de volgende opdracht uit op de opdracht regel:</span><span class="sxs-lookup"><span data-stu-id="744a8-114">To add a temporary value that is available only for the current session, run the following command at the command line:</span></span>

  `$env:PSModulePath = $env:PSModulePath + "$([System.IO.Path]::PathSeparator)$MyModulePath"`

- <span data-ttu-id="744a8-115">Als u een permanente waarde wilt toevoegen die beschikbaar is wanneer een sessie wordt geopend, voegt u de bovenstaande opdracht toe aan een Power shell-profiel bestand (`$PROFILE`) ></span><span class="sxs-lookup"><span data-stu-id="744a8-115">To add a persistent value that is available whenever a session is opened, add the above command to a PowerShell profile file (`$PROFILE`)></span></span>

  <span data-ttu-id="744a8-116">Zie [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles)voor meer informatie over profielen.</span><span class="sxs-lookup"><span data-stu-id="744a8-116">For more information about profiles, see [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles).</span></span>

- <span data-ttu-id="744a8-117">Als u een permanente variabele wilt toevoegen aan het REGI ster, maakt u een nieuwe gebruikers omgevings variabele met de naam `PSModulePath` met behulp van de editor voor omgevings variabelen in het dialoog venster **systeem eigenschappen** .</span><span class="sxs-lookup"><span data-stu-id="744a8-117">To add a persistent variable to the registry, create a new user environment variable called `PSModulePath` using the Environment Variables Editor in the **System Properties** dialog box.</span></span>

- <span data-ttu-id="744a8-118">Als u een permanente variabele wilt toevoegen met behulp van een script, gebruikt u de .net-methode [SetEnvironmentVariable](https://docs.microsoft.com/dotnet/api/system.environment.setenvironmentvariable) in de klasse [System. Environment](https://docs.microsoft.com/dotnet/api/system.environment) .</span><span class="sxs-lookup"><span data-stu-id="744a8-118">To add a persistent variable by using a script, use the .Net method [SetEnvironmentVariable](https://docs.microsoft.com/dotnet/api/system.environment.setenvironmentvariable) on the [System.Environment](https://docs.microsoft.com/dotnet/api/system.environment) class.</span></span> <span data-ttu-id="744a8-119">Het volgende script voegt bijvoorbeeld het `C:\Program Files\Fabrikam\Module` pad toe aan de waarde van de omgevings variabele `PSModulePath` voor de computer.</span><span class="sxs-lookup"><span data-stu-id="744a8-119">For example, the following script adds the `C:\Program Files\Fabrikam\Module` path to the value of the `PSModulePath` environment variable for the computer.</span></span> <span data-ttu-id="744a8-120">Als u het pad wilt toevoegen aan de gebruiker `PSModulePath` omgevings variabele, stelt u het doel in op ' gebruiker '.</span><span class="sxs-lookup"><span data-stu-id="744a8-120">To add the path to the user `PSModulePath` environment variable, set the target to "User".</span></span>

  ```powershell
  $CurrentValue = [Environment]::GetEnvironmentVariable("PSModulePath", "Machine")
  [Environment]::SetEnvironmentVariable("PSModulePath", $CurrentValue + [System.IO.Path]::PathSeparator + "C:\Program Files\Fabrikam\Modules", "Machine")

  ```

## <a name="to-remove-locations-from-the-psmodulepath"></a><span data-ttu-id="744a8-121">Locaties verwijderen uit de PSModulePath</span><span class="sxs-lookup"><span data-stu-id="744a8-121">To remove locations from the PSModulePath</span></span>

<span data-ttu-id="744a8-122">U kunt paden uit de variabele verwijderen met soort gelijke methoden: `$env:PSModulePath = $env:PSModulePath -replace "$([System.IO.Path]::PathSeparator)c:\\ModulePath"` verwijdert bijvoorbeeld het pad **c:\ModulePath** uit de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="744a8-122">You can remove paths from the variable using similar methods: for example, `$env:PSModulePath = $env:PSModulePath -replace "$([System.IO.Path]::PathSeparator)c:\\ModulePath"` will remove the **c:\ModulePath** path from the current session.</span></span>

## <a name="see-also"></a><span data-ttu-id="744a8-123">Zie ook</span><span class="sxs-lookup"><span data-stu-id="744a8-123">See Also</span></span>

[<span data-ttu-id="744a8-124">Een Windows Power shell-module schrijven</span><span class="sxs-lookup"><span data-stu-id="744a8-124">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)

[<span data-ttu-id="744a8-125">about_Modules</span><span class="sxs-lookup"><span data-stu-id="744a8-125">about_Modules</span></span>](/powershell/module/microsoft.powershell.core/about/about_modules)
