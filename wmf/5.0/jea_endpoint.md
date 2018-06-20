---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 66db78cfb136f22cad9078d7113dad085ee667a5
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188425"
---
# <a name="creating-and-connecting-to-a-jea-endpoint"></a>Een JEA-eindpunt maken en hier verbinding mee maken
Een JEA om eindpunt te maken, moet u maken en registreren van een speciaal geconfigureerde configuratie van de PowerShell-sessie-bestand dat kan worden gegenereerd met de **nieuw PSSessionConfigurationFile** cmdlet.

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -TranscriptDirectory "C:\ProgramData\JEATranscripts" -RunAsVirtualAccount -RoleDefinitions @{ 'CONTOSO\NonAdmin_Operators' = @{ RoleCapabilities = 'Maintenance' }} -Path "$env:ProgramData\JEAConfiguration\Demo.pssc"
```

Hiermee maakt u een sessie-configuratiebestand dat uitziet:
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
Wanneer u een eindpunt JEA maakt, moeten de volgende parameters van de opdracht (en de bijbehorende sleutels in het bestand) worden ingesteld:
1.  SessionType naar RestrictedRemoteServer
2.  RunAsVirtualAccount naar **$true**
3.  TranscriptPath naar de map waarin 'over de schouder' transcripties moeten worden opgeslagen na elke sessie
4.  RoleDefinitions naar een hashtabel die definieert welke groepen hebben toegang tot welke 'rol mogelijkheden'.  Dit veld wordt gedefinieerd **die** kunt doen **wat** op dit eindpunt.   Rol mogelijkheden zijn speciale bestanden die worden kort beschreven.


Het veld RoleDefinitions definieert welke groepen toegang had tot welke mogelijkheden rol.  De mogelijkheid van een rol is een bestand dat u een reeks mogelijkheden die zullen worden blootgesteld definieert voor het koppelen van gebruikers.  Kunt u mogelijkheden van rol met de **nieuw PSRoleCapabilityFile** opdracht.

```powershell
New-PSRoleCapabilityFile -Path "$env:ProgramFiles\WindowsPowerShell\Modules\DemoModule\RoleCapabilities\Maintenance.psrc"
```

Hierdoor wordt een sjabloon rol mogelijkheid ziet gegenereerd:
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
Om te worden gebruikt door een sessieconfiguratie JEA, moet de rol mogelijkheden worden opgeslagen als een geldige PowerShell-module in een map met de naam 'RoleCapabilities'. Een module mogelijk meerdere rol capability-bestanden, indien gewenst.

Als u wilt configureren welke cmdlets, functies, aliassen en scripts die een gebruiker toegang heeft tot bij het verbinden met een sessie JEA, uw eigen regels aan het rol mogelijkheid bestand toevoegen na de opmerkingen van sjablonen. Bekijk voor uitvoerig stil in hoe u de mogelijkheden van de rol kunt configureren, de volledige [handleiding ervaren](http://aka.ms/JEA).

Ten slotte zodra u klaar bent met het aanpassen van uw sessieconfiguratie en de gerelateerde rol mogelijkheden, registreren van deze sessieconfiguratie en het eindpunt te maken door te voeren **Register-PSSessionConfiguration**.

```powershell
Register-PSSessionConfiguration -Name Maintenance -Path "C:\ProgramData\JEAConfiguration\Demo.pssc"
```

## <a name="connect-to-a-jea-endpoint"></a>Verbinding maken met een eindpunt JEA
Verbinding maken met een eindpunt JEA werkt op dezelfde manier verbinding maken met een andere PowerShell eindpunt werkt.  Hoeft u alleen de naam van uw eindpunt JEA geven als de parameter 'ConfigurationName' voor **New-PSSession**, **Invoke-Command**, of **Enter-PSSession**.

```powershell
Enter-PSSession -ConfigurationName Maintenance -ComputerName localhost
```
Zodra u hebt gekoppeld aan de sessie JEA, kunt u zich beperkt tot de opdrachten wilt plaatsen in de rol mogelijkheden die u toegang tot hebt uitgevoerd. Als u probeert een opdracht is niet toegestaan voor uw rol uit te voeren, wordt er een fout optreden.
