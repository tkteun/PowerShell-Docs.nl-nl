---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/24/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-pssessionconfigurationfile?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSSessionConfigurationFile
ms.openlocfilehash: a41c52bf163aa0a73b54e75b5192389a14da82bb
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705622"
---
# <span data-ttu-id="6455a-102">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="6455a-102">New-PSSessionConfigurationFile</span></span>

## <span data-ttu-id="6455a-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="6455a-103">SYNOPSIS</span></span>
<span data-ttu-id="6455a-104">Hiermee maakt u een bestand dat een sessie configuratie definieert.</span><span class="sxs-lookup"><span data-stu-id="6455a-104">Creates a file that defines a session configuration.</span></span>

## <span data-ttu-id="6455a-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="6455a-105">SYNTAX</span></span>

```
New-PSSessionConfigurationFile [-Path] <String> [-SchemaVersion <Version>] [-Guid <Guid>]
 [-Author <String>] [-Description <String>] [-CompanyName <String>] [-Copyright <String>]
 [-SessionType <SessionType>] [-TranscriptDirectory <String>] [-RunAsVirtualAccount]
 [-RunAsVirtualAccountGroups <String[]>] [-MountUserDrive] [-UserDriveMaximumSize <Int64>]
 [-GroupManagedServiceAccount <String>] [-ScriptsToProcess <String[]>]
 [-RoleDefinitions <IDictionary>] [-RequiredGroups <IDictionary>] [-LanguageMode <PSLanguageMode>]
 [-ExecutionPolicy <ExecutionPolicy>] [-PowerShellVersion <Version>] [-ModulesToImport <Object[]>]
 [-VisibleAliases <String[]>] [-VisibleCmdlets <Object[]>] [-VisibleFunctions <Object[]>]
 [-VisibleExternalCommands <String[]>] [-VisibleProviders <String[]>]
 [-AliasDefinitions <IDictionary[]>] [-FunctionDefinitions <IDictionary[]>]
 [-VariableDefinitions <Object>] [-EnvironmentVariables <IDictionary>] [-TypesToProcess <String[]>]
 [-FormatsToProcess <String[]>] [-AssembliesToLoad <String[]>] [-Full] [<CommonParameters>]
```

## <span data-ttu-id="6455a-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="6455a-106">DESCRIPTION</span></span>

<span data-ttu-id="6455a-107">`New-PSSessionConfigurationFile`Met de cmdlet wordt een bestand met instellingen gemaakt waarmee een sessie configuratie en de omgeving van sessies worden gedefinieerd die worden gemaakt met behulp van de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="6455a-107">The `New-PSSessionConfigurationFile` cmdlet creates a file of settings that define a session configuration and the environment of sessions that are created by using the session configuration.</span></span>
<span data-ttu-id="6455a-108">Als u het bestand in een sessie configuratie wilt gebruiken, gebruikt u de para meter **Path** van de `Register-PSSessionConfiguration` `Set-PSSessionConfiguration` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="6455a-108">To use the file in a session configuration, use the **Path** parameter of the `Register-PSSessionConfiguration` or `Set-PSSessionConfiguration` cmdlets.</span></span>

<span data-ttu-id="6455a-109">Het bestand met de sessie configuratie dat wordt `New-PSSessionConfigurationFile` gemaakt, is een tekst bestand dat is gelezen met menselijke Lees baarheid dat een hash-tabel van de eigenschappen en waarden van de sessie configuratie bevat.</span><span class="sxs-lookup"><span data-stu-id="6455a-109">The session configuration file that `New-PSSessionConfigurationFile` creates is a human-readable text file that contains a hash table of the session configuration properties and values.</span></span> <span data-ttu-id="6455a-110">Het bestand heeft de `.pssc` bestands extensie.</span><span class="sxs-lookup"><span data-stu-id="6455a-110">The file has a `.pssc` filename extension.</span></span>

<span data-ttu-id="6455a-111">Alle para meters van `New-PSSessionConfigurationFile` zijn optioneel, met uitzonde ring van de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="6455a-111">All parameters of `New-PSSessionConfigurationFile` are optional, except for the **Path** parameter.</span></span>
<span data-ttu-id="6455a-112">Als u een para meter weglaat, wordt de bijbehorende sleutel in het sessie configuratie bestand commentaar-out, behalve wanneer vermeld in de parameter beschrijving.</span><span class="sxs-lookup"><span data-stu-id="6455a-112">If you omit a parameter, the corresponding key in the session configuration file is commented-out, except where noted in the parameter description.</span></span>

<span data-ttu-id="6455a-113">Een sessie configuratie, ook wel een eind punt genoemd, is een verzameling instellingen op de lokale computer die de omgeving definiëren voor Power shell-sessies (**PSSessions**) die verbinding maken met de computer.</span><span class="sxs-lookup"><span data-stu-id="6455a-113">A session configuration, also known as an endpoint, is a collection of settings on the local computer that define the environment for PowerShell sessions (**PSSessions**) that connect to the computer.</span></span> <span data-ttu-id="6455a-114">Alle **PSSessions** gebruiken een sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="6455a-114">All **PSSessions** use a session configuration.</span></span> <span data-ttu-id="6455a-115">Als u een bepaalde sessie configuratie wilt opgeven, gebruikt u de para meter **configuratiepad** van cmdlets die een sessie maken, zoals de `New-PSSession` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6455a-115">To specify a particular session configuration, use the **ConfigurationName** parameter of cmdlets that create a session, such as the `New-PSSession` cmdlet.</span></span>

<span data-ttu-id="6455a-116">Met een sessie configuratie bestand kunt u eenvoudig een sessie configuratie definiëren zonder complexe scripts of code-assembly's.</span><span class="sxs-lookup"><span data-stu-id="6455a-116">A session configuration file makes it easy to define a session configuration without complex scripts or code assemblies.</span></span> <span data-ttu-id="6455a-117">De instellingen in het bestand worden gebruikt met het optionele opstart script en alle assembly's in de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="6455a-117">The settings in the file are used with the optional startup script and any assemblies in the session configuration.</span></span>

<span data-ttu-id="6455a-118">Zie [about_Session_Configurations](About/about_Session_Configurations.md) en [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)voor meer informatie over sessie configuraties en sessie configuratie bestanden.</span><span class="sxs-lookup"><span data-stu-id="6455a-118">For more information about session configurations and session configuration files, see [about_Session_Configurations](About/about_Session_Configurations.md) and [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).</span></span>

<span data-ttu-id="6455a-119">Deze cmdlet is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="6455a-119">This cmdlet was introduced in PowerShell 3.0.</span></span>

## <span data-ttu-id="6455a-120">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="6455a-120">EXAMPLES</span></span>

### <span data-ttu-id="6455a-121">Voor beeld 1: een geen-taal sessie maken en gebruiken</span><span class="sxs-lookup"><span data-stu-id="6455a-121">Example 1: Creating and using a NoLanguage session</span></span>

<span data-ttu-id="6455a-122">In dit voor beeld ziet u hoe u een sessie zonder taal maakt en hoe u deze kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="6455a-122">This example show how to create and the effects of using a no-language session.</span></span>

<span data-ttu-id="6455a-123">De stappen zijn onder andere:</span><span class="sxs-lookup"><span data-stu-id="6455a-123">The steps include:</span></span>

1. <span data-ttu-id="6455a-124">Maak een nieuw configuratie bestand.</span><span class="sxs-lookup"><span data-stu-id="6455a-124">Create a new configuration file.</span></span>
1. <span data-ttu-id="6455a-125">Registreer de configuratie.</span><span class="sxs-lookup"><span data-stu-id="6455a-125">Register the configuration.</span></span>
1. <span data-ttu-id="6455a-126">Maak een nieuwe sessie die gebruikmaakt van de configuratie.</span><span class="sxs-lookup"><span data-stu-id="6455a-126">Create a new session that uses the configuration.</span></span>
1. <span data-ttu-id="6455a-127">Voer opdrachten in die nieuwe sessie uit.</span><span class="sxs-lookup"><span data-stu-id="6455a-127">Run commands in that new session.</span></span>

