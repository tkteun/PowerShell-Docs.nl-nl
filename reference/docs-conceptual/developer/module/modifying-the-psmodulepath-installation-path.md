---
ms.date: 04/19/2021
ms.topic: reference
title: Het PSModulePath-installatiepad wijzigen
description: Het PSModulePath-installatiepad wijzigen
ms.openlocfilehash: 9ea72d9d9188876e5d9503f50a00332410e1ef90
ms.sourcegitcommit: 2ad76cd528338f8c2cc10a84c5c56c0e25b93436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/19/2021
ms.locfileid: "107729740"
---
# <a name="modifying-the-psmodulepath-installation-path"></a>Het PSModulePath-installatiepad wijzigen

De `PSModulePath` omgevingsvariabele slaat de paden op naar de locaties van de modules die op schijf zijn geïnstalleerd. PowerShell gebruikt deze variabele om modules te zoeken wanneer de gebruiker niet het volledige pad naar een module opgeeft. De paden in deze variabele worden doorzocht in de volgorde waarin ze worden weergegeven.

Wanneer PowerShell wordt gestart, wordt gemaakt als een systeemomgevingsvariabele met de volgende standaardwaarde: in Windows en op Linux of Mac, en `PSModulePath` `$HOME\Documents\PowerShell\Modules; $PSHOME\Modules` voor `$HOME/.local/share/powershell/Modules: usr/local/share/powershell/Modules` `$HOME\Documents\WindowsPowerShell\Modules; $PSHOME\Modules` Windows PowerShell.

> [!NOTE]
> De gebruikersspecifieke **CurrentUser-locatie** is de map die zich `WindowsPowerShell\Modules` bevindt op de locatie **Documenten** in uw gebruikersprofiel. Het specifieke pad van die locatie varieert per versie van Windows en of u mapomleiding gebruikt. Standaard is Windows 10 locatie `$HOME\Documents\WindowsPowerShell\Modules` .

## <a name="to-view-the-psmodulepath-variable"></a>De variabele PSModulePath weergeven

Als u de paden die zijn opgegeven in de variabele `PSModulePath` wilt weergeven, typt u de volgende opdracht:

`$env:PSModulePath`

## <a name="to-add-locations-to-the-psmodulepath-variable"></a>Locaties toevoegen aan de variabele PSModulePath

Als u paden wilt toevoegen aan deze variabele, gebruikt u een van de volgende methoden:

- Als u een tijdelijke waarde wilt toevoegen die alleen beschikbaar is voor de huidige sessie, moet u de volgende opdracht uitvoeren op de opdrachtregel:

  `$env:PSModulePath = $env:PSModulePath + "$([System.IO.Path]::PathSeparator)$MyModulePath"`

- Als u een permanente waarde wilt toevoegen die beschikbaar is wanneer een sessie wordt geopend, voegt u de bovenstaande opdracht toe aan een PowerShell-profielbestand ( `$PROFILE` )>

  Zie voor meer informatie over [profielen about_Profiles.](/powershell/module/microsoft.powershell.core/about/about_profiles)

- Als u een permanente variabele wilt toevoegen aan het register, maakt u een nieuwe gebruikersomgevingsvariabele met de naam met behulp van de Editor voor `PSModulePath` omgevingsvariabelen in **het** dialoogvenster Systeemeigenschappen.

- Als u een permanente variabele wilt toevoegen met behulp van een script, gebruikt u de .NET-methode [SetEnvironmentVariable](/dotnet/api/system.environment.setenvironmentvariable) in de [klasse System.Environment.](/dotnet/api/system.environment) Met het volgende script wordt bijvoorbeeld het `C:\Program Files\Fabrikam\Module` pad toegevoegd aan de waarde van de `PSModulePath` omgevingsvariabele voor de computer. Als u het pad wilt toevoegen aan de `PSModulePath` omgevingsvariabele van de gebruiker, stelt u het doel in op 'Gebruiker'.

  ```powershell
  $CurrentValue = [Environment]::GetEnvironmentVariable("PSModulePath", "Machine")
  [Environment]::SetEnvironmentVariable("PSModulePath", $CurrentValue + [System.IO.Path]::PathSeparator + "C:\Program Files\Fabrikam\Modules", "Machine")
  ```

U kunt ook de waarden `PSModulePath` in het `powershell.config.json` configuratiebestand instellen. Zie voor meer informatie [about_PowerShell_Config](/powershell/module/microsoft.powershell.core/about/about_powershell_config#psmodulepath).

## <a name="to-remove-locations-from-the-psmodulepath"></a>Locaties verwijderen uit het PSModulePath

U kunt paden uit de variabele verwijderen met behulp van vergelijkbare methoden. In het volgende voorbeeld wordt het `C:\ModulePath` pad uit de huidige sessie verwijderd.

```powershell
$env:PSModulePath = $env:PSModulePath -replace "$([System.IO.Path]::PathSeparator)c:\\ModulePath"`
```

Als u deze wijziging permanent wilt maken voor alle PowerShell-sessies, gebruikt u de .NET-methode zoals eerder is uitgelegd.

```powershell
[Environment]::SetEnvironmentVariable("PSModulePath", $env:PSModulePath, "Machine")
```

## <a name="see-also"></a>Zie ook

[Een Windows PowerShell-module schrijven](./writing-a-windows-powershell-module.md)

[about_Modules](/powershell/module/microsoft.powershell.core/about/about_modules)
