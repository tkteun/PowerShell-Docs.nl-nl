---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 05/16/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/update-help?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-Help
ms.openlocfilehash: f4aec907a41378bbf49f744b66c5662aa3404beb
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705494"
---
# <span data-ttu-id="9fa3a-102">Update-Help</span><span class="sxs-lookup"><span data-stu-id="9fa3a-102">Update-Help</span></span>

## <span data-ttu-id="9fa3a-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="9fa3a-103">SYNOPSIS</span></span>
<span data-ttu-id="9fa3a-104">Downloadt en installeert de nieuwste Help-bestanden op uw computer.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-104">Downloads and installs the newest help files on your computer.</span></span>

## <span data-ttu-id="9fa3a-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="9fa3a-105">SYNTAX</span></span>

### <span data-ttu-id="9fa3a-106">Pad (standaard)</span><span class="sxs-lookup"><span data-stu-id="9fa3a-106">Path (Default)</span></span>

```
Update-Help [[-Module] <String[]>] [-FullyQualifiedModule <ModuleSpecification[]>]
 [[-SourcePath] <String[]>] [-Recurse] [[-UICulture] <CultureInfo[]>] [-Credential <PSCredential>]
 [-UseDefaultCredentials] [-Force] [-Scope <UpdateHelpScope>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="9fa3a-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="9fa3a-107">LiteralPath</span></span>

```
Update-Help [[-Module] <String[]>] [-FullyQualifiedModule <ModuleSpecification[]>]
 [-LiteralPath <String[]>] [-Recurse] [[-UICulture] <CultureInfo[]>] [-Credential <PSCredential>]
 [-UseDefaultCredentials] [-Force] [-Scope <UpdateHelpScope>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="9fa3a-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="9fa3a-108">DESCRIPTION</span></span>

<span data-ttu-id="9fa3a-109">De `Update-Help` cmdlet downloadt de nieuwste Help-bestanden voor Power shell-modules en installeert deze op uw computer.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-109">The `Update-Help` cmdlet downloads the newest help files for PowerShell modules and installs them on your computer.</span></span> <span data-ttu-id="9fa3a-110">U hoeft Power shell niet opnieuw op te starten om de wijziging van kracht te laten worden.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-110">You need not restart PowerShell to make the change effective.</span></span> <span data-ttu-id="9fa3a-111">U kunt de `Get-Help` cmdlet gebruiken om de nieuwe Help-bestanden onmiddellijk weer te geven.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-111">You can use the `Get-Help` cmdlet to view the new help files immediately.</span></span>

<span data-ttu-id="9fa3a-112">`Update-Help` Hiermee wordt de versie van de Help-bestanden op uw computer gecontroleerd.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-112">`Update-Help` checks the version of the help files on your computer.</span></span> <span data-ttu-id="9fa3a-113">Als u geen Help-bestanden voor een module hebt of als uw Help-bestanden zijn verouderd, `Update-Help` downloadt de nieuwste Help-bestanden.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-113">If you don't have help files for a module or if your help files are outdated, `Update-Help` downloads the newest help files.</span></span> <span data-ttu-id="9fa3a-114">De Help-bestanden kunnen worden gedownload en geïnstalleerd via internet of een bestands share.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-114">The help files can be downloaded and installed from the internet or a file share.</span></span>

<span data-ttu-id="9fa3a-115">Zonder para meters worden `Update-Help` de Help-bestanden voor modules in de sessie en voor alle geïnstalleerde modules bijgewerkt die ondersteuning bieden voor bijwerk bare Help.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-115">Without parameters, `Update-Help` updates the help files for modules in the session and for all installed modules that support Updatable Help.</span></span> <span data-ttu-id="9fa3a-116">Modules die zijn geïnstalleerd maar niet zijn geladen in de huidige sessie, worden opgenomen.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-116">Modules that are installed but not loaded in the current session are included.</span></span> <span data-ttu-id="9fa3a-117">Power shell-modules worden opgeslagen op een locatie die wordt vermeld in de `$env:PSModulePath` omgevings variabele.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-117">PowerShell modules are stored in a location listed in the `$env:PSModulePath` environment variable.</span></span> <span data-ttu-id="9fa3a-118">Zie [about_Updatable_Help](./About/about_Updatable_Help.md) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-118">For more information, see [about_Updatable_Help](./About/about_Updatable_Help.md).</span></span>

<span data-ttu-id="9fa3a-119">U kunt de **module** parameter gebruiken om Help-bestanden voor een bepaalde module bij te werken.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-119">You can use the **Module** parameter to update help files for a particular module.</span></span> <span data-ttu-id="9fa3a-120">Gebruik de para meter **uiCulture** om Help-bestanden te downloaden in meerdere talen en land instellingen.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-120">Use the **UICulture** parameter to download help files in multiple languages and locales.</span></span>

<span data-ttu-id="9fa3a-121">U kunt ook gebruiken `Update-Help` op computers die niet zijn verbonden met internet.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-121">You can also use `Update-Help` on computers that are not connected to the internet.</span></span> <span data-ttu-id="9fa3a-122">Gebruik eerst de `Save-Help` cmdlet om Help-bestanden te downloaden van Internet en deze op te slaan in een gedeelde map die toegankelijk is voor het systeem dat niet is verbonden met internet.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-122">First, use the `Save-Help`cmdlet to download help files from the internet and save them in a shared folder that is accessible to the system not connected to the internet.</span></span> <span data-ttu-id="9fa3a-123">Vervolgens gebruikt u de para meter **SourcePath** van `Update-Help` om de bijgewerkte Help-bestanden te downloaden van de gedeelde en te installeren op de computer.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-123">Then use the **SourcePath** parameter of `Update-Help` to download the updated help files from the shared and install them on the computer.</span></span>

<span data-ttu-id="9fa3a-124">U kunt de Help-updates automatiseren door de cmdlet toe te voegen `Update-Help` aan uw Power shell-profiel.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-124">You can automate help updates by adding the `Update-Help` cmdlet to your PowerShell profile.</span></span> <span data-ttu-id="9fa3a-125">Standaard `Update-Help` wordt slechts één keer per dag op elke computer uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-125">By default, `Update-Help` runs only one time per day on each computer.</span></span> <span data-ttu-id="9fa3a-126">Als u de limiet van één dag wilt overschrijven, gebruikt u de para meter **Force** .</span><span class="sxs-lookup"><span data-stu-id="9fa3a-126">To override the once-per-day limit, use the **Force** parameter.</span></span>

<span data-ttu-id="9fa3a-127">De `Update-Help` cmdlet is geïntroduceerd in Windows Power shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-127">The `Update-Help` cmdlet was introduced in Windows PowerShell 3.0.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9fa3a-128">`Update-Help` hiervoor zijn beheerders bevoegdheden in Power shell 6,0 en lager vereist.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-128">`Update-Help` requires administrative privileges in PowerShell 6.0 and below.</span></span>
> <span data-ttu-id="9fa3a-129">In Power shell 6,1 en hoger wordt het standaard **bereik** ingesteld op `CurrentUser` .</span><span class="sxs-lookup"><span data-stu-id="9fa3a-129">PowerShell 6.1 and above set the default **Scope** to `CurrentUser`.</span></span>
> <span data-ttu-id="9fa3a-130">Vóór Power shell 6,1 is de **bereik** parameter niet beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-130">Prior to PowerShell 6.1, the **Scope** parameter was not available.</span></span>
>
> <span data-ttu-id="9fa3a-131">U moet lid zijn van de groep Administrators op de computer om de Help-bestanden voor de Power shell core-modules bij te werken.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-131">You must be a member of the Administrators group on the computer to update the help files for the PowerShell Core modules.</span></span>
>
> <span data-ttu-id="9fa3a-132">Als u de Help-bestanden voor modules in de Power shell-installatie directory ( `$PSHOME\Modules` ), inclusief de Power shell-kern modules, wilt downloaden of bijwerken, start u Power shell met de optie **als administrator uitvoeren** .</span><span class="sxs-lookup"><span data-stu-id="9fa3a-132">To download or update the help files for modules in the PowerShell installation directory (`$PSHOME\Modules`), including the PowerShell Core modules, start PowerShell by using the **Run as administrator** option.</span></span>
> <span data-ttu-id="9fa3a-133">Bijvoorbeeld: `Start-Process pwsh.exe -Verb RunAs`.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-133">For example: `Start-Process pwsh.exe -Verb RunAs`.</span></span>

## <span data-ttu-id="9fa3a-134">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="9fa3a-134">EXAMPLES</span></span>

### <span data-ttu-id="9fa3a-135">Voor beeld 1: Help-bestanden voor alle modules bijwerken</span><span class="sxs-lookup"><span data-stu-id="9fa3a-135">Example 1: Update help files for all modules</span></span>

<span data-ttu-id="9fa3a-136">De `Update-Help` cmdlet werkt Help-bestanden bij voor geïnstalleerde modules die kunnen worden bijgewerkt met ondersteuning.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-136">The `Update-Help` cmdlet updates help files for installed modules that support Updatable Help.</span></span> <span data-ttu-id="9fa3a-137">De cultuur taal van de gebruikers interface (UI) is ingesteld in het besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-137">The user-interface (UI) culture language is set in the operating system.</span></span>

```powershell
Update-Help
```

### <span data-ttu-id="9fa3a-138">Voor beeld 2: Help-bestanden voor opgegeven modules bijwerken</span><span class="sxs-lookup"><span data-stu-id="9fa3a-138">Example 2: Update help files for specified modules</span></span>

<span data-ttu-id="9fa3a-139">De `Update-Help` cmdlet updatet alleen Help-bestanden voor module namen die beginnen met **micro soft. Power shell**.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-139">The `Update-Help` cmdlet updates help files only for module names that begin with **Microsoft.PowerShell**.</span></span>

```powershell
Update-Help -Module Microsoft.PowerShell*
```

### <span data-ttu-id="9fa3a-140">Voor beeld 3: Help-bestanden voor verschillende talen bijwerken</span><span class="sxs-lookup"><span data-stu-id="9fa3a-140">Example 3: Update help files for different languages</span></span>

<span data-ttu-id="9fa3a-141">`Update-Help`Met de cmdlet worden de Japanse (ja-JP) en de Engelse (en-US) Help-bestanden voor alle modules bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-141">The `Update-Help` cmdlet updates the Japanese (ja-JP) and English (en-US) help files for all modules.</span></span>

<span data-ttu-id="9fa3a-142">Als een module geen Help-bestanden voor een opgegeven UI-cultuur biedt, wordt een fout bericht weer gegeven voor de module en de UI-cultuur.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-142">If a module doesn't provide help files for a specified UI culture, an error message is displayed for the module and UI culture.</span></span> <span data-ttu-id="9fa3a-143">In dit voor beeld geeft het fout bericht aan dat de Help-bestanden van **ja-jp** niet zijn gevonden voor de module **micro soft. Power shell. Utility**.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-143">In this example, the error message indicates that the **ja-JP** help files were not found for module **Microsoft.PowerShell.Utility**.</span></span>

```powershell
Update-Help -UICulture ja-JP, en-US
```

```Output
Update-Help : Failed to update Help for the module(s) 'Microsoft.PowerShell.Utility' with UI culture(s) {ja-JP}
No UI culture was found that matches the following pattern: ja-JP.
```

### <span data-ttu-id="9fa3a-144">Voor beeld 4: Help-bestanden op meerdere computers bijwerken vanuit een bestands share</span><span class="sxs-lookup"><span data-stu-id="9fa3a-144">Example 4: Update help files on multiple computers from a file share</span></span>

<span data-ttu-id="9fa3a-145">In dit voor beeld worden bijgewerkte Help-bestanden gedownload van Internet en opgeslagen in een bestands share.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-145">In this example, updated help files are downloaded from the internet and saved in a file share.</span></span> <span data-ttu-id="9fa3a-146">Er zijn gebruikers referenties nodig die machtigingen hebben voor toegang tot de bestands share en om updates te installeren.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-146">User credentials are needed that have permissions to access the file share and install updates.</span></span> <span data-ttu-id="9fa3a-147">Wanneer een bestands share wordt gebruikt, is het mogelijk om computers bij te werken die zich achter een firewall bevinden of die niet zijn verbonden met internet.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-147">When a file share is used, it's possible to update computers that are behind firewalls or aren't connected to the internet.</span></span>

```powershell
Save-Help -DestinationPath \\Server01\Share\PSHelp -Credential Domain01\Admin01
Invoke-Command -ComputerName (Get-Content Servers.txt) -ScriptBlock {
     Update-Help -SourcePath \\Server01\Share\PSHelp -Credential Domain01\Admin01
}
```

<span data-ttu-id="9fa3a-148">`Save-Help`Met de opdracht worden de nieuwste Help-bestanden gedownload voor alle modules die kunnen worden bijgewerkt met ondersteuning.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-148">The `Save-Help` command downloads the newest help files for all modules that support Updatable Help.</span></span>
<span data-ttu-id="9fa3a-149">Met de para meter **doelpad** worden de bestanden opgeslagen in de `\\Server01\Share\PSHelp` Bestands share.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-149">The **DestinationPath** parameter saves the files in the `\\Server01\Share\PSHelp` file share.</span></span> <span data-ttu-id="9fa3a-150">De **referentie** parameter geeft u een gebruiker op die toegang heeft tot de bestands share.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-150">The **Credential** parameter specifies a user who has permission to access the file share.</span></span>

<span data-ttu-id="9fa3a-151">`Invoke-Command`Met de cmdlet worden externe `Update-Help` opdrachten op meerdere computers uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-151">The `Invoke-Command` cmdlet runs remote `Update-Help` commands on multiple computers.</span></span> <span data-ttu-id="9fa3a-152">De para meter **ComputerName** haalt een lijst op met externe computers uit het **Servers.txt** -bestand.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-152">The **ComputerName** parameter gets a list of remote computers from the **Servers.txt** file.</span></span> <span data-ttu-id="9fa3a-153">De para meter **script Block** voert de `Update-Help` opdracht uit en gebruikt de para meter **SourcePath** om de bestands share op te geven die de bijgewerkte Help-bestanden bevat.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-153">The **ScriptBlock** parameter runs the `Update-Help` command and uses the **SourcePath** parameter to specify the file share that contains the updated help files.</span></span> <span data-ttu-id="9fa3a-154">De **referentie** parameter geeft u een gebruiker die toegang heeft tot de bestands share en voert u de opdracht extern uit `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="9fa3a-154">The **Credential** parameter specifies a user who can access the file share and run the remote `Update-Help` command.</span></span>

### <span data-ttu-id="9fa3a-155">Voor beeld 5: een lijst met bijgewerkte Help-bestanden ophalen</span><span class="sxs-lookup"><span data-stu-id="9fa3a-155">Example 5: Get a list of updated help files</span></span>

<span data-ttu-id="9fa3a-156">De `Update-Help` cmdlet Update Help voor een opgegeven module.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-156">The `Update-Help` cmdlet updates help for a specified module.</span></span> <span data-ttu-id="9fa3a-157">De cmdlet gebruikt de **uitgebreide** para meter common om de lijst met Help-bestanden weer te geven die zijn bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-157">The cmdlet uses the **Verbose** common parameter to display the list of help files that were updated.</span></span> <span data-ttu-id="9fa3a-158">U kunt **uitgebreid** gebruiken om de uitvoer voor alle Help-bestanden of Help-bestanden voor een specifieke module weer te geven.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-158">You can use **Verbose** to view output for all help files or help files for a specific module.</span></span>

<span data-ttu-id="9fa3a-159">Zonder de para meter **uitgebreid** worden `Update-Help` de resultaten van de opdracht niet weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-159">Without the **Verbose** parameter, `Update-Help` doesn't display the results of the command.</span></span> <span data-ttu-id="9fa3a-160">De **uitgebreide** para meter uitvoer is handig om te controleren of de Help-bestanden zijn bijgewerkt of of de meest recente versie is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-160">The **Verbose** parameter output is useful to verify that the help files were updated or if the latest version is installed.</span></span>

```powershell
Update-Help -Module Microsoft.PowerShell.Utility -Verbose
```

### <span data-ttu-id="9fa3a-161">Voor beeld 6: modules zoeken die kunnen worden bijgewerkt met ondersteuning</span><span class="sxs-lookup"><span data-stu-id="9fa3a-161">Example 6: Find modules that support Updatable Help</span></span>

<span data-ttu-id="9fa3a-162">In dit voor beeld wordt een lijst weer gegeven met de modules die kunnen worden bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-162">This example lists modules that support Updatable Help.</span></span> <span data-ttu-id="9fa3a-163">De opdracht maakt gebruik van de eigenschap **HelpInfoUri** van de module om modules te identificeren die ondersteunende Help kunnen ondersteunen.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-163">The command uses the module's **HelpInfoUri** property to identify modules that support Updatable Help.</span></span> <span data-ttu-id="9fa3a-164">De eigenschap **HelpInfoUri** bevat een adres dat wordt omgeleid wanneer de `Update-Help` cmdlet wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-164">The **HelpInfoUri** property contains an address that is redirected when the `Update-Help` cmdlet is run.</span></span>

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

### <span data-ttu-id="9fa3a-165">Voor beeld 7: inventaris bijgewerkte Help-bestanden</span><span class="sxs-lookup"><span data-stu-id="9fa3a-165">Example 7: Inventory updated help files</span></span>

<span data-ttu-id="9fa3a-166">In dit voor beeld maakt het script `Get-UpdateHelpVersion.ps1` een inventarisatie van de Help-bestanden die kunnen worden bijgewerkt voor elke module en de bijbehorende versie nummers.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-166">In this example, the script `Get-UpdateHelpVersion.ps1` creates an inventory of the Updatable Help files for each module and their version numbers.</span></span>

<span data-ttu-id="9fa3a-167">Met het script worden modules geïdentificeerd die ondersteuning bieden voor Help bij het gebruik van de eigenschap **HelpInfoUri** van modules.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-167">The script identifies modules that support Updatable Help by using the **HelpInfoUri** property of modules.</span></span> <span data-ttu-id="9fa3a-168">Voor modules die kunnen worden bijgewerkt met ondersteuning, zoekt het script naar het Help-informatie bestand (\* helpinfo.xml) en parseert het naar het meest recente versie nummer.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-168">For modules that support Updatable Help, the script looks for and parses the help information file (\*helpinfo.xml) to find the latest version number.</span></span>

<span data-ttu-id="9fa3a-169">Het script maakt gebruik van de **PSCustomObject** -klasse en een hash-tabel om een aangepast uitvoer object te maken.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-169">The script uses the **PSCustomObject** class and a hash table to create a custom output object.</span></span>

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

## <span data-ttu-id="9fa3a-170">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9fa3a-170">PARAMETERS</span></span>

### <span data-ttu-id="9fa3a-171">-Credential</span><span class="sxs-lookup"><span data-stu-id="9fa3a-171">-Credential</span></span>

<span data-ttu-id="9fa3a-172">Hiermee geeft u de referenties op van een gebruiker die toegang heeft tot de locatie van het bestands systeem die is opgegeven door **SourcePath**.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-172">Specifies credentials of a user who has permission to access the file system location specified by **SourcePath**.</span></span> <span data-ttu-id="9fa3a-173">Deze para meter is alleen geldig als de para meter **SourcePath** of **LiteralPath** in de opdracht wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-173">This parameter is valid only when the **SourcePath** or **LiteralPath** parameter is used in the command.</span></span>

<span data-ttu-id="9fa3a-174">Met de para meter **Credential** kunt u `Update-Help` opdrachten uitvoeren met de para meter **SourcePath** op externe computers.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-174">The **Credential** parameter enables you to run `Update-Help` commands with the **SourcePath** parameter on remote computers.</span></span> <span data-ttu-id="9fa3a-175">Door expliciete referenties op te geven, kunt u de opdracht uitvoeren op een externe computer en toegang krijgen tot een bestands share op een derde computer zonder dat er een fout wordt geweigerd of als CredSSP-verificatie wordt gebruikt voor het delegeren van referenties.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-175">By providing explicit credentials, you can run the command on a remote computer and access a file share on a third computer without encountering an access denied error or using CredSSP authentication to delegate credentials.</span></span>

<span data-ttu-id="9fa3a-176">Typ een gebruikers naam, zoals **gebruiker01** of **Domain01\User01**, of voer een **PSCredential** -object in dat door de cmdlet wordt gegenereerd `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="9fa3a-176">Type a user name, such as **User01** or **Domain01\User01**, or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="9fa3a-177">Als u een gebruikers naam typt, wordt u gevraagd het wacht woord in te voeren.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-177">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="9fa3a-178">Referenties worden opgeslagen in een [PSCredential](/dotnet/api/system.management.automation.pscredential) -object en het wacht woord wordt opgeslagen als [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="9fa3a-178">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="9fa3a-179">Zie [Hoe veilig is securestring?](/dotnet/api/system.security.securestring#how-secure-is-securestring)voor meer informatie over **securestring** Data Protection.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-179">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="9fa3a-180">-Force</span><span class="sxs-lookup"><span data-stu-id="9fa3a-180">-Force</span></span>

<span data-ttu-id="9fa3a-181">Geeft aan dat deze cmdlet niet de beperking van één dag volgt, de versie controle overs laat en bestanden downloadt die de limiet van 1 GB overschrijden.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-181">Indicates that this cmdlet doesn't follow the once-per-day limitation, skips version checking, and downloads files that exceed the 1 GB limit.</span></span>

<span data-ttu-id="9fa3a-182">Zonder deze para meter `Update-Help` wordt slechts één keer per periode van 24 uur uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-182">Without this parameter, `Update-Help` runs only once in each 24-hour period.</span></span> <span data-ttu-id="9fa3a-183">Down loads zijn beperkt tot 1 GB aan niet-gecomprimeerde inhoud per module en Help-bestanden worden alleen geïnstalleerd wanneer ze nieuwer zijn dan de bestaande bestanden op de computer.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-183">Downloads are limited to 1 GB of uncompressed content per module and help files are only installed when they're newer than the existing files on the computer.</span></span>

<span data-ttu-id="9fa3a-184">De limiet van één dag beveiligt de servers die als host dienen voor de Help-bestanden en maken het praktisch om een opdracht toe te voegen `Update-Help` aan uw Power shell-profiel zonder de resource kosten van herhaalde verbindingen of down loads te maken.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-184">The once-per-day limit protects the servers that host the help files and makes it practical for you to add an `Update-Help` command to your PowerShell profile without incurring the resource cost of repeated connections or downloads.</span></span>

<span data-ttu-id="9fa3a-185">Als u de Help voor een module in meerdere GEBRUIKERSINTERFACE culturen wilt bijwerken zonder de para meter **Force** , neemt u alle gebruikersinterface culturen op in dezelfde opdracht, zoals:</span><span class="sxs-lookup"><span data-stu-id="9fa3a-185">To update help for a module in multiple UI cultures without the **Force** parameter, include all UI cultures in the same command, such as:</span></span>

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

### <span data-ttu-id="9fa3a-186">-FullyQualifiedModule</span><span class="sxs-lookup"><span data-stu-id="9fa3a-186">-FullyQualifiedModule</span></span>

<span data-ttu-id="9fa3a-187">Hiermee geeft u modules op met namen die zijn opgegeven in de vorm van **ModuleSpecification** -objecten.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-187">Specifies modules with names that are specified in the form of **ModuleSpecification** objects.</span></span>
<span data-ttu-id="9fa3a-188">Deze modules worden beschreven in de sectie opmerkingen van de [ModuleSpecification-constructor (hashtabel)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span><span class="sxs-lookup"><span data-stu-id="9fa3a-188">These modules are described in the Remarks section of [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span></span>

<span data-ttu-id="9fa3a-189">De para meter **FullyQualifiedModule** accepteert bijvoorbeeld een module naam die is opgegeven in de indeling:</span><span class="sxs-lookup"><span data-stu-id="9fa3a-189">For example, the **FullyQualifiedModule** parameter accepts a module name that is specified in the format:</span></span>

`@{ModuleName = "modulename"; ModuleVersion = "version_number"}`

<span data-ttu-id="9fa3a-190">of</span><span class="sxs-lookup"><span data-stu-id="9fa3a-190">or</span></span>

`@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}.`

<span data-ttu-id="9fa3a-191">**Module** naam en **ModuleVersion** zijn vereist, maar **GUID** is optioneel.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-191">**ModuleName** and **ModuleVersion** are required, but **Guid** is optional.</span></span>

<span data-ttu-id="9fa3a-192">U kunt de para meter **FullyQualifiedModule** niet opgeven in dezelfde opdracht als een **module** parameter.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-192">You can't specify the **FullyQualifiedModule** parameter in the same command as a **Module** parameter.</span></span>

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

### <span data-ttu-id="9fa3a-193">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="9fa3a-193">-LiteralPath</span></span>

<span data-ttu-id="9fa3a-194">Hiermee geeft u de map op voor bijgewerkte Help-bestanden in plaats van ze van Internet te downloaden.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-194">Specifies the folder for updated help files instead of downloading them from the internet.</span></span> <span data-ttu-id="9fa3a-195">Gebruik deze para meter of **bronpad** als u de cmdlet hebt gebruikt `Save-Help` om Help-bestanden te downloaden naar een map.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-195">Use this parameter or **SourcePath** if you've used the `Save-Help` cmdlet to download help files to a directory.</span></span>

<span data-ttu-id="9fa3a-196">U kunt een Directory-object, zoals uit de `Get-Item` `Get-ChildItem` -of-cmdlets, uitlijnen naar `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="9fa3a-196">You can pipeline a directory object, such as from the `Get-Item` or `Get-ChildItem` cmdlets, to `Update-Help`.</span></span>

