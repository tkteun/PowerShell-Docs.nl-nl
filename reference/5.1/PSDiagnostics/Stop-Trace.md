---
external help file: PSDiagnostics-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/stop-trace?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Trace
ms.openlocfilehash: 917f9f0eb4b9dfaf08c21a06f895d73c71bff5dd
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250325"
---
# Stop-Trace

## SAMENVATTING
Stop een logboek registratie sessie voor gebeurtenis tracering.

## SYNTAXIS

```
Stop-Trace [-SessionName] <Object> [-ETS] [<CommonParameters>]
```

## BESCHRIJVING

Met deze cmdlet wordt een Windows-sessie voor logboek registratie van gebeurtenissen gestopt.

Deze cmdlet wordt gebruikt door de volgende cmdlets:

- `Disable-PSWSManCombinedTrace`
- `Disable-WSManTrace`

U moet deze cmdlet uitvoeren vanuit een Power shell-sessie met verhoogde bevoegdheden.

## VOORBEELDEN

### Voor beeld 1: een sessie met WSMan-traceer logboeken stoppen

```powershell
Stop-Trace -SessionName 'wsmlog'
```

## PARAMETERS

### -ETS
Opdrachten zonder opslaan of plannen rechtstreeks naar Gebeurtenissessies Trace kunnen verzenden.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Sessie naam
De naam van de gebeurtenis tracerings sessie die moet worden gestopt.

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Geen

## UITVOER

### System. object

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Gebeurtenis tracering](/windows/desktop/ETW/event-tracing-portal)

[Start-traceren](start-trace.md)

[Disable-PSWSManCombinedTrace](Disable-PSWSManCombinedTrace.md)

[Disable-WSManTrace](Disable-WSManTrace.md)

[Enable-PSWSManCombinedTrace](Enable-PSWSManCombinedTrace.md)

[Enable-WSManTrace](Enable-WSManTrace.md)
