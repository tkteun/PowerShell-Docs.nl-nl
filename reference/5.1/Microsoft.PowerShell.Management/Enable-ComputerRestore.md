---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/enable-computerrestore?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-ComputerRestore
ms.openlocfilehash: f9616a7f9af4dd2fa45e150bb64eef65427b4947
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250814"
---
# Enable-ComputerRestore

## SAMENVATTING
Hiermee schakelt u de functie systeem herstel op het opgegeven bestandssysteem station.

## SYNTAXIS

```
Enable-ComputerRestore [-Drive] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING
Met de cmdlet **Enable-ComputerRestore** wordt de functie systeem herstel op een of meer bestandssysteem stations ingeschakeld.
Als gevolg hiervan kunt u hulpprogram ma's, zoals de cmdlet Restore-Computer, gebruiken om de computer terug te zetten naar een eerdere status.

Systeem herstel is standaard ingeschakeld op alle in aanmerking komende stations, maar u kunt dit uitschakelen, bijvoorbeeld met behulp van de cmdlet Disable-ComputerRestore.
Om systeem herstel op een wille keurige schijf in of uit te scha kelen, moet dit op het systeem station worden ingeschakeld, hetzij eerst, hetzij gelijktijdig.
Gebruik Rstrui.exe om de status van systeem herstel voor elk station te vinden.

Systeem herstel punten en de ComputerRestore-cmdlets worden alleen ondersteund op client besturingssystemen, zoals Windows 7, Windows Vista en Windows XP.

## VOORBEELDEN

### Voor beeld 1: systeem herstel inschakelen op het opgegeven station

```
PS C:\> Enable-ComputerRestore -Drive "C:\"
```

Met deze opdracht wordt systeem herstel ingeschakeld op station C: van de lokale computer.

### Voor beeld 2: systeem herstel op meerdere stations inschakelen

```
PS C:\> Enable-ComputerRestore -Drive "C:\", "D:\"
```

Met deze opdracht wordt systeem herstel ingeschakeld op de stations C: en D: van de lokale computer.

## PARAMETERS

### -Station
Hiermee geeft u de stations met het bestands systeem.
Voer een of meer bestandssysteem stationsletters in, gevolgd door een dubbele punt en een back slash en tussen aanhalings tekens, zoals C:\ of D:\.
Deze parameter is vereist.

U kunt deze cmdlet niet gebruiken om systeem herstel in te scha kelen op een extern netwerk station, zelfs als het station is toegewezen aan de lokale computer en u geen systeem herstel kunt inschakelen op stations die niet in aanmerking komen voor systeem herstel, zoals externe schijven.

Systeem herstel moet zijn ingeschakeld op het systeem station, hetzij voor of gelijktijdig, om systeem herstel op elk station in te scha kelen.

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
U kunt geen objecten naar deze cmdlet pipeen.

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

[Disable-ComputerRestore](Disable-ComputerRestore.md)

[Get-ComputerRestorePoint](Get-ComputerRestorePoint.md)

[Restart-Computer](Restart-Computer.md)

[Herstellen-computer](Restore-Computer.md)
