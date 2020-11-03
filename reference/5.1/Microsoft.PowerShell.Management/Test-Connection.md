---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/09/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/test-connection?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-Connection
ms.openlocfilehash: a8d3923db69a20cfada58391944b592cf999e6ef
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250527"
---
# Test-Connection

## SAMENVATTING
Verzendt ICMP echo aanvraag pakketten of pings naar een of meer computers.

## SYNTAXIS

### Standaard (standaard instelling)

```
Test-Connection [-AsJob] [-DcomAuthentication <AuthenticationLevel>] [-WsmanAuthentication <String>]
 [-Protocol <String>] [-BufferSize <Int32>] [-ComputerName] <String[]> [-Count <Int32>]
 [-Impersonation <ImpersonationLevel>] [-ThrottleLimit <Int32>] [-TimeToLive <Int32>]
 [-Delay <Int32>] [<CommonParameters>]
```

### Bron

```
Test-Connection [-AsJob] [-DcomAuthentication <AuthenticationLevel>] [-WsmanAuthentication <String>]
 [-Protocol <String>] [-BufferSize <Int32>] [-ComputerName] <String[]> [-Count <Int32>]
 [-Credential <PSCredential>] [-Source] <String[]> [-Impersonation <ImpersonationLevel>]
 [-ThrottleLimit <Int32>] [-TimeToLive <Int32>] [-Delay <Int32>] [<CommonParameters>]
```

### Quiet

```
Test-Connection [-DcomAuthentication <AuthenticationLevel>] [-WsmanAuthentication <String>]
 [-Protocol <String>] [-BufferSize <Int32>] [-ComputerName] <String[]> [-Count <Int32>]
 [-Impersonation <ImpersonationLevel>] [-TimeToLive <Int32>] [-Delay <Int32>] [-Quiet]
 [<CommonParameters>]
```

## BESCHRIJVING

De `Test-Connection` cmdlet stuurt Internet Control Message Protocol (ICMP) Echo aanvraag pakketten of pings naar een of meer externe computers en retourneert de antwoorden op de echo reactie. U kunt deze cmdlet gebruiken om te bepalen of er verbinding kan worden gemaakt met een bepaalde computer via een IP-netwerk.

U kunt de para meters van gebruiken `Test-Connection` om zowel de verzendende als ontvangende computers op te geven om de opdracht als achtergrond taak uit te voeren, om een time-out en een aantal pings in te stellen en om de verbinding en verificatie te configureren.

In tegens telling tot de bekende **ping** -opdracht `Test-Connection` retourneert een **Win32_PingStatus** -object dat u kunt onderzoeken in Power shell. De **stille** para meter retourneert een **Boole** -waarde in een object **System. Boolean** voor elke geteste verbinding. Als er meerdere verbindingen worden getest, wordt een matrix met **Boole** -waarden geretourneerd.

## VOORBEELDEN

### Voor beeld 1: ECHO aanvragen verzenden naar een externe computer

In dit voor beeld worden ECHO aanvraag pakketten van de lokale computer verzonden naar de Server01-computer.

```powershell
Test-Connection -ComputerName Server01
```

```Output
Source        Destination     IPV4Address     IPV6Address  Bytes    Time(ms)
------        -----------     -----------     -----------  -----    --------
ADMIN1        Server01         10.59.137.44                32       0
ADMIN1        Server01         10.59.137.44                32       0
ADMIN1        Server01         10.59.137.44                32       0
ADMIN1        Server01         10.59.137.44                32       1
```

`Test-Connection` maakt gebruik van de para meter **ComputerName** om de Server01-computer op te geven.

### Voor beeld 2: ECHO aanvragen verzenden naar verschillende computers

In dit voor beeld worden pings van de lokale computer naar verschillende externe computers verzonden.

```powershell
Test-Connection -ComputerName Server01, Server02, Server12
```

### Voor beeld 3: ECHO aanvragen van verschillende computers verzenden naar een computer

In dit voor beeld worden pings van verschillende bron computers verzonden naar één externe computer, Server01.

```powershell
Test-Connection -Source Server02, Server12, localhost -ComputerName Server01 -Credential Domain01\Admin01
```

