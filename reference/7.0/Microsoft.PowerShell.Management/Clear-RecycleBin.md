---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/clear-recyclebin?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-RecycleBin
ms.openlocfilehash: 4131232e7afb2e0a213bbe11f5da7ee3a0071a59
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/07/2020
ms.locfileid: "94344300"
---
# Clear-RecycleBin

## SAMENVATTING
Hiermee wordt de inhoud van een prullenbak gewist.

## SYNTAXIS

### Alles

```
Clear-RecycleBin [[-DriveLetter] <String[]>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

De `Clear-RecycleBin` cmdlet verwijdert de inhoud van de Prullenbak van een computer. Deze actie is vergelijkbaar met het gebruik van een prullenbak van Windows **Empty**.

Deze cmdlet is opnieuw toegevoegd in Power shell 7.

## VOORBEELDEN

### 1: alle prullen bakken wissen

In dit voor beeld worden alle prullen bakken van de lokale computer gewist.

```powershell
Clear-RecycleBin
```

```Output
Confirm
Are you sure you want to perform this action?
Performing the operation "Clear-RecycleBin" on target "All of the contents of the Recycle Bin".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

`Clear-RecycleBin` Hiermee wordt de gebruiker gevraagd om te bevestigen dat alle prullen bakken op de lokale computer moeten worden gewist.

### 2: een opgegeven Prullenbak wissen

In dit voor beeld wordt de Prullenbak voor een opgegeven stationsletter gewist.

```powershell
Clear-RecycleBin -DriveLetter C
```

`Clear-RecycleBin` gebruikt de **stationsletter** -para meter om de Prullenbak op het **C** -volume op te geven. De gebruiker wordt gevraagd om bevestiging om de opdracht uit te voeren.

### 3: alle prullen bakken wissen zonder bevestiging

In dit voor beeld wordt niet gevraagd om bevestiging om de prullen bakken van de lokale computer te wissen.

```powershell
Clear-RecycleBin -Force
```

`Clear-RecycleBin` gebruikt de **Force** -para meter en vraagt de gebruiker niet om bevestiging om alle prullen bakken op de lokale computer te wissen.

U kunt ook vervangen `-Force` door `-Confirm:$false` .

## PARAMETERS

### -Stationsletter

Hiermee geeft u de Prullenbak op die moet worden gewist voor één stationsletter of een reeks stationsletters.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Force

Geeft aan dat de gebruiker niet om bevestiging wordt gevraagd om een prullenbak te wissen.

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

### -Confirm

Vraagt om bevestiging van de gebruiker voordat de cmdlet wordt uitgevoerd. De gebruiker wordt om bevestiging gevraagd, zelfs als de para meter **confirm** niet is opgegeven.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

Hier wordt weer gegeven wat er gebeurt als er `Clear-RecycleBin` wordt uitgevoerd. De cmdlet wordt niet uitgevoerd.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

## UITVOER

### Geen

## OPMERKINGEN

Deze cmdlet is alleen beschikbaar op Windows-platforms.

## GERELATEERDE KOPPELINGEN
