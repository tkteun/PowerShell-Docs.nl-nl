---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-eventsubscriber?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-EventSubscriber
ms.openlocfilehash: c621ef5b76d4e282f4108094a79c8617bf6bb817
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250440"
---
# Get-EventSubscriber

## SAMENVATTING
Hiermee haalt u de gebeurtenis abonnees op in de huidige sessie.

## SYNTAXIS

### BySource (standaard)

```
Get-EventSubscriber [[-SourceIdentifier] <String>] [-Force] [<CommonParameters>]
```

### ById

```
Get-EventSubscriber [-SubscriptionId] <Int32> [-Force] [<CommonParameters>]
```

## BESCHRIJVING
De cmdlet **Get-EventSubscriber** haalt de gebeurtenis abonnees op in de huidige sessie.

Wanneer u zich abonneert op een gebeurtenis met behulp van een gebeurtenis-cmdlet registreren, wordt een gebeurtenis abonnee toegevoegd aan uw Windows Power shell-sessie en worden de gebeurtenissen waarop u bent geabonneerd aan uw gebeurtenis wachtrij toegevoegd wanneer deze worden gegenereerd.
Als u een gebeurtenis abonnement wilt annuleren, verwijdert u de Event Subscriber met behulp van de cmdlet Unregister-Event.

## VOORBEELDEN

### Voor beeld 1: de gebeurtenis abonnee voor een timer gebeurtenis ophalen

```
PS C:\> $Timer = New-Object Timers.Timer
PS C:\> $Timer | Get-Member -Type Event
PS C:\> Register-ObjectEvent -InputObject $Timer -EventName Elapsed -SourceIdentifier Timer.Elapsed
PS C:\> Get-EventSubscriber
PS C:\> $Timer = New-Object Timers.Timer
PS C:\> $Timer | Get-Member -Type Event
TypeName: System.Timers.Timer
Name     MemberType Definition
----     ---------- ----------
Disposed Event      System.EventHandler Disposed(System.Object, System.EventArgs)
Elapsed  Event      System.Timers.ElapsedEventHandler Elapsed(System.Object, System.Timers.ElapsedEventArgs) PS C:\> Register-ObjectEvent -InputObject $Timer -EventName Elapsed -SourceIdentifier Timer.Elapsed
PS C:\> Get-EventSubscriber
SubscriptionId   : 4
SourceObject     : System.Timers.Timer
EventName        : Elapsed
SourceIdentifier : Timer.Elapsed
Action           :
HandlerDelegate  :
SupportEvent     : False
ForwardEvent     : False
```

In dit voor beeld wordt de opdracht **Get-EventSubscriber** gebruikt om de Event Subscriber voor een timer gebeurtenis op te halen.

De eerste opdracht gebruikt de cmdlet New-Object om een exemplaar van een timer object te maken.
Het nieuwe timer object wordt opgeslagen in de variabele $Timer.

De tweede opdracht maakt gebruik van de cmdlet Get-Member om de gebeurtenissen weer te geven die beschikbaar zijn voor timer-objecten.
De opdracht maakt gebruik van de para meter type van de cmdlet **Get-member** met de waarde Event.

De derde opdracht gebruikt de cmdlet Register-ObjectEvent om u te registreren voor de verstreken gebeurtenis van het object Timer.

De vierde opdracht maakt gebruik van de cmdlet **Get-EventSubscriber** om de gebeurtenis abonnee voor de verstreken gebeurtenis op te halen.

### Voor beeld 2: de dynamische module in PSEventJob gebruiken in de eigenschap Action van de abonnee van de gebeurtenis

```
PS C:\> $Timer = New-Object Timers.Timer
PS C:\> $Timer.Interval = 500
PS C:\> Register-ObjectEvent -InputObject $Timer -EventName Elapsed -SourceIdentifier Timer.Random -Action { $Random = Get-Random -Min 0 -Max 100 }

Id  Name           State      HasMoreData  Location  Command
--  ----           -----      -----------  --------  -------
3   Timer.Random   NotStarted False                  $Random = Get-Random ...

PS C:\> $Timer.Enabled = $True
PS C:\> $Subscriber = Get-EventSubscriber -SourceIdentifier Timer.Random
PS C:\> ($Subscriber.action).gettype().fullname
System.Management.Automation.PSEventJob
PS C:\> $Subscriber.action | Format-List -Property *

State         : Running
Module        : __DynamicModule_6b5cbe82-d634-41d1-ae5e-ad7fe8d57fe0
StatusMessage :
HasMoreData   : True
Location      :
Command       : $random = Get-Random -Min 0 -Max 100
JobStateInfo  : Running
Finished      : System.Threading.ManualResetEvent
InstanceId    : 88944290-133d-4b44-8752-f901bd8012e2
Id            : 1
Name          : Timer.Random
ChildJobs     : {}
...

PS C:\> & $Subscriber.action.module {$Random}
96
PS C:\> & $Subscriber.action.module {$Random}
23
```

