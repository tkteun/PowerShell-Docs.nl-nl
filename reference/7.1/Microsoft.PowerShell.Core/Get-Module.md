---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 12/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-module?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Module
ms.openlocfilehash: 1f06d1e7114a84ea89097167b188ded605f81aa0
ms.sourcegitcommit: 7b376314e7640c39a53aac9f0db8bb935514a960
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/03/2020
ms.locfileid: "96564534"
---
# <span data-ttu-id="85c62-102">Get-Module</span><span class="sxs-lookup"><span data-stu-id="85c62-102">Get-Module</span></span>

## <span data-ttu-id="85c62-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="85c62-103">SYNOPSIS</span></span>
<span data-ttu-id="85c62-104">De modules weer geven die zijn geïmporteerd in de huidige sessie of die kunnen worden geïmporteerd uit de PSModulePath.</span><span class="sxs-lookup"><span data-stu-id="85c62-104">List the modules imported in the current session or that can be imported from the PSModulePath.</span></span>

## <span data-ttu-id="85c62-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="85c62-105">SYNTAX</span></span>

### <span data-ttu-id="85c62-106">Geladen (standaard)</span><span class="sxs-lookup"><span data-stu-id="85c62-106">Loaded (Default)</span></span>

```
Get-Module [[-Name] <String[]>] [-FullyQualifiedName <ModuleSpecification[]>] [-All] [<CommonParameters>]
```

### <span data-ttu-id="85c62-107">Beschikbaar</span><span class="sxs-lookup"><span data-stu-id="85c62-107">Available</span></span>

```
Get-Module [[-Name] <String[]>] [-FullyQualifiedName <ModuleSpecification[]>] [-All] [-ListAvailable]
 [-PSEdition <String>] [-SkipEditionCheck] [-Refresh] [<CommonParameters>]
```

### <span data-ttu-id="85c62-108">PsSession</span><span class="sxs-lookup"><span data-stu-id="85c62-108">PsSession</span></span>

```
Get-Module [[-Name] <String[]>] [-FullyQualifiedName <ModuleSpecification[]>] [-ListAvailable]
 [-PSEdition <String>] [-SkipEditionCheck] [-Refresh] -PSSession <PSSession> [<CommonParameters>]
```

### <span data-ttu-id="85c62-109">CimSession</span><span class="sxs-lookup"><span data-stu-id="85c62-109">CimSession</span></span>

```
Get-Module [[-Name] <String[]>] [-FullyQualifiedName <ModuleSpecification[]>] [-ListAvailable]
 [-SkipEditionCheck] [-Refresh] -CimSession <CimSession> [-CimResourceUri <Uri>] [-CimNamespace <String>]
 [<CommonParameters>]
```

## <span data-ttu-id="85c62-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="85c62-110">DESCRIPTION</span></span>

<span data-ttu-id="85c62-111">De `Get-Module` cmdlet geeft een lijst van de Power shell-modules die zijn geïmporteerd of die kunnen worden geïmporteerd in een Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="85c62-111">The `Get-Module` cmdlet lists the PowerShell modules that have been imported, or that can be imported, into a PowerShell session.</span></span> <span data-ttu-id="85c62-112">Zonder para meters worden `Get-Module` modules opgehaald die in de huidige sessie zijn geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="85c62-112">Without parameters, `Get-Module` gets modules that have been imported into the current session.</span></span> <span data-ttu-id="85c62-113">De para meter **ListAvailable** wordt gebruikt om een lijst weer te geven met de modules die kunnen worden geïmporteerd uit de paden die zijn opgegeven in de PSModulePath-omgevings variabele ( `$env:PSModulePath` ).</span><span class="sxs-lookup"><span data-stu-id="85c62-113">The **ListAvailable** parameter is used to list the modules that are available to be imported from the paths specified in the PSModulePath environment variable (`$env:PSModulePath`).</span></span>

<span data-ttu-id="85c62-114">Het module-object dat `Get-Module` retourneert, bevat waardevolle informatie over de module.</span><span class="sxs-lookup"><span data-stu-id="85c62-114">The module object that `Get-Module` returns contains valuable information about the module.</span></span> <span data-ttu-id="85c62-115">U kunt de module-objecten ook door sluizen naar andere cmdlets, zoals de- `Import-Module` en- `Remove-Module` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="85c62-115">You can also pipe the module objects to other cmdlets, such as the `Import-Module` and `Remove-Module` cmdlets.</span></span>

<span data-ttu-id="85c62-116">`Get-Module` Hiermee worden modules weer gegeven, maar niet geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="85c62-116">`Get-Module` lists modules, but it does not import them.</span></span> <span data-ttu-id="85c62-117">Vanaf Windows Power Shell 3,0 worden modules automatisch geïmporteerd wanneer u een opdracht in de module gebruikt, maar met een `Get-Module` opdracht wordt een automatische import bewerking niet geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="85c62-117">Starting in Windows PowerShell 3.0, modules are automatically imported when you use a command in the module, but a `Get-Module` command does not trigger an automatic import.</span></span> <span data-ttu-id="85c62-118">U kunt de modules ook importeren in uw-sessie met behulp van de- `Import-Module` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="85c62-118">You can also import the modules into your session using the `Import-Module` cmdlet.</span></span>

<span data-ttu-id="85c62-119">Vanaf Windows Power Shell 3,0 kunt u modules ophalen en vervolgens importeren van externe sessies in de lokale sessie.</span><span class="sxs-lookup"><span data-stu-id="85c62-119">Starting in Windows PowerShell 3.0, you can get and then, import modules from remote sessions into the local session.</span></span> <span data-ttu-id="85c62-120">Deze strategie maakt gebruik van de impliciete externe functie van Power shell en komt overeen met het gebruik van de `Import-PSSession` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="85c62-120">This strategy uses the Implicit Remoting feature of PowerShell and is equivalent to using the `Import-PSSession` cmdlet.</span></span> <span data-ttu-id="85c62-121">Wanneer u opdrachten gebruikt in modules die vanuit een andere sessie worden geïmporteerd, worden de opdrachten impliciet uitgevoerd in de externe sessie.</span><span class="sxs-lookup"><span data-stu-id="85c62-121">When you use commands in modules imported from another session, the commands run implicitly in the remote session.</span></span> <span data-ttu-id="85c62-122">Met deze functie kunt u de externe computer vanuit de lokale sessie beheren.</span><span class="sxs-lookup"><span data-stu-id="85c62-122">This feature lets you manage the remote computer from the local session.</span></span>

<span data-ttu-id="85c62-123">Vanuit Windows Power Shell 3,0 kunt u ook de modules van `Get-Module` `Import-Module` Common Information Model (CIM) gebruiken en importeren.</span><span class="sxs-lookup"><span data-stu-id="85c62-123">Also, starting in Windows PowerShell 3.0, you can use `Get-Module` and `Import-Module` to get and import Common Information Model (CIM) modules.</span></span> <span data-ttu-id="85c62-124">Met CIM-modules worden cmdlets in CDXML-bestanden (cmdlet definition XML) gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="85c62-124">CIM modules define cmdlets in Cmdlet Definition XML (CDXML) files.</span></span> <span data-ttu-id="85c62-125">Met deze functie kunt u cmdlets gebruiken die zijn geïmplementeerd in niet-beheerde code-assembly's, zoals die zijn geschreven in C++.</span><span class="sxs-lookup"><span data-stu-id="85c62-125">This feature lets you use cmdlets that are implemented in non-managed code assemblies, such as those written in C++.</span></span>

