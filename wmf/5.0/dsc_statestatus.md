---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installeren
ms.openlocfilehash: 32f8e20889ddc526def4b925e8d0761a2e851e19
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/20/2018
---
# <a name="unified-and-consistent-state-and-status-representation"></a>Uniforme en consistente status en statusweergave

Een reeks verbeteringen zijn aangebracht in deze release voor automatische LCM toestand en status van de DSC gebouwd. Dit omvat uniforme en consistente status en status verklaringen, beheerbare datetime-eigenschap van status objecten geretourneerd door de cmdlet Get-DscConfigurationStatus en verbeterde LCM status details eigenschap die is geretourneerd door Get-DscLocalConfigurationManager cmdlet.

De weergave van LCM status en de status van de DSC-bewerking worden herzien en uniform volgens de volgende regels:
1.  NotProcessed weer resource heeft geen gevolgen voor LCM toestand en DSC-status.
2.  LCM stoppen verdere resources voor het verwerken zodra er een resource die aanvragen van opnieuw opstarten wordt aangetroffen.
3.  Een resource die aanvragen van opnieuw opstarten is niet in de gewenste status totdat opnieuw opstarten feitelijk plaatsvindt.
4.  Na het vaststellen van een resource die is mislukt, houdt LCM verwerking van verdere resources zo lang ze zijn niet afhankelijk van de fout een.
5.  De algehele status geretourneerd door de cmdlet Get-DscConfigurationStatus is de super set van alle resources status.
6.  De status PendingReboot is een hoofdverzameling van PendingConfiguration status.

De volgende tabel ziet u de resulterende toestand en status gerelateerd eigenschappen onder enkele typische scenario's.

| **Scenario**                    | **LCMState\***       | **Status** | **Opnieuw opstarten aangevraagd**  | **ResourcesInDesiredState**  | **ResourcesNotInDesiredState** |
|---------------------------------|----------------------|------------|---------------|------------------------------|--------------------------------|
| S**^**                          | Actieve                 | Geslaagd    | $false        | S                            | $null                          |
| F**^**                          | PendingConfiguration | Mislukt    | $false        | $null                        | F                              |
| S, F                             | PendingConfiguration | Mislukt    | $false        | S                            | F                              |
| F,S                             | PendingConfiguration | Mislukt    | $false        | S                            | F                              |
| S<sub>1</sub>, F, S<sub>2</sub> | PendingConfiguration | Mislukt    | $false        | S<sub>1</sub>, S<sub>2</sub> | F                              |
| F<sub>1</sub>, S, F<sub>2</sub> | PendingConfiguration | Mislukt    | $false        | S                            | F<sub>1</sub>, F<sub>2</sub>   |
| S, r                            | PendingReboot        | Geslaagd    | $true         | S                            | r                              |
| F, r                            | PendingReboot        | Mislukt    | $true         | $null                        | F, r                           |
| r, S                            | PendingReboot        | Geslaagd    | $true         | $null                        | r                              |
| r, F                            | PendingReboot        | Geslaagd    | $true         | $null                        | r                              |

^ S<sub>ik</sub>: een reeks resources die F toegepast<sub>ik</sub>: een reeks resources die wordt toegepast zonder succes r: een bron die opnieuw opstarten vereist \*

```powershell
$LCMState = (Get-DscLocalConfigurationManager).LCMState
$Status = (Get-DscConfigurationStatus).Status

$RebootRequested = (Get-DscConfigurationStatus).RebootRequested

$ResourcesInDesiredState = (Get-DscConfigurationStatus).ResourcesInDesiredState

$ResourcesNotInDesiredState = (Get-DscConfigurationStatus).ResourcesNotInDesiredState
```
## <a name="enhancement-in-get-dscconfigurationstatus-cmdlet"></a>Uitbreiding in de cmdlet Get-DscConfigurationStatus

Er zijn enkele verbeteringen zijn aangebracht aan de cmdlet Get-DscConfigurationStatus in deze release. De eigenschap StartDate van objecten die worden geretourneerd door de cmdlet is eerder van het tekenreekstype. Nu is van het type Datetime, waardoor complexe te selecteren en filteren eenvoudiger op basis van de intrinsieke eigenschappen van een datum/tijd-object.
```powershell
(Get-DscConfigurationStatus).StartDate | fl \*
DateTime : Friday, November 13, 2015 1:39:44 PM
Date : 11/13/2015 12:00:00 AM
Day : 13
DayOfWeek : Friday
DayOfYear : 317
Hour : 13
Kind : Local
Millisecond : 886
Minute : 39
Month : 11
Second : 44
Ticks : 635830187848860000
TimeOfDay : 13:39:44.8860000
Year : 2015
```

Hier volgt een voorbeeld waarin alle records voor DSC-bewerking is uitgevoerd op dezelfde dag van week vandaag retourneert.
```powershell
(Get-DscConfigurationStatus –All) | where { $\_.startdate.dayofweek -eq (Get-Date).DayOfWeek }
```

Records van bewerkingen die geen wijzigingen knooppuntconfiguratie aanbrengen, (dat wil zeggen leesbewerkingen alleen) worden geëlimineerd. Daarom Test-DscConfiguration Get DscConfiguration bewerkingen zijn niet langer verontreinigde objecten van de cmdlet Get-DscConfigurationStatus geretourneerd.
Records van de bewerking meta configuratie-instelling wordt toegevoegd aan het retourtype van de cmdlet Get-DscConfigurationStatus.

Hieronder volgt een voorbeeld van resultaat geretourneerd door Get-DscConfigurationStatus – alle cmdlet.
```powershell
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
Een nieuw veld van LCMStateDetail is toegevoegd aan het object dat wordt geretourneerd door de cmdlet Get-DscLocalConfigurationManager. Dit veld wordt gevuld wanneer LCMState 'Bezet' is. Het kan worden opgehaald met de volgende cmdlet:
```powershell
(Get-DscLocalConfigurationManager).LCMStateDetail
```

Hier volgt een voorbeeld van uitvoer van een doorlopende bewaking van een configuratie die twee keer opnieuw opstarten op een externe knooppunt vereist.
```powershell
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

