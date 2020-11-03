---
external help file: PSDiagnostics-help.xml
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/enable-pstrace?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSTrace
ms.openlocfilehash: fea84d9ae83eae88f9a665e8a49aaf2e6743127d
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249797"
---
# Enable-PSTrace

## SAMENVATTING
Hiermee schakelt u de logboeken van de gebeurtenis provider van micro soft Windows-Power shell in.

## SYNTAXIS

```
Enable-PSTrace [-Force] [-AnalyticOnly] [<CommonParameters>]
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

### CommonParameters
Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Geen

## UITVOER

### Geen

## OPMERKINGEN

Met deze cmdlet worden de- `Get-LogProperties` en- `Set-LogProperties` cmdlets gebruikt.

U moet deze cmdlet uitvoeren vanuit een Power shell-sessie met verhoogde bevoegdheden.

## GERELATEERDE KOPPELINGEN

[Get-LogProperties](Get-LogProperties.md)

[Set-LogProperties](Set-LogProperties.md)

[Disable-PSTrace](Disable-PSTrace.md)
