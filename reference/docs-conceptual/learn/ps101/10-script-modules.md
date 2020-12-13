---
title: Scriptmodules
description: Script modules zijn een eenvoudige manier om scripts en functies te verpakken in een herbruikbaar hulp programma.
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 661ba725764e1f31df628f6c5f2d58d760656e37
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "84436510"
---
# <a name="chapter-10---script-modules"></a>Hoofd stuk 10: script modules

Het is nog belang rijker om uw one-Lines en scripts in Power shell in te scha kelen in herbruikbare Program ma's. Als u uw functies in een script module verdeelt, zien ze er professioneel uit en zijn ze gemakkelijker te delen.

## <a name="dot-sourcing-functions"></a>Dot-Sourcing functies

Iets wat we in het vorige hoofd stuk niet hebben gecommuniceerd, is de functie dot. Wanneer een functie in een script geen deel uitmaakt van een module, is de enige manier om deze in het geheugen te laden, het `.PS1` bestand dat wordt opgeslagen in te delen met een punt.

De volgende functie is opgeslagen als `Get-MrPSVersion.ps1` .

```powershell
function Get-MrPSVersion {
    $PSVersionTable
}
```

Wanneer u het script uitvoert, gebeurt er niets.

```powershell
.\Get-MrPSVersion.ps1
```

Als u probeert de functie aan te roepen, wordt een fout bericht gegenereerd.

```powershell
Get-MrPSVersion
```

```Output
Get-MrPSVersion : The term 'Get-MrPSVersion' is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or if a path
was included, verify that the path is correct and try again.
At line:1 char:1
+ Get-MrPSVersion
    + CategoryInfo          : ObjectNotFound: (Get-MrPSVersion:String) [], CommandNotFou
   ndException
    + FullyQualifiedErrorId : CommandNotFoundException

```

U kunt bepalen of functies in het geheugen worden geladen door te controleren of deze bestaan in de **functie** PSDrive.

```powershell
Get-ChildItem -Path Function:\Get-MrPSVersion
```

```Output
Get-ChildItem : Cannot find path 'Get-MrPSVersion' because it does not exist.
At line:1 char:1
+ Get-ChildItem -Path Function:\Get-MrPSVersion
    + CategoryInfo          : ObjectNotFound: (Get-MrPSVersion:String) [Get-ChildItem],
   ItemNotFoundException
    + FullyQualifiedErrorId : PathNotFound,Microsoft.PowerShell.Commands.GetChildItemCommand
```

Het probleem met het aanroepen van het script dat de functie bevat, is dat de functies worden geladen in het _script_ bereik. Wanneer het script is voltooid, wordt dat bereik verwijderd en wordt de functie Hiermee verwijderd.

De functie moet worden geladen in het _globale_ bereik. Dit kan worden bereikt door punt: het script dat de functie bevat. Het relatieve pad kan worden gebruikt.

```powershell
. .\Get-MrPSVersion.ps1
```

Het volledig gekwalificeerde pad kan ook worden gebruikt.

```powershell
. C:\Demo\Get-MrPSVersion.ps1
```

Als een deel van het pad wordt opgeslagen in een variabele, kan dit worden gecombineerd met de rest van het pad.
Er is geen reden om teken reeks koppeling te gebruiken om de variabele samen te voegen met de rest van het pad.

```powershell
$Path = 'C:\'
. $Path\Get-MrPSVersion.ps1
```

Wanneer ik de **functie** PSDrive Controleer, is de `Get-MrPSVersion` functie nu aanwezig.

```powershell
Get-ChildItem -Path Function:\Get-MrPSVersion
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Function        Get-MrPSVersion
```

## <a name="script-modules"></a>Script modules

Een script module in Power shell is een bestand met een of meer functies die als een bestand worden opgeslagen `.PSM1` in plaats van een `.PS1` bestand.

