---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 5/16/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/update-help?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-Help
ms.openlocfilehash: 4ef0865e81e01746fed77b73e265e68086a7a9e1
ms.sourcegitcommit: d3f78120bdc9096c72aa0dfdbdd91efaf254c738
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/04/2020
ms.locfileid: "93251713"
---
# <span data-ttu-id="61e48-103">Update-Help</span><span class="sxs-lookup"><span data-stu-id="61e48-103">Update-Help</span></span>

## <span data-ttu-id="61e48-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="61e48-104">SYNOPSIS</span></span>
<span data-ttu-id="61e48-105">Downloadt en installeert de nieuwste Help-bestanden op uw computer.</span><span class="sxs-lookup"><span data-stu-id="61e48-105">Downloads and installs the newest help files on your computer.</span></span>

## <span data-ttu-id="61e48-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="61e48-106">SYNTAX</span></span>

### <span data-ttu-id="61e48-107">Pad (standaard)</span><span class="sxs-lookup"><span data-stu-id="61e48-107">Path (Default)</span></span>

```
Update-Help [[-Module] <String[]>] [-FullyQualifiedModule <ModuleSpecification[]>]
 [[-SourcePath] <String[]>] [-Recurse] [[-UICulture] <CultureInfo[]>] [-Credential <PSCredential>]
 [-UseDefaultCredentials] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="61e48-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="61e48-108">LiteralPath</span></span>

```
Update-Help [[-Module] <String[]>] [-FullyQualifiedModule <ModuleSpecification[]>]
 [-LiteralPath <String[]>] [-Recurse] [[-UICulture] <CultureInfo[]>] [-Credential <PSCredential>]
 [-UseDefaultCredentials] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="61e48-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="61e48-109">DESCRIPTION</span></span>

<span data-ttu-id="61e48-110">De `Update-Help` cmdlet downloadt de nieuwste Help-bestanden voor Power shell-modules en installeert deze op uw computer.</span><span class="sxs-lookup"><span data-stu-id="61e48-110">The `Update-Help` cmdlet downloads the newest help files for PowerShell modules and installs them on your computer.</span></span> <span data-ttu-id="61e48-111">U hoeft Power shell niet opnieuw op te starten om de wijziging van kracht te laten worden.</span><span class="sxs-lookup"><span data-stu-id="61e48-111">You need not restart PowerShell to make the change effective.</span></span> <span data-ttu-id="61e48-112">U kunt de `Get-Help` cmdlet gebruiken om de nieuwe Help-bestanden onmiddellijk weer te geven.</span><span class="sxs-lookup"><span data-stu-id="61e48-112">You can use the `Get-Help` cmdlet to view the new help files immediately.</span></span>

<span data-ttu-id="61e48-113">`Update-Help` Hiermee wordt de versie van de Help-bestanden op uw computer gecontroleerd.</span><span class="sxs-lookup"><span data-stu-id="61e48-113">`Update-Help` checks the version of the help files on your computer.</span></span> <span data-ttu-id="61e48-114">Als u geen Help-bestanden voor een module hebt of als uw Help-bestanden zijn verouderd, `Update-Help` downloadt de nieuwste Help-bestanden.</span><span class="sxs-lookup"><span data-stu-id="61e48-114">If you don't have help files for a module or if your help files are outdated, `Update-Help` downloads the newest help files.</span></span> <span data-ttu-id="61e48-115">De Help-bestanden kunnen worden gedownload en geïnstalleerd via internet of een bestands share.</span><span class="sxs-lookup"><span data-stu-id="61e48-115">The help files can be downloaded and installed from the internet or a file share.</span></span>

<span data-ttu-id="61e48-116">Zonder para meters worden `Update-Help` de Help-bestanden voor modules in de sessie en voor alle geïnstalleerde modules bijgewerkt die ondersteuning bieden voor bijwerk bare Help.</span><span class="sxs-lookup"><span data-stu-id="61e48-116">Without parameters, `Update-Help` updates the help files for modules in the session and for all installed modules that support Updatable Help.</span></span> <span data-ttu-id="61e48-117">Modules die zijn geïnstalleerd maar niet zijn geladen in de huidige sessie, worden opgenomen.</span><span class="sxs-lookup"><span data-stu-id="61e48-117">Modules that are installed but not loaded in the current session are included.</span></span> <span data-ttu-id="61e48-118">Power shell-modules worden opgeslagen op een locatie die wordt vermeld in de `$env:PSModulePath` omgevings variabele.</span><span class="sxs-lookup"><span data-stu-id="61e48-118">PowerShell modules are stored in a location listed in the `$env:PSModulePath` environment variable.</span></span> <span data-ttu-id="61e48-119">Zie [about_Updatable_Help](./About/about_Updatable_Help.md) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="61e48-119">For more information, see [about_Updatable_Help](./About/about_Updatable_Help.md).</span></span>

<span data-ttu-id="61e48-120">U kunt de **module** parameter gebruiken om Help-bestanden voor een bepaalde module bij te werken.</span><span class="sxs-lookup"><span data-stu-id="61e48-120">You can use the **Module** parameter to update help files for a particular module.</span></span> <span data-ttu-id="61e48-121">Gebruik de para meter **uiCulture** om Help-bestanden te downloaden in meerdere talen en land instellingen.</span><span class="sxs-lookup"><span data-stu-id="61e48-121">Use the **UICulture** parameter to download help files in multiple languages and locales.</span></span>

<span data-ttu-id="61e48-122">U kunt ook gebruiken `Update-Help` op computers die niet zijn verbonden met internet.</span><span class="sxs-lookup"><span data-stu-id="61e48-122">You can also use `Update-Help` on computers that are not connected to the internet.</span></span> <span data-ttu-id="61e48-123">Gebruik eerst de `Save-Help` cmdlet om Help-bestanden te downloaden van Internet en deze op te slaan in een gedeelde map die toegankelijk is voor het systeem dat niet is verbonden met internet.</span><span class="sxs-lookup"><span data-stu-id="61e48-123">First, use the `Save-Help`cmdlet to download help files from the internet and save them in a shared folder that is accessible to the system not connected to the internet.</span></span> <span data-ttu-id="61e48-124">Vervolgens gebruikt u de para meter **SourcePath** van `Update-Help` om de bijgewerkte Help-bestanden te downloaden van de gedeelde en te installeren op de computer.</span><span class="sxs-lookup"><span data-stu-id="61e48-124">Then use the **SourcePath** parameter of `Update-Help` to download the updated help files from the shared and install them on the computer.</span></span>

<span data-ttu-id="61e48-125">U kunt de Help-updates automatiseren door de cmdlet toe te voegen `Update-Help` aan uw Power shell-profiel.</span><span class="sxs-lookup"><span data-stu-id="61e48-125">You can automate help updates by adding the `Update-Help` cmdlet to your PowerShell profile.</span></span> <span data-ttu-id="61e48-126">Standaard `Update-Help` wordt slechts één keer per dag op elke computer uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="61e48-126">By default, `Update-Help` runs only one time per day on each computer.</span></span> <span data-ttu-id="61e48-127">Als u de limiet van één dag wilt overschrijven, gebruikt u de para meter **Force** .</span><span class="sxs-lookup"><span data-stu-id="61e48-127">To override the once-per-day limit, use the **Force** parameter.</span></span>