<span data-ttu-id="85c62-126">Impliciete externe toegang kan worden gebruikt voor het beheren van externe computers waarvoor Power shell Remoting is ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="85c62-126">Implicit remoting can be used to manage remote computers that have PowerShell remoting enabled.</span></span>
<span data-ttu-id="85c62-127">Maak een **PSSession** op de externe computer en gebruik vervolgens de para meter **PSSession** van `Get-Module` om de Power shell-modules in de externe sessie op te halen.</span><span class="sxs-lookup"><span data-stu-id="85c62-127">Create a **PSSession** on the remote computer and then use the **PSSession** parameter of `Get-Module` to get the PowerShell modules in the remote session.</span></span> <span data-ttu-id="85c62-128">Wanneer u een module uit de externe sessie importeert, worden de geïmporteerde opdrachten uitgevoerd in de sessie op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="85c62-128">When you import a module from the remote session the imported commands run in the session on the remote computer.</span></span>

<span data-ttu-id="85c62-129">U kunt een vergelijk bare strategie gebruiken voor het beheren van computers waarop geen externe communicatie van Power shell is ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="85c62-129">You can use a similar strategy to manage computers that do not have PowerShell remoting enabled.</span></span>
<span data-ttu-id="85c62-130">Dit zijn onder andere computers waarop het Windows-besturings systeem niet wordt uitgevoerd en computers met Power shell, maar waarvoor geen externe communicatie van Power shell is ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="85c62-130">These include computers that are not running the Windows operating system, and computers that have PowerShell but do not have PowerShell remoting enabled.</span></span>

<span data-ttu-id="85c62-131">Maak eerst een CIM-sessie op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="85c62-131">Start by creating a CIM session on the remote computer.</span></span> <span data-ttu-id="85c62-132">Een CIM-sessie is een verbinding met Windows Management Instrumentation (WMI) op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="85c62-132">A CIM session is a connection to Windows Management Instrumentation (WMI) on the remote computer.</span></span> <span data-ttu-id="85c62-133">Gebruik vervolgens de para meter **CIMSession** van `Get-Module` om CIM-modules op te halen uit de CIM-sessie.</span><span class="sxs-lookup"><span data-stu-id="85c62-133">Then use the **CIMSession** parameter of `Get-Module` to get CIM modules from the CIM session.</span></span> <span data-ttu-id="85c62-134">Wanneer u een CIM-module importeert met behulp van de- `Import-Module` cmdlet en vervolgens de geïmporteerde opdrachten uitvoert, worden de opdrachten impliciet uitgevoerd op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="85c62-134">When you import a CIM module by using the `Import-Module` cmdlet and then run the imported commands, the commands run implicitly on the remote computer.</span></span> <span data-ttu-id="85c62-135">U kunt deze WMI-en CIM-strategie gebruiken om de externe computer te beheren.</span><span class="sxs-lookup"><span data-stu-id="85c62-135">You can use this WMI and CIM strategy to manage the remote computer.</span></span>

## <span data-ttu-id="85c62-136">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="85c62-136">EXAMPLES</span></span>

### <span data-ttu-id="85c62-137">Voor beeld 1: modules ophalen die in de huidige sessie zijn geïmporteerd</span><span class="sxs-lookup"><span data-stu-id="85c62-137">Example 1: Get modules imported into the current session</span></span>

```powershell
Get-Module
```

<span data-ttu-id="85c62-138">Met deze opdracht worden modules opgehaald die in de huidige sessie zijn geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="85c62-138">This command gets modules that have been imported into the current session.</span></span>

### <span data-ttu-id="85c62-139">Voor beeld 2: geïnstalleerde modules en beschik bare modules ophalen</span><span class="sxs-lookup"><span data-stu-id="85c62-139">Example 2: Get installed modules and available modules</span></span>

```powershell
Get-Module -ListAvailable
```

<span data-ttu-id="85c62-140">Met deze opdracht worden de modules opgehaald die op de computer zijn geïnstalleerd en die in de huidige sessie kunnen worden geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="85c62-140">This command gets the modules that are installed on the computer and can be imported into the current session.</span></span>

<span data-ttu-id="85c62-141">`Get-Module` zoekt naar beschik bare modules in het pad dat is opgegeven door de omgevings variabele **$env:P smodulepath** .</span><span class="sxs-lookup"><span data-stu-id="85c62-141">`Get-Module` looks for available modules in the path specified by the **$env:PSModulePath** environment variable.</span></span> <span data-ttu-id="85c62-142">Zie [about_Modules](About/about_Modules.md) en [about_Environment_Variables](About/about_Environment_Variables.md)voor meer informatie over **PSModulePath**.</span><span class="sxs-lookup"><span data-stu-id="85c62-142">For more information about **PSModulePath**, see [about_Modules](About/about_Modules.md) and [about_Environment_Variables](About/about_Environment_Variables.md).</span></span>

### <span data-ttu-id="85c62-143">Voor beeld 3: alle geëxporteerde bestanden ophalen</span><span class="sxs-lookup"><span data-stu-id="85c62-143">Example 3: Get all exported files</span></span>

```powershell
Get-Module -ListAvailable -All
```

<span data-ttu-id="85c62-144">Met deze opdracht worden alle geëxporteerde bestanden voor alle beschik bare modules opgehaald.</span><span class="sxs-lookup"><span data-stu-id="85c62-144">This command gets all of the exported files for all available modules.</span></span>

### <span data-ttu-id="85c62-145">Voor beeld 4: een module ophalen met de volledig gekwalificeerde naam</span><span class="sxs-lookup"><span data-stu-id="85c62-145">Example 4: Get a module by its fully qualified name</span></span>

```powershell
$FullyQualifedName = @{ModuleName="Microsoft.PowerShell.Management";ModuleVersion="3.1.0.0"}
Get-Module -FullyQualifiedName $FullyQualifedName | Format-Table -Property Name,Version
```

```Output
Name                             Version
----                             -------
Microsoft.PowerShell.Management  3.1.0.0
```

<span data-ttu-id="85c62-146">Met deze opdracht wordt de module **micro soft. Power shell. Management** opgehaald door de volledig gekwalificeerde naam van de module op te geven met behulp van de para meter **FullyQualifiedName** .</span><span class="sxs-lookup"><span data-stu-id="85c62-146">This command gets the **Microsoft.PowerShell.Management** module by specifying the fully qualified name of the module by using the **FullyQualifiedName** parameter.</span></span> <span data-ttu-id="85c62-147">De opdracht Pipet de resultaten vervolgens `Format-Table` naar de cmdlet om de resultaten op te maken als een tabel met de **naam** en **versie** als kolom koppen.</span><span class="sxs-lookup"><span data-stu-id="85c62-147">The command then pipes the results into the `Format-Table` cmdlet to format the results as a table with **Name** and **Version** as the column headings.</span></span>

### <span data-ttu-id="85c62-148">Voor beeld 5: eigenschappen van een module ophalen</span><span class="sxs-lookup"><span data-stu-id="85c62-148">Example 5: Get properties of a module</span></span>

```powershell
Get-Module | Get-Member -MemberType Property | Format-Table Name
```

```Output
Name
----
AccessMode
Author
ClrVersion
CompanyName
Copyright
Definition
Description
DotNetFrameworkVersion
ExportedAliases
ExportedCmdlets
ExportedCommands
ExportedFormatFiles
ExportedFunctions
ExportedTypeFiles
ExportedVariables
ExportedWorkflows
FileList
Guid
HelpInfoUri
LogPipelineExecutionDetails
ModuleBase
ModuleList
ModuleType
Name
NestedModules
OnRemove
Path
PowerShellHostName
PowerShellHostVersion
PowerShellVersion
PrivateData
ProcessorArchitecture
RequiredAssemblies
RequiredModules
RootModule
Scripts
SessionState
Version
```

