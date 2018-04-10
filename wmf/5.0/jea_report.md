---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installeren
ms.openlocfilehash: 2af56be1915c148809f52cd9040c45da160ae0a2
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="reporting-on-jea"></a>Rapportage over JEA
Om te rapporteren over de status van de configuratie van uw JEA, kunt u het volgende gebruiken:
1.  **Get-PSSessionConfiguration** geregistreerd om te retourneren van een lijst met alle eindpunten op een bepaalde computer.
2.  **Get-PSSessionCapability** om te rapporteren over de mogelijkheden voor een bepaalde gebruiker op een specifieke eindpunt heeft.

Hier volgt een voorbeeld van **Get-PSSessionCapability**:
```powershell
Get-PSSessionCapability -ConfigurationName Maintenance -Username "CONTOSO\JohnDoe"

CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           clear -> Clear-Host
Alias           cls -> Clear-Host
Alias           exsn -> Exit-PSSession
Alias           gcm -> Get-Command
Alias           measure -> Measure-Object
Alias           select -> Select-Object
Function        Clear-Host
Function        Exit-PSSession
Function        Get-Command
Function        Get-FormatData
Function        Get-Help
Function        Get-UserInfo
Function        Measure-Object
Function        Out-Default
Function        Select-Object
Cmdlet          Restart-Service                                    3.0.0.0 Microsof...


```

Om te rapporteren over de _acties_ gebruikers tijdens een sessie JEA duurde, kunt u:
1. Schakel de transcripties 'failover-de-schouder' voor dat eindpunt JEA en raadpleegt u de map met de tekst voor een volledige logboek van acties van elke gebruiker
2. PowerShell-module logboekregistratie inschakelen en controleren van de PowerShell-gebeurtenislogboeken.