---
ms.date: 08/27/2018
keywords: Power shell, cmdlet
title: Bekende opdrachtnamen gebruiken
ms.openlocfilehash: 30b33bc8739975c1a40e51c04a3ee4e426c199e7
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030892"
---
# <a name="using-familiar-command-names"></a>Bekende opdrachtnamen gebruiken

Power shell ondersteunt aliassen om te verwijzen naar opdrachten op alternatieve namen. Met aliasing kunnen gebruikers ervaring hebben met andere shells om algemene opdracht namen te gebruiken die ze al kennen voor vergelijk bare bewerkingen in Power shell.

Met aliasing wordt een nieuwe naam gekoppeld aan een andere opdracht. Power Shell heeft bijvoorbeeld een interne functie met de naam `Clear-Host` waarmee het uitvoer venster wordt gewist. U kunt de `cls` of `clear` alias typen bij een opdracht prompt. Power shell interpreteert deze aliassen en voert de `Clear-Host` functie uit.

Deze functie helpt gebruikers bij het leren van Power shell. Ten eerste hebben de meeste **cmd. exe** -en UNIX-gebruikers een grote aanbod opdrachten die gebruikers al op naam kennen. De Power shell-equivalenten kunnen geen identieke resultaten opleveren. De resultaten zijn echter bijna genoeg dat gebruikers kunnen werken zonder de naam van de Power shell-opdracht te weten. Finger Memory is een andere belang rijke bron van frustraties bij het leren van een nieuwe opdracht shell. Als u **cmd. exe** hebt gebruikt voor jaren, kunt u de `cls` opdracht om het scherm te wissen, reflexively typen. Zonder de alias voor `Clear-Host`ontvangt u een fout bericht en weet u niet wat u kunt doen om de uitvoer te wissen.

De volgende lijst bevat enkele van de algemene **cmd. exe** -en UNIX-opdrachten die u kunt gebruiken in Power shell:

|||||
|-|-|-|-|
|Cat5|dir|zachte|RM|
|cd|echo|verplaatsen|rmdir|
|ziet|wissen|popd|dwars|
|wissen|h|ps|sorteren|
|compatibiliteit|Geschiedenis|pushd|Tee|
|Kopieer|verwijderen|pwd|Type|
|drukt|snelheid|r|schrijven|
|verschillende|1|Outlook||

De cmdlet `Get-Alias` toont u de werkelijke naam van de systeem eigen Power shell-opdracht die aan een alias is gekoppeld.

```powershell
PS> Get-Alias cls
```

```Output
CommandType     Name                               Version    Source
-----------     ----                               -------    ------
Alias           cls -> Clear-Host
```

## <a name="interpreting-standard-aliases"></a>Standaard aliassen interpreteren

De aliassen die eerder zijn beschreven, zijn ontworpen voor naam compatibiliteit met andere opdracht shells.
De meeste aliassen die in Power shell zijn ingebouwd, zijn ontworpen voor de boog. Kortere namen zijn gemakkelijker te typen, maar zijn moeilijk te lezen als u niet weet waar ze naar verwijzen.

Power shell-aliassen proberen te knoeien tussen duidelijkheid en beknoptheid. Power shell gebruikt een standaardset aliassen voor veelvoorkomende naam woorden en termen.

Voor beelden van afkortingen:

| Zelfstandig naam woord of werk woord | Afkorting |
|--------------|--------------|
| Ophalen          | g            |
| Instellen          | s            |
| Item         | Ik            |
| Locatie     | l            |
| Opdracht      | bedraagt           |
| Alias        | al           |

Deze aliassen zijn begrijpelijk wanneer u de korte namen kent.

| Naam van cmdlet    | Alias |
|----------------|-------|
| `Get-Item`     | GI    |
| `Set-Item`     | si    |
| `Get-Location` | boekhoud    |
| `Set-Location` | lineaire    |
| `Get-Command`  | GCM   |
| `Get-Alias`    | Gal   |

Wanneer u bekend bent met het uitvoeren van Power shell-aliasing, kunt u gemakkelijk achterhalen dat de alias **Sal** naar `Set-Alias`verwijst.

## <a name="creating-new-aliases"></a>Nieuwe aliassen maken

U kunt uw eigen aliassen maken met behulp van de cmdlet `Set-Alias`. Met de volgende instructies worden bijvoorbeeld de standaard-cmdlet-aliassen gemaakt die eerder zijn besproken:

```powershell
Set-Alias -Name gi -Value Get-Item
Set-Alias -Name si -Value Set-Item
Set-Alias -Name gl -Value Get-Location
Set-Alias -Name sl -Value Set-Location
Set-Alias -Name gcm -Value Get-Command
```

Intern gebruikt Power shell vergelijk bare opdrachten tijdens het opstarten, maar deze aliassen kunnen niet worden gewijzigd.
Als u probeert een van deze opdrachten uit te voeren, krijgt u een fout melding waarin wordt uitgelegd dat de alias niet kan worden gewijzigd. Bijvoorbeeld:

```
PS> Set-Alias -Name gi -Value Get-Item
Set-Alias : Alias is not writeable because alias gi is read-only or constant and cannot be written to.
At line:1 char:10
+ Set-Alias  <<<< -Name gi -Value Get-Item
```
