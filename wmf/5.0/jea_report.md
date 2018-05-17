---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 7982acc111e95b4167f948314f176d53f39d3620
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2018
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