<span data-ttu-id="61e48-128">De `Update-Help` cmdlet is geïntroduceerd in Windows Power shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="61e48-128">The `Update-Help` cmdlet was introduced in Windows PowerShell 3.0.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="61e48-129">`Update-Help` beheerders bevoegdheden zijn vereist.</span><span class="sxs-lookup"><span data-stu-id="61e48-129">`Update-Help` requires administrative privileges.</span></span>
>
> <span data-ttu-id="61e48-130">U moet lid zijn van de groep Administrators op de computer om de Help-bestanden voor de Power shell core-modules bij te werken.</span><span class="sxs-lookup"><span data-stu-id="61e48-130">You must be a member of the Administrators group on the computer to update the help files for the PowerShell Core modules.</span></span>
>
> <span data-ttu-id="61e48-131">Als u de Help-bestanden voor modules in de Power shell-installatie directory ( `$PSHOME\Modules` ), inclusief de Power shell-kern modules, wilt downloaden of bijwerken, start u Power shell met de optie als administrator uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="61e48-131">To download or update the help files for modules in the PowerShell installation directory (`$PSHOME\Modules`), including the PowerShell Core modules, start PowerShell by using the Run as administrator option.</span></span>
> <span data-ttu-id="61e48-132">Bijvoorbeeld: `Start-Process powershell.exe -Verb RunAs`.</span><span class="sxs-lookup"><span data-stu-id="61e48-132">For example: `Start-Process powershell.exe -Verb RunAs`.</span></span>
>
> <span data-ttu-id="61e48-133">U kunt ook Help-bestanden bijwerken met behulp van het menu-item Windows Power shell Help bijwerken in het menu Help in Windows Power shell Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="61e48-133">You can also update help files by using the Update Windows PowerShell Help menu item in the Help menu in Windows PowerShell Integrated Scripting Environment (ISE).</span></span>
>
> <span data-ttu-id="61e48-134">Het Help-item update Windows Power Shell voert een `Update-Help` cmdlet zonder para meters uit.</span><span class="sxs-lookup"><span data-stu-id="61e48-134">The Update Windows PowerShell Help item runs an `Update-Help` cmdlet without parameters.</span></span>
> <span data-ttu-id="61e48-135">Als u de Help voor modules in de map wilt bijwerken `$PSHOME` , start u Windows PowerShell ISE met de optie als administrator uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="61e48-135">To update help for modules in the `$PSHOME` directory, start Windows PowerShell ISE by using the Run as administrator option.</span></span>

## <span data-ttu-id="61e48-136">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="61e48-136">EXAMPLES</span></span>

### <span data-ttu-id="61e48-137">Voor beeld 1: Help-bestanden voor alle modules bijwerken</span><span class="sxs-lookup"><span data-stu-id="61e48-137">Example 1: Update help files for all modules</span></span>

<span data-ttu-id="61e48-138">De `Update-Help` cmdlet werkt Help-bestanden bij voor geïnstalleerde modules die kunnen worden bijgewerkt met ondersteuning.</span><span class="sxs-lookup"><span data-stu-id="61e48-138">The `Update-Help` cmdlet updates help files for installed modules that support Updatable Help.</span></span> <span data-ttu-id="61e48-139">De cultuur taal van de gebruikers interface (UI) is ingesteld in het besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="61e48-139">The user-interface (UI) culture language is set in the operating system.</span></span>

```powershell
Update-Help
```

### <span data-ttu-id="61e48-140">Voor beeld 2: Help-bestanden voor opgegeven modules bijwerken</span><span class="sxs-lookup"><span data-stu-id="61e48-140">Example 2: Update help files for specified modules</span></span>

<span data-ttu-id="61e48-141">De `Update-Help` cmdlet updatet alleen Help-bestanden voor module namen die beginnen met **micro soft. Power shell**.</span><span class="sxs-lookup"><span data-stu-id="61e48-141">The `Update-Help` cmdlet updates help files only for module names that begin with **Microsoft.PowerShell**.</span></span>

```powershell
Update-Help -Module Microsoft.PowerShell*
```

### <span data-ttu-id="61e48-142">Voor beeld 3: Help-bestanden voor verschillende talen bijwerken</span><span class="sxs-lookup"><span data-stu-id="61e48-142">Example 3: Update help files for different languages</span></span>

<span data-ttu-id="61e48-143">`Update-Help`Met de cmdlet worden de Japanse (ja-JP) en de Engelse (en-US) Help-bestanden voor alle modules bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="61e48-143">The `Update-Help` cmdlet updates the Japanese (ja-JP) and English (en-US) help files for all modules.</span></span>

<span data-ttu-id="61e48-144">Als een module geen Help-bestanden voor een opgegeven UI-cultuur biedt, wordt een fout bericht weer gegeven voor de module en de UI-cultuur.</span><span class="sxs-lookup"><span data-stu-id="61e48-144">If a module doesn't provide help files for a specified UI culture, an error message is displayed for the module and UI culture.</span></span> <span data-ttu-id="61e48-145">In dit voor beeld geeft het fout bericht aan dat de Help-bestanden van **ja-jp** niet zijn gevonden voor de module **micro soft. Power shell. Utility**.</span><span class="sxs-lookup"><span data-stu-id="61e48-145">In this example, the error message indicates that the **ja-JP** help files were not found for module **Microsoft.PowerShell.Utility**.</span></span>

```powershell
Update-Help -UICulture ja-JP, en-US
```

```Output
Update-Help : Failed to update Help for the module(s) 'Microsoft.PowerShell.Utility' with UI culture(s) {ja-JP}
No UI culture was found that matches the following pattern: ja-JP.
```

### <span data-ttu-id="61e48-146">Voor beeld 4: Help-bestanden automatisch bijwerken</span><span class="sxs-lookup"><span data-stu-id="61e48-146">Example 4: Update help files automatically</span></span>

<span data-ttu-id="61e48-147">In dit voor beeld wordt een geplande taak gemaakt die elke dag om 3:00 uur Help voor alle modules bijwerkt.</span><span class="sxs-lookup"><span data-stu-id="61e48-147">This example creates a scheduled job that updates help for all modules every day at 3:00 AM.</span></span>

```powershell
$jobParams = @{
  Name = 'UpdateHelpJob'
  Credential = 'Domain01\User01'
  ScriptBlock = '{Update-Help}'
  Trigger = (New-JobTrigger -Daily -At "3 AM")
}
Register-ScheduledJob @jobParams
```

```Output
Id         Name            JobTriggers     Command                                  Enabled
--         ----            -----------     -------                                  -------
1          UpdateHelpJob   1               Update-Help                              True
```

