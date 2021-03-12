---
external help file: PSDiagnostics-help.xml
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/disable-pstrace?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSTrace
ms.openlocfilehash: 50d4118c5805a59d291d8dd17f467e7b47d34b46
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/12/2021
ms.locfileid: "103194508"
---
# Disable-PSTrace

## SAMENVATTING
Hiermee schakelt u de logboeken van de micro soft-Windows-Power shell-gebeurtenis provider uit.

## SYNTAXIS

```
Disable-PSTrace [-AnalyticOnly] [<CommonParameters>]
```

## BESCHRIJVING

Met deze cmdlet worden de operationele en analytische gebeurtenis logboeken van de micro soft-Windows-Power shell-gebeurtenis provider uitgeschakeld.

U moet deze cmdlet uitvoeren vanuit een Power shell-sessie met verhoogde bevoegdheden.

## VOORBEELDEN

### Voor beeld 1: het analytische gebeurtenis logboek uitschakelen voor Power shell

In het volgende voor beeld wordt alleen het analytische gebeurtenis logboek van de provider micro soft-Windows-Power shell uitgeschakeld.

```powershell
Disable-PSTrace -AnalyticOnly
```

## PARAMETERS

### -AnalyticOnly

Als deze para meter wordt gebruikt, schakelt de cmdlet het logboek voor analyse gebeurtenissen van de provider micro soft-Windows-Power shell uit. Het operationele gebeurtenis logboek is niet gewijzigd.

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

[Enable-PSTrace](Enable-PSTrace.md)
