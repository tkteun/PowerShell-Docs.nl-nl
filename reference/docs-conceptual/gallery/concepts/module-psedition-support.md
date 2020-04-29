---
ms.date: 03/28/2019
contributor: manikb
keywords: Galerie, Power shell, cmdlet, psget
title: Modules met compatibele Power shell-edities
ms.openlocfilehash: 425588c168a4f864fdc0c52aa53cfd748b80dc98
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "71329188"
---
# <a name="modules-with-compatible-powershell-editions"></a>Modules met compatibele Power shell-edities

Vanaf versie 5.1 is PowerShell beschikbaar in verschillende edities die staan voor verschillende functies en platformcompatibiliteit.

- **Desktop Edition:** Gebaseerd op .NET Framework, is van toepassing op Windows Power shell v 4.0 en hieronder, evenals Windows Power shell 5,1 op Windows Desktop, Windows Server, Windows Server Core en de meeste andere Windows-edities.
- **Core-editie:** Gebaseerd op .NET core, is van toepassing op Power shell Core 6,0 en hoger, evenals Windows Power shell 5,1 op Windows-edities met verminderde footprint, zoals Windows IoT en Windows nano server.

Zie [about_PowerShell_Editions][]voor meer informatie over Power shell-edities.

## <a name="declaring-compatible-editions"></a>Compatibele edities declareren

Auteurs van modules kunnen hun modules zo opstellen dat deze compatibel zijn met een of meer PowerShell-edities door de sleutel voor het modulemanifestbestand CompatiblePSEditions te gebruiken. Deze sleutel wordt alleen ondersteund in PowerShell 5.1 of hoger.

> [!NOTE]
> Zodra een module manifest is opgegeven met de CompatiblePSEditions-sleutel, kan het niet worden geïmporteerd in Power shell-versie 4 en lager.

```powershell
New-ModuleManifest -Path .\TestModuleWithEdition.psd1 -CompatiblePSEditions Desktop,Core -PowerShellVersion 5.1
$ModuleInfo = Test-ModuleManifest -Path .\TestModuleWithEdition.psd1
$ModuleInfo.CompatiblePSEditions
```

```Output
Desktop
Core
```

```powershell
$ModuleInfo | Get-Member CompatiblePSEditions
```

```Output
   TypeName: System.Management.Automation.PSModuleInfo

Name                 MemberType Definition
----                 ---------- ----------
CompatiblePSEditions Property   System.Collections.Generic.IEnumerable[string] CompatiblePSEditions {get;}
```

Bij het ophalen van een lijst met beschikbare modules kunt u de lijst filteren op PowerShell-editie.

```powershell
Get-Module -ListAvailable -PSEdition Desktop
```

```Output
    Directory: C:\Program Files\WindowsPowerShell\Modules


ModuleType Version    Name                                ExportedCommands
---------- -------    ----                                ----------------
Manifest   1.0        ModuleWithPSEditions
```

```powershell
Get-Module -ListAvailable -PSEdition Core | % CompatiblePSEditions
```

```Output
Desktop
Core
```

## <a name="targeting-multiple-editions"></a>Meerdere edities richten

Ontwerpers van modules kunnen één module richten op een of beide Power shell-edities (desktop en Core).

Eén module kan zowel op bureau blad-als op kern-edities worden uitgevoerd. in die module auteur moet de vereiste logica worden toegevoegd in RootModule of in het manifest module met $PSEdition variabele. Modules kunnen twee sets gecompileerde Dll's hebben die zijn gericht op zowel CoreCLR als FullCLR. Hier vindt u een aantal opties voor het inpakken van uw module met logica voor het laden van de juiste dll's.

### <a name="option-1-packaging-a-module-for-targeting-multiple-versions-and-multiple-editions-of-powershell"></a>Optie 1: een module verpakken voor het richten op meerdere versies en meerdere versies van Power shell

Inhoud van module map

- Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll
- Microsoft.Windows.PowerShell.ScriptAnalyzer.dll
- PSScriptAnalyzer.psd1
- PSScriptAnalyzer.psm1
- ScriptAnalyzer. Format. ps1xml
- ScriptAnalyzer.types.ps1xml
- coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll
- coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll
- en-US\about_PSScriptAnalyzer.help.txt
- en-US\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll-Help.xml
- PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll
- PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll
- Settings\CmdletDesign.psd1
- Settings\DSC.psd1
- Settings\ScriptFunctions.psd1
- Settings\ScriptingStyle.psd1
- Settings\ScriptSecurity.psd1

Inhoud van het bestand PSScriptAnalyzer. psd1

```powershell
@{

# Author of this module
Author = 'Microsoft Corporation'

# Script module or binary module file associated with this manifest.
RootModule = 'PSScriptAnalyzer.psm1'

# Version number of this module.
ModuleVersion = '1.6.1'

# ---
}
```

Onder Logic worden de vereiste assembly's geladen, afhankelijk van de huidige editie of versie.

Inhoud van het bestand PSScriptAnalyzer. psm1:

```powershell
#
# Script module for module 'PSScriptAnalyzer'
#
Set-StrictMode -Version Latest

# Set up some helper variables to make it easier to work with the module
$PSModule = $ExecutionContext.SessionState.Module
$PSModuleRoot = $PSModule.ModuleBase

# Import the appropriate nested binary module based on the current PowerShell version
$binaryModuleRoot = $PSModuleRoot


if (($PSVersionTable.Keys -contains "PSEdition") -and ($PSVersionTable.PSEdition -ne 'Desktop')) {
    $binaryModuleRoot = Join-Path -Path $PSModuleRoot -ChildPath 'coreclr'
}
else
{
    if ($PSVersionTable.PSVersion -lt [Version]'5.0')
    {
        $binaryModuleRoot = Join-Path -Path $PSModuleRoot -ChildPath 'PSv3'
    }
}

$binaryModulePath = Join-Path -Path $binaryModuleRoot -ChildPath 'Microsoft.Windows.PowerShell.ScriptAnalyzer.dll'
$binaryModule = Import-Module -Name $binaryModulePath -PassThru

# When the module is unloaded, remove the nested binary module that was loaded with it
$PSModule.OnRemove = {
    Remove-Module -ModuleInfo $binaryModule
}
```

### <a name="option-2-use-psedition-variable-in-the-psd1-file-to-load-the-proper-dlls-and-nestedrequired-modules"></a>Optie 2: gebruik $PSEdition variabele in het PSD1-bestand om de juiste Dll's en geneste/vereiste modules te laden

In PS 5,1 of hoger is $PSEdition globale variabele toegestaan in het manifest bestand van de module. Met deze variabele kan module Author de voorwaardelijke waarden opgeven in het manifest bestand van de module. Naar $PSEdition-variabele kan worden verwezen in de modus voor beperkte talen of in een gegevens gedeelte.

> [!NOTE]
> Zodra een module manifest is opgegeven met de sleutel CompatiblePSEditions of de `$PSEdition` variabele gebruikt, kan het niet worden geïmporteerd in lagere versies van Power shell.

Voor beeld van module manifest bestand met CompatiblePSEditions-sleutel

```powershell
@{
    # Script module or binary module file associated with this manifest.
    RootModule = if($PSEdition -eq 'Core')
    {
        'coreclr\MyCoreClrRM.dll'
    }
    else # Desktop
    {
        'clr\MyFullClrRM.dll'
    }

    # Supported PSEditions
    CompatiblePSEditions = 'Desktop', 'Core'

    # Modules to import as nested modules of the module specified in RootModule/ModuleToProcess
    NestedModules = if($PSEdition -eq 'Core')
    {
        'coreclr\MyCoreClrNM1.dll',
        'coreclr\MyCoreClrNM2.dll'
    }
    else # Desktop
    {
        'clr\MyFullClrNM1.dll',
        'clr\MyFullClrNM2.dll'
    }
}
```

### <a name="module-contents"></a>Inhoud van module

```powershell
dir -Recurse
```

```Output
    Directory: C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions

Mode           LastWriteTime   Length Name
----           -------------   ------ ----
d-----    7/5/2016   1:37 PM          clr
d-----    7/5/2016   1:36 PM          coreclr
-a----    7/5/2016   1:34 PM     4906 ModuleWithEditions.psd1

    Directory: C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions\clr

Mode           LastWriteTime    Length Name
----           -------------    ------ ----
-a----    7/5/2016   1:35 PM         0 MyFullClrNM1.dll
-a----    7/5/2016   1:35 PM         0 MyFullClrNM2.dll
-a----    7/5/2016   1:35 PM         0 MyFullClrRM.dl

    Directory: C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions\coreclr

Mode           LastWriteTime   Length Name
----           -------------   ------ ----
-a----    7/5/2016   1:35 PM        0 MyCoreClrNM1.dll
-a----    7/5/2016   1:35 PM        0 MyCoreClrNM2.dll
-a----    7/5/2016   1:35 PM        0 MyCoreClrRM.dl
```

PowerShell Gallery gebruikers kunnen de lijst met modules die worden ondersteund in een specifieke Power shell-editie vinden met behulp van labels PSEdition_Desktop en PSEdition_Core.

Modules zonder PSEdition_Desktop en PSEdition_Core-Tags worden beschouwd als goed op Power shell-Desktop-edities.

```powershell
# Find modules supported on PowerShell Desktop edition
Find-Module -Tag PSEdition_Desktop

# Find modules supported on PowerShell Core editions
Find-Module -Tag PSEdition_Core
```

## <a name="more-details"></a>Meer informatie

[Scripts met PSEditions](script-psedition-support.md)

[PSEditions-ondersteuning op PowerShellGallery](../how-to/finding-packages/searching-by-compatibility.md)

[Modulemanifest bijwerken](/powershell/module/powershellget/update-modulemanifest)

[about_PowerShell_Editions][]

[about_PowerShell_Editions]: /powershell/module/Microsoft.PowerShell.Core/About/about_PowerShell_Editions
