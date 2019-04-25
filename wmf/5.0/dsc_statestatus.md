---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: ff2c2bd7369893d72db001ecabf63991ded0bfd5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058978"
---
# <a name="unified-and-consistent-state-and-status-representation"></a>Uniforme en consistente status en statusweergave

Een reeks verbeteringen zijn aangebracht in deze release voor automatische ingebouwd LCM-status en DSC-status. Uniforme en consistente status en de status verklaringen, beheerbare datetime-eigenschap van de van statusobjecten die worden geretourneerd door het gaat hierbij `Get-DscConfigurationStatus` cmdlet en verbeterde LCM staat details van de eigenschap die wordt geretourneerd door `Get-DscLocalConfigurationManager` cmdlet.

De weergave van LCM-status en de status van de DSC-bewerking worden herzien en geïntegreerde op basis van de volgende regels:

1. NotProcessed weer resource heeft geen invloed op LCM-status en DSC-status.
2. LCM stoppen verdere informatie verwerken zodra er een resource die opnieuw opstarten aanvragen wordt aangetroffen.
3. Een resource die opnieuw opstarten aanvragen is niet in de gewenste status totdat opnieuw opstarten daadwerkelijk gebeurt.
4. Na het vaststellen van een resource die is mislukt, houdt LCM verwerken van meer resources, zolang ze niet afhankelijk van de fout een zijn.
5. De algemene status geretourneerd door `Get-DscConfigurationStatus` cmdlet is de super set alle resources de status.
6. De status PendingReboot is een superset van PendingConfiguration staat.

De onderstaande tabel ziet u de resulterende status en de status eigenschappen met betrekking tot onder een aantal typische scenario's.

| Scenario                        | LCMState             | Status     | Opnieuw opstarten aangevraagd | ResourcesInDesiredState   | ResourcesNotInDesiredState |
|---------------------------------|----------------------|------------|---------------|------------------------------|--------------------------------|
| S<sub>i</sub>                   | Actieve                 | Geslaagd    | $false        | S                            | $null                          |
| F<sub>i</sub>                   | PendingConfiguration | Mislukt    | $false        | $null                        | F                              |
| S,F                             | PendingConfiguration | Mislukt    | $false        | S                            | F                              |
| F,S                             | PendingConfiguration | Mislukt    | $false        | S                            | F                              |
| S<sub>1</sub>, F, S<sub>2</sub> | PendingConfiguration | Mislukt    | $false        | S<sub>1</sub>, S<sub>2</sub> | F                              |
| F<sub>1</sub>, S, F<sub>2</sub> | PendingConfiguration | Mislukt    | $false        | S                            | F<sub>1</sub>, F<sub>2</sub>   |
| S, r                            | PendingReboot        | Geslaagd    | $true         | S                            | r                              |
| F, r                            | PendingReboot        | Mislukt    | $true         | $null                        | F, r                           |
| r, S                            | PendingReboot        | Geslaagd    | $true         | $null                        | r                              |
| r, F                            | PendingReboot        | Geslaagd    | $true         | $null                        | r                              |

- S<sub>i</sub>: Een reeks resources die is toegepast
- F<sub>i</sub>: Een reeks resources die zonder succes toegepast
- R: Een resource die is vereist opnieuw opstarten

```powershell
$LCMState = (Get-DscLocalConfigurationManager).LCMState
$Status = (Get-DscConfigurationStatus).Status

$RebootRequested = (Get-DscConfigurationStatus).RebootRequested

$ResourcesInDesiredState = (Get-DscConfigurationStatus).ResourcesInDesiredState

$ResourcesNotInDesiredState = (Get-DscConfigurationStatus).ResourcesNotInDesiredState
```

## <a name="enhancement-in-get-dscconfigurationstatus-cmdlet"></a>Uitbreiding in de cmdlet Get-DscConfigurationStatus

Er zijn enkele verbeteringen zijn aangebracht aan `Get-DscConfigurationStatus` cmdlet in deze release. De eigenschap StartDate van objecten die worden geretourneerd door de cmdlet is eerder, van het type tekenreeks. Het is nu, van het type Datetime, waarmee complexe selecteren en filteren eenvoudiger op basis van de ingebouwde eigenschappen van een datum/tijd-object.

```powershell
(Get-DscConfigurationStatus).StartDate | Format-List *

DateTime    : Friday, November 13, 2015 1:39:44 PM
Date        : 11/13/2015 12:00:00 AM
Day         : 13
DayOfWeek   : Friday
DayOfYear   : 317
Hour        : 13
Kind        : Local
Millisecond : 886
Minute      : 39
Month       : 11
Second      : 44
Ticks       : 635830187848860000
TimeOfDay   : 13:39:44.8860000
Year        : 2015
```

Het volgende voorbeeld retourneert alle records van DSC-bewerking die hebben plaatsgevonden op dezelfde dag van week als de huidige dag.

```powershell
(Get-DscConfigurationStatus –All) | Where-Object { $_.startdate.dayofweek -eq (Get-Date).DayOfWeek }
```

Records van bewerkingen die geen wijzigingen in van het knooppunt configuratie aanbrengen mag (dat wil zeggen alleen bewerkingen lezen) worden geëlimineerd. Daarom `Test-DscConfiguration`, `Get-DscConfiguration` bewerkingen zijn niet meer in de geretourneerde objecten uit verontreinigde `Get-DscConfigurationStatus` cmdlet. Records van meta-configuratie-instelling bewerking wordt toegevoegd aan het rendement van `Get-DscConfigurationStatus` cmdlet.

Hieronder volgt een voorbeeld van resultaat geretourneerd vanuit `Get-DscConfigurationStatus –All` cmdlet.

```output
All configuration operations:

Status StartDate Type RebootRequested
------ --------- ---- ---------------
Success 11/13/2015 11:38:16 AM Consistency False
Success 11/13/2015 11:23:16 AM Reboot False
Success 11/13/2015 11:21:43 AM Reboot True
Success 11/13/2015 11:20:44 AM Initial True
Success 11/13/2015 11:20:44 AM LocalConfigurationManager False
```

## <a name="enhancement-in-get-dsclocalconfigurationmanager-cmdlet"></a>Uitbreiding in de cmdlet Get-DscLocalConfigurationManager

Een nieuw veld van LCMStateDetail wordt toegevoegd aan het object dat wordt geretourneerd vanaf `Get-DscLocalConfigurationManager` cmdlet. Dit veld wordt gevuld wanneer LCMState is 'Bezet'. Het kan worden opgehaald door de volgende cmdlet:

```powershell
(Get-DscLocalConfigurationManager).LCMStateDetail
```

Hieronder volgt een voorbeeld van uitvoer van een doorlopende bewaking van een configuratie waarvoor twee keer opnieuw opstarten op een externe knooppunt.

```output
Start a configuration that requires two reboots

Monitor LCM State:
LCM State: Busy, LCM is applying a new configuration.
LCM State: PendingReboot,
Machine is rebooting...
LCM State: Busy, LCM is continuing applying configuration after last reboot.
LCM State: PendingReboot,
Machine is rebooting...
LCM State: Busy, LCM is continuing applying configuration after last reboot.
LCM State: Idle,
LCM State: Busy, LCM is performing a consistency check.
LCM State: Idle,
```