<span data-ttu-id="9fa3a-197">In tegens telling tot de waarde van **SourcePath**, wordt de waarde van **LiteralPath** precies zo gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-197">Unlike the value of **SourcePath**, the value of **LiteralPath** is used exactly as it's typed.</span></span> <span data-ttu-id="9fa3a-198">Er worden geen tekens geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-198">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="9fa3a-199">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-199">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="9fa3a-200">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-200">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9fa3a-201">-Module</span><span class="sxs-lookup"><span data-stu-id="9fa3a-201">-Module</span></span>

<span data-ttu-id="9fa3a-202">Help bij updates voor de opgegeven modules.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-202">Updates help for the specified modules.</span></span> <span data-ttu-id="9fa3a-203">Voer een of meer module namen of naam patronen in een lijst met door komma's gescheiden waarden in, of geef een bestand op waarin één module naam op elke regel wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-203">Enter one or more module names or name patterns in a comma-separated list, or specify a file that lists one module name on each line.</span></span> <span data-ttu-id="9fa3a-204">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-204">Wildcard characters are permitted.</span></span> <span data-ttu-id="9fa3a-205">U kunt modules van de `Get-Module` cmdlet naar de cmdlet pijp lijnen `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="9fa3a-205">You can pipeline modules from the `Get-Module` cmdlet to the `Update-Help` cmdlet.</span></span>

