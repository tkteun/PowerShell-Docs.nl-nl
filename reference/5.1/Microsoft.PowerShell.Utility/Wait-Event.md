---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/wait-event?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Wait-Event
ms.openlocfilehash: 55fa54521a6c2e9d37b333a27af4572c6a34913a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250351"
---
# Wait-Event

## SAMENVATTING
Er wordt gewacht tot een bepaalde gebeurtenis is opgetreden voordat de uitvoering wordt voortgezet.

## SYNTAXIS

```
Wait-Event [[-SourceIdentifier] <String>] [-Timeout <Int32>] [<CommonParameters>]
```

## BESCHRIJVING

De `Wait-Event` cmdlet onderbreekt de uitvoering van een script of functie totdat een bepaalde gebeurtenis wordt gegenereerd. De uitvoering wordt hervat wanneer de gebeurtenis wordt gedetecteerd. U annuleert het wachten door op <kbd>CTRL</kbd> + <kbd>C</kbd>te drukken.

Deze functie biedt een alternatief voor het opvragen van een gebeurtenis. Daarnaast kunt u het antwoord op twee verschillende manieren bepalen voor een gebeurtenis:

- de **actie** parameter van het gebeurtenis abonnement gebruiken
- wachten tot een gebeurtenis is geretourneerd en vervolgens reageert met een actie

## VOORBEELDEN

### Voor beeld 1: wachten op de volgende gebeurtenis

In dit voor beeld wordt gewacht op de volgende gebeurtenis die optreedt.

```powershell
Wait-Event
```

### Voor beeld 2: wachten op een gebeurtenis met een opgegeven bron-id

In dit voor beeld wordt gewacht op de volgende gebeurtenis die optreedt en die een bron-id van ProcessStarted heeft.

```powershell
Wait-Event -SourceIdentifier "ProcessStarted"
```

### Voor beeld 3: wachten op gebeurtenis die is verstreken met een timer

In dit voor beeld wordt de `Wait-Event` cmdlet gebruikt om te wachten op een timer gebeurtenis in een timer die is ingesteld op 2000 milliseconden.

```powershell
$Timer = New-Object Timers.Timer
$objectEventArgs = @{
    InputObject = $Timer
    EventName = 'Elapsed'
    SourceIdentifier = 'Timer.Elapsed'
}
Register-ObjectEvent @objectEventArgs
$Timer.Interval = 2000
$Timer.Autoreset = $False
$Timer.Enabled = $True
Wait-Event Timer.Elapsed
```

```Output
ComputerName     :
RunspaceId       : bb560b14-ff43-48d4-b801-5adc31bbc6fb
EventIdentifier  : 1
Sender           : System.Timers.Timer
SourceEventArgs  : System.Timers.ElapsedEventArgs
SourceArgs       : {System.Timers.Timer, System.Timers.ElapsedEventArgs}
SourceIdentifier : Timer.Elapsed
TimeGenerated    : 4/23/2020 2:30:37 PM
MessageData      :
```

### Voor beeld 4: wachten op een gebeurtenis na een opgegeven time-out

In dit voor beeld wordt 90 seconden gewacht op de volgende gebeurtenis die optreedt en die een bron-id van **ProcessStarted** heeft. Als de opgegeven tijd verloopt, wordt het wachten beëindigd.

```powershell
Wait-Event -SourceIdentifier "ProcessStarted" -Timeout 90
```

## PARAMETERS

### -SourceIdentifier

Hiermee geeft u de bron-id op die met deze cmdlet wordt gewacht op gebeurtenissen.
Standaard wordt `Wait-Event` gewacht op een gebeurtenis.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Time-out

Hiermee geeft u de maximale tijds duur in seconden op waarmee wordt `Wait-Event` gewacht tot de gebeurtenis plaatsvindt. De standaard waarde-1, wacht oneindig. De timing wordt gestart wanneer u de `Wait-Event` opdracht verzendt.

Als de opgegeven tijd wordt overschreden, worden de wacht tijden beëindigd en wordt de opdracht prompt geretourneerd, zelfs als de gebeurtenis niet is gegenereerd. Er wordt geen fout bericht weer gegeven.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: TimeoutSec

Required: False
Position: Named
Default value: -1
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. String

## UITVOER

### System. Management. Automation. PSEventArgs

## OPMERKINGEN

Gebeurtenissen, gebeurtenis abonnementen en de gebeurtenis wachtrij bestaan alleen in de huidige sessie. Als u de huidige sessie sluit, wordt de gebeurtenis wachtrij verwijderd en wordt het gebeurtenis abonnement geannuleerd.

## GERELATEERDE KOPPELINGEN

[Get-Event](Get-Event.md)

[Get-EventSubscriber](Get-EventSubscriber.md)

[Nieuw-gebeurtenis](New-Event.md)

[REGI ster-EngineEvent](Register-EngineEvent.md)

[REGI ster-ObjectEvent](Register-ObjectEvent.md)

[Remove-gebeurtenis](Remove-Event.md)

[Registratie ongedaan maken-gebeurtenis](Unregister-Event.md)

[Wachten gebeurtenis](Wait-Event.md)
