---
ms.date: 08/27/2018
keywords: PowerShell-cmdlet
title: Variabelen gebruiken om objecten op te slaan
ms.assetid: b1688d73-c173-491e-9ba6-6d0c1cc852de
ms.openlocfilehash: d166ec58dc658c1b134030c9a9592249ee40d4f5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086541"
---
# <a name="using-variables-to-store-objects"></a>Variabelen gebruiken om objecten op te slaan

PowerShell in combinatie met objecten. PowerShell kunt u benoemde objecten bekend als variabelen maken.
Namen van variabelen kunnen het onderstrepingsteken en een alfanumerieke tekens bevatten. Wanneer gebruikt in PowerShell, een variabele altijd is opgegeven met behulp van de \$ gevolgd door de naam van variabele.

## <a name="creating-a-variable"></a>Het maken van een variabele

U kunt een variabele maken met een geldige variabele naam te typen:

```
PS> $loc
PS>
```

In dit voorbeeld retourneert geen resultaat omdat `$loc` heeft geen waarde. U kunt een variabele maken en hieraan een waarde in één stap. De variabele PowerShell alleen gemaakt als deze niet bestaat.
Anders wordt de opgegeven waarde toegewezen aan de bestaande variabele. Het volgende voorbeeld wordt de huidige locatie opgeslagen in de variabele `$loc`:

```powershell
$loc = Get-Location
```

Er is geen uitvoer wordt weergegeven wanneer u deze opdracht in PowerShell. PowerShell stuurt de uitvoer van Get-locatie naar `$loc`. Gegevens die niet is toegewezen of omgeleid is in PowerShell verzonden naar het scherm. Typen `$loc` ziet u uw huidige locatie:

```
PS> $loc

Path
----
C:\temp
```

U kunt `Get-Member` om informatie over de inhoud van variabelen weer te geven. `Get-Member` ziet u dat `$loc` is een **PathInfo** object, net als de uitvoer van `Get-Location`:

```powershell
PS> $loc | Get-Member -MemberType Property

   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   System.String Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {...
ProviderPath Property   System.String ProviderPath {get;}
```

## <a name="manipulating-variables"></a>Variabelen bewerken

PowerShell biedt diverse opdrachten voor het bewerken van variabelen. U kunt een volledige lijst in een leesbare vorm zien door te typen:

```powershell
Get-Command -Noun Variable | Format-Table -Property Name,Definition -AutoSize -Wrap
```

PowerShell maakt ook verschillende systeem gedefinieerde variabelen. U kunt de `Remove-Variable` cmdlet voor het verwijderen van variabelen, die niet worden beheerd met PowerShell, uit de huidige sessie. Typ de volgende opdracht om te wissen van alle variabelen:

```powershell
Remove-Variable -Name * -Force -ErrorAction SilentlyContinue
```

Na het uitvoeren van de vorige opdracht, de `Get-Variable` cmdlet ziet u de PowerShell-systeemvariabelen.

PowerShell maakt ook een variabele station. Gebruik het volgende voorbeeld om alle PowerShell-variabelen met behulp van de variabele station weer te geven:

```powershell
Get-ChildItem variable:
```

## <a name="using-cmdexe-variables"></a>Cmd.exe variabelen gebruiken

PowerShell kunt gebruiken de dezelfde omgevingsvariabelen die beschikbaar zijn voor alle Windows-proces, inclusief **cmd.exe**. Deze variabelen worden weergegeven via een station met de naam `env:`. U kunt deze variabelen weergeven door de volgende opdracht te typen:

```powershell
Get-ChildItem env:
```

De standaard `*-Variable` cmdlets zijn niet ontworpen voor gebruik met omgevingsvariabelen. Omgevingsvariabelen worden geopend met behulp van de `env:` stationsvoorvoegsel. Bijvoorbeeld, de **% SystemRoot %** variabele in **cmd.exe** bevat de naam van de map hoofdmap van het besturingssysteem. In PowerShell, gebruikt u `$env:SystemRoot` voor toegang tot dezelfde waarde.

```
PS> $env:SystemRoot
C:\WINDOWS
```

U kunt ook maken en wijzigen van omgevingsvariabelen uit in PowerShell. Omgevingsvariabelen in PowerShell volgt dezelfde regels gelden voor omgevingsvariabelen die elders in het besturingssysteem worden gebruikt. Het volgende voorbeeld wordt een nieuwe omgevingsvariabele:

```powershell
$env:LIB_PATH='/usr/local/lib'
```

Hoewel dit niet vereist, is het gebruikelijk dat namen van omgevingsvariabelen gebruiken alle hoofdletters.