<span data-ttu-id="9fa3a-206">De modules die u opgeeft, moeten op de computer zijn geïnstalleerd, maar ze hoeven niet in de huidige sessie te worden geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-206">The modules that you specify must be installed on the computer, but they don't have to be imported into the current session.</span></span> <span data-ttu-id="9fa3a-207">U kunt een wille keurige module opgeven in de sessie of een module die is geïnstalleerd op een locatie die wordt vermeld in de `$env:PSModulePath` omgevings variabele.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-207">You can specify any module in the session or any module that is installed in a location listed in the `$env:PSModulePath` environment variable.</span></span>

<span data-ttu-id="9fa3a-208">De waarde van `*` (alle) probeert de Help bij te werken voor alle modules die op de computer zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-208">A value of `*` (all) attempts to update help for all modules that are installed on the computer.</span></span>
<span data-ttu-id="9fa3a-209">Modules die geen ondersteuning bieden voor bijwerk bare Help zijn opgenomen.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-209">Modules that don't support Updatable Help are included.</span></span> <span data-ttu-id="9fa3a-210">Deze waarde kan fouten genereren wanneer de opdracht modules detecteert die geen ondersteuning bieden voor de Help die kan worden bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-210">This value might generate errors when the command encounters modules that don't support Updatable Help.</span></span> <span data-ttu-id="9fa3a-211">Voer in plaats daarvan `Update-Help` zonder para meters uit.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-211">Instead, run `Update-Help` without parameters.</span></span>