<span data-ttu-id="85c62-149">Met deze opdracht worden de eigenschappen opgehaald van het **PSModuleInfo** -object dat `Get-Module` retourneert.</span><span class="sxs-lookup"><span data-stu-id="85c62-149">This command gets the properties of the **PSModuleInfo** object that `Get-Module` returns.</span></span> <span data-ttu-id="85c62-150">Er is één object voor elk module bestand.</span><span class="sxs-lookup"><span data-stu-id="85c62-150">There is one object for each module file.</span></span>

<span data-ttu-id="85c62-151">U kunt de eigenschappen gebruiken om de module-objecten te Format teren en te filteren.</span><span class="sxs-lookup"><span data-stu-id="85c62-151">You can use the properties to format and filter the module objects.</span></span> <span data-ttu-id="85c62-152">Zie [PSModuleInfo Properties](/dotnet/api/system.management.automation.psmoduleinfo)(Engelstalig) voor meer informatie over de eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="85c62-152">For more information about the properties, see [PSModuleInfo Properties](/dotnet/api/system.management.automation.psmoduleinfo).</span></span>

<span data-ttu-id="85c62-153">De uitvoer bevat de nieuwe eigenschappen, zoals **Auteur** en **CompanyName**, die zijn geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="85c62-153">The output includes the new properties, such as **Author** and **CompanyName**, that were introduced in Windows PowerShell 3.0.</span></span>

### <span data-ttu-id="85c62-154">Voor beeld 6: alle modules op naam groeperen</span><span class="sxs-lookup"><span data-stu-id="85c62-154">Example 6: Group all modules by name</span></span>

```powershell
Get-Module -ListAvailable -All | Format-Table -Property Name, Moduletype, Path -Groupby Name
```

```Output
Name: AppLocker

Name      ModuleType Path
----      ---------- ----
AppLocker   Manifest C:\Windows\system32\WindowsPowerShell\v1.0\Modules\AppLocker\AppLocker.psd1


   Name: Appx

Name ModuleType Path
---- ---------- ----
Appx   Manifest C:\Windows\system32\WindowsPowerShell\v1.0\Modules\Appx\en-US\Appx.psd1
Appx   Manifest C:\Windows\system32\WindowsPowerShell\v1.0\Modules\Appx\Appx.psd1
Appx     Script C:\Windows\system32\WindowsPowerShell\v1.0\Modules\Appx\Appx.psm1


   Name: BestPractices

Name          ModuleType Path
----          ---------- ----
BestPractices   Manifest C:\Windows\system32\WindowsPowerShell\v1.0\Modules\BestPractices\BestPractices.psd1


   Name: BitsTransfer

Name         ModuleType Path
----         ---------- ----
BitsTransfer   Manifest C:\Windows\system32\WindowsPowerShell\v1.0\Modules\BitsTransfer\BitsTransfer.psd1
```

<span data-ttu-id="85c62-155">Met deze opdracht worden alle module bestanden, zowel geïmporteerd als beschikbaar, opgehaald en vervolgens gegroepeerd op module naam.</span><span class="sxs-lookup"><span data-stu-id="85c62-155">This command gets all module files, both imported and available, and then groups them by module name.</span></span> <span data-ttu-id="85c62-156">Zo kunt u de module bestanden zien die elk script exporteert.</span><span class="sxs-lookup"><span data-stu-id="85c62-156">This lets you see the module files that each script is exporting.</span></span>

### <span data-ttu-id="85c62-157">Voor beeld 7: de inhoud van een module manifest weer geven</span><span class="sxs-lookup"><span data-stu-id="85c62-157">Example 7: Display the contents of a module manifest</span></span>

<span data-ttu-id="85c62-158">Met deze opdrachten wordt de inhoud van het module manifest voor de Windows Power shell **BitsTransfer** -module weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="85c62-158">These commands display the contents of the module manifest for the Windows PowerShell **BitsTransfer** module.</span></span>

<span data-ttu-id="85c62-159">Modules hoeven geen manifest bestanden te bevatten.</span><span class="sxs-lookup"><span data-stu-id="85c62-159">Modules are not required to have manifest files.</span></span> <span data-ttu-id="85c62-160">Wanneer ze een manifest bestand hebben, is het manifest bestand alleen vereist voor het toevoegen van een versie nummer.</span><span class="sxs-lookup"><span data-stu-id="85c62-160">When they do have a manifest file, the manifest file is required only to include a version number.</span></span> <span data-ttu-id="85c62-161">Manifest bestanden bevatten echter vaak nuttige informatie over een module, de vereisten en de inhoud ervan.</span><span class="sxs-lookup"><span data-stu-id="85c62-161">However, manifest files often provide useful information about a module, its requirements, and its contents.</span></span>

```powershell
# First command
$m = Get-Module -list -Name BitsTransfer

# Second command
Get-Content $m.Path
```

```Output
@ {
    GUID               = "{8FA5064B-8479-4c5c-86EA-0D311FE48875}"
    Author             = "Microsoft Corporation"
    CompanyName        = "Microsoft Corporation"
    Copyright          = "Microsoft Corporation. All rights reserved."
    ModuleVersion      = "1.0.0.0"
    Description        = "Windows PowerShell File Transfer Module"
    PowerShellVersion  = "2.0"
    CLRVersion         = "2.0"
    NestedModules      = "Microsoft.BackgroundIntelligentTransfer.Management"
    FormatsToProcess   = "FileTransfer.Format.ps1xml"
    RequiredAssemblies = Join-Path $psScriptRoot "Microsoft.BackgroundIntelligentTransfer.Management.Interop.dll"
}
```

<span data-ttu-id="85c62-162">Met de eerste opdracht wordt het PSModuleInfo-object opgehaald dat de BitsTransfer-module vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="85c62-162">The first command gets the PSModuleInfo object that represents BitsTransfer module.</span></span> <span data-ttu-id="85c62-163">Hiermee wordt het object in de `$m` variabele opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="85c62-163">It saves the object in the `$m` variable.</span></span>

<span data-ttu-id="85c62-164">Met de tweede opdracht wordt de `Get-Content` cmdlet gebruikt om de inhoud van het manifest bestand in het opgegeven pad op te halen.</span><span class="sxs-lookup"><span data-stu-id="85c62-164">The second command uses the `Get-Content` cmdlet to get the content of the manifest file in the specified path.</span></span> <span data-ttu-id="85c62-165">De teken punt notatie wordt gebruikt om het pad naar het manifest bestand op te halen dat is opgeslagen in de eigenschap Path van het object.</span><span class="sxs-lookup"><span data-stu-id="85c62-165">It uses dot notation to get the path to the manifest file, which is stored in the Path property of the object.</span></span> <span data-ttu-id="85c62-166">De uitvoer toont de inhoud van het module manifest.</span><span class="sxs-lookup"><span data-stu-id="85c62-166">The output shows the contents of the module manifest.</span></span>

### <span data-ttu-id="85c62-167">Voor beeld 8: bestanden in de module directory weer geven</span><span class="sxs-lookup"><span data-stu-id="85c62-167">Example 8: List files in module directory</span></span>

```powershell
dir (Get-Module -ListAvailable FileTransfer).ModuleBase
```

