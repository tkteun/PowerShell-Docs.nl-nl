---
description: Verschillende versies van Power shell die worden uitgevoerd op verschillende onderliggende Runtimes.
Locale: en-US
ms.date: 03/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_powershell_editions?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PowerShell_Editions
ms.openlocfilehash: c4ff0bce0ddffb78d3328bffdb34d7f98abee86b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252700"
---
# <a name="about-powershell-editions"></a>Over Power shell-edities

## <a name="short-description"></a>Korte beschrijving
Verschillende versies van Power shell die worden uitgevoerd op verschillende onderliggende Runtimes.

## <a name="long-description"></a>Lange beschrijving

Vanuit Power shell 5,1 zijn er meerdere *versies* van Power shell die elk worden uitgevoerd op een andere .NET-runtime. Vanaf Power shell 6,2 zijn er twee versies van Power shell:

- **Bureau blad** , dat wordt uitgevoerd op .NET Framework. Power Shell 4 en lager, en Power shell 5,1 op volledig uitgeruste Windows-edities zoals Windows Desktop, Windows Server, Windows Server Core en de meeste andere Windows-besturings systemen zijn Desktop Edition.
  Dit is de oorspronkelijke Power shell-editie.
- **Core** , die wordt uitgevoerd op .net core. Power shell 6,0 en hoger, evenals Power shell 5,1 op sommige Windows-edities met een verminderde footprint, zoals Windows nano server en Windows IoT, waarbij .NET Framework niet beschikbaar is.

Omdat de editie van Power shell overeenkomt met de .NET runtime, is het de primaire indicator van de compatibiliteit van .NET API en Power shell-modules. Sommige .NET-Api's,-typen of-methoden zijn niet beschikbaar in .NET-Runtimes en zijn van invloed op Power shell-scripts en-modules die hiervan afhankelijk zijn.

## <a name="the-psedition-automatic-variable"></a>De `$PSEdition` Automatische variabele

In Power shell 5,1 en hoger kunt u zien welke editie u uitvoert met de `$PSEdition` Automatische variabele:

```powershell
$PSEdition
```

```Output
Core
```

Deze variabele bestaat niet in Power Shell 4 en lager. `$PSEdition` Null moet worden behandeld als gelijk aan de waarde `Desktop` .

### <a name="edition-in-psversiontable"></a>Edition in `$PSVersionTable`

De `$PSVersionTable` Automatische variabele bevat ook editie-informatie in Power shell 5,1 en hoger:

```powershell
$PSVersionTable
```

```Output
Name                           Value
----                           -----
PSVersion                      6.2.0-rc.1
PSEdition                      Core           # <-- Edition information
GitCommitId                    6.2.0-rc.1
OS                             Microsoft Windows 10.0.18865
Platform                       Win32NT
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
PSRemotingProtocolVersion      2.3
SerializationVersion           1.1.0.1
WSManStackVersion              3.0
```

Het `PSEdition` veld heeft dezelfde waarde als de `$PSEdition` Automatische variabele.

## <a name="the-compatiblepseditions-module-manifest-field"></a>Het `CompatiblePSEditions` veld module manifest

Power shell-modules kunnen declareren in welke versies van Power shell ze compatibel zijn met behulp `CompatiblePSEditions` van het veld van het module manifest.

Een module manifest dat bijvoorbeeld compatibiliteit met zowel-als- `Desktop` `Core` edities van Power shell declareert:

```powershell
@{
    ModuleVersion = '1.0'
    FunctionsToExport = @('Test-MyModule')
    CompatiblePSEditions = @('Desktop', 'Core')
}
```

Een voor beeld van een module manifest met alleen `Desktop` Compatibiliteit:

```powershell
@{
    ModuleVersion = '1.0'
    FunctionsToExport = @('Test-MyModule')
    CompatiblePSEditions = @('Desktop')
}
```

Het weglaten `CompatiblePSEditions` van het veld uit een module manifest heeft hetzelfde effect als het instellen op `Desktop` , omdat modules die zijn gemaakt voordat dit veld werd geïntroduceerd, impliciet werden geschreven voor deze editie.

