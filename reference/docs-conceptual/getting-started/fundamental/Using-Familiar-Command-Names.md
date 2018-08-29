---
ms.date: 08/27/2018
keywords: PowerShell-cmdlet
title: Bekende opdrachtnamen gebruiken
ms.assetid: 021e2424-c64e-4fa5-aa98-aa6405758d5d
ms.openlocfilehash: 08402aa5b959711c150fff89aa6747b6b43f8aa8
ms.sourcegitcommit: 59727f71dc204785a1bcdedc02716d8340a77aeb
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/28/2018
ms.locfileid: "43134080"
---
# <a name="using-familiar-command-names"></a>Bekende opdrachtnamen gebruiken

PowerShell ondersteunt om te verwijzen naar opdrachten met alternatieve namen-aliassen. Aliasing kan gebruikers met ervaring in andere schalen met namen van algemene opdrachten die ze al kennen voor vergelijkbare bewerkingen in PowerShell.

Een nieuwe naam koppelt aliasing aan een andere opdracht. PowerShell heeft bijvoorbeeld een interne functie met de naam `Clear-Host` die het uitvoervenster worden gewist. U kunt beide typen de `cls` of `clear` alias achter de opdrachtprompt. PowerShell wordt deze aliassen wordt geïnterpreteerd en wordt uitgevoerd de `Clear-Host` functie.

Deze functie helpt gebruikers voor meer informatie over PowerShell. Eerste, de meeste Cmd.exe- en Unix-gebruikers hebben een grote statusprovider van opdrachten die gebruikers al bekend met de naam. De PowerShell-equivalenten kunnen niet dezelfde resultaten opleveren. De resultaten zijn echter sluiten voldoende die gebruikers kunnen werken zonder te weten de naam van de PowerShell-opdracht. 'Finger geheugen' is een andere belangrijke bron van frustraties wanneer een nieuwe opdrachtshell learning. Als u Cmd.exe voor jaar hebt gebruikt, mogelijk reflexively typt u de `cls` opdracht voor het wissen van het scherm. Zonder de alias voor `Clear-Host`, u een foutbericht ontvangt en weet niet wat u moet doen om te wissen van de uitvoer.

De volgende lijst bevat enkele van de algemene Cmd.exe- en Unix-opdrachten die u kunt gebruiken in PowerShell:

|||||
|-|-|-|-|
|CAT|dir|koppelen|RM|
|cd|echo|verplaatsen|rmdir|
|chdir|Wissen|popd|slaapstand|
|wissen|H|PS|Sorteren|
|CLS|Geschiedenis|pushd|t|
|Kopiëren|KILL-instructie|pwd|Type|
|DEL|LP|r|schrijven|
|diff|Ls|ren||

De `Get-Alias` cmdlet ziet u de echte naam van de systeemeigen PowerShell-opdracht die is gekoppeld aan een alias.

```powershell
PS> Get-Alias cls
```

```Output
CommandType     Name                               Version    Source
-----------     ----                               -------    ------
Alias           cls -> Clear-Host
```

## <a name="interpreting-standard-aliases"></a>Standard aliassen interpreteren

De aliassen we vorige beschreven zijn ontworpen voor de naam van compatibiliteit met andere opdrachtshells.
De meeste aliassen die zijn ingebouwd in PowerShell zijn ontworpen voor kort te houden. Kortere namen zijn gemakkelijker te type, maar zijn moeilijk te lezen als u niet wat ze verwijzen weet naar.

PowerShell-aliassen proberen te manipuleren tussen duidelijkheid en beknopt te houden. PowerShell maakt gebruik van een standaardset aliassen voor veelvoorkomende woorden en bewerkingen.

Voorbeeld van de afkortingen:

| Zelfstandig naamwoord of term | Afkorting |
|--------------|--------------|
| Ophalen          | G            |
| Instellen          | s            |
| Item         | Ik            |
| Locatie     | l            |
| Opdracht      | cm           |
| Alias        | al           |

Deze aliassen zijn opgebouwd uit overzichtelijke als u weet dat de stenonaam.

| Naam van cmdlet    | Alias |
|----------------|-------|
| `Get-Item `    | GI    |
| `Set-Item`     | SI    |
| `Get-Location` | GB    |
| `Set-Location` | SL    |
| `Get-Command`  | GCM   |
| `Get-Alias`    | GAL   |

Als u bekend met PowerShell aliasing bent, is het gemakkelijk te raden dat de **sal** alias verwijst naar `Set-Alias`.

## <a name="creating-new-aliases"></a>Het maken van nieuwe aliassen

Kunt u uw eigen aliassen met behulp van de `Set-Alias` cmdlet. Bijvoorbeeld, maken de volgende instructies uit de standaard-cmdlet-aliassen die eerder werd besproken:

```powershell
Set-Alias -Name gi -Value Get-Item
Set-Alias -Name si -Value Set-Item
Set-Alias -Name gl -Value Get-Location
Set-Alias -Name sl -Value Set-Location
Set-Alias -Name gcm -Value Get-Command
```

Intern, PowerShell maakt gebruik van vergelijkbare opdrachten tijdens het opstarten, maar deze aliassen zijn niet mag worden gewijzigd.
Als u probeert uit te voeren op een van deze opdrachten, krijgt u een foutbericht waarin wordt uitgelegd dat de alias kan niet worden gewijzigd. Bijvoorbeeld:

```
PS> Set-Alias -Name gi -Value Get-Item
Set-Alias : Alias is not writeable because alias gi is read-only or constant and cannot be written to.
At line:1 char:10
+ Set-Alias  <<<< -Name gi -Value Get-Item
```