---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 5/15/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-module?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Module
ms.openlocfilehash: 4098b40c01085b266fa279107e5795b1283705cd
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93249958"
---
# <span data-ttu-id="be40d-103">Get-Module</span><span class="sxs-lookup"><span data-stu-id="be40d-103">Get-Module</span></span>

## <span data-ttu-id="be40d-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="be40d-104">SYNOPSIS</span></span>
<span data-ttu-id="be40d-105">Hiermee worden de modules opgehaald die zijn geïmporteerd of die in de huidige sessie kunnen worden geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="be40d-105">Gets the modules that have been imported or that can be imported into the current session.</span></span>

## <span data-ttu-id="be40d-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="be40d-106">SYNTAX</span></span>

### <span data-ttu-id="be40d-107">Geladen (standaard)</span><span class="sxs-lookup"><span data-stu-id="be40d-107">Loaded (Default)</span></span>

```
Get-Module [[-Name] <String[]>] [-FullyQualifiedName <ModuleSpecification[]>] [-All] [<CommonParameters>]
```

### <span data-ttu-id="be40d-108">Beschikbaar</span><span class="sxs-lookup"><span data-stu-id="be40d-108">Available</span></span>

```
Get-Module [[-Name] <String[]>] [-FullyQualifiedName <ModuleSpecification[]>] [-All] [-ListAvailable]
 [-PSEdition <String>] [-Refresh] [<CommonParameters>]
```

### <span data-ttu-id="be40d-109">PsSession</span><span class="sxs-lookup"><span data-stu-id="be40d-109">PsSession</span></span>

```
Get-Module [[-Name] <String[]>] [-FullyQualifiedName <ModuleSpecification[]>] [-ListAvailable]
 [-PSEdition <String>] [-Refresh] -PSSession <PSSession> [<CommonParameters>]
```

### <span data-ttu-id="be40d-110">CimSession</span><span class="sxs-lookup"><span data-stu-id="be40d-110">CimSession</span></span>

```
Get-Module [[-Name] <String[]>] [-FullyQualifiedName <ModuleSpecification[]>] [-ListAvailable] [-Refresh]
 -CimSession <CimSession> [-CimResourceUri <Uri>] [-CimNamespace <String>] [<CommonParameters>]
```

## <span data-ttu-id="be40d-111">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="be40d-111">DESCRIPTION</span></span>

<span data-ttu-id="be40d-112">De `Get-Module` cmdlet haalt de Power shell-modules die zijn geïmporteerd of die kunnen worden geïmporteerd, op in een Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="be40d-112">The `Get-Module` cmdlet gets the PowerShell modules that have been imported, or that can be imported, into a PowerShell session.</span></span>
<span data-ttu-id="be40d-113">Het module-object dat `Get-Module` retourneert, bevat waardevolle informatie over de module.</span><span class="sxs-lookup"><span data-stu-id="be40d-113">The module object that `Get-Module` returns contains valuable information about the module.</span></span>
<span data-ttu-id="be40d-114">U kunt de module-objecten ook door sluizen naar andere cmdlets, zoals de- `Import-Module` en- `Remove-Module` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="be40d-114">You can also pipe the module objects to other cmdlets, such as the `Import-Module` and `Remove-Module` cmdlets.</span></span>

<span data-ttu-id="be40d-115">Zonder para meters worden `Get-Module` modules opgehaald die in de huidige sessie zijn geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="be40d-115">Without parameters, `Get-Module` gets modules that have been imported into the current session.</span></span>
<span data-ttu-id="be40d-116">Geef de para meter **ListAvailable** op om alle geïnstalleerde modules op te halen.</span><span class="sxs-lookup"><span data-stu-id="be40d-116">To get all installed modules, specify the **ListAvailable** parameter.</span></span>

<span data-ttu-id="be40d-117">`Get-Module` Hiermee worden modules opgehaald, maar niet geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="be40d-117">`Get-Module` gets modules, but it does not import them.</span></span>
<span data-ttu-id="be40d-118">Vanaf Windows Power Shell 3,0 worden modules automatisch geïmporteerd wanneer u een opdracht in de module gebruikt, maar met een `Get-Module` opdracht wordt een automatische import bewerking niet geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="be40d-118">Starting in Windows PowerShell 3.0, modules are automatically imported when you use a command in the module, but a `Get-Module` command does not trigger an automatic import.</span></span>
<span data-ttu-id="be40d-119">U kunt de modules ook importeren in uw-sessie met behulp van de- `Import-Module` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="be40d-119">You can also import the modules into your session by using the `Import-Module` cmdlet.</span></span>

<span data-ttu-id="be40d-120">Vanaf Windows Power Shell 3,0 kunt u modules ophalen en vervolgens importeren van externe sessies in de lokale sessie.</span><span class="sxs-lookup"><span data-stu-id="be40d-120">Starting in Windows PowerShell 3.0, you can get and then, import modules from remote sessions into the local session.</span></span>
<span data-ttu-id="be40d-121">Deze strategie maakt gebruik van de impliciete externe functie van Power shell en komt overeen met het gebruik van de `Import-PSSession` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="be40d-121">This strategy uses the Implicit Remoting feature of PowerShell and is equivalent to using the `Import-PSSession` cmdlet.</span></span>
<span data-ttu-id="be40d-122">Wanneer u opdrachten gebruikt in modules die vanuit een andere sessie worden geïmporteerd, worden de opdrachten impliciet uitgevoerd in de externe sessie.</span><span class="sxs-lookup"><span data-stu-id="be40d-122">When you use commands in modules imported from another session, the commands run implicitly in the remote session.</span></span> <span data-ttu-id="be40d-123">Met deze functie kunt u de externe computer vanuit de lokale sessie beheren.</span><span class="sxs-lookup"><span data-stu-id="be40d-123">This feature lets you manage the remote computer from the local session.</span></span>

<span data-ttu-id="be40d-124">Met ingang van Windows Power Shell 3,0 kunt u ook `Get-Module` `Import-Module` de modules van Common Information Model (CIM) gebruiken en weer geven, waarin de cmdlets worden gedefinieerd in de CMDLET definition XML-bestanden (CDXML).</span><span class="sxs-lookup"><span data-stu-id="be40d-124">Also, starting in Windows PowerShell 3.0, you can use `Get-Module` and `Import-Module` to get and import Common Information Model (CIM) modules, in which the cmdlets are defined in Cmdlet Definition XML (CDXML) files.</span></span>
<span data-ttu-id="be40d-125">Met deze functie kunt u cmdlets gebruiken die zijn geïmplementeerd in niet-beheerde code-assembly's, zoals die zijn geschreven in C++.</span><span class="sxs-lookup"><span data-stu-id="be40d-125">This feature lets you use cmdlets that are implemented in non-managed code assemblies, such as those written in C++.</span></span>

