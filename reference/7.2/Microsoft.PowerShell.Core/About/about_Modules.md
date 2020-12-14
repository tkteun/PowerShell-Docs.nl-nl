---
description: Hierin wordt uitgelegd hoe u Power shell-modules installeert, importeert en gebruikt.
Locale: en-US
ms.date: 12/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_modules?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Modules
ms.openlocfilehash: b98c8b27b68c213ac43fbd350ecd920f813dec6b
ms.sourcegitcommit: 7b376314e7640c39a53aac9f0db8bb935514a960
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/03/2020
ms.locfileid: "96564589"
---
# <a name="about-modules"></a>Over modules

## <a name="short-description"></a>Korte beschrijving
Hierin wordt uitgelegd hoe u Power shell-modules installeert, importeert en gebruikt.

## <a name="long-description"></a>Lange beschrijving

Een module is een pakket met Power shell-leden, zoals cmdlets, providers, functies, werk stromen, variabelen en aliassen.

Personen die opdrachten schrijven, kunnen modules gebruiken om hun opdrachten te organiseren en ze te delen met anderen. Personen die een module ontvangen, kunnen de opdrachten in de modules toevoegen aan hun Power shell-sessies en deze gebruiken zoals de ingebouwde opdrachten.

In dit onderwerp wordt uitgelegd hoe u Power shell-modules gebruikt. Zie [een Power shell-module schrijven](/powershell/scripting/developer/module/writing-a-windows-powershell-module)voor meer informatie over het schrijven van Power shell-modules.

## <a name="what-is-a-module"></a>Wat is een module?

Een module is een pakket met Power shell-leden, zoals cmdlets, providers, functies, werk stromen, variabelen en aliassen. De leden van dit pakket kunnen worden geïmplementeerd in een Power shell-script, een gecompileerde DLL of een combi natie van beide. Deze bestanden worden meestal samen in één map gegroepeerd. Zie [informatie over een Windows Power shell-module](/powershell/scripting/developer/module/understanding-a-windows-powershell-module) in de SDK-documentatie voor meer informatie.

## <a name="module-auto-loading"></a>Module automatisch laden

Vanaf Power Shell 3,0 worden modules in Power shell automatisch geïmporteerd in de eerste keer dat u een opdracht in een geïnstalleerde module uitvoert. U kunt nu de opdrachten in een module zonder set-up-of profiel configuratie gebruiken. u hoeft geen modules te beheren nadat u ze op uw computer hebt geïnstalleerd.

De opdrachten in een module zijn ook gemakkelijker te vinden. De `Get-Command` cmdlet haalt nu alle opdrachten op in alle geïnstalleerde modules, zelfs als ze nog niet in de sessie zijn. U kunt een opdracht vinden en deze gebruiken zonder dat u hoeft te importeren om eerst de module te importeren.

In elk van de volgende voor beelden wordt de CimCmdlets-module, die bevat `Get-CimInstance` , in uw sessie geïmporteerd.

- Voer de opdracht uit

  ```powershell
  Get-CimInstance Win32_OperatingSystem
  ```

- De opdracht ophalen

  ```powershell
  Get-Command Get-CimInstance
  ```

- Hulp vragen voor de opdracht

  ```powershell
  Get-Help Get-CimInstance
  ```

`Get-Command` opdrachten die een Joker teken () bevatten, worden `*` beschouwd als voor detectie, niet voor gebruik en er worden geen modules geïmporteerd.

Alleen modules die zijn opgeslagen op de locatie die is opgegeven door de omgevings variabele PSModulePath, worden automatisch geïmporteerd. Modules op andere locaties moeten worden geïmporteerd door de cmdlet uit te voeren `Import-Module` .

Daarnaast importeren opdrachten die gebruikmaken van Power shell-providers niet automatisch een module. Als u bijvoorbeeld een opdracht gebruikt die het WSMan: station vereist, zoals de `Get-PSSessionConfiguration` cmdlet, moet u mogelijk de `Import-Module` cmdlet uitvoeren om de **micro soft. WSMan. Management** -module te importeren die het station bevat `WSMan:` .

U kunt nog steeds de `Import-Module` opdracht uitvoeren om een module te importeren en de `$PSModuleAutoloadingPreference` variabele gebruiken om het automatisch importeren van modules in te scha kelen, uit te scha kelen en te configureren. Zie [about_Preference_Variables](about_Preference_Variables.md)voor meer informatie.