<span data-ttu-id="61e48-148">`Register-ScheduledJob`Met de cmdlet wordt een geplande taak gemaakt waarmee een opdracht wordt uitgevoerd `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="61e48-148">The `Register-ScheduledJob` cmdlet creates a scheduled job that runs an `Update-Help` command.</span></span> <span data-ttu-id="61e48-149">De opdracht gebruikt de para meter **Credential** om uit te voeren met `Update-Help` behulp van de referenties van een lid van de groep Administrators op de computer.</span><span class="sxs-lookup"><span data-stu-id="61e48-149">The command uses the **Credential** parameter to run `Update-Help` by using the credentials of a member of the Administrators group on the computer.</span></span> <span data-ttu-id="61e48-150">De waarde van de **trigger** parameter is een `New-JobTrigger` opdracht waarmee een taak trigger wordt gemaakt waarmee de taak elke dag om 3:00 uur wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="61e48-150">The value of the **Trigger** parameter is a `New-JobTrigger` command that creates a job trigger that starts the job every day at 3:00 AM.</span></span>

<span data-ttu-id="61e48-151">Als u de `Register-ScheduledJob` opdracht wilt uitvoeren, start u Power shell met de optie **als administrator uitvoeren** .</span><span class="sxs-lookup"><span data-stu-id="61e48-151">To run the `Register-ScheduledJob` command, start PowerShell by using the **Run as administrator** option.</span></span> <span data-ttu-id="61e48-152">Power shell vraagt u om het wacht woord van de gebruiker opgegeven in de para meter **Credential** .</span><span class="sxs-lookup"><span data-stu-id="61e48-152">PowerShell prompts you for the password of the user specified in the **Credential** parameter.</span></span> <span data-ttu-id="61e48-153">De referenties worden opgeslagen met de geplande taak.</span><span class="sxs-lookup"><span data-stu-id="61e48-153">The credentials are stored with the scheduled job.</span></span> <span data-ttu-id="61e48-154">U wordt niet gevraagd wanneer de taak wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="61e48-154">You aren't prompted when the job runs.</span></span>

<span data-ttu-id="61e48-155">U kunt de `Get-ScheduledJob` cmdlet gebruiken om de geplande taak weer te geven, de `Set-ScheduledJob` cmdlet te gebruiken om deze te wijzigen en de `Unregister-ScheduledJob` cmdlet te gebruiken om deze te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="61e48-155">You can use the `Get-ScheduledJob` cmdlet to view the scheduled job, use the `Set-ScheduledJob` cmdlet to change it, and use the `Unregister-ScheduledJob` cmdlet to delete it.</span></span> <span data-ttu-id="61e48-156">U kunt de geplande taak ook weer geven en beheren in taak planner in het volgende pad:</span><span class="sxs-lookup"><span data-stu-id="61e48-156">You can also view and manage the scheduled job in Task Scheduler in the following path:</span></span>

<span data-ttu-id="61e48-157">`Task Scheduler Library\Microsoft\Windows\PowerShell\ScheduledJobs`.</span><span class="sxs-lookup"><span data-stu-id="61e48-157">`Task Scheduler Library\Microsoft\Windows\PowerShell\ScheduledJobs`.</span></span>

### <span data-ttu-id="61e48-158">Voor beeld 5: Help-bestanden op meerdere computers bijwerken vanuit een bestands share</span><span class="sxs-lookup"><span data-stu-id="61e48-158">Example 5: Update help files on multiple computers from a file share</span></span>

<span data-ttu-id="61e48-159">In dit voor beeld worden bijgewerkte Help-bestanden gedownload van Internet en opgeslagen in een bestands share.</span><span class="sxs-lookup"><span data-stu-id="61e48-159">In this example, updated help files are downloaded from the internet and saved in a file share.</span></span> <span data-ttu-id="61e48-160">Er zijn gebruikers referenties nodig die machtigingen hebben voor toegang tot de bestands share en om updates te installeren.</span><span class="sxs-lookup"><span data-stu-id="61e48-160">User credentials are needed that have permissions to access the file share and install updates.</span></span> <span data-ttu-id="61e48-161">Wanneer een bestands share wordt gebruikt, is het mogelijk om computers bij te werken die zich achter een firewall bevinden of die niet zijn verbonden met internet.</span><span class="sxs-lookup"><span data-stu-id="61e48-161">When a file share is used, it's possible to update computers that are behind firewalls or aren't connected to the internet.</span></span>

```powershell
Save-Help -DestinationPath \\Server01\Share\PSHelp -Credential Domain01\Admin01
Invoke-Command -ComputerName (Get-Content Servers.txt) -ScriptBlock {
     Update-Help -SourcePath \\Server01\Share\PSHelp -Credential Domain01\Admin01
}
```

<span data-ttu-id="61e48-162">`Save-Help`Met de opdracht worden de nieuwste Help-bestanden gedownload voor alle modules die kunnen worden bijgewerkt met ondersteuning.</span><span class="sxs-lookup"><span data-stu-id="61e48-162">The `Save-Help` command downloads the newest help files for all modules that support Updatable Help.</span></span>
<span data-ttu-id="61e48-163">Met de para meter **doelpad** worden de bestanden opgeslagen in de `\\Server01\Share\PSHelp` Bestands share.</span><span class="sxs-lookup"><span data-stu-id="61e48-163">The **DestinationPath** parameter saves the files in the `\\Server01\Share\PSHelp` file share.</span></span> <span data-ttu-id="61e48-164">De **referentie** parameter geeft u een gebruiker op die toegang heeft tot de bestands share.</span><span class="sxs-lookup"><span data-stu-id="61e48-164">The **Credential** parameter specifies a user who has permission to access the file share.</span></span>

<span data-ttu-id="61e48-165">`Invoke-Command`Met de cmdlet worden externe `Update-Help` opdrachten op meerdere computers uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="61e48-165">The `Invoke-Command` cmdlet runs remote `Update-Help` commands on multiple computers.</span></span> <span data-ttu-id="61e48-166">De para meter **ComputerName** haalt een lijst op met externe computers uit het **Servers.txt** -bestand.</span><span class="sxs-lookup"><span data-stu-id="61e48-166">The **ComputerName** parameter gets a list of remote computers from the **Servers.txt** file.</span></span> <span data-ttu-id="61e48-167">De para meter **script Block** voert de `Update-Help` opdracht uit en gebruikt de para meter **SourcePath** om de bestands share op te geven die de bijgewerkte Help-bestanden bevat.</span><span class="sxs-lookup"><span data-stu-id="61e48-167">The **ScriptBlock** parameter runs the `Update-Help` command and uses the **SourcePath** parameter to specify the file share that contains the updated help files.</span></span> <span data-ttu-id="61e48-168">De **referentie** parameter geeft u een gebruiker die toegang heeft tot de bestands share en voert u de opdracht extern uit `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="61e48-168">The **Credential** parameter specifies a user who can access the file share and run the remote `Update-Help` command.</span></span>

### <span data-ttu-id="61e48-169">Voor beeld 6: een lijst met bijgewerkte Help-bestanden ophalen</span><span class="sxs-lookup"><span data-stu-id="61e48-169">Example 6: Get a list of updated help files</span></span>

<span data-ttu-id="61e48-170">De `Update-Help` cmdlet Update Help voor een opgegeven module.</span><span class="sxs-lookup"><span data-stu-id="61e48-170">The `Update-Help` cmdlet updates help for a specified module.</span></span> <span data-ttu-id="61e48-171">De cmdlet gebruikt de **uitgebreide** para meter common om de lijst met Help-bestanden weer te geven die zijn bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="61e48-171">The cmdlet uses the **Verbose** common parameter to display the list of help files that were updated.</span></span> <span data-ttu-id="61e48-172">U kunt **uitgebreid** gebruiken om de uitvoer voor alle Help-bestanden of Help-bestanden voor een specifieke module weer te geven.</span><span class="sxs-lookup"><span data-stu-id="61e48-172">You can use **Verbose** to view output for all help files or help files for a specific module.</span></span>

