---
description: De omgevings variabele PSModulePath bevat een lijst met maplocaties die worden doorzocht om modules en resources te zoeken.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 04/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_PSModulePath?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PSModulePath
ms.openlocfilehash: b904b01cc3fc63f32151885d040fe7b0e618f6d5
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252842"
---
# <a name="about-psmodulepath"></a><span data-ttu-id="e45d7-104">Over PSModulePath</span><span class="sxs-lookup"><span data-stu-id="e45d7-104">About PSModulePath</span></span>

<span data-ttu-id="e45d7-105">De `$env:PSModulePath` omgevings variabele bevat een lijst met maplocaties die worden doorzocht om modules en resources te zoeken.</span><span class="sxs-lookup"><span data-stu-id="e45d7-105">The `$env:PSModulePath` environment variable contains a list of folder locations that are searched to find modules and resources.</span></span>

<span data-ttu-id="e45d7-106">De doel locaties die worden toegewezen aan, `$env:PSModulePath` zijn standaard:</span><span class="sxs-lookup"><span data-stu-id="e45d7-106">By default, the effective locations assigned to `$env:PSModulePath` are:</span></span>

- <span data-ttu-id="e45d7-107">Locaties voor het hele systeem: deze mappen bevatten modules die worden geleverd met Power shell.</span><span class="sxs-lookup"><span data-stu-id="e45d7-107">System-wide locations: These folders contain modules that ship with PowerShell.</span></span> <span data-ttu-id="e45d7-108">Deze modules worden opgeslagen in de `$PSHOME\Modules` map.</span><span class="sxs-lookup"><span data-stu-id="e45d7-108">These modules are store in the `$PSHOME\Modules` folder.</span></span> <span data-ttu-id="e45d7-109">Dit is ook de locatie waar de Windows-beheer modules worden geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="e45d7-109">This is also the location where the Windows management modules are installed.</span></span>

- <span data-ttu-id="e45d7-110">Door de gebruiker geïnstalleerde modules: Dit zijn de modules die door de gebruiker zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="e45d7-110">User-installed modules: These are modules installed by the user.</span></span>
  <span data-ttu-id="e45d7-111">`Install-Module` heeft een **bereik** parameter waarmee u kunt opgeven of de module is geïnstalleerd voor de huidige gebruiker of voor alle gebruikers.</span><span class="sxs-lookup"><span data-stu-id="e45d7-111">`Install-Module` has a **Scope** parameter that allows you to specify whether the module is installed for the current user or for all users.</span></span> <span data-ttu-id="e45d7-112">Zie [install-module](xref:PowerShellGet.Install-Module)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="e45d7-112">For more information, see [Install-Module](xref:PowerShellGet.Install-Module).</span></span>

  - <span data-ttu-id="e45d7-113">In Windows is de locatie van **het gebruikersspecifieke Windows-bereik de** `$HOME\Documents\PowerShell\Modules` map.</span><span class="sxs-lookup"><span data-stu-id="e45d7-113">On Windows, the location of the user-specific **CurrentUser** scope is the `$HOME\Documents\PowerShell\Modules` folder.</span></span> <span data-ttu-id="e45d7-114">De locatie van het **ALLUSERS** bereik is `$env:ProgramFiles\PowerShell\Modules` .</span><span class="sxs-lookup"><span data-stu-id="e45d7-114">The location of the **AllUsers** scope is `$env:ProgramFiles\PowerShell\Modules`.</span></span>
  - <span data-ttu-id="e45d7-115">Op niet-Windows-systemen is de locatie van **het gebruikersspecifieke Windows-bereik de** `$HOME/.local/share/powershell/Modules` map.</span><span class="sxs-lookup"><span data-stu-id="e45d7-115">On non-Windows systems, the location of the user-specific **CurrentUser** scope is the `$HOME/.local/share/powershell/Modules` folder.</span></span> <span data-ttu-id="e45d7-116">De locatie van het **ALLUSERS** bereik is `/usr/local/share/powershell/Modules` .</span><span class="sxs-lookup"><span data-stu-id="e45d7-116">The location of the **AllUsers** scope is `/usr/local/share/powershell/Modules`.</span></span>

