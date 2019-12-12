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
ms.openlocfilehash: 5957ea4c15cd3778bd09b67c4b97de0ef0cfdd2a
ms.sourcegitcommit: 0e4c69d8b5cf71431592fe41da816dec9b70f1f9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/09/2019
ms.locfileid: "74953837"
---
# <a name="modifying-the-psmodulepath-installation-path"></a><span data-ttu-id="c35ec-102">Het PSModulePath-installatiepad wijzigen</span><span class="sxs-lookup"><span data-stu-id="c35ec-102">Modifying the PSModulePath Installation Path</span></span>

<span data-ttu-id="c35ec-103">De variabele `PSModulePath` omgeving slaat de paden op naar de locaties van de modules die op schijf zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="c35ec-103">The `PSModulePath` environment variable stores the paths to the locations of the modules that are installed on disk.</span></span> <span data-ttu-id="c35ec-104">Power shell gebruikt deze variabele om modules te zoeken wanneer de gebruiker niet het volledige pad naar een module opgeeft.</span><span class="sxs-lookup"><span data-stu-id="c35ec-104">PowerShell uses this variable to locate modules when the user does not specify the full path to a module.</span></span> <span data-ttu-id="c35ec-105">De paden in deze variabele worden doorzocht in de volg orde waarin ze worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c35ec-105">The paths in this variable are searched in the order in which they appear.</span></span>

<span data-ttu-id="c35ec-106">Wanneer Power shell wordt gestart, wordt `PSModulePath` gemaakt als een systeem omgevingsvariabele met de volgende standaard waarde: `$HOME\Documents\PowerShell\Modules; $PSHOME\Modules` of `$HOME\Documents\WindowsPowerShell\Modules; $PSHOME\Modules` voor Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="c35ec-106">When PowerShell starts, `PSModulePath` is created as a system environment variable with the following default value: `$HOME\Documents\PowerShell\Modules; $PSHOME\Modules` or `$HOME\Documents\WindowsPowerShell\Modules; $PSHOME\Modules` for Windows PowerShell.</span></span>

## <a name="to-view-the-psmodulepath-variable"></a><span data-ttu-id="c35ec-107">De variabele PSModulePath weer geven</span><span class="sxs-lookup"><span data-stu-id="c35ec-107">To view the PSModulePath variable</span></span>

<span data-ttu-id="c35ec-108">Als u de paden wilt weer geven die zijn opgegeven in de variabele `PSModulePath`, typt u de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="c35ec-108">To view the paths that are specified in the `PSModulePath` variable, type the following command:</span></span>

`$env:PSModulePath`

## <a name="to-add-locations-to-the-psmodulepath-variable"></a><span data-ttu-id="c35ec-109">Locaties toevoegen aan de variabele PSModulePath</span><span class="sxs-lookup"><span data-stu-id="c35ec-109">To add locations to the PSModulePath variable</span></span>

<span data-ttu-id="c35ec-110">Gebruik een van de volgende methoden om paden aan deze variabele toe te voegen:</span><span class="sxs-lookup"><span data-stu-id="c35ec-110">To add paths to this variable, use one of the following methods:</span></span>

- <span data-ttu-id="c35ec-111">Als u een tijdelijke waarde wilt toevoegen die alleen beschikbaar is voor de huidige sessie, voert u de volgende opdracht uit op de opdracht regel:</span><span class="sxs-lookup"><span data-stu-id="c35ec-111">To add a temporary value that is available only for the current session, run the following command at the command line:</span></span>

  `$env:PSModulePath = $env:PSModulePath + "$([System.IO.Path]::PathSeparator)$MyModulePath"`

