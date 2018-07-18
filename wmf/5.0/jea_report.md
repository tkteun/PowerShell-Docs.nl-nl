---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 2fb2e4b0c40322b5ec78fabede22a7e3ecbbd2aa
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/17/2018
ms.locfileid: "39093759"
---
# <a name="reporting-on-jea"></a>Rapportage over JEA

Als u wilt rapporteren over de status van de JEA-configuratie, kunt u het volgende gebruiken:

1. **Get-PSSessionConfiguration** geregistreerd om terug te keren een lijst van alle eindpunten op een bepaalde computer.
1. **Get-PSSessionCapability** om te rapporteren over de mogelijkheden voor een bepaalde gebruiker is op een bepaald eindpunt.

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
