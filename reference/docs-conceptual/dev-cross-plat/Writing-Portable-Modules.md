---
ms.date: 10/21/2020
keywords: powershell,cmdlet
title: Draag bare modules schrijven
description: In dit artikel wordt uitgelegd hoe u nieuwe modules maakt of bestaande modules bijwerkt, zodat ze werken in de platforms die worden ondersteund door Power shell.
ms.openlocfilehash: 6d5c36263c3c6d1219f963cea2e94ae92b07e863
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500790"
---
# <a name="portable-modules"></a>Draag bare modules

Windows Power shell is geschreven voor [.NET Framework][] terwijl Power shell Core is geschreven voor [.net core][]. Draag bare modules zijn modules die in Windows Power shell en Power shell core werken. Hoewel .NET Framework en .NET core zeer compatibel zijn, zijn er verschillen in de beschik bare Api's tussen de twee. Er zijn ook verschillen in de Api's die beschikbaar zijn in Windows Power shell en Power shell core. Modules die in beide omgevingen moeten worden gebruikt, moeten op de hoogte zijn van deze verschillen.

## <a name="porting-an-existing-module"></a>Een bestaande module overbrengen

### <a name="porting-a-pssnapin"></a>Een PSSnapIn overbrengen

Power shell- [modules](/powershell/scripting/developer/cmdlet/modules-and-snap-ins) worden niet ondersteund in Power shell core. Het is echter een lastigere PSSnapIn te converteren naar een Power shell-module. De registratie code van de PSSnapIn bevindt zich doorgaans in één bron bestand van een klasse die is afgeleid van [PSSnapIn][]. Dit bron bestand verwijderen uit de build; het is niet meer nodig.

Gebruik [New-ModuleManifest][] om een nieuw module manifest te maken waarmee de PSSnapIn-registratie code moet worden vervangen. Sommige waarden van de **PSSnapIn** (zoals **Description**) kunnen opnieuw worden gebruikt binnen het module manifest.

De eigenschap **RootModule** in het manifest van de module moet worden ingesteld op de naam van de assembly (dll) die de cmdlets implementeert.

### <a name="the-net-portability-analyzer-aka-apiport"></a>De .NET-portabiliteit Analyzer (ook wel APIPort)

Als u poort modules hebt geschreven voor Windows Power shell voor gebruik met Power shell core, start u met de [.net-portabiliteit Analyzer][]. Voer dit hulp programma uit met de gecompileerde assembly om te bepalen of de .NET-Api's die in de module worden gebruikt, compatibel zijn met .NET Framework, .NET core en andere .NET-Runtimes. Het hulp programma stelt alternatieve Api's voor als deze bestaan. Als dat niet het geval is, moet u mogelijk [runtime controles][] toevoegen en de mogelijkheden beperken die niet beschikbaar zijn in specifieke Runtimes.

## <a name="creating-a-new-module"></a>Een nieuwe module maken

Als u een nieuwe module maakt, is de aanbeveling de [.net cli][]te gebruiken.

### <a name="installing-the-powershell-standard-module-template"></a>De sjabloon voor de Power Shell-standaard module installeren

Zodra .NET CLI is geïnstalleerd, installeert u een sjabloon bibliotheek voor het genereren van een eenvoudige Power shell-module.
De module is compatibel met Windows Power shell, Power shell core, Windows, Linux en macOS.

In het volgende voor beeld ziet u hoe u de sjabloon installeert:

```powershell
dotnet new -i Microsoft.PowerShell.Standard.Module.Template
```

```output
  Restoring packages for C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\restore.csproj...
  Installing Microsoft.PowerShell.Standard.Module.Template 0.1.3.
  Generating MSBuild file C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\obj\restore.csproj.nuget.g.props.
  Generating MSBuild file C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\obj\restore.csproj.nuget.g.targets.
  Restore completed in 1.66 sec for C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\restore.csproj.

Usage: new [options]

Options:
  -h, --help          Displays help for this command.
  -l, --list          Lists templates containing the specified name. If no name is specified, lists all templates.
  -n, --name          The name for the output being created. If no name is specified, the name of the current directory is used.
  -o, --output        Location to place the generated output.
  -i, --install       Installs a source or a template pack.
  -u, --uninstall     Uninstalls a source or a template pack.
  --nuget-source      Specifies a NuGet source to use during install.
  --type              Filters templates based on available types. Predefined values are "project", "item" or "other".
  --force             Forces content to be generated even if it would change existing files.
  -lang, --language   Filters templates based on language and specifies the language of the template to create.


Templates                        Short Name         Language          Tags
-----------------------------------------------------------------------------------------------
Console Application              console            [C#], F#, VB      Common/Console
Class library                    classlib           [C#], F#, VB      Common/Library
PowerShell Standard Module       psmodule           [C#]              Library/PowerShell/Module
...
```

