---
title: Een PowerShell-Module installeren | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb82827e-fdb7-4cbf-b3d4-093e72b3ff0e
caps.latest.revision: 28
ms.openlocfilehash: 7c2bfca50de4645676eafc01bbf23d9797e8b758
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059776"
---
# <a name="installing-a-powershell-module"></a>Een PowerShell-module installeren

Nadat u uw PowerShell-module hebt gemaakt, wordt u waarschijnlijk wilt voor het installeren van de module op een systeem, zodat u of anderen kunnen deze gebruiken. In het algemeen, bestaat deze gewoon van het kopiëren van de module-bestanden (ie, de .psm1 of de binaire assembly, het module-manifest en andere gekoppelde bestanden) naar een map op die computer. Voor een zeer klein project, kan dit net zo eenvoudig als kopiëren en plakken van de bestanden met Windows Explorer naar een externe computer; echter, voor grotere oplossingen kunt u een meer geavanceerde installatieproces gebruiken. Ongeacht hoe u uw module bij het systeem ophalen, kunt PowerShell een aantal technieken waarmee gebruikers vinden en gebruiken van uw modules kunt gebruiken. (Zie voor meer informatie, [importeren van een PowerShell-Module](./importing-a-powershell-module.md).) Daarom het belangrijkste probleem voor de installatie is ervoor te zorgen dat PowerShell zal kunnen vinden van uw module.

In dit onderwerp bevat de volgende secties:

- Regels voor het installeren van Modules

- WHERE-Modules installeren

- De installatie van meerdere versies van een Module

- Opdrachtnaamconflicten verwerken

## <a name="rules-for-installing-modules"></a>Regels voor het installeren van Modules

De volgende informatie heeft betrekking op alle modules, met inbegrip van modules die u maakt voor uw eigen gebruik, de modules die u via andere partijen en de modules die u naar anderen distribueert.

### <a name="install-modules-in-psmodulepath"></a>Modules installeren in PSModulePath

Indien mogelijk alle modules installeren in een pad dat wordt weergegeven in de **PSModulePath** omgevingsvariabele of toevoegen van de modulepad naar de **PSModulePath** omgevingsvariabele.

De **PSModulePath** omgevingsvariabele ($Env: PSModulePath) bevat de locaties van Windows PowerShell-modules. Cmdlets zijn afhankelijk van de waarde van deze omgevingsvariabele modules vinden.

Standaard de **PSModulePath** omgevingsvariabele bevat de volgende systeem en directory's van gebruiker-module, maar u kunt toevoegen aan en bewerkt u de waarde.

- $PSHome\Modules (%Windir%\System32\WindowsPowerShell\v1.0\Modules)

  > [!WARNING]
  > Deze locatie is gereserveerd voor modules die worden geleverd met Windows. Installeer de modules niet naar deze locatie.

- $Home\Documents\WindowsPowerShell\Modules (% UserProfile%\Documents\WindowsPowerShell\Modules)

- $Env:ProgramFiles\WindowsPowerShell\Modules (%ProgramFiles%\WindowsPowerShell\Modules)

  Om de waarde van de **PSModulePath** omgevingsvariabele, een van de volgende opdrachten gebruiken.

  ```powershell
  $Env:PSModulePath
  [Environment]::GetEnvironmentVariable("PSModulePath")
  ```

  Een modulepad toevoegen aan de waarde van de **PSModulePath** omgevingsvariabele waarde, gebruikt u de volgende opdrachtindeling. Deze indeling maakt gebruik van de **SetEnvironmentVariable** -methode van de **System.Environment** klasse voor het maken van een sessie-onafhankelijke wijziging in de **PSModulePath** omgeving variabele.

  ```powershell

  #Save the current value in the $p variable.
  $p = [Environment]::GetEnvironmentVariable("PSModulePath")

  #Add the new path to the $p variable. Begin with a semi-colon separator.
  $p += ";C:\Program Files (x86)\MyCompany\Modules\"

  #Add the paths in $p to the PSModulePath value.
  [Environment]::SetEnvironmentVariable("PSModulePath",$p)

  ```

  > [!IMPORTANT]
  > Nadat u het pad naar hebt toegevoegd **PSModulePath**, moet u een bericht van de omgeving van de wijziging uitzenden. De wijziging Broadcasting, kunt andere toepassingen, zoals de shell om op te halen de wijziging. Als u wilt de wijziging uitzenden, hebt u uw installatie-productcode verzenden een **WM_SETTINGCHANGE** message met `lParam` ingesteld op de tekenreeks 'Omgeving'. Zorg ervoor dat het bericht te verzenden nadat de installatie van module code heeft bijgewerkt **PSModulePath**.

