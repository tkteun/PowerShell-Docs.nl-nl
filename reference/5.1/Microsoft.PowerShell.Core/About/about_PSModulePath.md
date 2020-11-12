---
description: De omgevings variabele PSModulePath bevat een lijst met maplocaties die worden doorzocht om modules en resources te zoeken.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_PSModulePath?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PSModulePath
ms.openlocfilehash: 6e0307996bf619bc887b076a1f8c0faa619964fe
ms.sourcegitcommit: aac365f7813756e16b59322832a904e703e0465b
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/12/2020
ms.locfileid: "94524460"
---
# <a name="about-psmodulepath"></a>Over PSModulePath

De `$env:PSModulePath` omgevings variabele bevat een lijst met maplocaties die worden doorzocht om modules en resources te zoeken. Power shell zoekt recursief naar elke map voor module `.psd1` bestanden (of `.psm1` ).

De doel locaties die worden toegewezen aan, `$env:PSModulePath` zijn standaard:

- Locaties voor het hele systeem: deze mappen bevatten modules die worden geleverd met Power shell. Deze modules worden opgeslagen in de `$PSHOME\Modules` map. Dit is ook de locatie waar de Windows-beheer modules worden geïnstalleerd.

- Door de gebruiker geïnstalleerde modules: Dit zijn de modules die door de gebruiker zijn geïnstalleerd.
  `Install-Module` heeft een **bereik** parameter waarmee u kunt opgeven of de module is geïnstalleerd voor de huidige gebruiker of voor alle gebruikers. Zie [install-module](xref:PowerShellGet.Install-Module)voor meer informatie.

  - In Windows is de locatie van **het gebruikersspecifieke Windows-bereik de** `$HOME\Documents\PowerShell\Modules` map. De locatie van het **ALLUSERS** bereik is `$env:ProgramFiles\PowerShell\Modules` .
  - Op niet-Windows-systemen is de locatie van **het gebruikersspecifieke Windows-bereik de** `$HOME/.local/share/powershell/Modules` map. De locatie van het **ALLUSERS** bereik is `/usr/local/share/powershell/Modules` .

Daarnaast kunnen installatie Programma's waarmee modules in andere directory's worden geïnstalleerd, zoals de map Program Files, hun locaties toevoegen aan de waarde van `$env:PSModulePath` .

> [!NOTE]
> In Windows is de gebruikerspecifieke locatie de `PowerShell\Modules` map die zich bevindt in de map **documenten** van uw gebruikers profiel. Het specifieke pad van die locatie is afhankelijk van de versie van Windows en of u nu Mapomleiding gebruikt. Micro soft OneDrive kan ook de locatie van de map **documenten** wijzigen. U kunt de locatie van uw **Documentenmap** controleren met behulp van de volgende opdracht: `[Environment]::GetFolderPath('MyDocuments')` .

## <a name="modifying-psmodulepath"></a>PSModulePath wijzigen

Als u de standaard module mappen voor de huidige sessie wilt wijzigen, gebruikt u de volgende opdracht indeling om de waarde van de `PSModulePath` omgevings variabele te wijzigen.

Als u bijvoorbeeld de `C:\Program Files\Fabrikam\Modules` map wilt toevoegen aan de waarde van de omgevings variabele PSModulePath, typt u:

```powershell
$Env:PSModulePath = $Env:PSModulePath+";C:\Program Files\Fabrikam\Modules"
```

De punt komma ( `;` ) in de opdracht scheidt u het nieuwe pad van het pad dat voorafgaat aan deze in de lijst. Op niet-Windows-platforms scheidt de dubbele punt ( `:` ) de paden in de omgevings variabele.

Als u de waarde van `PSModulePath` in elke sessie wilt wijzigen, voegt u de vorige opdracht toe aan uw Power shell-profiel of gebruikt u de methode **SetEnvironmentVariable** van de klasse **Environment** .

De volgende opdracht maakt gebruik van de methode **GetEnvironmentVariable** om de computer instelling van `PSModulePath` en de methode **SetEnvironmentVariable** toe te voegen om het `C:\Program Files\Fabrikam\Modules` pad naar de waarde te kunnen toevoegen.

```powershell
$path = [Environment]::GetEnvironmentVariable('PSModulePath', 'Machine')
$newpath = $path + ';C:\Program Files\Fabrikam\Modules'
[Environment]::SetEnvironmentVariable('PSModulePath', $newpath, 'Machine')
```

Als u een pad wilt toevoegen aan de gebruikers instelling, wijzigt u de doel waarde in **gebruiker**.

```powershell
$path = [Environment]::GetEnvironmentVariable('PSModulePath', 'User')
$newpath = $path + ';C:\Program Files\Fabrikam\Modules'
[Environment]::SetEnvironmentVariable('PSModulePath', $newpath, 'User')
```

Zie [omgevings methoden](/dotnet/api/system.environment)voor meer informatie over de methoden van de klasse **System. Environment** .

## <a name="powershell-psmodulepath-construction"></a>Power shell PSModulePath-constructie

De waarde van `$env:PSModulePath` wordt opgebouwd elke keer dat Power shell wordt gestart.
De waarde is afhankelijk van de versie van Power shell en hoe deze wordt gestart.

### <a name="windows-powershell-startup"></a>Windows Power shell starten

Windows Power shell gebruikt de volgende logica voor het maken `PSModulePath` van de bij het opstarten:

- Als dat niet het geval `PSModulePath` is, combi neer u **CurrentUser** , **ALLUSERS** en de paden van de `$PSHOME` modules
- Als `PSModulePath` bestaat:
  - If `PSModulePath` bevat `$PSHOME` pad naar modules:
    - Pad naar **ALLUSERS** -modules wordt ingevoegd voor het `$PSHOME` pad naar de module
  - hierin
    - Alleen gebruiken `PSModulePath` zoals gedefinieerd, omdat de gebruiker de locatie opzettelijk heeft verwijderd `$PSHOME`

Het pad van de **CurrentUser** -module wordt alleen voorafgegaan als het gebruikers bereik `$env:PSModulePath` niet bestaat. Anders wordt het gebruikers bereik `$env:PSModulePath` gebruikt zoals gedefinieerd.

### <a name="powershell-core-6-startup"></a>Power shell Core 6 opstarten

Power shell Core 6 gebruikt geen inhoud van `$env:PSModulePath` als deze detecteert dat deze is gestart vanuit Power shell. Deze overschrijft deze met:

- Het pad voor de **CurrentUser** -modules + **ALLUSERS** -modules pad + `$PSHOME` modules pad + Windows Power shell- `$PSHOME` modules pad.

### <a name="powershell-7-startup"></a>Opstarten in Power shell 7

In Windows gebruikt voor de meeste omgevings variabelen, als de door de gebruiker gedefinieerde variabele bestaat, alleen die waarde door een nieuw proces, zelfs als er al een variabele met dezelfde naam met een computer bereik is.

In Power shell 7 `PSModulePath` wordt behandeld als de manier waarop de `Path` omgevings variabele wordt behandeld in Windows. In Windows `Path` wordt op verschillende manieren een andere omgevings variabelen behandeld. Wanneer een proces wordt gestart, wordt het gebruikers bereik gecombineerd `Path` met het bereik van de computer `Path` .

- Het bereik van de gebruiker ophalen `PSModulePath`
- Vergelijken met proces overgenomen `PSModulePath` omgevings variabele
  - Als hetzelfde:
    - De **ALLUSERS** toevoegen `PSModulePath` aan het eind na de semantiek van de `Path` omgevings variabele
    - Het Windows- `System32` pad is afkomstig van de computer die is gedefinieerd. `PSModulePath` Dit hoeft dus niet expliciet te worden toegevoegd
  - Als dit niet het geval is, wordt dit behandeld alsof de gebruiker deze expliciet heeft gewijzigd en niet **ALLUSERS** toevoegt `PSModulePath`
- Voor voegsel met PS7 gebruiker, systeem en `$PSHOME` paden in die volg orde
  - Als `powershell.config.json` een gebruikers bereik bevat `PSModulePath` , gebruikt u dat in plaats van de standaard waarde voor de gebruiker
  - Als `powershell.config.json` een systeem bereik bevat `PSModulePath` , gebruikt u dit in plaats van de standaard waarde voor het systeem

UNIX-systemen hebben geen schei ding van gebruikers-en systeem omgevingsvariabelen.
`PSModulePath` wordt overgenomen en de PS7-specifieke paden worden voorafgegaan als nog niet gedefinieerd.

### <a name="starting-windows-powershell-from-powershell-7"></a>Windows Power shell starten vanuit Power shell 7

Voor deze discussie betekent _Windows Power shell_ zowel `powershell.exe` als `powershell_ise.exe` .

De waarde van `$env:PSModulePath` wordt gekopieerd naar `WinPSModulePath` met de volgende wijzigingen:

- PS7 het pad van de gebruikers module verwijderen
- PS7 het pad naar de systeem module verwijderen
- PS7 het pad van de `$PSHOME` module verwijderen

De PS7-paden worden verwijderd zodat PS7-modules niet worden geladen in Windows Power shell. De `WinPSModulePath` waarde wordt gebruikt bij het starten van Windows Power shell.

### <a name="starting-powershell-7-from-windows-powershell"></a>Power shell 7 starten vanuit Windows Power shell

Het opstarten van Power shell 7 wordt voortgezet als-is met het toevoegen van overerving van paden die Windows Power Shell heeft toegevoegd. Omdat de PS7-specifieke paden worden voorafgegaan, is er geen functioneel probleem.

### <a name="starting-powershell-6-from-powershell-7"></a>Power shell 6 starten vanuit Power shell 7

Power shell Core 6 overschrijft `$env:PSModulePath` . Er zijn geen wijzigingen aangebracht.

### <a name="starting-powershell-7-from-powershell-6"></a>Power shell 7 starten vanuit Power shell 6

Het opstarten van Power shell 7 wordt voortgezet als-is met het toevoegen van paden die zijn toegevoegd aan Power shell Core 6. Omdat de PS7-specifieke paden worden voorafgegaan, is er geen functioneel probleem.

## <a name="module-search-behavior"></a>Module Zoek gedrag

Power shell doorzoekt elke map in de **PSModulePath** voor module ( `.psd1` of `.psm1` ) bestanden recursief. Met dit zoek patroon kunnen meerdere versies van dezelfde module in verschillende mappen worden geïnstalleerd. Bijvoorbeeld:

```Output
    Directory: C:\Program Files\WindowsPowerShell\Modules\PowerShellGet

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d----           8/14/2020  5:56 PM                1.0.0.1
d----           9/13/2019  3:53 PM                2.1.2
```

Power shell laadt standaard het hoogste versie nummer van een module wanneer er meerdere versies worden gevonden. Gebruik `Import-Module` met de para meter **FullyQualifiedName** om een specifieke versie te laden. Zie [import-module](xref:Microsoft.PowerShell.Core.Import-Module)voor meer informatie.

## <a name="see-also"></a>Zie tevens

- [about_Modules](about_Modules.md)
- [Omgevings methoden](/dotnet/api/system.environment)