Hoe maak ik een script module? Waarschijnlijk raden we u aan een opdracht met de naam iets zoals `New-Module` . De veronderstelling is onjuist. Terwijl er een opdracht in Power shell wordt genoemd `New-Module` , wordt met deze opdracht een dynamische module gemaakt en niet een script module. Lees altijd de Help-informatie voor een opdracht, zelfs als u denkt dat u de gewenste opdracht hebt gevonden.

```powershell
help New-Module
```

```Output
NAME
    New-Module

SYNOPSIS
    Creates a new dynamic module that exists only in memory.

SYNTAX
    New-Module [-Name] <String> [-ScriptBlock] <ScriptBlock> [-ArgumentList <Object[]>]
    [-AsCustomObject] [-Cmdlet <String[]>] [-Function <String[]>] [-ReturnResult]
    [<CommonParameters>]

DESCRIPTION
    The New-Module cmdlet creates a dynamic module from a script block. The members of
    the dynamic module, such as functions and variables, are immediately available in
    the session and remain available until you close the session.

    Like static modules, by default, the cmdlets and functions in a dynamic module are
    exported and the variables and aliases are not. However, you can use the
    Export-ModuleMember cmdlet and the parameters of New-Module to override the defaults.

    You can also use the AsCustomObject parameter of New-Module to return the dynamic
    module as a custom object. The members of the modules, such as functions, are
    implemented as script methods of the custom object instead of being imported into
    the session.

    Dynamic modules exist only in memory, not on disk. Like all modules, the members of
    dynamic modules run in a private module scope that is a child of the global scope.
    Get-Module cannot get a dynamic module, but Get-Command can get the exported members.

    To make a dynamic module available to Get-Module , pipe a New-Module command to
    Import-Module, or pipe the module object that New-Module returns to Import-Module .
    This action adds the dynamic module to the Get-Module list, but it does not save the
    module to disk or make it persistent.

RELATED LINKS
    Online Version: http://go.microsoft.com/fwlink/?LinkId=821495
    Export-ModuleMember
    Get-Module
    Import-Module
    Remove-Module

REMARKS
    To see the examples, type: "get-help New-Module -examples".
    For more information, type: "get-help New-Module -detailed".
    For technical information, type: "get-help New-Module -full".
    For online help, type: "get-help New-Module -online"
```

In het vorige hoofd stuk werd vermeld dat de functies goedgekeurde werk woorden moeten gebruiken, anders wordt er een waarschuwings bericht gegenereerd wanneer de module wordt geïmporteerd. De volgende code gebruikt de `New-Module` cmdlet om een dynamische module in het geheugen te maken. In deze module wordt de waarschuwing over een niet-goedgekeurde term gedemonstreerd.

```powershell
New-Module -Name MyModule -ScriptBlock {

    function Return-MrOsVersion {
        Get-CimInstance -ClassName Win32_OperatingSystem |
        Select-Object -Property @{label='OperatingSystem';expression={$_.Caption}}
    }

    Export-ModuleMember -Function Return-MrOsVersion

} | Import-Module
```

```Output
WARNING: The names of some imported commands from the module 'MyModule' include
unapproved verbs that might make them less discoverable. To find the commands with
unapproved verbs, run the Import-Module command again with the Verbose parameter. For a
list of approved verbs, type Get-Verb.
```

Net als `New-Module` in het vorige voor beeld, is dat niet de opdracht voor het maken van script modules in Power shell.

Sla de volgende twee functies op in een bestand met de naam `MyScriptModule.psm1` .

```powershell
function Get-MrPSVersion {
    $PSVersionTable
}

function Get-MrComputerName {
    $env:COMPUTERNAME
}
```

Probeer een van de functies aan te roepen.

```powershell
Get-MrComputerName
```

```Output
Get-MrComputerName : The term 'Get-MrComputerName' is not recognized as the name of a
cmdlet, function, script file, or operable program. Check the spelling of the name, or
if a path was included, verify that the path is correct and try again.
At line:1 char:1
+ Get-MrComputerName
    + CategoryInfo          : ObjectNotFound: (Get-MrComputerName:String) [], CommandNot
   FoundException
    + FullyQualifiedErrorId : CommandNotFoundException
```

