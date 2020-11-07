---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-event?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Event
ms.openlocfilehash: c822711b7fda94dd6a2a391560100758ee41d233
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/07/2020
ms.locfileid: "94344640"
---
# New-Event

## SAMENVATTING
Hiermee maakt u een nieuwe gebeurtenis.

## SYNTAXIS

```
New-Event [-SourceIdentifier] <String> [[-Sender] <PSObject>] [[-EventArguments] <PSObject[]>]
 [[-MessageData] <PSObject>] [<CommonParameters>]
```

## BESCHRIJVING

Met de `New-Event` cmdlet maakt u een nieuwe aangepaste gebeurtenis.

U kunt aangepaste gebeurtenissen gebruiken om gebruikers op de hoogte te stellen van status wijzigingen in uw programma en elke wijziging die uw programma kan detecteren, waaronder de hardware-of systeem voorwaarden, de toepassings status, de status van het netwerk of het volt ooien van een achtergrond taak.

Aangepaste gebeurtenissen worden automatisch toegevoegd aan de gebeurtenis wachtrij in uw sessie wanneer deze worden gegenereerd. u hoeft zich niet aan te melden. Als u echter een gebeurtenis wilt door sturen naar de lokale sessie of een actie wilt opgeven om te reageren op de gebeurtenis, gebruikt u de `Register-EngineEvent` cmdlet om u te abonneren op de aangepaste gebeurtenis.

Wanneer u zich abonneert op een aangepaste gebeurtenis, wordt de gebeurtenis abonnee toegevoegd aan uw sessie. Als u het gebeurtenis abonnement met behulp van de cmdlet annuleert `Unregister-Event` , worden de gebeurtenis abonnee en de aangepaste gebeurtenis verwijderd uit de sessie. Als u zich niet hebt geabonneerd op de aangepaste gebeurtenis, moet u de programma voorwaarden wijzigen of de Power shell-sessie sluiten om de gebeurtenis te verwijderen.

## VOORBEELDEN

### Voor beeld 1: een nieuwe gebeurtenis in de wachtrij voor gebeurtenissen maken

```
PS C:\> New-Event -SourceIdentifier Timer -Sender windows.timer -MessageData "Test"
```

Met deze opdracht maakt u een nieuwe gebeurtenis in de Power shell-gebeurtenis wachtrij. Er wordt gebruikgemaakt van een **Windows. timer** -object voor het verzenden van de gebeurtenis.

### Voor beeld 2: een gebeurtenis activeren als reactie op een andere gebeurtenis

```
PS C:\> function Enable-ProcessCreationEvent
{
   $Query = New-Object System.Management.WqlEventQuery "__InstanceCreationEvent", (New-Object TimeSpan 0,0,1), "TargetInstance isa 'Win32_Process'"
   $ProcessWatcher = New-Object System.Management.ManagementEventWatcher $Query
   $Identifier = "WMI.ProcessCreated"
   Register-ObjectEvent $ProcessWatcher "EventArrived" -SupportEvent $Identifier -Action
   {
      [void] (New-Event -SourceID "PowerShell.ProcessCreated" -Sender $Args[0] -EventArguments $Args[1].SourceEventArgs.NewEvent.TargetInstance)
   }
}
```

Deze voorbeeld functie maakt gebruik `New-Event` van de cmdlet om een gebeurtenis te genereren als reactie op een andere gebeurtenis. De opdracht gebruikt de `Register-ObjectEvent` cmdlet om u te abonneren op de gebeurtenis Windows Management Instrumentation (WMI) die wordt geactiveerd wanneer een nieuw proces wordt gemaakt. De opdracht gebruikt de **actie** parameter van de cmdlet om de cmdlet aan te roepen `New-Event` , waardoor de nieuwe gebeurtenis wordt gemaakt.

Omdat de gebeurtenissen die `New-Event` worden gegenereerd automatisch worden toegevoegd aan de Power shell-gebeurtenis wachtrij, hoeft u zich niet te registreren voor die gebeurtenis.

## PARAMETERS

### -EventArguments

Hiermee geeft u een object op dat opties bevat voor de gebeurtenis.

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MessageData

Hiermee geeft u aanvullende gegevens op die zijn gekoppeld aan de gebeurtenis. De waarde van deze para meter wordt weer gegeven in de eigenschap **MessageData** van het object Event.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Sender

Hiermee geeft u het object op waarmee de gebeurtenis wordt gegenereerd. De standaard waarde is de Power shell-engine.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SourceIdentifier

Hiermee geeft u een naam op voor de nieuwe gebeurtenis. Deze para meter is vereist en moet uniek zijn in de sessie.

De waarde van deze para meter wordt weer gegeven in de eigenschap **SourceIdentifier** van de gebeurtenissen.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Geen

U kunt geen invoer van een pipe naar deze cmdlet.

## UITVOER

### System. Management. Automation. PSEventArgs

## OPMERKINGEN

De nieuwe aangepaste gebeurtenis, het gebeurtenis abonnement en de gebeurtenis wachtrij bestaan alleen in de huidige sessie.
Als u de huidige sessie sluit, wordt de gebeurtenis wachtrij verwijderd en wordt het gebeurtenis abonnement geannuleerd.

## GERELATEERDE KOPPELINGEN

[Get-Event](Get-Event.md)

[REGI ster-EngineEvent](Register-EngineEvent.md)

[REGI ster-ObjectEvent](Register-ObjectEvent.md)

[Remove-gebeurtenis](Remove-Event.md)

[Registratie ongedaan maken-gebeurtenis](Unregister-Event.md)

[Wachten gebeurtenis](Wait-Event.md)