<span data-ttu-id="9fa3a-212">De **module** parameter van de `Update-Help` cmdlet accepteert niet het volledige pad naar het manifest bestand van een module bestand of module.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-212">The **Module** parameter of the `Update-Help` cmdlet doesn't accept the full path of a module file or module manifest file.</span></span> <span data-ttu-id="9fa3a-213">Als u de Help wilt bijwerken voor een module die zich niet in een locatie bevindt `$env:PSModulePath` , importeert u de module in de huidige sessie voordat u de `Update-Help` opdracht uitvoert.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-213">To update help for a module that isn't in a `$env:PSModulePath` location, import the module into the current session before you run the `Update-Help` command.</span></span>

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

### <span data-ttu-id="9fa3a-214">-Recursief</span><span class="sxs-lookup"><span data-stu-id="9fa3a-214">-Recurse</span></span>

<span data-ttu-id="9fa3a-215">Voert een recursieve zoek opdracht uit voor Help-bestanden in de opgegeven map.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-215">Performs a recursive search for help files in the specified directory.</span></span> <span data-ttu-id="9fa3a-216">Deze para meter is alleen geldig als de opdracht de para meter **SourcePath** gebruikt.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-216">This parameter is valid only when the command uses the **SourcePath** parameter.</span></span>

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