<span data-ttu-id="be40d-126">Met deze nieuwe functies worden de- `Get-Module` en- `Import-Module` cmdlets primaire hulp middelen voor het beheren van heterogene ondernemingen die computers bevatten waarop het Windows-besturings systeem wordt uitgevoerd en computers met andere besturings systemen.</span><span class="sxs-lookup"><span data-stu-id="be40d-126">With these new features, the `Get-Module` and `Import-Module` cmdlets become primary tools for managing heterogeneous enterprises that include computers that run the Windows operating system and computers that run other operating systems.</span></span>

<span data-ttu-id="be40d-127">Als u externe computers wilt beheren waarop het Windows-besturings systeem wordt uitgevoerd en externe communicatie van Power shell is ingeschakeld, maakt u een **PSSession** op de externe computer en gebruikt u vervolgens de para meter **PSSession** van `Get-Module` om de Power shell-modules op te halen in de **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="be40d-127">To manage remote computers that run the Windows operating system that have PowerShell and PowerShell remoting enabled, create a **PSSession** on the remote computer and then use the **PSSession** parameter of `Get-Module` to get the PowerShell modules in the **PSSession**.</span></span>
<span data-ttu-id="be40d-128">Wanneer u de modules importeert en vervolgens de geïmporteerde opdrachten in de huidige sessie gebruikt, worden de opdrachten impliciet uitgevoerd in de **PSSession** op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="be40d-128">When you import the modules, and then use the imported commands in the current session, the commands run implicitly in the **PSSession** on the remote computer.</span></span>
<span data-ttu-id="be40d-129">U kunt deze strategie gebruiken om de externe computer te beheren.</span><span class="sxs-lookup"><span data-stu-id="be40d-129">You can use this strategy to manage the remote computer.</span></span>

<span data-ttu-id="be40d-130">U kunt een vergelijk bare strategie gebruiken voor het beheren van computers waarop geen externe communicatie van Power shell is ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="be40d-130">You can use a similar strategy to manage computers that do not have PowerShell remoting enabled.</span></span>
<span data-ttu-id="be40d-131">Dit zijn onder andere computers waarop het Windows-besturings systeem niet wordt uitgevoerd en computers met Power shell, maar waarvoor geen externe communicatie van Power shell is ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="be40d-131">These include computers that are not running the Windows operating system, and computers that have PowerShell but do not have PowerShell remoting enabled.</span></span>

<span data-ttu-id="be40d-132">Maak eerst een CIM-sessie op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="be40d-132">Start by creating a CIM session on the remote computer.</span></span>
<span data-ttu-id="be40d-133">Een CIM-sessie is een verbinding met Windows Management Instrumentation (WMI) op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="be40d-133">A CIM session is a connection to Windows Management Instrumentation (WMI) on the remote computer.</span></span>
<span data-ttu-id="be40d-134">Gebruik vervolgens de para meter **CIMSession** van `Get-Module` om CIM-modules op te halen uit de CIM-sessie.</span><span class="sxs-lookup"><span data-stu-id="be40d-134">Then use the **CIMSession** parameter of `Get-Module` to get CIM modules from the CIM session.</span></span>
<span data-ttu-id="be40d-135">Wanneer u een CIM-module importeert met behulp van de- `Import-Module` cmdlet en vervolgens de geïmporteerde opdrachten uitvoert, worden de opdrachten impliciet uitgevoerd op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="be40d-135">When you import a CIM module by using the `Import-Module` cmdlet and then run the imported commands, the commands run implicitly on the remote computer.</span></span>
<span data-ttu-id="be40d-136">U kunt deze WMI-en CIM-strategie gebruiken om de externe computer te beheren.</span><span class="sxs-lookup"><span data-stu-id="be40d-136">You can use this WMI and CIM strategy to manage the remote computer.</span></span>

## <span data-ttu-id="be40d-137">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="be40d-137">EXAMPLES</span></span>

### <span data-ttu-id="be40d-138">Voor beeld 1: modules ophalen die in de huidige sessie zijn geïmporteerd</span><span class="sxs-lookup"><span data-stu-id="be40d-138">Example 1: Get modules imported into the current session</span></span>

```powershell
Get-Module
```

<span data-ttu-id="be40d-139">Met deze opdracht worden modules opgehaald die in de huidige sessie zijn geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="be40d-139">This command gets modules that have been imported into the current session.</span></span>

### <span data-ttu-id="be40d-140">Voor beeld 2: geïnstalleerde modules en beschik bare modules ophalen</span><span class="sxs-lookup"><span data-stu-id="be40d-140">Example 2: Get installed modules and available modules</span></span>

```powershell
Get-Module -ListAvailable
```

<span data-ttu-id="be40d-141">Met deze opdracht worden de modules opgehaald die op de computer zijn geïnstalleerd en die in de huidige sessie kunnen worden geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="be40d-141">This command gets the modules that are installed on the computer and can be imported into the current session.</span></span>

<span data-ttu-id="be40d-142">`Get-Module` zoekt naar beschik bare modules in het pad dat is opgegeven door de omgevings variabele **$env:P smodulepath** .</span><span class="sxs-lookup"><span data-stu-id="be40d-142">`Get-Module` looks for available modules in the path specified by the **$env:PSModulePath** environment variable.</span></span>
<span data-ttu-id="be40d-143">Zie [about_Modules](About/about_Modules.md) en [about_Environment_Variables](About/about_Environment_Variables.md)voor meer informatie over **PSModulePath**.</span><span class="sxs-lookup"><span data-stu-id="be40d-143">For more information about **PSModulePath** , see [about_Modules](About/about_Modules.md) and [about_Environment_Variables](About/about_Environment_Variables.md).</span></span>

### <span data-ttu-id="be40d-144">Voor beeld 3: alle geëxporteerde bestanden ophalen</span><span class="sxs-lookup"><span data-stu-id="be40d-144">Example 3: Get all exported files</span></span>

```powershell
Get-Module -ListAvailable -All
```

<span data-ttu-id="be40d-145">Met deze opdracht worden alle geëxporteerde bestanden voor alle beschik bare modules opgehaald.</span><span class="sxs-lookup"><span data-stu-id="be40d-145">This command gets all of the exported files for all available modules.</span></span>

### <span data-ttu-id="be40d-146">Voor beeld 4: een module ophalen met de volledig gekwalificeerde naam</span><span class="sxs-lookup"><span data-stu-id="be40d-146">Example 4: Get a module by its fully qualified name</span></span>

```powershell
$FullyQualifedName = @{ModuleName="Microsoft.PowerShell.Management";ModuleVersion="3.1.0.0"}
Get-Module -FullyQualifiedName $FullyQualifedName | Format-Table -Property Name,Version
```

```Output
Name                             Version
----                             -------
Microsoft.PowerShell.Management  3.1.0.0
```