<span data-ttu-id="61e48-173">Zonder de para meter **uitgebreid** worden `Update-Help` de resultaten van de opdracht niet weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="61e48-173">Without the **Verbose** parameter, `Update-Help` doesn't display the results of the command.</span></span> <span data-ttu-id="61e48-174">De **uitgebreide** para meter uitvoer is handig om te controleren of de Help-bestanden zijn bijgewerkt of of de meest recente versie is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="61e48-174">The **Verbose** parameter output is useful to verify that the help files were updated or if the latest version is installed.</span></span>

```powershell
Update-Help -Module Microsoft.PowerShell.Utility -Verbose
```

### <span data-ttu-id="61e48-175">Voor beeld 7: modules zoeken die kunnen worden bijgewerkt met ondersteuning</span><span class="sxs-lookup"><span data-stu-id="61e48-175">Example 7: Find modules that support Updatable Help</span></span>

<span data-ttu-id="61e48-176">In dit voor beeld wordt een lijst weer gegeven met de modules die kunnen worden bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="61e48-176">This example lists modules that support Updatable Help.</span></span> <span data-ttu-id="61e48-177">De opdracht maakt gebruik van de eigenschap **HelpInfoUri** van de module om modules te identificeren die ondersteunende Help kunnen ondersteunen.</span><span class="sxs-lookup"><span data-stu-id="61e48-177">The command uses the module's **HelpInfoUri** property to identify modules that support Updatable Help.</span></span> <span data-ttu-id="61e48-178">De eigenschap **HelpInfoUri** bevat een adres dat wordt omgeleid wanneer de `Update-Help` cmdlet wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="61e48-178">The **HelpInfoUri** property contains an address that is redirected when the `Update-Help` cmdlet is run.</span></span>

```powershell
Get-Module -ListAvailable | Where-Object -Property HelpInfoUri
```

```output
   Directory: C:\program files\powershell\6\Modules

ModuleType Version    Name                                PSEdition ExportedCommands
---------- -------    ----                                --------- ----------------
Manifest   6.1.0.0    CimCmdlets                          Core      {Get-CimAssociatedInstance... }
Manifest   1.2.2.0    Microsoft.PowerShell.Archive        Desk      {Compress-Archive... }
Manifest   6.1.0.0    Microsoft.PowerShell.Diagnostics    Core      {Get-WinEvent, New-WinEvent}

    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                                PSEdition ExportedCommands
---------- -------    ----                                --------- ----------------
Manifest   2.0.1.0    Appx                                Core,Desk {Add-AppxPackage, ... }
Script     1.0.0.0    AssignedAccess                      Core,Desk {Clear-AssignedAccess, ... }
Manifest   1.0.0.0    BitLocker                           Core,Desk {Unlock-BitLocker, ... }
```

### <span data-ttu-id="61e48-179">Voor beeld 8: bijgewerkte Help-bestanden met voor Raad</span><span class="sxs-lookup"><span data-stu-id="61e48-179">Example 8: Inventory updated help files</span></span>

<span data-ttu-id="61e48-180">In dit voor beeld maakt het script `Get-UpdateHelpVersion.ps1` een inventarisatie van de Help-bestanden die kunnen worden bijgewerkt voor elke module en de bijbehorende versie nummers.</span><span class="sxs-lookup"><span data-stu-id="61e48-180">In this example, the script `Get-UpdateHelpVersion.ps1` creates an inventory of the Updatable Help files for each module and their version numbers.</span></span>

<span data-ttu-id="61e48-181">Met het script worden modules geïdentificeerd die ondersteuning bieden voor Help bij het gebruik van de eigenschap **HelpInfoUri** van modules.</span><span class="sxs-lookup"><span data-stu-id="61e48-181">The script identifies modules that support Updatable Help by using the **HelpInfoUri** property of modules.</span></span> <span data-ttu-id="61e48-182">Voor modules die kunnen worden bijgewerkt met ondersteuning, zoekt het script naar het Help-informatie bestand (\* helpinfo.xml) en parseert het naar het meest recente versie nummer.</span><span class="sxs-lookup"><span data-stu-id="61e48-182">For modules that support Updatable Help, the script looks for and parses the help information file (\*helpinfo.xml) to find the latest version number.</span></span>

<span data-ttu-id="61e48-183">Het script maakt gebruik van de **PSCustomObject** -klasse en een hash-tabel om een aangepast uitvoer object te maken.</span><span class="sxs-lookup"><span data-stu-id="61e48-183">The script uses the **PSCustomObject** class and a hash table to create a custom output object.</span></span>

```powershell
# Get-UpdateHelpVersion.ps1
Param(
    [parameter(Mandatory=$False)]
    [String[]]
    $Module
)
$HelpInfoNamespace = @{helpInfo='http://schemas.microsoft.com/powershell/help/2010/05'}

if ($Module) { $Modules = Get-Module $Module -ListAvailable | where {$_.HelpInfoUri} }
else { $Modules = Get-Module -ListAvailable | where {$_.HelpInfoUri} }

foreach ($mModule in $Modules)
{
    $mDir = $mModule.ModuleBase

    if (Test-Path $mdir\*helpinfo.xml)
    {
        $mName=$mModule.Name
        $mNodes = dir $mdir\*helpinfo.xml -ErrorAction SilentlyContinue |
            Select-Xml -Namespace $HelpInfoNamespace -XPath "//helpInfo:UICulture"
        foreach ($mNode in $mNodes)
        {
            $mCulture=$mNode.Node.UICultureName
            $mVer=$mNode.Node.UICultureVersion

            [PSCustomObject]@{"ModuleName"=$mName; "Culture"=$mCulture; "Version"=$mVer}
        }
    }
}
```

```Output
ModuleName                              Culture                                 Version
----------                              -------                                 -------
ActiveDirectory                         en-US                                   3.0.0.0
ADCSAdministration                      en-US                                   3.0.0.0
ADCSDeployment                          en-US                                   3.0.0.0
ADDSDeployment                          en-US                                   3.0.0.0
ADFS                                    en-US                                   3.0.0.0
```

## <span data-ttu-id="61e48-184">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="61e48-184">PARAMETERS</span></span>

### <span data-ttu-id="61e48-185">-Credential</span><span class="sxs-lookup"><span data-stu-id="61e48-185">-Credential</span></span>

<span data-ttu-id="61e48-186">Hiermee geeft u de referenties op van een gebruiker die toegang heeft tot de locatie van het bestands systeem die is opgegeven door **SourcePath**.</span><span class="sxs-lookup"><span data-stu-id="61e48-186">Specifies credentials of a user who has permission to access the file system location specified by **SourcePath**.</span></span> <span data-ttu-id="61e48-187">Deze para meter is alleen geldig als de para meter **SourcePath** of **LiteralPath** in de opdracht wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="61e48-187">This parameter is valid only when the **SourcePath** or **LiteralPath** parameter is used in the command.</span></span>