`Test-Connection` maakt gebruik van de para meter **Credential** om de referenties op te geven van een gebruiker die gemachtigd is om een ping-aanvraag van de bron computers te verzenden. Gebruik deze opdracht indeling om de latentie van verbindingen vanaf meerdere punten te testen.

### Voor beeld 4: para meters gebruiken om de test opdracht aan te passen

In dit voor beeld worden de para meters van gebruikt `Test-Connection` voor het aanpassen van de opdracht. De lokale computer verzendt een ping-test naar een externe computer.

```powershell
Test-Connection -ComputerName Server01 -Count 3 -Delay 2 -TTL 255 -BufferSize 256 -ThrottleLimit 32
```

`Test-Connection` maakt gebruik van de para meter **ComputerName** om Server01 op te geven. De para meter **aantal** geeft aan dat drie pings worden verzonden naar de Server01-computer, met een **vertraging** van twee seconden intervallen.

U kunt deze opties gebruiken wanneer het ping-antwoord naar verwachting langer duurt dan normaal, ofwel vanwege een uitgebreid aantal hops of een netwerk toestand met een hoog verkeer.

### Voor beeld 5: een test uitvoeren als een achtergrond taak

In dit voor beeld ziet u hoe u een `Test-Connection` opdracht uitvoert als een Power shell-achtergrond taak.

```powershell
$job = Test-Connection -ComputerName (Get-Content Servers.txt) -AsJob
if ($job.JobStateInfo.State -ne "Running") {$Results = Receive-Job $job}
```

De `Test-Connection` opdracht pingt veel computers in een onderneming. De waarde van de para meter **ComputerName** is een `Get-Content` opdracht die een lijst met computer namen uit de heeft gelezen `Servers.txt file` . De opdracht gebruikt de para meter **AsJob** om de opdracht uit te voeren als een achtergrond taak en de taak wordt opgeslagen in de `$job` variabele.

De `if` opdracht controleert of de taak nog niet wordt uitgevoerd. Als de taak niet wordt uitgevoerd, `Receive-Job` worden de resultaten opgehaald en opgeslagen in de `$Results` variabele.

### Voor beeld 6: een externe computer met referenties pingen

Met deze opdracht wordt de `Test-Connection` cmdlet gebruikt voor het pingen van een externe computer.

```powershell
Test-Connection Server55 -Credential Domain55\User01 -Impersonation Identify
```

De opdracht gebruikt de para meter **Credential** om een gebruikers account op te geven dat is gemachtigd voor het pingen van de externe computer en de **imitatie** parameter om het imitatie niveau te wijzigen in **identificeren**.

### Voor beeld 7: een sessie alleen maken als de verbindings test is geslaagd

In dit voor beeld wordt alleen een sessie op de Server01-computer gemaakt als ten minste één van de pings die naar de computer worden verzonden, slaagt.

```powershell
if (Test-Connection -ComputerName Server01 -Quiet) {New-PSSession Server01}
```

De `if` opdracht gebruikt de `Test-Connection` cmdlet om de Server01-computer te pingen. De opdracht maakt gebruik van de **stille** para meter, waarmee een **Booleaanse** waarde wordt geretourneerd in plaats van een **Win32_PingStatus** -object. De waarde is `$True` als een van de vier pings slaagt en, anders, `$False` .

Als de `Test-Connection` opdracht een waarde retourneert `$True` , gebruikt de opdracht de `New-PSSession` cmdlet om de **PSSession** te maken.

## PARAMETERS

### -AsJob

Geeft aan dat deze cmdlet wordt uitgevoerd als een achtergrond taak.

Als u deze para meter wilt gebruiken, moeten de lokale en externe computers worden geconfigureerd voor externe toegang en, onder Windows Vista en latere versies van het Windows-besturings systeem, moet u Power shell openen met de optie **als administrator uitvoeren** . Zie [about_Remote_Requirements](../microsoft.powershell.core/about/about_remote_requirements.md)voor meer informatie.

Wanneer u de para meter **AsJob** opgeeft, retourneert de opdracht direct een object dat de achtergrond taak vertegenwoordigt. U kunt in de sessie blijven werken terwijl de taak is voltooid. De taak wordt gemaakt op de lokale computer en de resultaten van externe computers worden automatisch geretourneerd naar de lokale computer. Gebruik de cmdlet om de taak resultaten te verkrijgen `Receive-Job` .