### <a name="use-the-correct-module-directory-name"></a>Gebruik de naam van de juiste Module-map

Een 'opgemaakte' is een module die is opgeslagen in een map met dezelfde naam als de naam op van ten minste één bestand in de modulemap. Als een module niet grammaticaal correct is, Windows PowerShell niet wordt herkend als een module.

De 'algemene naam' van een bestand is de naam zonder de extensie. De naam van de map waarin de bestanden van de module moet overeenkomen met de naam op van ten minste één bestand in de module in een goed ingedeelde module.

Bijvoorbeeld de map waarin de bestanden van de module met de naam "Fabrikam" in de Fabrikam voorbeeldmodule en ten minste één bestand heeft de naam van de "Fabrikam". Zowel Fabrikam.psd1 en Fabrikam.dll hebben in dit geval de naam van de "Fabrikam".

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

Als de module niet grammaticaal correct is en de locatie niet in de waarde van opgenomen is de **PSModulePath** omgevingsvariabele, eenvoudige detectie nieuwe functies van Windows PowerShell, zoals het volgende, werken niet.

- De functie voor het laden van de Module automatisch kan niet automatisch de module importeren.

- De `ListAvailable` parameter van de [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet kan de module niet vinden.

- De [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet kan de module niet vinden. Voor het importeren van de module, moet u het volledige pad naar het root-modulebestand of de module-manifest-bestand opgeven.

  Extra functies, zoals de volgende, werken niet, tenzij de module wordt geïmporteerd in de sessie. In opgemaakte modules in de **PSModulePath** omgevingsvariabele, deze functies werken, zelfs wanneer de module is niet geïmporteerd in de sessie.

- De [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet opdrachten in de module kan niet vinden.

- De [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) en [Help opslaan](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets kan bijwerken of opslaan van de help voor de module.

- De [opdracht weergeven](/powershell/module/Microsoft.PowerShell.Utility/Show-Command) cmdlet niet kan vinden en weergeven van de opdrachten in de module.

  De opdrachten in de module niet aanwezig zijn in de `Show-Command` venster in Windows PowerShell Integrated Scripting Environment (ISE).

## <a name="where-to-install-modules"></a>WHERE-Modules installeren

Deze sectie wordt uitgelegd waar u in het bestandssysteem voor het installeren van Windows PowerShell-modules. De locatie, is afhankelijk van hoe de module wordt gebruikt.

### <a name="installing-modules-for-a-specific-user"></a>Modules installeren voor een specifieke gebruiker

Als u uw eigen module maken of een module ophalen uit een andere partij, zoals de website van een Windows PowerShell-community en u wilt dat de module moet beschikbaar zijn voor uw gebruikersaccount gebruikt, moet u de module installeren in uw directory gebruikersspecifieke-Modules.

```
$home\Documents\WindowsPowerShell\Modules\<Module Folder>\<Module Files>
```

De gebruiker-specifieke Modules-map wordt toegevoegd aan de waarde van de **PSModulePath** omgevingsvariabele standaard.

### <a name="installing-modules-for-all-users-in-program-files"></a>Modules installeren voor alle gebruikers in Program Files

Als u een module beschikbaar voor alle gebruikersaccounts op de computer, installeert u de module op de locatie voor programmabestanden.

```
$Env:ProgramFiles\WindowsPowerShell\Modules\<Module Folder>\<Module Files>
```

> [!NOTE]
> De locatie voor programmabestanden wordt toegevoegd aan de waarde van de omgevingsvariabele PSModulePath standaard in Windows PowerShell 4.0 en hoger. Voor eerdere versies van Windows PowerShell kunt u handmatig de locatie programmabestanden ((%ProgramFiles%\WindowsPowerShell\Modules) maken en dit pad toevoegen aan de omgevingsvariabele PSModulePath zoals hierboven is beschreven.

### <a name="installing-modules-in-a-product-directory"></a>Modules installeren in een Product-Directory

Als u de module aan de andere partijen distribueert, gebruikt u de standaardlocatie voor programmabestanden die hierboven worden beschreven of maak uw eigen bedrijf of product-specifieke submap van de map % ProgramFiles %.

Fabrikam-technologieën, een fictief bedrijf, levert bijvoorbeeld een Windows PowerShell-module voor hun product Manager voor Fabrikam. De module-installatieprogramma maakt een submap Modules in de submap van de product Manager voor Fabrikam.

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

Het installatieprogramma van de module Fabrikam voegt om in te schakelen van de functies van Windows PowerShell-module detectie te vinden van de module Fabrikam, de locatie van de module toe aan de waarde van de **PSModulePath** omgevingsvariabele.

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += "C:\Program Files\Fabrikam Technologies\Fabrikam Manager\Modules\"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

### <a name="installing-modules-in-the-common-files-directory"></a>Modules installeren in de map voor algemene

Als een module wordt gebruikt door meerdere onderdelen van een product of meerdere versies van een product, moet u de module installeren in een module-specifieke submap van de %ProgramFiles%\Common Files\Modules submap.

In het volgende voorbeeld wordt is de Fabrikam-module geïnstalleerd in een submap Fabrikam van de %ProgramFiles%\Common Files\Modules submap. Houd er rekening mee dat elke module bevindt zich in een eigen submap in de submap Modules.

```
C:\Program Files
  Common Files
    Modules
      Fabrikam
        Fabrikam.psd1 (module manifest)
        Fabrikam.dll (module assembly)

```

Vervolgens het installatieprogramma zorgen voor de waarde van de **PSModulePath** omgevingsvariabele bevat het pad van de algemene bestanden modules submap.

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

## <a name="installing-multiple-versions-of-a-module"></a>De installatie van meerdere versies van een Module

Gebruik de volgende procedure voor het installeren van meerdere versies van dezelfde module.

1. Maak een map voor elke versie van de module. Neem het versienummer in naam van de map.

2. Maak een module-manifest voor elke versie van de module. In de waarde van de **ModuleVersion** sleutel in het manifest, geef het versienummer van de module. Sla het manifestbestand (.psd1) in de map specifieke versies voor de module.

3. Pad naar de map van de module hoofdmap toevoegen aan de waarde van de **PSModulePath** omgevingsvariabele, zoals wordt weergegeven in de volgende voorbeelden.

Als u wilt importeren in een bepaalde versie van de module, de eindgebruiker kan gebruiken de `MinimumVersion` of `RequiredVersion` parameters van de [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.

Bijvoorbeeld, als de Fabrikam-module beschikbaar in versie 8.0 en 9.0 is, de mapstructuur van de Fabrikam-module kan lijken op de volgende.

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

Het installatieprogramma voegt beide van de modulepaden naar de **PSModulePath** omgevingsvariabele.

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam\Fabrikam8;C:\Program Files\Fabrikam\Fabrikam9"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

Wanneer deze stappen voltooid zijn, de **ListAvailable** parameter van de [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) -cmdlet krijgt u beide modules voor Fabrikam. Als u wilt importeren in een bepaalde module, gebruikt u de `MinimumVersion` of `RequiredVersion` parameters van de [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.

Als beide modules zijn geïmporteerd in dezelfde sessie en de modules cmdlets met dezelfde namen bevatten, gelden de cmdlets die laatste worden geïmporteerd in de sessie.

## <a name="handling-command-name-conflicts"></a>Opdrachtnaamconflicten verwerken

Opdrachtnaamconflicten kunnen optreden wanneer de opdrachten die Hiermee exporteert u een module dezelfde naam als de opdrachten in de sessie van de gebruiker hebben.

Wanneer een sessie twee opdrachten die dezelfde naam hebben bevat, wordt het opdrachttype voorrang heeft uitgevoerd in Windows PowerShell. Wanneer een sessie twee opdrachten met dezelfde naam en hetzelfde type bevat, wordt de opdracht die is toegevoegd aan de sessie meest recent uitgevoerd in Windows PowerShell. Voor het uitvoeren van een opdracht die niet standaard wordt uitgevoerd, kunnen gebruikers in aanmerking de naam van de opdracht met de naam van de module.

Bijvoorbeeld, als de sessie bevat een `Get-Date` functie en de `Get-Date` Windows PowerShell-cmdlet voert u de functie standaard. Voor het uitvoeren van de cmdlet, geeft u de opdracht met de naam van de module, zoals:

```powershell
Microsoft.PowerShell.Utility\Get-Date
```

Gebruik ter voorkoming van naamconflicten auteurs kunnen de **DefaultCommandPrefix** sleutel in de module-manifest om op te geven van een zelfstandig naamwoord voorvoegsel voor alle opdrachten die zijn geëxporteerd uit de module.

Gebruikers kunnen gebruiken de **voorvoegsel** parameter van de `Import-Module` cmdlet naar een alternatieve voorvoegsel gebruiken. De waarde van de **voorvoegsel** parameter voorrang boven de waarde van de **DefaultCommandPrefix** sleutel.

## <a name="see-also"></a>Zie ook

[about_Command_Precedence](/powershell/module/microsoft.powershell.core/about/about_command_precedence)

[Een Windows PowerShell-Module schrijven](./writing-a-windows-powershell-module.md)