<span data-ttu-id="6455a-128">Als u de opdrachten in dit voor beeld wilt uitvoeren, start u Power shell met de optie als administrator uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="6455a-128">To run the commands in this example, start PowerShell by using the Run as administrator option.</span></span> <span data-ttu-id="6455a-129">Deze optie is vereist om de cmdlet uit te voeren `Register-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="6455a-129">This option is required to run the `Register-PSSessionConfiguration` cmdlet.</span></span>

```powershell
New-PSSessionConfigurationFile -Path .\NoLanguage.pssc -LanguageMode NoLanguage
Register-PSSessionConfiguration -Path .\NoLanguage.pssc -Name NoLanguage -Force
$NoLanguageSession = New-PSSession -ComputerName Srv01 -ConfigurationName NoLanguage
Invoke-Command -Session $NoLanguageSession -ScriptBlock {
  if ((Get-Date) -lt '1January2099') {'Before'} else {'After'}
}
```

```Output
The syntax is not supported by this runspace. This might be because it is in no-language mode.
    + CategoryInfo          : ParserError: (if ((Get-Date) ...') {'Before'}  :String) [], ParseException
    + FullyQualifiedErrorId : ScriptsNotAllowed
    + PSComputerName        : localhost
```

<span data-ttu-id="6455a-130">In dit voor beeld `Invoke-Command` mislukt de fout omdat de **LanguageMode** is ingesteld op ' geen **taal**'.</span><span class="sxs-lookup"><span data-stu-id="6455a-130">In this example, the `Invoke-Command` fails because the **LanguageMode** is set to **NoLanguage**.</span></span>

### <span data-ttu-id="6455a-131">Voor beeld 2: een RestrictedLanguage-sessie maken en gebruiken</span><span class="sxs-lookup"><span data-stu-id="6455a-131">Example 2: Creating and using a RestrictedLanguage session</span></span>

<span data-ttu-id="6455a-132">In dit voor beeld ziet u hoe u een sessie zonder taal maakt en hoe u deze kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="6455a-132">This example show how to create and the effects of using a no-language session.</span></span>

<span data-ttu-id="6455a-133">De stappen zijn onder andere:</span><span class="sxs-lookup"><span data-stu-id="6455a-133">The steps include:</span></span>

1. <span data-ttu-id="6455a-134">Maak een nieuw configuratie bestand.</span><span class="sxs-lookup"><span data-stu-id="6455a-134">Create a new configuration file.</span></span>
1. <span data-ttu-id="6455a-135">Registreer de configuratie.</span><span class="sxs-lookup"><span data-stu-id="6455a-135">Register the configuration.</span></span>
1. <span data-ttu-id="6455a-136">Maak een nieuwe sessie die gebruikmaakt van de configuratie.</span><span class="sxs-lookup"><span data-stu-id="6455a-136">Create a new session that uses the configuration.</span></span>
1. <span data-ttu-id="6455a-137">Voer opdrachten in die nieuwe sessie uit.</span><span class="sxs-lookup"><span data-stu-id="6455a-137">Run commands in that new session.</span></span>

<span data-ttu-id="6455a-138">Als u de opdrachten in dit voor beeld wilt uitvoeren, start u Power shell met de optie als administrator uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="6455a-138">To run the commands in this example, start PowerShell by using the Run as administrator option.</span></span> <span data-ttu-id="6455a-139">Deze optie is vereist om de cmdlet uit te voeren `Register-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="6455a-139">This option is required to run the `Register-PSSessionConfiguration` cmdlet.</span></span>

```powershell
New-PSSessionConfigurationFile -Path .\NoLanguage.pssc -LanguageMode RestrictedLanguage
Register-PSSessionConfiguration -Path .\NoLanguage.pssc -Name RestrictedLanguage -Force
$RestrictedSession = New-PSSession -ComputerName Srv01 -ConfigurationName RestrictedLanguage
Invoke-Command -Session $RestrictedSession -ScriptBlock {
  if ((Get-Date) -lt '1January2099') {'Before'} else {'After'}
}
```

```Output
Before
```

<span data-ttu-id="6455a-140">In dit voor beeld `Invoke-Command` is het gelukt omdat de **LanguageMode** is ingesteld op **RestrictedLanguage**.</span><span class="sxs-lookup"><span data-stu-id="6455a-140">In this example, the `Invoke-Command` succeeds because the **LanguageMode** is set to **RestrictedLanguage**.</span></span>

### <span data-ttu-id="6455a-141">Voor beeld 3: een sessie configuratie bestand wijzigen</span><span class="sxs-lookup"><span data-stu-id="6455a-141">Example 3: Changing a Session Configuration File</span></span>

<span data-ttu-id="6455a-142">In dit voor beeld ziet u hoe u het sessie configuratie bestand wijzigt dat wordt gebruikt in een bestaande sessie met de naam ' ITTasks '.</span><span class="sxs-lookup"><span data-stu-id="6455a-142">This example shows how to change the session configuration file that is used in an existing session named "ITTasks".</span></span> <span data-ttu-id="6455a-143">Voorheen hadden deze sessies alleen de kern modules en een interne **ITTasks** -module.</span><span class="sxs-lookup"><span data-stu-id="6455a-143">Previously, these sessions had only the core modules and an internal **ITTasks** module.</span></span> <span data-ttu-id="6455a-144">De beheerder wil de **PSScheduledJob** -module toevoegen aan sessies die zijn gemaakt met behulp van de ITTasks-sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="6455a-144">The administrator wants to add the **PSScheduledJob** module to sessions created by using the ITTasks session configuration.</span></span>

```powershell
New-PSSessionConfigurationFile -Path .\New-ITTasks.pssc -ModulesToImport Microsoft*, ITTasks, PSScheduledJob
Set-PSSessionConfiguration -Name ITTasks -Path .\New-ITTasks.pssc
```

<span data-ttu-id="6455a-145">De `New-PSSessionConfigurationFile` cmdlet voor het maken van een sessie configuratie bestand waarmee de vereiste modules worden geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="6455a-145">The `New-PSSessionConfigurationFile` cmdlet to create a session configuration file that imports the required modules.</span></span> <span data-ttu-id="6455a-146">De `Set-PSSessionConfiguration` cmdlet vervangt het huidige configuratie bestand door de nieuwe.</span><span class="sxs-lookup"><span data-stu-id="6455a-146">The `Set-PSSessionConfiguration` cmdlet replaces the current configuration file with the new one.</span></span> <span data-ttu-id="6455a-147">Deze nieuwe configuratie is alleen van invloed op nieuwe sessies die zijn gemaakt na de wijziging.</span><span class="sxs-lookup"><span data-stu-id="6455a-147">This new configuration only affects new sessions created after the change.</span></span>
<span data-ttu-id="6455a-148">Bestaande ' ITTasks-sessies worden niet beïnvloed.</span><span class="sxs-lookup"><span data-stu-id="6455a-148">Existing "ITTasks" sessions are not affected.</span></span>

### <span data-ttu-id="6455a-149">Voor beeld 4: een sessie configuratie bestand bewerken</span><span class="sxs-lookup"><span data-stu-id="6455a-149">Example 4: Editing a Session Configuration File</span></span>

<span data-ttu-id="6455a-150">In dit voor beeld ziet u hoe u een sessie configuratie wijzigt door de configuratie kopie van de actieve sessie van het configuratie bestand te bewerken.</span><span class="sxs-lookup"><span data-stu-id="6455a-150">This example shows how to change a session configuration by editing the active session configuration copy of the configuration file.</span></span> <span data-ttu-id="6455a-151">Als u de sessie configuratie kopie van het configuratie bestand wilt wijzigen, moet u volledige controle over de toegang tot het bestand hebben.</span><span class="sxs-lookup"><span data-stu-id="6455a-151">To modify the session configuration copy of the configuration file, you must have full control access to the file.</span></span> <span data-ttu-id="6455a-152">Hiervoor moet u mogelijk de machtigingen voor het bestand wijzigen.</span><span class="sxs-lookup"><span data-stu-id="6455a-152">This may require you to change the permissions on the file.</span></span>

<span data-ttu-id="6455a-153">In dit scenario willen we een nieuwe alias voor de `Select-String` cmdlet toevoegen door het actieve configuratie bestand te bewerken.</span><span class="sxs-lookup"><span data-stu-id="6455a-153">In this scenario, we want to add a new alias for the `Select-String` cmdlet by editing the active configuration file.</span></span>

<span data-ttu-id="6455a-154">De voorbeeld code hieronder voert de volgende stappen uit om deze wijziging door te voeren:</span><span class="sxs-lookup"><span data-stu-id="6455a-154">The example code below performs the following steps to make this change:</span></span>

1. <span data-ttu-id="6455a-155">Het pad naar het configuratie bestand voor de ITConfig-sessie ophalen.</span><span class="sxs-lookup"><span data-stu-id="6455a-155">Get the configuration file path for the ITConfig session.</span></span>
1. <span data-ttu-id="6455a-156">De gebruiker bewerkt het configuratie bestand met **Notepad.exe** om de waarde **AliasDefinitions** als volgt te wijzigen: `AliasDefinitions = @(@{Name='slst';Value='Select-String'})` .</span><span class="sxs-lookup"><span data-stu-id="6455a-156">The user edits the configuration file using **Notepad.exe** to change the **AliasDefinitions** value as follows: `AliasDefinitions = @(@{Name='slst';Value='Select-String'})`.</span></span>
1. <span data-ttu-id="6455a-157">Het bijgewerkte configuratie bestand testen.</span><span class="sxs-lookup"><span data-stu-id="6455a-157">Test the updated configuration file.</span></span>

```powershell
$ITConfig = Get-PSSessionConfiguration -Name ITConfig
notepad.exe $ITConfig.ConfigFilePath
Test-PSSessionConfigurationFile -Path $ITConfig.ConfigFilePath
```

```Output
True
```

<span data-ttu-id="6455a-158">Gebruik de para meter **uitgebreid** `Test-PSSessionConfigurationFile` om eventuele fouten weer te geven die zijn gedetecteerd.</span><span class="sxs-lookup"><span data-stu-id="6455a-158">Use the **Verbose** parameter with `Test-PSSessionConfigurationFile` to display any errors that are detected.</span></span> <span data-ttu-id="6455a-159">De cmdlet wordt geretourneerd `$True` als er geen fouten worden gedetecteerd in het bestand.</span><span class="sxs-lookup"><span data-stu-id="6455a-159">The cmdlet returns `$True` if no errors are detected in the file.</span></span>

### <span data-ttu-id="6455a-160">Voor beeld 5: een voorbeeld configuratie bestand maken</span><span class="sxs-lookup"><span data-stu-id="6455a-160">Example 5: Create a sample configuration file</span></span>

<span data-ttu-id="6455a-161">In dit voor beeld ziet u een `New-PSSessionConfigurationFile` opdracht die gebruikmaakt van alle cmdlet-para meters.</span><span class="sxs-lookup"><span data-stu-id="6455a-161">This example shows a `New-PSSessionConfigurationFile` command that uses all the cmdlet parameters.</span></span>
<span data-ttu-id="6455a-162">Het is opgenomen om de juiste invoer indeling voor elke para meter weer te geven.</span><span class="sxs-lookup"><span data-stu-id="6455a-162">It is included to show the correct input format for each parameter.</span></span>

<span data-ttu-id="6455a-163">De resulterende SampleFile. pssc wordt weer gegeven in de uitvoer.</span><span class="sxs-lookup"><span data-stu-id="6455a-163">The resulting SampleFile.pssc is displayed in the output.</span></span>

```powershell
$configSettings = @{
    Path = '.\SampleFile.pssc'
    SchemaVersion = '1.0.0.0'
    Author = 'User01'
    Copyright = '(c) Fabrikam Corporation. All rights reserved.'
    CompanyName = 'Fabrikam Corporation'
    Description = 'This is a sample file.'
    ExecutionPolicy = 'AllSigned'
    PowerShellVersion = '3.0'
    LanguageMode = 'FullLanguage'
    SessionType = 'Default'
    EnvironmentVariables = @{TESTSHARE='\\Test2\Test'}
    ModulesToImport = @{ModuleName='PSScheduledJob'; ModuleVersion='1.0.0.0'; GUID='50cdb55f-5ab7-489f-9e94-4ec21ff51e59'},'PSDiagnostics'
    AssembliesToLoad = 'System.Web.Services','FSharp.Compiler.CodeDom.dll'
    TypesToProcess = 'Types1.ps1xml','Types2.ps1xml'
    FormatsToProcess = 'CustomFormats.ps1xml'
    ScriptsToProcess = 'Get-Inputs.ps1'
    AliasDefinitions = @{Name='hlp';Value='Get-Help';Description='Gets help.';Options='AllScope'},
        @{Name='Update';Value='Update-Help';Description='Updates help';Options='ReadOnly'}
    FunctionDefinitions = @{Name='Get-Function';ScriptBlock={Get-Command -CommandType Function};Options='ReadOnly'}
    VariableDefinitions = @{Name='WarningPreference';Value='SilentlyContinue'}
    VisibleAliases = 'c*','g*','i*','s*'
    VisibleCmdlets = 'Get*'
    VisibleFunctions = 'Get*'
    VisibleProviders = 'FileSystem','Function','Variable'
    RunAsVirtualAccount = $true
    RunAsVirtualAccountGroups = 'Backup Operators'
}
New-PSSessionConfigurationFile @configSettings
Get-Content SampleFile.pssc
```

```Output
@{

# Version number of the schema used for this document
SchemaVersion = '1.0.0.0'

# ID used to uniquely identify this document
GUID = '1caeff7f-27ca-4360-97cf-37846f594235'

# Author of this document
Author = 'User01'

# Description of the functionality provided by these settings
Description = 'This is a sample file.'

# Company associated with this document
CompanyName = 'Fabrikam Corporation'

# Copyright statement for this document
Copyright = '(c) Fabrikam Corporation. All rights reserved.'

# Session type defaults to apply for this session configuration. Can be 'RestrictedRemoteServer' (recommended), 'Empty', or 'Default'
SessionType = 'Default'

# Directory to place session transcripts for this session configuration
# TranscriptDirectory = 'C:\Transcripts\'

# Whether to run this session configuration as the machine's (virtual) administrator account
RunAsVirtualAccount = $true

# Groups associated with machine's (virtual) administrator account
RunAsVirtualAccountGroups = 'Backup Operators'

# Scripts to run when applied to a session
ScriptsToProcess = 'Get-Inputs.ps1'

# User roles (security groups), and the role capabilities that should be applied to them when applied to a session
# RoleDefinitions = @{ 'CONTOSO\SqlAdmins' = @{ RoleCapabilities = 'SqlAdministration' }; 'CONTOSO\SqlManaged' = @{ RoleCapabilityFiles = 'C:\RoleCapability\SqlManaged.psrc' }; 'CONTOSO\ServerMonitors' = @{ VisibleCmdlets = 'Get-Process' } }

# Language mode to apply when applied to a session. Can be 'NoLanguage' (recommended), 'RestrictedLanguage', 'ConstrainedLanguage', or 'FullLanguage'
LanguageMode = 'FullLanguage'

# Execution policy to apply when applied to a session
ExecutionPolicy = 'AllSigned'

# Version of the PowerShell engine to use when applied to a session
PowerShellVersion = '3.0'

# Modules to import when applied to a session
ModulesToImport = @{
    'GUID' = '50cdb55f-5ab7-489f-9e94-4ec21ff51e59'
    'ModuleName' = 'PSScheduledJob'
    'ModuleVersion' = '1.0.0.0' }, 'PSDiagnostics'

# Aliases to make visible when applied to a session
VisibleAliases = 'c*', 'g*', 'i*', 's*'

# Cmdlets to make visible when applied to a session
VisibleCmdlets = 'Get*'

# Functions to make visible when applied to a session
VisibleFunctions = 'Get*'

# Providers to make visible when applied to a session
VisibleProviders = 'FileSystem', 'Function', 'Variable'

# Aliases to be defined when applied to a session
AliasDefinitions = @{
    'Description' = 'Gets help.'
    'Name' = 'hlp'
    'Options' = 'AllScope'
    'Value' = 'Get-Help' }, @{
    'Description' = 'Updates help'
    'Name' = 'Update'
    'Options' = 'ReadOnly'
    'Value' = 'Update-Help' }

# Functions to define when applied to a session
FunctionDefinitions = @{
    'Name' = 'Get-Function'
    'Options' = 'ReadOnly'
    'ScriptBlock' = {Get-Command -CommandType Function} }

# Variables to define when applied to a session
VariableDefinitions = @{
    'Name' = 'WarningPreference'
    'Value' = 'SilentlyContinue' }

# Environment variables to define when applied to a session
EnvironmentVariables = @{
    'TESTSHARE' = '\\Test2\Test' }

# Type files (.ps1xml) to load when applied to a session
TypesToProcess = 'Types1.ps1xml', 'Types2.ps1xml'

# Format files (.ps1xml) to load when applied to a session
FormatsToProcess = 'CustomFormats.ps1xml'

# Assemblies to load when applied to a session
AssembliesToLoad = 'System.Web.Services', 'FSharp.Compiler.CodeDom.dll'

}
```

## <span data-ttu-id="6455a-164">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6455a-164">PARAMETERS</span></span>

### <span data-ttu-id="6455a-165">-AliasDefinitions</span><span class="sxs-lookup"><span data-stu-id="6455a-165">-AliasDefinitions</span></span>

<span data-ttu-id="6455a-166">Voegt de opgegeven aliassen toe aan sessies die gebruikmaken van de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="6455a-166">Adds the specified aliases to sessions that use the session configuration.</span></span> <span data-ttu-id="6455a-167">Voer een hash-tabel in met de volgende sleutels:</span><span class="sxs-lookup"><span data-stu-id="6455a-167">Enter a hash table with the following keys:</span></span>

- <span data-ttu-id="6455a-168">Naam: naam van de alias.</span><span class="sxs-lookup"><span data-stu-id="6455a-168">Name - Name of the alias.</span></span> <span data-ttu-id="6455a-169">Deze sleutel is vereist.</span><span class="sxs-lookup"><span data-stu-id="6455a-169">This key is required.</span></span>
- <span data-ttu-id="6455a-170">Waarde: de opdracht die door de alias wordt vertegenwoordigd.</span><span class="sxs-lookup"><span data-stu-id="6455a-170">Value - The command that the alias represents.</span></span> <span data-ttu-id="6455a-171">Deze sleutel is vereist.</span><span class="sxs-lookup"><span data-stu-id="6455a-171">This key is required.</span></span>
- <span data-ttu-id="6455a-172">Beschrijving: een teken reeks waarmee de alias wordt beschreven.</span><span class="sxs-lookup"><span data-stu-id="6455a-172">Description - A text string that describes the alias.</span></span> <span data-ttu-id="6455a-173">Deze sleutel is optioneel.</span><span class="sxs-lookup"><span data-stu-id="6455a-173">This key is optional.</span></span>
- <span data-ttu-id="6455a-174">Opties-alias opties.</span><span class="sxs-lookup"><span data-stu-id="6455a-174">Options - Alias options.</span></span> <span data-ttu-id="6455a-175">Deze sleutel is optioneel.</span><span class="sxs-lookup"><span data-stu-id="6455a-175">This key is optional.</span></span> <span data-ttu-id="6455a-176">De standaard waarde is **geen**.</span><span class="sxs-lookup"><span data-stu-id="6455a-176">The default value is **None**.</span></span> <span data-ttu-id="6455a-177">De acceptabele waarden voor deze para meter zijn: geen, alleen-lezen, constant, privé of AllScope.</span><span class="sxs-lookup"><span data-stu-id="6455a-177">The acceptable values for this parameter are: None, ReadOnly, Constant, Private, or AllScope.</span></span>

<span data-ttu-id="6455a-178">Bijvoorbeeld: `@{Name='hlp';Value='Get-Help';Description='Gets help';Options='ReadOnly'}`</span><span class="sxs-lookup"><span data-stu-id="6455a-178">For example: `@{Name='hlp';Value='Get-Help';Description='Gets help';Options='ReadOnly'}`</span></span>

```yaml
Type: System.Collections.IDictionary[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6455a-179">-AssembliesToLoad</span><span class="sxs-lookup"><span data-stu-id="6455a-179">-AssembliesToLoad</span></span>

<span data-ttu-id="6455a-180">Hiermee geeft u de assembly's op die moeten worden geladen in de sessies die gebruikmaken van de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="6455a-180">Specifies the assemblies to load into the sessions that use the session configuration.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6455a-181">-Author</span><span class="sxs-lookup"><span data-stu-id="6455a-181">-Author</span></span>

<span data-ttu-id="6455a-182">Hiermee geeft u de auteur van de sessie configuratie of het configuratie bestand.</span><span class="sxs-lookup"><span data-stu-id="6455a-182">Specifies the author of the session configuration or the configuration file.</span></span> <span data-ttu-id="6455a-183">Standaard is dit de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="6455a-183">The default is the current user.</span></span> <span data-ttu-id="6455a-184">De waarde van deze para meter is zichtbaar in het sessie configuratie bestand, maar is geen eigenschap van het sessie configuratie object.</span><span class="sxs-lookup"><span data-stu-id="6455a-184">The value of this parameter is visible in the session configuration file, but it is not a property of the session configuration object.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6455a-185">-CompanyName</span><span class="sxs-lookup"><span data-stu-id="6455a-185">-CompanyName</span></span>

<span data-ttu-id="6455a-186">Hiermee geeft u het bedrijf op dat de sessie configuratie of het configuratie bestand heeft gemaakt.</span><span class="sxs-lookup"><span data-stu-id="6455a-186">Specifies the company that created the session configuration or the configuration file.</span></span> <span data-ttu-id="6455a-187">De standaard waarde is **onbekend**.</span><span class="sxs-lookup"><span data-stu-id="6455a-187">The default value is **Unknown**.</span></span> <span data-ttu-id="6455a-188">De waarde van deze para meter is zichtbaar in het sessie configuratie bestand, maar is geen eigenschap van het sessie configuratie object.</span><span class="sxs-lookup"><span data-stu-id="6455a-188">The value of this parameter is visible in the session configuration file, but it is not a property of the session configuration object.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Unknown
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6455a-189">-Copyright</span><span class="sxs-lookup"><span data-stu-id="6455a-189">-Copyright</span></span>

<span data-ttu-id="6455a-190">Hiermee geeft u een copyright het configuratie bestand voor de sessie.</span><span class="sxs-lookup"><span data-stu-id="6455a-190">Specifies a copyright the session configuration file.</span></span> <span data-ttu-id="6455a-191">De waarde van deze para meter is zichtbaar in het sessie configuratie bestand, maar is geen eigenschap van het sessie configuratie object.</span><span class="sxs-lookup"><span data-stu-id="6455a-191">The value of this parameter is visible in the session configuration file, but it is not a property of the session configuration object.</span></span>

<span data-ttu-id="6455a-192">Als u deze para meter weglaat, `New-PSSessionConfigurationFile` genereert een copyright verklaring met behulp van de waarde van de para meter **Auteur** .</span><span class="sxs-lookup"><span data-stu-id="6455a-192">If you omit this parameter, `New-PSSessionConfigurationFile` generates a copyright statement by using the value of the **Author** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6455a-193">-Beschrijving</span><span class="sxs-lookup"><span data-stu-id="6455a-193">-Description</span></span>

<span data-ttu-id="6455a-194">Hiermee geeft u een beschrijving van de sessie configuratie of het sessie configuratie bestand op.</span><span class="sxs-lookup"><span data-stu-id="6455a-194">Specifies a description of the session configuration or the session configuration file.</span></span> <span data-ttu-id="6455a-195">De waarde van deze para meter is zichtbaar in het sessie configuratie bestand, maar is geen eigenschap van het sessie configuratie object.</span><span class="sxs-lookup"><span data-stu-id="6455a-195">The value of this parameter is visible in the session configuration file, but it is not a property of the session configuration object.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6455a-196">-Omgevings variabelen</span><span class="sxs-lookup"><span data-stu-id="6455a-196">-EnvironmentVariables</span></span>

<span data-ttu-id="6455a-197">Hiermee voegt u omgevings variabelen toe aan de sessie.</span><span class="sxs-lookup"><span data-stu-id="6455a-197">Adds environment variables to the session.</span></span> <span data-ttu-id="6455a-198">Voer een hash-tabel in waarin de sleutels de namen van omgevings variabelen zijn en de waarden zijn de waarden van omgevings variabelen.</span><span class="sxs-lookup"><span data-stu-id="6455a-198">Enter a hash table in which the keys are the environment variable names and the values are the environment variable values.</span></span>

<span data-ttu-id="6455a-199">Bijvoorbeeld: `EnvironmentVariables=@{TestShare='\\Server01\TestShare'}`</span><span class="sxs-lookup"><span data-stu-id="6455a-199">For example: `EnvironmentVariables=@{TestShare='\\Server01\TestShare'}`</span></span>

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6455a-200">-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="6455a-200">-ExecutionPolicy</span></span>

<span data-ttu-id="6455a-201">Hiermee geeft u het uitvoerings beleid op van sessies die gebruikmaken van de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="6455a-201">Specifies the execution policy of sessions that use the session configuration.</span></span> <span data-ttu-id="6455a-202">Als u deze para meter weglaat, wordt de waarde van de sleutel **ExecutionPolicy** in het sessie configuratie bestand **beperkt**.</span><span class="sxs-lookup"><span data-stu-id="6455a-202">If you omit this parameter, the value of the **ExecutionPolicy** key in the session configuration file is **Restricted**.</span></span> <span data-ttu-id="6455a-203">Zie [about_Execution_Policies](about/about_Execution_Policies.md)voor meer informatie over uitvoerings beleid in Power shell.</span><span class="sxs-lookup"><span data-stu-id="6455a-203">For information about execution policies in PowerShell, see [about_Execution_Policies](about/about_Execution_Policies.md).</span></span>

```yaml
Type: Microsoft.PowerShell.ExecutionPolicy
Parameter Sets: (All)
Aliases:
Accepted values: Unrestricted, RemoteSigned, AllSigned, Restricted, Default, Bypass, Undefined

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6455a-204">-FormatsToProcess</span><span class="sxs-lookup"><span data-stu-id="6455a-204">-FormatsToProcess</span></span>

<span data-ttu-id="6455a-205">Hiermee geeft u de indelings bestanden (. ps1xml) op die worden uitgevoerd in sessies die gebruikmaken van de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="6455a-205">Specifies the formatting files (.ps1xml) that run in sessions that use the session configuration.</span></span>
<span data-ttu-id="6455a-206">De waarde van deze para meter moet een volledig of absoluut pad van de indelings bestanden zijn.</span><span class="sxs-lookup"><span data-stu-id="6455a-206">The value of this parameter must be a full or absolute path of the formatting files.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6455a-207">-Volledig</span><span class="sxs-lookup"><span data-stu-id="6455a-207">-Full</span></span>

<span data-ttu-id="6455a-208">Geeft aan dat deze bewerking alle mogelijke configuratie-eigenschappen in het sessie configuratie bestand bevat.</span><span class="sxs-lookup"><span data-stu-id="6455a-208">Indicates that this operation includes all possible configuration properties in the session configuration file.</span></span>

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

### <span data-ttu-id="6455a-209">-FunctionDefinitions</span><span class="sxs-lookup"><span data-stu-id="6455a-209">-FunctionDefinitions</span></span>

<span data-ttu-id="6455a-210">Voegt de opgegeven functies toe aan sessies die gebruikmaken van de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="6455a-210">Adds the specified functions to sessions that use the session configuration.</span></span> <span data-ttu-id="6455a-211">Voer een hash-tabel in met de volgende sleutels:</span><span class="sxs-lookup"><span data-stu-id="6455a-211">Enter a hash table with the following keys:</span></span>

- <span data-ttu-id="6455a-212">Naam: naam van de functie.</span><span class="sxs-lookup"><span data-stu-id="6455a-212">Name - Name of the function.</span></span> <span data-ttu-id="6455a-213">Deze sleutel is vereist.</span><span class="sxs-lookup"><span data-stu-id="6455a-213">This key is required.</span></span>
- <span data-ttu-id="6455a-214">Script block-functie hoofd tekst.</span><span class="sxs-lookup"><span data-stu-id="6455a-214">ScriptBlock - Function body.</span></span> <span data-ttu-id="6455a-215">Voer een script blok in.</span><span class="sxs-lookup"><span data-stu-id="6455a-215">Enter a script block.</span></span> <span data-ttu-id="6455a-216">Deze sleutel is vereist.</span><span class="sxs-lookup"><span data-stu-id="6455a-216">This key is required.</span></span>
- <span data-ttu-id="6455a-217">Opties-functie opties.</span><span class="sxs-lookup"><span data-stu-id="6455a-217">Options - Function options.</span></span> <span data-ttu-id="6455a-218">Deze sleutel is optioneel.</span><span class="sxs-lookup"><span data-stu-id="6455a-218">This key is optional.</span></span> <span data-ttu-id="6455a-219">De standaard waarde is **geen**.</span><span class="sxs-lookup"><span data-stu-id="6455a-219">The default value is **None**.</span></span> <span data-ttu-id="6455a-220">De acceptabele waarden voor deze para meter zijn: geen, alleen-lezen, constant, privé of AllScope.</span><span class="sxs-lookup"><span data-stu-id="6455a-220">The acceptable values for this parameter are: None, ReadOnly, Constant, Private, or AllScope.</span></span>

<span data-ttu-id="6455a-221">Bijvoorbeeld: `@{Name='Get-PowerShellProcess';ScriptBlock={Get-Process PowerShell};Options='AllScope'}`</span><span class="sxs-lookup"><span data-stu-id="6455a-221">For example: `@{Name='Get-PowerShellProcess';ScriptBlock={Get-Process PowerShell};Options='AllScope'}`</span></span>

```yaml
Type: System.Collections.IDictionary[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6455a-222">-GroupManagedServiceAccount</span><span class="sxs-lookup"><span data-stu-id="6455a-222">-GroupManagedServiceAccount</span></span>

<span data-ttu-id="6455a-223">Hiermee configureert u sessies met behulp van deze sessie configuratie om uit te voeren in de context van het opgegeven beheerde service account van de groep.</span><span class="sxs-lookup"><span data-stu-id="6455a-223">Configures sessions using this session configuration to run under the context of the specified Group Managed Service Account.</span></span> <span data-ttu-id="6455a-224">De computer waarvoor deze sessie configuratie is geregistreerd, moet gemachtigd zijn om het gMSA-wacht woord aan te vragen om de sessies te kunnen maken.</span><span class="sxs-lookup"><span data-stu-id="6455a-224">The machine where this session configuration is registered must have permission to request the gMSA password in order for sessions to be created successfully.</span></span> <span data-ttu-id="6455a-225">Dit veld kan niet worden gebruikt met de para meter **RunAsVirtualAccount** .</span><span class="sxs-lookup"><span data-stu-id="6455a-225">This field cannot be used with the **RunAsVirtualAccount** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6455a-226">-GUID</span><span class="sxs-lookup"><span data-stu-id="6455a-226">-Guid</span></span>

<span data-ttu-id="6455a-227">Hiermee geeft u een unieke id voor het sessie configuratie bestand op.</span><span class="sxs-lookup"><span data-stu-id="6455a-227">Specifies a unique identifier for the session configuration file.</span></span> <span data-ttu-id="6455a-228">Als u deze para meter weglaat, `New-PSSessionConfigurationFile` genereert een GUID voor het bestand.</span><span class="sxs-lookup"><span data-stu-id="6455a-228">If you omit this parameter, `New-PSSessionConfigurationFile` generates a GUID for the file.</span></span> <span data-ttu-id="6455a-229">Als u een nieuwe GUID wilt maken in Power shell, typt u `New-Guid` .</span><span class="sxs-lookup"><span data-stu-id="6455a-229">To create a new GUID in PowerShell, type `New-Guid`.</span></span>

```yaml
Type: System.Guid
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6455a-230">-LanguageMode</span><span class="sxs-lookup"><span data-stu-id="6455a-230">-LanguageMode</span></span>

<span data-ttu-id="6455a-231">Hiermee wordt bepaald welke elementen van de Power shell-taal zijn toegestaan in sessies die gebruikmaken van deze sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="6455a-231">Determines which elements of the PowerShell language are permitted in sessions that use this session configuration.</span></span> <span data-ttu-id="6455a-232">U kunt deze para meter gebruiken om de opdrachten te beperken die bepaalde gebruikers op de computer kunnen uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="6455a-232">You can use this parameter to restrict the commands that particular users can run on the computer.</span></span>

<span data-ttu-id="6455a-233">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="6455a-233">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="6455a-234">FullLanguage: alle taal elementen zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="6455a-234">FullLanguage - All language elements are permitted.</span></span>
- <span data-ttu-id="6455a-235">ConstrainedLanguage-opdrachten die scripts bevatten die moeten worden geëvalueerd, zijn niet toegestaan.</span><span class="sxs-lookup"><span data-stu-id="6455a-235">ConstrainedLanguage - Commands that contain scripts to be evaluated are not allowed.</span></span> <span data-ttu-id="6455a-236">De ConstrainedLanguage-modus beperkt de gebruikers toegang tot Microsoft .NET Framework-typen,-objecten of-methoden.</span><span class="sxs-lookup"><span data-stu-id="6455a-236">The ConstrainedLanguage mode restricts user access to Microsoft .NET Framework types, objects, or methods.</span></span>
- <span data-ttu-id="6455a-237">Taal: gebruikers kunnen cmdlets en functies uitvoeren, maar mogen geen taal elementen gebruiken, zoals script blokken, variabelen of Opera tors.</span><span class="sxs-lookup"><span data-stu-id="6455a-237">NoLanguage - Users may run cmdlets and functions, but are not permitted to use any language elements, such as script blocks, variables, or operators.</span></span>
- <span data-ttu-id="6455a-238">RestrictedLanguage: gebruikers kunnen cmdlets en functies uitvoeren, maar mogen geen script blokken of variabelen gebruiken, met uitzonde ring van de volgende toegestane variabelen: `$PSCulture` , `$PSUICulture` , `$True` , en `$False` `$Null` .</span><span class="sxs-lookup"><span data-stu-id="6455a-238">RestrictedLanguage - Users may run cmdlets and functions, but are not permitted to use script blocks or variables except for the following permitted variables: `$PSCulture`, `$PSUICulture`, `$True`, `$False`, and `$Null`.</span></span> <span data-ttu-id="6455a-239">Gebruikers kunnen alleen de basis vergelijkings operatoren ( `-eq` , `-gt` ,) gebruiken `-lt` .</span><span class="sxs-lookup"><span data-stu-id="6455a-239">Users may use only the basic comparison operators (`-eq`, `-gt`, `-lt`).</span></span> <span data-ttu-id="6455a-240">Toewijzings instructies, verwijzingen naar eigenschappen en methode aanroepen zijn niet toegestaan.</span><span class="sxs-lookup"><span data-stu-id="6455a-240">Assignment statements, property references, and method calls are not permitted.</span></span>

<span data-ttu-id="6455a-241">De standaard waarde van de para meter **LanguageMode** is afhankelijk van de waarde van de para meter **SessionType** .</span><span class="sxs-lookup"><span data-stu-id="6455a-241">The default value of the **LanguageMode** parameter depends on the value of the **SessionType** parameter.</span></span>

- <span data-ttu-id="6455a-242">Lege-de taal</span><span class="sxs-lookup"><span data-stu-id="6455a-242">Empty - NoLanguage</span></span>
- <span data-ttu-id="6455a-243">RestrictedRemoteServer-taal</span><span class="sxs-lookup"><span data-stu-id="6455a-243">RestrictedRemoteServer - NoLanguage</span></span>
- <span data-ttu-id="6455a-244">Default-FullLanguage</span><span class="sxs-lookup"><span data-stu-id="6455a-244">Default - FullLanguage</span></span>

```yaml
Type: System.Management.Automation.PSLanguageMode
Parameter Sets: (All)
Aliases:
Accepted values: FullLanguage, RestrictedLanguage, NoLanguage, ConstrainedLanguage

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6455a-245">-ModulesToImport</span><span class="sxs-lookup"><span data-stu-id="6455a-245">-ModulesToImport</span></span>

<span data-ttu-id="6455a-246">Hiermee geeft u de modules en modules op die automatisch worden geïmporteerd in sessies die gebruikmaken van de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="6455a-246">Specifies the modules and snap-ins that are automatically imported into sessions that use the session configuration.</span></span>

<span data-ttu-id="6455a-247">Standaard wordt alleen de module **micro soft. Power shell. core** geïmporteerd in externe sessies, maar tenzij de cmdlets worden uitgesloten, kunnen gebruikers de `Import-Module` cmdlets en gebruiken `Add-PSSnapin` om modules en modules toe te voegen aan de sessie.</span><span class="sxs-lookup"><span data-stu-id="6455a-247">By default, only the **Microsoft.PowerShell.Core** snap-in is imported into remote sessions, but unless the cmdlets are excluded, users can use the `Import-Module` and `Add-PSSnapin` cmdlets to add modules and snap-ins to the session.</span></span>

<span data-ttu-id="6455a-248">Elke module of module in de waarde van deze para meter kan worden vertegenwoordigd door een teken reeks of als een hash-tabel.</span><span class="sxs-lookup"><span data-stu-id="6455a-248">Each module or snap-in in the value of this parameter can be represented by a string or as a hash table.</span></span> <span data-ttu-id="6455a-249">Een module teken reeks bestaat alleen uit de naam van de module of module.</span><span class="sxs-lookup"><span data-stu-id="6455a-249">A module string consists only of the name of the module or snap-in.</span></span> <span data-ttu-id="6455a-250">Een module-hash-tabel kan **module**-, **ModuleVersion**-en **GUID** -sleutels bevatten.</span><span class="sxs-lookup"><span data-stu-id="6455a-250">A module hash table can include **ModuleName**, **ModuleVersion**, and **GUID** keys.</span></span> <span data-ttu-id="6455a-251">Alleen de **module** sleutel is vereist.</span><span class="sxs-lookup"><span data-stu-id="6455a-251">Only the **ModuleName** key is required.</span></span>

<span data-ttu-id="6455a-252">De volgende waarde bestaat bijvoorbeeld uit een teken reeks en een hash-tabel.</span><span class="sxs-lookup"><span data-stu-id="6455a-252">For example, the following value consists of a string and a hash table.</span></span> <span data-ttu-id="6455a-253">Een combi natie van teken reeksen en hash-tabellen, in een wille keurige volg orde, is geldig.</span><span class="sxs-lookup"><span data-stu-id="6455a-253">Any combination of strings and hash tables, in any order, is valid.</span></span>

`'TroubleshootingPack', @{ModuleName='PSDiagnostics'; ModuleVersion='1.0.0.0';GUID='c61d6278-02a3-4618-ae37-a524d40a7f44'}`

<span data-ttu-id="6455a-254">De waarde van de para meter **ModulesToImport** van de `Register-PSSessionConfiguration` cmdlet krijgt voor rang op de waarde van de **ModulesToImport** -sleutel in het configuratie bestand voor de sessie.</span><span class="sxs-lookup"><span data-stu-id="6455a-254">The value of the **ModulesToImport** parameter of the `Register-PSSessionConfiguration` cmdlet takes precedence over the value of the **ModulesToImport** key in the session configuration file.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6455a-255">-MountUserDrive</span><span class="sxs-lookup"><span data-stu-id="6455a-255">-MountUserDrive</span></span>

<span data-ttu-id="6455a-256">Hiermee configureert u sessies die gebruikmaken van deze sessie configuratie om de PSDrive zichtbaar te maken `User:` .</span><span class="sxs-lookup"><span data-stu-id="6455a-256">Configures sessions that use this session configuration to expose the `User:` PSDrive.</span></span> <span data-ttu-id="6455a-257">Gebruikers stations zijn uniek voor elke gebruiker die verbinding maakt en waarmee gebruikers gegevens kunnen kopiëren van en naar Power shell-eind punten, zelfs als de bestandssysteem provider niet wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="6455a-257">User drives are unique for each connecting user and allow users to copy data to and from PowerShell endpoints even if the File System provider is not exposed.</span></span> <span data-ttu-id="6455a-258">Roots van het gebruikers station worden gemaakt onder `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\` .</span><span class="sxs-lookup"><span data-stu-id="6455a-258">User drive roots are created under `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\`.</span></span> <span data-ttu-id="6455a-259">Voor elke gebruiker die verbinding maakt met het eind punt, wordt een map met de naam gemaakt `$env:USERDOMAIN_$env:USERNAME` .</span><span class="sxs-lookup"><span data-stu-id="6455a-259">For each user connecting to the endpoint, a folder is created with the name `$env:USERDOMAIN_$env:USERNAME`.</span></span>

<span data-ttu-id="6455a-260">De inhoud van het gebruikers station blijft achter gebruikers sessies en wordt niet automatisch verwijderd.</span><span class="sxs-lookup"><span data-stu-id="6455a-260">Contents in the user drive persist across user sessions and are not automatically removed.</span></span> <span data-ttu-id="6455a-261">Standaard kunnen gebruikers alleen de 50 MB van gegevens in het gebruikers station opslaan.</span><span class="sxs-lookup"><span data-stu-id="6455a-261">By default, users can only store up to 50MB of data in the user drive.</span></span> <span data-ttu-id="6455a-262">Dit kan worden aangepast met de para meter **UserDriveMaximumSize** .</span><span class="sxs-lookup"><span data-stu-id="6455a-262">This can be customized with the **UserDriveMaximumSize** parameter.</span></span>

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

### <span data-ttu-id="6455a-263">-Path</span><span class="sxs-lookup"><span data-stu-id="6455a-263">-Path</span></span>

<span data-ttu-id="6455a-264">Hiermee geeft u het pad en de bestands naam van het sessie configuratie bestand.</span><span class="sxs-lookup"><span data-stu-id="6455a-264">Specifies the path and filename of the session configuration file.</span></span> <span data-ttu-id="6455a-265">Het bestand moet een `.pssc` bestandsnaam extensie hebben.</span><span class="sxs-lookup"><span data-stu-id="6455a-265">The file must have a `.pssc` file name extension.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6455a-266">-PowerShellVersion</span><span class="sxs-lookup"><span data-stu-id="6455a-266">-PowerShellVersion</span></span>

<span data-ttu-id="6455a-267">Hiermee geeft u de versie van de Power shell-engine in sessies die gebruikmaken van de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="6455a-267">Specifies the version of the PowerShell engine in sessions that use the session configuration.</span></span> <span data-ttu-id="6455a-268">De acceptabele waarden voor deze para meter zijn: 2,0 en 3,0.</span><span class="sxs-lookup"><span data-stu-id="6455a-268">The acceptable values for this parameter are: 2.0 and 3.0.</span></span> <span data-ttu-id="6455a-269">Als u deze para meter weglaat, wordt de **PowerShellVersion** -sleutel commentaar-out en de nieuwste versie van Power shell-uitvoeringen in de sessie.</span><span class="sxs-lookup"><span data-stu-id="6455a-269">If you omit this parameter, the **PowerShellVersion** key is commented-out and newest version of PowerShell runs in the session.</span></span>

<span data-ttu-id="6455a-270">De waarde van de para meter **PSVersion** van de `Register-PSSessionConfiguration` cmdlet krijgt voor rang op de waarde van de **PowerShellVersion** -sleutel in het configuratie bestand voor de sessie.</span><span class="sxs-lookup"><span data-stu-id="6455a-270">The value of the **PSVersion** parameter of the `Register-PSSessionConfiguration` cmdlet takes precedence over the value of the **PowerShellVersion** key in the session configuration file.</span></span>

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6455a-271">-RequiredGroups</span><span class="sxs-lookup"><span data-stu-id="6455a-271">-RequiredGroups</span></span>

<span data-ttu-id="6455a-272">Hiermee geeft u regels voor voorwaardelijke toegang op voor gebruikers die verbinding maken met sessies die gebruikmaken van deze sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="6455a-272">Specifies conditional access rules for users connecting to sessions that use this session configuration.</span></span>

<span data-ttu-id="6455a-273">Voer een hashtabel in om de lijst met regels te maken met slechts één sleutel per hashtabel, ' en ' of ' of ', en stel de waarde in op een matrix met namen van beveiligings groepen of extra hashtabellen.</span><span class="sxs-lookup"><span data-stu-id="6455a-273">Enter a hashtable to compose your list of rules using only 1 key per hashtable, 'And' or 'Or', and set the value to an array of security group names or additional hashtables.</span></span>

<span data-ttu-id="6455a-274">Voor beeld waarbij gebruikers worden verbonden om lid te zijn van één groep: `@{ And = 'MyRequiredGroup' }`</span><span class="sxs-lookup"><span data-stu-id="6455a-274">Example requiring connecting users to be members of a single group: `@{ And = 'MyRequiredGroup' }`</span></span>

<span data-ttu-id="6455a-275">Voor beeld dat gebruikers moeten deel uitmaken van groep A of beide groepen B en C om toegang te krijgen tot het eind punt: `@{ Or = 'GroupA', @{ And = 'GroupB', 'GroupC' } }`</span><span class="sxs-lookup"><span data-stu-id="6455a-275">Example requiring users to belong to group A, or both groups B and C, to access the endpoint: `@{ Or = 'GroupA', @{ And = 'GroupB', 'GroupC' } }`</span></span>

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6455a-276">-RoleDefinitions</span><span class="sxs-lookup"><span data-stu-id="6455a-276">-RoleDefinitions</span></span>

<span data-ttu-id="6455a-277">Hiermee geeft u de toewijzing op tussen beveiligings groepen (of gebruikers) en functie mogelijkheden.</span><span class="sxs-lookup"><span data-stu-id="6455a-277">Specifies the mapping between security groups (or users) and role capabilities.</span></span> <span data-ttu-id="6455a-278">Gebruikers krijgen toegang tot alle functie mogelijkheden die van toepassing zijn op hun groepslid maatschap op het moment dat de sessie wordt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="6455a-278">Users will be granted access to all role capabilities which apply to their group membership at the time the session is created.</span></span>

<span data-ttu-id="6455a-279">Voer een hash-tabel in waarin de sleutels de naam van de beveiligings groep zijn en de waarden zijn hash-tabellen die een lijst met functie mogelijkheden bevatten die beschikbaar moeten worden gemaakt voor de beveiligings groep.</span><span class="sxs-lookup"><span data-stu-id="6455a-279">Enter a hash table in which the keys are the name of the security group and the values are hash tables that contain a list of role capabilities that should be made available to the security group.</span></span>

<span data-ttu-id="6455a-280">Bijvoorbeeld: `@{'Contoso\Level 2 Helpdesk Users' = @{ RoleCapabilities = 'Maintenance', 'ADHelpDesk' }}`</span><span class="sxs-lookup"><span data-stu-id="6455a-280">For example: `@{'Contoso\Level 2 Helpdesk Users' = @{ RoleCapabilities = 'Maintenance', 'ADHelpDesk' }}`</span></span>

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6455a-281">-RunAsVirtualAccount</span><span class="sxs-lookup"><span data-stu-id="6455a-281">-RunAsVirtualAccount</span></span>

<span data-ttu-id="6455a-282">Hiermee configureert u sessies met behulp van deze sessie configuratie om te worden uitgevoerd als het virtuele beheerders account van de computer.</span><span class="sxs-lookup"><span data-stu-id="6455a-282">Configures sessions using this session configuration to be run as the computer's (virtual) administrator account.</span></span> <span data-ttu-id="6455a-283">Dit veld kan niet worden gebruikt met de para meter **GroupManagedServiceAccount** .</span><span class="sxs-lookup"><span data-stu-id="6455a-283">This field cannot be used with the **GroupManagedServiceAccount** parameter.</span></span>

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

### <span data-ttu-id="6455a-284">-RunAsVirtualAccountGroups</span><span class="sxs-lookup"><span data-stu-id="6455a-284">-RunAsVirtualAccountGroups</span></span>

<span data-ttu-id="6455a-285">Hiermee geeft u de beveiligings groepen op die moeten worden gekoppeld aan het virtuele account wanneer een sessie die gebruikmaakt van de sessie configuratie, als een virtueel account wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="6455a-285">Specifies the security groups to be associated with the virtual account when a session that uses the session configuration is run as a virtual account.</span></span> <span data-ttu-id="6455a-286">Als u dit weglaat, behoort het virtuele account bij domein Administrators op domein controllers en beheerders op alle andere computers.</span><span class="sxs-lookup"><span data-stu-id="6455a-286">If omitted, the virtual account belongs to Domain Admins on domain controllers and Administrators on all other computers.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6455a-287">-SchemaVersion</span><span class="sxs-lookup"><span data-stu-id="6455a-287">-SchemaVersion</span></span>

<span data-ttu-id="6455a-288">Hiermee geeft u de versie van het schema van het configuratie bestand voor de sessie.</span><span class="sxs-lookup"><span data-stu-id="6455a-288">Specifies the version of the session configuration file schema.</span></span> <span data-ttu-id="6455a-289">De standaard waarde is "1.0.0.0".</span><span class="sxs-lookup"><span data-stu-id="6455a-289">The default value is "1.0.0.0".</span></span>

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6455a-290">-ScriptsToProcess</span><span class="sxs-lookup"><span data-stu-id="6455a-290">-ScriptsToProcess</span></span>

<span data-ttu-id="6455a-291">Voegt de opgegeven scripts toe aan sessies die gebruikmaken van de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="6455a-291">Adds the specified scripts to sessions that use the session configuration.</span></span> <span data-ttu-id="6455a-292">Geef het pad en de bestands namen van de scripts op.</span><span class="sxs-lookup"><span data-stu-id="6455a-292">Enter the path and file names of the scripts.</span></span> <span data-ttu-id="6455a-293">De waarde van deze para meter moet een volledig of absoluut pad van script bestandsnamen zijn.</span><span class="sxs-lookup"><span data-stu-id="6455a-293">The value of this parameter must be a full or absolute path of script file names.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6455a-294">-SessionType</span><span class="sxs-lookup"><span data-stu-id="6455a-294">-SessionType</span></span>

<span data-ttu-id="6455a-295">Hiermee geeft u het type sessie op dat wordt gemaakt met behulp van de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="6455a-295">Specifies the type of session that is created by using the session configuration.</span></span> <span data-ttu-id="6455a-296">De standaard waarde is standaard.</span><span class="sxs-lookup"><span data-stu-id="6455a-296">The default value is Default.</span></span> <span data-ttu-id="6455a-297">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="6455a-297">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="6455a-298">Leeg: er worden standaard geen modules aan de sessie toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="6455a-298">Empty - No modules are added to session by default.</span></span> <span data-ttu-id="6455a-299">Gebruik de para meters van deze cmdlet om modules, functies, scripts en andere functies aan de sessie toe te voegen.</span><span class="sxs-lookup"><span data-stu-id="6455a-299">Use the parameters of this cmdlet to add modules, functions, scripts, and other features to the session.</span></span> <span data-ttu-id="6455a-300">Deze optie is bedoeld om aangepaste sessies te maken door geselecteerde opdrachten toe te voegen.</span><span class="sxs-lookup"><span data-stu-id="6455a-300">This option is designed for you to create custom sessions by adding selected commands.</span></span> <span data-ttu-id="6455a-301">Als u geen opdrachten toevoegt aan een lege sessie, is de sessie beperkt tot expressies en is deze mogelijk niet bruikbaar.</span><span class="sxs-lookup"><span data-stu-id="6455a-301">If you do not add commands to an empty session, the session is limited to expressions and might not be usable.</span></span>
- <span data-ttu-id="6455a-302">Default-de module micro soft. Power shell. core wordt toegevoegd aan de sessie.</span><span class="sxs-lookup"><span data-stu-id="6455a-302">Default - Adds the Microsoft.PowerShell.Core module to the session.</span></span> <span data-ttu-id="6455a-303">Deze module bevat de `Import-Module` cmdlet die gebruikers kunnen gebruiken om andere modules te importeren, tenzij u deze cmdlet expliciet niet toestaat.</span><span class="sxs-lookup"><span data-stu-id="6455a-303">This module includes the `Import-Module` cmdlet that users can use to import other modules unless you explicitly prohibit this cmdlet.</span></span>
- <span data-ttu-id="6455a-304">RestrictedRemoteServer.</span><span class="sxs-lookup"><span data-stu-id="6455a-304">RestrictedRemoteServer.</span></span> <span data-ttu-id="6455a-305">Bevat alleen de volgende proxy functies: `Exit-PSSession` , `Get-Command` , `Get-FormatData` , `Get-Help` ,, en `Measure-Object` `Out-Default` `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="6455a-305">Includes only the following proxy functions: `Exit-PSSession`, `Get-Command`, `Get-FormatData`, `Get-Help`, `Measure-Object`, `Out-Default`, and `Select-Object`.</span></span>
  <span data-ttu-id="6455a-306">Gebruik de para meters van deze cmdlet om modules, functies, scripts en andere functies aan de sessie toe te voegen.</span><span class="sxs-lookup"><span data-stu-id="6455a-306">Use the parameters of this cmdlet to add modules, functions, scripts, and other features to the session.</span></span>

```yaml
Type: System.Management.Automation.Remoting.SessionType
Parameter Sets: (All)
Aliases:
Accepted values: Empty, RestrictedRemoteServer, Default

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6455a-307">-TranscriptDirectory</span><span class="sxs-lookup"><span data-stu-id="6455a-307">-TranscriptDirectory</span></span>

<span data-ttu-id="6455a-308">Hiermee geeft u de map voor het plaatsen van sessie transcripten voor sessies met behulp van deze sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="6455a-308">Specifies the directory to place session transcripts for sessions using this session configuration.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6455a-309">-TypesToProcess</span><span class="sxs-lookup"><span data-stu-id="6455a-309">-TypesToProcess</span></span>

<span data-ttu-id="6455a-310">Voegt de opgegeven `.ps1xml` type bestanden toe aan sessies die gebruikmaken van de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="6455a-310">Adds the specified `.ps1xml` type files to sessions that use the session configuration.</span></span> <span data-ttu-id="6455a-311">Voer de bestands namen van het type in.</span><span class="sxs-lookup"><span data-stu-id="6455a-311">Enter the type filenames.</span></span> <span data-ttu-id="6455a-312">De waarde van deze para meter moet een volledig of absoluut pad zijn om bestands namen te kunnen typen.</span><span class="sxs-lookup"><span data-stu-id="6455a-312">The value of this parameter must be a full or absolute path to type filenames.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6455a-313">-UserDriveMaximumSize</span><span class="sxs-lookup"><span data-stu-id="6455a-313">-UserDriveMaximumSize</span></span>

<span data-ttu-id="6455a-314">Hiermee geeft u de maximale grootte op voor gebruikers stations die worden weer gegeven in sessies die gebruikmaken van deze sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="6455a-314">Specifies the maximum size for user drives exposed in sessions that use this session configuration.</span></span>
<span data-ttu-id="6455a-315">Als u dit weglaat, is de standaard grootte van elke hoofdmap van het `User:` station 50 MB.</span><span class="sxs-lookup"><span data-stu-id="6455a-315">When omitted, the default size of each `User:` drive root is 50MB.</span></span>

<span data-ttu-id="6455a-316">Deze para meter moet worden gebruikt met **MountUserDrive**.</span><span class="sxs-lookup"><span data-stu-id="6455a-316">This parameter should be used with **MountUserDrive**.</span></span>

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6455a-317">-VariableDefinitions</span><span class="sxs-lookup"><span data-stu-id="6455a-317">-VariableDefinitions</span></span>

<span data-ttu-id="6455a-318">Voegt de opgegeven variabelen toe aan sessies die gebruikmaken van de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="6455a-318">Adds the specified variables to sessions that use the session configuration.</span></span> <span data-ttu-id="6455a-319">Voer een hash-tabel in met de volgende sleutels:</span><span class="sxs-lookup"><span data-stu-id="6455a-319">Enter a hash table with the following keys:</span></span>

- <span data-ttu-id="6455a-320">Naam: naam van de variabele.</span><span class="sxs-lookup"><span data-stu-id="6455a-320">Name - Name of the variable.</span></span> <span data-ttu-id="6455a-321">Deze sleutel is vereist.</span><span class="sxs-lookup"><span data-stu-id="6455a-321">This key is required.</span></span>
- <span data-ttu-id="6455a-322">Waarde variabele.</span><span class="sxs-lookup"><span data-stu-id="6455a-322">Value - Variable value.</span></span> <span data-ttu-id="6455a-323">Deze sleutel is vereist.</span><span class="sxs-lookup"><span data-stu-id="6455a-323">This key is required.</span></span>
- <span data-ttu-id="6455a-324">Opties: variabele opties.</span><span class="sxs-lookup"><span data-stu-id="6455a-324">Options - Variable options.</span></span> <span data-ttu-id="6455a-325">Deze sleutel is optioneel.</span><span class="sxs-lookup"><span data-stu-id="6455a-325">This key is optional.</span></span> <span data-ttu-id="6455a-326">De standaard waarde is **geen**.</span><span class="sxs-lookup"><span data-stu-id="6455a-326">The default value is **None**.</span></span> <span data-ttu-id="6455a-327">De acceptabele waarden voor deze para meter zijn: geen, alleen-lezen, constant, privé of AllScope.</span><span class="sxs-lookup"><span data-stu-id="6455a-327">The acceptable values for this parameter are: None, ReadOnly, Constant, Private, or AllScope.</span></span>

<span data-ttu-id="6455a-328">Bijvoorbeeld: `@{Name='WarningPreference';Value='SilentlyContinue';Options='AllScope'}`</span><span class="sxs-lookup"><span data-stu-id="6455a-328">For example: `@{Name='WarningPreference';Value='SilentlyContinue';Options='AllScope'}`</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6455a-329">-VisibleAliases</span><span class="sxs-lookup"><span data-stu-id="6455a-329">-VisibleAliases</span></span>

<span data-ttu-id="6455a-330">Hiermee worden de aliassen in de sessie beperkt tot die welke zijn opgegeven in de waarde van deze para meter, plus alle aliassen die u definieert in de para meter **AliasDefinition** .</span><span class="sxs-lookup"><span data-stu-id="6455a-330">Limits the aliases in the session to those specified in the value of this parameter, plus any aliases that you define in the **AliasDefinition** parameter.</span></span> <span data-ttu-id="6455a-331">Joker tekens worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="6455a-331">Wildcard characters are supported.</span></span> <span data-ttu-id="6455a-332">Standaard worden alle aliassen die zijn gedefinieerd door de Power shell-engine en alle aliassen die modules exporteren, weer gegeven in de sessie.</span><span class="sxs-lookup"><span data-stu-id="6455a-332">By default, all aliases that are defined by the PowerShell engine and all aliases that modules export are visible in the session.</span></span>

<span data-ttu-id="6455a-333">Bijvoorbeeld: `VisibleAliases='gcm', 'gp'`</span><span class="sxs-lookup"><span data-stu-id="6455a-333">For example: `VisibleAliases='gcm', 'gp'`</span></span>

<span data-ttu-id="6455a-334">Wanneer een **zicht bare** para meter is opgenomen in het configuratie bestand van de sessie, verwijdert Power shell de `Import-Module` cmdlet en de ipmo-alias uit de sessie.</span><span class="sxs-lookup"><span data-stu-id="6455a-334">When any **Visible** parameter is included in the session configuration file, PowerShell removes the `Import-Module` cmdlet and its ipmo alias from the session.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="6455a-335">-VisibleCmdlets</span><span class="sxs-lookup"><span data-stu-id="6455a-335">-VisibleCmdlets</span></span>

<span data-ttu-id="6455a-336">Hiermee worden de cmdlets in de sessie beperkt tot die welke zijn opgegeven in de waarde van deze para meter.</span><span class="sxs-lookup"><span data-stu-id="6455a-336">Limits the cmdlets in the session to those specified in the value of this parameter.</span></span> <span data-ttu-id="6455a-337">Joker tekens en modules met gekwalificeerde namen worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="6455a-337">Wildcard characters and Module Qualified Names are supported.</span></span>

<span data-ttu-id="6455a-338">Standaard worden alle cmdlets die modules in de sessie exporteren, weer gegeven in de sessie.</span><span class="sxs-lookup"><span data-stu-id="6455a-338">By default, all cmdlets that modules in the session export are visible in the session.</span></span> <span data-ttu-id="6455a-339">Gebruik de para meters **SessionType** en **ModulesToImport** om te bepalen welke modules en modules in de sessie worden geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="6455a-339">Use the **SessionType** and **ModulesToImport** parameters to determine which modules and snap-ins are imported into the session.</span></span> <span data-ttu-id="6455a-340">Als er geen modules in **ModulesToImport** de cmdlet beschikbaar maken, probeert de juiste module automatisch te laden.</span><span class="sxs-lookup"><span data-stu-id="6455a-340">If no modules in **ModulesToImport** expose the cmdlet, the appropriate module will attempt to be autoloaded.</span></span>

<span data-ttu-id="6455a-341">Wanneer een **zicht bare** para meter is opgenomen in het configuratie bestand van de sessie, verwijdert Power shell de `Import-Module` cmdlet en de ipmo-alias uit de sessie.</span><span class="sxs-lookup"><span data-stu-id="6455a-341">When any **Visible** parameter is included in the session configuration file, PowerShell removes the `Import-Module` cmdlet and its ipmo alias from the session.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6455a-342">-VisibleExternalCommands</span><span class="sxs-lookup"><span data-stu-id="6455a-342">-VisibleExternalCommands</span></span>

<span data-ttu-id="6455a-343">Hiermee beperkt u de externe binaire bestanden, scripts en opdrachten die in de sessie kunnen worden uitgevoerd en die zijn opgegeven in de waarde van deze para meter.</span><span class="sxs-lookup"><span data-stu-id="6455a-343">Limits the external binaries, scripts, and commands that can be executed in the session to those specified in the value of this parameter.</span></span> <span data-ttu-id="6455a-344">Joker tekens worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="6455a-344">Wildcard characters are supported.</span></span>

<span data-ttu-id="6455a-345">Standaard zijn er geen externe opdrachten zichtbaar in de sessie.</span><span class="sxs-lookup"><span data-stu-id="6455a-345">By default, no external commands are visible in the session.</span></span>

<span data-ttu-id="6455a-346">Wanneer een **zicht bare** para meter is opgenomen in het configuratie bestand van de sessie, verwijdert Power shell de `Import-Module` cmdlet en de ipmo-alias van de sessie.</span><span class="sxs-lookup"><span data-stu-id="6455a-346">When any **Visible** parameter is included in the session configuration file, PowerShell, removes the `Import-Module` cmdlet and its ipmo alias from the session.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="6455a-347">-VisibleFunctions</span><span class="sxs-lookup"><span data-stu-id="6455a-347">-VisibleFunctions</span></span>

<span data-ttu-id="6455a-348">Hiermee beperkt u de functies in de sessie die zijn opgegeven in de waarde van deze para meter, plus de functies die u definieert in de para meter **FunctionDefinition** .</span><span class="sxs-lookup"><span data-stu-id="6455a-348">Limits the functions in the session to those specified in the value of this parameter, plus any functions that you define in the **FunctionDefinition** parameter.</span></span> <span data-ttu-id="6455a-349">Joker tekens worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="6455a-349">Wildcard characters are supported.</span></span>

<span data-ttu-id="6455a-350">Standaard zijn alle functies die modules in de sessie exporteren, weer gegeven in de sessie.</span><span class="sxs-lookup"><span data-stu-id="6455a-350">By default, all functions that modules in the session export are visible in the session.</span></span> <span data-ttu-id="6455a-351">Gebruik de para meters **SessionType** en **ModulesToImport** om te bepalen welke modules en modules in de sessie worden geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="6455a-351">Use the **SessionType** and **ModulesToImport** parameters to determine which modules and snap-ins are imported into the session.</span></span>

<span data-ttu-id="6455a-352">Wanneer een **zicht bare** para meter is opgenomen in het configuratie bestand van de sessie, verwijdert Power shell de `Import-Module` cmdlet en de ipmo-alias uit de sessie.</span><span class="sxs-lookup"><span data-stu-id="6455a-352">When any **Visible** parameter is included in the session configuration file, PowerShell removes the `Import-Module` cmdlet and its ipmo alias from the session.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="6455a-353">-VisibleProviders</span><span class="sxs-lookup"><span data-stu-id="6455a-353">-VisibleProviders</span></span>

<span data-ttu-id="6455a-354">Hiermee worden de Power shell-providers in de sessie beperkt tot die welke zijn opgegeven in de waarde van deze para meter.</span><span class="sxs-lookup"><span data-stu-id="6455a-354">Limits the PowerShell providers in the session to those specified in the value of this parameter.</span></span>
<span data-ttu-id="6455a-355">Joker tekens worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="6455a-355">Wildcard characters are supported.</span></span>

<span data-ttu-id="6455a-356">Standaard worden alle providers die modules in de sessie exporteren, weer gegeven in de sessie.</span><span class="sxs-lookup"><span data-stu-id="6455a-356">By default, all providers that modules in the session export are visible in the session.</span></span> <span data-ttu-id="6455a-357">Gebruik de para meters **SessionType** en **ModulesToImport** om te bepalen welke modules in de sessie worden geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="6455a-357">Use the **SessionType** and **ModulesToImport** parameters to determine which modules are imported into the session.</span></span>

<span data-ttu-id="6455a-358">Wanneer een **zicht bare** para meter is opgenomen in het configuratie bestand van de sessie, verwijdert Power shell de `Import-Module` cmdlet en de bijbehorende `ipmo` alias uit de sessie.</span><span class="sxs-lookup"><span data-stu-id="6455a-358">When any **Visible** parameter is included in the session configuration file, PowerShell removes the `Import-Module` cmdlet and its `ipmo` alias from the session.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="6455a-359">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6455a-359">CommonParameters</span></span>

<span data-ttu-id="6455a-360">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6455a-360">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6455a-361">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="6455a-361">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6455a-362">INVOER</span><span class="sxs-lookup"><span data-stu-id="6455a-362">INPUTS</span></span>

### <span data-ttu-id="6455a-363">Geen</span><span class="sxs-lookup"><span data-stu-id="6455a-363">None</span></span>

<span data-ttu-id="6455a-364">U kunt geen objecten door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6455a-364">You cannot pipe any objects to this cmdlet.</span></span>

## <span data-ttu-id="6455a-365">UITVOER</span><span class="sxs-lookup"><span data-stu-id="6455a-365">OUTPUTS</span></span>

### <span data-ttu-id="6455a-366">Geen</span><span class="sxs-lookup"><span data-stu-id="6455a-366">None</span></span>

<span data-ttu-id="6455a-367">Met deze cmdlet wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="6455a-367">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="6455a-368">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="6455a-368">NOTES</span></span>

<span data-ttu-id="6455a-369">Deze cmdlet is alleen beschikbaar op Windows-platforms.</span><span class="sxs-lookup"><span data-stu-id="6455a-369">This cmdlet is only available on Windows platforms.</span></span>

- <span data-ttu-id="6455a-370">In para meters, zoals **VisibleCmdlets** en **VisibleProviders**, worden geen items geïmporteerd in de sessie.</span><span class="sxs-lookup"><span data-stu-id="6455a-370">Parameters, such as **VisibleCmdlets** and **VisibleProviders**, do not import items into the session.</span></span> <span data-ttu-id="6455a-371">In plaats daarvan selecteren ze uit de items die in de sessie worden geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="6455a-371">Instead, they select from among the items imported into the session.</span></span> <span data-ttu-id="6455a-372">Als de waarde van de para meter **VisibleProviders** bijvoorbeeld de certificaat provider is, maar de **ModulesToImport** -para meter geeft geen **micro soft. Power shell. Security** -module op die de certificaat provider bevat, is de certificaat provider niet zichtbaar in de sessie.</span><span class="sxs-lookup"><span data-stu-id="6455a-372">For example, if the value of the **VisibleProviders** parameter is the Certificate provider, but the **ModulesToImport** parameter does not specify the **Microsoft.PowerShell.Security** module that contains the Certificate provider, the Certificate provider is not visible in the session.</span></span>
- <span data-ttu-id="6455a-373">`New-PSSessionConfigurationFile` Hiermee maakt u een sessie configuratie bestand met de bestandsnaam extensie. pssc in het pad dat u opgeeft in de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="6455a-373">`New-PSSessionConfigurationFile` creates a session configuration file that has a .pssc file name extension in the path that you specify in the **Path** parameter.</span></span> <span data-ttu-id="6455a-374">Wanneer u het sessie configuratie bestand gebruikt om een sessie configuratie te maken, `Register-PSSessionConfiguration` kopieert de cmdlet het configuratie bestand en slaat het een actieve kopie van het bestand op in de **SessionConfig** -submap van de `$PSHOME` map.</span><span class="sxs-lookup"><span data-stu-id="6455a-374">When you use the session configuration file to create a session configuration, the `Register-PSSessionConfiguration` cmdlet copies the configuration file and saves an active copy of the file in the **SessionConfig** subdirectory of the `$PSHOME` directory.</span></span>

  <span data-ttu-id="6455a-375">De eigenschap **ConfigFilePath** van de sessie configuratie bevat het volledig gekwalificeerde pad van het configuratie bestand van de actieve sessie.</span><span class="sxs-lookup"><span data-stu-id="6455a-375">The **ConfigFilePath** property of the session configuration contains the fully qualified path of the active session configuration file.</span></span> <span data-ttu-id="6455a-376">U kunt het actieve configuratie bestand `$PSHOME` op elk gewenst moment in de Directory wijzigen met behulp van een tekst editor.</span><span class="sxs-lookup"><span data-stu-id="6455a-376">You can modify the active configuration file in the `$PSHOME` directory at any time using any text editor.</span></span> <span data-ttu-id="6455a-377">De wijzigingen die u aanbrengt, zijn van invloed op alle nieuwe sessies die gebruikmaken van de sessie configuratie, maar niet op bestaande sessies.</span><span class="sxs-lookup"><span data-stu-id="6455a-377">The changes that you make affect all new sessions that use the session configuration, but not existing sessions.</span></span>

  <span data-ttu-id="6455a-378">Voordat u een bewerkte sessie configuratie bestand gebruikt, gebruikt `Test-PSSessionConfigurationFile` u de cmdlet om te controleren of de vermeldingen van het configuratie bestand geldig zijn.</span><span class="sxs-lookup"><span data-stu-id="6455a-378">Before using an edited session configuration file, use the `Test-PSSessionConfigurationFile` cmdlet to verify that the configuration file entries are valid.</span></span>

## <span data-ttu-id="6455a-379">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="6455a-379">RELATED LINKS</span></span>

[<span data-ttu-id="6455a-380">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="6455a-380">Disable-PSSessionConfiguration</span></span>](Disable-PSSessionConfiguration.md)

[<span data-ttu-id="6455a-381">Enable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="6455a-381">Enable-PSSessionConfiguration</span></span>](Enable-PSSessionConfiguration.md)

[<span data-ttu-id="6455a-382">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="6455a-382">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="6455a-383">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="6455a-383">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="6455a-384">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="6455a-384">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="6455a-385">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="6455a-385">Test-PSSessionConfigurationFile</span></span>](Test-PSSessionConfigurationFile.md)

[<span data-ttu-id="6455a-386">Registratie ongedaan maken-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="6455a-386">Unregister-PSSessionConfiguration</span></span>](Unregister-PSSessionConfiguration.md)

[<span data-ttu-id="6455a-387">WSMan Provider</span><span class="sxs-lookup"><span data-stu-id="6455a-387">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[<span data-ttu-id="6455a-388">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="6455a-388">about_Session_Configurations</span></span>](About/about_Session_Configurations.md)

[<span data-ttu-id="6455a-389">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="6455a-389">about_Session_Configuration_Files</span></span>](About/about_Session_Configuration_Files.md)
