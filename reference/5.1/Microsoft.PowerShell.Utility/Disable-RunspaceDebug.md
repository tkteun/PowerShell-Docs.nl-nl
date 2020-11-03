---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/disable-runspacedebug?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-RunspaceDebug
ms.openlocfilehash: 79fe5c58f26f9146adfca18827f65cff53bde23f
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250462"
---
# Disable-RunspaceDebug

## SAMENVATTING
Hiermee schakelt u fout opsporing op een of meer runspaces uit en worden alle in behandeling zijnde debugging stoppen vrijgegeven.

## SYNTAXIS

### RunspaceNameParameterSet (standaard)

```
Disable-RunspaceDebug [[-RunspaceName] <String[]>] [<CommonParameters>]
```

### RunspaceParameterSet

```
Disable-RunspaceDebug [-Runspace] <Runspace[]> [<CommonParameters>]
```

### RunspaceIdParameterSet

```
Disable-RunspaceDebug [-RunspaceId] <Int32[]> [<CommonParameters>]
```

### RunspaceInstanceIdParameterSet

```
Disable-RunspaceDebug [-RunspaceInstanceId] <Guid[]> [<CommonParameters>]
```

### ProcessNameParameterSet

```
Disable-RunspaceDebug [[-ProcessName] <String>] [[-AppDomainName] <String[]>] [<CommonParameters>]
```

## BESCHRIJVING

Met de `Disable-RunspaceDebug` cmdlet wordt fout opsporing op een of meer runspaces uitgeschakeld en worden alle in behandeling zijnde debugging gestopt.

## VOORBEELDEN

### 1: de standaard runs Pace-fout opsporing uitschakelen

```powershell
Disable-RunspaceDebug
Get-RunspaceDebug
```

```Output
 Id Name                 Enabled    BreakAll
 -- ----                 -------    --------
  1 Runspace1            False      False
```

## PARAMETERS

### -AppDomainName

De naam van het toepassings domein dat als host fungeert voor de Power shell-runs Pace.

```yaml
Type: System.String[]
Parameter Sets: ProcessNameParameterSet
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Procesnaam

De naam van het proces dat als host fungeert voor de Power shell-runs Pace.

```yaml
Type: System.String
Parameter Sets: ProcessNameParameterSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Runs Pace

Een of meer **runs Pace** -objecten die moeten worden uitgeschakeld.

```yaml
Type: System.Management.Automation.Runspaces.Runspace[]
Parameter Sets: RunspaceParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -RunspaceId

Een of meer **runs Pace** -id-nummers die moeten worden uitgeschakeld.

```yaml
Type: System.Int32[]
Parameter Sets: RunspaceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RunspaceInstanceId

Een of meer **runs Pace** -guid's die moeten worden uitgeschakeld.

```yaml
Type: System.Guid[]
Parameter Sets: RunspaceInstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RunspaceName

Een of meer **runs Pace** -namen die moeten worden uitgeschakeld.

```yaml
Type: System.String[]
Parameter Sets: RunspaceNameParameterSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

## UITVOER

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Enable-RunspaceDebug](Enable-RunspaceDebug.md)

[Get-RunspaceDebug](Get-RunspaceDebug.md)
