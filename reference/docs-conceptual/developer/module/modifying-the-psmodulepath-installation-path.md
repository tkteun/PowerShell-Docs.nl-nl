---
ms.date: 09/13/2016
ms.topic: reference
title: Het PSModulePath-installatiepad wijzigen
description: Het PSModulePath-installatiepad wijzigen
ms.openlocfilehash: b802492bf9b49e8165e296817e3f80b9ae8265a6
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92661938"
---
# <a name="modifying-the-psmodulepath-installation-path"></a>Het PSModulePath-installatiepad wijzigen

De `PSModulePath` omgevings variabele slaat de paden op naar de locaties van de modules die op schijf zijn geïnstalleerd. Power shell gebruikt deze variabele om modules te zoeken wanneer de gebruiker niet het volledige pad naar een module opgeeft. De paden in deze variabele worden doorzocht in de volg orde waarin ze worden weer gegeven.

Wanneer Power shell wordt gestart, `PSModulePath` wordt gemaakt als een systeem omgevingsvariabele met de volgende standaard waarde: `$HOME\Documents\PowerShell\Modules; $PSHOME\Modules` in Windows en `$HOME/.local/share/powershell/Modules: usr/local/share/powershell/Modules` op Linux of Mac, en `$HOME\Documents\WindowsPowerShell\Modules; $PSHOME\Modules` voor Windows Power shell.

> [!NOTE]
> De gebruikerspecifieke locatie van **CurrentUser** is de `WindowsPowerShell\Modules` map die zich bevindt op de locatie van **documenten** in uw gebruikers profiel. Het specifieke pad van die locatie is afhankelijk van de versie van Windows en of u nu Mapomleiding gebruikt. Deze locatie is standaard op Windows 10 `$HOME\Documents\WindowsPowerShell\Modules` .

## <a name="to-view-the-psmodulepath-variable"></a>De variabele PSModulePath weer geven

Als u de opgegeven paden in de variabele wilt weer geven `PSModulePath` , typt u de volgende opdracht:

`$env:PSModulePath`

## <a name="to-add-locations-to-the-psmodulepath-variable"></a>Locaties toevoegen aan de variabele PSModulePath

Gebruik een van de volgende methoden om paden aan deze variabele toe te voegen:

- Als u een tijdelijke waarde wilt toevoegen die alleen beschikbaar is voor de huidige sessie, voert u de volgende opdracht uit op de opdracht regel:

  `$env:PSModulePath = $env:PSModulePath + "$([System.IO.Path]::PathSeparator)$MyModulePath"`

- Als u een permanente waarde wilt toevoegen die beschikbaar is wanneer een sessie wordt geopend, voegt u de bovenstaande opdracht toe aan een Power shell-profiel bestand ( `$PROFILE` ) >

  Zie [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles)voor meer informatie over profielen.

- Als u een permanente variabele wilt toevoegen aan het REGI ster, maakt u een nieuwe gebruikers omgevings variabele `PSModulePath` met de naam met behulp van de editor voor omgevings variabelen in het dialoog venster **systeem eigenschappen** .

- Als u een permanente variabele wilt toevoegen met behulp van een script, gebruikt u de .net-methode [SetEnvironmentVariable](/dotnet/api/system.environment.setenvironmentvariable) in de klasse [System. Environment](/dotnet/api/system.environment) . Het volgende script voegt bijvoorbeeld het `C:\Program Files\Fabrikam\Module` pad toe aan de waarde van de `PSModulePath` omgevings variabele voor de computer. Als u het pad wilt toevoegen aan de variabele voor de gebruikers `PSModulePath` omgeving, stelt u het doel in op ' gebruiker '.

  ```powershell
  $CurrentValue = [Environment]::GetEnvironmentVariable("PSModulePath", "Machine")
  [Environment]::SetEnvironmentVariable("PSModulePath", $CurrentValue + [System.IO.Path]::PathSeparator + "C:\Program Files\Fabrikam\Modules", "Machine")

  ```

## <a name="to-remove-locations-from-the-psmodulepath"></a>Locaties verwijderen uit de PSModulePath

U kunt paden uit de variabele verwijderen met soort gelijke methoden: als u bijvoorbeeld `$env:PSModulePath = $env:PSModulePath -replace "$([System.IO.Path]::PathSeparator)c:\\ModulePath"` het pad **c:\ModulePath** verwijdert uit de huidige sessie.

## <a name="see-also"></a>Zie ook

[Een Windows PowerShell-module schrijven](./writing-a-windows-powershell-module.md)

[about_Modules](/powershell/module/microsoft.powershell.core/about/about_modules)