### <a name="creating-a-new-module-project"></a>Een nieuw module project maken

Nadat de sjabloon is geïnstalleerd, kunt u een nieuw Power shell-module project maken op basis van deze sjabloon. In dit voor beeld wordt de voorbeeld module ' myModule ' genoemd.

```
PS> mkdir myModule

    Directory: C:\Users\Steve

Mode LastWriteTime Length Name
---- ------------- ------ ----
d----- 8/3/2018 2:41 PM myModule

PS> cd myModule
PS C:\Users\Steve\myModule> dotnet new psmodule

The template "PowerShell Standard Module" was created successfully.

Processing post-creation actions...
Running 'dotnet restore' on C:\Users\Steve\myModule\myModule.csproj...
  Restoring packages for C:\Users\Steve\myModule\myModule.csproj...
  Installing PowerShellStandard.Library 5.1.0.
  Generating MSBuild file C:\Users\Steve\myModule\obj\myModule.csproj.nuget.g.props.
  Generating MSBuild file C:\Users\Steve\myModule\obj\myModule.csproj.nuget.g.targets.
  Restore completed in 1.76 sec for C:\Users\Steve\myModule\myModule.csproj.

Restore succeeded.
```

### <a name="building-the-module"></a>De module bouwen

Gebruik de standaard .NET CLI-opdrachten om het project te bouwen.

```powershell
dotnet build
```

```output
PS C:\Users\Steve\myModule> dotnet build
Microsoft (R) Build Engine version 15.7.179.6572 for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 76.85 ms for C:\Users\Steve\myModule\myModule.csproj.
  myModule -> C:\Users\Steve\myModule\bin\Debug\netstandard2.0\myModule.dll

Build succeeded.
    0 Warning(s)
    0 Error(s)

Time Elapsed 00:00:05.40
```

### <a name="testing-the-module"></a>De module testen

Nadat u de module hebt gemaakt, kunt u deze importeren en de voor beeld-cmdlet uitvoeren.

```powershell
Import-Module .\bin\Debug\netstandard2.0\myModule.dll
Test-SampleCmdlet -?
Test-SampleCmdlet -FavoriteNumber 7 -FavoritePet Cat
```

```output
NAME
    Test-SampleCmdlet

SYNTAX
    Test-SampleCmdlet [-FavoriteNumber] <int> [[-FavoritePet] {Cat | Dog | Horse}] [<CommonParameters>]


ALIASES
    None


REMARKS
    None


FavoriteNumber FavoritePet
-------------- -----------
             7 Cat
```

### <a name="debugging-the-module"></a>Fout opsporing in de module

Zie [Visual Studio code gebruiken voor het opsporen van fouten in gecompileerde cmdlets][]voor een hand leiding voor het instellen van Visual Studio code voor het opsporen van fouten in de module.

## <a name="supporting-technologies"></a>Ondersteunende technologieën

In de volgende secties worden een aantal technologieën beschreven die worden gebruikt door deze sjabloon.

### <a name="net-standard-library"></a>.NET Standard-bibliotheek

[.NET Standard][] is een formele specificatie van .net-api's die beschikbaar zijn in alle .net-implementaties. Beheerde code doelen .NET Standard werkt met de .NET Framework-en .NET Core-versies die compatibel zijn met die versie van de .NET Standard.

> [!NOTE]
> Hoewel er in .NET Standard een API kan bestaan, kan de API-implementatie in .NET core een `PlatformNotSupportedException` tijdens runtime genereren, zodat u de compatibiliteit met Windows Power shell en Power shell Core kunt controleren. de best practice is om in beide omgevingen tests uit te voeren voor uw module.
> Voer ook tests uit op Linux en macOS als uw module geschikt is voor meerdere platforms.

