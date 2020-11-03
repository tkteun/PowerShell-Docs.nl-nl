---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 11/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/test-connection?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-Connection
ms.openlocfilehash: 54ba1d7db60db7b4bb64f3161bba9c1fba124219
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250000"
---
# Test-Connection

## SAMENVATTING
Verzendt ICMP echo aanvraag pakketten of pings naar een of meer computers.

## SYNTAXIS

### PingCount (standaard)

```
Test-Connection [-Ping] [-IPv4] [-IPv6] [-ResolveDestination] [-Source <String>] [-MaxHops <Int32>]
 [-Count <Int32>] [-Delay <Int32>] [-BufferSize <Int32>] [-DontFragment] [-TimeoutSeconds <Int32>]
 [-TargetName] <String[]> [-Quiet] [<CommonParameters>]
```

### PingContinues

```
Test-Connection [-Ping] [-IPv4] [-IPv6] [-ResolveDestination] [-Source <String>] [-MaxHops <Int32>]
 [-Delay <Int32>] [-BufferSize <Int32>] [-DontFragment] [-Continues] [-TimeoutSeconds <Int32>]
 [-TargetName] <String[]> [-Quiet] [<CommonParameters>]
```

### DetectionOfMTUSize

```
Test-Connection [-IPv4] [-IPv6] [-ResolveDestination] [-TimeoutSeconds <Int32>]
 [-TargetName] <String[]> -MTUSizeDetect [-Quiet] [<CommonParameters>]
```

### TraceRoute

```
Test-Connection [-IPv4] [-IPv6] [-ResolveDestination] [-Source <String>] [-MaxHops <Int32>]
 [-TimeoutSeconds <Int32>] [-TargetName] <String[]> -Traceroute [-Quiet] [<CommonParameters>]
```

### ConnectionByTCPPort

```
Test-Connection [-IPv4] [-IPv6] [-ResolveDestination] [-Source <String>] [-TimeoutSeconds <Int32>]
 [-TargetName] <String[]> -TCPPort <Int32> [-Quiet] [<CommonParameters>]
```

## BESCHRIJVING

De `Test-Connection` cmdlet stuurt Internet Control Message Protocol (ICMP) Echo aanvraag pakketten of pings naar een of meer externe computers en retourneert de antwoorden op de echo reactie. U kunt deze cmdlet gebruiken om te bepalen of er verbinding kan worden gemaakt met een bepaalde computer via een IP-netwerk.

U kunt de para meters van gebruiken `Test-Connection` om zowel de verzendende als ontvangende computers op te geven om de opdracht als achtergrond taak uit te voeren, om een time-out en een aantal pings in te stellen en om de verbinding en verificatie te configureren.

In tegens telling tot de bekende **ping** -opdracht `Test-Connection` retourneert een **TestConnectionCommand + PingReport** -object dat u kunt onderzoeken in Power shell. De **stille** para meter retourneert een **Boole** -waarde in een object **System. Boolean** voor elke geteste verbinding. Als er meerdere verbindingen worden getest, wordt een matrix met **Boole** -waarden geretourneerd.

## VOORBEELDEN

### Voor beeld 1: ECHO aanvragen verzenden naar een externe computer

In dit voor beeld worden ECHO aanvraag pakketten van de lokale computer verzonden naar de Server01-computer.

```powershell
Test-Connection -TargetName Server01 -IPv4
```

```Output
Pinging Server01 [10.59.137.44] with 32 bytes of data:
Reply from 10.59.137.44: bytes=32 time=0ms TTL=128
Reply from 10.59.137.44: bytes=32 time=0ms TTL=128
Reply from 10.59.137.44: bytes=32 time=0ms TTL=128
Reply from 10.59.137.44: bytes=32 time=0ms TTL=128
Ping complete.

Source     Destination Replies
------     ----------- -------
Server01   Server01    {System.Net.NetworkInformation.PingReply, System.Net.NetworkInformation ...
```

`Test-Connection` maakt gebruik van de **TargetName** -para meter om de Server01-computer op te geven. De **IPv4** -para meter geeft u het protocol voor de test op.