<span data-ttu-id="be40d-147">Met deze opdracht wordt de module **micro soft. Power shell. Management** opgehaald door de volledig gekwalificeerde naam van de module op te geven met behulp van de para meter **FullyQualifiedName** .</span><span class="sxs-lookup"><span data-stu-id="be40d-147">This command gets the **Microsoft.PowerShell.Management** module by specifying the fully qualified name of the module by using the **FullyQualifiedName** parameter.</span></span>
<span data-ttu-id="be40d-148">De opdracht Pipet de resultaten vervolgens `Format-Table` naar de cmdlet om de resultaten op te maken als een tabel met de **naam** en **versie** als kolom koppen.</span><span class="sxs-lookup"><span data-stu-id="be40d-148">The command then pipes the results into the `Format-Table` cmdlet to format the results as a table with **Name** and **Version** as the column headings.</span></span>

### <span data-ttu-id="be40d-149">Voor beeld 5: eigenschappen van een module ophalen</span><span class="sxs-lookup"><span data-stu-id="be40d-149">Example 5: Get properties of a module</span></span>

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

<span data-ttu-id="be40d-150">Met deze opdracht worden de eigenschappen opgehaald van het **PSModuleInfo** -object dat `Get-Module` retourneert.</span><span class="sxs-lookup"><span data-stu-id="be40d-150">This command gets the properties of the **PSModuleInfo** object that `Get-Module` returns.</span></span>
<span data-ttu-id="be40d-151">Er is één object voor elk module bestand.</span><span class="sxs-lookup"><span data-stu-id="be40d-151">There is one object for each module file.</span></span>

<span data-ttu-id="be40d-152">U kunt de eigenschappen gebruiken om de module-objecten te Format teren en te filteren.</span><span class="sxs-lookup"><span data-stu-id="be40d-152">You can use the properties to format and filter the module objects.</span></span>
<span data-ttu-id="be40d-153">Zie [PSModuleInfo Properties](/dotnet/api/system.management.automation.psmoduleinfo)(Engelstalig) voor meer informatie over de eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="be40d-153">For more information about the properties, see [PSModuleInfo Properties](/dotnet/api/system.management.automation.psmoduleinfo).</span></span>

<span data-ttu-id="be40d-154">De uitvoer bevat de nieuwe eigenschappen, zoals **Auteur** en **CompanyName** , die zijn geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="be40d-154">The output includes the new properties, such as **Author** and **CompanyName** , that were introduced in Windows PowerShell 3.0.</span></span>

### <span data-ttu-id="be40d-155">Voor beeld 6: alle modules op naam groeperen</span><span class="sxs-lookup"><span data-stu-id="be40d-155">Example 6: Group all modules by name</span></span>

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

<span data-ttu-id="be40d-156">Met deze opdracht worden alle module bestanden, zowel geïmporteerd als beschikbaar, opgehaald en vervolgens gegroepeerd op module naam.</span><span class="sxs-lookup"><span data-stu-id="be40d-156">This command gets all module files, both imported and available, and then groups them by module name.</span></span> <span data-ttu-id="be40d-157">Zo kunt u de module bestanden zien die elk script exporteert.</span><span class="sxs-lookup"><span data-stu-id="be40d-157">This lets you see the module files that each script is exporting.</span></span>

### <span data-ttu-id="be40d-158">Voor beeld 7: de inhoud van een module manifest weer geven</span><span class="sxs-lookup"><span data-stu-id="be40d-158">Example 7: Display the contents of a module manifest</span></span>

<span data-ttu-id="be40d-159">Met deze opdrachten wordt de inhoud van het module manifest voor de Windows Power shell **BitsTransfer** -module weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="be40d-159">These commands display the contents of the module manifest for the Windows PowerShell **BitsTransfer** module.</span></span>

<span data-ttu-id="be40d-160">Modules hoeven geen manifest bestanden te bevatten.</span><span class="sxs-lookup"><span data-stu-id="be40d-160">Modules are not required to have manifest files.</span></span>
<span data-ttu-id="be40d-161">Wanneer ze een manifest bestand hebben, is het manifest bestand alleen vereist voor het toevoegen van een versie nummer.</span><span class="sxs-lookup"><span data-stu-id="be40d-161">When they do have a manifest file, the manifest file is required only to include a version number.</span></span>
<span data-ttu-id="be40d-162">Manifest bestanden bevatten echter vaak nuttige informatie over een module, de vereisten en de inhoud ervan.</span><span class="sxs-lookup"><span data-stu-id="be40d-162">However, manifest files often provide useful information about a module, its requirements, and its contents.</span></span>

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

<span data-ttu-id="be40d-163">Met de eerste opdracht wordt het PSModuleInfo-object opgehaald dat de BitsTransfer-module vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="be40d-163">The first command gets the PSModuleInfo object that represents BitsTransfer module.</span></span> <span data-ttu-id="be40d-164">Hiermee wordt het object in de `$m` variabele opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="be40d-164">It saves the object in the `$m` variable.</span></span>

<span data-ttu-id="be40d-165">Met de tweede opdracht wordt de `Get-Content` cmdlet gebruikt om de inhoud van het manifest bestand in het opgegeven pad op te halen.</span><span class="sxs-lookup"><span data-stu-id="be40d-165">The second command uses the `Get-Content` cmdlet to get the content of the manifest file in the specified path.</span></span> <span data-ttu-id="be40d-166">De teken punt notatie wordt gebruikt om het pad naar het manifest bestand op te halen dat is opgeslagen in de eigenschap Path van het object.</span><span class="sxs-lookup"><span data-stu-id="be40d-166">It uses dot notation to get the path to the manifest file, which is stored in the Path property of the object.</span></span> <span data-ttu-id="be40d-167">De uitvoer toont de inhoud van het module manifest.</span><span class="sxs-lookup"><span data-stu-id="be40d-167">The output shows the contents of the module manifest.</span></span>

### <span data-ttu-id="be40d-168">Voor beeld 8: bestanden in de module directory weer geven</span><span class="sxs-lookup"><span data-stu-id="be40d-168">Example 8: List files in module directory</span></span>

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

<span data-ttu-id="be40d-169">Met deze opdracht worden de bestanden in de map van de module weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="be40d-169">This command lists the files in the directory of the module.</span></span>
<span data-ttu-id="be40d-170">Dit is een andere manier om te bepalen wat zich in een module bevindt voordat u deze importeert.</span><span class="sxs-lookup"><span data-stu-id="be40d-170">This is another way to determine what is in a module before you import it.</span></span>
<span data-ttu-id="be40d-171">Sommige modules hebben mogelijk Help-bestanden of leesmij-bestanden waarin de module wordt beschreven.</span><span class="sxs-lookup"><span data-stu-id="be40d-171">Some modules might have help files or ReadMe files that describe the module.</span></span>

### <span data-ttu-id="be40d-172">Voor beeld 9: modules ophalen die op een computer zijn geïnstalleerd</span><span class="sxs-lookup"><span data-stu-id="be40d-172">Example 9: Get modules installed on a computer</span></span>

```powershell
$s = New-PSSession -ComputerName Server01

Get-Module -PSSession $s -ListAvailable
```

