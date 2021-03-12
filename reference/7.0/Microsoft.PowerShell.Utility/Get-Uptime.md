---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-uptime?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Uptime
ms.openlocfilehash: df4091609f403a58749a6821044d768089cdc03c
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/12/2021
ms.locfileid: "103194570"
---
# Get-Uptime

## SAMENVATTING
Haal de **tijds duur** op sinds de laatste keer dat deze is opgestart.

## SYNTAXIS

### Time span (standaard)

```
Get-Uptime [<CommonParameters>]
```

### Moment

```
Get-Uptime [-Since] [<CommonParameters>]
```

## BESCHRIJVING

Deze cmdlet retourneert de tijd die is verstreken sinds de laatste keer dat het besturings systeem is opgestart.

De `Get-Uptime` cmdlet is geïntroduceerd in Power shell 6,0.

## VOORBEELDEN

### Voor beeld 1: tijd weer geven sinds laatste keer opstarten

```powershell
Get-Uptime
```

```Output
Days              : 9
Hours             : 0
Minutes           : 9
Seconds           : 45
Milliseconds      : 0
Ticks             : 7781850000000
TotalDays         : 9.00677083333333
TotalHours        : 216.1625
TotalMinutes      : 12969.75
TotalSeconds      : 778185
TotalMilliseconds : 778185000
```

### Voor beeld 2: de tijd van de laatste keer opstarten weer geven

```powershell
Get-Uptime -Since
```

```Output
Tuesday, June 18, 2019 2:34:56 PM
```

## PARAMETERS

### -Sinds

Zorgt ervoor dat de cmdlet een **DateTime** -object retourneert dat de laatste keer dat het besturings systeem is opgestart.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Since
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Geen

## UITVOER

### System. time span

Dit is het standaard retour type wanneer er geen para meters worden gebruikt.

### System. DateTime

Dit type wordt geretourneerd wanneer de **sinds** -para meter wordt gebruikt.

> [!NOTE]
> Als Windows snel opstarten is ingeschakeld, wordt de waarde die is opgeslagen in **LastBootUpTime** niet door Windows bijgewerkt. Als u snel opstarten wilt uitschakelen, voert u de volgende opdracht uit: `Powercfg -h off` .
>
> Zie voor meer informatie over het snel opstarten van Windows een [onderscheid maken tussen snel opstarten vanuit](/windows-hardware/drivers/kernel/distinguishing-fast-startup-from-wake-from-hibernation)de slaap stand.

## OPMERKINGEN

In Windows is de geretourneerde waarde hetzelfde als de eigenschap **LastBootUpTime** van de klasse **Win32_OperatingSystem** in WMI.

## GERELATEERDE KOPPELINGEN

[Win32_OperatingSystem](/windows/win32/cimwin32prov/win32-operatingsystem#properties)