<span data-ttu-id="e45d7-117">Daarnaast kunnen installatie Programma's waarmee modules in andere directory's worden geïnstalleerd, zoals de map Program Files, hun locaties toevoegen aan de waarde van `$env:PSModulePath` .</span><span class="sxs-lookup"><span data-stu-id="e45d7-117">In addition, setup programs that install modules in other directories, such as the Program Files directory, can append their locations to the value of `$env:PSModulePath`.</span></span>

> [!NOTE]
> <span data-ttu-id="e45d7-118">In Windows is de gebruikerspecifieke locatie de `PowerShell\Modules` map die zich bevindt in de map **documenten** van uw gebruikers profiel.</span><span class="sxs-lookup"><span data-stu-id="e45d7-118">On Windows, the user-specific location is the `PowerShell\Modules` folder located in the **Documents** folder in your user profile.</span></span> <span data-ttu-id="e45d7-119">Het specifieke pad van die locatie is afhankelijk van de versie van Windows en of u nu Mapomleiding gebruikt.</span><span class="sxs-lookup"><span data-stu-id="e45d7-119">The specific path of that location varies by version of Windows and whether or not you are using folder redirection.</span></span> <span data-ttu-id="e45d7-120">Micro soft OneDrive kan ook de locatie van de map **documenten** wijzigen.</span><span class="sxs-lookup"><span data-stu-id="e45d7-120">Microsoft OneDrive can also change the location of your **Documents** folder.</span></span> <span data-ttu-id="e45d7-121">U kunt de locatie van uw **Documentenmap** controleren met behulp van de volgende opdracht: `[Environment]::GetFolderPath('MyDocuments')` .</span><span class="sxs-lookup"><span data-stu-id="e45d7-121">You can verify the location of your **Documents** folder using the following command: `[Environment]::GetFolderPath('MyDocuments')`.</span></span>

## <a name="modifying-psmodulepath"></a><span data-ttu-id="e45d7-122">PSModulePath wijzigen</span><span class="sxs-lookup"><span data-stu-id="e45d7-122">Modifying PSModulePath</span></span>

<span data-ttu-id="e45d7-123">Als u de standaard module mappen voor de huidige sessie wilt wijzigen, gebruikt u de volgende opdracht indeling om de waarde van de `PSModulePath` omgevings variabele te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="e45d7-123">To change the default module directories for the current session, use the following command format to change the value of the `PSModulePath` environment variable.</span></span>

<span data-ttu-id="e45d7-124">Als u bijvoorbeeld de `C:\Program Files\Fabrikam\Modules` map wilt toevoegen aan de waarde van de omgevings variabele PSModulePath, typt u:</span><span class="sxs-lookup"><span data-stu-id="e45d7-124">For example, to add the `C:\Program Files\Fabrikam\Modules` directory to the value of the PSModulePath environment variable, type:</span></span>

```powershell
$Env:PSModulePath = $Env:PSModulePath+";C:\Program Files\Fabrikam\Modules"
```

<span data-ttu-id="e45d7-125">De punt komma ( `;` ) in de opdracht scheidt u het nieuwe pad van het pad dat voorafgaat aan deze in de lijst.</span><span class="sxs-lookup"><span data-stu-id="e45d7-125">The semi-colon (`;`) in the command separates the new path from the path that precedes it in the list.</span></span> <span data-ttu-id="e45d7-126">Op niet-Windows-platforms scheidt de dubbele punt ( `:` ) de paden in de omgevings variabele.</span><span class="sxs-lookup"><span data-stu-id="e45d7-126">On non-Windows platforms, the colon (`:`) separates the path locations in the environment variable.</span></span>

<span data-ttu-id="e45d7-127">Als u de waarde van `PSModulePath` in elke sessie wilt wijzigen, voegt u de vorige opdracht toe aan uw Power shell-profiel of gebruikt u de methode **SetEnvironmentVariable** van de klasse **Environment** .</span><span class="sxs-lookup"><span data-stu-id="e45d7-127">To change the value of `PSModulePath` in every session, add the previous command to your PowerShell profile or use the **SetEnvironmentVariable** method of the **Environment** class.</span></span>

