---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 02/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/register-engineevent?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-EngineEvent
ms.openlocfilehash: 005e495ff5f532cc947edf894a67c078e524a72c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250954"
---
# Register-EngineEvent

## SAMENVATTING
Abonneren op gebeurtenissen die worden gegenereerd door de Power shell-engine en door de `New-Event` cmdlet.

## SYNTAXIS

```
Register-EngineEvent [-SourceIdentifier] <String> [[-Action] <ScriptBlock>] [-MessageData <PSObject>]
 [-SupportEvent] [-Forward] [-MaxTriggerCount <Int32>] [<CommonParameters>]
```

## BESCHRIJVING

De `Register-EngineEvent` cmdlet abonneert zich op gebeurtenissen die worden gegenereerd door de Power shell-engine en de `New-Event` cmdlet. Gebruik de para meter **SourceIdentifier** om de gebeurtenis op te geven.

U kunt deze cmdlet gebruiken om u te abonneren op de gebeurtenis van de **afsluit** engine en de gebeurtenissen die door de cmdlet worden gegenereerd `New-Event` . Deze gebeurtenissen worden automatisch toegevoegd aan uw gebeurtenis wachtrij in uw sessie zonder dat u zich abonneert. Met abonneren kunt u de gebeurtenissen echter door sturen, een actie opgeven die op de gebeurtenissen reageert en het abonnement annuleren.

Wanneer de geabonneerde gebeurtenis is gegenereerd, wordt deze toegevoegd aan de gebeurtenis wachtrij in uw sessie. Gebruik de cmdlet om gebeurtenissen in de gebeurtenis wachtrij op te halen `Get-Event` .

Wanneer u zich abonneert op een gebeurtenis, wordt een gebeurtenis abonnee toegevoegd aan uw sessie. Als u de gebeurtenis abonnees in de sessie wilt ophalen, gebruikt u de `Get-EventSubscriber` cmdlet. Als u het abonnement wilt annuleren, gebruikt u de `Unregister-Event` cmdlet waarmee de gebeurtenis abonnee uit de sessie wordt verwijderd.

## VOORBEELDEN

### Voor beeld 1: een Power shell-engine gebeurtenis op externe computers registreren

Dit voor beeld registreert voor een Power shell-engine gebeurtenis op twee externe computers.

```powershell
$S = New-PSSession -ComputerName "Server01, Server02"
Invoke-Command -Session $S { Register-EngineEvent -SourceIdentifier ([System.Management.Automation.PsEngineEvent]::Exiting) -Forward }
```

`New-PSSession` Hiermee maakt u een door de gebruiker beheerde sessie (PSSession) op elke externe computer. De `Invoke-Command` cmdlet voert de `Register-EngineEvent` opdracht uit in de externe sessies.
`Register-EngineEvent` maakt gebruik van de para meter **SourceIdentifier** om de gebeurtenis te identificeren. Met de para meter **Forward** wordt de engine verteld om de gebeurtenissen van de externe sessie door te sturen naar de lokale sessie.

### Voor beeld 2: een opgegeven actie uitvoeren wanneer de gebeurtenis afsluiten plaatsvindt

Dit voor beeld laat zien hoe u `Register-EngineEvent` kunt uitvoeren om een specifieke actie uit te voeren wanneer de **Power shell. exiting** -gebeurtenis plaatsvindt.

```powershell
Register-EngineEvent -SourceIdentifier PowerShell.Exiting -SupportEvent -Action {
    Get-History | Export-Clixml $Home\history.clixml
}
```

De para meter **SupportEvent** wordt toegevoegd om het gebeurtenis abonnement te verbergen. Wanneer Power shell wordt afgesloten, wordt in dit geval de opdracht geschiedenis van de afsluit sessie een XML-bestand in de map van de gebruiker geëxporteerd `$Home` .

### Voor beeld 3: een door de gebruiker gedefinieerde gebeurtenis maken en abonneren

In dit voor beeld wordt een abonnement gemaakt voor gebeurtenissen uit de bron- **MyEventSource**. Dit is een wille keurige bron die we gaan gebruiken om de voortgang van een taak te bewaken. `Register-EngineEvent` wordt gebruikt om het abonnement te maken. Het script blok voor de **actie** parameter registreert de gebeurtenis gegevens in een tekst bestand.

```powershell
Register-EngineEvent -SourceIdentifier MyEventSource -Action {
    "Event: {0}" -f $event.messagedata | Out-File c:\temp\MyEvents.txt -Append
}

Start-Job -Name TestJob -ScriptBlock {
    While ($True) {
        Register-EngineEvent -SourceIdentifier MyEventSource -Forward
        Start-Sleep -seconds 2
        "Doing some work..."
        New-Event -SourceIdentifier MyEventSource -Message ("{0} -  Work done..." -f (Get-Date))
    }
}
Start-Sleep -seconds 4
Get-EventSubscriber
Get-Job
```

```Output
SubscriptionId   : 12
SourceObject     :
EventName        :
SourceIdentifier : MyEventSource
Action           : System.Management.Automation.PSEventJob
HandlerDelegate  :
SupportEvent     : False
ForwardEvent     : False

Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
18     MyEventSource                   Running       True                                 …
19     TestJob         BackgroundJob   Running       True            localhost            …
```