Voor modules die niet worden geleverd als onderdeel van Windows (modules die u schrijft of installeert vanuit de galerie), is dit veld alleen ter informatie. Power shell verandert geen gedrag op basis van het `CompatiblePSEditions` veld, maar maakt het op het `PSModuleInfo` object zichtbaar (geretourneerd door `Get-Module` ) voor uw eigen logica:

```powershell
New-ModuleManifest -Path .\TestModuleWithEdition.psd1 -CompatiblePSEditions Desktop,Core -PowerShellVersion '5.1'
$ModuleInfo = Test-ModuleManifest -Path .\TestModuleWithEdition.psd1
$ModuleInfo.CompatiblePSEditions
```

```Output
Desktop
Core
```

> [!NOTE]
> Het `CompatiblePSEditions` module veld is alleen compatibel met Power shell 5,1 en hoger.
> Met inbegrip van dit veld wordt een module niet compatibel met Power Shell 4 en lager.
> Omdat het veld louter informatief is, kan het veilig worden wegge laten in latere Power shell-versies.

In Power shell 6,1 `Get-Module -ListAvailable` heeft de indelings functie bijgewerkt om de editie-compatibiliteit van elke module weer te geven:

```PowerShell
Get-Module -ListAvailable
```

```Output

    Directory: C:\Users\me\Documents\PowerShell\Modules

ModuleType Version    Name                                PSEdition ExportedCommands
---------- -------    ----                                --------- ----------------
Script     1.4.0      Az                                  Core,Desk
Script     1.3.1      Az.Accounts                         Core,Desk {Disable-AzDataCollection, Disable-AzContextAutosave, E...
Script     1.0.1      Az.Aks                              Core,Desk {Get-AzAks, New-AzAks, Remove-AzAks, Import-AzAksCreden...

...

Script     4.4.0      Pester                              Desk      {Describe, Context, It, Should...}
Script     1.18.0     PSScriptAnalyzer                    Desk      {Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer, Invoke-...
Script     1.0.0      WindowsCompatibility                Core      {Initialize-WinSession, Add-WinFunction, Invoke-WinComm...

```

## <a name="edition-compatibility-for-modules-that-ship-as-part-of-windows"></a>Editie-compatibiliteit voor modules die worden geleverd als onderdeel van Windows

Voor modules die deel uitmaken van Windows (of die zijn geïnstalleerd als onderdeel van een functie of onderdeel), wordt het veld anders behandeld in Power shell 6,1 en hoger `CompatiblePSEditions` . Dergelijke modules vindt u in de Directory systeem modules van Windows Power shell ( `%windir%\System\WindowsPowerShell\v1.0\Modules` ).

Voor modules die zijn geladen vanuit of gevonden in deze map, gebruikt Power shell 6,1 en hoger het `CompatiblePSEditions` veld om te bepalen of de module compatibel is met de huidige sessie en zich dienovereenkomstig gedraagt.

Wanneer `Import-Module` wordt gebruikt, wordt een module zonder `Core` in `CompatiblePSEditions` niet geïmporteerd en wordt er een fout melding weer gegeven:

```powershell
Import-Module BitsTransfer
```

```Output
Import-Module : Module 'C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\BitsTransfer\BitsTransfer.psd1' does not support current PowerShell edition 'Core'. Its supported editions are 'Desktop'. Use 'Import-Module -SkipEditionCheck' to ignore the compatibility of this module.
At line:1 char:1
+ Import-Module BitsTransfer
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : ResourceUnavailable: (C:\WINDOWS\system32\u2026r\BitsTransfer.psd1:String) [Import-Module], InvalidOperationException
+ FullyQualifiedErrorId : Modules_PSEditionNotSupported,Microsoft.PowerShell.Commands.ImportModuleCommand
```

Als `Get-Module -ListAvailable` wordt gebruikt, worden modules zonder `Core` in `CompatiblePSEditions` niet weer gegeven:

```powershell
Get-Module -ListAvailable BitsTransfer
```

```Output
# No output
```

In beide gevallen kan de `-SkipEditionCheck` para meter switch worden gebruikt om dit gedrag te negeren:

```powershell
Get-Module -ListAvailable -SkipEditionCheck BitsTransfer
```

```Output

    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                                PSEdition ExportedCommands
---------- -------    ----                                --------- ----------------
Manifest   2.0.0.0    BitsTransfer                        Desk      {Add-BitsFile, Complete-BitsTransfer, Get-BitsTransfer,...

```

> [!WARNING]
> `Import-Module -SkipEditionCheck` lijkt voor een module te slagen, maar het gebruik van die module voert het risico op een later tijdstip van compatibiliteit tegen problemen uit. terwijl het laden van de module in eerste instantie slaagt, kan een opdracht later een incompatibele API aanroepen en spon Taan mislukken.

## <a name="authoring-powershell-modules-for-edition-cross-compatibility"></a>Power shell-modules ontwerpen voor compatibiliteit tussen versies

Wanneer u een Power shell-module schrijft om te richten op zowel `Desktop` `Core` -als-edities van Power shell, zijn er dingen die u kunt doen om compatibiliteit met meerdere edities te garanderen.

De enige manier om compatibiliteit te bevestigen en voortdurend te valideren is het schrijven van tests voor uw script of module, en het uitvoeren ervan op alle versies en edities van Power shell waarvoor u compatibiliteit nodig hebt. Een aanbevolen test raamwerk voor dit is een [ziekte][].

### <a name="powershell-script"></a>PowerShell-script

Power shell werkt als een taal hetzelfde tussen de edities. Dit zijn de cmdlets, modules en .NET-Api's die u gebruikt die worden beïnvloed door editie compatibiliteit.

Scripts die in Power shell 6,1 en hoger werken, werken meestal met Windows Power shell 5,1, maar er zijn enkele uitzonde ringen.

De module versie 1.18.0 [PSScriptAnalyzer][] bevat regels zoals [`PSUseCompatibleCommands`][] en [`PSUseCompatibleTypes`][] die mogelijk incompatibel gebruik van opdrachten en .net-api's in Power shell-scripts kunnen detecteren.

### <a name="net-assemblies"></a>.NET-assembly's

Als u een binaire module schrijft of een module die .NET-assembly's (Dll's) bevat die zijn gegenereerd op basis van de bron code, moet u zich compileren op basis van [.NET Standard][] en [Power shell Standard][] voor het valideren van de compatibiliteit van .net-en Power shell-API-compatibiliteit.

Hoewel deze bibliotheken tijdens de compilatie enige compatibiliteit kunnen controleren, kunnen ze geen mogelijke gedrags verschillen tussen de edities ondervangen. Voor dit moet u nog steeds tests schrijven.

## <a name="see-also"></a>Zie ook

- [about_Automatic_Variables](about_Automatic_Variables.md)
- [Import-module](xref:Microsoft.PowerShell.Core.Import-Module)
- [Get-module](xref:Microsoft.PowerShell.Core.Get-Module)
- [Modules met compatibele Power shell-edities](/powershell/scripting/gallery/concepts/module-psedition-support)

[Pester]: https://github.com/pester/Pester/wiki/Pester
[PSScriptAnalyzer]: https://github.com/PowerShell/PSScriptAnalyzer
['PSUseCompatibleCommands']: https://github.com/PowerShell/PSScriptAnalyzer/blob/master/RuleDocumentation/UseCompatibleCommands.md
['PSUseCompatibleTypes']: https://github.com/PowerShell/PSScriptAnalyzer/blob/master/RuleDocumentation/UseCompatibleTypes.md
[.NET Standard]: /dotnet/standard/net-standard
[Power Shell-standaard]: https://devblogs.microsoft.com/powershell/powershell-standard-library-build-single-module-that-works-across-windows-powershell-and-powershell-core/
