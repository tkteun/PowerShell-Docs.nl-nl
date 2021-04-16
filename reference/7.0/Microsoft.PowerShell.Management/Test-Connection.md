---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/test-connection?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-Connection
ms.openlocfilehash: 6a3dfd09d604ae83e1b301d34b565ea9c997dc5b
ms.sourcegitcommit: 366304d096c1caf52f0e17962f6ed23d20f86e7b
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/16/2021
ms.locfileid: "107543850"
---
# Test-Connection

## SAMENVATTING
Verzendt ICMP echoaanvraagpakketten, of pings, naar een of meer computers.

## SYNTAXIS

### DefaultPing (standaard)

```
Test-Connection [-TargetName] <string[]> [-Ping] [-IPv4] [-IPv6] [-ResolveDestination]
 [-Source <string>] [-MaxHops <int>] [-Count <int>] [-Delay <int>] [-BufferSize <int>]
 [-DontFragment] [-TimeoutSeconds <int>] [-Quiet] [<CommonParameters>]
```

### Herhalen

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

### Traceroute

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

De cmdlet verzendt Internet Control Message Protocol echoaanvraagpakketten (ICMP) of pings naar een of meer externe computers en retourneert antwoorden van `Test-Connection` de echoreacties. U kunt deze cmdlet gebruiken om te bepalen of er via een IP-netwerk contact kan worden opgenomen met een bepaalde computer.

U kunt de parameters van gebruiken om zowel de verzendende als ontvangende computers op te geven, de opdracht als achtergrondopdracht uit te voeren, een time-out en aantal pings in te stellen en de verbinding en verificatie `Test-Connection` te configureren.

In tegenstelling tot de **bekende ping** opdracht `Test-Connection` retourneert een **TestConnectionCommand + PingStatus-object** dat u kunt onderzoeken in PowerShell. De **parameter Quiet** retourneert een **Booleaanse** waarde in een **System.Boolean-object** voor elke geteste verbinding. Als meerdere verbindingen worden getest, wordt een matrix met **Booleaanse** waarden geretourneerd.

## VOORBEELDEN

### Voorbeeld 1: Echoaanvragen verzenden naar een externe computer

In dit voorbeeld verzendt echoaanvraagpakketten van de lokale computer naar de computer Server01.

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

`Test-Connection` gebruikt de **TargetName** parameter opgeven voor de Server01-computer. De **IPv4** parameter geeft u het protocol voor de test.

Er wordt een **reeks TestConnectionCommand+PingStatus-objecten** verzonden naar de uitvoerstroom, één object per pingantwoord van de doelmachine.

### Voorbeeld 2: Echoaanvragen verzenden naar verschillende computers

In dit voorbeeld worden pings vanaf de lokale computer naar verschillende externe computers verzendt.

```powershell
Test-Connection -TargetName Server01, Server02, Server12
```

### Voorbeeld 3: Parameters gebruiken om de testopdracht aan te passen

In dit voorbeeld worden de parameters van `Test-Connection` gebruikt om de opdracht aan te passen. De lokale computer verzendt een ping-test naar een externe computer.

```powershell
Test-Connection -TargetName Server01 -Count 3 -Delay 2 -MaxHops 255 -BufferSize 256
```

`Test-Connection` gebruikt de **Parameter TargetName** om Server01 op te geven. De **aantal** parameter geeft u drie pings worden verzonden naar de server01 computer met een **vertraging** van 2 seconden intervallen.

U kunt deze opties gebruiken wanneer het ping-antwoord naar verwachting langer duurt dan normaal, vanwege een uitgebreid aantal hops of een netwerkvoorwaarde met veel verkeer.

### Voorbeeld 4: Een test uitvoeren als achtergrond job

In dit voorbeeld ziet u hoe u een opdracht `Test-Connection` kunt uitvoeren als een PowerShell-achtergrondopdracht.

```powershell
$job = Start-Job -ScriptBlock { Test-Connection -TargetName (Get-Content -Path "Servers.txt") }
$Results = Receive-Job $job -Wait
```

De `Start-Job` opdracht gebruikt de `Test-Connection` cmdlet om veel computers in een onderneming te pingen.
De waarde van de **TargetName** parameter is een opdracht die een lijst met `Get-Content` computernamen uit het bestand `Servers.txt` leest. De opdracht gebruikt de cmdlet om de opdracht uit te voeren als achtergrond job en slaat `Start-Job` de taak op in de variabele `$job` .

De `Receive-Job` opdracht wordt geïnstrueerd tot de taak is voltooid, waarna de resultaten worden op halen `-Wait` en in de variabele worden op `$Results` slaat.

### Voorbeeld 5: alleen een sessie maken als een verbindingstest is geslaagd

In dit voorbeeld maakt u een sessie op de server01-computer alleen als ten minste één van de pings naar de computer slaagt.

```powershell
if (Test-Connection -TargetName Server01 -Quiet) { New-PSSession -ComputerName Server01 }
```

De `Test-Connection` cmdlet pingt de `Server01` computer met de parameter **Quiet** opgegeven.
De resulterende waarde is `$True` als een van de vier pings slaagt. Als geen van de pings slaagt, is de waarde `$False` .

