---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/test-connection?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-Connection
ms.openlocfilehash: 6a03d5a644e3d4be515a93a702d0ef0aff23a8d7
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93249998"
---
# Test-Connection

## SAMENVATTING
Verzendt ICMP echo aanvraag pakketten of pings naar een of meer computers.

## SYNTAXIS

### DefaultPing (standaard)

```
Test-Connection [-TargetName] <string[]> [-Ping] [-IPv4] [-IPv6] [-ResolveDestination]
 [-Source <string>] [-MaxHops <int>] [-Count <int>] [-Delay <int>] [-BufferSize <int>]
 [-DontFragment] [-TimeoutSeconds <int>] [-Quiet] [<CommonParameters>]
```

### RepeatPing

```
Test-Connection [-TargetName] <string[]> -Repeat [-Ping] [-IPv4] [-IPv6] [-ResolveDestination]
 [-Source <string>] [-MaxHops <int>] [-Delay <int>] [-BufferSize <int>] [-DontFragment]
 [-TimeoutSeconds <int>] [-Quiet] [<CommonParameters>]
```

### MtuSizeDetect

```
Test-Connection [-TargetName] <string[]> -MtuSize [-IPv4] [-IPv6] [-ResolveDestination]
 [-TimeoutSeconds <int>] [-Quiet] [<CommonParameters>]
```

### TraceRoute

```
Test-Connection [-TargetName] <string[]> -Traceroute [-IPv4] [-IPv6] [-ResolveDestination]
 [-Source <string>] [-MaxHops <int>] [-TimeoutSeconds <int>] [-Quiet] [<CommonParameters>]
```

### TcpPort

```
Test-Connection [-TargetName] <string[]> -TcpPort <int> [-IPv4] [-IPv6] [-ResolveDestination]
 [-Source <string>] [-TimeoutSeconds <int>] [-Quiet] [<CommonParameters>]
```

## BESCHRIJVING

De `Test-Connection` cmdlet stuurt Internet Control Message Protocol (ICMP) Echo aanvraag pakketten of pings naar een of meer externe computers en retourneert de antwoorden op de echo reactie. U kunt deze cmdlet gebruiken om te bepalen of er verbinding kan worden gemaakt met een bepaalde computer via een IP-netwerk.

U kunt de para meters van gebruiken `Test-Connection` om zowel de verzendende als ontvangende computers op te geven om de opdracht als achtergrond taak uit te voeren, om een time-out en een aantal pings in te stellen en om de verbinding en verificatie te configureren.

In tegens telling tot de bekende **ping** -opdracht `Test-Connection` retourneert een **TestConnectionCommand + PingStatus** -object dat u kunt onderzoeken in Power shell. De **stille** para meter retourneert een **Boole** -waarde in een object **System. Boolean** voor elke geteste verbinding. Als er meerdere verbindingen worden getest, wordt een matrix met **Boole** -waarden geretourneerd.

## VOORBEELDEN

### Voor beeld 1: ECHO aanvragen verzenden naar een externe computer

In dit voor beeld worden ECHO aanvraag pakketten van de lokale computer verzonden naar de Server01-computer.

```powershell
Test-Connection -TargetName Server01 -IPv4
```

```Output
   Destination: Server01

Ping Source           Address                   Latency BufferSize Status
                                                   (ms)        (B)
---- ------           -------                   ------- ---------- ------
   1 ADMIN1           10.59.137.44                   24         32 Success
   2 ADMIN1           10.59.137.44                   39         32 Success
   3 ADMIN1           *                               *          * TimedOut
   4 ADMIN1           10.59.137.44                   28         32 Success
```

`Test-Connection` maakt gebruik van de **TargetName** -para meter om de Server01-computer op te geven. De **IPv4** -para meter geeft u het protocol voor de test op.

Er wordt een reeks TestConnectionCommand-en **PingStatus** -objecten verzonden naar de uitvoer stroom, één object per ping-antwoord van de doel computer.

### Voor beeld 2: ECHO aanvragen verzenden naar verschillende computers

In dit voor beeld worden pings van de lokale computer naar verschillende externe computers verzonden.

```powershell
Test-Connection -TargetName Server01, Server02, Server12
```

### Voor beeld 3: para meters gebruiken voor het aanpassen van de test opdracht

In dit voor beeld worden de para meters van gebruikt `Test-Connection` voor het aanpassen van de opdracht. De lokale computer verzendt een ping-test naar een externe computer.

```powershell
Test-Connection -TargetName Server01 -Count 3 -Delay 2 -MaxHops 255 -BufferSize 256
```

`Test-Connection` maakt gebruik van de para meter **TargetName** om Server01 op te geven. De para meter **aantal** geeft aan dat drie pings worden verzonden naar de Server01-computer, met een **vertraging** van twee seconden intervallen.

U kunt deze opties gebruiken wanneer het ping-antwoord naar verwachting langer duurt dan normaal, ofwel vanwege een uitgebreid aantal hops of een netwerk toestand met een hoog verkeer.

