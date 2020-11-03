---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 02/20/2019
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/register-cimindicationevent?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-CimIndicationEvent
ms.openlocfilehash: 802af0d2a130a0ddc01d9a94cadf7f503eb7d697
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249479"
---
# Register-CimIndicationEvent

## SAMENVATTING
Abonneer u op indicaties met een filter expressie of een query-expressie.

## SYNTAXIS

### ClassNameComputerSet (standaard)

```
Register-CimIndicationEvent [-Namespace <String>] [-ClassName] <String>
 [-OperationTimeoutSec <UInt32>] [-ComputerName <String>] [[-SourceIdentifier] <String>]
 [[-Action] <ScriptBlock>] [-MessageData <PSObject>] [-SupportEvent] [-Forward]
 [-MaxTriggerCount <Int32>] [<CommonParameters>]
```

### ClassNameSessionSet

```
Register-CimIndicationEvent [-Namespace <String>] [-ClassName] <String>
 [-OperationTimeoutSec <UInt32>] -CimSession <CimSession> [[-SourceIdentifier] <String>]
 [[-Action] <ScriptBlock>] [-MessageData <PSObject>] [-SupportEvent] [-Forward]
 [-MaxTriggerCount <Int32>] [<CommonParameters>]
```

### QueryExpressionSessionSet

```
Register-CimIndicationEvent [-Namespace <String>] [-Query] <String> [-QueryDialect <String>]
 [-OperationTimeoutSec <UInt32>] -CimSession <CimSession> [[-SourceIdentifier] <String>]
 [[-Action] <ScriptBlock>] [-MessageData <PSObject>] [-SupportEvent] [-Forward]
 [-MaxTriggerCount <Int32>] [<CommonParameters>]
```

### QueryExpressionComputerSet

```
Register-CimIndicationEvent [-Namespace <String>] [-Query] <String> [-QueryDialect <String>]
 [-OperationTimeoutSec <UInt32>] [-ComputerName <String>] [[-SourceIdentifier] <String>]
 [[-Action] <ScriptBlock>] [-MessageData <PSObject>] [-SupportEvent] [-Forward]
 [-MaxTriggerCount <Int32>] [<CommonParameters>]
```

## BESCHRIJVING

De `Register-CimIndicationEvent` cmdlet wordt geabonneerd op indicaties met behulp van de naam van een indicatie klasse of een query-expressie. Gebruik de para meter **SourceIdentifier** Geef een naam op voor het abonnement.

Met deze cmdlet wordt een **EventSubscription** -object geretourneerd. U kunt dit object gebruiken om het abonnement te annuleren.

## VOORBEELDEN

### Voor beeld 1: de gebeurtenissen registreren die door een klasse zijn gegenereerd

In dit voor beeld wordt een abonnement genomen op de gebeurtenissen die worden gegenereerd door de klasse met de naam **Win32_ProcessStartTrace**. Deze klasse genereert een gebeurtenis wanneer een proces wordt gestart.

```powershell
Register-CimIndicationEvent -ClassName 'Win32_ProcessStartTrace' -SourceIdentifier "ProcessStarted"
Get-Event -SourceIdentifier "ProcessStarted"
```

De `Get-Event` cmdlet haalt de gebeurtenissen op met het **ProcessStarted** -abonnement. Zie [Get-Event](../Microsoft.PowerShell.Utility/Get-Event.md)voor meer informatie.

> [!NOTE]
> Voor dit voor beeld moet u Power shell uitvoeren als beheerder.

### Voor beeld 2: de gebeurtenissen registreren met behulp van een query

In dit voor beeld wordt een-query gebruikt om u te abonneren op een gebeurtenis die wordt gegenereerd wanneer er een wijziging is in het exemplaar van een klasse met de naam **Win32_LocalTime**.

```powershell
$query = "SELECT * FROM CIM_InstModification WHERE TargetInstance ISA 'Win32_LocalTime'"
Register-CimIndicationEvent -Query $query -SourceIdentifier "Timer"
```

### Voor beeld 3: een script uitvoeren wanneer de gebeurtenis arriveert

