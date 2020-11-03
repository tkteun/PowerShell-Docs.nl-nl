---
description: Hierin wordt de Windows Power shell-compatibiliteits functionaliteit voor Power shell 7 beschreven.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 04/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_windows_powershell_compatibility?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Windows_PowerShell_Compatibility
ms.openlocfilehash: 522c9d2169e49584915450813ad28dfc5e0d5ca2
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252133"
---
# <a name="about-windows-powershell-compatibility"></a><span data-ttu-id="3ef1d-104">Over Windows Power shell-compatibiliteit</span><span class="sxs-lookup"><span data-stu-id="3ef1d-104">About Windows PowerShell compatibility</span></span>

## <a name="short-description"></a><span data-ttu-id="3ef1d-105">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="3ef1d-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="3ef1d-106">Hierin wordt de Windows Power shell-compatibiliteits functionaliteit voor Power shell 7 beschreven.</span><span class="sxs-lookup"><span data-stu-id="3ef1d-106">Describes the Windows PowerShell Compatibility functionality for PowerShell 7.</span></span>

## <a name="long-description"></a><span data-ttu-id="3ef1d-107">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="3ef1d-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="3ef1d-108">Tenzij in het manifest van de module wordt aangegeven dat de module compatibel is met Power shell core, worden modules in de `%windir%\system32\WindowsPowerShell\v1.0\Modules` map geladen in een achtergrond Windows Power shell 5,1-proces met Windows Power shell-compatibiliteits functie.</span><span class="sxs-lookup"><span data-stu-id="3ef1d-108">Unless the module manifest indicates that module is compatible with PowerShell Core, modules in the `%windir%\system32\WindowsPowerShell\v1.0\Modules` folder are loaded in a background Windows PowerShell 5.1 process by Windows PowerShell Compatibility feature.</span></span>

### <a name="using-the-compatibility-feature"></a><span data-ttu-id="3ef1d-109">De compatibiliteits functie gebruiken</span><span class="sxs-lookup"><span data-stu-id="3ef1d-109">Using the Compatibility feature</span></span>

<span data-ttu-id="3ef1d-110">Wanneer de eerste module wordt geïmporteerd met behulp van de Windows Power shell-compatibiliteits functie, maakt Power shell een externe sessie met de naam `WinPSCompatSession` die wordt uitgevoerd in een Windows Power shell 5,1-proces op de achtergrond.</span><span class="sxs-lookup"><span data-stu-id="3ef1d-110">When the first module is imported using Windows PowerShell Compatibility feature, PowerShell creates a remote session named `WinPSCompatSession` that is running in a background Windows PowerShell 5.1 process.</span></span> <span data-ttu-id="3ef1d-111">Dit proces wordt gemaakt wanneer met de compatibiliteits functie de eerste module wordt geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="3ef1d-111">This process is created when the Compatibility feature imports the first module.</span></span> <span data-ttu-id="3ef1d-112">Het proces wordt gesloten wanneer de laatste module wordt verwijderd (met `Remove-Module` ) of wanneer het Power Shell-proces wordt afgesloten.</span><span class="sxs-lookup"><span data-stu-id="3ef1d-112">The process is closed when the last such module is removed (using `Remove-Module`) or when PowerShell process exits.</span></span>

<span data-ttu-id="3ef1d-113">De modules die in de `WinPSCompatSession` sessie worden geladen, worden gebruikt via impliciete externe communicatie en worden weer gegeven in de huidige Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="3ef1d-113">The modules loaded in the `WinPSCompatSession` session are used via implicit remoting and reflected into current PowerShell session.</span></span> <span data-ttu-id="3ef1d-114">Dit is dezelfde transport methode die wordt gebruikt voor Power shell-taken.</span><span class="sxs-lookup"><span data-stu-id="3ef1d-114">This is the same transport method used for PowerShell jobs.</span></span>

<span data-ttu-id="3ef1d-115">Wanneer een module in de sessie wordt geïmporteerd `WinPSCompatSession` , wordt in impliciete externe toegang een proxy module in de map van de gebruiker gegenereerd `$env:Temp` en wordt deze proxy module in de huidige Power shell-sessie geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="3ef1d-115">When a module is imported into the `WinPSCompatSession` session, implicit remoting generates a proxy module in the user's `$env:Temp` directory and imports this proxy module into current PowerShell session.</span></span> <span data-ttu-id="3ef1d-116">Hierdoor kan Power shell detecteren dat de module is geladen met behulp van Windows Power shell-compatibiliteits functionaliteit.</span><span class="sxs-lookup"><span data-stu-id="3ef1d-116">This allows PowerShell to detect that the module was loaded using Windows PowerShell Compatibility functionality.</span></span>