### <span data-ttu-id="9fa3a-217">-Bereik</span><span class="sxs-lookup"><span data-stu-id="9fa3a-217">-Scope</span></span>

<span data-ttu-id="9fa3a-218">Hiermee geeft u het systeem bereik op waar Help wordt bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-218">Specifies the system scope where help is updated.</span></span> <span data-ttu-id="9fa3a-219">Voor updates in het **ALLUSERS** -bereik zijn beheerders bevoegdheden op Windows-systemen vereist.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-219">Updates at the **AllUsers** scope require administrative privileges on Windows systems.</span></span> <span data-ttu-id="9fa3a-220">De `-Scope` para meter is geïntroduceerd in Power shell core versie 6,1.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-220">The `-Scope` parameter was introduced in PowerShell Core version 6.1.</span></span>

<span data-ttu-id="9fa3a-221">**CurrentUser** is het standaard bereik voor Help-bestanden in power shell 6,1 en hoger.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-221">**CurrentUser** is the default scope for help files in PowerShell 6.1 and above.</span></span> <span data-ttu-id="9fa3a-222">**ALLUSERS** kan worden opgegeven om Help voor alle gebruikers te installeren of bij te werken.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-222">**AllUsers** can be specified to install or update help for all users.</span></span> <span data-ttu-id="9fa3a-223">Op UNIX-systeem `sudo` privileges zijn vereist om Help bij te werken voor alle gebruikers.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-223">On Unix systems `sudo` privileges are required to update help for all users.</span></span> <span data-ttu-id="9fa3a-224">Bijvoorbeeld: `sudo pwsh -c Update-Help`</span><span class="sxs-lookup"><span data-stu-id="9fa3a-224">For example: `sudo pwsh -c Update-Help`</span></span>