De ping-uitvoer wordt verzonden naar de **informatie** stroom terwijl het **TestConnectionCommand + PingReport** -object wordt verzonden naar de stroom van **slagen** . Zie [about_Redirection](../microsoft.powershell.core/about/about_redirection.md)voor meer informatie over de uitvoer stromen.

### Voor beeld 2: ECHO aanvragen verzenden naar verschillende computers

In dit voor beeld worden pings van de lokale computer naar verschillende externe computers verzonden.

```powershell
Test-Connection -TargetName Server01, Server02, Server12
```

### Voor beeld 3: ECHO aanvragen van verschillende computers verzenden naar een computer

In dit voor beeld worden pings van verschillende bron computers verzonden naar één externe computer, Server01.

```powershell
Test-Connection -Source Server02, Server12, localhost -TargetName Server01
```

Gebruik deze opdracht indeling om de latentie van verbindingen vanaf meerdere punten te testen.

### Voor beeld 4: para meters gebruiken om de test opdracht aan te passen

In dit voor beeld worden de para meters van gebruikt `Test-Connection` voor het aanpassen van de opdracht. De lokale computer verzendt een ping-test naar een externe computer.

```powershell
Test-Connection -TargetName Server01 -Count 3 -Delay 2 -MaxHops 255 -BufferSize 256
```

`Test-Connection` maakt gebruik van de para meter **TargetName** om Server01 op te geven. De para meter **aantal** geeft aan dat drie pings worden verzonden naar de Server01-computer, met een **vertraging** van twee seconden intervallen.

U kunt deze opties gebruiken wanneer het ping-antwoord naar verwachting langer duurt dan normaal, ofwel vanwege een uitgebreid aantal hops of een netwerk toestand met een hoog verkeer.

### Voor beeld 5: een test uitvoeren als een achtergrond taak

In dit voor beeld ziet u hoe u een `Test-Connection` opdracht uitvoert als een Power shell-achtergrond taak.

```powershell
$job = Start-Job -ScriptBlock { Test-Connection -TargetName (Get-Content "Servers.txt") }
if ($job.JobStateInfo.State -ne "Running") { $Results = Receive-Job $job }
```

De `Start-Job` opdracht gebruikt de `Test-Connection` cmdlet voor het pingen van veel computers in een onderneming.
De waarde van de **TargetName** -para meter is een `Get-Content` opdracht waarmee een lijst met computer namen uit het `Servers.txt` bestand wordt gelezen. De opdracht gebruikt de `Start-Job` cmdlet om de opdracht uit te voeren als een achtergrond taak en de taak wordt opgeslagen in de `$job` variabele.

De `if` opdracht controleert of de taak nog niet wordt uitgevoerd. Als de taak niet wordt uitgevoerd, `Receive-Job` worden de resultaten opgehaald en opgeslagen in de `$Results` variabele.

### Voor beeld 6: een sessie alleen maken als de verbindings test is geslaagd

In dit voor beeld wordt alleen een sessie op de Server01-computer gemaakt als ten minste één van de pings die naar de computer worden verzonden, slaagt.

```powershell
if (Test-Connection -TargetName Server01 -Quiet) {New-PSSession Server01}
```

De `if` opdracht gebruikt de `Test-Connection` cmdlet om de Server01-computer te pingen. De opdracht maakt gebruik van de **stille** para meter, waarmee een **Booleaanse** waarde wordt geretourneerd in plaats van een **TestConnectionCommand + PingReport** -object.

De waarde is `$True` als een van de vier pings slaagt. Als geen van de pings slaagt, is de waarde `$False` .

Als de `Test-Connection` opdracht een waarde retourneert `$True` , gebruikt de opdracht de `New-PSSession` cmdlet om de **PSSession** te maken.

### Voor beeld 7: de para meter traceroute gebruiken

Vanaf Power shell 6,0 wijst de para meter **traceroute** een route toe tussen de lokale computer en de externe bestemming die u opgeeft met de para meter **TargetName** .

```powershell
Test-Connection -TargetName www.microsoft.com -Traceroute | ForEach-Object {
  $_ | Format-Table Source, DestinationAddress, DestinationHost
  $_.Replies | ForEach-Object {
      $_ | Format-Table Hop, ReplyRouterAddress
      $_.PingReplies | Format-Table
  }
}
```

