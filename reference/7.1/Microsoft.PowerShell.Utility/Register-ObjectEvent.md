---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/register-objectevent?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-ObjectEvent
ms.openlocfilehash: a8e59419aed08a4ebe4fc781e9827ca5b0593b3e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250183"
---
# Register-ObjectEvent

## SAMENVATTING
Abonneer u op de gebeurtenissen die door een Microsoft .NET Framework-object worden gegenereerd.

## SYNTAXIS

```
Register-ObjectEvent [-InputObject] <PSObject> [-EventName] <String> [[-SourceIdentifier] <String>]
 [[-Action] <ScriptBlock>] [-MessageData <PSObject>] [-SupportEvent] [-Forward] [-MaxTriggerCount <Int32>]
 [<CommonParameters>]
```

## BESCHRIJVING

De `Register-ObjectEvent` cmdlet abonneert zich op gebeurtenissen die worden gegenereerd door .net-objecten op de lokale computer of op een externe computer.

Wanneer de geabonneerde gebeurtenis is gegenereerd, wordt deze toegevoegd aan de gebeurtenis wachtrij in uw sessie. Gebruik de cmdlet om gebeurtenissen in de gebeurtenis wachtrij op te halen `Get-Event` .

U kunt de para meters van gebruiken `Register-ObjectEvent` om eigenschaps waarden op te geven van de gebeurtenissen die u kunnen helpen bij het identificeren van de gebeurtenis in de wachtrij. U kunt ook de **actie** parameter gebruiken om op te geven welke acties moeten worden uitgevoerd wanneer een geplaatste gebeurtenis wordt gegenereerd en de para meter **Forward** voor het verzenden van externe gebeurtenissen naar de gebeurtenis wachtrij in de lokale sessie.

Wanneer u zich abonneert op een gebeurtenis, wordt een gebeurtenis abonnee toegevoegd aan uw sessie. Als u de gebeurtenis abonnees in de sessie wilt ophalen, gebruikt u de `Get-EventSubscriber` cmdlet. Als u het abonnement wilt annuleren, gebruikt u de `Unregister-Event` cmdlet waarmee de gebeurtenis abonnee uit de sessie wordt verwijderd.

## VOORBEELDEN

### Voor beeld 1: abonneren op gebeurtenissen wanneer een nieuw proces wordt gestart

In dit voor beeld wordt een abonnement genomen op gebeurtenissen die worden gegenereerd wanneer een nieuw proces wordt gestart.

De opdracht gebruikt het object **ManagementEventWatcher** om **EventArrived** -gebeurtenissen op te halen. Met een query-object geeft u op dat de gebeurtenissen worden gemaakt voor het maken van een instantie voor de klasse **Win32_Process** .

```powershell
$queryParameters = '__InstanceCreationEvent', (New-Object TimeSpan 0,0,1),
    "TargetInstance isa 'Win32_Process'"
$Query = New-Object System.Management.WqlEventQuery -ArgumentList $queryParameters
$ProcessWatcher = New-Object System.Management.ManagementEventWatcher $Query
Register-ObjectEvent -InputObject $ProcessWatcher -EventName "EventArrived"
```

### Voor beeld 2: een actie opgeven om te reageren op een gebeurtenis

Wanneer u een actie opgeeft, worden gebeurtenissen die worden gegenereerd, niet toegevoegd aan de gebeurtenis wachtrij. In plaats daarvan reageert de actie op de gebeurtenis. In dit voor beeld wordt een nieuwe **ProcessCreated** -gebeurtenis gegenereerd wanneer er een gebeurtenis voor het maken van een instantie wordt gegenereerd die aangeeft dat een nieuw proces wordt gestart.

```powershell
$queryParameters = '__InstanceCreationEvent', (New-Object TimeSpan 0,0,1),
    "TargetInstance isa 'Win32_Process'"
$Query = New-Object System.Management.WqlEventQuery -ArgumentList $queryParameters
$ProcessWatcher = New-Object System.Management.ManagementEventWatcher $query
$newEventArgs = @{
    SourceIdentifier = 'PowerShell.ProcessCreated'
    Sender = $Sender
    EventArguments = $EventArgs.NewEvent.TargetInstance
}
$Action = { New-Event @newEventArgs }
Register-ObjectEvent -InputObject $ProcessWatcher -EventName "EventArrived" -Action $Action
```

```Output
Id   Name               PSJobTypeName   State       HasMoreData   Location   Command
--   ----               -------------   -----       -----------   --------   -------
 5   3db2d67a-efff-...                 NotStarted   False                    New-Event @newEventArgs
```

