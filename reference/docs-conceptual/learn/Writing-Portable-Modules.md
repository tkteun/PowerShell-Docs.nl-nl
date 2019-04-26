---
ms.date: 12/14/2018
keywords: PowerShell-cmdlet
title: Draagbare Modules schrijven
ms.openlocfilehash: 38a93b5b030d58784b91292e2cd060b3a2c19a00
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086405"
---
# <a name="portable-modules"></a>Draagbare Modules

Windows PowerShell is geschreven voor [.NET Framework][] terwijl PowerShell Core is geschreven voor [.NET Core][]. Draagbare modules worden modules die in Windows PowerShell en PowerShell Core werken. .NET Framework en .NET Core zijn zeer compatibel is, zijn er verschillen in de beschikbare API's tussen de twee. Er zijn ook verschillen in de API's beschikbaar in Windows PowerShell en PowerShell Core. Modules die zijn bedoeld om te worden gebruikt in beide omgevingen moeten rekening houden met deze verschillen.

## <a name="porting-an-existing-module"></a>Overzetten van een bestaande Module

### <a name="porting-a-pssnapin"></a>Een PSSnapIn overzetten

PowerShell SnapIns (PSSnapIn) worden niet ondersteund in PowerShell Core. Het is echter pretje om een PSSnapIn converteren naar een PowerShell-module. De registratiecode PSSnapIn is meestal in een bestand met één bron van een klasse die is afgeleid van [PSSnapIn][]. Dit bestand verwijderen van de build; het niet meer nodig.

Gebruik [Nieuwe ModuleManifest][] te maken van een nieuwe modulemanifest dat de registratiecode PSSnapIn meer nodig. Sommige van de waarden uit de PSSnapIn (zoals beschrijving) opnieuw kan worden gebruikt in de module-manifest.

De `RootModule` eigenschap in de module-manifest moet worden ingesteld op de naam van de implementatie van de cmdlets assembly (dll).

### <a name="the-net-portability-analyzer-aka-apiport"></a>De .NET draagbaarheid Analyzer (ook wel APIPort)

Poort-modules die zijn geschreven voor Windows PowerShell om te werken met PowerShell Core, te beginnen met de [.NET Portability Analyzer][]. Dit hulpprogramma uitvoeren op basis van uw gecompileerde assembly om te bepalen of de .NET-API's gebruikt in de module compatibel met .NET Framework, .NET Core en andere runtimes .NET zijn. Het hulpprogramma zijn overeenkomstig alternatieve API's als deze bestaan. U moet anders toevoegen [Runtime-controles][] en beperken de mogelijkheden die niet beschikbaar in bepaalde runtimes.

## <a name="creating-a-new-module"></a>Het maken van een nieuwe Module

Als u een nieuwe module maakt, wordt de aanbeveling is het gebruik van de [.NET CLI][].

### <a name="installing-the-powershell-standard-module-template"></a>De sjabloon standaard PowerShell-Module installeren

Nadat de .NET-CLI is geïnstalleerd, installeert u een bibliotheek voor sjablonen voor het genereren van een eenvoudige PowerShell-module.
De module is compatibel met Windows PowerShell, PowerShell Core, Windows, Linux en macOS.

Het volgende voorbeeld laat zien hoe de sjabloon wilt installeren:

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


