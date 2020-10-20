---
title: Een Power shell-module installeren | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 201679c97acdccae9aa4c2be641ee1da09a8275c
ms.sourcegitcommit: d073e69708bd499ea42642b4b923ce5f11cca295
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "92197822"
---
# <a name="installing-a-powershell-module"></a>Een PowerShell-module installeren

Nadat u de Power shell-module hebt gemaakt, wilt u waarschijnlijk de module op een systeem installeren, zodat u of anderen deze kunnen gebruiken. Over het algemeen is dit het kopiëren van de module bestanden (IE, de. psm1 of de binaire assembly, het module manifest en eventuele andere gekoppelde bestanden) naar een map op die computer. Voor een zeer klein project is dit mogelijk zo eenvoudig als het kopiëren en plakken van de bestanden met Windows Verkenner op één externe computer. voor grotere oplossingen kunt u echter een geavanceerder installatie proces gebruiken. Ongeacht hoe u uw module op het systeem ophaalt, kan Power shell een aantal technieken gebruiken waarmee gebruikers uw modules kunnen vinden en gebruiken. Het belangrijkste probleem voor de installatie is daarom ervoor te zorgen dat Power shell uw module kan vinden. Zie [een Power shell-module importeren](./importing-a-powershell-module.md)voor meer informatie.

## <a name="rules-for-installing-modules"></a>Regels voor het installeren van modules

De volgende informatie is van toepassing op alle modules, waaronder modules die u voor eigen gebruik maakt, modules die u van andere partijen krijgt en modules die u naar anderen distribueert.

### <a name="install-modules-in-psmodulepath"></a>Modules installeren in PSModulePath

Als dat mogelijk is, installeert u alle modules in een pad dat wordt weer gegeven in de omgevings variabele **PSModulePath** of voegt u het pad van de module toe aan de waarde van de **PSModulePath** -omgevings variabele.

De omgevings variabele **PSModulePath** ($env:P smodulepath) bevat de locaties van Windows Power shell-modules. -Cmdlets zijn afhankelijk van de waarde van deze omgevings variabele om modules te vinden.

De waarde van de omgevings variabele **PSModulePath** bevat standaard de volgende systeem-en gebruikers module mappen, maar u kunt de waarde toevoegen en bewerken.

- `$PSHome\Modules` (%Windir%\System32\WindowsPowerShell\v1.0\Modules)

  > [!WARNING]
  > Deze locatie is gereserveerd voor modules die worden geleverd met Windows. Installeer geen modules op deze locatie.

- `$Home\Documents\WindowsPowerShell\Modules` (%UserProfile%\Documents\WindowsPowerShell\Modules)

- `$Env:ProgramFiles\WindowsPowerShell\Modules` (%ProgramFiles%\WindowsPowerShell\Modules)

  Als u de waarde van de omgevings variabele **PSModulePath** wilt ophalen, gebruikt u een van de volgende opdrachten.

  ```powershell
  $Env:PSModulePath
  [Environment]::GetEnvironmentVariable("PSModulePath")
  ```

  Als u een pad naar de module wilt toevoegen aan de waarde van de waarde van de omgevings variabele **PSModulePath** , gebruikt u de volgende opdracht indeling. Deze indeling maakt gebruik van de methode **SetEnvironmentVariable** van de klasse **System. Environment** om een sessie-onafhankelijke wijziging aan te brengen in de omgevings variabele **PSModulePath** .

  ```powershell
  #Save the current value in the $p variable.
  $p = [Environment]::GetEnvironmentVariable("PSModulePath")

  #Add the new path to the $p variable. Begin with a semi-colon separator.
  $p += ";C:\Program Files (x86)\MyCompany\Modules\"

  #Add the paths in $p to the PSModulePath value.
  [Environment]::SetEnvironmentVariable("PSModulePath",$p)

  ```

  > [!IMPORTANT]
  > Zodra u het pad naar **PSModulePath**hebt toegevoegd, moet u een omgevings bericht over de wijziging uitzenden. Door de wijziging uit te zenden, kunnen andere toepassingen, zoals de shell, de wijziging ophalen. Als u de wijziging wilt door sturen, laat u uw product installatie code een **WM_SETTINGCHANGE** -bericht verzenden `lParam` dat is ingesteld op de teken reeks omgeving. Zorg ervoor dat u het bericht verzendt nadat de module-installatie code het **PSModulePath**heeft bijgewerkt.

### <a name="use-the-correct-module-directory-name"></a>De juiste naam voor de module directory gebruiken

Een goed opgemaakte module is een module die is opgeslagen in een map met dezelfde naam als de basis naam van ten minste één bestand in de module directory. Als een module niet goed gevormd is, wordt deze niet door Windows Power shell herkend als een module.

De ' basis naam ' van een bestand is de naam zonder de bestandsnaam extensie. In een goed opgemaakte module moet de naam van de map die de module bestanden bevat, overeenkomen met de basis naam van ten minste één bestand in de module.