### Voor beeld 4: een test uitvoeren als een achtergrond taak

In dit voor beeld ziet u hoe u een `Test-Connection` opdracht uitvoert als een Power shell-achtergrond taak.

```powershell
$job = Start-Job -ScriptBlock { Test-Connection -TargetName (Get-Content -Path "Servers.txt") }
$Results = Receive-Job $job -Wait
```

De `Start-Job` opdracht gebruikt de `Test-Connection` cmdlet voor het pingen van veel computers in een onderneming.
De waarde van de **TargetName** -para meter is een `Get-Content` opdracht waarmee een lijst met computer namen uit het `Servers.txt` bestand wordt gelezen. De opdracht gebruikt de `Start-Job` cmdlet om de opdracht uit te voeren als een achtergrond taak en de taak wordt opgeslagen in de `$job` variabele.

De `Receive-Job` opdracht wordt geïnstrueerd `-Wait` totdat de taak is voltooid, waarna de resultaten worden opgehaald en opgeslagen in de `$Results` variabele.

### Voor beeld 5: een sessie alleen maken als de verbindings test is geslaagd

In dit voor beeld wordt alleen een sessie op de Server01-computer gemaakt als ten minste één van de pings die naar de computer worden verzonden, slaagt.

```powershell
if (Test-Connection -TargetName Server01 -Quiet) { New-PSSession -ComputerName Server01 }
```

De `Test-Connection` cmdlet pingt de `Server01` computer, waarbij de **stille** para meter wordt gegeven.
De resulterende waarde is `$True` als een van de vier pings slaagt. Als geen van de pings slaagt, is de waarde `$False` .

Als de `Test-Connection` opdracht een waarde retourneert `$True` , gebruikt de opdracht de `New-PSSession` cmdlet om de **PSSession** te maken.

### Voor beeld 6: de para meter traceroute gebruiken

De **traceroute** -para meter is geïntroduceerd in power shell 6,0 en wijst een route toe tussen de lokale computer en de externe bestemming die u opgeeft met de para meter **TargetName** .

```powershell
Test-Connection -TargetName www.google.com -Traceroute
```

```Output
   Target: google.com

Hop Hostname                  Ping Latency Status           Source       TargetAddress
                                      (ms)
--- --------                  ---- ------- ------           ------       -------------
  1 172.20.0.1                   1       4 Success          Lira         172.217.9.174
  1 172.20.0.1                   2       3 Success          Lira         172.217.9.174
  1 172.20.0.1                   3       2 Success          Lira         172.217.9.174
  2 12.108.153.193               1       3 Success          Lira         172.217.9.174
  2 12.108.153.193               2       3 Success          Lira         172.217.9.174
  2 12.108.153.193               3       2 Success          Lira         172.217.9.174
  3 12.244.85.177                1      11 Success          Lira         172.217.9.174
  3 12.244.85.177                2      12 Success          Lira         172.217.9.174
  3 12.244.85.177                3      12 Success          Lira         172.217.9.174
  4 *                            1      14 DestinationNetw… Lira         172.217.9.174
  4 *                            2       * TimedOut         Lira         172.217.9.174
  4 *                            3      20 DestinationNetw… Lira         172.217.9.174
  5 *                            1       * TimedOut         Lira         172.217.9.174
  5 *                            2      15 DestinationNetw… Lira         172.217.9.174
  5 *                            3       * TimedOut         Lira         172.217.9.174
  6 *                            1      18 DestinationNetw… Lira         172.217.9.174
  6 *                            2       * TimedOut         Lira         172.217.9.174
  6 *                            3      16 DestinationNetw… Lira         172.217.9.174
  7 *                            1       * TimedOut         Lira         172.217.9.174
  7 *                            2       * TimedOut         Lira         172.217.9.174
  7 *                            3       * TimedOut         Lira         172.217.9.174
  8 *                            1       * TimedOut         Lira         172.217.9.174
  8 *                            2       * TimedOut         Lira         172.217.9.174
  8 *                            3       * TimedOut         Lira         172.217.9.174
  9 *                            1       * TimedOut         Lira         172.217.9.174
  9 *                            2       * TimedOut         Lira         172.217.9.174
  9 *                            3       * TimedOut         Lira         172.217.9.174
 10 *                            1       * TimedOut         Lira         172.217.9.174
 10 *                            2       * TimedOut         Lira         172.217.9.174
 10 *                            3       * TimedOut         Lira         172.217.9.174
 11 172.217.9.174                1      23 Success          Lira         172.217.9.174
 11 172.217.9.174                2      21 Success          Lira         172.217.9.174
 11 172.217.9.174                3      22 Success          Lira         172.217.9.174
```

De `Test-Connection` opdracht wordt aangeroepen met de para meter **traceroute** . De resultaten, die `[Microsoft.PowerShell.Commands.TestConnectionCommand+TraceStatus]` objecten zijn, worden uitgevoerd naar de uitvoer stroom **geslaagd** .

