---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-event?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Event
ms.openlocfilehash: 45d9e45bfbbeba7b9467985dc6abf3a28cd8702b
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/07/2020
ms.locfileid: "94342345"
---
# Get-Event

## SAMENVATTING
Hiermee haalt u de gebeurtenissen in de wachtrij van de gebeurtenis op.

## SYNTAXIS

### BySource (standaard)

```
Get-Event [[-SourceIdentifier] <String>] [<CommonParameters>]
```

### ById

```
Get-Event [-EventIdentifier] <Int32> [<CommonParameters>]
```

## BESCHRIJVING

De `Get-Event` cmdlet haalt gebeurtenissen op in de Power shell-gebeurtenis wachtrij voor de huidige sessie. U kunt alle gebeurtenissen ophalen of de para meter **EventIdentifier** of **SourceIdentifier** gebruiken om de gebeurtenissen op te geven.

Wanneer er een gebeurtenis optreedt, wordt deze toegevoegd aan de gebeurtenis wachtrij. De gebeurtenissen wachtrij bevat gebeurtenissen waarvoor u bent geregistreerd, gebeurtenissen die zijn gemaakt met behulp van de `New-Event` cmdlet en de gebeurtenis die optreedt wanneer Power shell wordt afgesloten. U kunt `Get-Event` of gebruiken `Wait-Event` om de gebeurtenissen op te halen.

Met deze cmdlet worden geen gebeurtenissen uit de Logboeken Logboeken opgehaald. Gebruik of om deze gebeurtenissen op te halen `Get-WinEvent` `Get-EventLog` .

## VOORBEELDEN

### Voor beeld 1: alle gebeurtenissen ophalen

```
PS C:\> Get-Event
```

Met deze opdracht worden alle gebeurtenissen in de wachtrij van de gebeurtenis opgehaald.

### Voor beeld 2: gebeurtenissen ophalen op bron-id

```
PS C:\> Get-Event -SourceIdentifier "PowerShell.ProcessCreated"
```

Met deze opdracht worden gebeurtenissen opgehaald waarin de waarde van de eigenschap SourceIdentifier Power shell. ProcessCreated is.

### Voor beeld 3: een gebeurtenis ophalen op basis van de tijd dat deze is gegenereerd

```
PS C:\> $Events = Get-Event
PS C:\> $Events[0] | Format-List -Property *
ComputerName     :
RunspaceId       : c2153740-256d-46c0-a57c-b805917d1b7b
EventIdentifier  : 1
Sender           : System.Management.ManagementEventWatcher
SourceEventArgs  : System.Management.EventArrivedEventArgs
SourceArgs       : {System.Management.ManagementEventWatcher, System.Management.EventArrivedEventArgs}
SourceIdentifier : ProcessStarted
TimeGenerated    : 11/13/2008 12:09:32 PM
MessageData      : PS C:\> Get-Event | Where {$_.TimeGenerated -ge "11/13/2008 12:15:00 PM"}
ComputerName     :
RunspaceId       : c2153740-256d-46c0-a57c-b8059325d1a0
EventIdentifier  : 1
Sender           : System.Management.ManagementEventWatcher
SourceEventArgs  : System.Management.EventArrivedEventArgs
SourceArgs       : {System.Management.ManagementEventWatcher, System.Management.EventArrivedEventArgs}
SourceIdentifier : ProcessStarted
TimeGenerated    : 11/13/2008 12:15:00 PM
MessageData      :
```

In dit voor beeld ziet u hoe u gebeurtenissen kunt ophalen met behulp van andere eigenschappen dan SourceIdentifier.

Met de eerste opdracht worden alle gebeurtenissen in de gebeurtenis wachtrij opgehaald en opgeslagen in de `$Events` variabele.

De tweede opdracht maakt gebruik van de matrix notatie om de eerste (0-index) gebeurtenis op te halen in de matrix in de `$Events` variabele. De opdracht maakt gebruik van een pijplijn operator ( `|` ) om de gebeurtenis naar de `Format-List` opdracht te verzenden, waarin alle eigenschappen van de gebeurtenis in een lijst worden weer gegeven. Hiermee kunt u de eigenschappen van het gebeurtenis object controleren.

De derde opdracht laat zien hoe u de `Where-Object` cmdlet gebruikt om een gebeurtenis op te halen op basis van de tijd dat deze is gegenereerd.

### Voor beeld 4: een gebeurtenis op basis van de id ophalen

```
PS C:\> Get-Event -EventIdentifier 2
```