```Output
Tracing route to www.microsoft.com [96.6.27.90] over a maximum of 128 hops:
  1   0 ms   0 ms   0 ms   192.168.0.3 [192.168.0.3]
  2   0 ms   0 ms   0 ms   192.168.1.1 [192.168.1.1]
  3   3 ms   29 ms   4 ms   96.6.27.90 [96.6.27.90]
Trace complete.

Source      DestinationAddress DestinationHost   Replies
------      ------------------ ---------------   -------
SERVER01    96.6.27.90         www.microsoft.com {, , }

Hop ReplyRouterAddress
--- ------------------
  1 192.168.0.3

    Status Address      RoundtripTime Options Buffer
    ------ -------      ------------- ------- ------
TtlExpired 192.168.86.1             0         {}
TtlExpired 192.168.86.1             0         {}
TtlExpired 192.168.86.1             0         {}

Hop ReplyRouterAddress
--- ------------------
  2 192.168.1.1

    Status Address     RoundtripTime Options Buffer
    ------ -------     ------------- ------- ------
TtlExpired 192.168.1.1             0         {}
TtlExpired 192.168.1.1             0         {}
TtlExpired 192.168.1.1             0         {}

Hop ReplyRouterAddress
--- ------------------
  3 96.6.27.90

 Status Address    RoundtripTime Options                                   Buffer
 ------ -------    ------------- -------                                   ------
Success 96.6.27.90             3 System.Net.NetworkInformation.PingOptions {97, 98, 99, 100…}
Success 96.6.27.90             2 System.Net.NetworkInformation.PingOptions {97, 98, 99, 100…}
Success 96.6.27.90             4 System.Net.NetworkInformation.PingOptions {97, 98, 99, 100…}
```

De `Test-Connection` opdracht maakt gebruik van de para meter **traceroute** . De resultaten, die `[Microsoft.PowerShell.Commands.TestConnectionCommand+TraceRouteResult]` objecten zijn, worden door gegeven aan de `ForEach-Object` cmdlet. `ForEach-Object` Hiermee maakt u een gestructureerde uitvoer van de Inge sloten `[Microsoft.PowerShell.Commands.TestConnectionCommand+TraceRouteReply]` objecten en de volgende `[System.Net.NetworkInformation.PingReply]` objecten.

## PARAMETERS

### -BufferSize

Hiermee geeft u de grootte, in bytes, van de buffer die met deze opdracht wordt verzonden. De standaard waarde is 32.

```yaml
Type: System.Int32
Parameter Sets: PingCount, PingContinues
Aliases: Size, Bytes, BS

Required: False
Position: Named
Default value: 32
Accept pipeline input: False
Accept wildcard characters: False
```

### -Aantal

Hiermee geeft u het aantal ECHO aanvragen dat moet worden verzonden. De standaardwaarde is 4.

```yaml
Type: System.Int32
Parameter Sets: PingCount
Aliases:

Required: False
Position: Named
Default value: 4
Accept pipeline input: False
Accept wildcard characters: False
```

### -Vertraging

Hiermee geeft u het interval tussen pings op, in seconden.

```yaml
Type: System.Int32
Parameter Sets: PingCount, PingContinues
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DontFragment

Met deze para meter wordt de vlag **don't fragment** in de IP-header ingesteld. U kunt deze para meter met de waarde **BufferSize** gebruiken om de grootte van het pad MTU te testen. Zie het artikel [Path MTU Discovery](https://wikipedia.org/wiki/Path_MTU_Discovery) in Wikipedia voor meer informatie over Path MTU.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PingCount, PingContinues
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -IPv4

Hiermee wordt de cmdlet gedwongen het IPv4-protocol voor de test te gebruiken.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -IPv6

Hiermee wordt de cmdlet gedwongen het IPv6-protocol voor de test te gebruiken.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaxHops

Hiermee stelt u het maximum aantal hops in dat een ICMP-aanvraag bericht kan worden verzonden. De standaard waarde wordt beheerd door het besturings systeem. De standaard waarde voor Windows 10 is 128 hops.

```yaml
Type: System.Int32
Parameter Sets: PingCount, PingContinues, TraceRoute
Aliases: Ttl, TimeToLive, Hops