<span data-ttu-id="3ef1d-117">Zodra de sessie is gemaakt, kan deze worden gebruikt voor bewerkingen die niet goed werken op gedeserialiseerd objecten.</span><span class="sxs-lookup"><span data-stu-id="3ef1d-117">Once the session is created, it can be used for operations that don't work correctly on deserialized objects.</span></span> <span data-ttu-id="3ef1d-118">De volledige pijp lijn wordt uitgevoerd in Windows Power shell en alleen het uiteindelijke resultaat wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="3ef1d-118">The entire pipeline is executed in Windows PowerShell and only the final result is returned.</span></span> <span data-ttu-id="3ef1d-119">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="3ef1d-119">For example:</span></span>

```powershell
$s = Get-PSSession -Name WinPSCompatSession
Invoke-Command -Session $s -ScriptBlock {
  "Running in Windows PowerShell version $($PSVersionTable.PSVersion)"
}
```

<span data-ttu-id="3ef1d-120">De compatibiliteits functie kan op twee manieren worden aangeroepen:</span><span class="sxs-lookup"><span data-stu-id="3ef1d-120">The Compatibility feature can be invoked in two ways:</span></span>

- <span data-ttu-id="3ef1d-121">Expliciet door een module te importeren met de para meter **UseWindowsPowerShell**</span><span class="sxs-lookup"><span data-stu-id="3ef1d-121">Explicitly by importing a module using the **UseWindowsPowerShell** parameter</span></span>

   ```powershell
   Import-Module -Name ScheduledTasks -UseWindowsPowerShell
   ```

- <span data-ttu-id="3ef1d-122">U kunt het importeren van een Windows Power shell-module per module naam, pad of autoload via opdracht detectie.</span><span class="sxs-lookup"><span data-stu-id="3ef1d-122">Implicitly by importing a Windows PowerShell module by module name, path, or autoloading via command discovery.</span></span>

   ```powershell
   Import-Module -Name ServerManager
   Get-AppLockerPolicy -Local
   ```

   <span data-ttu-id="3ef1d-123">Als dat nog niet is gebeurd, wordt de AppLocker-module tijdens het uitvoeren van opnieuw geladen  `Get-AppLockerPolicy` .</span><span class="sxs-lookup"><span data-stu-id="3ef1d-123">If not already loaded, the AppLocker module is autoloaded when you run  `Get-AppLockerPolicy`.</span></span>

<span data-ttu-id="3ef1d-124">Windows Power shell-compatibiliteit blokkeert het laden van modules die worden vermeld in de `WindowsPowerShellCompatibilityModuleDenyList` instelling in het Power shell-configuratie bestand.</span><span class="sxs-lookup"><span data-stu-id="3ef1d-124">Windows PowerShell Compatibility blocks loading of modules that are listed in the `WindowsPowerShellCompatibilityModuleDenyList` setting in PowerShell configuration file.</span></span>

<span data-ttu-id="3ef1d-125">De standaard waarde voor deze instelling is:</span><span class="sxs-lookup"><span data-stu-id="3ef1d-125">The default value of this setting is:</span></span>

```json
"WindowsPowerShellCompatibilityModuleDenyList":  [
   "PSScheduledJob","BestPractices","UpdateServices"
]
```

### <a name="managing-implicit-module-loading"></a><span data-ttu-id="3ef1d-126">Impliciete module laden beheren</span><span class="sxs-lookup"><span data-stu-id="3ef1d-126">Managing implicit module loading</span></span>

