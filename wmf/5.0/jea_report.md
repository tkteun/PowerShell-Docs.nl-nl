---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: cd3338ae305896e282056a871974e5f899ef6ff5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686241"
---
# <a name="reporting-on-jea"></a>Rapportage over JEA

Als u wilt rapporteren over de status van de JEA-configuratie, kunt u het volgende gebruiken:

1. **Get-PSSessionConfiguration** geregistreerd om terug te keren een lijst van alle eindpunten op een bepaalde computer.
2. **Get-PSSessionCapability** om te rapporteren over de mogelijkheden voor een bepaalde gebruiker is op een bepaald eindpunt.

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

Om te rapporteren over de _acties_ gebruikers duurde tijdens een JEA-sessie, kunt u:

1. De "over-the-schouder" Transcripten voor dat JEA-eindpunt inschakelen en raadpleegt u de map transcript voor een volledige logboek van acties van elke gebruiker
2. PowerShell-module logboekregistratie inschakelen en controleren van de PowerShell-gebeurtenislogboeken.