In dit voor beeld ziet u hoe u de dynamische module gebruikt in het object **PSEventJob** in de eigenschap Action van de abonnee van de gebeurtenis.

De eerste opdracht maakt gebruik van de cmdlet New-Object om een timer object te maken.
Met de tweede opdracht wordt het interval van de timer ingesteld op 500 (milliseconden).

De derde opdracht gebruikt de cmdlet Register-ObjectEvent om de verstreken gebeurtenis van het object Timer te registreren.
De opdracht bevat een actie waarmee de gebeurtenis wordt afgehandeld.
Wanneer het timer interval is verstreken, wordt een gebeurtenis gegenereerd en worden de opdrachten in de actie uitgevoerd.
In dit geval genereert de cmdlet Get-Random een wille keurig getal tussen 0 en 100 en slaat dit op in de $Random variabele.
De bron-id van de gebeurtenis is timer. wille keurig.

Wanneer u een *actie* parameter gebruikt in een **REGI ster-ObjectEvent** opdracht, retourneert de opdracht een **PSEventJob** -object dat de actie vertegenwoordigt.

Met de vierde opdracht wordt de timer ingeschakeld.

De vijfde opdracht maakt gebruik van de cmdlet **Get-EventSubscriber** om de gebeurtenis abonnee van de timer. wille keurige gebeurtenis op te halen.
Het event Subscriber-object wordt opgeslagen in de variabele $Subscriber.

De zesde opdracht geeft aan dat de eigenschap Action van het object Event Subscriber een **PSEventJob** -object bevat.
Het bevat eigenlijk hetzelfde **PSEventJob** -object dat de opdracht **REGI ster-ObjectEvent** heeft geretourneerd.

De zevende opdracht maakt gebruik van de cmdlet Format-List om alle eigenschappen van het object **PSEventJob** in de eigenschap Action in een lijst weer te geven.
Het resultaat blijkt dat het object **PSEventJob** een module-eigenschap heeft die een dynamische script module bevat waarmee de actie wordt geïmplementeerd.

De overige opdrachten gebruiken de aanroep operator (&) om de opdracht in de module aan te roepen en de waarde van de $Random variabele weer te geven.
U kunt de aanroep operator gebruiken om een wille keurige opdracht aan te roepen in een module, met inbegrip van opdrachten die niet worden geëxporteerd.
In dit geval geven de opdrachten het wille keurig getal weer dat wordt gegenereerd wanneer de verstreken gebeurtenis optreedt.

Zie [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md)voor meer informatie over modules.

## PARAMETERS

### -Force
Hiermee wordt aangegeven dat met deze cmdlet alle gebeurtenis abonnees worden opgehaald, waaronder abonnees voor gebeurtenissen die zijn verborgen met de para meter *SupportEvent* van Regi ster-ObjectEvent, REGI ster-WmiEvent en REGI ster-EngineEvent.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SourceIdentifier
Hiermee wordt de waarde van de eigenschap **SourceIdentifier** opgegeven waarmee alleen de gebeurtenis abonnees worden opgehaald.
**Get-EventSubscriber** haalt standaard alle gebeurtenis abonnees op in de sessie.
Joker tekens zijn niet toegestaan.
Deze para meter is hoofdletter gevoelig.

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

### -SubscriptionId
Hiermee geeft u de abonnements-id op die met deze cmdlet wordt opgehaald.
**Get-EventSubscriber** haalt standaard alle gebeurtenis abonnees op in de sessie.

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

### CommonParameters
Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Geen
U kunt geen invoer van een pipe naar deze cmdlet.

## UITVOER

### System. Management. Automation. PSEventSubscriber
**Get-EventSubscriber** retourneert een-object dat elke gebeurtenis abonnee vertegenwoordigt.

## OPMERKINGEN

* Met de cmdlet New-Event, die een aangepaste gebeurtenis maakt, wordt er geen abonnee gegenereerd. Daarom kan de cmdlet **Get-EventSubscriber** geen Subscriber-object vinden voor deze gebeurtenissen. Als u echter de Register-EngineEvent cmdlet gebruikt om u te abonneren op een aangepaste gebeurtenis (als u de gebeurtenis wilt door sturen of als u een actie wilt opgeven), wordt met **Get-EventSubscriber** de abonnee gezocht die door **REGI ster-EngineEvent** wordt gegenereerd.

  Gebeurtenissen, gebeurtenis abonnementen en de gebeurtenis wachtrij bestaan alleen in de huidige sessie.
Als u de huidige sessie sluit, wordt de gebeurtenis wachtrij verwijderd en wordt het gebeurtenis abonnement geannuleerd.

*

## GERELATEERDE KOPPELINGEN

[Get-Event](Get-Event.md)

[Nieuw-gebeurtenis](New-Event.md)

[REGI ster-EngineEvent](Register-EngineEvent.md)

[REGI ster-ObjectEvent](Register-ObjectEvent.md)

[Remove-gebeurtenis](Remove-Event.md)

[Registratie ongedaan maken-gebeurtenis](Unregister-Event.md)

[Wachten gebeurtenis](Wait-Event.md)
