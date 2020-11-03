---
description: Hierin wordt uitgelegd hoe u Power shell-modules installeert, importeert en gebruikt.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 09/15/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_modules?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Modules
ms.openlocfilehash: 9cd6cb2f8924c868cf4dc45ff322abbc53c07f19
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252304"
---
# <a name="about-modules"></a><span data-ttu-id="586cc-104">Over modules</span><span class="sxs-lookup"><span data-stu-id="586cc-104">About Modules</span></span>

## <a name="short-description"></a><span data-ttu-id="586cc-105">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="586cc-105">Short Description</span></span>
<span data-ttu-id="586cc-106">Hierin wordt uitgelegd hoe u Power shell-modules installeert, importeert en gebruikt.</span><span class="sxs-lookup"><span data-stu-id="586cc-106">Explains how to install, import, and use PowerShell modules.</span></span>

## <a name="long-description"></a><span data-ttu-id="586cc-107">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="586cc-107">Long Description</span></span>

<span data-ttu-id="586cc-108">Een module is een pakket met Power shell-opdrachten, zoals cmdlets, providers, functies, werk stromen, variabelen en aliassen.</span><span class="sxs-lookup"><span data-stu-id="586cc-108">A module is a package that contains PowerShell commands, such as cmdlets, providers, functions, workflows, variables, and aliases.</span></span>

<span data-ttu-id="586cc-109">Personen die opdrachten schrijven, kunnen modules gebruiken om hun opdrachten te organiseren en ze te delen met anderen.</span><span class="sxs-lookup"><span data-stu-id="586cc-109">People who write commands can use modules to organize their commands and share them with others.</span></span> <span data-ttu-id="586cc-110">Personen die een module ontvangen, kunnen de opdrachten in de modules toevoegen aan hun Power shell-sessies en deze gebruiken zoals de ingebouwde opdrachten.</span><span class="sxs-lookup"><span data-stu-id="586cc-110">People who receive modules can add the commands in the modules to their PowerShell sessions and use them just like the built-in commands.</span></span>

<span data-ttu-id="586cc-111">In dit onderwerp wordt uitgelegd hoe u Power shell-modules gebruikt.</span><span class="sxs-lookup"><span data-stu-id="586cc-111">This topic explains how to use PowerShell modules.</span></span> <span data-ttu-id="586cc-112">Zie [een Power shell-module schrijven](/powershell/scripting/developer/module/writing-a-windows-powershell-module)voor meer informatie over het schrijven van Power shell-modules.</span><span class="sxs-lookup"><span data-stu-id="586cc-112">For information about how to write PowerShell modules, see [Writing a PowerShell Module](/powershell/scripting/developer/module/writing-a-windows-powershell-module).</span></span>

## <a name="what-is-a-module"></a><span data-ttu-id="586cc-113">Wat is een module?</span><span class="sxs-lookup"><span data-stu-id="586cc-113">What Is a Module?</span></span>

<span data-ttu-id="586cc-114">Een module is een pakket met opdrachten.</span><span class="sxs-lookup"><span data-stu-id="586cc-114">A module is a package of commands.</span></span> <span data-ttu-id="586cc-115">Alle cmdlets en providers in uw sessie worden toegevoegd door een module of module.</span><span class="sxs-lookup"><span data-stu-id="586cc-115">All cmdlets and providers in your session are added by a module or a snap-in.</span></span>

## <a name="module-auto-loading"></a><span data-ttu-id="586cc-116">Module automatisch laden</span><span class="sxs-lookup"><span data-stu-id="586cc-116">Module Auto-Loading</span></span>

<span data-ttu-id="586cc-117">Vanaf Power Shell 3,0 worden modules in Power shell automatisch geïmporteerd in de eerste keer dat u een opdracht in een geïnstalleerde module uitvoert.</span><span class="sxs-lookup"><span data-stu-id="586cc-117">Beginning in PowerShell 3.0, PowerShell imports modules automatically the first time that you run any command in an installed module.</span></span> <span data-ttu-id="586cc-118">U kunt nu de opdrachten in een module zonder set-up-of profiel configuratie gebruiken. u hoeft geen modules te beheren nadat u ze op uw computer hebt geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="586cc-118">You can now use the commands in a module without any set-up or profile configuration, so there's no need to manage modules after you install them on your computer.</span></span>

<span data-ttu-id="586cc-119">De opdrachten in een module zijn ook gemakkelijker te vinden.</span><span class="sxs-lookup"><span data-stu-id="586cc-119">The commands in a module are also easier to find.</span></span> <span data-ttu-id="586cc-120">De `Get-Command` cmdlet haalt nu alle opdrachten op in alle geïnstalleerde modules, zelfs als ze nog niet in de sessie aanwezig zijn, zodat u een opdracht kunt vinden en gebruiken zonder te importeren.</span><span class="sxs-lookup"><span data-stu-id="586cc-120">The `Get-Command` cmdlet now gets all commands in all installed modules, even if they are not yet in the session, so you can find a command and use it without importing.</span></span>

<span data-ttu-id="586cc-121">In elk van de volgende voor beelden wordt de CimCmdlets-module, die bevat `Get-CimInstance` , in uw sessie geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="586cc-121">Each of the following examples cause the CimCmdlets module, which contains `Get-CimInstance`, to be imported into your session.</span></span>

- <span data-ttu-id="586cc-122">Voer de opdracht uit</span><span class="sxs-lookup"><span data-stu-id="586cc-122">Run the Command</span></span>

  ```powershell
  Get-CimInstance Win32_OperatingSystem
  ```

- <span data-ttu-id="586cc-123">De opdracht ophalen</span><span class="sxs-lookup"><span data-stu-id="586cc-123">Get the Command</span></span>

  ```powershell
  Get-Command Get-CimInstance
  ```

- <span data-ttu-id="586cc-124">Hulp vragen voor de opdracht</span><span class="sxs-lookup"><span data-stu-id="586cc-124">Get Help for the Command</span></span>

  ```powershell
  Get-Help Get-CimInstance
  ```

<span data-ttu-id="586cc-125">`Get-Command` opdrachten die een Joker teken () bevatten, worden `*` beschouwd als voor detectie, niet voor gebruik en er worden geen modules geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="586cc-125">`Get-Command` commands that include a wildcard character (`*`) are considered to be for discovery, not use, and do not import any modules.</span></span>

