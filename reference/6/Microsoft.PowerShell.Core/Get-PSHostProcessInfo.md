---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-pshostprocessinfo?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSHostProcessInfo
ms.openlocfilehash: 24ebb507b2f9544115d6309b0a91d8b19b0745ec
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250969"
---
# Get-PSHostProcessInfo

## SAMENVATTING
Hiermee wordt proces informatie over de Power shell-host opgehaald.

## SYNTAXIS

### ProcessNameParameterSet (standaard)

```
Get-PSHostProcessInfo [[-Name] <String[]>] [<CommonParameters>]
```

### ProcessParameterSet

```
Get-PSHostProcessInfo [-Process] <Process[]> [<CommonParameters>]
```

### ProcessIdParameterSet

```
Get-PSHostProcessInfo [-Id] <Int32[]> [<CommonParameters>]
```

## BESCHRIJVING

De `Get-PSHostProcessInfo` cmdlet haalt informatie op over de Power shell-hostproces processen die op de lokale computer worden uitgevoerd.

Vanaf Power shell 6,2 wordt deze cmdlet ondersteund op niet-Windows-platforms.

## VOORBEELDEN

### 1: een lijst met Power shell-hosts die worden uitgevoerd op het systeem ophalen

```powershell
Get-PSHostProcessInfo
```

```Output
ProcessName ProcessId AppDomainName
----------- --------- -------------
powershell      11204 DefaultAppDomain
pwsh            13912 DefaultAppDomain
```

### 2: informatie over de Power shell-host ophalen voor een specifieke proces naam

```powershell
Get-PSHostProcessInfo -Name pwsh
```

```Output
ProcessName ProcessId AppDomainName
----------- --------- -------------
pwsh            13912 DefaultAppDomain
```

## PARAMETERS

### -Id

Hiermee geeft u een proces met de proces-ID op. Voer de cmdlet uit om een proces-ID op te halen `Get-Process` .

```yaml
Type: System.Int32[]
Parameter Sets: ProcessIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Hiermee geeft u een proces op met de proces naam. Voer de cmdlet uit om een proces naam op te halen `Get-Process` .

```yaml
Type: System.String[]
Parameter Sets: ProcessNameParameterSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Proces

Hiermee geeft u een proces op voor het proces object. De eenvoudigste manier om deze para meter te gebruiken is het opslaan van de resultaten van een `Get-Process` opdracht die het proces retourneert dat u in een variabele wilt invoeren, en vervolgens geeft u de variabele op als de waarde van deze para meter.

```yaml
Type: System.Diagnostics.Process[]
Parameter Sets: ProcessParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. Diagnostics. process

U kunt een **proces** object door sluizen van `Get-Process` naar deze cmdlet.

## UITVOER

### Micro soft. Power shell. commands. PSHostProcessInfo

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Get-Process](../Microsoft.PowerShell.Management/get-process.md)