<span data-ttu-id="be40d-173">Met deze opdrachten worden de modules opgehaald die zijn geïnstalleerd op de Server01-computer.</span><span class="sxs-lookup"><span data-stu-id="be40d-173">These commands get the modules that are installed on the Server01 computer.</span></span>

<span data-ttu-id="be40d-174">De eerste opdracht gebruikt de `New-PSSession` cmdlet om een **PSSession** te maken op de Server01-computer.</span><span class="sxs-lookup"><span data-stu-id="be40d-174">The first command uses the `New-PSSession` cmdlet to create a **PSSession** on the Server01 computer.</span></span> <span data-ttu-id="be40d-175">Met de opdracht slaat u de **PSSession** op in de variabele $s.</span><span class="sxs-lookup"><span data-stu-id="be40d-175">The command saves the **PSSession** in the $s variable.</span></span>

<span data-ttu-id="be40d-176">De tweede opdracht maakt gebruik van de **PSSession** -en **ListAvailable** -para meters van `Get-Module` om de modules in de **PSSession** te verkrijgen in de variabele $s.</span><span class="sxs-lookup"><span data-stu-id="be40d-176">The second command uses the **PSSession** and **ListAvailable** parameters of `Get-Module` to get the modules in the **PSSession** in the $s variable.</span></span>

<span data-ttu-id="be40d-177">Als u modules van andere sessies naar de cmdlet pipet `Import-Module` , `Import-Module` importeert de module in de huidige sessie met behulp van de functie impliciete externe toegang.</span><span class="sxs-lookup"><span data-stu-id="be40d-177">If you pipe modules from other sessions to the `Import-Module` cmdlet, `Import-Module` imports the module into the current session by using the implicit remoting feature.</span></span>
<span data-ttu-id="be40d-178">Dit is gelijk aan het gebruik van de `Import-PSSession` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="be40d-178">This is equivalent to using the `Import-PSSession` cmdlet.</span></span>
<span data-ttu-id="be40d-179">U kunt de-cmdlets uit de module in de huidige sessie gebruiken, maar met opdrachten die gebruikmaken van deze cmdlets wordt de externe sessie daad werkelijk uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="be40d-179">You can use the cmdlets from the module in the current session, but commands that use these cmdlets actually run the remote session.</span></span>
<span data-ttu-id="be40d-180">Zie en voor meer informatie [`Import-Module`](Import-Module.md) [`Import-PSSession`](../Microsoft.PowerShell.Utility/Import-PSSession.md) .</span><span class="sxs-lookup"><span data-stu-id="be40d-180">For more information, see [`Import-Module`](Import-Module.md) and [`Import-PSSession`](../Microsoft.PowerShell.Utility/Import-PSSession.md).</span></span>

### <span data-ttu-id="be40d-181">Voor beeld 10: een computer beheren waarop het Windows-besturings systeem niet wordt uitgevoerd</span><span class="sxs-lookup"><span data-stu-id="be40d-181">Example 10: Manage a computer that does not run the Windows operating system</span></span>

<span data-ttu-id="be40d-182">Met de opdrachten in dit voor beeld kunt u de opslag systemen beheren van een externe computer waarop het Windows-besturings systeem niet wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="be40d-182">The commands in this example enable you to manage the storage systems of a remote computer that is not running the Windows operating system.</span></span>
<span data-ttu-id="be40d-183">In dit voor beeld, omdat de beheerder van de computer de WMI-provider voor module detectie heeft geïnstalleerd, kunnen de CIM-opdrachten de standaard waarden gebruiken die zijn ontworpen voor de provider.</span><span class="sxs-lookup"><span data-stu-id="be40d-183">In this example, because the administrator of the computer has installed the Module Discovery WMI provider, the CIM commands can use the default values, which are designed for the provider.</span></span>

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

<span data-ttu-id="be40d-184">De eerste opdracht gebruikt de `New-CimSession` cmdlet om een sessie te maken op de externe computer RSDGF03.</span><span class="sxs-lookup"><span data-stu-id="be40d-184">The first command uses the `New-CimSession` cmdlet to create a session on the RSDGF03 remote computer.</span></span> <span data-ttu-id="be40d-185">De sessie maakt verbinding met WMI op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="be40d-185">The session connects to WMI on the remote computer.</span></span> <span data-ttu-id="be40d-186">Met de opdracht wordt de CIM-sessie in de `$cs` variabele opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="be40d-186">The command saves the CIM session in the `$cs` variable.</span></span>

<span data-ttu-id="be40d-187">Met de tweede opdracht wordt de CIM-sessie in de `$cs` variabele gebruikt om een opdracht uit te voeren `Get-Module` op de RSDGF03-computer.</span><span class="sxs-lookup"><span data-stu-id="be40d-187">The second command uses the CIM session in the `$cs` variable to run a `Get-Module` command on the RSDGF03 computer.</span></span> <span data-ttu-id="be40d-188">De opdracht gebruikt de para meter name om de opslag module op te geven.</span><span class="sxs-lookup"><span data-stu-id="be40d-188">The command uses the Name parameter to specify the Storage module.</span></span> <span data-ttu-id="be40d-189">De opdracht maakt gebruik van een pijplijn operator (|) voor het verzenden van de opslag module naar de `Import-Module` cmdlet, die deze in de lokale sessie importeert.</span><span class="sxs-lookup"><span data-stu-id="be40d-189">The command uses a pipeline operator (|) to send the Storage module to the `Import-Module` cmdlet, which imports it into the local session.</span></span>

<span data-ttu-id="be40d-190">Met de derde opdracht voert u de `Get-Command` cmdlet `Get-Disk` uit op de opdracht in de module opslag.</span><span class="sxs-lookup"><span data-stu-id="be40d-190">The third command runs the `Get-Command` cmdlet on the `Get-Disk` command in the Storage module.</span></span>
<span data-ttu-id="be40d-191">Wanneer u een CIM-module in de lokale sessie importeert, worden de CDXML-bestanden die de CIM-module vertegenwoordigen, omgezet in Power shell-scripts, die als functies in de lokale sessie worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="be40d-191">When you import a CIM module into the local session, PowerShell converts the CDXML files that represent the CIM module into PowerShell scripts, which appear as functions in the local session.</span></span>

<span data-ttu-id="be40d-192">Met de vierde opdracht voert u de `Get-Disk` opdracht uit.</span><span class="sxs-lookup"><span data-stu-id="be40d-192">The fourth command runs the `Get-Disk` command.</span></span> <span data-ttu-id="be40d-193">Hoewel de opdracht in de lokale sessie wordt getypt, wordt deze impliciet uitgevoerd op de externe computer van waaruit deze is geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="be40d-193">Although the command is typed in the local session, it runs implicitly on the remote computer from which it was imported.</span></span> <span data-ttu-id="be40d-194">De opdracht haalt objecten van de externe computer op en retourneert deze naar de lokale sessie.</span><span class="sxs-lookup"><span data-stu-id="be40d-194">The command gets objects from the remote computer and returns them to the local session.</span></span>

