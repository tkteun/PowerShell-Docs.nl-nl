---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
title: Gegevensstroom
ms.openlocfilehash: 1a8df66f7489910b964ec398e90b76e9f30cd2e2
ms.sourcegitcommit: 87b9b989f261b52969e99159e99ee28ad8d8839a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/21/2020
ms.locfileid: "86567838"
---
# <a name="information-stream"></a>Gegevensstroom

Power shell 5,0 voegt een nieuwe gestructureerde **informatie** stroom toe voor het verzenden van gestructureerde gegevens tussen een script en de host. `Write-Host` is ook bijgewerkt met het verzenden van de uitvoer naar de **informatie** stroom waar u deze nu kunt vastleggen of stilte. De nieuwe `Write-Information` cmdlet die wordt gebruikt met de algemene para meters **InformationVariable** en **Information Action** biedt meer flexibiliteit en meer mogelijkheden.

De volgende functie maakt gebruik van cmdlets die gebruikmaken van de nieuwe **informatie** stroom.

```powershell
function OutputGusher {
  [CmdletBinding()]
  param()
  Write-Host -ForegroundColor Green 'Preparing to give you output!'
  Write-Host '============================='
  Write-Host 'I ' -ForegroundColor White -NoNewline
  Write-Host '<3 ' -ForegroundColor Red -NoNewline
  Write-Host 'Output' -ForegroundColor White
  Write-Host '============================='

  $p = Get-Process -id $pid
  $p

  Write-Information $p -Tag Process
  Write-Information 'Some spammy logging information' -Tag LogLow
  Write-Information 'Some important logging information' -Tag LogHigh

  Write-Host
  Write-Host -ForegroundColor Green 'SCRIPT COMPLETE!!'
}
```

In de volgende voor beelden ziet u de resultaten van het uitvoeren van deze functie.

```powershell
$r = OutputGusher
```

```Output
Preparing to give you output!
=============================
I <3 Output
=============================

SCRIPT COMPLETE!!
```

De `$r` variabele heeft de proces informatie vastgelegd in de script variabele `$p` .

```powershell
$r.Id
4008
```

In tegens telling tot de `Write-Host` cmdlet kunt u met de para meter **InformationVariable** van `Write-Information` de uitvoer vastleggen in een variabele. Met behulp van de- **tag**kunt u afzonderlijke kanalen maken voor het bericht dat naar de **informatie** stroom wordt verzonden.

```powershell
$r = OutputGusher -InformationVariable iv
$ivOutput = $iv | Group-Object -AsHash { $_.Tags[0] } -AsString
$ivOutput
```

```Output
Preparing to give you output!
=============================
I <3 Output
=============================
SCRIPT COMPLETE!!

Name                 Value
----                 -----
LogLow               {Some spammy logging information}
LogHigh              {Some important logging information}
Process              {System.Diagnostics.Process (powershell)}
PSHOST               {Preparing to give you output!, =============================, I , <3 ...}
```

Wanneer u een bericht verzendt naar de **informatie** stroom met een tag, wordt dat bericht niet weer gegeven in de hosttoepassing, maar kan het worden opgehaald met de label naam. Bijvoorbeeld:

```powershell
$iv | where Tags -eq 'LogHigh'
```

```Output
Some important logging information
```
