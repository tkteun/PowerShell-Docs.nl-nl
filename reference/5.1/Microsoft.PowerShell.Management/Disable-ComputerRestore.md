---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/disable-computerrestore?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-ComputerRestore
ms.openlocfilehash: 941829c3caa0f6bb2f5712dda9eb7d8c36908062
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250815"
---
# Disable-ComputerRestore

## SAMENVATTING
Hiermee schakelt u de functie systeem herstel uit op het opgegeven bestandssysteem station.

## SYNTAXIS

```
Disable-ComputerRestore [-Drive] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING
De cmdlet **Disable-ComputerRestore** schakelt de functie systeem herstel uit op een of meer bestandssysteem stations.
Als gevolg hiervan worden pogingen om de computer te herstellen niet van invloed op het opgegeven station.

Als u systeem herstel op een wille keurig station wilt uitschakelen, moet dit worden uitgeschakeld op het systeem station, hetzij eerst, hetzij gelijktijdig.

Gebruik de cmdlet Enable-ComputerRestore om systeem herstel opnieuw in te scha kelen.
Gebruik Rstrui.exe om de status van systeem herstel voor elk station te vinden.

Systeem herstel punten en de ComputerRestore-cmdlets worden alleen ondersteund op client besturingssystemen, zoals Windows 7, Windows Vista en Windows XP.

## VOORBEELDEN

### Voor beeld 1: systeem herstel op het opgegeven station uitschakelen

```
PS C:\> Disable-ComputerRestore -Drive "C:\"
```

Met deze opdracht wordt systeem herstel op station C: uitgeschakeld.

### Voor beeld 2: systeem herstel op meerdere stations uitschakelen

```
PS C:\> Disable-ComputerRestore "C:\", "D:\"
```

Met deze opdracht wordt systeem herstel op de stations C: en D: uitgeschakeld.
Met de opdracht wordt de para meter *Drive* gebruikt, maar wordt de parameter naam van de station wegge laten.

## PARAMETERS

### -Station
Hiermee geeft u de stations met het bestands systeem.
Voer een of meer bestandssysteem stationsletters in, gevolgd door een dubbele punt en een back slash en tussen aanhalings tekens, zoals C:\ of D:\.
Deze parameter is vereist.

U kunt deze cmdlet niet gebruiken om systeem herstel uit te scha kelen op een extern netwerk station, zelfs als het station is toegewezen aan de lokale computer en u geen systeem herstel kunt uitschakelen op stations die niet in aanmerking komen voor systeem herstel, zoals externe schijven.

Als u systeem herstel op een wille keurig station wilt uitschakelen, moet systeem herstel worden uitgeschakeld op het systeem station, hetzij voor of gelijktijdig.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm
Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.

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
Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.
De cmdlet wordt niet uitgevoerd.

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

### Geen
U kunt geen invoer van een pipe naar deze cmdlet.

## UITVOER

### Geen
Met deze cmdlet wordt geen uitvoer gegenereerd.

## OPMERKINGEN

* Als u deze cmdlet wilt uitvoeren op Windows Vista en latere versies van Windows, opent u Windows Power shell met de optie als administrator uitvoeren.

  Als u de bestandssysteem stations wilt vinden die in aanmerking komen voor systeem herstel, gaat u naar het tabblad systeem beveiliging in het onderdeel systeem in het configuratie scherm. Als u dit tabblad in Windows Power shell wilt openen, typt u `SystemPropertiesProtection` .

  Deze cmdlet maakt gebruik van de Windows Management Instrumentation klasse **SystemRestore** (WMI).

*

## GERELATEERDE KOPPELINGEN

[Checkpoint-Computer](Checkpoint-Computer.md)

[Enable-ComputerRestore](Enable-ComputerRestore.md)

[Get-ComputerRestorePoint](Get-ComputerRestorePoint.md)

[Restart-Computer](Restart-Computer.md)

[Herstellen-computer](Restore-Computer.md)
