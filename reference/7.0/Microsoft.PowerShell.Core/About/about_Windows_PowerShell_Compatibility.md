---
description: Hierin wordt de Windows Power shell-compatibiliteits functionaliteit voor Power shell 7 beschreven.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 04/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_windows_powershell_compatibility?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Windows_PowerShell_Compatibility
ms.openlocfilehash: 777dab1cce4329958337a7c0857b0d712b4387a9
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252524"
---
# <a name="about-windows-powershell-compatibility"></a>Over Windows Power shell-compatibiliteit

## <a name="short-description"></a>KORTE BESCHRIJVING

Hierin wordt de Windows Power shell-compatibiliteits functionaliteit voor Power shell 7 beschreven.

## <a name="long-description"></a>LANGE BESCHRIJVING

Tenzij in het manifest van de module wordt aangegeven dat de module compatibel is met Power shell core, worden modules in de `%windir%\system32\WindowsPowerShell\v1.0\Modules` map geladen in een achtergrond Windows Power shell 5,1-proces met Windows Power shell-compatibiliteits functie.

### <a name="using-the-compatibility-feature"></a>De compatibiliteits functie gebruiken

Wanneer de eerste module wordt geïmporteerd met behulp van de Windows Power shell-compatibiliteits functie, maakt Power shell een externe sessie met de naam `WinPSCompatSession` die wordt uitgevoerd in een Windows Power shell 5,1-proces op de achtergrond. Dit proces wordt gemaakt wanneer met de compatibiliteits functie de eerste module wordt geïmporteerd. Het proces wordt gesloten wanneer de laatste module wordt verwijderd (met `Remove-Module` ) of wanneer het Power Shell-proces wordt afgesloten.

De modules die in de `WinPSCompatSession` sessie worden geladen, worden gebruikt via impliciete externe communicatie en worden weer gegeven in de huidige Power shell-sessie. Dit is dezelfde transport methode die wordt gebruikt voor Power shell-taken.

Wanneer een module in de sessie wordt geïmporteerd `WinPSCompatSession` , wordt in impliciete externe toegang een proxy module in de map van de gebruiker gegenereerd `$env:Temp` en wordt deze proxy module in de huidige Power shell-sessie geïmporteerd. Hierdoor kan Power shell detecteren dat de module is geladen met behulp van Windows Power shell-compatibiliteits functionaliteit.

Zodra de sessie is gemaakt, kan deze worden gebruikt voor bewerkingen die niet goed werken op gedeserialiseerd objecten. De volledige pijp lijn wordt uitgevoerd in Windows Power shell en alleen het uiteindelijke resultaat wordt geretourneerd. Bijvoorbeeld:

```powershell
$s = Get-PSSession -Name WinPSCompatSession
Invoke-Command -Session $s -ScriptBlock {
  "Running in Windows PowerShell version $($PSVersionTable.PSVersion)"
}
```

De compatibiliteits functie kan op twee manieren worden aangeroepen:

- Expliciet door een module te importeren met de para meter **UseWindowsPowerShell**

   ```powershell
   Import-Module -Name ScheduledTasks -UseWindowsPowerShell
   ```

- U kunt het importeren van een Windows Power shell-module per module naam, pad of autoload via opdracht detectie.

   ```powershell
   Import-Module -Name ServerManager
   Get-AppLockerPolicy -Local
   ```

   Als dat nog niet is gebeurd, wordt de AppLocker-module tijdens het uitvoeren van opnieuw geladen  `Get-AppLockerPolicy` .

Windows Power shell-compatibiliteit blokkeert het laden van modules die worden vermeld in de `WindowsPowerShellCompatibilityModuleDenyList` instelling in het Power shell-configuratie bestand.

De standaard waarde voor deze instelling is:

```json
"WindowsPowerShellCompatibilityModuleDenyList":  [
   "PSScheduledJob","BestPractices","UpdateServices"
]
```

### <a name="managing-implicit-module-loading"></a>Impliciete module laden beheren

Als u het impliciete import gedrag van de Windows Power shell-compatibiliteits functie wilt uitschakelen, gebruikt u de `DisableImplicitWinCompat` instelling in een Power shell-configuratie bestand. Deze instelling kan worden toegevoegd aan het `powershell.config.json` bestand. Zie [about_powershell_config](about_powershell_config.md)voor meer informatie.

In dit voor beeld ziet u hoe u een configuratie bestand maakt waarmee de functie voor het laden van impliciete modules van Windows Power shell-compatibiliteit wordt uitgeschakeld.

```powershell
$ConfigPath = "$PSHOME\DisableWinCompat.powershell.config.json"
$ConfigJSON = ConvertTo-Json -InputObject @{
  "DisableImplicitWinCompat" = $true
  "Microsoft.PowerShell:ExecutionPolicy" = "RemoteSigned"
}
$ConfigJSON | Out-File -Force $ConfigPath
pwsh -settingsFile $ConfigPath
```

Zie de compatibiliteits lijst van de [module Power shell 7](https://aka.ms/PSModuleCompat) voor meer informatie over de compatibiliteit van modules.

### <a name="managing-cmdlet-clobbering"></a>Cmdlet clobbering beheren

De Windows Power shell-compatibiliteits functie maakt gebruik van impliciete externe communicatie om modules in de compatibiliteits modus te laden. Het resultaat is dat opdrachten die door de module worden geëxporteerd, voor rang hebben op opdrachten met dezelfde naam in de huidige Power shell 7-sessie. In de Power shell 7.0.0-versie zijn dit de kern modules die worden geleverd met Power shell.

In Power shell 7,1 is het gedrag gewijzigd, zodat de volgende Power shell-modules niet clobbered zijn:

- Micro soft. Power shell. ConsoleHost
- Micro soft. Power shell. Diagnostics
- Micro soft. Power shell. host
- Micro soft. Power shell. Management
- Micro soft. Power shell. Security
- Microsoft.PowerShell.Utility
- Micro soft. WSMan. Management

Power shell 7,1 heeft ook de mogelijkheid toegevoegd om extra modules weer te geven die niet moeten worden clobbered door de compatibiliteits modus.

U kunt de `WindowsPowerShellCompatibilityNoClobberModuleList` instelling toevoegen aan het Power shell-configuratie bestand. De waarde van deze instelling is een door komma's gescheiden lijst met module namen. De standaard waarde voor deze instelling is:

```json
"WindowsPowerShellCompatibilityNoClobberModuleList": [ ]
```

## <a name="limitations"></a>Beperkingen

De compatibiliteits functionaliteit van Windows Power shell:

1. Werkt alleen lokaal op Windows-computers
1. Vereist dat Windows Power shell 5,1
1. Werkt op geserialiseerde cmdlet-para meters en retour waarden, niet op live-objecten
1. Alle modules die in de Windows Power shell-sessie voor externe toegang worden geïmporteerd, delen dezelfde runs Pace.

## <a name="keywords"></a>Trefwoorden

about_Windows_PowerShell_Compatibility

## <a name="see-also"></a>Zie ook

[about_Modules](about_Modules.md)

[Import-module](xref:Microsoft.PowerShell.Core.Import-Module)