Templates                                         Short Name         Language          Tags
----------------------------------------------------------------------------------------------------------------------------
Console Application                               console            [C#], F#, VB      Common/Console
Class library                                     classlib           [C#], F#, VB      Common/Library
PowerShell Standard Module                        psmodule           [C#]              Library/PowerShell/Module
...
```

### <a name="creating-a-new-module-project"></a>Het maken van een nieuw Project in de Module

Nadat de sjabloon is geïnstalleerd, kunt u een nieuw PowerShell-module-project met deze sjabloon kunt maken. In dit voorbeeld wordt de voorbeeldmodule 'myModule' genoemd.

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

### <a name="building-the-module"></a>Het bouwen van de Module

Standaard .NET-CLI-opdrachten gebruiken om het project te bouwen.

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

### <a name="testing-the-module"></a>De Module testen

U kunt na het maken van de module importeren en uitvoeren van de voorbeeld-cmdlet.

```powershell
ipmo .\bin\Debug\netstandard2.0\myModule.dll
Test-SampleCmdlet -?
Test-SampleCmdlet -FavoriteNumber 7 -FavoritePet Cat
```

```output
PS C:\Users\Steve\myModule> ipmo .\bin\Debug\netstandard2.0\myModule.dll
PS C:\Users\Steve\myModule> Test-SampleCmdlet -?

NAME
    Test-SampleCmdlet

SYNTAX
    Test-SampleCmdlet [-FavoriteNumber] <int> [[-FavoritePet] {Cat | Dog | Horse}] [<CommonParameters>]


ALIASES
    None


REMARKS
    None


PS C:\Users\Steve\myModule> Test-SampleCmdlet -FavoriteNumber 7 -FavoritePet Cat

FavoriteNumber FavoritePet
-------------- -----------
             7 Cat
```

De volgende secties wordt beschreven in detail van de technologieën die worden gebruikt door deze sjabloon.

## <a name="net-standard-library"></a>Standaard .NET-bibliotheek

[.NET standard][] is een formele specificatie van .NET-API's die beschikbaar in alle .NET-implementaties zijn. Beheerde code die gericht is op .NET Standard werkt met de .NET Framework en .NET Core-versies die compatibel met die versie van .NET Standard zijn.

> [!NOTE]
> Hoewel een API in .NET Standard bestaat mogelijk, de implementatie van de API in .NET Core kan veroorzaken een `PlatformNotSupportedException` tijdens runtime, dus als u wilt controleren van compatibiliteit met Windows PowerShell en PowerShell Core, de aanbevolen procedure is om uit te voeren tests voor de module in beide omgevingen.
> Ook tests uitvoeren op Linux en Mac OS, als uw module is bedoeld voor meerdere platforms.

Die gericht is op .NET Standard, zorgt ervoor dat, als de module zich verder ontwikkelt, niet-compatibele API's niet per ongeluk in de module introduceren. Compatibiliteitsproblemen zijn gedetecteerd bij het compileren in plaats van de runtime.

Het is echter niet vereist voor het doel .NET Standard voor een module om te werken met Windows PowerShell en PowerShell Core, zolang u compatibele API's gebruiken. De tussenliggende taal (IL) is tussen de twee runtimes compatibel. U kunt .NET Framework 4.6.1 installeert, doelgroep die compatibel is met .NET Standard 2.0. Als u API's buiten .NET Standard 2.0 niet gebruikt, klikt u vervolgens werkt de module met PowerShell Core 6 zonder hercompilatie.

## <a name="powershell-standard-library"></a>PowerShell-Standard-bibliotheek

De [PowerShell-standaard][] bibliotheek is een formele specificatie van de PowerShell-APIs beschikbaar in alle versies van PowerShell groter is dan of gelijk zijn aan de versie van die standaard.

Bijvoorbeeld, [PowerShell Standard 5.1][] is compatibel met Windows PowerShell 5.1 en PowerShell Core 6.0 of hoger.

Het is raadzaam om eerst te compileren van de module met behulp van PowerShell Standard-bibliotheek. De bibliotheek zorgt ervoor dat de API's zijn beschikbaar en worden geïmplementeerd in Windows PowerShell en PowerShell Core 6.
PowerShell-standaard is bedoeld om altijd worden doorgestuurd-compatibel. Een module die is gebouwd met behulp van PowerShell Standard-bibliotheek 5.1 wordt altijd compatibel zijn met toekomstige versies van PowerShell.

## <a name="module-manifest"></a>Module-Manifest

### <a name="indicating-compatibility-with-windows-powershell-and-powershell-core"></a>Compatibiliteit met Windows PowerShell en PowerShell Core die aangeeft

Nadat is gevalideerd dat de module met Windows PowerShell en PowerShell Core werkt, de module-manifest moet expliciet aangeven compatibiliteit met behulp van de [CompatiblePSEditions][] eigenschap. Een waarde van `Desktop` betekent dat de module compatibel met Windows PowerShell, terwijl een waarde van is `Core` betekent dat de module compatibel met PowerShell Core is. Zowel `Desktop` en `Core` betekent dat de module compatibel met Windows PowerShell en PowerShell Core is.

> [!NOTE]
> `Core` automatisch betekent niet dat de module compatibel met Windows, Linux en macOS is.
> De **CompatiblePSEditions** eigenschap werd geïntroduceerd in PowerShell versie 5. Module manifesten die gebruikmaken van de **CompatiblePSEditions** eigenschap niet worden geladen in versies voorafgaand aan PowerShell-versie 5.

### <a name="indicating-os-compatibility"></a>Compatibiliteit met besturingssystemen die aangeeft

Valideer eerst of uw module in Linux en macOS werkt. Vervolgens geven compatibiliteit met deze besturingssystemen in de module-manifest. Dit maakt het gemakkelijker voor gebruikers van uw module vinden voor hun besturingssysteem wanneer gepubliceerd naar de [PowerShell Gallery][].

In de module-manifest, het `PrivateData` eigenschap heeft een `PSData` onderliggende eigenschap. De optionele `Tags` eigenschap van `PSData` wordt een matrix met waarden die worden weergegeven in de PowerShell Gallery. De PowerShell Gallery ondersteunt de volgende waarden voor de compatibiliteit van:

| Code               | Description                                |
|-------------------|--------------------------------------------|
| PSEdition_Core    | Compatibel met PowerShell Core 6          |
| PSEdition_Desktop | Compatibel met Windows PowerShell         |
| Windows           | Compatibel met Windows                    |
| Linux             | Compatibel met Linux (Er zijn geen specifieke distributie) |
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

<!-- reference links -->
[.NET Framework]: /dotnet/framework/
[.NET Core]: /dotnet/core/
[PSSnapIn]: /dotnet/api/system.management.automation.pssnapin
[Nieuwe ModuleManifest]: /powershell/module/microsoft.powershell.core/new-modulemanifest
[Runtime-controles]: /dotnet/api/system.runtime.interopservices.runtimeinformation.frameworkdescription#System_Runtime_InteropServices_RuntimeInformation_FrameworkDescription
[.NET CLI]: /dotnet/core/tools/?tabs=netcore2x
[.NET Standard]: /dotnet/standard/net-standard
[PowerShell-standaard]: https://github.com/PowerShell/PowerShellStandard
[PowerShell Standard 5.1]: https://www.nuget.org/packages/PowerShellStandard.Library/5.1.0
[PowerShell Gallery]: https://www.powershellgallery.com
[.NET Portability Analyzer]: https://github.com/Microsoft/dotnet-apiport
[CompatiblePSEditions]: /powershell/gallery/concepts/module-psedition-support