## PARAMETERS

### -BufferSize

Hiermee geeft u de grootte, in bytes, van de buffer die met deze opdracht wordt verzonden. De standaard waarde is 32.

```yaml
Type: System.Int32
Parameter Sets: DefaultPing, RepeatPing
Aliases: Size, Bytes, BS

Required: False
Position: Named
Default value: 32
Accept pipeline input: False
Accept wildcard characters: False
```

### -REPEAT

Zorgt ervoor dat de cmdlet doorlopend ping-aanvragen verzendt. Deze para meter kan niet worden gebruikt met de para meter **Count** .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: RepeatPing
Aliases: Continuous

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Aantal

Hiermee geeft u het aantal ECHO aanvragen dat moet worden verzonden. De standaardwaarde is 4.

```yaml
Type: System.Int32
Parameter Sets: DefaultPing
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
Parameter Sets: DefaultPing, RepeatPing
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
Parameter Sets: DefaultPing, RepeatPing
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
Parameter Sets: DefaultPing, RepeatPing, TraceRoute
Aliases: Ttl, TimeToLive, Hops

Required: False
Position: Named
Default value: 128 hops in Windows 10
Accept pipeline input: False
Accept wildcard characters: False
```

### -Ping

Zorgt ervoor dat de cmdlet een ping-test doet. Dit is de standaard modus voor de `Test-Connection` cmdlet.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DefaultPing, RepeatPing
Aliases:

Required: False
Position: Named
Default value: True
Accept pipeline input: False
Accept wildcard characters: False
```

### -Quiet

De **stille** para meter retourneert een **Booleaanse** waarde. Als u deze para meter gebruikt, worden alle fouten onderdrukt.

Elke geteste verbinding retourneert een **Booleaanse** waarde. Als de **TargetName** -para meter meerdere computers opgeeft, wordt een matrix met **Boole** -waarden geretourneerd.

Als **een** ping naar een bepaald doel slaagt, `$True` wordt geretourneerd.

Als **alle** pings naar een bepaald doel mislukken, `$False` wordt geretourneerd.

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

Zorgt ervoor dat de cmdlet probeert de DNS-naam van het doel op te lossen. Bij gebruik in combi natie met de para meter **traceroute** worden ook de DNS-namen van alle tussenliggende hosts opgehaald, indien mogelijk.

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

**Opmerking:** Deze para meter is niet functioneel in Power shell versie 6 en hoger.
Het opgeven van deze para meter heeft geen effect op de opdracht.

```yaml
Type: System.String
Parameter Sets: DefaultPing, RepeatPing, TraceRoute, TcpPort
Aliases:

Required: False
Position: Named
Default value: Local computer
Accept pipeline input: False
Accept wildcard characters: False
```

### -Doel naam

Hiermee geeft u de computer (s) op die u wilt testen. Typ de computer namen of typ de IP-adressen in de IPv4-of IPv6-indeling.

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

Zorgt ervoor dat de cmdlet een traceroute-test doet. Als deze para meter wordt gebruikt, retourneert de cmdlet een- `TestConnectionCommand+TraceStatus` object.

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

### -MtuSize

Deze para meter wordt gebruikt om de MTU-grootte van het pad te detecteren. De cmdlet retourneert een **PingReply # MTUSize** -object dat de MTU-grootte van het pad naar het doel bevat. Zie het artikel [Path MTU Discovery](https://wikipedia.org/wiki/Path_MTU_Discovery) in Wikipedia voor meer informatie over Path MTU.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: MtuSizeDetect
Aliases: MtuSizeDetect

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -TcpPort

Hiermee geeft u het TCP-poort nummer op het doel dat moet worden gebruikt in de TCP-verbindings test. De cmdlet probeert een TCP-verbinding tot stand te brengen met de opgegeven poort op het doel.

Als er een verbinding kan worden gemaakt, `$True` wordt geretourneerd.

Als er geen verbinding kan worden gemaakt, `$False` wordt geretourneerd.

```yaml
Type: System.Int32
Parameter Sets: TcpPort
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Geen

U kunt invoer niet naar deze cmdlet pipeen.

## UITVOER

### TestConnectionCommand + PingStatus, TestConnectionCommand + TraceStatus, Boolean, TestConnectionCommand + PingMtuStatus

`Test-Connection`Retourneert standaard een **TestConnectionCommand + PingStatus** -object voor elk ping-antwoord.

Als u de para meter **traceroute** opgeeft, retourneert de cmdlet een **TestConnectionCommand + TraceStatus** -object voor elk ping-antwoord op de route.

Als u de para meters **quiet** of **TcpPort** opgeeft, wordt een **Booleaanse** waarde geretourneerd. Als er meerdere verbindingen worden getest, wordt een matrix met **Boole** -waarden geretourneerd.

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Restart-Computer](Restart-Computer.md)

[Stop-computer](Stop-Computer.md)