## <span data-ttu-id="be40d-195">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="be40d-195">PARAMETERS</span></span>

### <span data-ttu-id="be40d-196">-Alle</span><span class="sxs-lookup"><span data-stu-id="be40d-196">-All</span></span>

<span data-ttu-id="be40d-197">Geeft aan dat deze cmdlet alle modules in elke module map ophaalt, inclusief geneste modules, manifest bestanden (. psd1), script module bestanden (. psm1) en binaire module bestanden (. dll).</span><span class="sxs-lookup"><span data-stu-id="be40d-197">Indicates that this cmdlet gets all modules in each module folder, including nested modules, manifest (.psd1) files, script module (.psm1) files, and binary module (.dll) files.</span></span>
<span data-ttu-id="be40d-198">Zonder deze para meter `Get-Module` wordt alleen de standaard module in elke module map opgehaald.</span><span class="sxs-lookup"><span data-stu-id="be40d-198">Without this parameter, `Get-Module` gets only the default module in each module folder.</span></span>

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

### <span data-ttu-id="be40d-199">-CimNamespace</span><span class="sxs-lookup"><span data-stu-id="be40d-199">-CimNamespace</span></span>

<span data-ttu-id="be40d-200">Hiermee geeft u de naam ruimte van een alternatieve CIM-provider die CIM-modules beschikbaar stelt.</span><span class="sxs-lookup"><span data-stu-id="be40d-200">Specifies the namespace of an alternate CIM provider that exposes CIM modules.</span></span>
<span data-ttu-id="be40d-201">De standaard waarde is de naam ruimte van de WMI-provider van de module detectie.</span><span class="sxs-lookup"><span data-stu-id="be40d-201">The default value is the namespace of the Module Discovery WMI provider.</span></span>

<span data-ttu-id="be40d-202">Gebruik deze para meter om CIM-modules op te halen van computers en apparaten waarop het Windows-besturings systeem niet wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="be40d-202">Use this parameter to get CIM modules from computers and devices that are not running the Windows operating system.</span></span>

<span data-ttu-id="be40d-203">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="be40d-203">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="be40d-204">-CimResourceUri</span><span class="sxs-lookup"><span data-stu-id="be40d-204">-CimResourceUri</span></span>

<span data-ttu-id="be40d-205">Hiermee geeft u een alternatieve locatie voor CIM-modules op.</span><span class="sxs-lookup"><span data-stu-id="be40d-205">Specifies an alternate location for CIM modules.</span></span>
<span data-ttu-id="be40d-206">De standaard waarde is de resource-URI van de module detectie WMI-provider op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="be40d-206">The default value is the resource URI of the Module Discovery WMI provider on the remote computer.</span></span>

<span data-ttu-id="be40d-207">Gebruik deze para meter om CIM-modules op te halen van computers en apparaten waarop het Windows-besturings systeem niet wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="be40d-207">Use this parameter to get CIM modules from computers and devices that are not running the Windows operating system.</span></span>

<span data-ttu-id="be40d-208">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="be40d-208">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="be40d-209">-CimSession</span><span class="sxs-lookup"><span data-stu-id="be40d-209">-CimSession</span></span>

<span data-ttu-id="be40d-210">Hiermee geeft u een CIM-sessie op de externe computer op.</span><span class="sxs-lookup"><span data-stu-id="be40d-210">Specifies a CIM session on the remote computer.</span></span>
<span data-ttu-id="be40d-211">Voer een variabele in die de CIM-sessie bevat of een opdracht waarmee de CIM-sessie wordt opgehaald, zoals een [Get-CimSession-](/powershell/module/cimcmdlets/get-cimsession) opdracht.</span><span class="sxs-lookup"><span data-stu-id="be40d-211">Enter a variable that contains the CIM session or a command that gets the CIM session, such as a [Get-CimSession](/powershell/module/cimcmdlets/get-cimsession) command.</span></span>

<span data-ttu-id="be40d-212">`Get-Module` maakt gebruik van de verbinding met de CIM-sessie om modules van de externe computer op te halen.</span><span class="sxs-lookup"><span data-stu-id="be40d-212">`Get-Module` uses the CIM session connection to get modules from the remote computer.</span></span>
<span data-ttu-id="be40d-213">Wanneer u de module importeert met behulp `Import-Module` van de-cmdlet en de opdrachten uit de geïmporteerde module gebruikt in de huidige sessie, worden de opdrachten daad werkelijk uitgevoerd op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="be40d-213">When you import the module by using the `Import-Module` cmdlet and use the commands from the imported module in the current session, the commands actually run on the remote computer.</span></span>

<span data-ttu-id="be40d-214">U kunt deze para meter gebruiken om-modules op te halen van computers en apparaten waarop het Windows-besturings systeem niet wordt uitgevoerd, en computers met Power shell, maar externe communicatie van Power shell is niet ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="be40d-214">You can use this parameter to get modules from computers and devices that are not running the Windows operating system, and computers that have PowerShell, but do not have PowerShell remoting enabled.</span></span>

<span data-ttu-id="be40d-215">De para meter **CimSession** haalt alle modules op in de **CimSession**.</span><span class="sxs-lookup"><span data-stu-id="be40d-215">The **CimSession** parameter gets all modules in the **CIMSession**.</span></span>
<span data-ttu-id="be40d-216">U kunt echter alleen op CIM gebaseerde en cmdlet definition XML-modules (CDXML) importeren.</span><span class="sxs-lookup"><span data-stu-id="be40d-216">However, you can import only CIM-based and Cmdlet Definition XML (CDXML)-based modules.</span></span>

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

### <span data-ttu-id="be40d-217">-FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="be40d-217">-FullyQualifiedName</span></span>

<span data-ttu-id="be40d-218">Hiermee worden de namen van modules in de vorm van **ModuleSpecification** -objecten opgegeven.</span><span class="sxs-lookup"><span data-stu-id="be40d-218">Specifies names of modules in the form of **ModuleSpecification** objects.</span></span>
<span data-ttu-id="be40d-219">Deze objecten worden beschreven in de sectie opmerkingen van de [ModuleSpecification-constructor (hashtabel)](https://msdn.microsoft.com/library/jj136290) in de MSDN-bibliotheek.</span><span class="sxs-lookup"><span data-stu-id="be40d-219">These objects are described in the Remarks section of [ModuleSpecification Constructor (Hashtable)](https://msdn.microsoft.com/library/jj136290) in the MSDN library.</span></span>
<span data-ttu-id="be40d-220">De para meter **FullyQualifiedName** accepteert bijvoorbeeld een module naam die is opgegeven in de volgende indelingen:</span><span class="sxs-lookup"><span data-stu-id="be40d-220">For example, the **FullyQualifiedName** parameter accepts a module name that is specified in the following formats:</span></span>

- <span data-ttu-id="be40d-221">@ {Module naam = "module naam"; ModuleVersion = "version_number"}</span><span class="sxs-lookup"><span data-stu-id="be40d-221">@{ModuleName = "modulename"; ModuleVersion = "version_number"}</span></span>
- <span data-ttu-id="be40d-222">@ {Module naam = "module naam"; ModuleVersion = "version_number"; GUID = "GUID"}</span><span class="sxs-lookup"><span data-stu-id="be40d-222">@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}</span></span>