<span data-ttu-id="61e48-188">Met de para meter **Credential** kunt u `Update-Help` opdrachten uitvoeren met de para meter **SourcePath** op externe computers.</span><span class="sxs-lookup"><span data-stu-id="61e48-188">The **Credential** parameter enables you to run `Update-Help` commands with the **SourcePath** parameter on remote computers.</span></span> <span data-ttu-id="61e48-189">Door expliciete referenties op te geven, kunt u de opdracht uitvoeren op een externe computer en toegang krijgen tot een bestands share op een derde computer zonder dat er een fout wordt geweigerd of als CredSSP-verificatie wordt gebruikt voor het delegeren van referenties.</span><span class="sxs-lookup"><span data-stu-id="61e48-189">By providing explicit credentials, you can run the command on a remote computer and access a file share on a third computer without encountering an access denied error or using CredSSP authentication to delegate credentials.</span></span>

<span data-ttu-id="61e48-190">Typ een gebruikers naam, zoals **gebruiker01** of **Domain01\User01** , of voer een **PSCredential** -object in dat door de cmdlet wordt gegenereerd `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="61e48-190">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="61e48-191">Als u een gebruikers naam typt, wordt u gevraagd het wacht woord in te voeren.</span><span class="sxs-lookup"><span data-stu-id="61e48-191">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="61e48-192">Referenties worden opgeslagen in een [PSCredential](/dotnet/api/system.management.automation.pscredential) -object en het wacht woord wordt opgeslagen als [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="61e48-192">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="61e48-193">Zie [Hoe veilig is securestring?](/dotnet/api/system.security.securestring#how-secure-is-securestring)voor meer informatie over **securestring** Data Protection.</span><span class="sxs-lookup"><span data-stu-id="61e48-193">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="61e48-194">-Force</span><span class="sxs-lookup"><span data-stu-id="61e48-194">-Force</span></span>

<span data-ttu-id="61e48-195">Geeft aan dat deze cmdlet niet de beperking van één dag volgt, de versie controle overs laat en bestanden downloadt die de limiet van 1 GB overschrijden.</span><span class="sxs-lookup"><span data-stu-id="61e48-195">Indicates that this cmdlet doesn't follow the once-per-day limitation, skips version checking, and downloads files that exceed the 1 GB limit.</span></span>

<span data-ttu-id="61e48-196">Zonder deze para meter `Update-Help` wordt slechts één keer per periode van 24 uur uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="61e48-196">Without this parameter, `Update-Help` runs only once in each 24-hour period.</span></span> <span data-ttu-id="61e48-197">Down loads zijn beperkt tot 1 GB aan niet-gecomprimeerde inhoud per module en Help-bestanden worden alleen geïnstalleerd wanneer ze nieuwer zijn dan de bestaande bestanden op de computer.</span><span class="sxs-lookup"><span data-stu-id="61e48-197">Downloads are limited to 1 GB of uncompressed content per module and help files are only installed when they're newer than the existing files on the computer.</span></span>

<span data-ttu-id="61e48-198">De limiet van één dag beveiligt de servers die als host dienen voor de Help-bestanden en maken het praktisch om een opdracht toe te voegen `Update-Help` aan uw Power shell-profiel zonder de resource kosten van herhaalde verbindingen of down loads te maken.</span><span class="sxs-lookup"><span data-stu-id="61e48-198">The once-per-day limit protects the servers that host the help files and makes it practical for you to add an `Update-Help` command to your PowerShell profile without incurring the resource cost of repeated connections or downloads.</span></span>

<span data-ttu-id="61e48-199">Als u de Help voor een module in meerdere GEBRUIKERSINTERFACE culturen wilt bijwerken zonder de para meter **Force** , neemt u alle gebruikersinterface culturen op in dezelfde opdracht, zoals:</span><span class="sxs-lookup"><span data-stu-id="61e48-199">To update help for a module in multiple UI cultures without the **Force** parameter, include all UI cultures in the same command, such as:</span></span>

`Update-Help -Module PSScheduledJobs -UICulture en-US, fr-FR, pt-BR`

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="61e48-200">-FullyQualifiedModule</span><span class="sxs-lookup"><span data-stu-id="61e48-200">-FullyQualifiedModule</span></span>

<span data-ttu-id="61e48-201">Hiermee geeft u modules op met namen die zijn opgegeven in de vorm van **ModuleSpecification** -objecten.</span><span class="sxs-lookup"><span data-stu-id="61e48-201">Specifies modules with names that are specified in the form of **ModuleSpecification** objects.</span></span>
<span data-ttu-id="61e48-202">Deze modules worden beschreven in de sectie opmerkingen van de [ModuleSpecification-constructor (hashtabel)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span><span class="sxs-lookup"><span data-stu-id="61e48-202">These modules are described in the Remarks section of [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span></span>

<span data-ttu-id="61e48-203">De para meter **FullyQualifiedModule** accepteert bijvoorbeeld een module naam die is opgegeven in de indeling:</span><span class="sxs-lookup"><span data-stu-id="61e48-203">For example, the **FullyQualifiedModule** parameter accepts a module name that is specified in the format:</span></span>

`@{ModuleName = "modulename"; ModuleVersion = "version_number"}`

<span data-ttu-id="61e48-204">of</span><span class="sxs-lookup"><span data-stu-id="61e48-204">or</span></span>

`@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}.`

<span data-ttu-id="61e48-205">**Module** naam en **ModuleVersion** zijn vereist, maar **GUID** is optioneel.</span><span class="sxs-lookup"><span data-stu-id="61e48-205">**ModuleName** and **ModuleVersion** are required, but **Guid** is optional.</span></span>

<span data-ttu-id="61e48-206">U kunt de para meter **FullyQualifiedModule** niet opgeven in dezelfde opdracht als een **module** parameter.</span><span class="sxs-lookup"><span data-stu-id="61e48-206">You can't specify the **FullyQualifiedModule** parameter in the same command as a **Module** parameter.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="61e48-207">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="61e48-207">-LiteralPath</span></span>

<span data-ttu-id="61e48-208">Hiermee geeft u de map op voor bijgewerkte Help-bestanden in plaats van ze van Internet te downloaden.</span><span class="sxs-lookup"><span data-stu-id="61e48-208">Specifies the folder for updated help files instead of downloading them from the internet.</span></span> <span data-ttu-id="61e48-209">Gebruik deze para meter of **bronpad** als u de cmdlet hebt gebruikt `Save-Help` om Help-bestanden te downloaden naar een map.</span><span class="sxs-lookup"><span data-stu-id="61e48-209">Use this parameter or **SourcePath** if you've used the `Save-Help` cmdlet to download help files to a directory.</span></span>

<span data-ttu-id="61e48-210">U kunt een Directory-object, zoals uit de `Get-Item` `Get-ChildItem` -of-cmdlets, uitlijnen naar `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="61e48-210">You can pipeline a directory object, such as from the `Get-Item` or `Get-ChildItem` cmdlets, to `Update-Help`.</span></span>

<span data-ttu-id="61e48-211">In tegens telling tot de waarde van **SourcePath** , wordt de waarde van **LiteralPath** precies zo gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="61e48-211">Unlike the value of **SourcePath** , the value of **LiteralPath** is used exactly as it's typed.</span></span> <span data-ttu-id="61e48-212">Er worden geen tekens geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="61e48-212">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="61e48-213">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="61e48-213">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="61e48-214">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="61e48-214">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="61e48-215">-Module</span><span class="sxs-lookup"><span data-stu-id="61e48-215">-Module</span></span>

