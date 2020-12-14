---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-runspacedebug?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-RunspaceDebug
ms.openlocfilehash: a77695fe32345fda8e6a0284cd29becb432a4273
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705932"
---
# Get-RunspaceDebug

## SAMENVATTING
Hiermee worden opties voor fout opsporing in runs weer gegeven.

## SYNTAXIS

### RunspaceNameParameterSet (standaard)

```
Get-RunspaceDebug [[-RunspaceName] <String[]>] [<CommonParameters>]
```

### RunspaceParameterSet

```
Get-RunspaceDebug [-Runspace] <Runspace[]> [<CommonParameters>]
```

### RunspaceIdParameterSet

```
Get-RunspaceDebug [-RunspaceId] <Int32[]> [<CommonParameters>]
```

### RunspaceInstanceIdParameterSet

```
Get-RunspaceDebug [-RunspaceInstanceId] <Guid[]> [<CommonParameters>]
```

### ProcessNameParameterSet

```
Get-RunspaceDebug [[-ProcessName] <String>] [[-AppDomainName] <String[]>] [<CommonParameters>]
```

## BESCHRIJVING

Met de `Get-RunspaceDebug` cmdlet worden de opties voor fout opsporing in runs weer gegeven.

## VOORBEELDEN

### 1: de status van de standaard fout opsporing voor runs Pace weer geven

```powershell
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

[Disable-RunspaceDebug](Disable-RunspaceDebug.md)

[Enable-RunspaceDebug](Enable-RunspaceDebug.md)