```Output
Directory: C:\Windows\system32\WindowsPowerShell\v1.0\Modules\FileTransfer
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        12/16/2008  12:36 PM            en-US
-a---        11/19/2008  11:30 PM      16184 FileTransfer.Format.ps1xml
-a---        11/20/2008  11:30 PM       1044 FileTransfer.psd1
-a---        12/16/2008  12:20 AM     108544 Microsoft.BackgroundIntelligentTransfer.Management.Interop.dll
```

<span data-ttu-id="85c62-168">Met deze opdracht worden de bestanden in de map van de module weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="85c62-168">This command lists the files in the directory of the module.</span></span> <span data-ttu-id="85c62-169">Dit is een andere manier om te bepalen wat zich in een module bevindt voordat u deze importeert.</span><span class="sxs-lookup"><span data-stu-id="85c62-169">This is another way to determine what is in a module before you import it.</span></span> <span data-ttu-id="85c62-170">Sommige modules hebben mogelijk Help-bestanden of leesmij-bestanden waarin de module wordt beschreven.</span><span class="sxs-lookup"><span data-stu-id="85c62-170">Some modules might have help files or ReadMe files that describe the module.</span></span>

### <span data-ttu-id="85c62-171">Voor beeld 9: modules ophalen die op een computer zijn geïnstalleerd</span><span class="sxs-lookup"><span data-stu-id="85c62-171">Example 9: Get modules installed on a computer</span></span>

```powershell
$s = New-PSSession -ComputerName Server01

Get-Module -PSSession $s -ListAvailable
```

<span data-ttu-id="85c62-172">Met deze opdrachten worden de modules opgehaald die zijn geïnstalleerd op de Server01-computer.</span><span class="sxs-lookup"><span data-stu-id="85c62-172">These commands get the modules that are installed on the Server01 computer.</span></span>

<span data-ttu-id="85c62-173">De eerste opdracht gebruikt de `New-PSSession` cmdlet om een **PSSession** te maken op de Server01-computer.</span><span class="sxs-lookup"><span data-stu-id="85c62-173">The first command uses the `New-PSSession` cmdlet to create a **PSSession** on the Server01 computer.</span></span> <span data-ttu-id="85c62-174">Met de opdracht slaat u de **PSSession** op in de variabele $s.</span><span class="sxs-lookup"><span data-stu-id="85c62-174">The command saves the **PSSession** in the $s variable.</span></span>

<span data-ttu-id="85c62-175">De tweede opdracht maakt gebruik van de **PSSession** -en **ListAvailable** -para meters van `Get-Module` om de modules in de **PSSession** in de variabele op te halen `$s` .</span><span class="sxs-lookup"><span data-stu-id="85c62-175">The second command uses the **PSSession** and **ListAvailable** parameters of `Get-Module` to get the modules in the **PSSession** in the `$s` variable.</span></span>

<span data-ttu-id="85c62-176">Als u modules van andere sessies naar de cmdlet pipet `Import-Module` , `Import-Module` importeert de module in de huidige sessie met behulp van de functie impliciete externe toegang.</span><span class="sxs-lookup"><span data-stu-id="85c62-176">If you pipe modules from other sessions to the `Import-Module` cmdlet, `Import-Module` imports the module into the current session by using the implicit remoting feature.</span></span> <span data-ttu-id="85c62-177">Dit is gelijk aan het gebruik van de `Import-PSSession` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="85c62-177">This is equivalent to using the `Import-PSSession` cmdlet.</span></span> <span data-ttu-id="85c62-178">U kunt de-cmdlets uit de module in de huidige sessie gebruiken, maar met opdrachten die gebruikmaken van deze cmdlets wordt de externe sessie daad werkelijk uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="85c62-178">You can use the cmdlets from the module in the current session, but commands that use these cmdlets actually run the remote session.</span></span> <span data-ttu-id="85c62-179">Zie en voor meer informatie [`Import-Module`](Import-Module.md) [`Import-PSSession`](../Microsoft.PowerShell.Utility/Import-PSSession.md) .</span><span class="sxs-lookup"><span data-stu-id="85c62-179">For more information, see [`Import-Module`](Import-Module.md) and [`Import-PSSession`](../Microsoft.PowerShell.Utility/Import-PSSession.md).</span></span>

### <span data-ttu-id="85c62-180">Voor beeld 10: een computer beheren waarop het Windows-besturings systeem niet wordt uitgevoerd</span><span class="sxs-lookup"><span data-stu-id="85c62-180">Example 10: Manage a computer that does not run the Windows operating system</span></span>

<span data-ttu-id="85c62-181">Met de opdrachten in dit voor beeld kunt u de opslag systemen beheren van een externe computer waarop het Windows-besturings systeem niet wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="85c62-181">The commands in this example enable you to manage the storage systems of a remote computer that is not running the Windows operating system.</span></span>
<span data-ttu-id="85c62-182">In dit voor beeld, omdat de beheerder van de computer de WMI-provider voor module detectie heeft geïnstalleerd, kunnen de CIM-opdrachten de standaard waarden gebruiken die zijn ontworpen voor de provider.</span><span class="sxs-lookup"><span data-stu-id="85c62-182">In this example, because the administrator of the computer has installed the Module Discovery WMI provider, the CIM commands can use the default values, which are designed for the provider.</span></span>

```powershell
$cs = New-CimSession -ComputerName RSDGF03
Get-Module -CimSession $cs -Name Storage | Import-Module
Get-Command Get-Disk
```

```Output
CommandType     Name                  ModuleName
-----------     ----                  ----------
Function        Get-Disk              Storage
```

```powershell
Get-Disk
```

```Output
Number Friendly Name              OperationalStatus          Total Size Partition Style
------ -------------              -----------------          ---------- ---------------
0      Virtual HD ATA Device      Online                          40 GB MBR
```

<span data-ttu-id="85c62-183">De eerste opdracht gebruikt de `New-CimSession` cmdlet om een sessie te maken op de externe computer RSDGF03.</span><span class="sxs-lookup"><span data-stu-id="85c62-183">The first command uses the `New-CimSession` cmdlet to create a session on the RSDGF03 remote computer.</span></span> <span data-ttu-id="85c62-184">De sessie maakt verbinding met WMI op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="85c62-184">The session connects to WMI on the remote computer.</span></span> <span data-ttu-id="85c62-185">Met de opdracht wordt de CIM-sessie in de `$cs` variabele opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="85c62-185">The command saves the CIM session in the `$cs` variable.</span></span>

<span data-ttu-id="85c62-186">Met de tweede opdracht wordt de CIM-sessie in de `$cs` variabele gebruikt om een opdracht uit te voeren `Get-Module` op de RSDGF03-computer.</span><span class="sxs-lookup"><span data-stu-id="85c62-186">The second command uses the CIM session in the `$cs` variable to run a `Get-Module` command on the RSDGF03 computer.</span></span> <span data-ttu-id="85c62-187">De opdracht gebruikt de para meter name om de opslag module op te geven.</span><span class="sxs-lookup"><span data-stu-id="85c62-187">The command uses the Name parameter to specify the Storage module.</span></span> <span data-ttu-id="85c62-188">De opdracht maakt gebruik van een pijplijn operator (|) voor het verzenden van de opslag module naar de `Import-Module` cmdlet, die deze in de lokale sessie importeert.</span><span class="sxs-lookup"><span data-stu-id="85c62-188">The command uses a pipeline operator (|) to send the Storage module to the `Import-Module` cmdlet, which imports it into the local session.</span></span>