<span data-ttu-id="61e48-216">Help bij updates voor de opgegeven modules.</span><span class="sxs-lookup"><span data-stu-id="61e48-216">Updates help for the specified modules.</span></span> <span data-ttu-id="61e48-217">Voer een of meer module namen of naam patronen in een lijst met door komma's gescheiden waarden in, of geef een bestand op waarin één module naam op elke regel wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="61e48-217">Enter one or more module names or name patterns in a comma-separated list, or specify a file that lists one module name on each line.</span></span> <span data-ttu-id="61e48-218">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="61e48-218">Wildcard characters are permitted.</span></span> <span data-ttu-id="61e48-219">U kunt modules van de `Get-Module` cmdlet naar de cmdlet pijp lijnen `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="61e48-219">You can pipeline modules from the `Get-Module` cmdlet to the `Update-Help` cmdlet.</span></span>

<span data-ttu-id="61e48-220">De modules die u opgeeft, moeten op de computer zijn geïnstalleerd, maar ze hoeven niet in de huidige sessie te worden geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="61e48-220">The modules that you specify must be installed on the computer, but they don't have to be imported into the current session.</span></span> <span data-ttu-id="61e48-221">U kunt een wille keurige module opgeven in de sessie of een module die is geïnstalleerd op een locatie die wordt vermeld in de `$env:PSModulePath` omgevings variabele.</span><span class="sxs-lookup"><span data-stu-id="61e48-221">You can specify any module in the session or any module that is installed in a location listed in the `$env:PSModulePath` environment variable.</span></span>

<span data-ttu-id="61e48-222">De waarde van `*` (alle) probeert de Help bij te werken voor alle modules die op de computer zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="61e48-222">A value of `*` (all) attempts to update help for all modules that are installed on the computer.</span></span>
<span data-ttu-id="61e48-223">Modules die geen ondersteuning bieden voor bijwerk bare Help zijn opgenomen.</span><span class="sxs-lookup"><span data-stu-id="61e48-223">Modules that don't support Updatable Help are included.</span></span> <span data-ttu-id="61e48-224">Deze waarde kan fouten genereren wanneer de opdracht modules detecteert die geen ondersteuning bieden voor de Help die kan worden bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="61e48-224">This value might generate errors when the command encounters modules that don't support Updatable Help.</span></span> <span data-ttu-id="61e48-225">Voer in plaats daarvan `Update-Help` zonder para meters uit.</span><span class="sxs-lookup"><span data-stu-id="61e48-225">Instead, run `Update-Help` without parameters.</span></span>

<span data-ttu-id="61e48-226">De **module** parameter van de `Update-Help` cmdlet accepteert niet het volledige pad naar het manifest bestand van een module bestand of module.</span><span class="sxs-lookup"><span data-stu-id="61e48-226">The **Module** parameter of the `Update-Help` cmdlet doesn't accept the full path of a module file or module manifest file.</span></span> <span data-ttu-id="61e48-227">Als u de Help wilt bijwerken voor een module die zich niet in een locatie bevindt `$env:PSModulePath` , importeert u de module in de huidige sessie voordat u de `Update-Help` opdracht uitvoert.</span><span class="sxs-lookup"><span data-stu-id="61e48-227">To update help for a module that isn't in a `$env:PSModulePath` location, import the module into the current session before you run the `Update-Help` command.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Name

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="61e48-228">-Recursief</span><span class="sxs-lookup"><span data-stu-id="61e48-228">-Recurse</span></span>

<span data-ttu-id="61e48-229">Voert een recursieve zoek opdracht uit voor Help-bestanden in de opgegeven map.</span><span class="sxs-lookup"><span data-stu-id="61e48-229">Performs a recursive search for help files in the specified directory.</span></span> <span data-ttu-id="61e48-230">Deze para meter is alleen geldig als de opdracht de para meter **SourcePath** gebruikt.</span><span class="sxs-lookup"><span data-stu-id="61e48-230">This parameter is valid only when the command uses the **SourcePath** parameter.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="61e48-231">-Bronpad</span><span class="sxs-lookup"><span data-stu-id="61e48-231">-SourcePath</span></span>

<span data-ttu-id="61e48-232">Hiermee geeft u een bestandsmap op waarin `Update-Help` bijgewerkte Help-bestanden worden opgehaald, in plaats van ze van Internet te downloaden.</span><span class="sxs-lookup"><span data-stu-id="61e48-232">Specifies a file system folder where `Update-Help` gets updated help files, instead of downloading them from the internet.</span></span> <span data-ttu-id="61e48-233">Geef het pad van een map op.</span><span class="sxs-lookup"><span data-stu-id="61e48-233">Enter the path of a folder.</span></span> <span data-ttu-id="61e48-234">Geef geen bestands naam of bestandsnaam extensie op.</span><span class="sxs-lookup"><span data-stu-id="61e48-234">Don't specify a file name or file name extension.</span></span> <span data-ttu-id="61e48-235">U kunt een map, zoals een, uit de `Get-Item` `Get-ChildItem` cmdlets, naar koppelen `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="61e48-235">You can pipeline a folder, such as one from the `Get-Item` or `Get-ChildItem` cmdlets, to `Update-Help`.</span></span>

<span data-ttu-id="61e48-236">`Update-Help`Downloadt standaard bijgewerkte Help-bestanden van het internet.</span><span class="sxs-lookup"><span data-stu-id="61e48-236">By default, `Update-Help` downloads updated help files from the internet.</span></span> <span data-ttu-id="61e48-237">Gebruik **SourcePath** wanneer u de cmdlet hebt gebruikt `Save-Help` om bijgewerkte Help-bestanden te downloaden naar een map.</span><span class="sxs-lookup"><span data-stu-id="61e48-237">Use **SourcePath** when you've used the `Save-Help` cmdlet to download updated help files to a directory.</span></span>