<span data-ttu-id="3ef1d-127">Als u het impliciete import gedrag van de Windows Power shell-compatibiliteits functie wilt uitschakelen, gebruikt u de `DisableImplicitWinCompat` instelling in een Power shell-configuratie bestand.</span><span class="sxs-lookup"><span data-stu-id="3ef1d-127">To disable implicit import behavior of the Windows PowerShell Compatibility feature, use the `DisableImplicitWinCompat` setting in a PowerShell configuration file.</span></span> <span data-ttu-id="3ef1d-128">Deze instelling kan worden toegevoegd aan het `powershell.config.json` bestand.</span><span class="sxs-lookup"><span data-stu-id="3ef1d-128">This setting can be added to the `powershell.config.json` file.</span></span> <span data-ttu-id="3ef1d-129">Zie [about_powershell_config](about_powershell_config.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="3ef1d-129">For more information, see [about_powershell_config](about_powershell_config.md).</span></span>

<span data-ttu-id="3ef1d-130">In dit voor beeld ziet u hoe u een configuratie bestand maakt waarmee de functie voor het laden van impliciete modules van Windows Power shell-compatibiliteit wordt uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="3ef1d-130">This example shows how to create a configuration file that disables the implicit module-loading feature of Windows PowerShell Compatibility.</span></span>

```powershell
$ConfigPath = "$PSHOME\DisableWinCompat.powershell.config.json"
$ConfigJSON = ConvertTo-Json -InputObject @{
  "DisableImplicitWinCompat" = $true
  "Microsoft.PowerShell:ExecutionPolicy" = "RemoteSigned"
}
$ConfigJSON | Out-File -Force $ConfigPath
pwsh -settingsFile $ConfigPath
```

<span data-ttu-id="3ef1d-131">Zie de compatibiliteits lijst van de [module Power shell 7](https://aka.ms/PSModuleCompat) voor meer informatie over de compatibiliteit van modules.</span><span class="sxs-lookup"><span data-stu-id="3ef1d-131">For more the latest information about module compatibility, see the [PowerShell 7 module compatibility](https://aka.ms/PSModuleCompat) list.</span></span>

### <a name="managing-cmdlet-clobbering"></a><span data-ttu-id="3ef1d-132">Cmdlet clobbering beheren</span><span class="sxs-lookup"><span data-stu-id="3ef1d-132">Managing cmdlet clobbering</span></span>

<span data-ttu-id="3ef1d-133">De Windows Power shell-compatibiliteits functie maakt gebruik van impliciete externe communicatie om modules in de compatibiliteits modus te laden.</span><span class="sxs-lookup"><span data-stu-id="3ef1d-133">The Windows PowerShell Compatibility feature uses implicit remoting to load modules in compatibility mode.</span></span> <span data-ttu-id="3ef1d-134">Het resultaat is dat opdrachten die door de module worden geëxporteerd, voor rang hebben op opdrachten met dezelfde naam in de huidige Power shell 7-sessie.</span><span class="sxs-lookup"><span data-stu-id="3ef1d-134">The result is that commands exported by the module take precedence over commands of the same name in the current PowerShell 7 session.</span></span> <span data-ttu-id="3ef1d-135">In de Power shell 7.0.0-versie zijn dit de kern modules die worden geleverd met Power shell.</span><span class="sxs-lookup"><span data-stu-id="3ef1d-135">In the PowerShell 7.0.0 release, this included the core modules that ship with PowerShell.</span></span>

<span data-ttu-id="3ef1d-136">In Power shell 7,1 is het gedrag gewijzigd, zodat de volgende Power shell-modules niet clobbered zijn:</span><span class="sxs-lookup"><span data-stu-id="3ef1d-136">In PowerShell 7.1, the behavior was changed so that the following core PowerShell modules are not clobbered:</span></span>

- <span data-ttu-id="3ef1d-137">Micro soft. Power shell. ConsoleHost</span><span class="sxs-lookup"><span data-stu-id="3ef1d-137">Microsoft.PowerShell.ConsoleHost</span></span>
- <span data-ttu-id="3ef1d-138">Micro soft. Power shell. Diagnostics</span><span class="sxs-lookup"><span data-stu-id="3ef1d-138">Microsoft.PowerShell.Diagnostics</span></span>
- <span data-ttu-id="3ef1d-139">Micro soft. Power shell. host</span><span class="sxs-lookup"><span data-stu-id="3ef1d-139">Microsoft.PowerShell.Host</span></span>
- <span data-ttu-id="3ef1d-140">Micro soft. Power shell. Management</span><span class="sxs-lookup"><span data-stu-id="3ef1d-140">Microsoft.PowerShell.Management</span></span>
- <span data-ttu-id="3ef1d-141">Micro soft. Power shell. Security</span><span class="sxs-lookup"><span data-stu-id="3ef1d-141">Microsoft.PowerShell.Security</span></span>
- <span data-ttu-id="3ef1d-142">Microsoft.PowerShell.Utility</span><span class="sxs-lookup"><span data-stu-id="3ef1d-142">Microsoft.PowerShell.Utility</span></span>
- <span data-ttu-id="3ef1d-143">Micro soft. WSMan. Management</span><span class="sxs-lookup"><span data-stu-id="3ef1d-143">Microsoft.WSMan.Management</span></span>

<span data-ttu-id="3ef1d-144">Power shell 7,1 heeft ook de mogelijkheid toegevoegd om extra modules weer te geven die niet moeten worden clobbered door de compatibiliteits modus.</span><span class="sxs-lookup"><span data-stu-id="3ef1d-144">PowerShell 7.1 also added the ability to list additional modules that should not be clobbered by compatibility mode.</span></span>

<span data-ttu-id="3ef1d-145">U kunt de `WindowsPowerShellCompatibilityNoClobberModuleList` instelling toevoegen aan het Power shell-configuratie bestand.</span><span class="sxs-lookup"><span data-stu-id="3ef1d-145">You can add the `WindowsPowerShellCompatibilityNoClobberModuleList` setting to PowerShell configuration file.</span></span> <span data-ttu-id="3ef1d-146">De waarde van deze instelling is een door komma's gescheiden lijst met module namen.</span><span class="sxs-lookup"><span data-stu-id="3ef1d-146">The value of this setting is a comma-separated list of module names.</span></span> <span data-ttu-id="3ef1d-147">De standaard waarde voor deze instelling is:</span><span class="sxs-lookup"><span data-stu-id="3ef1d-147">The default value of this setting is:</span></span>

```json
"WindowsPowerShellCompatibilityNoClobberModuleList": [ ]
```

## <a name="limitations"></a><span data-ttu-id="3ef1d-148">Beperkingen</span><span class="sxs-lookup"><span data-stu-id="3ef1d-148">Limitations</span></span>

<span data-ttu-id="3ef1d-149">De compatibiliteits functionaliteit van Windows Power shell:</span><span class="sxs-lookup"><span data-stu-id="3ef1d-149">The Windows PowerShell Compatibility functionality:</span></span>

1. <span data-ttu-id="3ef1d-150">Werkt alleen lokaal op Windows-computers</span><span class="sxs-lookup"><span data-stu-id="3ef1d-150">Only works locally on Windows computers</span></span>
1. <span data-ttu-id="3ef1d-151">Vereist dat Windows Power shell 5,1</span><span class="sxs-lookup"><span data-stu-id="3ef1d-151">Requires that Windows PowerShell 5.1</span></span>
1. <span data-ttu-id="3ef1d-152">Werkt op geserialiseerde cmdlet-para meters en retour waarden, niet op live-objecten</span><span class="sxs-lookup"><span data-stu-id="3ef1d-152">Operates on serialized cmdlet parameters and return values, not on live objects</span></span>
1. <span data-ttu-id="3ef1d-153">Alle modules die in de Windows Power shell-sessie voor externe toegang worden geïmporteerd, delen dezelfde runs Pace.</span><span class="sxs-lookup"><span data-stu-id="3ef1d-153">All modules imported into the Windows PowerShell remoting session share the same runspace.</span></span>

## <a name="keywords"></a><span data-ttu-id="3ef1d-154">Trefwoorden</span><span class="sxs-lookup"><span data-stu-id="3ef1d-154">Keywords</span></span>

<span data-ttu-id="3ef1d-155">about_Windows_PowerShell_Compatibility</span><span class="sxs-lookup"><span data-stu-id="3ef1d-155">about_Windows_PowerShell_Compatibility</span></span>

## <a name="see-also"></a><span data-ttu-id="3ef1d-156">Zie ook</span><span class="sxs-lookup"><span data-stu-id="3ef1d-156">See also</span></span>

[<span data-ttu-id="3ef1d-157">about_Modules</span><span class="sxs-lookup"><span data-stu-id="3ef1d-157">about_Modules</span></span>](about_Modules.md)

[<span data-ttu-id="3ef1d-158">Import-module</span><span class="sxs-lookup"><span data-stu-id="3ef1d-158">Import-Module</span></span>](xref:Microsoft.PowerShell.Core.Import-Module)