<span data-ttu-id="85c62-189">Met de derde opdracht voert u de `Get-Command` cmdlet `Get-Disk` uit op de opdracht in de module opslag.</span><span class="sxs-lookup"><span data-stu-id="85c62-189">The third command runs the `Get-Command` cmdlet on the `Get-Disk` command in the Storage module.</span></span>
<span data-ttu-id="85c62-190">Wanneer u een CIM-module in de lokale sessie importeert, worden de CDXML-bestanden die de CIM-module vertegenwoordigen, omgezet in Power shell-scripts, die als functies in de lokale sessie worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="85c62-190">When you import a CIM module into the local session, PowerShell converts the CDXML files that represent the CIM module into PowerShell scripts, which appear as functions in the local session.</span></span>

<span data-ttu-id="85c62-191">Met de vierde opdracht voert u de `Get-Disk` opdracht uit.</span><span class="sxs-lookup"><span data-stu-id="85c62-191">The fourth command runs the `Get-Disk` command.</span></span> <span data-ttu-id="85c62-192">Hoewel de opdracht in de lokale sessie wordt getypt, wordt deze impliciet uitgevoerd op de externe computer van waaruit deze is geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="85c62-192">Although the command is typed in the local session, it runs implicitly on the remote computer from which it was imported.</span></span> <span data-ttu-id="85c62-193">De opdracht haalt objecten van de externe computer op en retourneert deze naar de lokale sessie.</span><span class="sxs-lookup"><span data-stu-id="85c62-193">The command gets objects from the remote computer and returns them to the local session.</span></span>

## <span data-ttu-id="85c62-194">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="85c62-194">PARAMETERS</span></span>

### <span data-ttu-id="85c62-195">-Alle</span><span class="sxs-lookup"><span data-stu-id="85c62-195">-All</span></span>

<span data-ttu-id="85c62-196">Geeft aan dat deze cmdlet alle modules in elke module map ophaalt, inclusief geneste modules, manifest bestanden (. psd1), script module bestanden (. psm1) en binaire module bestanden (. dll).</span><span class="sxs-lookup"><span data-stu-id="85c62-196">Indicates that this cmdlet gets all modules in each module folder, including nested modules, manifest (.psd1) files, script module (.psm1) files, and binary module (.dll) files.</span></span> <span data-ttu-id="85c62-197">Zonder deze para meter `Get-Module` wordt alleen de standaard module in elke module map opgehaald.</span><span class="sxs-lookup"><span data-stu-id="85c62-197">Without this parameter, `Get-Module` gets only the default module in each module folder.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Loaded, Available
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="85c62-198">-CimNamespace</span><span class="sxs-lookup"><span data-stu-id="85c62-198">-CimNamespace</span></span>

<span data-ttu-id="85c62-199">Hiermee geeft u de naam ruimte van een alternatieve CIM-provider die CIM-modules beschikbaar stelt.</span><span class="sxs-lookup"><span data-stu-id="85c62-199">Specifies the namespace of an alternate CIM provider that exposes CIM modules.</span></span> <span data-ttu-id="85c62-200">De standaard waarde is de naam ruimte van de WMI-provider van de module detectie.</span><span class="sxs-lookup"><span data-stu-id="85c62-200">The default value is the namespace of the Module Discovery WMI provider.</span></span>

<span data-ttu-id="85c62-201">Gebruik deze para meter om CIM-modules op te halen van computers en apparaten waarop het Windows-besturings systeem niet wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="85c62-201">Use this parameter to get CIM modules from computers and devices that are not running the Windows operating system.</span></span>

<span data-ttu-id="85c62-202">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="85c62-202">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: CimSession
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="85c62-203">-CimResourceUri</span><span class="sxs-lookup"><span data-stu-id="85c62-203">-CimResourceUri</span></span>

<span data-ttu-id="85c62-204">Hiermee geeft u een alternatieve locatie voor CIM-modules op.</span><span class="sxs-lookup"><span data-stu-id="85c62-204">Specifies an alternate location for CIM modules.</span></span> <span data-ttu-id="85c62-205">De standaard waarde is de resource-URI van de module detectie WMI-provider op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="85c62-205">The default value is the resource URI of the Module Discovery WMI provider on the remote computer.</span></span>

<span data-ttu-id="85c62-206">Gebruik deze para meter om CIM-modules op te halen van computers en apparaten waarop het Windows-besturings systeem niet wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="85c62-206">Use this parameter to get CIM modules from computers and devices that are not running the Windows operating system.</span></span>

<span data-ttu-id="85c62-207">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="85c62-207">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Uri
Parameter Sets: CimSession
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="85c62-208">-CimSession</span><span class="sxs-lookup"><span data-stu-id="85c62-208">-CimSession</span></span>

<span data-ttu-id="85c62-209">Hiermee geeft u een CIM-sessie op de externe computer op.</span><span class="sxs-lookup"><span data-stu-id="85c62-209">Specifies a CIM session on the remote computer.</span></span> <span data-ttu-id="85c62-210">Voer een variabele in die de CIM-sessie bevat of een opdracht waarmee de CIM-sessie wordt opgehaald, zoals een [Get-CimSession-](/powershell/module/cimcmdlets/get-cimsession) opdracht.</span><span class="sxs-lookup"><span data-stu-id="85c62-210">Enter a variable that contains the CIM session or a command that gets the CIM session, such as a [Get-CimSession](/powershell/module/cimcmdlets/get-cimsession) command.</span></span>

<span data-ttu-id="85c62-211">`Get-Module` maakt gebruik van de verbinding met de CIM-sessie om modules van de externe computer op te halen.</span><span class="sxs-lookup"><span data-stu-id="85c62-211">`Get-Module` uses the CIM session connection to get modules from the remote computer.</span></span> <span data-ttu-id="85c62-212">Wanneer u de module importeert met behulp `Import-Module` van de-cmdlet en de opdrachten uit de geïmporteerde module gebruikt in de huidige sessie, worden de opdrachten daad werkelijk uitgevoerd op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="85c62-212">When you import the module by using the `Import-Module` cmdlet and use the commands from the imported module in the current session, the commands actually run on the remote computer.</span></span>

<span data-ttu-id="85c62-213">U kunt deze para meter gebruiken om-modules op te halen van computers en apparaten waarop het Windows-besturings systeem niet wordt uitgevoerd, en computers met Power shell, maar externe communicatie van Power shell is niet ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="85c62-213">You can use this parameter to get modules from computers and devices that are not running the Windows operating system, and computers that have PowerShell, but do not have PowerShell remoting enabled.</span></span>

<span data-ttu-id="85c62-214">De para meter **CimSession** haalt alle modules op in de **CimSession**.</span><span class="sxs-lookup"><span data-stu-id="85c62-214">The **CimSession** parameter gets all modules in the **CIMSession**.</span></span> <span data-ttu-id="85c62-215">U kunt echter alleen op CIM gebaseerde en cmdlet definition XML-modules (CDXML) importeren.</span><span class="sxs-lookup"><span data-stu-id="85c62-215">However, you can import only CIM-based and Cmdlet Definition XML (CDXML)-based modules.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession
Parameter Sets: CimSession
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="85c62-216">-FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="85c62-216">-FullyQualifiedName</span></span>