<span data-ttu-id="e45d7-128">De volgende opdracht maakt gebruik van de methode **GetEnvironmentVariable** om de computer instelling van `PSModulePath` en de methode **SetEnvironmentVariable** toe te voegen om het `C:\Program Files\Fabrikam\Modules` pad naar de waarde te kunnen toevoegen.</span><span class="sxs-lookup"><span data-stu-id="e45d7-128">The following command uses the **GetEnvironmentVariable** method to get the machine setting of `PSModulePath` and the **SetEnvironmentVariable** method to add the `C:\Program Files\Fabrikam\Modules` path to the value.</span></span>

```powershell
$path = [Environment]::GetEnvironmentVariable('PSModulePath', 'Machine')
$newpath = $path + ';C:\Program Files\Fabrikam\Modules'
[Environment]::SetEnvironmentVariable('PSModulePath', $newpath, 'Machine')
```

<span data-ttu-id="e45d7-129">Als u een pad wilt toevoegen aan de gebruikers instelling, wijzigt u de doel waarde in **gebruiker**.</span><span class="sxs-lookup"><span data-stu-id="e45d7-129">To add a path to the user setting, change the target value to **User**.</span></span>

```powershell
$path = [Environment]::GetEnvironmentVariable('PSModulePath', 'User')
$newpath = $path + ';C:\Program Files\Fabrikam\Modules'
[Environment]::SetEnvironmentVariable('PSModulePath', $newpath, 'User')
```

<span data-ttu-id="e45d7-130">Zie [omgevings methoden](/dotnet/api/system.environment)voor meer informatie over de methoden van de klasse **System. Environment** .</span><span class="sxs-lookup"><span data-stu-id="e45d7-130">For more information about the methods of the **System.Environment** class, see [Environment Methods](/dotnet/api/system.environment).</span></span>

## <a name="powershell-psmodulepath-construction"></a><span data-ttu-id="e45d7-131">Power shell PSModulePath-constructie</span><span class="sxs-lookup"><span data-stu-id="e45d7-131">PowerShell PSModulePath construction</span></span>

<span data-ttu-id="e45d7-132">De waarde van `$env:PSModulePath` wordt opgebouwd elke keer dat Power shell wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="e45d7-132">The value of `$env:PSModulePath` is constructed each time PowerShell starts.</span></span>
<span data-ttu-id="e45d7-133">De waarde is afhankelijk van de versie van Power shell en hoe deze wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="e45d7-133">The value varies by version of PowerShell and how it is launched.</span></span>

### <a name="windows-powershell-startup"></a><span data-ttu-id="e45d7-134">Windows Power shell starten</span><span class="sxs-lookup"><span data-stu-id="e45d7-134">Windows PowerShell startup</span></span>

<span data-ttu-id="e45d7-135">Windows Power shell gebruikt de volgende logica voor het maken `PSModulePath` van de bij het opstarten:</span><span class="sxs-lookup"><span data-stu-id="e45d7-135">Windows PowerShell uses the following logic to construct the `PSModulePath` at startup:</span></span>

- <span data-ttu-id="e45d7-136">Als dat niet het geval `PSModulePath` is, combi neer u **CurrentUser** , **ALLUSERS** en de paden van de `$PSHOME` modules</span><span class="sxs-lookup"><span data-stu-id="e45d7-136">If `PSModulePath` doesn't exist, combine **CurrentUser** , **AllUsers** , and the `$PSHOME` modules paths</span></span>
- <span data-ttu-id="e45d7-137">Als `PSModulePath` bestaat:</span><span class="sxs-lookup"><span data-stu-id="e45d7-137">If `PSModulePath` does exist:</span></span>
  - <span data-ttu-id="e45d7-138">If `PSModulePath` bevat `$PSHOME` pad naar modules:</span><span class="sxs-lookup"><span data-stu-id="e45d7-138">If `PSModulePath` contains `$PSHOME` modules path:</span></span>
    - <span data-ttu-id="e45d7-139">Pad naar **ALLUSERS** -modules wordt ingevoegd voor het `$PSHOME` pad naar de module</span><span class="sxs-lookup"><span data-stu-id="e45d7-139">**AllUsers** modules path is inserted before `$PSHOME` modules path</span></span>
  - <span data-ttu-id="e45d7-140">hierin</span><span class="sxs-lookup"><span data-stu-id="e45d7-140">else:</span></span>
    - <span data-ttu-id="e45d7-141">Alleen gebruiken `PSModulePath` zoals gedefinieerd, omdat de gebruiker de locatie opzettelijk heeft verwijderd `$PSHOME`</span><span class="sxs-lookup"><span data-stu-id="e45d7-141">Just use `PSModulePath` as defined since the user deliberately removed the `$PSHOME` location</span></span>