<span data-ttu-id="9fa3a-225">De acceptabele waarden zijn:</span><span class="sxs-lookup"><span data-stu-id="9fa3a-225">The acceptable values are:</span></span>

- <span data-ttu-id="9fa3a-226">CurrentUser</span><span class="sxs-lookup"><span data-stu-id="9fa3a-226">CurrentUser</span></span>
- <span data-ttu-id="9fa3a-227">AllUsers</span><span class="sxs-lookup"><span data-stu-id="9fa3a-227">AllUsers</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.UpdateHelpScope
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: CurrentUser
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9fa3a-228">-Bronpad</span><span class="sxs-lookup"><span data-stu-id="9fa3a-228">-SourcePath</span></span>

<span data-ttu-id="9fa3a-229">Hiermee geeft u een bestandsmap op waarin `Update-Help` bijgewerkte Help-bestanden worden opgehaald, in plaats van ze van Internet te downloaden.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-229">Specifies a file system folder where `Update-Help` gets updated help files, instead of downloading them from the internet.</span></span> <span data-ttu-id="9fa3a-230">Geef het pad van een map op.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-230">Enter the path of a folder.</span></span> <span data-ttu-id="9fa3a-231">Geef geen bestands naam of bestandsnaam extensie op.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-231">Don't specify a file name or file name extension.</span></span> <span data-ttu-id="9fa3a-232">U kunt een map, zoals een, uit de `Get-Item` `Get-ChildItem` cmdlets, naar koppelen `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="9fa3a-232">You can pipeline a folder, such as one from the `Get-Item` or `Get-ChildItem` cmdlets, to `Update-Help`.</span></span>

<span data-ttu-id="9fa3a-233">`Update-Help`Downloadt standaard bijgewerkte Help-bestanden van het internet.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-233">By default, `Update-Help` downloads updated help files from the internet.</span></span> <span data-ttu-id="9fa3a-234">Gebruik **SourcePath** wanneer u de cmdlet hebt gebruikt `Save-Help` om bijgewerkte Help-bestanden te downloaden naar een map.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-234">Use **SourcePath** when you've used the `Save-Help` cmdlet to download updated help files to a directory.</span></span>