<span data-ttu-id="85c62-217">Hiermee geeft u modules op met namen die zijn opgegeven in de vorm van **ModuleSpecification** -objecten.</span><span class="sxs-lookup"><span data-stu-id="85c62-217">Specifies modules with names that are specified in the form of **ModuleSpecification** objects.</span></span> <span data-ttu-id="85c62-218">Zie de sectie opmerkingen van de [ModuleSpecification-constructor (hashtabel)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span><span class="sxs-lookup"><span data-stu-id="85c62-218">See the Remarks section of [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span></span>

<span data-ttu-id="85c62-219">De para meter **FullyQualifiedModule** accepteert bijvoorbeeld een module naam die is opgegeven in een van de volgende indelingen:</span><span class="sxs-lookup"><span data-stu-id="85c62-219">For example, the **FullyQualifiedModule** parameter accepts a module name that is specified in either of these formats:</span></span>

- `@{ModuleName = "modulename"; ModuleVersion = "version_number"}`
- `@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}`

<span data-ttu-id="85c62-220">**Module** naam en **ModuleVersion** zijn vereist, maar **GUID** is optioneel.</span><span class="sxs-lookup"><span data-stu-id="85c62-220">**ModuleName** and **ModuleVersion** are required, but **Guid** is optional.</span></span> <span data-ttu-id="85c62-221">U kunt de para meter **FullyQualifiedModule** niet opgeven in dezelfde opdracht als een **module** parameter.</span><span class="sxs-lookup"><span data-stu-id="85c62-221">You cannot specify the **FullyQualifiedModule** parameter in the same command as a **Module** parameter.</span></span> <span data-ttu-id="85c62-222">de twee para meters sluiten elkaar wederzijds uit.</span><span class="sxs-lookup"><span data-stu-id="85c62-222">the two parameters are mutually exclusive.</span></span>

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

### <span data-ttu-id="85c62-223">-ListAvailable</span><span class="sxs-lookup"><span data-stu-id="85c62-223">-ListAvailable</span></span>

<span data-ttu-id="85c62-224">Geeft aan dat met deze cmdlet alle geïnstalleerde modules worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="85c62-224">Indicates that this cmdlet gets all installed modules.</span></span> <span data-ttu-id="85c62-225">`Get-Module` Hiermee worden modules opgehaald in paden die worden weer gegeven in de omgevings variabele **PSModulePath** .</span><span class="sxs-lookup"><span data-stu-id="85c62-225">`Get-Module` gets modules in paths listed in the **PSModulePath** environment variable.</span></span> <span data-ttu-id="85c62-226">Zonder deze para meter `Get-Module` worden alleen de modules opgehaald die beide zijn opgenomen in de omgevings variabele **PSModulePath** en die worden geladen in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="85c62-226">Without this parameter, `Get-Module` gets only the modules that are both listed in the **PSModulePath** environment variable, and that are loaded in the current session.</span></span> <span data-ttu-id="85c62-227">**ListAvailable** retourneert geen informatie over modules die niet zijn gevonden in de omgevings variabele **PSModulePath** , zelfs niet als deze modules in de huidige sessie worden geladen.</span><span class="sxs-lookup"><span data-stu-id="85c62-227">**ListAvailable** does not return information about modules that are not found in the **PSModulePath** environment variable, even if those modules are loaded in the current session.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Available, PsSession, CimSession
Aliases:

Required: True (Available), False (PsSession, CimSession)
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="85c62-228">-Name</span><span class="sxs-lookup"><span data-stu-id="85c62-228">-Name</span></span>

<span data-ttu-id="85c62-229">Hiermee worden namen of naam patronen van modules opgegeven die met deze cmdlet worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="85c62-229">Specifies names or name patterns of modules that this cmdlet gets.</span></span> <span data-ttu-id="85c62-230">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="85c62-230">Wildcard characters are permitted.</span></span> <span data-ttu-id="85c62-231">U kunt ook de namen door sluizen naar `Get-Module` .</span><span class="sxs-lookup"><span data-stu-id="85c62-231">You can also pipe the names to `Get-Module`.</span></span> <span data-ttu-id="85c62-232">U kunt de para meter **FullyQualifiedName** niet opgeven in dezelfde opdracht als de para meter **name** .</span><span class="sxs-lookup"><span data-stu-id="85c62-232">You cannot specify the **FullyQualifiedName** parameter in the same command as a **Name** parameter.</span></span>

<span data-ttu-id="85c62-233">De **naam** kan geen module-GUID als waarde accepteren.</span><span class="sxs-lookup"><span data-stu-id="85c62-233">**Name** cannot accept a module GUID as a value.</span></span>
<span data-ttu-id="85c62-234">Gebruik **FullyQualifiedName** in plaats daarvan om modules te retour neren door een GUID op te geven.</span><span class="sxs-lookup"><span data-stu-id="85c62-234">To return modules by specifying a GUID, use **FullyQualifiedName** instead.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="85c62-235">-PSEdition</span><span class="sxs-lookup"><span data-stu-id="85c62-235">-PSEdition</span></span>

<span data-ttu-id="85c62-236">Hiermee worden de modules opgehaald die de opgegeven editie van Power shell ondersteunen.</span><span class="sxs-lookup"><span data-stu-id="85c62-236">Gets the modules that support specified edition of PowerShell.</span></span>

<span data-ttu-id="85c62-237">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="85c62-237">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="85c62-238">Bureaublad</span><span class="sxs-lookup"><span data-stu-id="85c62-238">Desktop</span></span>
- <span data-ttu-id="85c62-239">Kern</span><span class="sxs-lookup"><span data-stu-id="85c62-239">Core</span></span>

<span data-ttu-id="85c62-240">De Get-Module-cmdlet controleert de eigenschap **CompatiblePSEditions** van het **PSModuleInfo** -object voor de opgegeven waarde en retourneert alleen de modules die het heeft ingesteld.</span><span class="sxs-lookup"><span data-stu-id="85c62-240">The Get-Module cmdlet checks **CompatiblePSEditions** property of **PSModuleInfo** object for the specified value and returns only those modules that have it set.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="85c62-241">**Desktop-editie:** deze editie is gebaseerd op .NET Framework en biedt compatibiliteit met scripts en modules die zijn gericht op versies van PowerShell die worden uitgevoerd op edities van Windows met een volledige footprint zoals Server Core en Windows Desktop.</span><span class="sxs-lookup"><span data-stu-id="85c62-241">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
> - <span data-ttu-id="85c62-242">**Core-editie:** deze editie is gebaseerd op .NET Framework en biedt compatibiliteit met scripts en modules die zijn gericht op versies van PowerShell die worden uitgevoerd op edities van Windows met een verminderde footprint zoals Nano Server en Windows IoT.</span><span class="sxs-lookup"><span data-stu-id="85c62-242">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

```yaml
Type: System.String
Parameter Sets: PsSession, Available
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="85c62-243">-PSSession</span><span class="sxs-lookup"><span data-stu-id="85c62-243">-PSSession</span></span>

<span data-ttu-id="85c62-244">Hiermee worden de modules in de opgegeven door de gebruiker beheerde Power shell-sessie (**PSSession**) opgehaald.</span><span class="sxs-lookup"><span data-stu-id="85c62-244">Gets the modules in the specified user-managed PowerShell session (**PSSession**).</span></span> <span data-ttu-id="85c62-245">Voer een variabele in die de sessie bevat, een opdracht waarmee de sessie wordt opgehaald, zoals een `Get-PSSession` opdracht of een opdracht waarmee de sessie wordt gemaakt, zoals een `New-PSSession` opdracht.</span><span class="sxs-lookup"><span data-stu-id="85c62-245">Enter a variable that contains the session, a command that gets the session, such as a `Get-PSSession` command, or a command that creates the session, such as a `New-PSSession` command.</span></span>

<span data-ttu-id="85c62-246">Wanneer de sessie is verbonden met een externe computer, moet u de para meter **ListAvailable** opgeven.</span><span class="sxs-lookup"><span data-stu-id="85c62-246">When the session is connected to a remote computer, you must specify the **ListAvailable** parameter.</span></span>

<span data-ttu-id="85c62-247">Een `Get-Module` opdracht die gebruikmaakt van de para meter **PSSession** is gelijk aan het gebruik van de `Invoke-Command` cmdlet om een `Get-Module -ListAvailable` opdracht uit te voeren in een **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="85c62-247">A `Get-Module` command that uses the **PSSession** parameter is equivalent to using the `Invoke-Command` cmdlet to run a `Get-Module -ListAvailable` command in a **PSSession**.</span></span>

<span data-ttu-id="85c62-248">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="85c62-248">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: PsSession
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="85c62-249">-Vernieuwen</span><span class="sxs-lookup"><span data-stu-id="85c62-249">-Refresh</span></span>

<span data-ttu-id="85c62-250">Geeft aan dat met deze cmdlet de cache van geïnstalleerde opdrachten wordt vernieuwd.</span><span class="sxs-lookup"><span data-stu-id="85c62-250">Indicates that this cmdlet refreshes the cache of installed commands.</span></span> <span data-ttu-id="85c62-251">De opdracht cache wordt gemaakt wanneer de sessie wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="85c62-251">The command cache is created when the session starts.</span></span> <span data-ttu-id="85c62-252">Hiermee kan de `Get-Command` cmdlet opdrachten ophalen uit modules die niet in de sessie zijn geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="85c62-252">It enables the `Get-Command` cmdlet to get commands from modules that are not imported into the session.</span></span>

<span data-ttu-id="85c62-253">Deze para meter is bedoeld voor ontwikkelings-en test scenario's waarin de inhoud van modules is gewijzigd sinds het starten van de sessie.</span><span class="sxs-lookup"><span data-stu-id="85c62-253">This parameter is designed for development and testing scenarios in which the contents of modules have changed since the session started.</span></span>

<span data-ttu-id="85c62-254">Wanneer u de **vernieuwings** parameter opgeeft in een opdracht, moet u **ListAvailable** opgeven.</span><span class="sxs-lookup"><span data-stu-id="85c62-254">When you specify the **Refresh** parameter in a command, you must specify **ListAvailable**.</span></span>

<span data-ttu-id="85c62-255">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="85c62-255">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Available, PsSession, CimSession
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="85c62-256">-SkipEditionCheck</span><span class="sxs-lookup"><span data-stu-id="85c62-256">-SkipEditionCheck</span></span>

<span data-ttu-id="85c62-257">De controle van het veld overs Laan `CompatiblePSEditions` .</span><span class="sxs-lookup"><span data-stu-id="85c62-257">Skips the check of the `CompatiblePSEditions` field.</span></span>

<span data-ttu-id="85c62-258">Get-Module worden standaard modules in de map wegge laten `%windir%\System32\WindowsPowerShell\v1.0\Modules` die niet `Core` in het veld zijn opgegeven `CompatiblePSEditions` .</span><span class="sxs-lookup"><span data-stu-id="85c62-258">By default, Get-Module will omit modules in the `%windir%\System32\WindowsPowerShell\v1.0\Modules` directory that do not specify `Core` in the `CompatiblePSEditions` field.</span></span> <span data-ttu-id="85c62-259">Als deze schakel optie is ingesteld, worden modules zonder `Core` opgenomen, zodat modules onder het pad van de Windows Power shell-module die incompatibel zijn met Power shell core, worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="85c62-259">When this switch is set, modules without `Core` will be included, so that modules under the Windows PowerShell module path that are incompatible with PowerShell Core will be returned.</span></span>

<span data-ttu-id="85c62-260">In macOS en Linux heeft deze para meter niets.</span><span class="sxs-lookup"><span data-stu-id="85c62-260">On macOS and Linux, this parameter does nothing.</span></span>

<span data-ttu-id="85c62-261">Zie [about_PowerShell_Editions](About/about_PowerShell_Editions.md) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="85c62-261">See [about_PowerShell_Editions](About/about_PowerShell_Editions.md) for more information.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Available, PsSession, CimSession
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="85c62-262">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="85c62-262">CommonParameters</span></span>

<span data-ttu-id="85c62-263">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="85c62-263">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="85c62-264">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="85c62-264">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="85c62-265">INVOER</span><span class="sxs-lookup"><span data-stu-id="85c62-265">INPUTS</span></span>

### <span data-ttu-id="85c62-266">System. String</span><span class="sxs-lookup"><span data-stu-id="85c62-266">System.String</span></span>

<span data-ttu-id="85c62-267">U kunt module namen door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="85c62-267">You can pipe module names to this cmdlet.</span></span>

## <span data-ttu-id="85c62-268">UITVOER</span><span class="sxs-lookup"><span data-stu-id="85c62-268">OUTPUTS</span></span>

### <span data-ttu-id="85c62-269">System. Management. Automation. PSModuleInfo</span><span class="sxs-lookup"><span data-stu-id="85c62-269">System.Management.Automation.PSModuleInfo</span></span>

<span data-ttu-id="85c62-270">Deze cmdlet retourneert objecten die modules vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="85c62-270">This cmdlet returns objects that represent modules.</span></span>
<span data-ttu-id="85c62-271">Wanneer u de para meter **ListAvailable** opgeeft, wordt `Get-Module` een **ModuleInfoGrouping** -object geretourneerd. Dit is een type **PSModuleInfo** -object met dezelfde eigenschappen en methoden.</span><span class="sxs-lookup"><span data-stu-id="85c62-271">When you specify the **ListAvailable** parameter, `Get-Module` returns a **ModuleInfoGrouping** object, which is a type of **PSModuleInfo** object that has the same properties and methods.</span></span>

## <span data-ttu-id="85c62-272">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="85c62-272">NOTES</span></span>

- <span data-ttu-id="85c62-273">Vanaf Windows Power Shell 3,0 worden de kern opdrachten die zijn opgenomen in Power shell, verpakt in modules.</span><span class="sxs-lookup"><span data-stu-id="85c62-273">Beginning in Windows PowerShell 3.0, the core commands that are included in PowerShell are packaged in modules.</span></span> <span data-ttu-id="85c62-274">De uitzonde ring is **micro soft. Power shell. core**, een module (**PSSnapin**).</span><span class="sxs-lookup"><span data-stu-id="85c62-274">The exception is **Microsoft.PowerShell.Core**, which is a snap-in (**PSSnapin**).</span></span> <span data-ttu-id="85c62-275">Standaard wordt alleen de module **micro soft. Power shell. core** toegevoegd aan de sessie.</span><span class="sxs-lookup"><span data-stu-id="85c62-275">By default, only the **Microsoft.PowerShell.Core** snap-in is added to the session.</span></span> <span data-ttu-id="85c62-276">Modules worden automatisch geïmporteerd bij het eerste gebruik en u kunt de `Import-Module` cmdlet gebruiken om ze te importeren.</span><span class="sxs-lookup"><span data-stu-id="85c62-276">Modules are imported automatically on first use and you can use the `Import-Module` cmdlet to import them.</span></span>

- <span data-ttu-id="85c62-277">In Windows Power Shell 2,0, en in hostgroepen die oudere sessies maken in latere versies van Power shell, worden de kern opdrachten verpakt in modules (**PSSnapins**).</span><span class="sxs-lookup"><span data-stu-id="85c62-277">In Windows PowerShell 2.0, and in host programs that create older-style sessions in later versions of PowerShell, the core commands are packaged in snap-ins (**PSSnapins**).</span></span> <span data-ttu-id="85c62-278">De uitzonde ring is **micro soft. Power shell. core**. Dit is altijd een module.</span><span class="sxs-lookup"><span data-stu-id="85c62-278">The exception is **Microsoft.PowerShell.Core**, which is always a snap-in.</span></span> <span data-ttu-id="85c62-279">Externe sessies, zoals computers die zijn gestart door de `New-PSSession` cmdlet, zijn ook oudere sessies met kern modules.</span><span class="sxs-lookup"><span data-stu-id="85c62-279">Also, remote sessions, such as those started by the `New-PSSession` cmdlet, are older-style sessions that include core snap-ins.</span></span>

  <span data-ttu-id="85c62-280">Zie de [methode CreateDefault2](/dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2)voor informatie over de **CreateDefault2** -methode waarmee nieuwe-stijl sessies met kern modules worden gemaakt.</span><span class="sxs-lookup"><span data-stu-id="85c62-280">For information about the **CreateDefault2** method that creates newer-style sessions with core modules, see [CreateDefault2 Method](/dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2).</span></span>

- <span data-ttu-id="85c62-281">`Get-Module` haalt alleen modules op in locaties die zijn opgeslagen in de waarde van de **PSModulePath** -omgevings variabele ($env:P smodulepath).</span><span class="sxs-lookup"><span data-stu-id="85c62-281">`Get-Module` only gets modules in locations that are stored in the value of the **PSModulePath** environment variable ($env:PSModulePath).</span></span> <span data-ttu-id="85c62-282">Met de `Import-Module` cmdlet kunnen modules op andere locaties worden geïmporteerd, maar u kunt de cmdlet niet gebruiken `Get-Module` om deze te downloaden.</span><span class="sxs-lookup"><span data-stu-id="85c62-282">The `Import-Module` cmdlet can import modules in other locations, but you cannot use the `Get-Module` cmdlet to get them.</span></span>

- <span data-ttu-id="85c62-283">Vanuit Power Shell 3,0 zijn er ook nieuwe eigenschappen toegevoegd aan het object, waardoor `Get-Module` het eenvoudiger wordt om te leren over modules, zelfs voordat ze worden geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="85c62-283">Also, starting in PowerShell 3.0, new properties have been added to the object that `Get-Module` returns that make it easier to learn about modules even before they are imported.</span></span> <span data-ttu-id="85c62-284">Alle eigenschappen worden ingevuld voordat ze worden geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="85c62-284">All properties are populated before importing.</span></span> <span data-ttu-id="85c62-285">Dit zijn onder andere de eigenschappen **ExportedCommands**, **ExportedCmdlets** en **ExportedFunctions** die de opdrachten vermeld die de module exporteert.</span><span class="sxs-lookup"><span data-stu-id="85c62-285">These include the **ExportedCommands**, **ExportedCmdlets** and **ExportedFunctions** properties that list the commands that the module exports.</span></span>

- <span data-ttu-id="85c62-286">De para meter **ListAvailable** haalt alleen goed opgemaakte modules op, dat wil zeggen mappen die ten minste één bestand bevatten waarvan de basis naam hetzelfde is als de naam van de module map.</span><span class="sxs-lookup"><span data-stu-id="85c62-286">The **ListAvailable** parameter gets only well-formed modules, that is, folders that contain at least one file whose base name is the same as the name of the module folder.</span></span> <span data-ttu-id="85c62-287">De basis naam is de naam zonder de bestandsnaam extensie.</span><span class="sxs-lookup"><span data-stu-id="85c62-287">The base name is the name without the file name extension.</span></span> <span data-ttu-id="85c62-288">Mappen met bestanden die verschillende namen hebben, worden beschouwd als containers, maar niet in modules.</span><span class="sxs-lookup"><span data-stu-id="85c62-288">Folders that contain files that have different names are considered to be containers, but not modules.</span></span>

  <span data-ttu-id="85c62-289">Als u modules wilt ophalen die als DLL-bestanden zijn geïmplementeerd, maar die niet zijn opgenomen in een module-map, geeft u zowel de **ListAvailable** als **alle** para meters op.</span><span class="sxs-lookup"><span data-stu-id="85c62-289">To get modules that are implemented as DLL files, but are not enclosed in a module folder, specify both the **ListAvailable** and **All** parameters.</span></span>

- <span data-ttu-id="85c62-290">Als u de functie CIM-sessie wilt gebruiken, moet de externe computer beschikken over WS-Management remoting en Windows Management Instrumentation (WMI), de micro soft-implementatie van de Common Information Model (CIM)-standaard.</span><span class="sxs-lookup"><span data-stu-id="85c62-290">To use the CIM session feature, the remote computer must have WS-Management remoting and Windows Management Instrumentation (WMI), which is the Microsoft implementation of the Common Information Model (CIM) standard.</span></span> <span data-ttu-id="85c62-291">De computer moet ook de WMI-provider voor module detectie hebben of een alternatieve WMI-provider die dezelfde basis functies heeft.</span><span class="sxs-lookup"><span data-stu-id="85c62-291">The computer must also have the Module Discovery WMI provider or an alternate WMI provider that has the same basic features.</span></span>

  <span data-ttu-id="85c62-292">U kunt de functie CIM-sessie gebruiken op computers waarop het Windows-besturings systeem niet wordt uitgevoerd en op Windows-computers met Power shell, maar externe communicatie van Power shell niet is ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="85c62-292">You can use the CIM session feature on computers that are not running the Windows operating system and on Windows computers that have PowerShell, but do not have PowerShell remoting enabled.</span></span>

  <span data-ttu-id="85c62-293">U kunt ook de CIM-para meters gebruiken om CIM-modules op te halen van computers waarop externe communicatie van Power shell is ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="85c62-293">You can also use the CIM parameters to get CIM modules from computers that have PowerShell remoting enabled.</span></span> <span data-ttu-id="85c62-294">Dit omvat de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="85c62-294">This includes the local computer.</span></span> <span data-ttu-id="85c62-295">Wanneer u een CIM-sessie op de lokale computer maakt, gebruikt Power shell DCOM in plaats van WMI om de sessie te maken.</span><span class="sxs-lookup"><span data-stu-id="85c62-295">When you create a CIM session on the local computer, PowerShell uses DCOM, instead of WMI, to create the session.</span></span>

## <span data-ttu-id="85c62-296">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="85c62-296">RELATED LINKS</span></span>

[<span data-ttu-id="85c62-297">Get-CimSession</span><span class="sxs-lookup"><span data-stu-id="85c62-297">Get-CimSession</span></span>](../CimCmdlets/Get-CimSession.md)

[<span data-ttu-id="85c62-298">New-CimSession</span><span class="sxs-lookup"><span data-stu-id="85c62-298">New-CimSession</span></span>](../CimCmdlets/New-CimSession.md)

[<span data-ttu-id="85c62-299">about_Modules</span><span class="sxs-lookup"><span data-stu-id="85c62-299">about_Modules</span></span>](About/about_Modules.md)

[<span data-ttu-id="85c62-300">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="85c62-300">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="85c62-301">Import-module</span><span class="sxs-lookup"><span data-stu-id="85c62-301">Import-Module</span></span>](Import-Module.md)

[<span data-ttu-id="85c62-302">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="85c62-302">Import-PSSession</span></span>](../Microsoft.PowerShell.Utility/Import-PSSession.md)

[<span data-ttu-id="85c62-303">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="85c62-303">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="85c62-304">Remove-module</span><span class="sxs-lookup"><span data-stu-id="85c62-304">Remove-Module</span></span>](Remove-Module.md)

[<span data-ttu-id="85c62-305">about_PowerShell_Editions</span><span class="sxs-lookup"><span data-stu-id="85c62-305">about_PowerShell_Editions</span></span>](About/about_PowerShell_Editions.md)