<span data-ttu-id="e45d7-142">Het pad van de **CurrentUser** -module wordt alleen voorafgegaan als het gebruikers bereik `$env:PSModulePath` niet bestaat.</span><span class="sxs-lookup"><span data-stu-id="e45d7-142">The **CurrentUser** module path is prefixed only if User scope `$env:PSModulePath` doesn't exist.</span></span> <span data-ttu-id="e45d7-143">Anders wordt het gebruikers bereik `$env:PSModulePath` gebruikt zoals gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="e45d7-143">Otherwise, the User scope `$env:PSModulePath` is used as defined.</span></span>

### <a name="powershell-core-6-startup"></a><span data-ttu-id="e45d7-144">Power shell Core 6 opstarten</span><span class="sxs-lookup"><span data-stu-id="e45d7-144">PowerShell Core 6 startup</span></span>

<span data-ttu-id="e45d7-145">Power shell Core 6 gebruikt geen inhoud van `$env:PSModulePath` als deze detecteert dat deze is gestart vanuit Power shell.</span><span class="sxs-lookup"><span data-stu-id="e45d7-145">PowerShell Core 6 doesn't use contents of `$env:PSModulePath` if it detects it was started from PowerShell.</span></span> <span data-ttu-id="e45d7-146">Deze overschrijft deze met:</span><span class="sxs-lookup"><span data-stu-id="e45d7-146">It overwrites it with:</span></span>

- <span data-ttu-id="e45d7-147">Het pad voor de **CurrentUser** -modules + **ALLUSERS** -modules pad + `$PSHOME` modules pad + Windows Power shell- `$PSHOME` modules pad.</span><span class="sxs-lookup"><span data-stu-id="e45d7-147">**CurrentUser** modules path + **AllUsers** modules path + `$PSHOME` modules path + Windows PowerShell `$PSHOME` modules path.</span></span>

### <a name="powershell-7-startup"></a><span data-ttu-id="e45d7-148">Opstarten in Power shell 7</span><span class="sxs-lookup"><span data-stu-id="e45d7-148">PowerShell 7 startup</span></span>

<span data-ttu-id="e45d7-149">In Windows gebruikt voor de meeste omgevings variabelen, als de door de gebruiker gedefinieerde variabele bestaat, alleen die waarde door een nieuw proces, zelfs als er al een variabele met dezelfde naam met een computer bereik is.</span><span class="sxs-lookup"><span data-stu-id="e45d7-149">In Windows, for most environment variables, if the User-scoped variable exists, a new process uses that value only even if a Machine-scoped variable of the same name exists.</span></span>

<span data-ttu-id="e45d7-150">In Power shell 7 `PSModulePath` wordt behandeld als de manier waarop de `Path` omgevings variabele wordt behandeld in Windows.</span><span class="sxs-lookup"><span data-stu-id="e45d7-150">In PowerShell 7, `PSModulePath` is treated similar to how the `Path` environment variable is treated on Windows.</span></span> <span data-ttu-id="e45d7-151">In Windows `Path` wordt op verschillende manieren een andere omgevings variabelen behandeld.</span><span class="sxs-lookup"><span data-stu-id="e45d7-151">On Windows, `Path` is treated differently from other environment variables.</span></span> <span data-ttu-id="e45d7-152">Wanneer een proces wordt gestart, wordt het gebruikers bereik gecombineerd `Path` met het bereik van de computer `Path` .</span><span class="sxs-lookup"><span data-stu-id="e45d7-152">When a process is started, Windows combines the User-scoped `Path` with the Machine-scoped `Path`.</span></span>

