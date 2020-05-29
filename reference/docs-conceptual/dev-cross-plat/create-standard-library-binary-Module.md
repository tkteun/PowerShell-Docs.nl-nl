---
title: Een binaire module van een standaard bibliotheek maken
description: Met de standaard bibliotheek van Power shell kunnen wij platformoverschrijdende modules maken die zowel in Power shell Core als met Windows Power shell 5,1 worden uitgevoerd.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: 51734fd9232e7c33b11c6c5a6abddbcc1f28413c
ms.sourcegitcommit: ed4a895d672334c7b02fb7ef6e950dbc2ba4a197
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/28/2020
ms.locfileid: "84149787"
---
# <a name="how-to-create-a-standard-library-binary-module"></a>Een binaire module van een standaard bibliotheek maken

Ik heb onlangs een idee voor de module die ik wilde implementeren als binaire module. Ik heb een wacht tijd gemaakt met behulp van de [standaard bibliotheek van Power shell][] , zodat deze zo goed mogelijk is. Ik heb de hand leiding [een multi-platform binaire module maken][] gebruikt om deze module zonder obstakels te maken.
We gaan hetzelfde proces door lopen en ik voeg graag een beetje extra commentaar toe.

> [!NOTE]
> De [oorspronkelijke versie][] van dit artikel is gepubliceerd op de blog geschreven door [@KevinMarquette][] . Het Power shell-team hartelijk dank voor het delen van deze inhoud met ons. Raadpleeg zijn blog op [PowerShellExplained.com][].

## <a name="what-is-the-powershell-standard-library"></a>Wat is de standaard-Power shell-bibliotheek?

Met de standaard bibliotheek van Power shell kunnen wij cross platform modules maken die zowel in Power shell Core als in Windows Power shell 5,1 (of 3,0) werken.

## <a name="planning-our-module"></a>Onze module plannen

Het plan voor deze module is het maken `src` van een map voor de C#-code en de structuur van de rest, zoals voor een script module. Dit omvat het gebruik van een build-script voor het compileren van alles in een `output` map. De mapstructuur ziet er als volgt uit:

```
MyModule
├───src
├───Output
│   └───MyModule
├───MyModule
│   ├───Data
│   ├───Private
│   └───Public
└───Tests
```

## <a name="getting-started"></a>Aan de slag

Ik gebruik normaal gesp roken een gips sjabloon, maar mijn huidige sjabloon heeft nog geen ondersteuning voor binaire modules. Niet veel. Ik maak dit nu hand matig.

Eerst moet u de map maken en de Git-opslag plaats maken. Ik gebruik `$module` als tijdelijke aanduiding voor de naam van de module. Zo nodig kunt u deze voor beelden gemakkelijker opnieuw gebruiken.

```powershell
$module = 'MyModule'
New-Item -Path $module -Type Directory
Set-Location $module
git init
```

Maak vervolgens de mappen op het hoofd niveau.

```powershell
New-Item -Path 'src' -Type Directory
New-Item -Path 'Output' -Type Directory
New-Item -Path 'Tests' -Type Directory
New-Item -Path $module -Type Directory
```

### <a name="binary-module-setup"></a>Setup van binaire module

Dit artikel is gericht op de binaire module, zodat we beginnen. In deze sectie vindt u voor beelden van de hand leiding [een multi-platform binaire module maken][] . Lees deze hand leiding als u meer informatie nodig hebt of problemen ondervindt.

Het eerste wat we willen doen, is de versie controleren van de [DotNet core SDK][] die we hebben geïnstalleerd. Ik gebruik 2.1.4, maar u moet 2.0.0 of nieuwer hebben voordat u kunt door gaan.

```powershell
PS> dotnet --version
2.1.4
```

Ik werk samen met de `src` map voor deze sectie.

```powershell
Set-Location 'src'
```

Maak met behulp van de opdracht DotNet een nieuwe klassen bibliotheek.

```powershell
dotnet new classlib --name $module
```

Het bibliotheek project is gemaakt in een submap, maar ik wil niet dat het extra geneste niveau. Ik ga deze bestanden naar een niveau omhoog verplaatsen.

```powershell
Move-Item -Path .\$module\* -Destination .\
Remove-Item $module -Recurse
```

