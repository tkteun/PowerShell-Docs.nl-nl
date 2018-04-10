---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Variabelen gebruiken om objecten op te slaan
ms.assetid: b1688d73-c173-491e-9ba6-6d0c1cc852de
ms.openlocfilehash: e52f0a344d0ad13db42b34bed912d584c99b0e30
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="using-variables-to-store-objects"></a>Variabelen gebruiken om objecten op te slaan
PowerShell werkt met objecten. PowerShell kunt u variabelen in wezen benoemde objecten, behouden de uitvoer voor later gebruik te maken. Als u worden gebruikt voor het werken met variabelen in andere houders Vergeet niet dat PowerShell variabelen objecten, niet naar tekst.

Variabelen altijd worden opgegeven met het eerste teken $ en alle alfanumerieke tekens of het onderstrepingsteken kunnen opnemen in hun naam.

### <a name="creating-a-variable"></a>Maken van een variabele
U kunt een variabele maken door een geldige variabele naam te typen:

```
PS> $loc
PS>
```

Dit resultaat wordt geen omdat **$loc** geen waarde hebben. U kunt maken van een variabele en wijs hieraan een waarde in één stap. De variabele PowerShell alleen gemaakt als deze niet bestaat nog; anders wordt de opgegeven waarde toegewezen aan de bestaande variabele. Voor het opslaan van uw huidige locatie in de variabele **$loc**, type:

```
$loc = Get-Location
```

Er wordt geen uitvoer weergegeven wanneer u deze opdracht invoert, omdat de uitvoer wordt verzonden naar $loc. In PowerShell wordt weergegeven uitvoer een neveneffect van het feit dat de gegevens die niet anders omgeleid, worden altijd naar het scherm verzonden. Typen $loc, ziet uw huidige locatie:

```
PS> $loc

Path
----
C:\temp
```

U kunt **Get-lid** om informatie over de inhoud van variabelen weer te geven. $Loc aan Get-lid sluizen ziet u dat het is een **PathInfo** object, net als de uitvoer van Get-locatie:

```
PS> $loc | Get-Member -MemberType Property

   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   System.String Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {...
ProviderPath Property   System.String ProviderPath {get;}
```

### <a name="manipulating-variables"></a>Variabelen bewerken
PowerShell levert een aantal opdrachten voor het bewerken van variabelen. Een volledige lijst in een leesbare vorm kunt u zien door te typen:

```
Get-Command -Noun Variable | Format-Table -Property Name,Definition -AutoSize -Wrap
```

Naast de variabelen die u in uw huidige PowerShell-sessie maken, zijn er verschillende systeem gedefinieerde variabelen. U kunt de **Remove-Variable** cmdlet op te ruimen alle variabelen die niet worden beheerd door PowerShell. Typ de volgende opdracht om te wissen van alle variabelen:

```
Remove-Variable -Name * -Force -ErrorAction SilentlyContinue
```

Het resultaat bevestiging wordt gevraagd die u hieronder ziet.

```
Confirm
Are you sure you want to perform this action?
Performing operation "Remove Variable" on Target "Name: Error".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):A
```

Als u vervolgens de **Get-Variable** cmdlet, ziet u de resterende PowerShell-variabelen. Omdat er ook een variabele PowerShell-station, kunt u alle PowerShell-variabelen ook weergeven door te typen:

```
Get-ChildItem variable:
```

### <a name="using-cmdexe-variables"></a>Gebruik van variabelen Cmd.exe
Hoewel PowerShell niet Cmd.exe, wordt uitgevoerd in een opdracht shell-omgeving en kunt u de dezelfde variabelen die beschikbaar zijn in elke omgeving van Windows gebruiken. Deze variabelen worden weergegeven via een station met de naam **env**:. U kunt deze variabelen weergeven door te typen:

```
Get-ChildItem env:
```

Hoewel de standaard variabele cmdlets niet ontworpen zijn voor gebruik met **env:** variabelen, kunt u ze door te geven de **env:** voorvoegsel. Bijvoorbeeld, om te zien in de hoofdmap van het besturingssysteem, kunt u de opdrachtshell **% SystemRoot %** variabele van PowerShell door te typen:

```
PS> $env:SystemRoot
C:\WINDOWS
```

U kunt ook maken en wijzigen van omgevingsvariabelen van PowerShell. Omgevingsvariabelen toegankelijk vanuit Windows PowerShell voldoen aan de normale regels voor omgevingsvariabelen elders in Windows.