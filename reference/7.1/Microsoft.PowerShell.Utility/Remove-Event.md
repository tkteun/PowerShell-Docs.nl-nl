---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/remove-event?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Event
ms.openlocfilehash: 2ef1125320141d0a16a2a0120560efbe65017b4a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250182"
---
# Remove-Event

## SAMENVATTING
Hiermee verwijdert u gebeurtenissen uit de wachtrij van de gebeurtenis.

## SYNTAXIS

### BySource (standaard)

```
Remove-Event [-SourceIdentifier] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByIdentifier

```
Remove-Event [-EventIdentifier] <Int32> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING
Met de cmdlet **Remove-Event** worden gebeurtenissen uit de gebeurtenis wachtrij in de huidige sessie verwijderd.

Met deze cmdlet worden alleen de gebeurtenissen uit de wachtrij verwijderd.
Als u gebeurtenis registraties wilt annuleren of zich wilt afmelden, gebruikt u de Unregister-Event-cmdlet.

## VOORBEELDEN

### Voor beeld 1: een gebeurtenis verwijderen op bron-id

```
PS C:\> Remove-Event -SourceIdentifier "ProcessStarted"
```

Met deze opdracht worden gebeurtenissen verwijderd met een bron-id van het proces dat is gestart vanuit de gebeurtenis wachtrij.

### Voor beeld 2: een gebeurtenis verwijderen op gebeurtenis-id

```
PS C:\> Remove-Event -EventIdentifier 30
```

Met deze opdracht wordt de gebeurtenis met gebeurtenis-ID 30 uit de gebeurtenis wachtrij verwijderd.

### Voor beeld 3: alle gebeurtenissen verwijderen

```
PS C:\> Get-Event | Remove-Event
```

Met deze opdracht worden alle gebeurtenissen uit de gebeurtenis wachtrij verwijderd.

## PARAMETERS

### -EventIdentifier
Hiermee geeft u de gebeurtenis-id op waarvoor de cmdlet wordt verwijderd.
Een *EventIdentifier* -of *SourceIdentifier* -para meter is vereist in elke opdracht.

```yaml
Type: System.Int32
Parameter Sets: ByIdentifier
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -SourceIdentifier
Hiermee geeft u de bron-id op waarvoor met deze cmdlet gebeurtenissen worden verwijderd.
Joker tekens zijn niet toegestaan.
Een *EventIdentifier* -of *SourceIdentifier* -para meter is vereist in elke opdracht.

```yaml
Type: System.String
Parameter Sets: BySource
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

### System. Management. Automation. PSEventArgs
U kunt gebeurtenissen van Get-Event naar **Remove-Event** door sluizen.

## UITVOER

### Geen
De cmdlet genereert geen uitvoer.

## OPMERKINGEN

* Gebeurtenissen, gebeurtenis abonnementen en de gebeurtenis wachtrij bestaan alleen in de huidige sessie. Als u de huidige sessie sluit, wordt de gebeurtenis wachtrij verwijderd en wordt het gebeurtenis abonnement geannuleerd.

*

## GERELATEERDE KOPPELINGEN

[Get-Event](Get-Event.md)

[Nieuw-gebeurtenis](New-Event.md)

[REGI ster-EngineEvent](Register-EngineEvent.md)

[REGI ster-ObjectEvent](Register-ObjectEvent.md)

[Remove-gebeurtenis](Remove-Event.md)

[Registratie ongedaan maken-gebeurtenis](Unregister-Event.md)

[Wachten gebeurtenis](Wait-Event.md)

