---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/enable-runspacedebug?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-RunspaceDebug
ms.openlocfilehash: 54fb9500a924d2e5de98489fa4fb391accb23d0c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250461"
---
# Enable-RunspaceDebug

## SAMENVATTING
Hiermee schakelt u fout opsporing in voor runspaces waarbij een onderbrekings punt wordt bewaard totdat er een fout opsporingsprogramma is gekoppeld.

## SYNTAXIS

### RunspaceNameParameterSet (standaard)

```
Enable-RunspaceDebug [-BreakAll] [[-RunspaceName] <String[]>] [<CommonParameters>]
```

### RunspaceParameterSet

```
Enable-RunspaceDebug [-BreakAll] [-Runspace] <Runspace[]> [<CommonParameters>]
```

### RunspaceIdParameterSet

```
Enable-RunspaceDebug [-BreakAll] [-RunspaceId] <Int32[]> [<CommonParameters>]
```

### RunspaceInstanceIdParameterSet

```
Enable-RunspaceDebug [-RunspaceInstanceId] <Guid[]> [<CommonParameters>]
```

### ProcessNameParameterSet

```
Enable-RunspaceDebug [[-ProcessName] <String>] [[-AppDomainName] <String[]>] [<CommonParameters>]
```

## BESCHRIJVING

De `Enable-RunspaceDebug` cmdlet schakelt fout opsporing in voor runspaces waarbij een onderbrekings punt wordt bewaard totdat er een fout opsporingsprogramma is gekoppeld.

## VOORBEELDEN

### 1: de standaard runs Pace-fout opsporing inschakelen

```powershell
Enable-RunspaceDebug
Get-RunspaceDebug
```

```Output
 Id Name                 Enabled    BreakAll
 -- ----                 -------    --------
  1 Runspace1            True       False
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

### -BreakAll

Zorgt ervoor dat een wille keurige opdracht of script in de runs Pace stopt in stap modus, ongeacht of er momenteel een fout opsporingsprogramma is gekoppeld. Het script of de opdracht blijft actief totdat er een fout opsporingsprogramma is gekoppeld aan het opsporen van fouten in het huidige stop punt.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: RunspaceNameParameterSet, RunspaceParameterSet, RunspaceIdParameterSet
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

[Get-RunspaceDebug](Get-RunspaceDebug.md)