Met behulp van .NET Standard kunt u ervoor zorgen dat bij het ontwikkelen van de module niet-compatibele Api's per ongeluk worden geïntroduceerd in de module. Incompatibiliteiten worden tijdens het compileren gedetecteerd in plaats van runtime.

Het is echter niet nodig om .NET Standard te richten op een module om te kunnen werken met Windows Power shell en Power shell core, zolang u compatibele Api's gebruikt. De tussen taal (IL) is compatibel tussen de twee Runtimes. U kunt .NET Framework 4.6.1 instellen, die compatibel is met .NET Standard 2,0. Als u geen Api's buiten .NET Standard 2,0 gebruikt, werkt uw module met Power shell Core 6 zonder opnieuw te compileren.

### <a name="powershell-standard-library"></a>Standaard bibliotheek van Power shell

De [standaard bibliotheek van Power shell][] is een formele specificatie van Power shell-api's die beschikbaar zijn in alle Power shell-versies die groter zijn dan of gelijk zijn aan de versie van die Standard.

[Power shell Standard 5,1][] is bijvoorbeeld compatibel met Windows power shell 5,1 en Power shell Core 6,0 of hoger.

U wordt aangeraden uw module te compileren met behulp van de standaard bibliotheek van Power shell. De tape wisselaar zorgt ervoor dat de Api's beschikbaar zijn en in Windows Power shell en Power shell Core 6 worden geïmplementeerd.
Power shell Standard is bedoeld om altijd compatibel te zijn. Een module die is gemaakt met behulp van de standaard bibliotheek 5,1 van Power shell is altijd compatibel met toekomstige versies van Power shell.

### <a name="module-manifest"></a>Module manifest

#### <a name="indicating-compatibility-with-windows-powershell-and-powershell-core"></a>Duidt op compatibiliteit met Windows Power shell en Power shell core

Nadat u hebt gecontroleerd of de module werkt met Windows Power shell en Power shell core, moet het module manifest expliciet duiden op compatibiliteit met behulp van de eigenschap [CompatiblePSEditions][] . Een waarde `Desktop` betekent dat de module compatibel is met Windows Power shell, terwijl een waarde `Core` betekent dat de module compatibel is met Power shell core. Inclusief beide `Desktop` en `Core` betekent dat de module compatibel is met Windows Power shell en Power shell core.

> [!NOTE]
> `Core` betekent niet automatisch dat de module compatibel is met Windows, Linux en macOS.
> De eigenschap **CompatiblePSEditions** is geïntroduceerd in Power Shell v5. Module manifesten die gebruikmaken van de eigenschap **CompatiblePSEditions** , kunnen niet worden geladen in versies voorafgaand aan Power Shell v5.

### <a name="indicating-os-compatibility"></a>De compatibiliteit van besturings systemen aangeven

Controleer eerst of uw module werkt op Linux en macOS. Geef vervolgens compatibiliteit met deze besturings systemen op in het module manifest. Dit maakt het gemakkelijker voor gebruikers om uw module te vinden voor hun besturings systeem wanneer deze naar de [PowerShell Gallery][]worden gepubliceerd.

Binnen het module manifest heeft de `PrivateData` eigenschap een `PSData` subeigenschap. De optionele `Tags` eigenschap van `PSData` heeft een matrix van waarden die worden weer gegeven in PowerShell Gallery. De PowerShell Gallery ondersteunt de volgende compatibiliteits waarden:

| Tag               | Beschrijving                                |
|-------------------|--------------------------------------------|
| PSEdition_Core    | Compatibel met Power shell Core 6          |
| PSEdition_Desktop | Compatibel met Windows Power shell         |
| Windows           | Compatibel met Windows                    |
| Linux             | Compatibel met Linux (geen specifieke distributie) |
| macOS             | Compatibel met macOS                      |

Voorbeeld:

```powershell
@{
    GUID = "4ae9fd46-338a-459c-8186-07f910774cb8"
    Author = "Microsoft Corporation"
    CompanyName = "Microsoft Corporation"
    Copyright = "(C) Microsoft Corporation. All rights reserved."
    HelpInfoUri = "https://go.microsoft.com/fwlink/?linkid=855962"
    ModuleVersion = "1.2.4"
    PowerShellVersion = "3.0"
    ClrVersion = "4.0"
    RootModule = "PackageManagement.psm1"
    Description = 'PackageManagement (a.k.a. OneGet) is a new way to discover and install software packages from around the web.
 It is a manager or multiplexer of existing package managers (also called package providers) that unifies Windows package management with a single Windows PowerShell interface. With PackageManagement, you can do the following.
  - Manage a list of software repositories in which packages can be searched, acquired and installed
  - Discover software packages
  - Seamlessly install, uninstall, and inventory packages from one or more software repositories'

    CmdletsToExport = @(
        'Find-Package',
        'Get-Package',
        'Get-PackageProvider',
        'Get-PackageSource',
        'Install-Package',
        'Import-PackageProvider'
        'Find-PackageProvider'
        'Install-PackageProvider'
        'Register-PackageSource',
        'Set-PackageSource',
        'Unregister-PackageSource',
        'Uninstall-Package'
        'Save-Package'
    )

    FormatsToProcess  = @('PackageManagement.format.ps1xml')

    PrivateData = @{
        PSData = @{
            Tags = @('PackageManagement', 'PSEdition_Core', 'PSEdition_Desktop', 'Windows', 'Linux', 'macOS')
            ProjectUri = 'https://oneget.org'
        }
    }
}
```

### <a name="dependency-on-native-libraries"></a>Afhankelijkheid van systeem eigen bibliotheken

Modules die bedoeld zijn voor gebruik in verschillende besturings systemen of processor architecturen kunnen afhankelijk zijn van een beheerde bibliotheek die zelf afhankelijk is van sommige systeem eigen bibliotheken.

Voorafgaand aan Power shell 7 zou een aangepaste code moeten hebben om de juiste systeem eigen dll te laden, zodat de beheerde bibliotheek deze correct kan vinden.

Met Power shell 7 worden systeem eigen binaire bestanden die worden geladen in submappen in de locatie van de beheerde bibliotheek doorzocht na een subset van de [.net Rid-catalogus][] notatie.

```
managed.dll folder
    |
    |--- 'win-x64' folder
    |       |--- native.dll
    |
    |--- 'win-x86' folder
    |       |--- native.dll
    |
    |--- 'win-arm' folder
    |       |--- native.dll
    |
    |--- 'win-arm64' folder
    |       |--- native.dll
    |
    |--- 'linux-x64' folder
    |       |--- native.so
    |
    |--- 'linux-x86' folder
    |       |--- native.so
    |
    |--- 'linux-arm' folder
    |       |--- native.so
    |
    |--- 'linux-arm64' folder
    |       |--- native.so
    |
    |--- 'osx-x64' folder
    |       |--- native.dylib
```

<!-- reference links -->
[.NET Framework]: /dotnet/framework/
[.NET Core]: /dotnet/core/
[PSSnapIn]: /dotnet/api/system.management.automation.pssnapin
[New-ModuleManifest]: /powershell/module/microsoft.powershell.core/new-modulemanifest
[runtime controles]: /dotnet/api/system.runtime.interopservices.runtimeinformation.frameworkdescription#System_Runtime_InteropServices_RuntimeInformation_FrameworkDescription
[.NET CLI]: /dotnet/core/tools/?tabs=netcore2x
[Visual Studio code gebruiken voor het opsporen van fouten in gecompileerde cmdlets]: vscode/using-vscode-for-debugging-compiled-cmdlets.md
[.NET Standard]: /dotnet/standard/net-standard
[Power Shell-standaard]: https://github.com/PowerShell/PowerShellStandard
[Power Shell-standaard 5,1]: https://www.nuget.org/packages/PowerShellStandard.Library/5.1.0
[PowerShell Gallery]: https://www.powershellgallery.com
[.NET-portabiliteit Analyzer]: https://github.com/Microsoft/dotnet-apiport
[CompatiblePSEditions]: /powershell/scripting/gallery/concepts/module-psedition-support
[.NET RID-catalogus]: /dotnet/core/rid-catalog
