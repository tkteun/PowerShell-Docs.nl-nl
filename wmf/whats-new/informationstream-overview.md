---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
title: Gegevensstroom
ms.openlocfilehash: c54603cf0dd4f0b69f8147620130f9f29bc3e5ec
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856383"
---
# <a name="information-stream"></a>Gegevensstroom

PowerShell 5.0 voegt een nieuwe gestructureerde **informatie** stream om gestructureerde gegevens tussen een script en de host te verzenden. `Write-Host` is ook bijgewerkt voor het verzenden van de uitvoer naar de **informatie** stream kunt u nu vastleggen of het stilte. De nieuwe `Write-Information` cmdlet die wordt gebruikt met **InformationVariable** en **InformationAction** algemene parameters kunt u meer flexibiliteit en mogelijkheden.

De volgende functie maakt gebruik van cmdlets die van de nieuwe gebruikmaken **informatie** stream.

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

De volgende voorbeelden tonen de resultaten van het uitvoeren van deze functie.

```powershell
$r = c:\temp\OutputGusher
```

```Output
Preparing to give you output!
=============================
I <3 Output
=============================

SCRIPT COMPLETE!!
```

De `$r` variabele de procesinformatie in de script-variabele heeft vastgelegd `$p`.

```powershell
$r.Id
4008
```

In tegenstelling tot de `Write-Host` cmdlet, met behulp van de **InformationVariable** parameter van `Write-Information` kunt u om vast te leggen van de uitvoer in een variabele. Met behulp van de **Tag**, kunt u afzonderlijke kanalen voor het bericht is verzonden naar de **informatie** stream.

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

Wanneer u een bericht verzendt de **informatie** stream met een label, dat bericht wordt pas weergegeven in de hosttoepassing, maar kunnen worden opgehaald met de naam van de tag. Bijvoorbeeld:

```powershell
$iv | where Tags -eq 'LogHigh'
```

```Output
Some important logging information
```