- <span data-ttu-id="e45d7-153">Het bereik van de gebruiker ophalen `PSModulePath`</span><span class="sxs-lookup"><span data-stu-id="e45d7-153">Retrieve the User-scoped `PSModulePath`</span></span>
- <span data-ttu-id="e45d7-154">Vergelijken met proces overgenomen `PSModulePath` omgevings variabele</span><span class="sxs-lookup"><span data-stu-id="e45d7-154">Compare to process inherited `PSModulePath` environment variable</span></span>
  - <span data-ttu-id="e45d7-155">Als hetzelfde:</span><span class="sxs-lookup"><span data-stu-id="e45d7-155">If the same:</span></span>
    - <span data-ttu-id="e45d7-156">De **ALLUSERS** toevoegen `PSModulePath` aan het eind na de semantiek van de `Path` omgevings variabele</span><span class="sxs-lookup"><span data-stu-id="e45d7-156">Append the **AllUsers** `PSModulePath` to the end following the semantics of the `Path` environment variable</span></span>
    - <span data-ttu-id="e45d7-157">Het Windows- `System32` pad is afkomstig van de computer die is gedefinieerd. `PSModulePath` Dit hoeft dus niet expliciet te worden toegevoegd</span><span class="sxs-lookup"><span data-stu-id="e45d7-157">The Windows `System32` path comes from the machine defined `PSModulePath` so does not need to be added explicitly</span></span>
  - <span data-ttu-id="e45d7-158">Als dit niet het geval is, wordt dit behandeld alsof de gebruiker deze expliciet heeft gewijzigd en niet **ALLUSERS** toevoegt `PSModulePath`</span><span class="sxs-lookup"><span data-stu-id="e45d7-158">If different, treat as though user explicitly modified it and don't append **AllUsers** `PSModulePath`</span></span>
- <span data-ttu-id="e45d7-159">Voor voegsel met PS7 gebruiker, systeem en `$PSHOME` paden in die volg orde</span><span class="sxs-lookup"><span data-stu-id="e45d7-159">Prefix with PS7 User, System, and `$PSHOME` paths in that order</span></span>
  - <span data-ttu-id="e45d7-160">Als `powershell.config.json` een gebruikers bereik bevat `PSModulePath` , gebruikt u dat in plaats van de standaard waarde voor de gebruiker</span><span class="sxs-lookup"><span data-stu-id="e45d7-160">If `powershell.config.json` contains a user scoped `PSModulePath`, use that instead of the default for the user</span></span>
  - <span data-ttu-id="e45d7-161">Als `powershell.config.json` een systeem bereik bevat `PSModulePath` , gebruikt u dit in plaats van de standaard waarde voor het systeem</span><span class="sxs-lookup"><span data-stu-id="e45d7-161">If `powershell.config.json` contains a system scoped `PSModulePath`, use that instead of the default for the system</span></span>

<span data-ttu-id="e45d7-162">UNIX-systemen hebben geen schei ding van gebruikers-en systeem omgevingsvariabelen.</span><span class="sxs-lookup"><span data-stu-id="e45d7-162">Unix systems don't have a separation of User and System environment variables.</span></span>
<span data-ttu-id="e45d7-163">`PSModulePath` wordt overgenomen en de PS7-specifieke paden worden voorafgegaan als nog niet gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="e45d7-163">`PSModulePath` is inherited and the PS7-specific paths are prefixed if not already defined.</span></span>

### <a name="starting-windows-powershell-from-powershell-7"></a><span data-ttu-id="e45d7-164">Windows Power shell starten vanuit Power shell 7</span><span class="sxs-lookup"><span data-stu-id="e45d7-164">Starting Windows PowerShell from PowerShell 7</span></span>

<span data-ttu-id="e45d7-165">Voor deze discussie betekent _Windows Power shell_ zowel `powershell.exe` als `powershell_ise.exe` .</span><span class="sxs-lookup"><span data-stu-id="e45d7-165">For this discussion, _Windows PowerShell_ means both `powershell.exe` and `powershell_ise.exe`.</span></span>

<span data-ttu-id="e45d7-166">De waarde van `$env:PSModulePath` wordt gekopieerd naar `WinPSModulePath` met de volgende wijzigingen:</span><span class="sxs-lookup"><span data-stu-id="e45d7-166">The value of `$env:PSModulePath` is copied to `WinPSModulePath` with the following modifications:</span></span>