In dit voor beeld ziet u hoe u een actie gebruikt als antwoord op een gebeurtenis. De variabele `$action` bevat het script blok voor de **actie** , waarbij de `$event` variabele wordt gebruikt voor toegang tot de gebeurtenis ontvangen van CIM.

```powershell
$action = {
  $name = $event.SourceEventArgs.NewEvent.ProcessName
  $id = $event.SourceEventArgs.NewEvent.ProcessId
  Write-Host -Object "New Process Started : Name = $name
 ID = $id"
}
Register-CimIndicationEvent -ClassName 'Win32_ProcessStartTrace' -SourceIdentifier "ProcessStarted" -Action $action
```

Zie [Win32_ProcessStartTrace](/previous-versions/windows/desktop/krnlprov/win32-processstarttrace)voor meer informatie.

### Voor beeld 4: de gebeurtenissen registreren op een externe computer

In dit voor beeld wordt geabonneerd op gebeurtenissen op een externe computer met de naam **Server01**. Gebeurtenissen die van de CIM-server worden ontvangen, worden opgeslagen in de wachtrij van de huidige Power shell-sessie en vervolgens wordt een lokale gebeurtenis uitgevoerd `Get-Event` om de gebeurtenissen op te halen.

```powershell
Register-CimIndicationEvent -ClassName 'Win32_ProcessStartTrace' -SourceIdentifier "ProcessStarted" -ComputerName Server01
Get-Event -SourceIdentifier "ProcessStarted"
```

## PARAMETERS

### -Actie

Hiermee geeft u de opdrachten op waarmee de gebeurtenissen worden verwerkt. De opdrachten die door deze para meter worden opgegeven, worden uitgevoerd wanneer een gebeurtenis wordt gegenereerd, in plaats van de gebeurtenis naar de gebeurtenis wachtrij te verzenden. Plaats de opdrachten tussen accolades ( `{}` ) om een script blok te maken.

Het script blok dat is opgegeven met **actie** kan `$Event` de `$EventSubscriber` variabelen,,, `$Sender` `$SourceEventArgs` en `$SourceArgs` automatisch bevatten. deze bevatten informatie over de gebeurtenis in het blok **actie** script. Zie [about Automatic Varia bles](../microsoft.powershell.core/about/about_automatic_variables.md)(Engelstalig) voor meer informatie.

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CimSession

De opdracht wordt uitgevoerd met behulp van de opgegeven CIM-sessie. Voer een variabele in die de CIM-sessie bevat of een opdracht die de CIM-sessie, zoals de `New-CimSession` of cmdlets, maakt of ontvangt `Get-CimSession` . Zie [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md)voor meer informatie.