<span data-ttu-id="be40d-223">**Module** naam en **ModuleVersion** zijn vereist, maar **GUID** is optioneel.</span><span class="sxs-lookup"><span data-stu-id="be40d-223">**ModuleName** and **ModuleVersion** are required, but **Guid** is optional.</span></span>

<span data-ttu-id="be40d-224">U kunt de para meter **FullyQualifiedName** niet opgeven in dezelfde opdracht als de para meter **name** .</span><span class="sxs-lookup"><span data-stu-id="be40d-224">You cannot specify the **FullyQualifiedName** parameter in the same command as a **Name** parameter.</span></span>

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

### <span data-ttu-id="be40d-225">-ListAvailable</span><span class="sxs-lookup"><span data-stu-id="be40d-225">-ListAvailable</span></span>

<span data-ttu-id="be40d-226">Geeft aan dat met deze cmdlet alle geïnstalleerde modules worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="be40d-226">Indicates that this cmdlet gets all installed modules.</span></span>
<span data-ttu-id="be40d-227">`Get-Module` Hiermee worden modules opgehaald in paden die worden weer gegeven in de omgevings variabele **PSModulePath** .</span><span class="sxs-lookup"><span data-stu-id="be40d-227">`Get-Module` gets modules in paths listed in the **PSModulePath** environment variable.</span></span>
<span data-ttu-id="be40d-228">Zonder deze para meter `Get-Module` worden alleen de modules opgehaald die beide zijn opgenomen in de omgevings variabele **PSModulePath** en die worden geladen in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="be40d-228">Without this parameter, `Get-Module` gets only the modules that are both listed in the **PSModulePath** environment variable, and that are loaded in the current session.</span></span>
<span data-ttu-id="be40d-229">**ListAvailable** retourneert geen informatie over modules die niet zijn gevonden in de omgevings variabele **PSModulePath** , zelfs niet als deze modules in de huidige sessie worden geladen.</span><span class="sxs-lookup"><span data-stu-id="be40d-229">**ListAvailable** does not return information about modules that are not found in the **PSModulePath** environment variable, even if those modules are loaded in the current session.</span></span>

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

### <span data-ttu-id="be40d-230">-Name</span><span class="sxs-lookup"><span data-stu-id="be40d-230">-Name</span></span>

<span data-ttu-id="be40d-231">Hiermee worden namen of naam patronen van modules opgegeven die met deze cmdlet worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="be40d-231">Specifies names or name patterns of modules that this cmdlet gets.</span></span>
<span data-ttu-id="be40d-232">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="be40d-232">Wildcard characters are permitted.</span></span>
<span data-ttu-id="be40d-233">U kunt ook de namen door sluizen naar `Get-Module` .</span><span class="sxs-lookup"><span data-stu-id="be40d-233">You can also pipe the names to `Get-Module`.</span></span>
<span data-ttu-id="be40d-234">U kunt de para meter **FullyQualifiedName** niet opgeven in dezelfde opdracht als de para meter **name** .</span><span class="sxs-lookup"><span data-stu-id="be40d-234">You cannot specify the **FullyQualifiedName** parameter in the same command as a **Name** parameter.</span></span>

<span data-ttu-id="be40d-235">De **naam** kan geen module-GUID als waarde accepteren.</span><span class="sxs-lookup"><span data-stu-id="be40d-235">**Name** cannot accept a module GUID as a value.</span></span>
<span data-ttu-id="be40d-236">Gebruik **FullyQualifiedName** in plaats daarvan om modules te retour neren door een GUID op te geven.</span><span class="sxs-lookup"><span data-stu-id="be40d-236">To return modules by specifying a GUID, use **FullyQualifiedName** instead.</span></span>

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

### <span data-ttu-id="be40d-237">-PSEdition</span><span class="sxs-lookup"><span data-stu-id="be40d-237">-PSEdition</span></span>

<span data-ttu-id="be40d-238">Hiermee worden de modules opgehaald die de opgegeven editie van Power shell ondersteunen.</span><span class="sxs-lookup"><span data-stu-id="be40d-238">Gets the modules that support specified edition of PowerShell.</span></span>

<span data-ttu-id="be40d-239">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="be40d-239">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="be40d-240">Bureaublad</span><span class="sxs-lookup"><span data-stu-id="be40d-240">Desktop</span></span>
- <span data-ttu-id="be40d-241">Kern</span><span class="sxs-lookup"><span data-stu-id="be40d-241">Core</span></span>

<span data-ttu-id="be40d-242">De Get-Module-cmdlet controleert de eigenschap **CompatiblePSEditions** van het **PSModuleInfo** -object voor de opgegeven waarde en retourneert alleen de modules die het heeft ingesteld.</span><span class="sxs-lookup"><span data-stu-id="be40d-242">The Get-Module cmdlet checks **CompatiblePSEditions** property of **PSModuleInfo** object for the specified value and returns only those modules that have it set.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="be40d-243">**Desktop-editie:** deze editie is gebaseerd op .NET Framework en biedt compatibiliteit met scripts en modules die zijn gericht op versies van PowerShell die worden uitgevoerd op edities van Windows met een volledige footprint zoals Server Core en Windows Desktop.</span><span class="sxs-lookup"><span data-stu-id="be40d-243">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
> - <span data-ttu-id="be40d-244">**Core-editie:** deze editie is gebaseerd op .NET Framework en biedt compatibiliteit met scripts en modules die zijn gericht op versies van PowerShell die worden uitgevoerd op edities van Windows met een verminderde footprint zoals Nano Server en Windows IoT.</span><span class="sxs-lookup"><span data-stu-id="be40d-244">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

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

### <span data-ttu-id="be40d-245">-PSSession</span><span class="sxs-lookup"><span data-stu-id="be40d-245">-PSSession</span></span>

<span data-ttu-id="be40d-246">Hiermee worden de modules in de opgegeven door de gebruiker beheerde Power shell-sessie ( **PSSession** ) opgehaald.</span><span class="sxs-lookup"><span data-stu-id="be40d-246">Gets the modules in the specified user-managed PowerShell session ( **PSSession** ).</span></span>
<span data-ttu-id="be40d-247">Voer een variabele in die de sessie bevat, een opdracht waarmee de sessie wordt opgehaald, zoals een `Get-PSSession` opdracht of een opdracht waarmee de sessie wordt gemaakt, zoals een `New-PSSession` opdracht.</span><span class="sxs-lookup"><span data-stu-id="be40d-247">Enter a variable that contains the session, a command that gets the session, such as a `Get-PSSession` command, or a command that creates the session, such as a `New-PSSession` command.</span></span>