Stel de .NET core SDK-versie voor het project in. Ik heb de 2,1-SDK zodat ik 2.1.0 kan opgeven.
Gebruik 2.0.0 als u de 2,0-SDK gebruikt.

```powershell
dotnet new globaljson --sdk-version 2.1.0
```

Voeg het [NuGet-pakket][] van de Power Shell-standaard bibliotheek toe aan het project. Zorg ervoor dat u de meest recente versie gebruikt die beschikbaar is voor het compatibiliteits niveau dat u nodig hebt. Ik zou standaard de nieuwste versie kunnen gebruiken, maar ik denk eraan dat deze module geen functies gebruikt die nieuwer zijn dan Power Shell 3,0.

```powershell
dotnet add package PowerShellStandard.Library --version 7.0.0-preview.1
```

De map src moet er als volgt uitzien:

```powershell
PS> Get-ChildItem
    Directory: \MyModule\src

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        7/14/2018   9:51 PM                obj
-a----        7/14/2018   9:51 PM             86 Class1.cs
-a----        7/14/2018  10:03 PM            259 MyModule.csproj
-a----        7/14/2018  10:05 PM             45 global.json
```

U kunt nu onze eigen code aan het project toevoegen.

### <a name="building-a-binary-cmdlet"></a>Een binaire cmdlet bouwen

De `src\Class1.cs` moet worden bijgewerkt om deze start-cmdlet te bevatten:

```csharp
using System;
using System.Management.Automation;

namespace MyModule
{
    [Cmdlet( VerbsDiagnostic.Resolve , "MyCmdlet")]
    public class ResolveMyCmdletCommand : PSCmdlet
    {
        [Parameter(Position=0)]
        public Object InputObject { get; set; }

        protected override void EndProcessing()
        {
            this.WriteObject(this.InputObject);
            base.EndProcessing();
        }
    }
}
```

Wijzig de naam van het bestand zodat dit overeenkomt met de naam van de klasse.

```powershell
Rename-Item .\Class1.cs .\ResolveMyCmdletCommand.cs
```

Vervolgens kunnen we onze module bouwen.

```powershell
PS> dotnet build

Microsoft (R) Build Engine version 15.5.180.51428 for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

Restore completed in 18.19 ms for C:\workspace\MyModule\src\MyModule.csproj.
MyModule -> C:\workspace\MyModule\src\bin\Debug\netstandard2.0\MyModule.dll

Build succeeded.
    0 Warning(s)
    0 Error(s)

Time Elapsed 00:00:02.19
```

We kunnen `Import-Module` op de nieuwe dll bellen om onze nieuwe CMDlet te laden.

```powershell
PS> Import-Module .\bin\Debug\netstandard2.0\$module.dll
PS> Get-Command -Module $module

CommandType Name                    Version Source
----------- ----                    ------- ------
Cmdlet      Resolve-MyCmdlet        1.0.0.0 MyModule
```

Als het importeren mislukt op uw systeem, probeert u .NET bij te werken naar 4.7.1 of nieuwer. De hand leiding voor het [maken van een multi platform binaire module][] biedt meer informatie over .net-ondersteuning en-compatibiliteit voor oudere versies van .net.

### <a name="module-manifest"></a>Module manifest

Het is geweldig dat de dll kan worden geïmporteerd en dat er een werkende module is. Ik ga graag aan de slag en maak een module manifest. U hebt het manifest nodig als u later naar de PSGallery wilt publiceren.

In de hoofdmap van ons project kunnen we deze opdracht uitvoeren om het module manifest te maken dat we nodig hebben.

```powershell
$manifestSplat = @{
    Path              = ".\$module\$module.psd1"
    Author            = 'Kevin Marquette'
    NestedModules     = @('bin\MyModule.dll')
    RootModule        = "$module.psm1"
    FunctionsToExport = @('Resolve-MyCmdlet')
}
New-ModuleManifest @manifestSplat
```

U gaat ook een lege basis module maken voor toekomstige Power shell-functies.

```powershell
Set-Content -Value '' -Path ".\$module\$module.psm1"
```

Zo kunt u zowel normale Power shell-functies als binaire cmdlets in hetzelfde project combi neren.

### <a name="building-the-full-module"></a>De volledige module bouwen