Zie [about_Jobs](../Microsoft.PowerShell.Core/About/about_jobs.md) en [about_Remote_Jobs](../Microsoft.PowerShell.Core/About/about_remote_jobs.md)voor meer informatie over Power shell-achtergrond taken.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Default, Source
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -BufferSize

Hiermee geeft u de grootte, in bytes, van de buffer die met deze opdracht wordt verzonden. De standaard waarde is 32.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: Size, Bytes, BS

Required: False
Position: Named
Default value: 32
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

Hiermee geeft u de computers op die moeten worden gepingd. Typ de computer namen of typ de IP-adressen in de IPv4-of IPv6-indeling. Joker tekens zijn niet toegestaan. Deze parameter is vereist.

Deze para meter is niet afhankelijk van externe communicatie met Power shell. U kunt de para meter **ComputerName** ook gebruiken als uw computer niet is geconfigureerd om externe opdrachten uit te voeren.

> [!NOTE]
> De naam van de para meter **ComputerName** wordt gewijzigd in **TargetName** in Power shell 6,0 en hoger.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN, IPAddress, __SERVER, Server, Destination

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Aantal

Hiermee geeft u het aantal ECHO aanvragen dat moet worden verzonden. De standaardwaarde is 4.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 4
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential

Hiermee geeft u een gebruikers account op dat gemachtigd is om een ping-aanvraag van de bron computer te verzenden. Typ een gebruikers naam, zoals gebruiker01 of Domain01\User01, of voer een **PSCredential** -object in, bijvoorbeeld een van de `Get-Credential` cmdlets.

De para meter **Credential** is alleen geldig als de para meter **Source** wordt gebruikt in de opdracht. De referenties hebben geen invloed op de doel computer.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: Source
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### -DcomAuthentication

Hiermee geeft u het verificatie niveau op dat met deze cmdlet wordt gebruikt met WMI.
`Test-Connection` maakt gebruik van WMI.
De aanvaardbare waarden voor deze parameter zijn:

- **Standaard instelling**. Windows-verificatie
- **Geen**. Geen COM-verificatie
- **Verbinding maken**. COM-verificatie op verbindings niveau
- **Aanroep**. COM-verificatie op aanroepen niveau
- **Pakket**. COM-verificatie op pakket niveau
- **PacketIntegrity**. COM-verificatie op pakket integriteit-niveau
- **PacketPrivacy**. COM-verificatie op privacyniveau op pakket niveau
- **Ongewijzigd**. Hetzelfde als de vorige opdracht

De standaard waarde is **pakket** met een opsommings waarde van **4**. Zie [authenticationLevel](/dotnet/api/system.management.authenticationlevel) Enumeration (Engelstalig) voor meer informatie over de waarden van deze para meter.

```yaml
Type: System.Management.AuthenticationLevel
Parameter Sets: (All)
Aliases: Authentication
Accepted values: Default, None, Connect, Call, Packet, PacketIntegrity, PacketPrivacy, Unchanged

Required: False
Position: Named
Default value: Packet (enumerated value of 4)
Accept pipeline input: False
Accept wildcard characters: False
```

### -Vertraging

Hiermee geeft u het interval tussen pings op, in seconden.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 1 (second)
Accept pipeline input: False
Accept wildcard characters: False
```

### -Imitatie

Hiermee geeft u het imitatie niveau op dat moet worden gebruikt wanneer deze cmdlet WMI aanroept. `Test-Connection` maakt gebruik van WMI.

De acceptabele waarden voor deze para meter zijn als volgt:

- **Standaard instelling**. Standaard imitatie.
- **Anoniem**. Hiermee verbergt u de identiteit van de aanroeper.
- **Identificeren**. Hiermee kunnen objecten query's uitvoeren op de referenties van de aanroeper.
- **Imiteren**. Toestaan dat objecten de referenties van de aanroep functie gebruiken.

De standaard waarde is **imiteren**.

```yaml
Type: System.Management.ImpersonationLevel
Parameter Sets: (All)
Aliases:
Accepted values: Default, Anonymous, Identify, Impersonate, Delegate