## <a name="how-to-use-a-module"></a>Een module gebruiken

Als u een module wilt gebruiken, voert u de volgende taken uit:

1. Installeer de module. (Dit gebeurt vaak voor u.)
1. Zoek de opdrachten die de module heeft toegevoegd.
1. Gebruik de opdrachten die door de module zijn toegevoegd.

In dit onderwerp wordt uitgelegd hoe u deze taken uitvoert. Het bevat ook andere nuttige informatie over het beheren van modules.

## <a name="how-to-install-a-module"></a>Een module installeren

Als u een module als een map met bestanden ontvangt, moet u deze op uw computer installeren voordat u deze kunt gebruiken in Power shell.

De meeste modules zijn voor u geïnstalleerd. Power shell wordt geleverd met verschillende vooraf geïnstalleerde modules, ook wel de _kern_ modules genoemd. Op Windows-computers worden deze modules vooraf geïnstalleerd als de functies die deel uitmaken van het besturings systeem cmdlets hebben om ze te beheren. Wanneer u een Windows-functie installeert met behulp van bijvoorbeeld de wizard functies en onderdelen toevoegen in Serverbeheer of het dialoog venster Windows-onderdelen in-of uitschakelen in het configuratie scherm, worden alle Power shell-modules die deel uitmaken van de functie geïnstalleerd. Er zijn veel andere modules beschikbaar in een installatie programma of Setup-toepassing waarmee de module wordt geïnstalleerd.

Gebruik de volgende opdracht om een directory **modules** voor de huidige gebruiker te maken:

```powershell
New-Item -Type Directory -Path $HOME\Documents\PowerShell\Modules
```

Kopieer de volledige module-map naar de map modules. U kunt elke methode gebruiken om de map te kopiëren, met inbegrip van Windows Verkenner en Cmd.exe, en Power shell. Gebruik in Power shell de `Copy-Item` cmdlet. Als u bijvoorbeeld de map MyModule wilt kopiëren van `C:\ps-test\MyModule` naar de map modules, typt u:

```powershell
Copy-Item -Path C:\ps-test\MyModule -Destination `
    $HOME\Documents\PowerShell\Modules