<span data-ttu-id="586cc-126">Alleen modules die zijn opgeslagen op de locatie die is opgegeven door de omgevings variabele PSModulePath, worden automatisch geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="586cc-126">Only modules that are stored in the location specified by the PSModulePath environment variable are automatically imported.</span></span> <span data-ttu-id="586cc-127">Modules op andere locaties moeten worden geïmporteerd door de cmdlet uit te voeren `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="586cc-127">Modules in other locations must be imported by running the `Import-Module` cmdlet.</span></span>

<span data-ttu-id="586cc-128">Daarnaast importeren opdrachten die gebruikmaken van Power shell-providers niet automatisch een module.</span><span class="sxs-lookup"><span data-stu-id="586cc-128">Also, commands that use PowerShell providers do not automatically import a module.</span></span> <span data-ttu-id="586cc-129">Als u bijvoorbeeld een opdracht gebruikt die het WSMan: station vereist, zoals de `Get-PSSessionConfiguration` cmdlet, moet u mogelijk de `Import-Module` cmdlet uitvoeren om de **micro soft. WSMan. Management** -module te importeren die het station bevat `WSMan:` .</span><span class="sxs-lookup"><span data-stu-id="586cc-129">For example, if you use a command that requires the WSMan: drive, such as the `Get-PSSessionConfiguration` cmdlet, you might need to run the `Import-Module` cmdlet to import the **Microsoft.WSMan.Management** module that includes the `WSMan:` drive.</span></span>

<span data-ttu-id="586cc-130">U kunt nog steeds de `Import-Module` opdracht uitvoeren om een module te importeren en de `$PSModuleAutoloadingPreference` variabele gebruiken om het automatisch importeren van modules in te scha kelen, uit te scha kelen en te configureren.</span><span class="sxs-lookup"><span data-stu-id="586cc-130">You can still run the `Import-Module` command to import a module and use the `$PSModuleAutoloadingPreference` variable to enable, disable and configure automatic importing of modules.</span></span> <span data-ttu-id="586cc-131">Zie [about_Preference_Variables](about_Preference_Variables.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="586cc-131">For more information, see [about_Preference_Variables](about_Preference_Variables.md).</span></span>

## <a name="how-to-use-a-module"></a><span data-ttu-id="586cc-132">Een module gebruiken</span><span class="sxs-lookup"><span data-stu-id="586cc-132">How to Use a Module</span></span>

<span data-ttu-id="586cc-133">Als u een module wilt gebruiken, voert u de volgende taken uit:</span><span class="sxs-lookup"><span data-stu-id="586cc-133">To use a module, perform the following tasks:</span></span>

1. <span data-ttu-id="586cc-134">Installeer de module.</span><span class="sxs-lookup"><span data-stu-id="586cc-134">Install the module.</span></span> <span data-ttu-id="586cc-135">(Dit gebeurt vaak voor u.)</span><span class="sxs-lookup"><span data-stu-id="586cc-135">(This is often done for you.)</span></span>
1. <span data-ttu-id="586cc-136">Zoek de opdrachten die de module heeft toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="586cc-136">Find the commands that the module added.</span></span>
1. <span data-ttu-id="586cc-137">Gebruik de opdrachten die door de module zijn toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="586cc-137">Use the commands that the module added.</span></span>

<span data-ttu-id="586cc-138">In dit onderwerp wordt uitgelegd hoe u deze taken uitvoert.</span><span class="sxs-lookup"><span data-stu-id="586cc-138">This topic explains how to perform these tasks.</span></span> <span data-ttu-id="586cc-139">Het bevat ook andere nuttige informatie over het beheren van modules.</span><span class="sxs-lookup"><span data-stu-id="586cc-139">It also includes other useful information about managing modules.</span></span>

## <a name="how-to-install-a-module"></a><span data-ttu-id="586cc-140">Een module installeren</span><span class="sxs-lookup"><span data-stu-id="586cc-140">How to Install a Module</span></span>

<span data-ttu-id="586cc-141">Als u een module als een map met bestanden ontvangt, moet u deze op uw computer installeren voordat u deze kunt gebruiken in Power shell.</span><span class="sxs-lookup"><span data-stu-id="586cc-141">If you receive a module as a folder with files in it, you need to install it on your computer before you can use it in PowerShell.</span></span>

<span data-ttu-id="586cc-142">De meeste modules zijn voor u geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="586cc-142">Most modules are installed for you.</span></span> <span data-ttu-id="586cc-143">Power shell wordt geleverd met verschillende vooraf geïnstalleerde modules, ook wel de _kern_ modules genoemd.</span><span class="sxs-lookup"><span data-stu-id="586cc-143">PowerShell comes with several preinstalled modules, sometimes called the _core_ modules.</span></span> <span data-ttu-id="586cc-144">Op Windows-computers worden deze modules vooraf geïnstalleerd als de functies die deel uitmaken van het besturings systeem cmdlets hebben om ze te beheren.</span><span class="sxs-lookup"><span data-stu-id="586cc-144">On Windows-based computers, if features that are included with the operating system have cmdlets to manage them, those modules are preinstalled.</span></span> <span data-ttu-id="586cc-145">Wanneer u een Windows-functie installeert met behulp van bijvoorbeeld de wizard functies en onderdelen toevoegen in Serverbeheer of het dialoog venster Windows-onderdelen in-of uitschakelen in het configuratie scherm, worden alle Power shell-modules die deel uitmaken van de functie geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="586cc-145">When you install a Windows feature, by using, for example, the Add Roles and Features Wizard in Server Manager, or the Turn Windows features on or off dialog box in Control Panel, any PowerShell modules that are part of the feature are installed.</span></span> <span data-ttu-id="586cc-146">Er zijn veel andere modules beschikbaar in een installatie programma of Setup-toepassing waarmee de module wordt geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="586cc-146">Many other modules come in an installer or Setup program that installs the module.</span></span>

<span data-ttu-id="586cc-147">Gebruik de volgende opdracht om een directory **modules** voor de huidige gebruiker te maken:</span><span class="sxs-lookup"><span data-stu-id="586cc-147">Use the following command to create a **Modules** directory for the current user:</span></span>

```powershell
New-Item -Type Directory -Path $HOME\Documents\PowerShell\Modules
```

<span data-ttu-id="586cc-148">Kopieer de volledige module-map naar de map modules.</span><span class="sxs-lookup"><span data-stu-id="586cc-148">Copy the entire module folder into the Modules directory.</span></span> <span data-ttu-id="586cc-149">U kunt elke methode gebruiken om de map te kopiëren, met inbegrip van Windows Verkenner en Cmd.exe, en Power shell.</span><span class="sxs-lookup"><span data-stu-id="586cc-149">You can use any method to copy the folder, including Windows Explorer and Cmd.exe, as well as PowerShell.</span></span> <span data-ttu-id="586cc-150">Gebruik in Power shell de `Copy-Item` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="586cc-150">In PowerShell use the `Copy-Item` cmdlet.</span></span> <span data-ttu-id="586cc-151">Als u bijvoorbeeld de map MyModule wilt kopiëren van `C:\ps-test\MyModule` naar de map modules, typt u:</span><span class="sxs-lookup"><span data-stu-id="586cc-151">For example, to copy the MyModule folder from `C:\ps-test\MyModule` to the Modules directory, type:</span></span>

```powershell
Copy-Item -Path C:\ps-test\MyModule -Destination `
    $HOME\Documents\PowerShell\Modules
```