- <span data-ttu-id="c35ec-112">Als u een permanente waarde wilt toevoegen die beschikbaar is wanneer een sessie wordt geopend, voegt u de bovenstaande opdracht toe aan een Power shell-profiel bestand (`$PROFILE`) ></span><span class="sxs-lookup"><span data-stu-id="c35ec-112">To add a persistent value that is available whenever a session is opened, add the above command to a PowerShell profile file (`$PROFILE`)></span></span>

  <span data-ttu-id="c35ec-113">Zie [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles)voor meer informatie over profielen.</span><span class="sxs-lookup"><span data-stu-id="c35ec-113">For more information about profiles, see [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles).</span></span>

- <span data-ttu-id="c35ec-114">Als u een permanente variabele wilt toevoegen aan het REGI ster, maakt u een nieuwe gebruikers omgevings variabele met de naam `PSModulePath` met behulp van de editor voor omgevings variabelen in het dialoog venster **systeem eigenschappen** .</span><span class="sxs-lookup"><span data-stu-id="c35ec-114">To add a persistent variable to the registry, create a new user environment variable called `PSModulePath` using the Environment Variables Editor in the **System Properties** dialog box.</span></span>

- <span data-ttu-id="c35ec-115">Als u een permanente variabele wilt toevoegen met behulp van een script, gebruikt u de .net-methode [SetEnvironmentVariable](https://docs.microsoft.com/dotnet/api/system.environment.setenvironmentvariable) in de klasse [System. Environment](https://docs.microsoft.com/dotnet/api/system.environment) .</span><span class="sxs-lookup"><span data-stu-id="c35ec-115">To add a persistent variable by using a script, use the .Net method [SetEnvironmentVariable](https://docs.microsoft.com/dotnet/api/system.environment.setenvironmentvariable) on the [System.Environment](https://docs.microsoft.com/dotnet/api/system.environment) class.</span></span> <span data-ttu-id="c35ec-116">Het volgende script voegt bijvoorbeeld het `C:\Program Files\Fabrikam\Module` pad toe aan de waarde van de omgevings variabele `PSModulePath` voor de computer.</span><span class="sxs-lookup"><span data-stu-id="c35ec-116">For example, the following script adds the `C:\Program Files\Fabrikam\Module` path to the value of the `PSModulePath` environment variable for the computer.</span></span> <span data-ttu-id="c35ec-117">Als u het pad wilt toevoegen aan de gebruiker `PSModulePath` omgevings variabele, stelt u het doel in op ' gebruiker '.</span><span class="sxs-lookup"><span data-stu-id="c35ec-117">To add the path to the user `PSModulePath` environment variable, set the target to "User".</span></span>

  ```powershell
  $CurrentValue = [Environment]::GetEnvironmentVariable("PSModulePath", "Machine")
  [Environment]::SetEnvironmentVariable("PSModulePath", $CurrentValue + [System.IO.Path]::PathSeparator + "C:\Program Files\Fabrikam\Modules", "Machine")

  ```

## <a name="to-remove-locations-from-the-psmodulepath"></a><span data-ttu-id="c35ec-118">Locaties verwijderen uit de PSModulePath</span><span class="sxs-lookup"><span data-stu-id="c35ec-118">To remove locations from the PSModulePath</span></span>

<span data-ttu-id="c35ec-119">U kunt paden uit de variabele verwijderen met soort gelijke methoden: `$env:PSModulePath = $env:PSModulePath -replace "$([System.IO.Path]::PathSeparator)c:\\ModulePath"` verwijdert bijvoorbeeld het pad **c:\ModulePath** uit de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="c35ec-119">You can remove paths from the variable using similar methods: for example, `$env:PSModulePath = $env:PSModulePath -replace "$([System.IO.Path]::PathSeparator)c:\\ModulePath"` will remove the **c:\ModulePath** path from the current session.</span></span>

## <a name="see-also"></a><span data-ttu-id="c35ec-120">Zie ook</span><span class="sxs-lookup"><span data-stu-id="c35ec-120">See Also</span></span>

[<span data-ttu-id="c35ec-121">Een Windows Power shell-module schrijven</span><span class="sxs-lookup"><span data-stu-id="c35ec-121">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)