```

U kunt een module op elke locatie installeren, maar als u uw modules in een standaard module locatie installeert, zijn deze gemakkelijker te beheren. Zie de sectie [module en DSC-resource locaties en PSModulePath](#module-and-dsc-resource-locations-and-psmodulepath) voor meer informatie over de standaard module locaties.

## <a name="how-to-find-installed-modules"></a>Geïnstalleerde modules zoeken

Als u modules wilt zoeken die zijn geïnstalleerd op een standaard locatie van de module, maar nog niet zijn geïmporteerd in uw sessie, typt u:

```powershell
Get-Module -ListAvailable
```

Als u de modules wilt vinden die al in uw sessie zijn geïmporteerd, typt u bij de Power shell-prompt het volgende:

```powershell
Get-Module
```

`Get-Module`Zie [Get-module](xref:Microsoft.PowerShell.Core.Get-Module)voor meer informatie over de cmdlet.

## <a name="how-to-find-the-commands-in-a-module"></a>De opdrachten in een module vinden

Gebruik de `Get-Command` cmdlet om alle beschik bare opdrachten te vinden. U kunt de para meters van de `Get-Command` cmdlet gebruiken om opdrachten te filteren, bijvoorbeeld per module, naam en zelfstandignaam programma.

Als u alle opdrachten in een module wilt zoeken, typt u:

```powershell
Get-Command -Module <module-name>
```

Als u bijvoorbeeld de opdrachten in de BitsTransfer-module wilt zoeken, typt u:

```powershell
Get-Command -Module BitsTransfer
```

`Get-Command`Zie [Get-opdracht](xref:Microsoft.PowerShell.Core.Get-Command)voor meer informatie over de cmdlet.

## <a name="how-to-get-help-for-the-commands-in-a-module"></a>Hulp krijgen voor de opdrachten in een module

Als de module Help-bestanden bevat voor de opdrachten die worden geëxporteerd, `Get-Help` worden de Help-onderwerpen weer gegeven door de cmdlet. Gebruik dezelfde `Get-Help` opdracht indeling die u zou gebruiken om hulp te krijgen voor elke opdracht in Power shell.

Vanaf Power Shell 3,0 kunt u Help-bestanden voor een module downloaden en updates naar de Help-bestanden downloaden zodat deze nooit verouderd zijn.

Als u hulp wilt krijgen voor een-opdracht in een module, typt u:

```powershell
Get-Help <command-name>
```

Als u online hulp voor de opdracht wilt krijgen in een module, typt u:

```powershell
Get-Help <command-name> -Online
```

Als u de Help-bestanden voor de opdrachten in een module wilt downloaden en installeren, typt u:

```powershell
Update-Help -Module <module-name>
```

Zie [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) en [Update-Help](xref:Microsoft.PowerShell.Core.Update-Help)voor meer informatie.

## <a name="how-to-import-a-module"></a>Een module importeren

Mogelijk moet u een module importeren of een module bestand importeren. Importeren is vereist wanneer een module niet is geïnstalleerd op de locaties die zijn opgegeven door de omgevings variabele **PSModulePath** , `$env:PSModulePath` of als de module bestaat uit een bestand, zoals een. dll-of. psm1-bestand, in plaats van een typische module die wordt geleverd als een map.

U kunt er ook voor kiezen om een module te importeren, zodat u de para meters van de `Import-Module` opdracht, zoals de para meter prefix, een onderscheidend voor voegsel toevoegt aan de naam van het zelfstandige zelfstandig van alle geïmporteerde opdrachten of de para meter **NoClobber** , waarmee wordt voor komen dat de module opdrachten kan toevoegen waarmee bestaande opdrachten in de sessie worden verborgen of vervangen.

Als u modules wilt importeren, gebruikt u de `Import-Module` cmdlet.

Als u modules in een PSModulePath-locatie in de huidige sessie wilt importeren, gebruikt u de volgende opdracht indeling.

```powershell
Import-Module <module-name>
```

Met de volgende opdracht wordt bijvoorbeeld de module BitsTransfer in de huidige sessie geïmporteerd.

```powershell
Import-Module BitsTransfer
```

Als u een module wilt importeren die zich niet in een standaard module locatie bevindt, gebruikt u het volledig gekwalificeerde pad naar de module map in de opdracht.

Als u bijvoorbeeld de module TestCmdlets in de `C:\ps-test` map wilt toevoegen aan uw sessie, typt u:

```powershell
Import-Module C:\ps-test\TestCmdlets
```

Als u een module bestand wilt importeren dat zich niet in een module-map bevindt, gebruikt u het volledige pad naar het module bestand in de opdracht.

Als u bijvoorbeeld de module TestCmdlets.dll in de `C:\ps-test` map wilt toevoegen aan uw sessie, typt u:

```powershell
Import-Module C:\ps-test\TestCmdlets.dll
```

Zie [import-module](xref:Microsoft.PowerShell.Core.Import-Module)voor meer informatie over het toevoegen van modules aan uw sessie.

## <a name="how-to-import-a-module-into-every-session"></a>Een module in elke sessie importeren

Met de `Import-Module` opdracht worden modules in uw huidige Power shell-sessie geïmporteerd. Als u een module wilt importeren in elke Power shell-sessie die u start, voegt u de `Import-Module` opdracht toe aan uw Power shell-profiel.

Zie [about_Profiles](about_Profiles.md)voor meer informatie over profielen.

## <a name="how-to-remove-a-module"></a>Een module verwijderen

Wanneer u een module verwijdert, worden de opdrachten die de module heeft toegevoegd, verwijderd uit de sessie.

Als u een module uit uw sessie wilt verwijderen, gebruikt u de volgende opdracht indeling.

```powershell
Remove-Module <module-name>
```

Met de volgende opdracht wordt bijvoorbeeld de module BitsTransfer verwijderd uit de huidige sessie.

```powershell
Remove-Module BitsTransfer
```

Als u een module verwijdert, wordt de bewerking van het importeren van een module ongedaan gemaakt. Als u een module verwijdert, wordt de module niet verwijderd. Zie [Remove-module](xref:Microsoft.PowerShell.Core.Remove-Module)voor meer informatie.

## <a name="module-and-dsc-resource-locations-and-psmodulepath"></a>Module-en DSC-resource locaties en PSModulePath

De `$env:PSModulePath` omgevings variabele bevat een lijst met maplocaties die worden doorzocht om modules en resources te zoeken.

De doel locaties die worden toegewezen aan, `$env:PSModulePath` zijn standaard:

- Locaties voor het hele systeem: `$PSHOME\Modules`

  Deze mappen bevatten modules die worden geleverd met Windows en Power shell.

  DSC-resources die zijn opgenomen in Power shell, worden opgeslagen in de `$PSHOME\Modules\PSDesiredStateConfiguration\DSCResources` map.

- Gebruikersspecifieke modules: Dit zijn de modules die door de gebruiker worden geïnstalleerd in het bereik van de gebruiker. `Install-Module` heeft een **bereik** parameter waarmee u kunt opgeven of de module is geïnstalleerd voor de huidige gebruiker of voor alle gebruikers. Zie [install-module](xref:PowerShellGet.Install-Module)voor meer informatie.

  De gebruikerspecifieke locatie van **CurrentUser** op Windows is de `PowerShell\Modules` map die zich bevindt op de locatie van **documenten** in uw gebruikers profiel. Het specifieke pad van die locatie is afhankelijk van de versie van Windows en of u nu Mapomleiding gebruikt. Micro soft OneDrive kan ook de locatie van de map **documenten** wijzigen.

  Deze locatie is standaard op Windows 10 `$HOME\Documents\PowerShell\Modules` . Op Linux of Mac is de  locatie van CurrentUser `$HOME/.local/share/powershell/Modules` .

  > [!NOTE]
  > U kunt de locatie van uw **Documentenmap** controleren met behulp van de volgende opdracht: `[Environment]::GetFolderPath('MyDocuments')` .

- De **ALLUSERS** -locatie bevindt zich `$env:PROGRAMFILES\PowerShell\Modules` in Windows. Op Linux of Mac worden de modules opgeslagen op `/usr/local/share/powershell/Modules` .

> [!NOTE]
> Als u bestanden in de map wilt toevoegen of wijzigen `$env:Windir\System32` , start u Power shell met de optie **als administrator uitvoeren** .

U kunt de standaard module locaties op uw systeem wijzigen door de waarde van de omgevings variabele **PSModulePath** te wijzigen `$Env:PSModulePath` . De omgevings variabele **PSModulePath** is gemodelleerd op de omgevings variabele PATH en heeft dezelfde indeling.

Als u de standaard-module locaties wilt weer geven, typt u:

```powershell
$Env:PSModulePath
```

Gebruik de volgende opdracht indeling om een standaard module locatie toe te voegen.

```powershell
$Env:PSModulePath = $Env:PSModulePath + ";<path>"
```

De punt komma ( `;` ) in de opdracht scheidt u het nieuwe pad van het pad dat voorafgaat aan deze in de lijst.

Als u bijvoorbeeld de map wilt toevoegen `C:\ps-test\Modules` , typt u:

```powershell
$Env:PSModulePath + ";C:\ps-test\Modules"
```

Als u een standaard module locatie in Linux of MacOS wilt toevoegen, gebruikt u de volgende opdracht indeling:

```powershell
$Env:PSModulePath += ":<path>"
```

Als u bijvoorbeeld de `/usr/local/Fabrikam/Modules` map wilt toevoegen aan de waarde van de omgevings variabele **PSModulePath** , typt u:

```powershell
$Env:PSModulePath += ":/usr/local/Fabrikam/Modules"
```

In Linux of MacOS scheidt de dubbele punt ( `:` ) in de opdracht het nieuwe pad van het pad dat voorafgaat aan de voor waarde in de lijst.

Wanneer u een pad naar **PSModulePath** toevoegt, `Get-Module` en `Import-Module` opdrachten bevatten modules in dat pad.

De waarde die u instelt, is alleen van invloed op de huidige sessie. Als u de wijziging permanent wilt maken, voegt u de opdracht toe aan uw Power shell-profiel of gebruikt u het onderdeel systeem in het configuratie scherm om de waarde van de omgevings variabele **PSModulePath** in het REGI ster te wijzigen.

Als u de wijziging permanent wilt aanbrengen, kunt u ook de methode **SetEnvironmentVariable** van de klasse **System. Environment** gebruiken om een pad toe te voegen aan de omgevings variabele **PSModulePath** .

Zie [about_Environment_Variables](about_Environment_Variables.md)voor meer informatie over de variabele **PSModulePath** .

## <a name="modules-and-name-conflicts"></a>Conflicten met modules en naam

Naam conflicten treden op wanneer meer dan één opdracht in de sessie dezelfde naam heeft. Het importeren van een module veroorzaakt een naam conflict wanneer opdrachten in de module dezelfde namen hebben als opdrachten of items in de sessie.

Naam conflicten kunnen ertoe leiden dat opdrachten worden verborgen of vervangen.

### <a name="hidden"></a>Verborgen

Een opdracht is verborgen wanneer het niet de opdracht is die wordt uitgevoerd wanneer u de naam van de opdracht typt, maar u kunt deze uitvoeren met behulp van een andere methode, bijvoorbeeld door de opdracht naam te kwalificeren met de naam van de module of module waarin deze afkomstig is.

### <a name="replaced"></a>Geplaatst

Een opdracht wordt vervangen wanneer u deze niet kunt uitvoeren omdat deze is overschreven door een opdracht met dezelfde naam. Zelfs wanneer u de module verwijdert die het conflict heeft veroorzaakt, kunt u een vervangen opdracht alleen uitvoeren als u de sessie opnieuw opstart.

`Import-Module` kan opdrachten toevoegen die opdrachten in de huidige sessie verbergen en vervangen. Ook kunnen opdrachten in uw sessie opdrachten verbergen die zijn toegevoegd aan de module.

Als u naam conflicten wilt detecteren, gebruikt u de para meter **all** van de `Get-Command` cmdlet. Vanaf Power Shell 3,0 worden `Get-Command` alleen de opdrachten opgehaald die worden uitgevoerd wanneer u de naam van de opdracht typt. De **alle** para meters haalt alle opdrachten met de specifieke naam op in de sessie.

Als u naam conflicten wilt voor komen, gebruikt u de para meters **NoClobber** of **voor voegsel** van de `Import-Module` cmdlet. De para meter **prefix** voegt een voor voegsel toe aan de namen van geïmporteerde opdrachten, zodat deze uniek zijn in de sessie. Met de para meter **NoClobber** worden geen opdrachten geïmporteerd waarmee bestaande opdrachten in de sessie worden verborgen of vervangen.

U kunt ook de para meters **alias**, **cmdlet**, **Function** en **Variable** van gebruiken `Import-Module` om alleen de opdrachten te selecteren die u wilt importeren, en u kunt opdrachten uitsluiten die naam conflicten veroorzaken in uw sessie.

Module auteurs kunnen naam conflicten voor komen door gebruik te maken van de eigenschap **DefaultCommandPrefix** van het module manifest om een standaard voorvoegsel toe te voegen aan alle opdracht namen.
De waarde van de para meter **prefix** krijgt voor rang op de waarde van **DefaultCommandPrefix**.

Zelfs als een opdracht verborgen is, kunt u deze uitvoeren door in aanmerking te komen voor de naam van de module of module waarin deze afkomstig is.

De prioriteits regels van de Power shell-opdracht bepalen welke opdracht wordt uitgevoerd wanneer de sessie opdrachten met dezelfde naam bevat.

Als een sessie bijvoorbeeld een functie en een cmdlet met dezelfde naam bevat, voert Power shell de functie standaard uit. Wanneer de sessie opdrachten van hetzelfde type met dezelfde naam bevat, zoals twee cmdlets met dezelfde naam, wordt standaard de laatst toegevoegde opdracht uitgevoerd.

Zie [about_Command_Precedence](about_Command_Precedence.md)voor meer informatie, inclusief een uitleg van de prioriteits regels en instructies voor het uitvoeren van verborgen opdrachten.

## <a name="modules-and-snap-ins"></a>Modules en snap-ins

U kunt vanuit modules en modules opdrachten toevoegen aan uw sessie. Modules kunnen alle typen opdrachten toevoegen, waaronder cmdlets, providers en functies, en items, zoals variabelen, aliassen en Power Shell-stations. Modules kunnen alleen cmdlets en providers toevoegen.

Voordat u een module of module uit uw sessie verwijdert, gebruikt u de volgende opdrachten om te bepalen welke opdrachten worden verwijderd.

Als u de bron van een cmdlet in uw sessie wilt zoeken, gebruikt u de volgende opdracht indeling:

```powershell
Get-Command <cmdlet-name> | Format-List -Property verb,noun,pssnapin,module
```

Als u bijvoorbeeld de bron van de cmdlet wilt zoeken `Get-Date` , typt u:

```powershell
Get-Command Get-Date | Format-List -Property verb,noun,module
```

## <a name="module-related-warnings-and-errors"></a>Waarschuwingen en fouten met betrekking tot modules

De opdrachten die een module exporteert, moeten voldoen aan de naamgevings regels van de Power shell-opdracht. Als de module die u importeert cmdlets of functies met een niet-goedgekeurde term in hun naam exporteert, `Import-Module` wordt de volgende waarschuwing weer gegeven in de cmdlet.

> Waarschuwing: Sommige geïmporteerde opdracht namen bevatten niet-goedgekeurde werk woorden, waardoor ze minder kunnen worden gedetecteerd. Gebruik de para meter uitgebreid voor meer details of typ Get-Verb om de lijst met goedgekeurde werk woorden weer te geven.

Dit bericht wordt alleen een waarschuwing gegeven. De volledige module is nog steeds geïmporteerd, met inbegrip van de niet-conforme opdrachten. Hoewel het bericht wordt weer gegeven voor module gebruikers, moet het naam probleem worden opgelost door de module auteur.

Als u het waarschuwings bericht wilt onderdrukken, gebruikt u de para meter **DisableNameChecking** van de `Import-Module` cmdlet.

## <a name="built-in-modules-and-snap-ins"></a>Ingebouwde modules en modules

In Power Shell 2,0 en in oudere host-Program ma's in Power Shell 3,0 en hoger, worden de kern opdrachten die met Power shell zijn geïnstalleerd, verpakt in modules die automatisch aan elke Power shell-sessie worden toegevoegd.

Vanaf Power Shell 3,0 worden host-Program ma's die de `InitialSessionState.CreateDefault2` oorspronkelijke sessie status-API implementeren de module micro soft. Power shell. core, standaard aan elke sessie toegevoegd. Modules worden automatisch geladen bij het eerste gebruik.

> [!NOTE]
> Externe sessies, met inbegrip van sessies die zijn gestart met behulp van de `New-PSSession` cmdlet, zijn oudere sessies waarin de ingebouwde opdrachten zijn verpakt in modules.

De volgende modules (of modules) worden geïnstalleerd met Power shell.

- CimCmdlets
- Micro soft. Power shell. Archive
- Micro soft. Power shell. core
- Micro soft. Power shell. Diagnostics
- Micro soft. Power shell. host
- Micro soft. Power shell. Management
- Micro soft. Power shell. Security
- Microsoft.PowerShell.Utility
- Micro soft. WSMan. Management
- PackageManagement
- PowerShellGet
- PSDesiredStateConfiguration
- PSDiagnostics
- PSReadline

## <a name="logging-module-events"></a>Logboek registratie module gebeurtenissen

Vanaf Power Shell 3,0 kunt u uitvoerings gebeurtenissen vastleggen voor de cmdlets en functies in Power shell-modules en-modules door de eigenschap **LogPipelineExecutionDetails** van modules en modules in te stellen op `$True` .
U kunt ook een groepsbeleid instelling gebruiken, module logboek registratie inschakelen om module logboek registratie in te scha kelen in alle Power shell-sessies. Zie de artikelen logboek registratie en groeps beleid voor meer informatie.

## <a name="see-also"></a>Zie ook

[about_Logging_Windows](about_Logging_Windows.md)

[about_Logging_Non-Windows](about_Logging_Non-Windows.md)

[about_Group_Policy_Settings](about_Group_Policy_Settings.md)

[about_Command_Precedence](about_Command_Precedence.md)

[about_Group_Policy_Settings](about_Group_Policy_Settings.md)

[Get-Command](xref:Microsoft.PowerShell.Core.Get-Command)

[Get-Help](xref:Microsoft.PowerShell.Core.Get-Help)

[Get-module](xref:Microsoft.PowerShell.Core.Get-Module)

[Import-module](xref:Microsoft.PowerShell.Core.Import-Module)

[Remove-module](xref:Microsoft.PowerShell.Core.Remove-Module)