```yaml
Type: Microsoft.Management.Infrastructure.CimSession
Parameter Sets: ClassNameSessionSet, QueryExpressionSessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ClassName

Hiermee geeft u de indicatie klasse op waarop u bent geabonneerd. U kunt met behulp van het tabblad volt ooien door de lijst met klassen bladeren, omdat Power shell een lijst met klassen van de lokale WMI-server krijgt om een lijst met klasse-namen te bieden.

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, ClassNameSessionSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

Hiermee geeft u de naam op van de computer waarop u de CIM-bewerking wilt uitvoeren. U kunt een Fully Qualified Domain Name (FQDN), een NetBIOS-naam of een IP-adres opgeven.

Als u deze para meter opgeeft, maakt de cmdlet een tijdelijke sessie met de opgegeven computer met behulp van het WsMan-protocol. Als u deze para meter niet opgeeft, voert de cmdlet de bewerking uit op het lokale systeem met behulp van Component Object Model (COM).

Als er meerdere bewerkingen worden uitgevoerd op dezelfde computer, kunt u verbinding maken met behulp van een CIM-sessie voor betere prestaties.

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, QueryExpressionComputerSet
Aliases: CN, ServerName

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Voorwaarts

Hiermee geeft u op dat gebeurtenissen voor het abonnement worden doorgestuurd naar de sessie op de lokale computer. Gebruik deze para meter als u zich registreert voor gebeurtenissen op een externe computer of in een externe sessie.

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

Para meter om aan te geven dat de abonnee automatisch moet worden verwijderd na het activeren van de opgegeven tijden. Als de waarde gelijk is aan of kleiner is dan nul, is er geen limiet voor het aantal keren dat de gebeurtenis kan worden geactiveerd zonder dat de registratie ervan ongedaan wordt gemaakt.

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

Hiermee geeft u aanvullende gegevens op die u wilt koppelen aan dit gebeurtenis abonnement. De waarde van deze para meter wordt weer gegeven in de eigenschap **MessageData** van alle gebeurtenissen die aan dit abonnement zijn gekoppeld.

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

### -Naam ruimte

Hiermee geeft u de naam ruimte voor de CIM-bewerking op. De standaard naam ruimte is **root-cimv2**. U kunt met behulp van tab volt ooien door de lijst met naam ruimten bladeren, omdat Power shell een lijst met naam ruimten van de lokale WMI-server krijgt om de lijst met naam ruimten op te geven.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -OperationTimeoutSec

Hiermee geeft u de hoeveelheid tijd op die de cmdlet wacht op een reactie van de computer. Standaard is de waarde van deze para meter 0, wat betekent dat de cmdlet de standaard time-outwaarde voor de server gebruikt.

Als de para meter **OperationTimeoutSec** is ingesteld op een waarde die kleiner is dan de robuuste time-out voor de verbinding opnieuw proberen 3 minuten, kunnen netwerk fouten die langer zijn dan de waarde van de para meter **OperationTimeoutSec** , niet worden hersteld, omdat er een time-out optreedt voor de bewerking op de server voordat de client opnieuw verbinding kan maken.

```yaml
Type: System.UInt32
Parameter Sets: (All)
Aliases: OT

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Query uitvoeren

Hiermee geeft u een query op die moet worden uitgevoerd op de CIM-server. Als de opgegeven waarde dubbele aanhalings tekens `"` , enkele aanhalings tekens `'` of een back slash bevat `\` , moet u deze tekens weglaten door ze voor te plaatsen met het back slash-teken. Als de opgegeven waarde gebruikmaakt van de WQL LIKE-operator, moet u de volgende tekens door geven tussen vier Kante haken `[]` : percentage `%` , onderstrepings teken `_` of vier kant haakje openen `[` .

```yaml
Type: System.String
Parameter Sets: QueryExpressionSessionSet, QueryExpressionComputerSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -QueryDialect

Hiermee geeft u de query taal op die wordt gebruikt voor de **query** parameter. De acceptabele waarden voor deze para meter zijn: **WQL** of **CQL**. De standaard waarde is **WQL**.

```yaml
Type: System.String
Parameter Sets: QueryExpressionSessionSet, QueryExpressionComputerSet
Aliases:

Required: False
Position: Named
Default value: WQL
Accept pipeline input: False
Accept wildcard characters: False
```

### -SourceIdentifier

Hiermee geeft u een naam op voor het abonnement. De naam die u opgeeft, moet uniek zijn in de huidige sessie. De standaard waarde is een GUID die door Power shell wordt toegewezen. Deze waarde wordt weer gegeven in de waarde van de eigenschap **SourceIdentifier** van het object Subscriber en alle gebeurtenis objecten die zijn gekoppeld aan dit abonnement.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SupportEvent

Geeft aan dat het gebeurtenis abonnement is verborgen. Gebruik deze para meter wanneer het huidige abonnement deel uitmaakt van een complexere gebeurtenis registratie mechanisme en niet onafhankelijk moet worden gedetecteerd.

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

Deze cmdlet accepteert geen invoer objecten.

## UITVOER

### System. object

Met deze cmdlet wordt een **EventSubscription** -object uitgevoerd.

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Get-Event](../microsoft.powershell.utility/get-event.md)

[Remove-gebeurtenis](../microsoft.powershell.utility/remove-event.md)

[Registratie ongedaan maken-gebeurtenis](../microsoft.powershell.utility/unregister-event.md)

[Write-host](../microsoft.powershell.utility/write-host.md)

[Get-CimSession](Get-CimSession.md)

[New-CimSession](New-CimSession.md)
