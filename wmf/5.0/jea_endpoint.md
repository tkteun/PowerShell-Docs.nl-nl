---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: e4910e95a417da61661aaddd98b2dc7da9f98a3d
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/17/2018
ms.locfileid: "39093715"
---
# <a name="creating-and-connecting-to-a-jea-endpoint"></a><span data-ttu-id="404ed-102">Een JEA-eindpunt maken en hier verbinding mee maken</span><span class="sxs-lookup"><span data-stu-id="404ed-102">Creating and Connecting to a JEA Endpoint</span></span>
<span data-ttu-id="404ed-103">Voor het maken van een JEA-eindpunt, moet u maken en registreren van een speciaal geconfigureerd PowerShell-sessie configuratiebestand, die kan worden gegenereerd met de **New-PSSessionConfigurationFile** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="404ed-103">To create a JEA endpoint, you need to create and register a specially-configured PowerShell Session Configuration file, which can be generated with the **New-PSSessionConfigurationFile** cmdlet.</span></span>

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -TranscriptDirectory "C:\ProgramData\JEATranscripts" -RunAsVirtualAccount -RoleDefinitions @{ 'CONTOSO\NonAdmin_Operators' = @{ RoleCapabilities = 'Maintenance' }} -Path "$env:ProgramData\JEAConfiguration\Demo.pssc"
```

<span data-ttu-id="404ed-104">Hiermee maakt u een sessie-configuratiebestand dat er als uitzien volgt:</span><span class="sxs-lookup"><span data-stu-id="404ed-104">This will create a session configuration file that looks like this:</span></span>
```powershell
@{

# Version number of the schema used for this document
SchemaVersion = '2.0.0.0'

# ID used to uniquely identify this document
GUID = 'a384fdd3-5830-4a2c-ac86-cdd1822c3afd'

# Author of this document
Author = 'Administrator'

# Description of the functionality provided by these settings
# Description = ''

# Session type defaults to apply for this session configuration. Can be 'RestrictedRemoteServer' (recommended), 'Empty', or 'Default'
SessionType = 'RestrictedRemoteServer'

# Directory to place session transcripts for this session configuration
TranscriptDirectory = 'C:\ProgramData\JEATranscripts'

# Whether to run this session configuration as the machine's (virtual) administrator account
RunAsVirtualAccount = $true

# Groups associated with machine's (virtual) administrator account
# RunAsVirtualAccountGroups = 'Remote Desktop Users', 'Remote Management Users'

# Scripts to run when applied to a session
# ScriptsToProcess = 'C:\ConfigData\InitScript1.ps1', 'C:\ConfigData\InitScript2.ps1'

# User roles (security groups), and the Role Capabilities that should be applied to them when applied to a session
RoleDefinitions = @{
    'CONTOSO\NonAdmin_Operators' = @{
        'RoleCapabilities' = 'Maintenance' } }

}
```
<span data-ttu-id="404ed-105">Bij het maken van een JEA-eindpunt, moeten de volgende parameters van de opdracht (en de bijbehorende sleutels in het bestand) worden ingesteld:</span><span class="sxs-lookup"><span data-stu-id="404ed-105">When creating a JEA endpoint, the following parameters of the command (and corresponding keys in the file) must be set:</span></span>
1.  <span data-ttu-id="404ed-106">SessionType naar RestrictedRemoteServer</span><span class="sxs-lookup"><span data-stu-id="404ed-106">SessionType to RestrictedRemoteServer</span></span>
2.  <span data-ttu-id="404ed-107">RunAsVirtualAccount naar **$true**</span><span class="sxs-lookup"><span data-stu-id="404ed-107">RunAsVirtualAccount to **$true**</span></span>
3.  <span data-ttu-id="404ed-108">TranscriptPath naar de map waarin 'meekijk' Transcripten moeten worden opgeslagen na elke sessie</span><span class="sxs-lookup"><span data-stu-id="404ed-108">TranscriptPath to the directory where “over the shoulder” transcripts will be saved after each session</span></span>
4.  <span data-ttu-id="404ed-109">RoleDefinitions naar een hashtabel waarmee wordt gedefinieerd welke groepen hebben toegang tot welke 'Rolmogelijkheden'.</span><span class="sxs-lookup"><span data-stu-id="404ed-109">RoleDefinitions to a hashtable that defines which groups have access to which “Role Capabilities.”</span></span>  <span data-ttu-id="404ed-110">Dit veld wordt gedefinieerd **die** kunt doen **wat** op dit eindpunt.</span><span class="sxs-lookup"><span data-stu-id="404ed-110">This field defines **who** can do **what** on this endpoint.</span></span>   <span data-ttu-id="404ed-111">Rolmogelijkheden zijn speciale bestanden die binnenkort worden beschreven.</span><span class="sxs-lookup"><span data-stu-id="404ed-111">Role Capabilities are special files that will be explained shortly.</span></span>


<span data-ttu-id="404ed-112">Het veld RoleDefinitions wordt gedefinieerd welke groepen heeft toegang tot de mogelijkheden van welke rol.</span><span class="sxs-lookup"><span data-stu-id="404ed-112">The RoleDefinitions field defines which groups had access to which Role Capabilities.</span></span>  <span data-ttu-id="404ed-113">De mogelijkheid van een rol is een bestand dat u een verscheidenheid aan functies die worden weergegeven definieert voor het koppelen van gebruikers.</span><span class="sxs-lookup"><span data-stu-id="404ed-113">A Role Capability is a file that defines a set of capabilities that will be exposed to connecting users.</span></span>  <span data-ttu-id="404ed-114">Rolmogelijkheden met kunt u de **New-PSRoleCapabilityFile** opdracht.</span><span class="sxs-lookup"><span data-stu-id="404ed-114">You can create Role Capabilities with the **New-PSRoleCapabilityFile** command.</span></span>

```powershell
New-PSRoleCapabilityFile -Path "$env:ProgramFiles\WindowsPowerShell\Modules\DemoModule\RoleCapabilities\Maintenance.psrc"
```

<span data-ttu-id="404ed-115">Dit genereert een sjabloon voor rol-functie die er als uitzien volgt:</span><span class="sxs-lookup"><span data-stu-id="404ed-115">This will generate a template role capability that looks like this:</span></span>
```
@{

# ID used to uniquely identify this document
GUID = '9287a34f-3f0e-4fbe-9dd7-f1361ba9fd65'

# Author of this document
Author = 'Administrator'

# Description of the functionality provided by these settings
# Description = ''

# Company associated with this document
CompanyName = 'Unknown'

# Copyright statement for this document
Copyright = '(c) 2015 Administrator. All rights reserved.'

# Modules to import when applied to a session
# ModulesToImport = 'MyCustomModule', @{ ModuleName = 'MyCustomModule'; ModuleVersion = '1.0.0.0'; GUID = '4d30d5f0-cb16-4898-812d-f20a6c596bdf' }

# Aliases to make visible when applied to a session
# VisibleAliases = 'Item1', 'Item2'

# Cmdlets to make visible when applied to a session
# VisibleCmdlets = 'Invoke-Cmdlet1', @{ Name = 'Invoke-Cmdlet2'; Parameters = @{ Name = 'Parameter1'; ValidateSet = 'Item1', 'Item2' }, @{ Name = 'Parameter2'; ValidatePattern = 'L*' } }

# Functions to make visible when applied to a session
# VisibleFunctions = 'Invoke-Function1', @{ Name = 'Invoke-Function2'; Parameters = @{ Name = 'Parameter1'; ValidateSet = 'Item1', 'Item2' }, @{ Name = 'Parameter2'; ValidatePattern = 'L*' } }

# External commands (scripts and applications) to make visible when applied to a session
# VisibleExternalCommands = 'Item1', 'Item2'

# Providers to make visible when applied to a session
# VisibleProviders = 'Item1', 'Item2'

# Scripts to run when applied to a session
# ScriptsToProcess = 'C:\ConfigData\InitScript1.ps1', 'C:\ConfigData\InitScript2.ps1'

# Aliases to be defined when applied to a session
# AliasDefinitions = @{ Name = 'Alias1'; Value = 'Invoke-Alias1'}, @{ Name = 'Alias2'; Value = 'Invoke-Alias2'}

# Functions to define when applied to a session
# FunctionDefinitions = @{ Name = 'MyFunction'; ScriptBlock = { param($MyInput) $MyInput } }

# Variables to define when applied to a session
# VariableDefinitions = @{ Name = 'Variable1'; Value = { 'Dynamic' + 'InitialValue' } }, @{ Name = 'Variable2'; Value = 'StaticInitialValue' }

# Environment variables to define when applied to a session
# EnvironmentVariables = @{ Variable1 = 'Value1'; Variable2 = 'Value2' }

# Type files (.ps1xml) to load when applied to a session
# TypesToProcess = 'C:\ConfigData\MyTypes.ps1xml', 'C:\ConfigData\OtherTypes.ps1xml'

# Format files (.ps1xml) to load when applied to a session
# FormatsToProcess = 'C:\ConfigData\MyFormats.ps1xml', 'C:\ConfigData\OtherFormats.ps1xml'

# Assemblies to load when applied to a session
# AssembliesToLoad = 'System.Web', 'System.OtherAssembly, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a'

}
```

<span data-ttu-id="404ed-116">Om te worden gebruikt door een sessieconfiguratie JEA, moet de Rolmogelijkheden worden opgeslagen als een geldige PowerShell-module in een map met de naam 'RoleCapabilities'.</span><span class="sxs-lookup"><span data-stu-id="404ed-116">To be used by a JEA session configuration, Role Capabilities must be saved as a valid PowerShell module in a directory named “RoleCapabilities”.</span></span> <span data-ttu-id="404ed-117">Een module mogelijk meerdere rol mogelijkheid bestanden, indien gewenst.</span><span class="sxs-lookup"><span data-stu-id="404ed-117">A module may have multiple role capability files, if desired.</span></span>

<span data-ttu-id="404ed-118">Om te beginnen met de configuratie van welke cmdlets, functies, aliassen en scripts die een gebruiker toegang heeft tot bij het verbinden met een JEA-sessie, moet u uw eigen regels toevoegen aan de rol mogelijkheid bestand na de opmerkingen van sjablonen.</span><span class="sxs-lookup"><span data-stu-id="404ed-118">To start configuring which cmdlets, functions, aliases, and scripts a user may access when connecting to a JEA session, add your own rules to the Role Capability file following the commented out templates.</span></span> <span data-ttu-id="404ed-119">Voor een stil in hoe u Rolmogelijkheden kunt configureren, bekijkt u de volledige [gids voor gebruikerservaring](http://aka.ms/JEA).</span><span class="sxs-lookup"><span data-stu-id="404ed-119">For a deeper look into how you can configure Role Capabilities, check out the full [experience guide](http://aka.ms/JEA).</span></span>

<span data-ttu-id="404ed-120">Tot slot zodra u klaar bent met het aanpassen van de sessieconfiguratie en aanverwante mogelijkheden van de rol, registreren van deze sessieconfiguratie en het eindpunt maken door te voeren **Register-PSSessionConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="404ed-120">Finally, once you have finished customizing your session configuration and related Role Capabilities, register this session configuration and create the endpoint by running **Register-PSSessionConfiguration**.</span></span>

```powershell
Register-PSSessionConfiguration -Name Maintenance -Path "C:\ProgramData\JEAConfiguration\Demo.pssc"
```

## <a name="connect-to-a-jea-endpoint"></a><span data-ttu-id="404ed-121">Verbinding maken met een JEA-eindpunt</span><span class="sxs-lookup"><span data-stu-id="404ed-121">Connect to a JEA Endpoint</span></span>

<span data-ttu-id="404ed-122">Verbinding maken met een JEA-eindpunt werkt op dezelfde manier verbinding te maken met een andere PowerShell-eindpunt werkt.</span><span class="sxs-lookup"><span data-stu-id="404ed-122">Connecting to a JEA Endpoint works the same way connecting to any other PowerShell endpoint works.</span></span>  <span data-ttu-id="404ed-123">U hoeft uw JEA-eindpunt om naam te geven als de parameter 'ConfigurationName' voor **New-PSSession**, **Invoke-Command**, of **Enter-PSSession**.</span><span class="sxs-lookup"><span data-stu-id="404ed-123">You simply have to give your JEA endpoint name as the “ConfigurationName” parameter for **New-PSSession**, **Invoke-Command**, or **Enter-PSSession**.</span></span>

```powershell
Enter-PSSession -ConfigurationName Maintenance -ComputerName localhost
```

<span data-ttu-id="404ed-124">Nadat u verbinding hebt gemaakt met de JEA-sessie, zich kunt u beperkt tot de opdrachten in de whitelist opgenomen in de rol-mogelijkheden die u toegang tot hebt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="404ed-124">Once you have connected to the JEA session, you will be limited to running the commands whitelisted in the Role Capabilities that you have access to.</span></span> <span data-ttu-id="404ed-125">Als u probeert een opdracht niet toegestaan voor uw rol uit te voeren, wordt u er een fout optreden.</span><span class="sxs-lookup"><span data-stu-id="404ed-125">If you try to run any command not allowed for your role, you will encounter an error.</span></span>