In de voor beeld-module Fabrikam is de map die de module bestanden bevat de naam ' fabrikam ' en ten minste één bestand de basis naam ' fabrikam ' heeft. In dit geval hebben zowel Fabrikam.psd1 als Fabrikam.dll de basis naam ' fabrikam '.

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

### <a name="effect-of-incorrect-installation"></a>Effect van onjuiste installatie

Als de module niet de juiste indeling heeft en de locatie ervan niet is opgenomen in de waarde van de omgevings variabele **PSModulePath** , werken de basis detectie functies van Windows Power shell, zoals de volgende, niet.

- Met de functie voor het automatisch laden van de module kan de module niet automatisch worden geïmporteerd.

- De- `ListAvailable` para meter van de cmdlet [Get-module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) kan de module niet vinden.

- De module voor [importeren-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) kan niet worden gevonden. Als u de module wilt importeren, moet u het volledige pad naar het hoofd module bestand of het manifest bestand van de module opgeven.

  Aanvullende functies, zoals de volgende, werken alleen als de module in de sessie wordt geïmporteerd. In goed opgemaakte modules in de omgevings variabele **PSModulePath** werken deze functies zelfs wanneer de module niet in de sessie wordt geïmporteerd.

- De cmdlet [Get-opdracht](/powershell/module/Microsoft.PowerShell.Core/Get-Command) kan geen opdrachten vinden in de module.

- U kunt de Help- [cmdlets](/powershell/module/Microsoft.PowerShell.Core/Save-Help) [Update Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) en Help-informatie voor de module niet bijwerken of opslaan.

- Met de cmdlet [show-command](/powershell/module/Microsoft.PowerShell.Utility/Show-Command) kunnen de opdrachten in de module niet worden gevonden en weer gegeven.

  De opdrachten in de module ontbreken `Show-Command` in het venster in Windows Power shell Integrated Scripting Environment (ISE).

## <a name="where-to-install-modules"></a>Waar modules worden geïnstalleerd?

In deze sectie wordt uitgelegd waar in het bestands systeem Windows Power shell-modules moet worden geïnstalleerd. De locatie is afhankelijk van de manier waarop de module wordt gebruikt.

### <a name="installing-modules-for-a-specific-user"></a>Modules voor een specifieke gebruiker installeren

Als u uw eigen module maakt of een module van een andere partij krijgt, zoals een Windows Power shell-community-website, en u wilt dat de module alleen beschikbaar is voor uw gebruikers account, installeert u de module in uw map met gebruikersspecifieke modules.

`$home\Documents\WindowsPowerShell\Modules\<Module Folder>\<Module Files>`

De map met gebruikersspecifieke modules wordt standaard toegevoegd aan de waarde van de omgevings variabele **PSModulePath** .

### <a name="installing-modules-for-all-users-in-program-files"></a>Modules voor alle gebruikers in programma bestanden installeren

Als u wilt dat een module beschikbaar is voor alle gebruikers accounts op de computer, installeert u de module in de locatie van de programma bestanden.

`$Env:ProgramFiles\WindowsPowerShell\Modules\<Module Folder>\<Module Files>`

> [!NOTE]
> De locatie van de programma bestanden wordt standaard toegevoegd aan de waarde van de omgevings variabele PSModulePath in Windows Power Shell 4,0 en hoger. Voor eerdere versies van Windows Power shell kunt u de locatie van de programma bestanden (%ProgramFiles%\WindowsPowerShell\Modules) hand matig maken en dit pad toevoegen aan de omgevings variabele PSModulePath, zoals hierboven wordt beschreven.

### <a name="installing-modules-in-a-product-directory"></a>Modules in een productsitemap installeren

Als u de module naar andere partijen distribueert, gebruikt u de standaard locatie voor programma bestanden die hierboven wordt beschreven, of maakt u uw eigen bedrijfsspecifieke of productspecifieke submap van de map% Program Files%.

Bijvoorbeeld: fabrikam-technologieën, een fictief bedrijf, verzendt een Windows Power shell-module voor hun fabrikam Manager-product. Het installatie programma van de module maakt een subdirectory modules in de submap van het fabrikam Manager-product.

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

Voor het inschakelen van de detectie functies van de Windows Power shell-module om de module fabrikam te vinden, wordt in het installatie programma van de module voor Fabrikam de modules-locatie toegevoegd aan de waarde van de omgevings variabele **PSModulePath** .

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam Technologies\Fabrikam Manager\Modules\"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

### <a name="installing-modules-in-the-common-files-directory"></a>Modules worden geïnstalleerd in de map common files

Als een module door meerdere onderdelen van een product of meerdere versies van een product wordt gebruikt, installeert u de module in een module-specifieke submap van de map%ProgramFiles%\Common Files\Modules.