`Register-EngineEvent` Taak-id 18 gemaakt. `Start-Job` Er is een taak-id 19 gemaakt. In voor beeld #4 worden het gebeurtenis abonnement en de taken verwijderd, waarna het logboek bestand wordt gecontroleerd.

### Voor beeld 4: registratie van gebeurtenissen opheffen en taken opschonen

Dit is een voortzetting van voor beeld 3. In dit voor beeld wachten we tien seconden om verschillende gebeurtenissen te laten optreden. Vervolgens wordt de registratie van het gebeurtenis abonnement ongedaan gemaakt.

```powershell
PS> Start-Sleep -seconds 10
PS> Get-EventSubscriber | Unregister-Event
PS> Get-Job

Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
18     MyEventSource                   Stopped       False                                …
19     TestJob         BackgroundJob   Running       True            localhost            …

PS> Stop-Job -Id 19
PS> Get-Job | Remove-Job
PS> Get-Content C:\temp\MyEvents.txt
Event: 2/18/2020 2:36:19 PM -  Work done...
Event: 2/18/2020 2:36:21 PM -  Work done...
Event: 2/18/2020 2:36:23 PM -  Work done...
Event: 2/18/2020 2:36:25 PM -  Work done...
Event: 2/18/2020 2:36:27 PM -  Work done...
Event: 2/18/2020 2:36:29 PM -  Work done...
Event: 2/18/2020 2:36:31 PM -  Work done...
```

De `Unregister-Event` cmdlet stopt de taak die is gekoppeld aan het gebeurtenis abonnement (taak-id 18). Taak-id 19 wordt nog steeds uitgevoerd en er worden nieuwe gebeurtenissen gemaakt. We gebruiken de **taak** -cmdlets om de taak te stoppen en de overbodige taak objecten te verwijderen. `Get-Content` Hiermee wordt de inhoud van het logboek bestand weer gegeven.

## PARAMETERS

### -Actie

Geeft opdrachten voor het afhandelen van de gebeurtenissen. De opdrachten in de **actie** worden uitgevoerd wanneer een gebeurtenis wordt gegenereerd, in plaats van de gebeurtenis naar de gebeurtenis wachtrij te verzenden. Plaats de opdrachten tussen accolades ({}) om een script blok te maken.

De waarde van de **actie** parameter kan de `$Event` variabelen, `$EventSubscriber` , `$Sender` , `$EventArgs` en `$Args` automatisch bevatten, die informatie geven over de gebeurtenis in het **actie** script blok. Zie [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)voor meer informatie.

Wanneer u een actie opgeeft, `Register-EngineEvent` retourneert een gebeurtenis taak object dat die actie vertegenwoordigt. U kunt de taak-cmdlets gebruiken om de gebeurtenis taak te beheren.

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: False
Position: 101
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Voorwaarts

Geeft aan dat de cmdlet gebeurtenissen voor dit abonnement naar de sessie op de lokale computer verzendt.
Gebruik deze para meter als u zich registreert voor gebeurtenissen op een externe computer of in een externe sessie.

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

### -MaxTriggerCount

Hiermee geeft u het maximum aantal keer op dat de actie voor het gebeurtenis abonnement wordt uitgevoerd.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
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
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SourceIdentifier

Hiermee geeft u de bron-id op van de gebeurtenis waarop u bent geabonneerd. De bron-id moet uniek zijn in de huidige sessie. Deze parameter is vereist.

De waarde van deze para meter wordt weer gegeven in de waarde van de eigenschap **SourceIdentifier** van het object Subscriber en alle gebeurtenis objecten die zijn gekoppeld aan dit abonnement.

De waarde is specifiek voor de bron van de gebeurtenis. Dit kan een wille keurige waarde zijn die u hebt gemaakt voor gebruik met de `New-Event` cmdlet. De Power shell-Engine ondersteunt de **EngineEvent** -waarden **Power shell. exiting** en **Power shell. OnIdle**.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 100
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SupportEvent

Hiermee wordt aangegeven dat het gebeurtenis abonnement wordt verborgen met de cmdlet. Voeg deze para meter toe wanneer het huidige abonnement deel uitmaakt van een complexere gebeurtenis registratie mechanisme en niet onafhankelijk moet worden gedetecteerd.

Als u een abonnement wilt bekijken of annuleren dat is gemaakt met de para meter **SupportEvent** , voegt u de para meter **Force** toe aan de `Get-EventSubscriber` `Unregister-Event` cmdlets of.

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

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Geen

U kunt geen pipe invoer naar `Register-EngineEvent` .

## UITVOER

### Geen of System. Management. Automation. PSEventJob

Als u de **actie** parameter gebruikt, `Register-EngineEvent` retourneert een **System. Management. Automation. PSEventJob** -object. Anders wordt er geen uitvoer gegenereerd.

## OPMERKINGEN

Gebeurtenissen, gebeurtenis abonnementen en de gebeurtenis wachtrij bestaan alleen in de huidige sessie. Als u de huidige sessie sluit, wordt de gebeurtenis wachtrij verwijderd en wordt het gebeurtenis abonnement geannuleerd.

## GERELATEERDE KOPPELINGEN

[Get-Event](Get-Event.md)

[Nieuw-gebeurtenis](New-Event.md)

[REGI ster-ObjectEvent](Register-ObjectEvent.md)

[Remove-gebeurtenis](Remove-Event.md)

[Registratie ongedaan maken-gebeurtenis](Unregister-Event.md)

[Wachten gebeurtenis](Wait-Event.md)