<span data-ttu-id="be40d-248">Wanneer de sessie is verbonden met een externe computer, moet u de para meter **ListAvailable** opgeven.</span><span class="sxs-lookup"><span data-stu-id="be40d-248">When the session is connected to a remote computer, you must specify the **ListAvailable** parameter.</span></span>

<span data-ttu-id="be40d-249">Een `Get-Module` opdracht die gebruikmaakt van de para meter **PSSession** is gelijk aan het gebruik van de `Invoke-Command` cmdlet om een `Get-Module -ListAvailable` opdracht uit te voeren in een **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="be40d-249">A `Get-Module` command that uses the **PSSession** parameter is equivalent to using the `Invoke-Command` cmdlet to run a `Get-Module -ListAvailable` command in a **PSSession**.</span></span>

<span data-ttu-id="be40d-250">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="be40d-250">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="be40d-251">-Vernieuwen</span><span class="sxs-lookup"><span data-stu-id="be40d-251">-Refresh</span></span>

<span data-ttu-id="be40d-252">Geeft aan dat met deze cmdlet de cache van geïnstalleerde opdrachten wordt vernieuwd.</span><span class="sxs-lookup"><span data-stu-id="be40d-252">Indicates that this cmdlet refreshes the cache of installed commands.</span></span>
<span data-ttu-id="be40d-253">De opdracht cache wordt gemaakt wanneer de sessie wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="be40d-253">The command cache is created when the session starts.</span></span>
<span data-ttu-id="be40d-254">Hiermee kan de `Get-Command` cmdlet opdrachten ophalen uit modules die niet in de sessie zijn geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="be40d-254">It enables the `Get-Command` cmdlet to get commands from modules that are not imported into the session.</span></span>

<span data-ttu-id="be40d-255">Deze para meter is bedoeld voor ontwikkelings-en test scenario's waarin de inhoud van modules is gewijzigd sinds het starten van de sessie.</span><span class="sxs-lookup"><span data-stu-id="be40d-255">This parameter is designed for development and testing scenarios in which the contents of modules have changed since the session started.</span></span>

<span data-ttu-id="be40d-256">Wanneer u de **vernieuwings** parameter opgeeft in een opdracht, moet u **ListAvailable** opgeven.</span><span class="sxs-lookup"><span data-stu-id="be40d-256">When you specify the **Refresh** parameter in a command, you must specify **ListAvailable**.</span></span>

<span data-ttu-id="be40d-257">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="be40d-257">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PsSession, Available, CimSession
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="be40d-258">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="be40d-258">CommonParameters</span></span>

<span data-ttu-id="be40d-259">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="be40d-259">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="be40d-260">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="be40d-260">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="be40d-261">INVOER</span><span class="sxs-lookup"><span data-stu-id="be40d-261">INPUTS</span></span>

### <span data-ttu-id="be40d-262">System. String</span><span class="sxs-lookup"><span data-stu-id="be40d-262">System.String</span></span>

<span data-ttu-id="be40d-263">U kunt module namen door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="be40d-263">You can pipe module names to this cmdlet.</span></span>

## <span data-ttu-id="be40d-264">UITVOER</span><span class="sxs-lookup"><span data-stu-id="be40d-264">OUTPUTS</span></span>

### <span data-ttu-id="be40d-265">System. Management. Automation. PSModuleInfo</span><span class="sxs-lookup"><span data-stu-id="be40d-265">System.Management.Automation.PSModuleInfo</span></span>

<span data-ttu-id="be40d-266">Deze cmdlet retourneert objecten die modules vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="be40d-266">This cmdlet returns objects that represent modules.</span></span>
<span data-ttu-id="be40d-267">Wanneer u de para meter **ListAvailable** opgeeft, wordt `Get-Module` een **ModuleInfoGrouping** -object geretourneerd. Dit is een type **PSModuleInfo** -object met dezelfde eigenschappen en methoden.</span><span class="sxs-lookup"><span data-stu-id="be40d-267">When you specify the **ListAvailable** parameter, `Get-Module` returns a **ModuleInfoGrouping** object, which is a type of **PSModuleInfo** object that has the same properties and methods.</span></span>

## <span data-ttu-id="be40d-268">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="be40d-268">NOTES</span></span>

- <span data-ttu-id="be40d-269">Vanaf Windows Power Shell 3,0 worden de kern opdrachten die zijn opgenomen in Power shell, verpakt in modules.</span><span class="sxs-lookup"><span data-stu-id="be40d-269">Beginning in Windows PowerShell 3.0, the core commands that are included in PowerShell are packaged in modules.</span></span> <span data-ttu-id="be40d-270">De uitzonde ring is **micro soft. Power shell. core** , een module ( **PSSnapin** ).</span><span class="sxs-lookup"><span data-stu-id="be40d-270">The exception is **Microsoft.PowerShell.Core** , which is a snap-in ( **PSSnapin** ).</span></span> <span data-ttu-id="be40d-271">Standaard wordt alleen de module **micro soft. Power shell. core** toegevoegd aan de sessie.</span><span class="sxs-lookup"><span data-stu-id="be40d-271">By default, only the **Microsoft.PowerShell.Core** snap-in is added to the session.</span></span>
<span data-ttu-id="be40d-272">Modules worden automatisch geïmporteerd bij het eerste gebruik en u kunt de `Import-Module` cmdlet gebruiken om ze te importeren.</span><span class="sxs-lookup"><span data-stu-id="be40d-272">Modules are imported automatically on first use and you can use the `Import-Module` cmdlet to import them.</span></span>
- <span data-ttu-id="be40d-273">Vanaf Windows Power Shell 3,0 worden de kern opdrachten die zijn geïnstalleerd met Power shell, verpakt in modules.</span><span class="sxs-lookup"><span data-stu-id="be40d-273">Starting in Windows PowerShell 3.0, the core commands that are installed with PowerShell are packaged in modules.</span></span> <span data-ttu-id="be40d-274">In Windows Power Shell 2,0, en in hostgroepen die oudere sessies maken in latere versies van Power shell, worden de kern opdrachten verpakt in modules ( **PSSnapins** ).</span><span class="sxs-lookup"><span data-stu-id="be40d-274">In Windows PowerShell 2.0, and in host programs that create older-style sessions in later versions of PowerShell, the core commands are packaged in snap-ins ( **PSSnapins** ).</span></span> <span data-ttu-id="be40d-275">De uitzonde ring is **micro soft. Power shell. core**. Dit is altijd een module.</span><span class="sxs-lookup"><span data-stu-id="be40d-275">The exception is **Microsoft.PowerShell.Core** , which is always a snap-in.</span></span> <span data-ttu-id="be40d-276">Externe sessies, zoals computers die zijn gestart door de `New-PSSession` cmdlet, zijn ook oudere sessies met kern modules.</span><span class="sxs-lookup"><span data-stu-id="be40d-276">Also, remote sessions, such as those started by the `New-PSSession` cmdlet, are older-style sessions that include core snap-ins.</span></span>

  <span data-ttu-id="be40d-277">Zie de [methode CreateDefault2](/dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2) in de MSDN-bibliotheek voor meer informatie over de **CreateDefault2** -methode voor het maken van nieuwere sessies met kern modules.</span><span class="sxs-lookup"><span data-stu-id="be40d-277">For information about the **CreateDefault2** method that creates newer-style sessions with core modules, see [CreateDefault2 Method](/dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2) in the MSDN library.</span></span>