Met deze opdracht wordt de gebeurtenis met de gebeurtenis-id 2 opgehaald.

## PARAMETERS

### -EventIdentifier

Hiermee geeft u de gebeurtenis-id's op waarvoor deze cmdlet gebeurtenissen ontvangt.

```yaml
Type: System.Int32
Parameter Sets: ById
Aliases: Id

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -SourceIdentifier

Hiermee geeft u de bron-id's op waarvoor deze cmdlet gebeurtenissen ontvangt. De standaard instelling is alle gebeurtenissen in de wachtrij van de gebeurtenis. Joker tekens zijn niet toegestaan.

```yaml
Type: System.String
Parameter Sets: BySource
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Geen

U kunt geen invoer van een pipe naar deze cmdlet.

## UITVOER

### System. Management. Automation. PSEventArgs

`Get-Event` retourneert een **PSEventArgs** -object voor elke gebeurtenis. Als u een beschrijving van dit object wilt weer geven, typt `Get-Help Get-Event -Full` en raadpleegt u de sectie Notities van het Help-onderwerp.

## OPMERKINGEN

Er zijn geen gebeurtenis bronnen beschikbaar op de Linux-of macOS-platforms.

Gebeurtenissen, gebeurtenis abonnementen en de gebeurtenis wachtrij bestaan alleen in de huidige sessie. Als u de huidige sessie sluit, wordt de gebeurtenis wachtrij verwijderd en wordt het gebeurtenis abonnement geannuleerd.

De `Get-Event` cmdlet retourneert een **PSEventArgs** -object ( **System. Management. Automation. PSEventArgs** ) met de volgende eigenschappen:

- ComputerName. De naam van de computer waarop de gebeurtenis heeft plaatsgevonden. Deze eigenschaps waarde wordt alleen ingevuld wanneer de gebeurtenis wordt doorgestuurd vanaf een externe computer.

- RunspaceId. Een GUID die een unieke identificatie vormt van de sessie waarin de gebeurtenis heeft plaatsgevonden. Deze eigenschaps waarde wordt alleen ingevuld wanneer de gebeurtenis wordt doorgestuurd vanaf een externe computer.

- EventIdentifier. Een geheel getal (INT32) waarmee de gebeurtenis melding in de huidige sessie op unieke wijze wordt geïdentificeerd.

- SenderName. Het object dat de gebeurtenis heeft gegenereerd. In de waarde van de **actie** parameter bevat de `$Sender` Automatische variabele het object Sender.

- SourceEventArgs. De eerste para meter die is afgeleid van EventArgs, als deze bestaat. In een verstreken timer gebeurtenis waarbij de hand tekening de afzender van het formulier object, **timers. ElapsedEventArgs** e heeft, bevat de eigenschap **SourceEventArgs** de **timers. ElapsedEventArgs**. In de waarde van de **actie** parameter bevat de `$EventArgs` Automatische variabele deze waarde.

- SourceArgs. Alle para meters van de oorspronkelijke gebeurtenis handtekening. Voor een standaard gebeurtenis handtekening `$Args[0]` vertegenwoordigt de afzender en `$Args[1]` vertegenwoordigt het **SourceEventArgs**. In de waarde van de **actie** parameter bevat de `$Args` Automatische variabele deze waarde.

- SourceIdentifier. Een teken reeks waarmee het gebeurtenis abonnement wordt geïdentificeerd. In de waarde van de **actie** parameter bevat de eigenschap **SourceIdentifier** van de `$Event` Automatische variabele deze waarde.

- TimeGenerated. Een **DateTime** -object dat het tijdstip vertegenwoordigt waarop de gebeurtenis is gegenereerd.
  In de waarde van de **actie** parameter bevat de eigenschap **TimeGenerated** van de `$Event` Automatische variabele deze waarde.

- MessageData. Gegevens die zijn gekoppeld aan het gebeurtenis abonnement. Gebruikers geven deze gegevens op wanneer ze een gebeurtenis registreren. In de waarde van de **actie** parameter bevat de eigenschap **MessageData** van de `$Event` Automatische variabele deze waarde.

## GERELATEERDE KOPPELINGEN

[Nieuw-gebeurtenis](New-Event.md)

[REGI ster-EngineEvent](Register-EngineEvent.md)

[REGI ster-ObjectEvent](Register-ObjectEvent.md)

[Remove-gebeurtenis](Remove-Event.md)

[Registratie ongedaan maken-gebeurtenis](Unregister-Event.md)

[Wachten gebeurtenis](Wait-Event.md)
