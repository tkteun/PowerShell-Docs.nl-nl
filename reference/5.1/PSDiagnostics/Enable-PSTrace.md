---
external help file: PSDiagnostics-help.xml
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/enable-pstrace?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSTrace
ms.openlocfilehash: 9abc91086d42ec7b813695e241820947f7fb0acc
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250333"
---
# Enable-PSTrace

## SAMENVATTING
Hiermee schakelt u de logboeken van de gebeurtenis provider van micro soft Windows-Power shell in.

## SYNTAXIS

```
Enable-PSTrace [-Force] [-AnalyticOnly]
```

## BESCHRIJVING

Met deze cmdlet worden de operationele en analytische gebeurtenis logboeken van de micro soft-Windows-Power shell-gebeurtenis provider ingeschakeld.

U moet deze cmdlet uitvoeren vanuit een Power shell-sessie met verhoogde bevoegdheden.

## VOORBEELDEN

### Voor beeld 1: het analytische gebeurtenis logboek inschakelen voor Power shell

In het volgende voor beeld wordt alleen het logboek van de analytische gebeurtenissen van de provider micro soft-Windows-Power shell ingeschakeld.

```powershell
Enable-PSTrace -AnalyticOnly
```

## PARAMETERS

### -AnalyticOnly

Als deze para meter wordt gebruikt, schakelt de cmdlet het logboek voor analyse gebeurtenissen van de provider micro soft-Windows-Power shell in. Het operationele gebeurtenis logboek is niet gewijzigd.

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

### -Force

Wordt gebruikt om de wijziging te forceren zonder te vragen.

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

## INVOER

### Geen

## UITVOER

### System. object

## OPMERKINGEN

Met deze cmdlet worden de- `Get-LogProperties` en- `Set-LogProperties` cmdlets gebruikt.

U moet deze cmdlet uitvoeren vanuit een Power shell-sessie met verhoogde bevoegdheden.

## GERELATEERDE KOPPELINGEN

[Get-LogProperties](Get-LogProperties.md)

[Set-LogProperties](Set-LogProperties.md)

[Disable-PSTrace](Disable-PSTrace.md)