- <span data-ttu-id="be40d-278">`Get-Module` haalt alleen modules op in locaties die zijn opgeslagen in de waarde van de **PSModulePath** -omgevings variabele ($env:P smodulepath).</span><span class="sxs-lookup"><span data-stu-id="be40d-278">`Get-Module` only gets modules in locations that are stored in the value of the **PSModulePath** environment variable ($env:PSModulePath).</span></span> <span data-ttu-id="be40d-279">U kunt de para meter **Path** van de `Import-Module` cmdlet gebruiken voor het importeren van modules op andere locaties, maar u kunt de cmdlet niet gebruiken `Get-Module` om deze te downloaden.</span><span class="sxs-lookup"><span data-stu-id="be40d-279">You can use the **Path** parameter of the `Import-Module` cmdlet to import modules in other locations, but you cannot use the `Get-Module` cmdlet to get them.</span></span>
- <span data-ttu-id="be40d-280">Vanuit Power Shell 3,0 zijn er ook nieuwe eigenschappen toegevoegd aan het object, waardoor `Get-Module` het eenvoudiger wordt om te leren over modules, zelfs voordat ze worden geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="be40d-280">Also, starting in PowerShell 3.0, new properties have been added to the object that `Get-Module` returns that make it easier to learn about modules even before they are imported.</span></span> <span data-ttu-id="be40d-281">Alle eigenschappen worden ingevuld voordat ze worden geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="be40d-281">All properties are populated before importing.</span></span> <span data-ttu-id="be40d-282">Dit zijn onder andere de eigenschappen **ExportedCommands** , **ExportedCmdlets** en **ExportedFunctions** die de opdrachten vermeld die de module exporteert.</span><span class="sxs-lookup"><span data-stu-id="be40d-282">These include the **ExportedCommands** , **ExportedCmdlets** and **ExportedFunctions** properties that list the commands that the module exports.</span></span>
- <span data-ttu-id="be40d-283">De para meter **ListAvailable** haalt alleen goed opgemaakte modules op, dat wil zeggen mappen die ten minste één bestand bevatten waarvan de basis naam hetzelfde is als de naam van de module map.</span><span class="sxs-lookup"><span data-stu-id="be40d-283">The **ListAvailable** parameter gets only well-formed modules, that is, folders that contain at least one file whose base name is the same as the name of the module folder.</span></span> <span data-ttu-id="be40d-284">De basis naam is de naam zonder de bestandsnaam extensie.</span><span class="sxs-lookup"><span data-stu-id="be40d-284">The base name is the name without the file name extension.</span></span> <span data-ttu-id="be40d-285">Mappen met bestanden die verschillende namen hebben, worden beschouwd als containers, maar niet in modules.</span><span class="sxs-lookup"><span data-stu-id="be40d-285">Folders that contain files that have different names are considered to be containers, but not modules.</span></span>

  <span data-ttu-id="be40d-286">Als u modules wilt ophalen die als dll-bestanden zijn geïmplementeerd, maar die niet zijn opgenomen in een module-map, geeft u zowel de **ListAvailable** als **alle** para meters op.</span><span class="sxs-lookup"><span data-stu-id="be40d-286">To get modules that are implemented as .dll files, but are not enclosed in a module folder, specify both the **ListAvailable** and **All** parameters.</span></span>

- <span data-ttu-id="be40d-287">Als u de functie CIM-sessie wilt gebruiken, moet de externe computer beschikken over WS-Management remoting en Windows Management Instrumentation (WMI), de micro soft-implementatie van de Common Information Model (CIM)-standaard.</span><span class="sxs-lookup"><span data-stu-id="be40d-287">To use the CIM session feature, the remote computer must have WS-Management remoting and Windows Management Instrumentation (WMI), which is the Microsoft implementation of the Common Information Model (CIM) standard.</span></span> <span data-ttu-id="be40d-288">De computer moet ook de WMI-provider voor module detectie hebben of een alternatieve WMI-provider die dezelfde basis functies heeft.</span><span class="sxs-lookup"><span data-stu-id="be40d-288">The computer must also have the Module Discovery WMI provider or an alternate WMI provider that has the same basic features.</span></span>

  <span data-ttu-id="be40d-289">U kunt de functie CIM-sessie gebruiken op computers waarop het Windows-besturings systeem niet wordt uitgevoerd en op Windows-computers met Power shell, maar externe communicatie van Power shell niet is ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="be40d-289">You can use the CIM session feature on computers that are not running the Windows operating system and on Windows computers that have PowerShell, but do not have PowerShell remoting enabled.</span></span>

  <span data-ttu-id="be40d-290">U kunt ook de CIM-para meters gebruiken om CIM-modules op te halen van computers waarop externe communicatie van Power shell is ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="be40d-290">You can also use the CIM parameters to get CIM modules from computers that have PowerShell remoting enabled.</span></span> <span data-ttu-id="be40d-291">Dit omvat de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="be40d-291">This includes the local computer.</span></span>
<span data-ttu-id="be40d-292">Wanneer u een CIM-sessie op de lokale computer maakt, gebruikt Power shell DCOM in plaats van WMI om de sessie te maken.</span><span class="sxs-lookup"><span data-stu-id="be40d-292">When you create a CIM session on the local computer, PowerShell uses DCOM, instead of WMI, to create the session.</span></span>

## <span data-ttu-id="be40d-293">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="be40d-293">RELATED LINKS</span></span>

[<span data-ttu-id="be40d-294">Get-CimSession</span><span class="sxs-lookup"><span data-stu-id="be40d-294">Get-CimSession</span></span>](../CimCmdlets/Get-CimSession.md)

[<span data-ttu-id="be40d-295">New-CimSession</span><span class="sxs-lookup"><span data-stu-id="be40d-295">New-CimSession</span></span>](../CimCmdlets/New-CimSession.md)

[<span data-ttu-id="be40d-296">about_Modules</span><span class="sxs-lookup"><span data-stu-id="be40d-296">about_Modules</span></span>](About/about_Modules.md)

[<span data-ttu-id="be40d-297">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="be40d-297">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="be40d-298">Import-module</span><span class="sxs-lookup"><span data-stu-id="be40d-298">Import-Module</span></span>](Import-Module.md)

[<span data-ttu-id="be40d-299">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="be40d-299">Import-PSSession</span></span>](../Microsoft.PowerShell.Utility/Import-PSSession.md)

[<span data-ttu-id="be40d-300">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="be40d-300">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="be40d-301">Remove-module</span><span class="sxs-lookup"><span data-stu-id="be40d-301">Remove-Module</span></span>](Remove-Module.md)