- <span data-ttu-id="e45d7-167">PS7 het pad van de gebruikers module verwijderen</span><span class="sxs-lookup"><span data-stu-id="e45d7-167">Remove PS7 the User module path</span></span>
- <span data-ttu-id="e45d7-168">PS7 het pad naar de systeem module verwijderen</span><span class="sxs-lookup"><span data-stu-id="e45d7-168">Remove PS7 the System module path</span></span>
- <span data-ttu-id="e45d7-169">PS7 het pad van de `$PSHOME` module verwijderen</span><span class="sxs-lookup"><span data-stu-id="e45d7-169">Remove PS7 the `$PSHOME` module path</span></span>

<span data-ttu-id="e45d7-170">De PS7-paden worden verwijderd zodat PS7-modules niet worden geladen in Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="e45d7-170">The PS7 paths are removed so that PS7 modules don't get loaded in Windows PowerShell.</span></span> <span data-ttu-id="e45d7-171">De `WinPSModulePath` waarde wordt gebruikt bij het starten van Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="e45d7-171">The `WinPSModulePath` value is used when starting Windows PowerShell.</span></span>

### <a name="starting-powershell-7-from-windows-powershell"></a><span data-ttu-id="e45d7-172">Power shell 7 starten vanuit Windows Power shell</span><span class="sxs-lookup"><span data-stu-id="e45d7-172">Starting PowerShell 7 from Windows PowerShell</span></span>

<span data-ttu-id="e45d7-173">Het opstarten van Power shell 7 wordt voortgezet als-is met het toevoegen van overerving van paden die Windows Power Shell heeft toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="e45d7-173">The PowerShell 7 startup continues as-is with the addition of inheriting paths that Windows PowerShell added.</span></span> <span data-ttu-id="e45d7-174">Omdat de PS7-specifieke paden worden voorafgegaan, is er geen functioneel probleem.</span><span class="sxs-lookup"><span data-stu-id="e45d7-174">Since the PS7-specific paths are prefixed, there is no functional issue.</span></span>

### <a name="starting-powershell-6-from-powershell-7"></a><span data-ttu-id="e45d7-175">Power shell 6 starten vanuit Power shell 7</span><span class="sxs-lookup"><span data-stu-id="e45d7-175">Starting PowerShell 6 from PowerShell 7</span></span>

<span data-ttu-id="e45d7-176">Power shell Core 6 overschrijft `$env:PSModulePath` .</span><span class="sxs-lookup"><span data-stu-id="e45d7-176">PowerShell Core 6 overwrites `$env:PSModulePath`.</span></span> <span data-ttu-id="e45d7-177">Er zijn geen wijzigingen aangebracht.</span><span class="sxs-lookup"><span data-stu-id="e45d7-177">No changes are made.</span></span>

### <a name="starting-powershell-7-from-powershell-6"></a><span data-ttu-id="e45d7-178">Power shell 7 starten vanuit Power shell 6</span><span class="sxs-lookup"><span data-stu-id="e45d7-178">Starting PowerShell 7 from PowerShell 6</span></span>

<span data-ttu-id="e45d7-179">Het opstarten van Power shell 7 wordt voortgezet als-is met het toevoegen van paden die zijn toegevoegd aan Power shell Core 6.</span><span class="sxs-lookup"><span data-stu-id="e45d7-179">The PowerShell 7 startup continues as-is with the addition of inheriting paths that PowerShell Core 6 added.</span></span> <span data-ttu-id="e45d7-180">Omdat de PS7-specifieke paden worden voorafgegaan, is er geen functioneel probleem.</span><span class="sxs-lookup"><span data-stu-id="e45d7-180">Since the PS7-specific paths are prefixed, there is no functional issue.</span></span>

## <a name="see-also"></a><span data-ttu-id="e45d7-181">Zie ook</span><span class="sxs-lookup"><span data-stu-id="e45d7-181">See also</span></span>

- [<span data-ttu-id="e45d7-182">about_Modules</span><span class="sxs-lookup"><span data-stu-id="e45d7-182">about_Modules</span></span>](about_Modules.md)
- [<span data-ttu-id="e45d7-183">Omgevings methoden</span><span class="sxs-lookup"><span data-stu-id="e45d7-183">Environment Methods</span></span>](/dotnet/api/system.environment)