Er wordt een fout bericht gegenereerd met de melding dat de functie niet kan worden gevonden. U kunt ook de **functie** PSDrive controleren, net zoals eerder, en u zult zien dat deze niet aanwezig is.

U kunt het bestand hand matig met de `Import-Module` cmdlet importeren.

```powershell
Import-Module C:\MyScriptModule.psm1
```

De functie voor het autoladen van module is geïntroduceerd in Power shell versie 3. Een script module moet worden opgeslagen in een map met dezelfde basis naam als het `.PSM1` bestand en op een locatie die is opgegeven in om te profiteren van het autoloaden van module `$env:PSModulePath` .

```powershell
$env:PSModulePath
```

```Output
C:\Users\mike-ladm\Documents\WindowsPowerShell\Modules;C:\Program Files\WindowsPowerShell\
Modules;C:\Windows\system32\WindowsPowerShell\v1.0\Modules;C:\Program Files (x86)\Microsof
t SQL Server\130\Tools\PowerShell\Modules\
```

De resultaten zijn moeilijk te lezen. Aangezien de paden worden gescheiden door een punt komma, kunt u de resultaten splitsen om elk pad op een afzonderlijke regel te retour neren. Dit maakt het gemakkelijker om ze te lezen.

```powershell
$env:PSModulePath -split ';'
```

```Output
C:\Users\mike-ladm\Documents\WindowsPowerShell\Modules
C:\Program Files\WindowsPowerShell\Modules
C:\Windows\system32\WindowsPowerShell\v1.0\Modules
C:\Program Files (x86)\Microsoft SQL Server\130\Tools\PowerShell\Modules\
```

De eerste drie paden in de lijst zijn de standaard waarden. Als SQL Server Management Studio is geïnstalleerd, is het laatste pad toegevoegd. Als u de module autoloading wilt gebruiken, `MyScriptModule.psm1` moet het bestand zich bevinden in een map met de naam `MyScriptModule` direct in een van deze paden.

Niet zo snel. Voor mij is mijn huidige gebruikers pad niet de eerste in de lijst. Ik gebruik dit pad bijna nooit omdat ik me bij Windows aanmeld met een andere gebruiker dan het account dat ik gebruik om Power shell uit te voeren. Dit betekent dat het zich niet in de map normale documenten bevindt.

Het tweede pad is het **ALLUSERS** -pad. Dit is de locatie waar ik al mijn modules Bewaar.

Het derde pad staat eronder `C:\Windows\System32` . Alleen micro soft moet modules op die locatie opslaan, omdat deze zich in de map besturings systeem bevindt.

Zodra het `.PSM1` bestand zich in het juiste pad bevindt, wordt de module automatisch geladen wanneer een van de opdrachten wordt genoemd.

## <a name="module-manifests"></a>Module manifesten

Alle modules moeten een module manifest hebben. Een module manifest bevat meta gegevens over uw module.
De bestands extensie voor een manifest bestand van de module is `.PSD1` . Niet alle bestanden met een `.PSD1` extensie zijn module manifesten. Ze kunnen ook worden gebruikt voor zaken zoals het opslaan van het onderdeel van een DSC-configuratie. `New-ModuleManifest` wordt gebruikt om een module manifest te maken. Het **pad** is de enige vereiste waarde. De module werkt echter niet als **RootModule** niet is opgegeven. Het is een goed idee om de **Auteur** en **Beschrijving** op te geven voor het geval u besluit uw module te uploaden naar een NuGet-opslag plaats met PowerShellGet, omdat deze waarden in dat scenario zijn vereist.

De versie van een module zonder manifest is 0,0. Dit is een Dead-Giveaway dat de module geen manifest heeft.

```powershell
Get-Module -Name MyScriptModule
```