Als de `Test-Connection` opdracht een waarde van retourneert, gebruikt de opdracht de `$True` `New-PSSession` cmdlet om de **PSSession te maken.**

### Voorbeeld 6: De parameter Traceroute gebruiken

De parameter **Traceroute,** geïntroduceerd in PowerShell 6.0, brengt een route toe tussen de lokale computer en de externe bestemming die u opgeeft met de parameter **TargetName.**

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

De `Test-Connection` opdracht wordt aangeroepen met de parameter **Traceroute.** De resultaten, die objecten `[Microsoft.PowerShell.Commands.TestConnectionCommand+TraceStatus]` zijn, worden uitgevoerd naar de **uitvoerstroom Geslaagd.**

## PARAMETERS

### -BufferSize

Hiermee geeft u de grootte, in bytes, van de buffer verzonden met deze opdracht. De standaardwaarde is 32.

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

### -Herhalen

Zorgt ervoor dat de cmdlet continu ping-aanvragen verzendt. Deze parameter kan niet worden gebruikt met de parameter **Count.**

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

Hiermee geeft u het aantal echoaanvragen te verzenden. De standaardwaarde is 4.

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

Hiermee geeft u het interval tussen pings, in seconden.

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

Met deze parameter stelt u **de vlag Niet fragment in** de IP-header in. U kunt deze parameter gebruiken met de **parameter BufferSize** om de MTU-grootte van het pad te testen. Zie het artikel Path MTU Discovery (MTU-detectiepad) op Wikipedia voor meer informatie over Path [MTU.](https://wikipedia.org/wiki/Path_MTU_Discovery)

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

Dwingt de cmdlet om het IPv4-protocol voor de test te gebruiken.

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

Dwingt de cmdlet om het IPv6-protocol voor de test te gebruiken.

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

Hiermee stelt u het maximum aantal hops in dat een ICMP-aanvraagbericht kan worden verzonden. De standaardwaarde wordt bepaald door het besturingssysteem. De standaardwaarde voor Windows 10 is 128 hops.

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

Zorgt ervoor dat de cmdlet een ping-test uitvoeren. Dit is de standaardmodus voor de `Test-Connection` cmdlet.

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

De **parameter Quiet** retourneert een **Booleaanse** waarde. Met deze parameter worden alle fouten onderdrukt.

Elke geteste verbinding retourneert een **Booleaanse** waarde. Als de **parameter TargetName** meerdere computers opgeeft, wordt een matrix met **Booleaanse** waarden geretourneerd.

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

Zorgt ervoor dat de cmdlet probeert om te lossen van de DNS-naam van het doel. Wanneer u deze gebruikt in combinatie met de parameter **Traceroute,** worden indien mogelijk ook de DNS-namen van alle tussenliggende hosts opgehaald.

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

Hiermee geeft u de namen van de computers waar de ping afkomstig is. Voer een door komma's gescheiden lijst met computernamen in. Standaard is dit de lokale computer.

> [!NOTE]
> Deze parameter wordt niet ondersteund in PowerShell versie 6 en nieuwe versies. Het opgeven van deze parameter veroorzaakt een fout.

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

### -TargetName

Hiermee geeft u de computer(s) te testen. Typ de computernamen of ip-adressen in IPv4- of IPv6-indeling.

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

Hiermee stelt u de time-outwaarde voor de test in. De test mislukt als er geen antwoord wordt ontvangen voordat de time-out verloopt. De standaardwaarde is vijf seconden.

Deze parameter is geïntroduceerd in PowerShell 6.0.

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

Zorgt ervoor dat de cmdlet een traceroute-test moet uitvoeren. Wanneer deze parameter wordt gebruikt, retourneert de cmdlet een `TestConnectionCommand+TraceStatus` -object.

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

Deze parameter wordt gebruikt om de MTU-grootte van het pad te ontdekken. De cmdlet retourneert een **PingReply#MTUSize-object** dat de MTU-padgrootte naar het doel bevat. Zie het artikel Path MTU Discovery (MTU-detectiepad) op Wikipedia voor meer informatie over Path [MTU.](https://wikipedia.org/wiki/Path_MTU_Discovery)

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

Hiermee geeft u het TCP-poortnummer op het doel dat moet worden gebruikt in de TCP-verbindingstest. De cmdlet probeert een TCP-verbinding te maken met de opgegeven poort op het doel.

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

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie voor meer informatie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INVOER

### Geen

U kunt geen invoer doorspijpen naar deze cmdlet.

## UITVOER

### TestConnectionCommand+PingStatus, TestConnectionCommand+TraceStatus, Boolean, TestConnectionCommand+PingMtuStatus

Retourneert `Test-Connection` standaard een **TestConnectionCommand +PingStatus-object** voor elk pingantwoord.

Als u de **parameter Traceroute opgeeft,** retourneert de cmdlet een **TestConnectionCommand+TraceStatus-object** voor elk pingantwoord langs de route.

Als u de **parameters Quiet** of **TcpPort opgeeft,** wordt een **Booleaanse waarde** retourneert. Als meerdere verbindingen worden getest, wordt een matrix met **Booleaanse** waarden geretourneerd.

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Restart-Computer](Restart-Computer.md)

[Stop-Computer](Stop-Computer.md)