Ik compileer alles samen in een uitvoermap. We moeten een bouw script maken om dit te doen. Ik voeg dit normaal gesp roken toe aan een `Invoke-Build` script, maar we kunnen het eenvoudig voor dit voor beeld blijven gebruiken. Voeg dit toe aan een `build.ps1` aan de basis van het project.

```powershell
$module = 'MyModule'
Push-Location $PSScriptRoot

dotnet build $PSScriptRoot\src -o $PSScriptRoot\output\$module\bin
Copy-Item "$PSScriptRoot\$module\*" "$PSScriptRoot\output\$module" -Recurse -Force

Import-Module "$PSScriptRoot\Output\$module\$module.psd1"
Invoke-Pester "$PSScriptRoot\Tests"
```

Met deze opdrachten bouwt u onze DLL en plaatst u deze in onze `output\$module\bin` map. Vervolgens worden de andere module bestanden gekopieerd naar de locatie.

```
Output
└───MyModule
    │   MyModule.psd1
    │   MyModule.psm1
    │
    └───bin
            MyModule.deps.json
            MyModule.dll
            MyModule.pdb
```

Op dit moment kunnen we onze module met het psd1-bestand importeren.

```powershell
Import-Module ".\Output\$module\$module.psd1"
```

Hier kunt u de map neerzetten `.\Output\$module` in onze `$env:PSModulePath` Directory en de opdracht wordt op elk gewenst moment geladen.

### <a name="update-dotnet-new-psmodule"></a>Update: dotnet New PSModule

Ik heb geleerd dat het `dotnet` hulp programma een `PSModule` sjabloon heeft.

Alle stappen die hieronder worden beschreven, zijn nog steeds geldig, maar deze sjabloon knipt veel uit. Er is nog steeds een redelijk nieuwe sjabloon aanwezig, waardoor er nog steeds een gepolijste manier wordt opgenomen. Verwacht wordt dat u deze beter kunt blijven gebruiken.

Dit is de manier waarop u de PSModule-sjabloon installeert en gebruikt.

```powershell
dotnet new -i Microsoft.PowerShell.Standard.Module.Template
dotnet new psmodule
dotnet build
Import-Module "bin\Debug\netstandard2.0\$module.dll"
Get-Module $module
```

Deze sjabloon met minimale beschik bare sjablonen zorgt ervoor dat u de .NET SDK, de standaard bibliotheek van Power shell toevoegt en een voorbeeld klasse maakt in het project. U kunt het bouwen en direct uitvoeren.

## <a name="important-details"></a>Belang rijke Details

Voordat we dit artikel beëindigen, zijn hier enkele andere details te vermelden.

### <a name="unloading-dlls"></a>Dll-bestanden verwijderen

Zodra een binaire module is geladen, kunt u deze niet verwijderen. Het DLL-bestand wordt vergrendeld totdat u het verwijdert. Dit kan vervelend zijn wanneer u een wijziging aanbrengt en u deze wilt bouwen, maar het bestand is vaak vergrendeld. De enige betrouw bare manier om dit probleem op te lossen is het sluiten van de Power shell-sessie die de DLL heeft geladen.

### <a name="vs-code-reload-window-action"></a>De actie VS-code opnieuw laden

Ik voer de meeste van mijn Power shell-ontwikkel werkzaamheden uit in [VS code][]. Wanneer ik aan een binaire module (of een module met klassen) aan het werk ben, heb ik dan elke keer dat ik bouw, de code opnieuw geladen.
<kbd>CTRL</kbd> + <kbd>SHIFT</kbd> + <kbd>P</kbd> het opdracht venster wordt weer gegeven en `Reload Window` is altijd aan de bovenkant van de lijst.

### <a name="nested-powershell-sessions"></a>Geneste Power shell-sessies

Een andere mogelijkheid is een goede dekkings test voor de ziekte te hebben. Vervolgens kunt u het script build. ps1 aanpassen om een nieuwe Power shell-sessie te starten, de build uit te voeren, de tests uit te voeren en de sessie te sluiten.

### <a name="updating-installed-modules"></a>Geïnstalleerde modules bijwerken