Required: False
Position: Named
Default value: 128 hops in Windows 10
Accept pipeline input: False
Accept wildcard characters: False
```

### -Ping

Zorgt ervoor dat de cmdlet een ping-test uitvoert. Dit is de standaard actie.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PingCount, PingContinues
Aliases:

Required: False
Position: Named
Default value: Ping test
Accept pipeline input: False
Accept wildcard characters: False
```

### -Quiet

De **stille** para meter retourneert een **Booleaanse** waarde in een object **System. Boolean** . Als u deze para meter gebruikt, worden alle fouten onderdrukt.

Elke geteste verbinding retourneert een **Booleaanse** waarde. Als de **TargetName** -para meter meerdere computers opgeeft, wordt een matrix met **Boole** -waarden geretourneerd.

Als **een** ping slaagt, `$True` wordt geretourneerd.

Als **alle** pings mislukken, `$False` wordt geretourneerd.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -ResolveDestination

Zorgt ervoor dat de cmdlet probeert de DNS-naam van het doel op te lossen.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Source

Hiermee geeft u de namen van de computers waarvan de ping afkomstig is. Voer een door komma's gescheiden lijst met computer namen in. Standaard is dit de lokale computer.

```yaml
Type: System.String
Parameter Sets: PingCount, PingContinues, TraceRoute, ConnectionByTCPPort
Aliases:

Required: False
Position: Named
Default value: Local computer
Accept pipeline input: False
Accept wildcard characters: False
```

### -Doel naam

Hiermee geeft u de computers op die u wilt testen. Typ de computer namen of typ de IP-adressen in de IPv4-of IPv6-indeling. Joker tekens zijn niet toegestaan. Deze parameter is vereist. **ComputerName** is een alias voor deze para meter.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: ComputerName

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -TCPPort

Hiermee geeft u het TCP-poort nummer op het doel dat moet worden gebruikt in de TCP-verbindings test. De cmdlet probeert een TCP-verbinding tot stand te brengen met de opgegeven poort op het doel.

```yaml
Type: System.Int32
Parameter Sets: ConnectionByTCPPort
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TimeoutSeconds

Hiermee stelt u de time-outwaarde voor de test. De test mislukt als er geen antwoord wordt ontvangen voordat de time-out is verstreken. De standaard waarde is vijf seconden.

Deze para meter is geïntroduceerd in Power shell 6,0.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 5 seconds
Accept pipeline input: False
Accept wildcard characters: False
```

### -Traceroute

Zorgt ervoor dat de cmdlet een traceroute-test doet. Als deze para meter wordt gebruikt, retourneert de cmdlet een- `TestConnectionCommand+TraceRouteResult` object.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TraceRoute
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Doorgaat

Zorgt ervoor dat de cmdlet doorlopend ping-aanvragen verzendt. Deze para meter kan niet worden gebruikt met de para meter **Count** .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PingContinues
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MTUSizeDetect

Deze para meter wordt gebruikt om de MTU-grootte van het pad te detecteren. De cmdlet retourneert een **PingReply # MTUSize** -object dat de MTU-grootte van het pad naar het doel bevat. Zie het artikel [Path MTU Discovery](https://wikipedia.org/wiki/Path_MTU_Discovery) in Wikipedia voor meer informatie over Path MTU.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DetectionOfMTUSize
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Geen

U kunt invoer niet naar deze cmdlet pipeen.

## UITVOER

### TestConnectionCommand + PingReport, TestConnectionCommand + TraceRouteResult, Boolean, PingReply # MTUSize

Als u de **stille** para meter opgeeft, wordt een **Booleaanse** waarde geretourneerd. Als er meerdere verbindingen worden getest, wordt een matrix met **Boole** -waarden geretourneerd. Als dat niet het geval is, `Test-Connection` wordt er voor elke ping een **TestConnectionCommand + PingReport** -object geretourneerd.

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Restart-Computer](Restart-Computer.md)

[Stop-computer](Stop-Computer.md)
