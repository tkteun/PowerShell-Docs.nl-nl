---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/unregister-event?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unregister-Event
ms.openlocfilehash: 7aff17c29c8105c79d9bb3955552c75a3a05f752
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/07/2020
ms.locfileid: "94344710"
---
# Unregister-Event

## SAMENVATTING
Hiermee wordt een gebeurtenis abonnement geannuleerd.

## SYNTAXIS

### BySource (standaard)

```
Unregister-Event [-SourceIdentifier] <String> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ById

```
Unregister-Event [-SubscriptionId] <Int32> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

De `Unregister-Event` cmdlet annuleert een gebeurtenis abonnement dat is gemaakt met behulp van de `Register-EngineEvent` -, `Register-ObjectEvent` -of- `Register-WmiEvent` cmdlet.

Wanneer een gebeurtenis abonnement wordt geannuleerd, wordt de gebeurtenis abonnee verwijderd uit de sessie en worden de geabonneerde gebeurtenissen niet meer toegevoegd aan de gebeurtenis wachtrij. Wanneer u een abonnement opzegt op een gebeurtenis die is gemaakt met behulp van de `New-Event` cmdlet, wordt de nieuwe gebeurtenis ook verwijderd uit de sessie.

`Unregister-Event` verwijdert geen gebeurtenissen uit de wachtrij van de gebeurtenis. Als u gebeurtenissen wilt verwijderen, gebruikt u de `Remove-Event` cmdlet.

## VOORBEELDEN

### Voor beeld 1: een gebeurtenis abonnement op bron-id annuleren

```
PS C:\> Unregister-Event -SourceIdentifier "ProcessStarted"
```

Met deze opdracht wordt het gebeurtenis abonnement met de bron-id ProcessStarted geannuleerd.

Gebruik de cmdlet om de bron-id van een gebeurtenis te vinden `Get-Event` . Als u de bron-id van een gebeurtenis abonnement wilt zoeken, gebruikt u de `Get-EventSubscriber` cmdlet.

### Voor beeld 2: een gebeurtenis abonnement op abonnements-id annuleren

```
PS C:\> Unregister-Event -SubscriptionId 2
```

Met deze opdracht wordt het gebeurtenis abonnement met de abonnements-id 2 geannuleerd.

Gebruik de cmdlet om de abonnements-id van een gebeurtenis abonnement te vinden `Get-EventSubscriber` .

### Voor beeld 3: alle gebeurtenis abonnementen annuleren

```
PS C:\> Get-EventSubscriber -Force | Unregister-Event -Force
```

Met deze opdracht worden alle gebeurtenis abonnementen in de sessie geannuleerd.

De opdracht gebruikt de `Get-EventSubscriber` cmdlet om alle Event Subscriber-objecten in de sessie op te halen, met inbegrip van de abonnees die zijn verborgen met behulp van de para meter **SupportEvent** van de cmdlets voor gebeurtenis registratie.

Er wordt gebruikgemaakt van een pijplijn operator ( `|` ) om de abonnee objecten te verzenden `Unregister-Event` , waardoor ze uit de sessie worden verwijderd. Voor het volt ooien van de taak is de para meter **Forces** ook vereist voor `Unregister-Event` .

## PARAMETERS

### -Force

Annuleert alle gebeurtenis abonnementen, inclusief abonnementen die zijn verborgen met de para meter **SupportEvent** van `Register-ObjectEvent` , `Register-WmiEvent` en `Register-EngineEvent` .

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

### -SourceIdentifier

Hiermee geeft u een bron-id op die met deze cmdlet gebeurtenis abonnementen annuleert.

Een **SourceIdentifier** -of **SubscriptionId** -para meter moet worden opgenomen in elke opdracht.

```yaml
Type: System.String
Parameter Sets: BySource
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -SubscriptionId

Hiermee geeft u een bron-id-ID op die met deze cmdlet gebeurtenis abonnementen annuleert.

Een **SourceIdentifier** -of **SubscriptionId** -para meter moet worden opgenomen in elke opdracht.

```yaml
Type: System.Int32
Parameter Sets: ById
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
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

Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert. De cmdlet wordt niet uitgevoerd.

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

### System. Management. Automation. PSEventSubscriber

U kunt de uitvoer door sluizen van `Get-EventSubscriber` naar `Unregister-Event` .

## UITVOER

### Geen

Met deze cmdlet wordt geen uitvoer geretourneerd.

## OPMERKINGEN

Er zijn geen gebeurtenis bronnen beschikbaar op de Linux-of macOS-platforms.

Gebeurtenissen, gebeurtenis abonnementen en de gebeurtenis wachtrij bestaan alleen in de huidige sessie. Als u de huidige sessie sluit, wordt de gebeurtenis wachtrij verwijderd en wordt het gebeurtenis abonnement geannuleerd.

`Unregister-Event` kan geen gebeurtenissen verwijderen die zijn gemaakt met behulp van de `New-Event` cmdlet tenzij u bent geabonneerd op de gebeurtenis met behulp van de `Register-EngineEvent` cmdlet. Als u een aangepaste gebeurtenis uit de sessie wilt verwijderen, moet u deze programmatisch verwijderen of de sessie sluiten.

## GERELATEERDE KOPPELINGEN

[Get-Event](Get-Event.md)

[Get-EventSubscriber](Get-EventSubscriber.md)

[Nieuw-gebeurtenis](New-Event.md)

[REGI ster-EngineEvent](Register-EngineEvent.md)

[REGI ster-ObjectEvent](Register-ObjectEvent.md)

[Remove-gebeurtenis](Remove-Event.md)

[Registratie ongedaan maken-gebeurtenis](Unregister-Event.md)

[Wachten gebeurtenis](Wait-Event.md)