Deze vergren deling kan vervelend zijn wanneer u uw lokaal geïnstalleerde module wilt bijwerken. Als een sessie is geladen, moet u deze opsporen en sluiten. Dit is minder van een probleem bij de installatie vanaf een PSGallery, omdat de module versie beheer het nieuwe item in een andere map plaatst.

U kunt een lokale PSGallery instellen en deze publiceren als onderdeel van uw build. Voer vervolgens uw lokale installatie uit vanaf die PSGallery. Dit klinkt als veel werk, maar dit kan net zo eenvoudig zijn als het starten van een docker-container. Ik bevindt een manier om dit te doen in mijn post op het [gebruik van een NuGet-server voor een PSRepository][].

## <a name="why-binary-modules"></a>Waarom binaire modules?

Ik heb het recht om een binaire module te maken en heeft niet aangegeven waarom u er een wilt maken. In werkelijkheid schrijft u C# en kunt u eenvoudig toegang krijgen tot Power shell-cmdlets en-functies. Dit is de belangrijkste reden waarom ik eerder geen binaire modules heb verplaatst.

Maar als u een module maakt die niet afhankelijk is van een groot aantal Power shell-opdrachten, kan het prestatie voordeel aanzienlijk zijn. Door in C# te verwijderen, kunt u de overhead die is toegevoegd door Power shell uitbrengen. Power shell is geoptimaliseerd voor de beheerder en niet op de computer, waardoor er weinig overhead wordt toegevoegd.

Op het werk hebben we een kritiek proces dat veel werk met JSON en hashtabellen. We hebben de Power shell zoveel mogelijk geoptimaliseerd, maar dit proces werd 12 minuten nog steeds uitgevoerd. De module bevat al een heleboel C# style Power shell. Hierdoor is de conversie naar een binaire module schoon en eenvoudig. Onze conversie knipt dat proces van meer dan 12 minuten tot minder dan vier minuten.

### <a name="hybrid-modules"></a>Hybride modules

U kunt binaire cmdlets combi neren met geavanceerde Power shell-functies. Dat is precies wat ik in deze hand leiding doe. U kunt alles wat u weet over script modules en dit allemaal op dezelfde manier Toep assen.
Het lege `psm1` bestand dat ik nu heb gemaakt, is op dit moment alleen mogelijk in andere Power shell-functies.

Bijna alle gecompileerde cmdlets die we hebben gemaakt, zijn de eerste keer gestart als een Power shell-functie. Al onze binaire modules zijn eigenlijk hybride modules.

### <a name="build-scripts"></a>Scripts maken

Ik heb het opbouw script hier eenvoudig gehouden. Ik gebruik in het algemeen een groot `Invoke-Build` script als onderdeel van mijn CI/cd-pijp lijn. Het is meer Magic, zoals het uitvoeren van ziekte tests, het uitvoeren van PSScriptAnalyzer, het beheren van versie beheer en het publiceren naar de PSGallery. Nadat ik een build-script voor mijn modules heb gestart, heb ik veel dingen kunnen vinden om hieraan toe te voegen.

## <a name="final-thoughts"></a>Laatste ideeën

Binaire modules zijn eenvoudig te maken. Ik heb niet gereageerd op de C#-syntaxis voor het maken van een cmdlet, maar er is in de [Windows Power shell-SDK][]nog meer documentatie over. Het is een goed idee om te experimenteren met als steper-steen in meer ernstige C#.

<!-- link references -->
[oorspronkelijke versie]: https://powershellexplained.com/2018-08-04-Powershell-Standard-Library-Binary-Module/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[Standaard bibliotheek van Power shell]: https://github.com/PowerShell/PowerShellStandard
[Een binaire module voor meerdere platforms maken]: https://github.com/PowerShell/PowerShell/blob/master/docs/cmdlet-example/command-line-simple-example.md
[DotNet core SDK]: https://www.microsoft.com/net/download/core
[Een NuGet-server gebruiken voor een PSRepository]: https://powershellexplained.com/2018-03-03-Powershell-Using-a-NuGet-server-for-a-PSRepository/
[Windows PowerShell SDK]: /powershell/scripting/developer/windows-powershell-reference
[VS-code]: https://code.visualstudio.com
[nuget-pakket]: https://www.nuget.org/packages/PowerShellStandard.Library/