De actie gebruikt de `$Sender` en `$EventArgs` automatische variabelen die alleen worden ingevuld voor gebeurtenis acties.

De `Register-ObjectEvent` opdracht retourneert een taak object dat de actie vertegenwoordigt die als achtergrond taak wordt uitgevoerd. U kunt de taak-cmdlets, zoals `Get-Job` en `Receive-Job` , gebruiken om de achtergrond taak te beheren. Zie [About Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md) (Taken) voor meer informatie.

### Voor beeld 3: abonneren op object gebeurtenissen op externe computers

In dit voor beeld ziet u hoe u zich abonneert op object gebeurtenissen op externe computers. In dit voor beeld wordt de `Enable-ProcessCreationEvent` functie gebruikt die in het `ProcessCreationEvent.ps1` script bestand is gedefinieerd. Dit script is beschikbaar voor alle computers in het voor beeld.

```powershell
# ProcessCreationEvent.ps1
function  Enable-ProcessCreationEvent {
    $queryParameters = "__InstanceCreationEvent", (New-Object TimeSpan 0,0,1),
        "TargetInstance isa 'Win32_Process'"
    $Query = New-Object System.Management.WqlEventQuery -ArgumentList $queryParameters

    $objectEventArgs = @{
        Input = New-Object System.Management.ManagementEventWatcher $Query
        EventName = 'EventArrived'
        SourceIdentifier = 'WMI.ProcessCreated'
        MessageData = 'Test'
        Forward = $True
    }
    Register-ObjectEvent @objectEventArgs
}

$S = New-PSSession -ComputerName "Server01, Server02"
Invoke-Command -Session $S -FilePath ProcessCreationEvent.ps1
Invoke-Command -Session $S { Enable-ProcessCreationEvent }
```

De eerste **PSSessions** maken op twee externe computers en slaat ze op in de `$S` variabele. Vervolgens voert de `Invoke-Command` cmdlet het `ProcessCreationEvent.ps1` script uit in elk van de PSSessions in `$S` . Met deze actie wordt de `Enable-ProcessCreationEvent` functie in de externe sessies gemaakt.
Ten slotte wordt de `Enable-ProcessCreationEvent` functie uitgevoerd in de externe sessies.

 De functie bevat een `Register-ObjectEvent` opdracht die zich abonneert op gebeurtenissen voor het maken van instanties op het **Win32_Process** -object via het **ManagementEventWatcher** -object en de bijbehorende **EventArrived** -gebeurtenis.

### Voor beeld 4: de dynamische module gebruiken in het PSEventJob-object

In dit voor beeld ziet u hoe u de dynamische module gebruikt in het **PSEventJob** -object dat wordt gemaakt wanneer u een **actie** opneemt in een gebeurtenis registratie. Eerst createand en inschakelt u een timer object in en stelt u het interval van de timer in op 500 (milliseconden). De `Register-ObjectEvent` cmdlet registreert de **verstreken** gebeurtenis van het object Timer. Het **PSEventJob** -object wordt opgeslagen in de `$Job` variabele en is ook beschikbaar in de eigenschap **Action** van de abonnee van de gebeurtenis. Zie [Get-EventSubscriber](Get-EventSubscriber.md)voor meer informatie.

Wanneer het timer interval is verstreken, wordt een gebeurtenis gegenereerd en wordt de actie uitgevoerd. In dit geval genereert de `Get-Random` cmdlet een wille keurig getal tussen 0 en 100 en slaat deze op in de `$Random` variabele.

```powershell
$Timer = New-Object Timers.Timer
$Timer.Interval = 500
$Timer.Enabled = $True
$objectEventArgs = @{
    InputObject = $Timer
    EventName = 'Elapsed'
    SourceIdentifier = 'Timer.Random'
    Action = {$Random = Get-Random -Min 0 -Max 100}
}
$Job = Register-ObjectEvent @objectEventArgs
$Job | Format-List -Property *
& $Job.module {$Random}
& $Job.module {$Random}
```

```Output
State         : Running
Module        : __DynamicModule_53113769-31f2-42dc-830b-8749325e28d6
StatusMessage :
HasMoreData   : True
Location      :
Command       : $Random = Get-Random -Min 0 -Max 100
JobStateInfo  : Running
Finished      : System.Threading.ManualResetEvent
InstanceId    : 47b5ec9f-bfe3-4605-860a-4674e5d44ca8
Id            : 7
Name          : Timer.Random
ChildJobs     : {}
PSBeginTime   : 6/27/2019 10:19:06 AM
PSEndTime     :
PSJobTypeName :
Output        : {}
Error         : {}
Progress      : {}
Verbose       : {}
Debug         : {}
Warning       : {}
Information   : {}
60
47
```