<span data-ttu-id="586cc-152">U kunt een module op elke locatie installeren, maar als u uw modules in een standaard module locatie installeert, zijn deze gemakkelijker te beheren.</span><span class="sxs-lookup"><span data-stu-id="586cc-152">You can install a module in any location, but installing your modules in a default module location makes them easier to manage.</span></span> <span data-ttu-id="586cc-153">Zie de sectie [module en DSC-resource locaties en PSModulePath](#module-and-dsc-resource-locations-and-psmodulepath) voor meer informatie over de standaard module locaties.</span><span class="sxs-lookup"><span data-stu-id="586cc-153">For more information about the default module locations, see the [Module and DSC Resource Locations, and PSModulePath](#module-and-dsc-resource-locations-and-psmodulepath) section.</span></span>

## <a name="how-to-find-installed-modules"></a><span data-ttu-id="586cc-154">Geïnstalleerde modules zoeken</span><span class="sxs-lookup"><span data-stu-id="586cc-154">How to Find Installed Modules</span></span>

<span data-ttu-id="586cc-155">Als u modules wilt zoeken die zijn geïnstalleerd op een standaard locatie van de module, maar nog niet zijn geïmporteerd in uw sessie, typt u:</span><span class="sxs-lookup"><span data-stu-id="586cc-155">To find modules that are installed in a default module location, but not yet imported into your session, type:</span></span>

```powershell
Get-Module -ListAvailable
```

<span data-ttu-id="586cc-156">Als u de modules wilt vinden die al in uw sessie zijn geïmporteerd, typt u bij de Power shell-prompt het volgende:</span><span class="sxs-lookup"><span data-stu-id="586cc-156">To find the modules that have already been imported into your session, at the PowerShell prompt, type:</span></span>

```powershell
Get-Module
```

<span data-ttu-id="586cc-157">`Get-Module`Zie [Get-module](xref:Microsoft.PowerShell.Core.Get-Module)voor meer informatie over de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="586cc-157">For more information about the `Get-Module` cmdlet, see [Get-Module](xref:Microsoft.PowerShell.Core.Get-Module).</span></span>

## <a name="how-to-find-the-commands-in-a-module"></a><span data-ttu-id="586cc-158">De opdrachten in een module vinden</span><span class="sxs-lookup"><span data-stu-id="586cc-158">How to Find the Commands in a Module</span></span>

<span data-ttu-id="586cc-159">Gebruik de `Get-Command` cmdlet om alle beschik bare opdrachten te vinden.</span><span class="sxs-lookup"><span data-stu-id="586cc-159">Use the `Get-Command` cmdlet to find all available commands.</span></span> <span data-ttu-id="586cc-160">U kunt de para meters van de `Get-Command` cmdlet gebruiken om opdrachten te filteren, bijvoorbeeld per module, naam en zelfstandignaam programma.</span><span class="sxs-lookup"><span data-stu-id="586cc-160">You can use the parameters of the `Get-Command` cmdlet to filter commands such as by module, name, and noun.</span></span>

<span data-ttu-id="586cc-161">Als u alle opdrachten in een module wilt zoeken, typt u:</span><span class="sxs-lookup"><span data-stu-id="586cc-161">To find all commands in a module, type:</span></span>

```powershell
Get-Command -Module <module-name>
```

<span data-ttu-id="586cc-162">Als u bijvoorbeeld de opdrachten in de BitsTransfer-module wilt zoeken, typt u:</span><span class="sxs-lookup"><span data-stu-id="586cc-162">For example, to find the commands in the BitsTransfer module, type:</span></span>

```powershell
Get-Command -Module BitsTransfer
```

<span data-ttu-id="586cc-163">`Get-Command`Zie [Get-opdracht](xref:Microsoft.PowerShell.Core.Get-Command)voor meer informatie over de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="586cc-163">For more information about the `Get-Command` cmdlet, see [Get-Command](xref:Microsoft.PowerShell.Core.Get-Command).</span></span>

## <a name="how-to-get-help-for-the-commands-in-a-module"></a><span data-ttu-id="586cc-164">Hulp krijgen voor de opdrachten in een module</span><span class="sxs-lookup"><span data-stu-id="586cc-164">How to Get Help for the Commands in a Module</span></span>

<span data-ttu-id="586cc-165">Als de module Help-bestanden bevat voor de opdrachten die worden geëxporteerd, `Get-Help` worden de Help-onderwerpen weer gegeven door de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="586cc-165">If the module contains Help files for the commands that it exports, the `Get-Help` cmdlet will display the Help topics.</span></span> <span data-ttu-id="586cc-166">Gebruik dezelfde `Get-Help` opdracht indeling die u zou gebruiken om hulp te krijgen voor elke opdracht in Power shell.</span><span class="sxs-lookup"><span data-stu-id="586cc-166">Use the same `Get-Help` command format that you would use to get help for any command in PowerShell.</span></span>

<span data-ttu-id="586cc-167">Vanaf Power Shell 3,0 kunt u Help-bestanden voor een module downloaden en updates naar de Help-bestanden downloaden zodat deze nooit verouderd zijn.</span><span class="sxs-lookup"><span data-stu-id="586cc-167">Beginning in PowerShell 3.0, you can download Help files for a module and download updates to the Help files so they are never obsolete.</span></span>

<span data-ttu-id="586cc-168">Als u hulp wilt krijgen voor een-opdracht in een module, typt u:</span><span class="sxs-lookup"><span data-stu-id="586cc-168">To get help for a commands in a module, type:</span></span>

```powershell
Get-Help <command-name>
```

<span data-ttu-id="586cc-169">Als u online hulp voor de opdracht wilt krijgen in een module, typt u:</span><span class="sxs-lookup"><span data-stu-id="586cc-169">To get help online for command in a module, type:</span></span>

```powershell
Get-Help <command-name> -Online
```

<span data-ttu-id="586cc-170">Als u de Help-bestanden voor de opdrachten in een module wilt downloaden en installeren, typt u:</span><span class="sxs-lookup"><span data-stu-id="586cc-170">To download and install the help files for the commands in a module, type:</span></span>

```powershell
Update-Help -Module <module-name>
```

<span data-ttu-id="586cc-171">Zie [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) en [Update-Help](xref:Microsoft.PowerShell.Core.Update-Help)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="586cc-171">For more information, see [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) and [Update-Help](xref:Microsoft.PowerShell.Core.Update-Help).</span></span>

## <a name="how-to-import-a-module"></a><span data-ttu-id="586cc-172">Een module importeren</span><span class="sxs-lookup"><span data-stu-id="586cc-172">How to Import a Module</span></span>

<span data-ttu-id="586cc-173">Mogelijk moet u een module importeren of een module bestand importeren.</span><span class="sxs-lookup"><span data-stu-id="586cc-173">You might have to import a module or import a module file.</span></span> <span data-ttu-id="586cc-174">Importeren is vereist wanneer een module niet is geïnstalleerd op de locaties die zijn opgegeven door de omgevings variabele **PSModulePath** , `$env:PSModulePath` of als de module bestaat uit een bestand, zoals een. dll-of. psm1-bestand, in plaats van een typische module die wordt geleverd als een map.</span><span class="sxs-lookup"><span data-stu-id="586cc-174">Importing is required when a module is not installed in the locations specified by the **PSModulePath** environment variable, `$env:PSModulePath`, or the module consists of file, such as a .dll or .psm1 file, instead of typical module that is delivered as a folder.</span></span>

<span data-ttu-id="586cc-175">U kunt er ook voor kiezen om een module te importeren, zodat u de para meters van de `Import-Module` opdracht, zoals de para meter prefix, een onderscheidend voor voegsel toevoegt aan de naam van het zelfstandige zelfstandig van alle geïmporteerde opdrachten of de para meter **NoClobber** , waarmee wordt voor komen dat de module opdrachten kan toevoegen waarmee bestaande opdrachten in de sessie worden verborgen of vervangen.</span><span class="sxs-lookup"><span data-stu-id="586cc-175">You might also choose to import a module so that you can use the parameters of the `Import-Module` command, such as the Prefix parameter, which adds a distinctive prefix to the noun names of all imported commands, or the **NoClobber** parameter, which prevents the module from adding commands that would hide or replace existing commands in the session.</span></span>

<span data-ttu-id="586cc-176">Als u modules wilt importeren, gebruikt u de `Import-Module` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="586cc-176">To import modules, use the `Import-Module` cmdlet.</span></span>

<span data-ttu-id="586cc-177">Als u modules in een PSModulePath-locatie in de huidige sessie wilt importeren, gebruikt u de volgende opdracht indeling.</span><span class="sxs-lookup"><span data-stu-id="586cc-177">To import modules in a PSModulePath location into the current session, use the following command format.</span></span>

```powershell
Import-Module <module-name>
```

<span data-ttu-id="586cc-178">Met de volgende opdracht wordt bijvoorbeeld de module BitsTransfer in de huidige sessie geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="586cc-178">For example, the following command imports the BitsTransfer module into the current session.</span></span>

```powershell
Import-Module BitsTransfer
```

<span data-ttu-id="586cc-179">Als u een module wilt importeren die zich niet in een standaard module locatie bevindt, gebruikt u het volledig gekwalificeerde pad naar de module map in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="586cc-179">To import a module that is not in a default module location, use the fully qualified path to the module folder in the command.</span></span>

<span data-ttu-id="586cc-180">Als u bijvoorbeeld de module TestCmdlets in de `C:\ps-test` map wilt toevoegen aan uw sessie, typt u:</span><span class="sxs-lookup"><span data-stu-id="586cc-180">For example, to add the TestCmdlets module in the `C:\ps-test` directory to your session, type:</span></span>

```powershell
Import-Module C:\ps-test\TestCmdlets
```

<span data-ttu-id="586cc-181">Als u een module bestand wilt importeren dat zich niet in een module-map bevindt, gebruikt u het volledige pad naar het module bestand in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="586cc-181">To import a module file that is not contained in a module folder, use the fully qualified path to the module file in the command.</span></span>

<span data-ttu-id="586cc-182">Als u bijvoorbeeld de module TestCmdlets.dll in de `C:\ps-test` map wilt toevoegen aan uw sessie, typt u:</span><span class="sxs-lookup"><span data-stu-id="586cc-182">For example, to add the TestCmdlets.dll module in the `C:\ps-test` directory to your session, type:</span></span>

```powershell
Import-Module C:\ps-test\TestCmdlets.dll
```

<span data-ttu-id="586cc-183">Zie [import-module](xref:Microsoft.PowerShell.Core.Import-Module)voor meer informatie over het toevoegen van modules aan uw sessie.</span><span class="sxs-lookup"><span data-stu-id="586cc-183">For more information about adding modules to your session, see [Import-Module](xref:Microsoft.PowerShell.Core.Import-Module).</span></span>

## <a name="how-to-import-a-module-into-every-session"></a><span data-ttu-id="586cc-184">Een module in elke sessie importeren</span><span class="sxs-lookup"><span data-stu-id="586cc-184">How to Import a Module into Every Session</span></span>

<span data-ttu-id="586cc-185">Met de `Import-Module` opdracht worden modules in uw huidige Power shell-sessie geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="586cc-185">The `Import-Module` command imports modules into your current PowerShell session.</span></span> <span data-ttu-id="586cc-186">Als u een module wilt importeren in elke Power shell-sessie die u start, voegt u de `Import-Module` opdracht toe aan uw Power shell-profiel.</span><span class="sxs-lookup"><span data-stu-id="586cc-186">To import a module into every PowerShell session that you start, add the `Import-Module` command to your PowerShell profile.</span></span>

<span data-ttu-id="586cc-187">Zie [about_Profiles](about_Profiles.md)voor meer informatie over profielen.</span><span class="sxs-lookup"><span data-stu-id="586cc-187">For more information about profiles, see [about_Profiles](about_Profiles.md).</span></span>

## <a name="how-to-remove-a-module"></a><span data-ttu-id="586cc-188">Een module verwijderen</span><span class="sxs-lookup"><span data-stu-id="586cc-188">How to Remove a Module</span></span>

<span data-ttu-id="586cc-189">Wanneer u een module verwijdert, worden de opdrachten die de module heeft toegevoegd, verwijderd uit de sessie.</span><span class="sxs-lookup"><span data-stu-id="586cc-189">When you remove a module, the commands that the module added are deleted from the session.</span></span>

<span data-ttu-id="586cc-190">Als u een module uit uw sessie wilt verwijderen, gebruikt u de volgende opdracht indeling.</span><span class="sxs-lookup"><span data-stu-id="586cc-190">To remove a module from your session, use the following command format.</span></span>

```powershell
Remove-Module <module-name>
```

<span data-ttu-id="586cc-191">Met de volgende opdracht wordt bijvoorbeeld de module BitsTransfer verwijderd uit de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="586cc-191">For example, the following command removes the BitsTransfer module from the current session.</span></span>

```powershell
Remove-Module BitsTransfer
```

<span data-ttu-id="586cc-192">Als u een module verwijdert, wordt de bewerking van het importeren van een module ongedaan gemaakt.</span><span class="sxs-lookup"><span data-stu-id="586cc-192">Removing a module reverses the operation of importing a module.</span></span> <span data-ttu-id="586cc-193">Als u een module verwijdert, wordt de module niet verwijderd.</span><span class="sxs-lookup"><span data-stu-id="586cc-193">Removing a module does not uninstall the module.</span></span> <span data-ttu-id="586cc-194">Zie [Remove-module](xref:Microsoft.PowerShell.Core.Remove-Module)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="586cc-194">For more information, see [Remove-Module](xref:Microsoft.PowerShell.Core.Remove-Module).</span></span>

## <a name="module-and-dsc-resource-locations-and-psmodulepath"></a><span data-ttu-id="586cc-195">Module-en DSC-resource locaties en PSModulePath</span><span class="sxs-lookup"><span data-stu-id="586cc-195">Module and DSC Resource Locations, and PSModulePath</span></span>

<span data-ttu-id="586cc-196">De `$env:PSModulePath` omgevings variabele bevat een lijst met maplocaties die worden doorzocht om modules en resources te zoeken.</span><span class="sxs-lookup"><span data-stu-id="586cc-196">The `$env:PSModulePath` environment variable contains a list of folder locations that are searched to find modules and resources.</span></span>

<span data-ttu-id="586cc-197">De doel locaties die worden toegewezen aan, `$env:PSModulePath` zijn standaard:</span><span class="sxs-lookup"><span data-stu-id="586cc-197">By default, the effective locations assigned to `$env:PSModulePath` are:</span></span>

- <span data-ttu-id="586cc-198">Locaties voor het hele systeem: `$PSHOME\Modules`</span><span class="sxs-lookup"><span data-stu-id="586cc-198">System-wide locations: `$PSHOME\Modules`</span></span>

  <span data-ttu-id="586cc-199">Deze mappen bevatten modules die worden geleverd met Windows en Power shell.</span><span class="sxs-lookup"><span data-stu-id="586cc-199">These folders contain modules that ship with Windows and PowerShell.</span></span>

  <span data-ttu-id="586cc-200">DSC-resources die zijn opgenomen in Power shell, worden opgeslagen in de `$PSHOME\Modules\PSDesiredStateConfiguration\DSCResources` map.</span><span class="sxs-lookup"><span data-stu-id="586cc-200">DSC resources that are included with PowerShell are stored in the `$PSHOME\Modules\PSDesiredStateConfiguration\DSCResources` folder.</span></span>

- <span data-ttu-id="586cc-201">Gebruikersspecifieke modules: Dit zijn de modules die door de gebruiker worden geïnstalleerd in het bereik van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="586cc-201">User-specific modules: These are modules installed by the user in the user's scope.</span></span> <span data-ttu-id="586cc-202">`Install-Module` heeft een **bereik** parameter waarmee u kunt opgeven of de module is geïnstalleerd voor de huidige gebruiker of voor alle gebruikers.</span><span class="sxs-lookup"><span data-stu-id="586cc-202">`Install-Module` has a **Scope** parameter that allows you to specify whether the module is installed for the current user or for all users.</span></span> <span data-ttu-id="586cc-203">Zie [install-module](xref:PowerShellGet.Install-Module)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="586cc-203">For more information, see [Install-Module](xref:PowerShellGet.Install-Module).</span></span>

  <span data-ttu-id="586cc-204">De gebruikerspecifieke locatie van **CurrentUser** op Windows is de `PowerShell\Modules` map die zich bevindt op de locatie van **documenten** in uw gebruikers profiel.</span><span class="sxs-lookup"><span data-stu-id="586cc-204">The user-specific **CurrentUser** location on Windows is the `PowerShell\Modules` folder located in the **Documents** location in your user profile.</span></span> <span data-ttu-id="586cc-205">Het specifieke pad van die locatie is afhankelijk van de versie van Windows en of u nu Mapomleiding gebruikt.</span><span class="sxs-lookup"><span data-stu-id="586cc-205">The specific path of that location varies by version of Windows and whether or not you are using folder redirection.</span></span> <span data-ttu-id="586cc-206">Micro soft OneDrive kan ook de locatie van de map **documenten** wijzigen.</span><span class="sxs-lookup"><span data-stu-id="586cc-206">Microsoft OneDrive can also change the location of your **Documents** folder.</span></span>

  <span data-ttu-id="586cc-207">Deze locatie is standaard op Windows 10 `$HOME\Documents\PowerShell\Modules` .</span><span class="sxs-lookup"><span data-stu-id="586cc-207">By default, on Windows 10, that location is `$HOME\Documents\PowerShell\Modules`.</span></span> <span data-ttu-id="586cc-208">Op Linux of Mac is de **CurrentUser** locatie van CurrentUser `$HOME/.local/share/powershell/Modules` .</span><span class="sxs-lookup"><span data-stu-id="586cc-208">On Linux or Mac, the **CurrentUser** location is `$HOME/.local/share/powershell/Modules`.</span></span>

  > [!NOTE]
  > <span data-ttu-id="586cc-209">U kunt de locatie van uw **Documentenmap** controleren met behulp van de volgende opdracht: `[Environment]::GetFolderPath('MyDocuments')` .</span><span class="sxs-lookup"><span data-stu-id="586cc-209">You can verify the location of your **Documents** folder using the following command: `[Environment]::GetFolderPath('MyDocuments')`.</span></span>

- <span data-ttu-id="586cc-210">De **ALLUSERS** -locatie bevindt zich `$env:PROGRAMFILES\PowerShell\Modules` in Windows.</span><span class="sxs-lookup"><span data-stu-id="586cc-210">The **AllUsers** location is `$env:PROGRAMFILES\PowerShell\Modules` on Windows.</span></span> <span data-ttu-id="586cc-211">Op Linux of Mac worden de modules opgeslagen op `/usr/local/share/powershell/Modules` .</span><span class="sxs-lookup"><span data-stu-id="586cc-211">On Linux or Mac the modules are stored at `/usr/local/share/powershell/Modules`.</span></span>

> [!NOTE]
> <span data-ttu-id="586cc-212">Als u bestanden in de map wilt toevoegen of wijzigen `$env:Windir\System32` , start u Power shell met de optie **als administrator uitvoeren** .</span><span class="sxs-lookup"><span data-stu-id="586cc-212">To add or change files in the `$env:Windir\System32` directory, start PowerShell with the **Run as administrator** option.</span></span>

<span data-ttu-id="586cc-213">U kunt de standaard module locaties op uw systeem wijzigen door de waarde van de omgevings variabele **PSModulePath** te wijzigen `$Env:PSModulePath` .</span><span class="sxs-lookup"><span data-stu-id="586cc-213">You can change the default module locations on your system by changing the value of the **PSModulePath** environment variable, `$Env:PSModulePath`.</span></span> <span data-ttu-id="586cc-214">De omgevings variabele **PSModulePath** is gemodelleerd op de omgevings variabele PATH en heeft dezelfde indeling.</span><span class="sxs-lookup"><span data-stu-id="586cc-214">The **PSModulePath** environment variable is modeled on the Path environment variable and has the same format.</span></span>

<span data-ttu-id="586cc-215">Als u de standaard-module locaties wilt weer geven, typt u:</span><span class="sxs-lookup"><span data-stu-id="586cc-215">To view the default module locations, type:</span></span>

```powershell
$Env:PSModulePath
```

<span data-ttu-id="586cc-216">Gebruik de volgende opdracht indeling om een standaard module locatie toe te voegen.</span><span class="sxs-lookup"><span data-stu-id="586cc-216">To add a default module location, use the following command format.</span></span>

```powershell
$Env:PSModulePath = $Env:PSModulePath + ";<path>"
```

<span data-ttu-id="586cc-217">De punt komma ( `;` ) in de opdracht scheidt u het nieuwe pad van het pad dat voorafgaat aan deze in de lijst.</span><span class="sxs-lookup"><span data-stu-id="586cc-217">The semi-colon (`;`) in the command separates the new path from the path that precedes it in the list.</span></span>

<span data-ttu-id="586cc-218">Als u bijvoorbeeld de map wilt toevoegen `C:\ps-test\Modules` , typt u:</span><span class="sxs-lookup"><span data-stu-id="586cc-218">For example, to add the `C:\ps-test\Modules` directory, type:</span></span>

```powershell
$Env:PSModulePath + ";C:\ps-test\Modules"
```

<span data-ttu-id="586cc-219">Als u een standaard module locatie in Linux of MacOS wilt toevoegen, gebruikt u de volgende opdracht indeling:</span><span class="sxs-lookup"><span data-stu-id="586cc-219">To add a default module location on Linux or MacOS, use the following command format:</span></span>

```powershell
$Env:PSModulePath += ":<path>"
```

<span data-ttu-id="586cc-220">Als u bijvoorbeeld de `/usr/local/Fabrikam/Modules` map wilt toevoegen aan de waarde van de omgevings variabele **PSModulePath** , typt u:</span><span class="sxs-lookup"><span data-stu-id="586cc-220">For example, to add the `/usr/local/Fabrikam/Modules` directory to the value of the **PSModulePath** environment variable, type:</span></span>

```powershell
$Env:PSModulePath += ":/usr/local/Fabrikam/Modules"
```

<span data-ttu-id="586cc-221">In Linux of MacOS scheidt de dubbele punt ( `:` ) in de opdracht het nieuwe pad van het pad dat voorafgaat aan de voor waarde in de lijst.</span><span class="sxs-lookup"><span data-stu-id="586cc-221">On Linux or MacOS, the colon (`:`) in the command separates the new path from the path that precedes it in the list.</span></span>

<span data-ttu-id="586cc-222">Wanneer u een pad naar **PSModulePath** toevoegt, `Get-Module` en `Import-Module` opdrachten bevatten modules in dat pad.</span><span class="sxs-lookup"><span data-stu-id="586cc-222">When you add a path to **PSModulePath** , `Get-Module` and `Import-Module` commands include modules in that path.</span></span>

<span data-ttu-id="586cc-223">De waarde die u instelt, is alleen van invloed op de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="586cc-223">The value that you set affects only the current session.</span></span> <span data-ttu-id="586cc-224">Als u de wijziging permanent wilt maken, voegt u de opdracht toe aan uw Power shell-profiel of gebruikt u het onderdeel systeem in het configuratie scherm om de waarde van de omgevings variabele **PSModulePath** in het REGI ster te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="586cc-224">To make the change persistent, add the command to your PowerShell profile or use System in Control Panel to change the value of the **PSModulePath** environment variable in the registry.</span></span>

<span data-ttu-id="586cc-225">Als u de wijziging permanent wilt aanbrengen, kunt u ook de methode **SetEnvironmentVariable** van de klasse **System. Environment** gebruiken om een pad toe te voegen aan de omgevings variabele **PSModulePath** .</span><span class="sxs-lookup"><span data-stu-id="586cc-225">Also, to make the change persistent, you can also use the **SetEnvironmentVariable** method of the **System.Environment** class to add a Path to the **PSModulePath** environment variable.</span></span>

<span data-ttu-id="586cc-226">Zie [about_Environment_Variables](about_Environment_Variables.md)voor meer informatie over de variabele **PSModulePath** .</span><span class="sxs-lookup"><span data-stu-id="586cc-226">For more information about the **PSModulePath** variable, see [about_Environment_Variables](about_Environment_Variables.md).</span></span>

## <a name="modules-and-name-conflicts"></a><span data-ttu-id="586cc-227">Conflicten met modules en naam</span><span class="sxs-lookup"><span data-stu-id="586cc-227">Modules and Name Conflicts</span></span>

<span data-ttu-id="586cc-228">Naam conflicten treden op wanneer meer dan één opdracht in de sessie dezelfde naam heeft.</span><span class="sxs-lookup"><span data-stu-id="586cc-228">Name conflicts occur when more than one command in the session has the same name.</span></span> <span data-ttu-id="586cc-229">Het importeren van een module veroorzaakt een naam conflict wanneer opdrachten in de module dezelfde namen hebben als opdrachten of items in de sessie.</span><span class="sxs-lookup"><span data-stu-id="586cc-229">Importing a module causes a name conflict when commands in the module have the same names as commands or items in the session.</span></span>

<span data-ttu-id="586cc-230">Naam conflicten kunnen ertoe leiden dat opdrachten worden verborgen of vervangen.</span><span class="sxs-lookup"><span data-stu-id="586cc-230">Name conflicts can result in commands being hidden or replaced.</span></span>

### <a name="hidden"></a><span data-ttu-id="586cc-231">Verborgen</span><span class="sxs-lookup"><span data-stu-id="586cc-231">Hidden</span></span>

<span data-ttu-id="586cc-232">Een opdracht is verborgen wanneer het niet de opdracht is die wordt uitgevoerd wanneer u de naam van de opdracht typt, maar u kunt deze uitvoeren met behulp van een andere methode, bijvoorbeeld door de opdracht naam te kwalificeren met de naam van de module of module waarin deze afkomstig is.</span><span class="sxs-lookup"><span data-stu-id="586cc-232">A command is hidden when it is not the command that runs when you type the command name, but you can run it by using another method, such as by qualifying the command name with the name of the module or snap-in in which it originated.</span></span>

### <a name="replaced"></a><span data-ttu-id="586cc-233">Geplaatst</span><span class="sxs-lookup"><span data-stu-id="586cc-233">Replaced</span></span>

<span data-ttu-id="586cc-234">Een opdracht wordt vervangen wanneer u deze niet kunt uitvoeren omdat deze is overschreven door een opdracht met dezelfde naam.</span><span class="sxs-lookup"><span data-stu-id="586cc-234">A command is replaced when you cannot run it because it has been overwritten by a command with the same name.</span></span> <span data-ttu-id="586cc-235">Zelfs wanneer u de module verwijdert die het conflict heeft veroorzaakt, kunt u een vervangen opdracht alleen uitvoeren als u de sessie opnieuw opstart.</span><span class="sxs-lookup"><span data-stu-id="586cc-235">Even when you remove the module that caused the conflict, you cannot run a replaced command unless you restart the session.</span></span>

<span data-ttu-id="586cc-236">`Import-Module` kan opdrachten toevoegen die opdrachten in de huidige sessie verbergen en vervangen.</span><span class="sxs-lookup"><span data-stu-id="586cc-236">`Import-Module` might add commands that hide and replace commands in the current session.</span></span> <span data-ttu-id="586cc-237">Ook kunnen opdrachten in uw sessie opdrachten verbergen die zijn toegevoegd aan de module.</span><span class="sxs-lookup"><span data-stu-id="586cc-237">Also, commands in your session can hide commands that the module added.</span></span>

<span data-ttu-id="586cc-238">Als u naam conflicten wilt detecteren, gebruikt u de para meter **all** van de `Get-Command` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="586cc-238">To detect name conflicts, use the **All** parameter of the `Get-Command` cmdlet.</span></span> <span data-ttu-id="586cc-239">Vanaf Power Shell 3,0 worden `Get-Command` alleen de opdrachten opgehaald die worden uitgevoerd wanneer u de naam van de opdracht typt.</span><span class="sxs-lookup"><span data-stu-id="586cc-239">Beginning in PowerShell 3.0, `Get-Command` gets only that commands that run when you type the command name.</span></span> <span data-ttu-id="586cc-240">De **alle** para meters haalt alle opdrachten met de specifieke naam op in de sessie.</span><span class="sxs-lookup"><span data-stu-id="586cc-240">The **All** parameter gets all commands with the specific name in the session.</span></span>

<span data-ttu-id="586cc-241">Als u naam conflicten wilt voor komen, gebruikt u de para meters **NoClobber** of **voor voegsel** van de `Import-Module` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="586cc-241">To prevent name conflicts, use the **NoClobber** or **Prefix** parameters of the `Import-Module` cmdlet.</span></span> <span data-ttu-id="586cc-242">De para meter **prefix** voegt een voor voegsel toe aan de namen van geïmporteerde opdrachten, zodat deze uniek zijn in de sessie.</span><span class="sxs-lookup"><span data-stu-id="586cc-242">The **Prefix** parameter adds a prefix to the names of imported commands so that they are unique in the session.</span></span> <span data-ttu-id="586cc-243">Met de para meter **NoClobber** worden geen opdrachten geïmporteerd waarmee bestaande opdrachten in de sessie worden verborgen of vervangen.</span><span class="sxs-lookup"><span data-stu-id="586cc-243">The **NoClobber** parameter does not import any commands that would hide or replace existing commands in the session.</span></span>

<span data-ttu-id="586cc-244">U kunt ook de para meters **alias** , **cmdlet** , **Function** en **Variable** van gebruiken `Import-Module` om alleen de opdrachten te selecteren die u wilt importeren, en u kunt opdrachten uitsluiten die naam conflicten veroorzaken in uw sessie.</span><span class="sxs-lookup"><span data-stu-id="586cc-244">You can also use the **Alias** , **Cmdlet** , **Function** , and **Variable** parameters of `Import-Module` to select only the commands that you want to import, and you can exclude commands that cause name conflicts in your session.</span></span>

<span data-ttu-id="586cc-245">Module auteurs kunnen naam conflicten voor komen door gebruik te maken van de eigenschap **DefaultCommandPrefix** van het module manifest om een standaard voorvoegsel toe te voegen aan alle opdracht namen.</span><span class="sxs-lookup"><span data-stu-id="586cc-245">Module authors can prevent name conflicts by using the **DefaultCommandPrefix** property of the module manifest to add a default prefix to all command names.</span></span>
<span data-ttu-id="586cc-246">De waarde van de para meter **prefix** krijgt voor rang op de waarde van **DefaultCommandPrefix**.</span><span class="sxs-lookup"><span data-stu-id="586cc-246">The value of the **Prefix** parameter takes precedence over the value of **DefaultCommandPrefix**.</span></span>

<span data-ttu-id="586cc-247">Zelfs als een opdracht verborgen is, kunt u deze uitvoeren door in aanmerking te komen voor de naam van de module of module waarin deze afkomstig is.</span><span class="sxs-lookup"><span data-stu-id="586cc-247">Even if a command is hidden, you can run it by qualifying the command name with the name of the module or snap-in in which it originated.</span></span>

<span data-ttu-id="586cc-248">De prioriteits regels van de Power shell-opdracht bepalen welke opdracht wordt uitgevoerd wanneer de sessie opdrachten met dezelfde naam bevat.</span><span class="sxs-lookup"><span data-stu-id="586cc-248">The PowerShell command precedence rules determine which command runs when the session includes commands with the same name.</span></span>

<span data-ttu-id="586cc-249">Als een sessie bijvoorbeeld een functie en een cmdlet met dezelfde naam bevat, voert Power shell de functie standaard uit.</span><span class="sxs-lookup"><span data-stu-id="586cc-249">For example, when a session includes a function and a cmdlet with the same name, PowerShell runs the function by default.</span></span> <span data-ttu-id="586cc-250">Wanneer de sessie opdrachten van hetzelfde type met dezelfde naam bevat, zoals twee cmdlets met dezelfde naam, wordt standaard de laatst toegevoegde opdracht uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="586cc-250">When the session includes commands of the same type with the same name, such as two cmdlets with the same name, by default, it runs the most recently added command.</span></span>

<span data-ttu-id="586cc-251">Zie [about_Command_Precedence](about_Command_Precedence.md)voor meer informatie, inclusief een uitleg van de prioriteits regels en instructies voor het uitvoeren van verborgen opdrachten.</span><span class="sxs-lookup"><span data-stu-id="586cc-251">For more information, including an explanation of the precedence rules and instructions for running hidden commands, see [about_Command_Precedence](about_Command_Precedence.md).</span></span>

## <a name="modules-and-snap-ins"></a><span data-ttu-id="586cc-252">Modules en snap-ins</span><span class="sxs-lookup"><span data-stu-id="586cc-252">Modules and Snap-ins</span></span>

<span data-ttu-id="586cc-253">U kunt vanuit modules en modules opdrachten toevoegen aan uw sessie. Modules kunnen alle typen opdrachten toevoegen, waaronder cmdlets, providers en functies, en items, zoals variabelen, aliassen en Power Shell-stations.</span><span class="sxs-lookup"><span data-stu-id="586cc-253">You can add commands to your session from modules and snap-ins. Modules can add all types of commands, including cmdlets, providers, and functions, and items, such as variables, aliases, and PowerShell drives.</span></span> <span data-ttu-id="586cc-254">Modules kunnen alleen cmdlets en providers toevoegen.</span><span class="sxs-lookup"><span data-stu-id="586cc-254">Snap-ins can add only cmdlets and providers.</span></span>

<span data-ttu-id="586cc-255">Voordat u een module of module uit uw sessie verwijdert, gebruikt u de volgende opdrachten om te bepalen welke opdrachten worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="586cc-255">Before removing a module or snap-in from your session, use the following commands to determine which commands will be removed.</span></span>

<span data-ttu-id="586cc-256">Als u de bron van een cmdlet in uw sessie wilt zoeken, gebruikt u de volgende opdracht indeling:</span><span class="sxs-lookup"><span data-stu-id="586cc-256">To find the source of a cmdlet in your session, use the following command format:</span></span>

```powershell
Get-Command <cmdlet-name> | Format-List -Property verb,noun,pssnapin,module
```

<span data-ttu-id="586cc-257">Als u bijvoorbeeld de bron van de cmdlet wilt zoeken `Get-Date` , typt u:</span><span class="sxs-lookup"><span data-stu-id="586cc-257">For example, to find the source of the `Get-Date` cmdlet, type:</span></span>

```powershell
Get-Command Get-Date | Format-List -Property verb,noun,module
```

## <a name="module-related-warnings-and-errors"></a><span data-ttu-id="586cc-258">Waarschuwingen en fouten met betrekking tot modules</span><span class="sxs-lookup"><span data-stu-id="586cc-258">Module-related Warnings and Errors</span></span>

<span data-ttu-id="586cc-259">De opdrachten die een module exporteert, moeten voldoen aan de naamgevings regels van de Power shell-opdracht.</span><span class="sxs-lookup"><span data-stu-id="586cc-259">The commands that a module exports should follow the PowerShell command naming rules.</span></span> <span data-ttu-id="586cc-260">Als de module die u importeert cmdlets of functies met een niet-goedgekeurde term in hun naam exporteert, `Import-Module` wordt de volgende waarschuwing weer gegeven in de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="586cc-260">If the module that you import exports cmdlets or functions that have unapproved verbs in their names, the `Import-Module` cmdlet displays the following warning message.</span></span>

> <span data-ttu-id="586cc-261">Waarschuwing: Sommige geïmporteerde opdracht namen bevatten niet-goedgekeurde werk woorden, waardoor ze minder kunnen worden gedetecteerd.</span><span class="sxs-lookup"><span data-stu-id="586cc-261">WARNING: Some imported command names include unapproved verbs which might make them less discoverable.</span></span> <span data-ttu-id="586cc-262">Gebruik de para meter uitgebreid voor meer details of typ Get-Verb om de lijst met goedgekeurde werk woorden weer te geven.</span><span class="sxs-lookup"><span data-stu-id="586cc-262">Use the Verbose parameter for more detail or type Get-Verb to see the list of approved verbs.</span></span>

<span data-ttu-id="586cc-263">Dit bericht wordt alleen een waarschuwing gegeven.</span><span class="sxs-lookup"><span data-stu-id="586cc-263">This message is only a warning.</span></span> <span data-ttu-id="586cc-264">De volledige module is nog steeds geïmporteerd, met inbegrip van de niet-conforme opdrachten.</span><span class="sxs-lookup"><span data-stu-id="586cc-264">The complete module is still imported, including the non-conforming commands.</span></span> <span data-ttu-id="586cc-265">Hoewel het bericht wordt weer gegeven voor module gebruikers, moet het naam probleem worden opgelost door de module auteur.</span><span class="sxs-lookup"><span data-stu-id="586cc-265">Although the message is displayed to module users, the naming problem should be fixed by the module author.</span></span>

<span data-ttu-id="586cc-266">Als u het waarschuwings bericht wilt onderdrukken, gebruikt u de para meter **DisableNameChecking** van de `Import-Module` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="586cc-266">To suppress the warning message, use the **DisableNameChecking** parameter of the `Import-Module` cmdlet.</span></span>

## <a name="built-in-modules-and-snap-ins"></a><span data-ttu-id="586cc-267">Ingebouwde modules en modules</span><span class="sxs-lookup"><span data-stu-id="586cc-267">Built-in Modules and Snap-ins</span></span>

<span data-ttu-id="586cc-268">In Power Shell 2,0 en in oudere host-Program ma's in Power Shell 3,0 en hoger, worden de kern opdrachten die met Power shell zijn geïnstalleerd, verpakt in modules die automatisch aan elke Power shell-sessie worden toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="586cc-268">In PowerShell 2.0 and in older-style host programs in PowerShell 3.0 and later, the core commands that are installed with PowerShell are packaged in snap-ins that are added automatically to every PowerShell session.</span></span>

<span data-ttu-id="586cc-269">Vanaf Power Shell 3,0 worden host-Program ma's die de `InitialSessionState.CreateDefault2` oorspronkelijke sessie status-API implementeren de module micro soft. Power shell. core, standaard aan elke sessie toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="586cc-269">Beginning in PowerShell 3.0, for host programs that implement the `InitialSessionState.CreateDefault2` initial session state API the Microsoft.PowerShell.Core snap-in is added to every session by default.</span></span> <span data-ttu-id="586cc-270">Modules worden automatisch geladen bij het eerste gebruik.</span><span class="sxs-lookup"><span data-stu-id="586cc-270">Modules are loaded automatically on first-use.</span></span>

> [!NOTE]
> <span data-ttu-id="586cc-271">Externe sessies, met inbegrip van sessies die zijn gestart met behulp van de `New-PSSession` cmdlet, zijn oudere sessies waarin de ingebouwde opdrachten zijn verpakt in modules.</span><span class="sxs-lookup"><span data-stu-id="586cc-271">Remote sessions, including sessions that are started by using the `New-PSSession` cmdlet, are older-style sessions in which the built-in commands are packaged in snap-ins.</span></span>

<span data-ttu-id="586cc-272">De volgende modules (of modules) worden geïnstalleerd met Power shell.</span><span class="sxs-lookup"><span data-stu-id="586cc-272">The following modules (or snap-ins) are installed with PowerShell.</span></span>

- <span data-ttu-id="586cc-273">CimCmdlets</span><span class="sxs-lookup"><span data-stu-id="586cc-273">CimCmdlets</span></span>
- <span data-ttu-id="586cc-274">Micro soft. Power shell. Archive</span><span class="sxs-lookup"><span data-stu-id="586cc-274">Microsoft.PowerShell.Archive</span></span>
- <span data-ttu-id="586cc-275">Micro soft. Power shell. core</span><span class="sxs-lookup"><span data-stu-id="586cc-275">Microsoft.PowerShell.Core</span></span>
- <span data-ttu-id="586cc-276">Micro soft. Power shell. Diagnostics</span><span class="sxs-lookup"><span data-stu-id="586cc-276">Microsoft.PowerShell.Diagnostics</span></span>
- <span data-ttu-id="586cc-277">Micro soft. Power shell. host</span><span class="sxs-lookup"><span data-stu-id="586cc-277">Microsoft.PowerShell.Host</span></span>
- <span data-ttu-id="586cc-278">Micro soft. Power shell. Management</span><span class="sxs-lookup"><span data-stu-id="586cc-278">Microsoft.PowerShell.Management</span></span>
- <span data-ttu-id="586cc-279">Micro soft. Power shell. Security</span><span class="sxs-lookup"><span data-stu-id="586cc-279">Microsoft.PowerShell.Security</span></span>
- <span data-ttu-id="586cc-280">Microsoft.PowerShell.Utility</span><span class="sxs-lookup"><span data-stu-id="586cc-280">Microsoft.PowerShell.Utility</span></span>
- <span data-ttu-id="586cc-281">Micro soft. WSMan. Management</span><span class="sxs-lookup"><span data-stu-id="586cc-281">Microsoft.WSMan.Management</span></span>
- <span data-ttu-id="586cc-282">PackageManagement</span><span class="sxs-lookup"><span data-stu-id="586cc-282">PackageManagement</span></span>
- <span data-ttu-id="586cc-283">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="586cc-283">PowerShellGet</span></span>
- <span data-ttu-id="586cc-284">PSDesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="586cc-284">PSDesiredStateConfiguration</span></span>
- <span data-ttu-id="586cc-285">PSDiagnostics</span><span class="sxs-lookup"><span data-stu-id="586cc-285">PSDiagnostics</span></span>
- <span data-ttu-id="586cc-286">PSReadline</span><span class="sxs-lookup"><span data-stu-id="586cc-286">PSReadline</span></span>

## <a name="logging-module-events"></a><span data-ttu-id="586cc-287">Logboek registratie module gebeurtenissen</span><span class="sxs-lookup"><span data-stu-id="586cc-287">Logging Module Events</span></span>

<span data-ttu-id="586cc-288">Vanaf Power Shell 3,0 kunt u uitvoerings gebeurtenissen vastleggen voor de cmdlets en functies in Power shell-modules en-modules door de eigenschap **LogPipelineExecutionDetails** van modules en modules in te stellen op `$True` .</span><span class="sxs-lookup"><span data-stu-id="586cc-288">Beginning in PowerShell 3.0, you can record execution events for the cmdlets and functions in PowerShell modules and snap-ins by setting the **LogPipelineExecutionDetails** property of modules and snap-ins to `$True`.</span></span>
<span data-ttu-id="586cc-289">U kunt ook een groepsbeleid instelling gebruiken, module logboek registratie inschakelen om module logboek registratie in te scha kelen in alle Power shell-sessies.</span><span class="sxs-lookup"><span data-stu-id="586cc-289">You can also use a Group Policy setting, Turn on Module Logging, to enable module logging in all PowerShell sessions.</span></span> <span data-ttu-id="586cc-290">Zie de artikelen logboek registratie en groeps beleid voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="586cc-290">For more information, see the logging and group policy articles.</span></span>

## <a name="see-also"></a><span data-ttu-id="586cc-291">Zie ook</span><span class="sxs-lookup"><span data-stu-id="586cc-291">See Also</span></span>

[<span data-ttu-id="586cc-292">about_Logging_Windows</span><span class="sxs-lookup"><span data-stu-id="586cc-292">about_Logging_Windows</span></span>](about_Logging_Windows.md)

[<span data-ttu-id="586cc-293">about_Logging_Non-Windows</span><span class="sxs-lookup"><span data-stu-id="586cc-293">about_Logging_Non-Windows</span></span>](about_Logging_Non-Windows.md)

[<span data-ttu-id="586cc-294">about_Group_Policy_Settings</span><span class="sxs-lookup"><span data-stu-id="586cc-294">about_Group_Policy_Settings</span></span>](about_Group_Policy_Settings.md)

[<span data-ttu-id="586cc-295">about_Command_Precedence</span><span class="sxs-lookup"><span data-stu-id="586cc-295">about_Command_Precedence</span></span>](about_Command_Precedence.md)

[<span data-ttu-id="586cc-296">about_Group_Policy_Settings</span><span class="sxs-lookup"><span data-stu-id="586cc-296">about_Group_Policy_Settings</span></span>](about_Group_Policy_Settings.md)

[<span data-ttu-id="586cc-297">Get-Command</span><span class="sxs-lookup"><span data-stu-id="586cc-297">Get-Command</span></span>](xref:Microsoft.PowerShell.Core.Get-Command)

[<span data-ttu-id="586cc-298">Get-Help</span><span class="sxs-lookup"><span data-stu-id="586cc-298">Get-Help</span></span>](xref:Microsoft.PowerShell.Core.Get-Help)

[<span data-ttu-id="586cc-299">Get-module</span><span class="sxs-lookup"><span data-stu-id="586cc-299">Get-Module</span></span>](xref:Microsoft.PowerShell.Core.Get-Module)

[<span data-ttu-id="586cc-300">Import-module</span><span class="sxs-lookup"><span data-stu-id="586cc-300">Import-Module</span></span>](xref:Microsoft.PowerShell.Core.Import-Module)

[<span data-ttu-id="586cc-301">Remove-module</span><span class="sxs-lookup"><span data-stu-id="586cc-301">Remove-Module</span></span>](xref:Microsoft.PowerShell.Core.Remove-Module)