<span data-ttu-id="61e48-238">Als u een standaard waarde voor **SourcePath** wilt opgeven, gaat u naar **Groepsbeleid** , **computer configuratie** en **stelt u het standaard bronpad voor update-Help** in.</span><span class="sxs-lookup"><span data-stu-id="61e48-238">To specify a default value for **SourcePath** , go to **Group Policy** , **Computer Configuration** , and **Set the default source path for Update-Help**.</span></span> <span data-ttu-id="61e48-239">Met deze groepsbeleid instelling wordt voor komen dat gebruikers `Update-Help` Help-bestanden downloaden van het internet.</span><span class="sxs-lookup"><span data-stu-id="61e48-239">This Group Policy setting prevents users from using `Update-Help` to download help files from the internet.</span></span>
<span data-ttu-id="61e48-240">Zie [about_Group_Policy_Settings](./About/about_Group_Policy_Settings.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="61e48-240">For more information, see [about_Group_Policy_Settings](./About/about_Group_Policy_Settings.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="61e48-241">-UICulture</span><span class="sxs-lookup"><span data-stu-id="61e48-241">-UICulture</span></span>

<span data-ttu-id="61e48-242">Hiermee geeft u de UI-cultuur waarden `Update-Help` op die worden gebruikt voor het ophalen van bijgewerkte Help-bestanden.</span><span class="sxs-lookup"><span data-stu-id="61e48-242">Specifies UI culture values that `Update-Help` uses to get updated help files.</span></span> <span data-ttu-id="61e48-243">Voer een of meer taal codes in, zoals **es-es** , een variabele die cultuur objecten bevat of een opdracht die cultuur objecten, zoals een of-opdracht, ophalen `Get-Culture` `Get-UICulture` .</span><span class="sxs-lookup"><span data-stu-id="61e48-243">Enter one or more language codes, such as **es-ES** , a variable that contains culture objects, or a command that gets culture objects, such as a `Get-Culture` or `Get-UICulture` command.</span></span> <span data-ttu-id="61e48-244">Joker tekens zijn niet toegestaan en u kunt geen gedeeltelijke taal code verzenden, zoals **de**.</span><span class="sxs-lookup"><span data-stu-id="61e48-244">Wildcard characters aren't permitted and you can't submit a partial language code, such as **de**.</span></span>

<span data-ttu-id="61e48-245">Hiermee worden standaard `Update-Help` Help-bestanden in de UI-cultuur ingesteld voor het besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="61e48-245">By default, `Update-Help` gets help files in the UI culture set for the operating system.</span></span> <span data-ttu-id="61e48-246">Als u de para meter **uiCulture** opgeeft, `Update-Help` zoekt alleen naar de opgegeven gebruikersinterface cultuur.</span><span class="sxs-lookup"><span data-stu-id="61e48-246">If you specify the **UICulture** parameter, `Update-Help` looks for help only for the specified UI culture.</span></span>

<span data-ttu-id="61e48-247">Opdrachten die gebruikmaken van de para meter **uiCulture** , worden alleen uitgevoerd wanneer de module Help-bestanden voor de opgegeven UI-cultuur bevat.</span><span class="sxs-lookup"><span data-stu-id="61e48-247">Commands that use the **UICulture** parameter succeed only when the module provides help files for the specified UI culture.</span></span> <span data-ttu-id="61e48-248">Als de opdracht mislukt omdat de opgegeven GEBRUIKERSINTERFACE cultuur niet wordt ondersteund, wordt een fout bericht weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="61e48-248">If the command fails because the specified UI culture isn't supported, an error message is displayed.</span></span>

```yaml
Type: System.Globalization.CultureInfo[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="61e48-249">-UseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="61e48-249">-UseDefaultCredentials</span></span>

<span data-ttu-id="61e48-250">Hiermee wordt aangegeven dat `Update-Help` de opdracht wordt uitgevoerd, met inbegrip van het downloaden van Internet, met behulp van de referenties van de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="61e48-250">Indicates that `Update-Help` runs the command, including the internet download, by using the credentials of the current user.</span></span> <span data-ttu-id="61e48-251">Standaard wordt de opdracht uitgevoerd zonder expliciete referenties.</span><span class="sxs-lookup"><span data-stu-id="61e48-251">By default, the command runs without explicit credentials.</span></span>

<span data-ttu-id="61e48-252">Deze para meter is alleen effectief wanneer het webdownloaden NT LAN Manager (NTLM), onderhandelen of Kerberos-verificatie gebruikt.</span><span class="sxs-lookup"><span data-stu-id="61e48-252">This parameter is effective only when the web download uses NT LAN Manager (NTLM), negotiate, or Kerberos-based authentication.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="61e48-253">-Confirm</span><span class="sxs-lookup"><span data-stu-id="61e48-253">-Confirm</span></span>

<span data-ttu-id="61e48-254">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="61e48-254">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="61e48-255">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="61e48-255">-WhatIf</span></span>

<span data-ttu-id="61e48-256">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="61e48-256">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="61e48-257">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="61e48-257">The cmdlet isn't run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="61e48-258">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="61e48-258">CommonParameters</span></span>

<span data-ttu-id="61e48-259">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="61e48-259">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="61e48-260">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="61e48-260">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="61e48-261">INVOER</span><span class="sxs-lookup"><span data-stu-id="61e48-261">INPUTS</span></span>

### <span data-ttu-id="61e48-262">System. IO. DirectoryInfo</span><span class="sxs-lookup"><span data-stu-id="61e48-262">System.IO.DirectoryInfo</span></span>

<span data-ttu-id="61e48-263">U kunt een mappad door sluizen naar `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="61e48-263">You can pipe a directory path to `Update-Help`.</span></span>

### <span data-ttu-id="61e48-264">System. Management. Automation. PSModuleInfo</span><span class="sxs-lookup"><span data-stu-id="61e48-264">System.Management.Automation.PSModuleInfo</span></span>

<span data-ttu-id="61e48-265">U kunt een module-object vanuit de `Get-Module` cmdlet door sluizen naar `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="61e48-265">You can pipe a module object from the `Get-Module` cmdlet to `Update-Help`.</span></span>

## <span data-ttu-id="61e48-266">UITVOER</span><span class="sxs-lookup"><span data-stu-id="61e48-266">OUTPUTS</span></span>

### <span data-ttu-id="61e48-267">Geen</span><span class="sxs-lookup"><span data-stu-id="61e48-267">None</span></span>

<span data-ttu-id="61e48-268">`Update-Help` Er wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="61e48-268">`Update-Help` doesn't generate any output.</span></span>

## <span data-ttu-id="61e48-269">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="61e48-269">NOTES</span></span>

<span data-ttu-id="61e48-270">Als u de Help voor de Power shell core-modules wilt bijwerken die de opdrachten bevatten die zijn geïnstalleerd met Power shell of een module in de `$PSHOME\Modules` Directory, start u Power shell met de optie om **als Administrator uit te voeren**.</span><span class="sxs-lookup"><span data-stu-id="61e48-270">To update help for the PowerShell Core modules, that contain the commands that are installed with PowerShell, or any module in the `$PSHOME\Modules` directory, start PowerShell with the option to **Run as administrator**.</span></span>

<span data-ttu-id="61e48-271">Alleen leden van de groep Administrators op de computer kunnen de Help-informatie voor de Power shell core-modules, de opdrachten die worden geïnstalleerd samen met Power shell en modules in de `$PSHOME\Modules` map bijwerken.</span><span class="sxs-lookup"><span data-stu-id="61e48-271">Only members of the Administrators group on the computer can update help for the PowerShell Core modules, the commands that are installed together with PowerShell, and for modules in the `$PSHOME\Modules` folder.</span></span> <span data-ttu-id="61e48-272">Als u geen machtiging hebt om Help-bestanden bij te werken, kunt u de Help-bestanden online lezen.</span><span class="sxs-lookup"><span data-stu-id="61e48-272">If you don't have permission to update help files, you can read the help files online.</span></span> <span data-ttu-id="61e48-273">Bijvoorbeeld `Get-Help Update-Help -Online`.</span><span class="sxs-lookup"><span data-stu-id="61e48-273">For example, `Get-Help Update-Help -Online`.</span></span>

<span data-ttu-id="61e48-274">Modules zijn de kleinste eenheid van Help die kan worden bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="61e48-274">Modules are the smallest unit of updatable help.</span></span> <span data-ttu-id="61e48-275">U kunt de Help voor een bepaalde cmdlet niet bijwerken.</span><span class="sxs-lookup"><span data-stu-id="61e48-275">You can't update help for a particular cmdlet.</span></span> <span data-ttu-id="61e48-276">Als u de module wilt vinden die een bepaalde cmdlet bevat, gebruikt u **de eigenschap PropertyName** van de `Get-Command` cmdlet, bijvoorbeeld `(Get-Command Update-Help).ModuleName` .</span><span class="sxs-lookup"><span data-stu-id="61e48-276">To find the module that contains a particular cmdlet, use the **ModuleName** property of the `Get-Command` cmdlet, for example, `(Get-Command Update-Help).ModuleName`.</span></span>

<span data-ttu-id="61e48-277">Omdat Help-bestanden in de module directory zijn geïnstalleerd, `Update-Help` kan de cmdlet alleen een bijgewerkt Help-bestand installeren voor modules die op de computer zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="61e48-277">Because help files are installed in the module directory, the `Update-Help` cmdlet can install updated help file only for modules that are installed on the computer.</span></span> <span data-ttu-id="61e48-278">De `Save-Help` cmdlet kan echter de Help opslaan voor modules die niet op de computer zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="61e48-278">However, the `Save-Help` cmdlet can save help for modules that aren't installed on the computer.</span></span>

<span data-ttu-id="61e48-279">Als er `Update-Help` geen bijgewerkte Help-bestanden kunnen worden gevonden voor een module, of als er geen bijgewerkte Help kan worden gevonden in de opgegeven taal, wordt de installatie zonder fouten voortgezet.</span><span class="sxs-lookup"><span data-stu-id="61e48-279">If `Update-Help` can't find updated help files for a module, or can't find updated help in the specified language, it continues silently without displaying an error message.</span></span> <span data-ttu-id="61e48-280">Als u de status en Details van de voortgang wilt bekijken, gebruikt u de para meter **uitgebreid** .</span><span class="sxs-lookup"><span data-stu-id="61e48-280">To see status and progress details, use the **Verbose** parameter.</span></span>

<span data-ttu-id="61e48-281">De `Update-Help` cmdlet is geïntroduceerd in Windows Power shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="61e48-281">The `Update-Help` cmdlet was introduced in Windows PowerShell 3.0.</span></span> <span data-ttu-id="61e48-282">Deze functie werkt niet in eerdere versies van Power shell.</span><span class="sxs-lookup"><span data-stu-id="61e48-282">It doesn't work in earlier versions of PowerShell.</span></span> <span data-ttu-id="61e48-283">Op computers met Windows Power Shell 2,0 en Windows Power Shell 3,0 gebruikt u de `Update-Help` cmdlet in een Windows Power shell 3,0-sessie om Help-bestanden te downloaden en bij te werken.</span><span class="sxs-lookup"><span data-stu-id="61e48-283">On computers that have both Windows PowerShell 2.0 and Windows PowerShell 3.0, use the `Update-Help` cmdlet in a Windows PowerShell 3.0 session to download and update help files.</span></span> <span data-ttu-id="61e48-284">De Help-bestanden zijn beschikbaar voor zowel Windows Power Shell 2,0 als Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="61e48-284">The help files are available to both Windows PowerShell 2.0 and Windows PowerShell 3.0.</span></span>

<span data-ttu-id="61e48-285">De `Update-Help` `Save-Help` cmdlets en gebruiken de volgende poorten om Help-bestanden te downloaden: poort 80 voor http en poort 443 voor HTTPS.</span><span class="sxs-lookup"><span data-stu-id="61e48-285">The `Update-Help` and `Save-Help` cmdlets use the following ports to download help files: Port 80 for HTTP and port 443 for HTTPS.</span></span>

<span data-ttu-id="61e48-286">`Update-Help` ondersteunt alle modules en de Power shell core-modules. Andere modules worden niet ondersteund.</span><span class="sxs-lookup"><span data-stu-id="61e48-286">`Update-Help` supports all modules and the PowerShell Core snap-ins. It doesn't support any other snap-ins.</span></span>

<span data-ttu-id="61e48-287">Als u de Help wilt bijwerken voor een module op een locatie die niet wordt weer gegeven in de `$env:PSModulePath` omgevings variabele, importeert u de module in de huidige sessie en voert u vervolgens een `Update-Help` opdracht uit.</span><span class="sxs-lookup"><span data-stu-id="61e48-287">To update help for a module in a location that isn't listed in the `$env:PSModulePath` environment variable, import the module into the current session and then run an `Update-Help` command.</span></span> <span data-ttu-id="61e48-288">`Update-Help`Zonder para meters uitvoeren of de **module** parameter gebruiken om de module naam op te geven.</span><span class="sxs-lookup"><span data-stu-id="61e48-288">Run `Update-Help` without parameters or use the **Module** parameter to specify the module name.</span></span> <span data-ttu-id="61e48-289">Met de **module** parameter van `Update-Help` de `Save-Help` cmdlets en wordt het volledige pad van een module bestand of module manifest bestand niet geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="61e48-289">The **Module** parameter of the `Update-Help` and `Save-Help` cmdlets doesn't accept the full path of a module file or module manifest file.</span></span>

<span data-ttu-id="61e48-290">Elke module kan de Help die kan worden bijgewerkt ondersteunen.</span><span class="sxs-lookup"><span data-stu-id="61e48-290">Any module can support Updatable Help.</span></span> <span data-ttu-id="61e48-291">Zie [ondersteunende Help-informatie](/powershell/scripting/developer/module/supporting-updatable-help)voor instructies voor het ondersteunen van Help-informatie in de modules die u ontwerpt.</span><span class="sxs-lookup"><span data-stu-id="61e48-291">For instructions for supporting Updatable Help in the modules that you author, see [Supporting Updatable Help](/powershell/scripting/developer/module/supporting-updatable-help).</span></span>

<span data-ttu-id="61e48-292">De `Update-Help` `Save-Help` cmdlets en worden niet ondersteund op Windows Preinstallation Environment (Windows PE).</span><span class="sxs-lookup"><span data-stu-id="61e48-292">The `Update-Help` and `Save-Help` cmdlets are not supported on Windows Preinstallation Environment (Windows PE).</span></span>

## <span data-ttu-id="61e48-293">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="61e48-293">RELATED LINKS</span></span>

[<span data-ttu-id="61e48-294">Get-cultuur</span><span class="sxs-lookup"><span data-stu-id="61e48-294">Get-Culture</span></span>](../Microsoft.PowerShell.Utility/Get-Culture.md)

[<span data-ttu-id="61e48-295">Get-Help</span><span class="sxs-lookup"><span data-stu-id="61e48-295">Get-Help</span></span>](Get-Help.md)

[<span data-ttu-id="61e48-296">Get-module</span><span class="sxs-lookup"><span data-stu-id="61e48-296">Get-Module</span></span>](Get-Module.md)

[<span data-ttu-id="61e48-297">Get-UICulture</span><span class="sxs-lookup"><span data-stu-id="61e48-297">Get-UICulture</span></span>](../Microsoft.PowerShell.Utility/Get-UICulture.md)

[<span data-ttu-id="61e48-298">Begin taak</span><span class="sxs-lookup"><span data-stu-id="61e48-298">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="61e48-299">Opslaan-Help</span><span class="sxs-lookup"><span data-stu-id="61e48-299">Save-Help</span></span>](Save-Help.md)