De **PSEventJob** heeft een **module** -eigenschap die een dynamische script module bevat waarmee de actie wordt geïmplementeerd. Met de aanroep operator ( `&` ) roept u de opdracht in de module in om de waarde van de variabele weer te geven `$Random` .

Zie [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md)voor meer informatie over modules.

## PARAMETERS

### -Actie

Hiermee geeft u de opdrachten voor het afhandelen van de gebeurtenis. De opdrachten in de **actie** worden uitgevoerd wanneer een gebeurtenis wordt gegenereerd, in plaats van de gebeurtenis naar de gebeurtenis wachtrij te verzenden. Plaats de opdrachten tussen accolades ({}) om een script blok te maken.

De waarde van de **actie** parameter kan de `$Event` variabelen, `$EventSubscriber` , `$Sender` , `$EventArgs` en `$Args` automatisch bevatten. Deze variabelen bieden informatie over de gebeurtenis in het **actie** script blok. Zie [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)voor meer informatie.

Wanneer u een actie opgeeft, `Register-ObjectEvent` retourneert een gebeurtenis taak object dat die actie vertegenwoordigt. U kunt de taak-cmdlets gebruiken om de gebeurtenis taak te beheren.

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

### -Eventname

Hiermee geeft u de gebeurtenis op waarop u bent geabonneerd.

De waarde van deze para meter moet de naam zijn van de gebeurtenis die door het .NET-object wordt weer gegeven. De klasse **ManagementEventWatcher** heeft bijvoorbeeld gebeurtenissen met de naam **EventArrived** en **gestopt**. Gebruik de cmdlet om de gebeurtenis naam van een gebeurtenis te vinden `Get-Member` .

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Voorwaarts

Geeft aan dat de cmdlet gebeurtenissen voor dit abonnement naar een externe sessie verzendt. Gebruik deze para meter als u zich registreert voor gebeurtenissen op een externe computer of in een externe sessie.

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

### -Input object

Hiermee geeft u het .NET-object op waarmee de gebeurtenissen worden gegenereerd. Voer een variabele in die het object bevat of typ een opdracht of expressie waarmee het object wordt opgehaald.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaxTriggerCount

Hiermee geeft u het maximum aantal keren op dat een gebeurtenis kan worden geactiveerd.

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

Hiermee geeft u aanvullende gegevens op die moeten worden gekoppeld aan dit gebeurtenis abonnement. De waarde van deze para meter wordt weer gegeven in de eigenschap MessageData van alle gebeurtenissen die aan dit abonnement zijn gekoppeld.

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

Hiermee geeft u een naam op die u voor het abonnement selecteert. De naam die u selecteert, moet uniek zijn in de huidige sessie. De standaard waarde is de GUID die Power shell toewijst.

De waarde van deze para meter wordt weer gegeven in de waarde van de eigenschap **SourceIdentifier** van het object Subscriber en alle gebeurtenis objecten die zijn gekoppeld aan dit abonnement.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 100
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SupportEvent

Hiermee wordt aangegeven dat het gebeurtenis abonnement wordt verborgen met de cmdlet. Gebruik deze para meter wanneer het huidige abonnement deel uitmaakt van een complex mechanisme voor gebeurtenis registratie en niet onafhankelijk moet worden gedetecteerd.

Als u een abonnement wilt bekijken of annuleren dat is gemaakt met de para meter **SupportEvent** , gebruikt u de para meter **Force** van de `Get-EventSubscriber` `Unregister-Event` cmdlets.

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

U kunt geen objecten pipeen naar `Register-ObjectEvent` .

## UITVOER

### Geen of System. Management. Automation. PSEventJob

Wanneer u de **actie** parameter gebruikt, `Register-ObjectEvent` retourneert een **System. Management. Automation. PSEventJob** -object. Anders wordt er geen uitvoer gegenereerd.

## OPMERKINGEN

Gebeurtenissen, gebeurtenis abonnementen en de gebeurtenis wachtrij bestaan alleen in de huidige sessie. Als u de huidige sessie sluit, wordt de gebeurtenis wachtrij verwijderd en wordt het gebeurtenis abonnement geannuleerd.

## GERELATEERDE KOPPELINGEN

[Get-Event](Get-Event.md)

[Nieuw-gebeurtenis](New-Event.md)

[REGI ster-EngineEvent](Register-EngineEvent.md)

[Remove-gebeurtenis](Remove-Event.md)

[Registratie ongedaan maken-gebeurtenis](Unregister-Event.md)

[Wachten gebeurtenis](Wait-Event.md)