Required: False
Position: Named
Default value: Impersonate
Accept pipeline input: False
Accept wildcard characters: False
```

### -Protocol

Hiermee geeft u een protocol. De acceptabele waarden voor deze para meter zijn DCOM en WSMan.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: DCOM, WSMan

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Quiet

De **stille** para meter retourneert een **Booleaanse** waarde in een object **System. Boolean** . Als u deze para meter gebruikt, worden alle fouten onderdrukt.

Elke geteste verbinding retourneert een **Booleaanse** waarde. Als de para meter **ComputerName** meerdere computers bevat, wordt een matrix met **Boole** -waarden geretourneerd.

Als **een** ping slaagt, `$True` wordt geretourneerd.

Als **alle** pings mislukken, `$False` wordt geretourneerd.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Quiet
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
Type: System.String[]
Parameter Sets: Source
Aliases: FCN, SRC

Required: True
Position: 1
Default value: Local computer
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit

Hiermee geeft u het maximum aantal gelijktijdige verbindingen op dat tot stand kan worden gebracht om deze opdracht uit te voeren.
Als u deze para meter weglaat of een waarde van 0 invoert, wordt de standaard waarde 32 gebruikt.

De beperkings limiet geldt alleen voor de huidige opdracht, niet voor de sessie of voor de computer.

```yaml
Type: System.Int32
Parameter Sets: Default, Source
Aliases:

Required: False
Position: Named
Default value: 32
Accept pipeline input: False
Accept wildcard characters: False
```

### -TimeToLive

Hiermee geeft u het maximum aantal keren op dat een pakket kan worden doorgestuurd. Voor elke hop in gateways, routers enzovoort. de waarde van **TimeToLive** wordt met één verlaagd. Bij nul wordt het pakket verwijderd en wordt er een fout geretourneerd.
In **Windows** is de standaard waarde **128**. De alias van de para meter **TimeToLive** is **TTL**.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: TTL

Required: False
Position: Named
Default value: 128 in Windows
Accept pipeline input: False
Accept wildcard characters: False
```

### -WsmanAuthentication

Hiermee geeft u het mechanisme op dat wordt gebruikt voor het verifiëren van de gebruikers referenties wanneer deze cmdlet gebruikmaakt van het WSMan-protocol.
De aanvaardbare waarden voor deze parameter zijn:

- Basic
- CredSSP
- Standaard
- Samenvatting
- Kerberos
- Afspraken.

De standaard waarde is standaard.

Zie [AuthenticationMechanism Enumeration (Engelstalig)](/dotnet/api/system.management.automation.runspaces.authenticationmechanism?view=powershellsdk-1.1.0)voor meer informatie over de waarden van deze para meter.

Let op: de verificatie van de Credential Security service provider (CredSSP), waarbij de gebruikers referenties worden door gegeven aan een externe computer die moet worden geverifieerd, is ontworpen voor opdrachten die verificatie vereisen voor meer dan één bron, zoals het openen van een externe netwerk share.
Dit mechanisme verhoogt het beveiligings risico van de externe bewerking.
Als er is geknoeid met de externe computer, kunnen de referenties die aan worden door gegeven, worden gebruikt om de netwerk sessie te beheren.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Default, Basic, Negotiate, CredSSP, Digest, Kerberos

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Geen

U kunt invoer niet naar deze cmdlet pipeen.

## UITVOER

### System. Management. ManagementObject # root\cimv2\ Win32_PingStatus, System. Management. Automation. RemotingJob, System. Boolean

Met deze cmdlet wordt een taak object geretourneerd als u de para meter **AsJob** opgeeft.

Als u de **stille** para meter opgeeft, wordt een **Booleaanse** waarde geretourneerd. Als er meerdere verbindingen worden getest, wordt een matrix met **Boole** -waarden geretourneerd. Anders `Test-Connection` retourneert een **Win32_PingStatus** -object voor elke ping.

## OPMERKINGEN

Deze cmdlet maakt gebruik van de **Win32_PingStatus** -klasse. Een `Get-WMIObject Win32_PingStatus` opdracht is gelijk aan een `Test-Connection` opdracht.

De para meter set van de **bron** is geïntroduceerd in power Shell 3,0.

## GERELATEERDE KOPPELINGEN

[Add-computer](Add-Computer.md)

[Restart-Computer](Restart-Computer.md)

[Stop-computer](Stop-Computer.md)