<span data-ttu-id="9fa3a-235">Als u een standaard waarde voor **SourcePath** wilt opgeven, gaat u naar **Groepsbeleid**, **computer configuratie** en **stelt u het standaard bronpad voor update-Help** in.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-235">To specify a default value for **SourcePath**, go to **Group Policy**, **Computer Configuration**, and **Set the default source path for Update-Help**.</span></span> <span data-ttu-id="9fa3a-236">Met deze groepsbeleid instelling wordt voor komen dat gebruikers `Update-Help` Help-bestanden downloaden van het internet.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-236">This Group Policy setting prevents users from using `Update-Help` to download help files from the internet.</span></span>
<span data-ttu-id="9fa3a-237">Zie [about_Group_Policy_Settings](./About/about_Group_Policy_Settings.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-237">For more information, see [about_Group_Policy_Settings](./About/about_Group_Policy_Settings.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases: Path

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9fa3a-238">-UICulture</span><span class="sxs-lookup"><span data-stu-id="9fa3a-238">-UICulture</span></span>

<span data-ttu-id="9fa3a-239">Hiermee geeft u de UI-cultuur waarden `Update-Help` op die worden gebruikt voor het ophalen van bijgewerkte Help-bestanden.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-239">Specifies UI culture values that `Update-Help` uses to get updated help files.</span></span> <span data-ttu-id="9fa3a-240">Voer een of meer taal codes in, zoals **es-es**, een variabele die cultuur objecten bevat of een opdracht die cultuur objecten, zoals een of-opdracht, ophalen `Get-Culture` `Get-UICulture` .</span><span class="sxs-lookup"><span data-stu-id="9fa3a-240">Enter one or more language codes, such as **es-ES**, a variable that contains culture objects, or a command that gets culture objects, such as a `Get-Culture` or `Get-UICulture` command.</span></span> <span data-ttu-id="9fa3a-241">Joker tekens zijn niet toegestaan en u kunt geen gedeeltelijke taal code verzenden, zoals **de**.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-241">Wildcard characters aren't permitted and you can't submit a partial language code, such as **de**.</span></span>

<span data-ttu-id="9fa3a-242">Hiermee worden standaard `Update-Help` Help-bestanden in de UI-cultuur ingesteld voor het besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-242">By default, `Update-Help` gets help files in the UI culture set for the operating system.</span></span> <span data-ttu-id="9fa3a-243">Als u de para meter **uiCulture** opgeeft, `Update-Help` zoekt alleen naar de opgegeven gebruikersinterface cultuur.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-243">If you specify the **UICulture** parameter, `Update-Help` looks for help only for the specified UI culture.</span></span>

> [!NOTE]
> <span data-ttu-id="9fa3a-244">Ubuntu 18,04 heeft de standaard land instelling gewijzigd in `C.UTF.8` , een niet-herkende UI-cultuur.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-244">Ubuntu 18.04 changed the default locale setting to `C.UTF.8`, which is not a recognized UI culture.</span></span> <span data-ttu-id="9fa3a-245">`Update-Help` de Help kan niet op de achtergrond worden gedownload, tenzij u deze para meter gebruikt met een ondersteunde land instelling zoals `en-US` .</span><span class="sxs-lookup"><span data-stu-id="9fa3a-245">`Update-Help` silently fails to download help unless you use this parameter with a supported locale like `en-US`.</span></span> <span data-ttu-id="9fa3a-246">Dit kan gebeuren op elk platform dat gebruikmaakt van een niet-ondersteunde waarde.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-246">This could occur on any platform that uses an unsupported value.</span></span>

<span data-ttu-id="9fa3a-247">Opdrachten die gebruikmaken van de para meter **uiCulture** , worden alleen uitgevoerd wanneer de module Help-bestanden voor de opgegeven UI-cultuur bevat.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-247">Commands that use the **UICulture** parameter succeed only when the module provides help files for the specified UI culture.</span></span> <span data-ttu-id="9fa3a-248">Als de opdracht mislukt omdat de opgegeven GEBRUIKERSINTERFACE cultuur niet wordt ondersteund, wordt een fout bericht weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-248">If the command fails because the specified UI culture isn't supported, an error message is displayed.</span></span>

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

### <span data-ttu-id="9fa3a-249">-UseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="9fa3a-249">-UseDefaultCredentials</span></span>

<span data-ttu-id="9fa3a-250">Hiermee wordt aangegeven dat `Update-Help` de opdracht wordt uitgevoerd, met inbegrip van het downloaden van Internet, met behulp van de referenties van de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-250">Indicates that `Update-Help` runs the command, including the internet download, by using the credentials of the current user.</span></span> <span data-ttu-id="9fa3a-251">Standaard wordt de opdracht uitgevoerd zonder expliciete referenties.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-251">By default, the command runs without explicit credentials.</span></span>

<span data-ttu-id="9fa3a-252">Deze para meter is alleen effectief wanneer het webdownloaden NT LAN Manager (NTLM), onderhandelen of Kerberos-verificatie gebruikt.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-252">This parameter is effective only when the web download uses NT LAN Manager (NTLM), negotiate, or Kerberos-based authentication.</span></span>

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

### <span data-ttu-id="9fa3a-253">-Confirm</span><span class="sxs-lookup"><span data-stu-id="9fa3a-253">-Confirm</span></span>

<span data-ttu-id="9fa3a-254">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-254">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="9fa3a-255">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="9fa3a-255">-WhatIf</span></span>

<span data-ttu-id="9fa3a-256">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-256">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="9fa3a-257">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-257">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="9fa3a-258">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9fa3a-258">CommonParameters</span></span>

<span data-ttu-id="9fa3a-259">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-259">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9fa3a-260">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-260">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9fa3a-261">INVOER</span><span class="sxs-lookup"><span data-stu-id="9fa3a-261">INPUTS</span></span>

### <span data-ttu-id="9fa3a-262">System. IO. DirectoryInfo</span><span class="sxs-lookup"><span data-stu-id="9fa3a-262">System.IO.DirectoryInfo</span></span>

<span data-ttu-id="9fa3a-263">U kunt een mappad door sluizen naar `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="9fa3a-263">You can pipe a directory path to `Update-Help`.</span></span>

### <span data-ttu-id="9fa3a-264">System. Management. Automation. PSModuleInfo</span><span class="sxs-lookup"><span data-stu-id="9fa3a-264">System.Management.Automation.PSModuleInfo</span></span>

<span data-ttu-id="9fa3a-265">U kunt een module-object vanuit de `Get-Module` cmdlet door sluizen naar `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="9fa3a-265">You can pipe a module object from the `Get-Module` cmdlet to `Update-Help`.</span></span>

## <span data-ttu-id="9fa3a-266">UITVOER</span><span class="sxs-lookup"><span data-stu-id="9fa3a-266">OUTPUTS</span></span>

### <span data-ttu-id="9fa3a-267">Geen</span><span class="sxs-lookup"><span data-stu-id="9fa3a-267">None</span></span>

<span data-ttu-id="9fa3a-268">`Update-Help` Er wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-268">`Update-Help` doesn't generate any output.</span></span>

## <span data-ttu-id="9fa3a-269">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="9fa3a-269">NOTES</span></span>

<span data-ttu-id="9fa3a-270">Als u de Help voor de Power shell core-modules wilt bijwerken die de opdrachten bevatten die zijn geïnstalleerd met Power shell of een module in de `$PSHOME\Modules` Directory, start u Power shell met de optie om **als Administrator uit te voeren**.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-270">To update help for the PowerShell Core modules, that contain the commands that are installed with PowerShell, or any module in the `$PSHOME\Modules` directory, start PowerShell with the option to **Run as administrator**.</span></span>

<span data-ttu-id="9fa3a-271">Alleen leden van de groep Administrators op de computer kunnen de Help-informatie voor de Power shell core-modules, de opdrachten die worden geïnstalleerd samen met Power shell en modules in de `$PSHOME\Modules` map bijwerken.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-271">Only members of the Administrators group on the computer can update help for the PowerShell Core modules, the commands that are installed together with PowerShell, and for modules in the `$PSHOME\Modules` folder.</span></span> <span data-ttu-id="9fa3a-272">Als u geen machtiging hebt om Help-bestanden bij te werken, kunt u de Help-bestanden online lezen.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-272">If you don't have permission to update help files, you can read the help files online.</span></span> <span data-ttu-id="9fa3a-273">Bijvoorbeeld `Get-Help Update-Help -Online`.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-273">For example, `Get-Help Update-Help -Online`.</span></span>

<span data-ttu-id="9fa3a-274">Modules zijn de kleinste eenheid van Help die kan worden bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-274">Modules are the smallest unit of updatable help.</span></span> <span data-ttu-id="9fa3a-275">U kunt de Help voor een bepaalde cmdlet niet bijwerken.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-275">You can't update help for a particular cmdlet.</span></span> <span data-ttu-id="9fa3a-276">Als u de module wilt vinden die een bepaalde cmdlet bevat, gebruikt u **de eigenschap PropertyName** van de `Get-Command` cmdlet, bijvoorbeeld `(Get-Command Update-Help).ModuleName` .</span><span class="sxs-lookup"><span data-stu-id="9fa3a-276">To find the module that contains a particular cmdlet, use the **ModuleName** property of the `Get-Command` cmdlet, for example, `(Get-Command Update-Help).ModuleName`.</span></span>

<span data-ttu-id="9fa3a-277">Omdat Help-bestanden in de module directory zijn geïnstalleerd, `Update-Help` kan de cmdlet alleen een bijgewerkt Help-bestand installeren voor modules die op de computer zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-277">Because help files are installed in the module directory, the `Update-Help` cmdlet can install updated help file only for modules that are installed on the computer.</span></span> <span data-ttu-id="9fa3a-278">De `Save-Help` cmdlet kan echter de Help opslaan voor modules die niet op de computer zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-278">However, the `Save-Help` cmdlet can save help for modules that aren't installed on the computer.</span></span>

<span data-ttu-id="9fa3a-279">Als er `Update-Help` geen bijgewerkte Help-bestanden kunnen worden gevonden voor een module, of als er geen bijgewerkte Help kan worden gevonden in de opgegeven taal, wordt de installatie zonder fouten voortgezet.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-279">If `Update-Help` can't find updated help files for a module, or can't find updated help in the specified language, it continues silently without displaying an error message.</span></span> <span data-ttu-id="9fa3a-280">Als u de status en Details van de voortgang wilt bekijken, gebruikt u de para meter **uitgebreid** .</span><span class="sxs-lookup"><span data-stu-id="9fa3a-280">To see status and progress details, use the **Verbose** parameter.</span></span>

<span data-ttu-id="9fa3a-281">De `Update-Help` cmdlet is geïntroduceerd in Windows Power shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-281">The `Update-Help` cmdlet was introduced in Windows PowerShell 3.0.</span></span> <span data-ttu-id="9fa3a-282">Deze functie werkt niet in eerdere versies van Power shell.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-282">It doesn't work in earlier versions of PowerShell.</span></span> <span data-ttu-id="9fa3a-283">Op computers met Windows Power Shell 2,0 en Windows Power Shell 3,0 gebruikt u de `Update-Help` cmdlet in een Windows Power shell 3,0-sessie om Help-bestanden te downloaden en bij te werken.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-283">On computers that have both Windows PowerShell 2.0 and Windows PowerShell 3.0, use the `Update-Help` cmdlet in a Windows PowerShell 3.0 session to download and update help files.</span></span> <span data-ttu-id="9fa3a-284">De Help-bestanden zijn beschikbaar voor zowel Windows Power Shell 2,0 als Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-284">The help files are available to both Windows PowerShell 2.0 and Windows PowerShell 3.0.</span></span>

<span data-ttu-id="9fa3a-285">De `Update-Help` `Save-Help` cmdlets en gebruiken de volgende poorten om Help-bestanden te downloaden: poort 80 voor http en poort 443 voor HTTPS.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-285">The `Update-Help` and `Save-Help` cmdlets use the following ports to download help files: Port 80 for HTTP and port 443 for HTTPS.</span></span>

<span data-ttu-id="9fa3a-286">`Update-Help` ondersteunt alle modules en de Power shell core-modules. Andere modules worden niet ondersteund.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-286">`Update-Help` supports all modules and the PowerShell Core snap-ins. It doesn't support any other snap-ins.</span></span>

<span data-ttu-id="9fa3a-287">Als u de Help wilt bijwerken voor een module op een locatie die niet wordt weer gegeven in de `$env:PSModulePath` omgevings variabele, importeert u de module in de huidige sessie en voert u vervolgens een `Update-Help` opdracht uit.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-287">To update help for a module in a location that isn't listed in the `$env:PSModulePath` environment variable, import the module into the current session and then run an `Update-Help` command.</span></span> <span data-ttu-id="9fa3a-288">`Update-Help`Zonder para meters uitvoeren of de **module** parameter gebruiken om de module naam op te geven.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-288">Run `Update-Help` without parameters or use the **Module** parameter to specify the module name.</span></span> <span data-ttu-id="9fa3a-289">Met de **module** parameter van `Update-Help` de `Save-Help` cmdlets en wordt het volledige pad van een module bestand of module manifest bestand niet geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-289">The **Module** parameter of the `Update-Help` and `Save-Help` cmdlets doesn't accept the full path of a module file or module manifest file.</span></span>

<span data-ttu-id="9fa3a-290">Elke module kan de Help die kan worden bijgewerkt ondersteunen.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-290">Any module can support Updatable Help.</span></span> <span data-ttu-id="9fa3a-291">Zie [ondersteunende Help-informatie](/powershell/scripting/developer/module/supporting-updatable-help)voor instructies voor het ondersteunen van Help-informatie in de modules die u ontwerpt.</span><span class="sxs-lookup"><span data-stu-id="9fa3a-291">For instructions for supporting Updatable Help in the modules that you author, see [Supporting Updatable Help](/powershell/scripting/developer/module/supporting-updatable-help).</span></span>

<span data-ttu-id="9fa3a-292">De `Update-Help` `Save-Help` cmdlets en worden niet ondersteund op Windows Preinstallation Environment (Windows PE).</span><span class="sxs-lookup"><span data-stu-id="9fa3a-292">The `Update-Help` and `Save-Help` cmdlets are not supported on Windows Preinstallation Environment (Windows PE).</span></span>

## <span data-ttu-id="9fa3a-293">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="9fa3a-293">RELATED LINKS</span></span>

[<span data-ttu-id="9fa3a-294">Get-cultuur</span><span class="sxs-lookup"><span data-stu-id="9fa3a-294">Get-Culture</span></span>](../Microsoft.PowerShell.Utility/Get-Culture.md)

[<span data-ttu-id="9fa3a-295">Get-Help</span><span class="sxs-lookup"><span data-stu-id="9fa3a-295">Get-Help</span></span>](Get-Help.md)

[<span data-ttu-id="9fa3a-296">Get-module</span><span class="sxs-lookup"><span data-stu-id="9fa3a-296">Get-Module</span></span>](Get-Module.md)

[<span data-ttu-id="9fa3a-297">Get-UICulture</span><span class="sxs-lookup"><span data-stu-id="9fa3a-297">Get-UICulture</span></span>](../Microsoft.PowerShell.Utility/Get-UICulture.md)

[<span data-ttu-id="9fa3a-298">Begin taak</span><span class="sxs-lookup"><span data-stu-id="9fa3a-298">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="9fa3a-299">Opslaan-Help</span><span class="sxs-lookup"><span data-stu-id="9fa3a-299">Save-Help</span></span>](Save-Help.md)
