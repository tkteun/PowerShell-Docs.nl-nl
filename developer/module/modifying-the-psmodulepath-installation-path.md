---
title: Het installatiepad PSModulePath wijzigen | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dc5ce5a2-50e9-4c88-abf1-ac148a8a6b7b
caps.latest.revision: 15
ms.openlocfilehash: 639d3a28dd2af09fcc498caedc5fe74c1493445d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082206"
---
# <a name="modifying-the-psmodulepath-installation-path"></a><span data-ttu-id="23839-102">Het PSModulePath-installatiepad wijzigen</span><span class="sxs-lookup"><span data-stu-id="23839-102">Modifying the PSModulePath Installation Path</span></span>

<span data-ttu-id="23839-103">De `PSModulePath` omgevingsvariabele de paden naar de locaties van de modules die zijn geïnstalleerd op de schijf worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="23839-103">The `PSModulePath` environment variable stores the paths to the locations of the modules that are installed on disk.</span></span> <span data-ttu-id="23839-104">Windows PowerShell wordt deze variabele om te zoeken modules wanneer de gebruiker heeft niet het volledige pad naar een module opgeven.</span><span class="sxs-lookup"><span data-stu-id="23839-104">Windows PowerShell uses this variable to locate modules when the user does not specify the full path to a module.</span></span> <span data-ttu-id="23839-105">De paden in deze variabele wordt gezocht in de volgorde waarin ze worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="23839-105">The paths in this variable are searched in the order in which they appear.</span></span>

<span data-ttu-id="23839-106">Wanneer Windows PowerShell wordt gestart, `PSModulePath` gemaakt als een systeem-omgevingsvariabele met de volgende standaardwaarde: `$home\Documents\WindowsPowerShell\Modules; $pshome\Modules`.</span><span class="sxs-lookup"><span data-stu-id="23839-106">When Windows PowerShell starts, `PSModulePath` is created as a system environment variable with the following default value: `$home\Documents\WindowsPowerShell\Modules; $pshome\Modules`.</span></span>

## <a name="to-view-the-psmodulepath-variable"></a><span data-ttu-id="23839-107">Om de variabele PSModulePath weer te geven</span><span class="sxs-lookup"><span data-stu-id="23839-107">To view the PSModulePath variable</span></span>

<span data-ttu-id="23839-108">Om weer te geven van de paden die zijn opgegeven in de `PSModulePath` variabele, typt u de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="23839-108">To view the paths that are specified in the `PSModulePath` variable, type the following command:</span></span>

`$env:PSModulePath`

## <a name="to-add-locations-to-the-psmodulepath-variable"></a><span data-ttu-id="23839-109">Locaties toevoegen aan de variabele PSModulePath</span><span class="sxs-lookup"><span data-stu-id="23839-109">To add locations to the PSModulePath variable</span></span>

<span data-ttu-id="23839-110">Paden naar deze variabele toevoegen, moet u een van de volgende methoden gebruiken:</span><span class="sxs-lookup"><span data-stu-id="23839-110">To add paths to this variable, use one of the following methods:</span></span>

- <span data-ttu-id="23839-111">Als u wilt toevoegen een tijdelijke waarde die is alleen beschikbaar voor de huidige sessie, moet u de volgende opdracht uitvoeren op de opdrachtregel:</span><span class="sxs-lookup"><span data-stu-id="23839-111">To add a temporary value that is available only for the current session, run the following command at the command line:</span></span>

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

- <span data-ttu-id="23839-112">Als u wilt toevoegen een permanente waarde die beschikbaar is wanneer een sessie wordt geopend, toevoegen de volgende opdracht aan een Windows PowerShell-profiel:</span><span class="sxs-lookup"><span data-stu-id="23839-112">To add a persistent value that is available whenever a session is opened, add the following command to a Windows PowerShell profile:</span></span>

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

  <span data-ttu-id="23839-113">Zie voor meer informatie over profielen [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles) in de Microsoft TechNet-bibliotheek.</span><span class="sxs-lookup"><span data-stu-id="23839-113">For more information about profiles, see [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles) in the Microsoft TechNet library.</span></span>

- <span data-ttu-id="23839-114">Als u wilt een permanente variabele toevoegen aan het register, maakt u een nieuwe omgevingsvariabele met de naam `PSModulePath` met behulp van de Editor van de variabelen voor de omgeving in de **Systeemeigenschappen** in het dialoogvenster.</span><span class="sxs-lookup"><span data-stu-id="23839-114">To add a persistent variable to the registry, create a new user environment variable called `PSModulePath` using the Environment Variables Editor in the **System Properties** dialog box.</span></span>

- <span data-ttu-id="23839-115">U kunt een permanente variabele toevoegen met behulp van een script met de **SetEnvironmentVariable** methode voor de klasse omgeving.</span><span class="sxs-lookup"><span data-stu-id="23839-115">To add a persistent variable by using a script, use the **SetEnvironmentVariable** method on the Environment class.</span></span> <span data-ttu-id="23839-116">Het volgende script wordt bijvoorbeeld toegevoegd voor het "C:\Program Files\Fabrikam\Module pad naar de waarde van de omgevingsvariabele PSModulePath voor de computer.</span><span class="sxs-lookup"><span data-stu-id="23839-116">For example, the following script adds the "C:\Program Files\Fabrikam\Module path to the value of the PSModulePath environment variable for the computer.</span></span> <span data-ttu-id="23839-117">Het pad toevoegen aan de omgevingsvariabele van de gebruiker PSModulePath, stelt u het doel 'Gebruiker'.</span><span class="sxs-lookup"><span data-stu-id="23839-117">To add the path to the user PSModulePath environment variable, set the target to "User".</span></span>

  ```powershell
  $CurrentValue = [Environment]::GetEnvironmentVariable("PSModulePath", "Machine")
  [Environment]::SetEnvironmentVariable("PSModulePath", $CurrentValue + ";C:\Program Files\Fabrikam\Modules", "Machine")

  ```

## <a name="to-remove-locations-from-the-psmodulepath"></a><span data-ttu-id="23839-118">Locaties van de PSModulePath verwijderen</span><span class="sxs-lookup"><span data-stu-id="23839-118">To remove locations from the PSModulePath</span></span>

<span data-ttu-id="23839-119">Kunt u de paden van de variabele met behulp van vergelijkbare methoden verwijderen: bijvoorbeeld `$env:PSModulePath = $env:PSModulePath -replace ";c:\\ModulePath"` verwijdert de **c:\ModulePath** pad van de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="23839-119">You can remove paths from the variable using similar methods: for example, `$env:PSModulePath = $env:PSModulePath -replace ";c:\\ModulePath"` will remove the **c:\ModulePath** path from the current session.</span></span>

## <a name="see-also"></a><span data-ttu-id="23839-120">Zie ook</span><span class="sxs-lookup"><span data-stu-id="23839-120">See Also</span></span>

[<span data-ttu-id="23839-121">Een Windows PowerShell-Module schrijven</span><span class="sxs-lookup"><span data-stu-id="23839-121">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)