In het volgende voor beeld wordt de module fabrikam geïnstalleerd in een submap van Fabrikam van de `%ProgramFiles%\Common Files\Modules` submap. Elke module bevindt zich in een eigen submap in de submap modules.

```
C:\Program Files
  Common Files
    Modules
      Fabrikam
        Fabrikam.psd1 (module manifest)
        Fabrikam.dll (module assembly)
```

Het installatie programma zorgt er vervolgens voor dat de waarde van de omgevings variabele **PSModulePath** het pad van de submap common files modules bevat.

```powershell
$m = $env:ProgramFiles + '\Common Files\Modules'
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$q = $p -split ';'
if ($q -notContains $m) {
    $q += ";$m"
}
$p = $q -join ';'
[Environment]::SetEnvironmentVariable("PSModulePath", $p)
```

## <a name="installing-multiple-versions-of-a-module"></a>Meerdere versies van een module installeren

Als u meerdere versies van dezelfde module wilt installeren, gebruikt u de volgende procedure.

1. Maak een map voor elke versie van de module. Het versie nummer in de mapnaam toevoegen.
2. Maak een module manifest voor elke versie van de module. Voer in de waarde van de sleutel **ModuleVersion** in het manifest het module versie nummer in. Sla het manifest bestand (. psd1) op in de versie-specifieke directory voor de module.
3. Voeg het pad van de module-basismap toe aan de waarde van de omgevings variabele **PSModulePath** , zoals wordt weer gegeven in de volgende voor beelden.

Als u een bepaalde versie van de module wilt importeren, kan de eind gebruiker gebruikmaken `MinimumVersion` `RequiredVersion` van de para meters of van de cmdlet [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) .

Bijvoorbeeld, als de module fabrikam beschikbaar is in versie 8,0 en 9,0, kan de directory structuur van de module Fabrikam er als volgt uitzien.

 ```
C:\Program Files
Fabrikam Manager
  Fabrikam8
    Fabrikam
      Fabrikam.psd1 (module manifest: ModuleVersion = "8.0")
      Fabrikam.dll (module assembly)
  Fabrikam9
    Fabrikam
      Fabrikam.psd1 (module manifest: ModuleVersion = "9.0")
      Fabrikam.dll (module assembly)
```

Het installatie programma voegt beide module paden toe aan de waarde van de omgevings variabele **PSModulePath** .

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam\Fabrikam8;C:\Program Files\Fabrikam\Fabrikam9"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

Wanneer deze stappen zijn voltooid, haalt de para meter **ListAvailable** van de cmdlet [Get-module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) beide fabrikam-modules op. Als u een bepaalde module wilt importeren, gebruikt u de `MinimumVersion` `RequiredVersion` para meters van de cmdlet [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) .

Als beide modules in dezelfde sessie worden geïmporteerd en de modules cmdlets met dezelfde namen bevatten, zijn de cmdlets die het laatst zijn geïmporteerd in de sessie effectief.

## <a name="handling-command-name-conflicts"></a>Conflicten bij het afhandelen van namen van opdrachten

Conflicten met de naam van de opdracht kunnen zich voordoen wanneer de opdrachten die een module exporteert dezelfde naam hebben als opdrachten in de sessie van de gebruiker.

Wanneer een sessie twee opdrachten met dezelfde naam bevat, voert Windows Power shell het type opdracht uit dat voor rang heeft. Wanneer een sessie twee opdrachten bevat die dezelfde naam en hetzelfde type hebben, voert Windows Power shell de opdracht uit die het laatst aan de sessie is toegevoegd. Als u een opdracht wilt uitvoeren die niet standaard wordt uitgevoerd, kunnen gebruikers de naam van de opdracht kwalificeren met de module naam.

Als de sessie bijvoorbeeld een `Get-Date` functie en de `Get-Date` cmdlet bevat, wordt de functie standaard uitgevoerd door Windows Power shell. Als u de cmdlet wilt uitvoeren, moet u voor de opdracht de module naam gebruiken, bijvoorbeeld:

```powershell
Microsoft.PowerShell.Utility\Get-Date
```

Om conflicten met de naam te voor komen, kunnen module auteurs de sleutel **DefaultCommandPrefix** in het module manifest gebruiken om een zelfstandig naam woord voor voegsel op te geven voor alle opdrachten die vanuit de module worden geëxporteerd.

Gebruikers kunnen de para meter **prefix** van de `Import-Module` cmdlet gebruiken om een alternatief voor voegsel te gebruiken. De waarde van de para meter **prefix krijgt voor** rang op de waarde van de sleutel **DefaultCommandPrefix** .

## <a name="see-also"></a>Zie ook

[about_Command_Precedence](/powershell/module/microsoft.powershell.core/about/about_command_precedence)

[Een Windows PowerShell-module schrijven](./writing-a-windows-powershell-module.md)