```Output
ModuleType Version    Name                                ExportedCommands
---------- -------    ----                                ----------------
Script     0.0        myscriptmodule                      {Get-MrComputerName, Get-MrP...
```

Het module manifest kan worden gemaakt met alle aanbevolen informatie.

```powershell
New-ModuleManifest -Path $env:ProgramFiles\WindowsPowerShell\Modules\MyScriptModule\MyScriptModule.psd1 -RootModule MyScriptModule -Author 'Mike F Robbins' -Description 'MyScriptModule' -CompanyName 'mikefrobbins.com'
```

Als een van deze gegevens wordt gemist tijdens het maken van de eerste keer dat het module manifest wordt gemaakt, kan het worden toegevoegd of later worden bijgewerkt met `Update-ModuleManifest` . Maak het manifest niet opnieuw met behulp `New-ModuleManifest` van zodra het al is gemaakt, omdat de GUID verandert.

## <a name="defining-public-and-private-functions"></a>Open bare en persoonlijke functies definiëren

Mogelijk hebt u hulp functies die u mogelijk persoonlijk wilt maken en alleen toegankelijk zijn voor andere functies in de module. Ze zijn niet bedoeld om toegankelijk te zijn voor gebruikers van uw module. Er zijn een aantal verschillende manieren om dit te bereiken.

Als u niet de aanbevolen procedures volgt en alleen een bestand hebt `.PSM1` , kunt u de cmdlet alleen gebruiken `Export-ModuleMember` .

```powershell
function Get-MrPSVersion {
    $PSVersionTable
}

function Get-MrComputerName {
    $env:COMPUTERNAME
}

Export-ModuleMember -Function Get-MrPSVersion
```

In het vorige voor beeld is alleen de `Get-MrPSVersion` functie beschikbaar voor de gebruikers van uw module, maar de `Get-MrComputerName` functie is beschikbaar voor andere functies in de module zelf.

```powershell
Get-Command -Module MyScriptModule

CommandType     Name                        Version    Source
-----------     ----                        -------    ------
Function        Get-MrPSVersion             1.0        MyScript...
```

Als u een module manifest hebt toegevoegd aan uw module (en dit moet u wel doen), raden we u aan om de afzonderlijke functies op te geven die u wilt exporteren in de sectie **FunctionsToExport** van het module manifest.

```powershell
FunctionsToExport = 'Get-MrPSVersion'
```

Het is niet nodig om zowel `Export-ModuleMember` in het `.PSM1` bestand als in het gedeelte **FunctionsToExport** van het module manifest te gebruiken. De ene of de andere is voldoende.

## <a name="summary"></a>Samenvatting

In dit hoofd stuk hebt u geleerd hoe u uw functies kunt omzetten in een script module in Power shell. Daarnaast hebt u een aantal aanbevolen procedures voor het maken van script modules, zoals het maken van een module manifest voor uw script module, gelean.

## <a name="review"></a>Beoordelen

1. Hoe maak ik een script module in Power shell?
1. Waarom is het belang rijk dat uw functies een goedgekeurde term gebruiken?
1. Hoe maak ik een module manifest in Power shell?
1. Wat zijn de twee opties voor het exporteren van alleen bepaalde functies uit uw module?
1. Wat is er nodig om uw modules automatisch te laden wanneer een opdracht wordt aangeroepen?

## <a name="recommended-reading"></a>Aanbevolen Lees bewerkingen

- [Power shell-script modules en module manifesten maken][]
- [about_Modules][]
- [New-ModuleManifest][]
- [Exporteren-ModuleMember][]

<!-- link references -->
[Power shell-script modules en module manifesten maken]: https://mikefrobbins.com/2013/07/04/how-to-create-powershell-script-modules-and-module-manifests/
[about_Modules]: /powershell/module/microsoft.powershell.core/about/about_modules
[New-ModuleManifest]: /powershell/module/microsoft.powershell.core/new-modulemanifest
[Exporteren-ModuleMember]: /powershell/module/microsoft.powershell.core/export-modulemember
