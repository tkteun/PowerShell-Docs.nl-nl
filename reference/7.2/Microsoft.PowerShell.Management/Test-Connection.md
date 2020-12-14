---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/test-connection?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-Connection
ms.openlocfilehash: af8a953536bb9683ba737522ad738348c5c695e2
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705948"
---
# <span data-ttu-id="15631-102">Test-Connection</span><span class="sxs-lookup"><span data-stu-id="15631-102">Test-Connection</span></span>

## <span data-ttu-id="15631-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="15631-103">SYNOPSIS</span></span>
<span data-ttu-id="15631-104">Verzendt ICMP echo aanvraag pakketten of pings naar een of meer computers.</span><span class="sxs-lookup"><span data-stu-id="15631-104">Sends ICMP echo request packets, or pings, to one or more computers.</span></span>

## <span data-ttu-id="15631-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="15631-105">SYNTAX</span></span>

### <span data-ttu-id="15631-106">DefaultPing (standaard)</span><span class="sxs-lookup"><span data-stu-id="15631-106">DefaultPing (Default)</span></span>

```
Test-Connection [-TargetName] <string[]> [-Ping] [-IPv4] [-IPv6] [-ResolveDestination]
 [-Source <string>] [-MaxHops <int>] [-Count <int>] [-Delay <int>] [-BufferSize <int>]
 [-DontFragment] [-TimeoutSeconds <int>] [-Quiet] [<CommonParameters>]
```

### <span data-ttu-id="15631-107">RepeatPing</span><span class="sxs-lookup"><span data-stu-id="15631-107">RepeatPing</span></span>

```
Test-Connection [-TargetName] <string[]> -Repeat [-Ping] [-IPv4] [-IPv6] [-ResolveDestination]
 [-Source <string>] [-MaxHops <int>] [-Delay <int>] [-BufferSize <int>] [-DontFragment]
 [-TimeoutSeconds <int>] [-Quiet] [<CommonParameters>]
```

### <span data-ttu-id="15631-108">MtuSizeDetect</span><span class="sxs-lookup"><span data-stu-id="15631-108">MtuSizeDetect</span></span>

```
Test-Connection [-TargetName] <string[]> -MtuSize [-IPv4] [-IPv6] [-ResolveDestination]
 [-TimeoutSeconds <int>] [-Quiet] [<CommonParameters>]
```

### <span data-ttu-id="15631-109">TraceRoute</span><span class="sxs-lookup"><span data-stu-id="15631-109">TraceRoute</span></span>

```
Test-Connection [-TargetName] <string[]> -Traceroute [-IPv4] [-IPv6] [-ResolveDestination]
 [-Source <string>] [-MaxHops <int>] [-TimeoutSeconds <int>] [-Quiet] [<CommonParameters>]
```

### <span data-ttu-id="15631-110">TcpPort</span><span class="sxs-lookup"><span data-stu-id="15631-110">TcpPort</span></span>

```
Test-Connection [-TargetName] <string[]> -TcpPort <int> [-IPv4] [-IPv6] [-ResolveDestination]
 [-Source <string>] [-TimeoutSeconds <int>] [-Quiet] [<CommonParameters>]
```

## <span data-ttu-id="15631-111">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="15631-111">DESCRIPTION</span></span>

<span data-ttu-id="15631-112">De `Test-Connection` cmdlet stuurt Internet Control Message Protocol (ICMP) Echo aanvraag pakketten of pings naar een of meer externe computers en retourneert de antwoorden op de echo reactie.</span><span class="sxs-lookup"><span data-stu-id="15631-112">The `Test-Connection` cmdlet sends Internet Control Message Protocol (ICMP) echo request packets, or pings, to one or more remote computers and returns the echo response replies.</span></span> <span data-ttu-id="15631-113">U kunt deze cmdlet gebruiken om te bepalen of er verbinding kan worden gemaakt met een bepaalde computer via een IP-netwerk.</span><span class="sxs-lookup"><span data-stu-id="15631-113">You can use this cmdlet to determine whether a particular computer can be contacted across an IP network.</span></span>

<span data-ttu-id="15631-114">U kunt de para meters van gebruiken `Test-Connection` om zowel de verzendende als ontvangende computers op te geven om de opdracht als achtergrond taak uit te voeren, om een time-out en een aantal pings in te stellen en om de verbinding en verificatie te configureren.</span><span class="sxs-lookup"><span data-stu-id="15631-114">You can use the parameters of `Test-Connection` to specify both the sending and receiving computers, to run the command as a background job, to set a time-out and number of pings, and to configure the connection and authentication.</span></span>

<span data-ttu-id="15631-115">In tegens telling tot de bekende **ping** -opdracht `Test-Connection` retourneert een **TestConnectionCommand + PingStatus** -object dat u kunt onderzoeken in Power shell.</span><span class="sxs-lookup"><span data-stu-id="15631-115">Unlike the familiar **ping** command, `Test-Connection` returns a **TestConnectionCommand+PingStatus** object that you can investigate in PowerShell.</span></span> <span data-ttu-id="15631-116">De **stille** para meter retourneert een **Boole** -waarde in een object **System. Boolean** voor elke geteste verbinding.</span><span class="sxs-lookup"><span data-stu-id="15631-116">The **Quiet** parameter returns a **Boolean** value in a **System.Boolean** object for each tested connection.</span></span> <span data-ttu-id="15631-117">Als er meerdere verbindingen worden getest, wordt een matrix met **Boole** -waarden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="15631-117">If multiple connections are tested, an array of **Boolean** values is returned.</span></span>

## <span data-ttu-id="15631-118">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="15631-118">EXAMPLES</span></span>

### <span data-ttu-id="15631-119">Voor beeld 1: ECHO aanvragen verzenden naar een externe computer</span><span class="sxs-lookup"><span data-stu-id="15631-119">Example 1: Send echo requests to a remote computer</span></span>

<span data-ttu-id="15631-120">In dit voor beeld worden ECHO aanvraag pakketten van de lokale computer verzonden naar de Server01-computer.</span><span class="sxs-lookup"><span data-stu-id="15631-120">This example sends echo request packets from the local computer to the Server01 computer.</span></span>

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

<span data-ttu-id="15631-121">`Test-Connection` maakt gebruik van de **TargetName** -para meter om de Server01-computer op te geven.</span><span class="sxs-lookup"><span data-stu-id="15631-121">`Test-Connection` uses the **TargetName** parameter to specify the Server01 computer.</span></span> <span data-ttu-id="15631-122">De **IPv4** -para meter geeft u het protocol voor de test op.</span><span class="sxs-lookup"><span data-stu-id="15631-122">The **IPv4** parameter specifies the protocol for the test.</span></span>

<span data-ttu-id="15631-123">Er wordt een reeks TestConnectionCommand-en **PingStatus** -objecten verzonden naar de uitvoer stroom, één object per ping-antwoord van de doel computer.</span><span class="sxs-lookup"><span data-stu-id="15631-123">A series of **TestConnectionCommand+PingStatus** objects are sent to the output stream, one object per ping reply from the target machine.</span></span>

### <span data-ttu-id="15631-124">Voor beeld 2: ECHO aanvragen verzenden naar verschillende computers</span><span class="sxs-lookup"><span data-stu-id="15631-124">Example 2: Send echo requests to several computers</span></span>

<span data-ttu-id="15631-125">In dit voor beeld worden pings van de lokale computer naar verschillende externe computers verzonden.</span><span class="sxs-lookup"><span data-stu-id="15631-125">This example sends pings from the local computer to several remote computers.</span></span>

```powershell
Test-Connection -TargetName Server01, Server02, Server12
```

### <span data-ttu-id="15631-126">Voor beeld 3: para meters gebruiken voor het aanpassen van de test opdracht</span><span class="sxs-lookup"><span data-stu-id="15631-126">Example 3: Use parameters to customize the test command</span></span>

<span data-ttu-id="15631-127">In dit voor beeld worden de para meters van gebruikt `Test-Connection` voor het aanpassen van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="15631-127">This example uses the parameters of `Test-Connection` to customize the command.</span></span> <span data-ttu-id="15631-128">De lokale computer verzendt een ping-test naar een externe computer.</span><span class="sxs-lookup"><span data-stu-id="15631-128">The local computer sends a ping test to a remote computer.</span></span>

```powershell
Test-Connection -TargetName Server01 -Count 3 -Delay 2 -MaxHops 255 -BufferSize 256
```

<span data-ttu-id="15631-129">`Test-Connection` maakt gebruik van de para meter **TargetName** om Server01 op te geven.</span><span class="sxs-lookup"><span data-stu-id="15631-129">`Test-Connection` uses the **TargetName** parameter to specify Server01.</span></span> <span data-ttu-id="15631-130">De para meter **aantal** geeft aan dat drie pings worden verzonden naar de Server01-computer, met een **vertraging** van twee seconden intervallen.</span><span class="sxs-lookup"><span data-stu-id="15631-130">The **Count** parameter specifies three pings are sent to the Server01 computer with a **Delay** of 2-second intervals.</span></span>

<span data-ttu-id="15631-131">U kunt deze opties gebruiken wanneer het ping-antwoord naar verwachting langer duurt dan normaal, ofwel vanwege een uitgebreid aantal hops of een netwerk toestand met een hoog verkeer.</span><span class="sxs-lookup"><span data-stu-id="15631-131">You might use these options when the ping response is expected to take longer than usual, either because of an extended number of hops or a high-traffic network condition.</span></span>

### <span data-ttu-id="15631-132">Voor beeld 4: een test uitvoeren als een achtergrond taak</span><span class="sxs-lookup"><span data-stu-id="15631-132">Example 4: Run a test as a background job</span></span>

<span data-ttu-id="15631-133">In dit voor beeld ziet u hoe u een `Test-Connection` opdracht uitvoert als een Power shell-achtergrond taak.</span><span class="sxs-lookup"><span data-stu-id="15631-133">This example shows how to run a `Test-Connection` command as a PowerShell background job.</span></span>

```powershell
$job = Start-Job -ScriptBlock { Test-Connection -TargetName (Get-Content -Path "Servers.txt") }
$Results = Receive-Job $job -Wait
```

<span data-ttu-id="15631-134">De `Start-Job` opdracht gebruikt de `Test-Connection` cmdlet voor het pingen van veel computers in een onderneming.</span><span class="sxs-lookup"><span data-stu-id="15631-134">The `Start-Job` command uses the `Test-Connection` cmdlet to ping many computers in an enterprise.</span></span>
<span data-ttu-id="15631-135">De waarde van de **TargetName** -para meter is een `Get-Content` opdracht waarmee een lijst met computer namen uit het `Servers.txt` bestand wordt gelezen.</span><span class="sxs-lookup"><span data-stu-id="15631-135">The value of the **TargetName** parameter is a `Get-Content` command that reads a list of computer names from the `Servers.txt` file.</span></span> <span data-ttu-id="15631-136">De opdracht gebruikt de `Start-Job` cmdlet om de opdracht uit te voeren als een achtergrond taak en de taak wordt opgeslagen in de `$job` variabele.</span><span class="sxs-lookup"><span data-stu-id="15631-136">The command uses the `Start-Job` cmdlet to run the command as a background job and it saves the job in the `$job` variable.</span></span>

<span data-ttu-id="15631-137">De `Receive-Job` opdracht wordt geïnstrueerd `-Wait` totdat de taak is voltooid, waarna de resultaten worden opgehaald en opgeslagen in de `$Results` variabele.</span><span class="sxs-lookup"><span data-stu-id="15631-137">The `Receive-Job` command is instructed to `-Wait` until the job is completed, and then gets the results and stores them in the `$Results` variable.</span></span>

### <span data-ttu-id="15631-138">Voor beeld 5: een sessie alleen maken als de verbindings test is geslaagd</span><span class="sxs-lookup"><span data-stu-id="15631-138">Example 5: Create a session only if a connection test succeeds</span></span>

<span data-ttu-id="15631-139">In dit voor beeld wordt alleen een sessie op de Server01-computer gemaakt als ten minste één van de pings die naar de computer worden verzonden, slaagt.</span><span class="sxs-lookup"><span data-stu-id="15631-139">This example creates a session on the Server01 computer only if at least one of the pings sent to the computer succeeds.</span></span>

```powershell
if (Test-Connection -TargetName Server01 -Quiet) { New-PSSession -ComputerName Server01 }
```

<span data-ttu-id="15631-140">De `Test-Connection` cmdlet pingt de `Server01` computer, waarbij de **stille** para meter wordt gegeven.</span><span class="sxs-lookup"><span data-stu-id="15631-140">The `Test-Connection` cmdlet pings the `Server01` computer, with the **Quiet** parameter provided.</span></span>
<span data-ttu-id="15631-141">De resulterende waarde is `$True` als een van de vier pings slaagt.</span><span class="sxs-lookup"><span data-stu-id="15631-141">The resulting value is `$True` if any of the four pings succeed.</span></span> <span data-ttu-id="15631-142">Als geen van de pings slaagt, is de waarde `$False` .</span><span class="sxs-lookup"><span data-stu-id="15631-142">If none of the pings succeed, the value is `$False`.</span></span>

<span data-ttu-id="15631-143">Als de `Test-Connection` opdracht een waarde retourneert `$True` , gebruikt de opdracht de `New-PSSession` cmdlet om de **PSSession** te maken.</span><span class="sxs-lookup"><span data-stu-id="15631-143">If the `Test-Connection` command returns a value of `$True`, the command uses the `New-PSSession` cmdlet to create the **PSSession**.</span></span>

### <span data-ttu-id="15631-144">Voor beeld 6: de para meter traceroute gebruiken</span><span class="sxs-lookup"><span data-stu-id="15631-144">Example 6: Use the Traceroute parameter</span></span>

<span data-ttu-id="15631-145">De **traceroute** -para meter is geïntroduceerd in power shell 6,0 en wijst een route toe tussen de lokale computer en de externe bestemming die u opgeeft met de para meter **TargetName** .</span><span class="sxs-lookup"><span data-stu-id="15631-145">Introduced in PowerShell 6.0, the **Traceroute** parameter maps a route between the local computer and the remote destination you specify with the **TargetName** parameter.</span></span>

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

<span data-ttu-id="15631-146">De `Test-Connection` opdracht wordt aangeroepen met de para meter **traceroute** .</span><span class="sxs-lookup"><span data-stu-id="15631-146">The `Test-Connection` command is called with the **Traceroute** parameter.</span></span> <span data-ttu-id="15631-147">De resultaten, die `[Microsoft.PowerShell.Commands.TestConnectionCommand+TraceStatus]` objecten zijn, worden uitgevoerd naar de uitvoer stroom **geslaagd** .</span><span class="sxs-lookup"><span data-stu-id="15631-147">The results, which are `[Microsoft.PowerShell.Commands.TestConnectionCommand+TraceStatus]` objects, are output to the **Success** output stream.</span></span>

## <span data-ttu-id="15631-148">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="15631-148">PARAMETERS</span></span>

### <span data-ttu-id="15631-149">-BufferSize</span><span class="sxs-lookup"><span data-stu-id="15631-149">-BufferSize</span></span>

<span data-ttu-id="15631-150">Hiermee geeft u de grootte, in bytes, van de buffer die met deze opdracht wordt verzonden.</span><span class="sxs-lookup"><span data-stu-id="15631-150">Specifies the size, in bytes, of the buffer sent with this command.</span></span> <span data-ttu-id="15631-151">De standaard waarde is 32.</span><span class="sxs-lookup"><span data-stu-id="15631-151">The default value is 32.</span></span>

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

### <span data-ttu-id="15631-152">-REPEAT</span><span class="sxs-lookup"><span data-stu-id="15631-152">-Repeat</span></span>

<span data-ttu-id="15631-153">Zorgt ervoor dat de cmdlet doorlopend ping-aanvragen verzendt.</span><span class="sxs-lookup"><span data-stu-id="15631-153">Causes the cmdlet to send ping requests continuously.</span></span> <span data-ttu-id="15631-154">Deze para meter kan niet worden gebruikt met de para meter **Count** .</span><span class="sxs-lookup"><span data-stu-id="15631-154">This parameter can't be used with the **Count** parameter.</span></span>

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

### <span data-ttu-id="15631-155">-Aantal</span><span class="sxs-lookup"><span data-stu-id="15631-155">-Count</span></span>

<span data-ttu-id="15631-156">Hiermee geeft u het aantal ECHO aanvragen dat moet worden verzonden.</span><span class="sxs-lookup"><span data-stu-id="15631-156">Specifies the number of echo requests to send.</span></span> <span data-ttu-id="15631-157">De standaardwaarde is 4.</span><span class="sxs-lookup"><span data-stu-id="15631-157">The default value is 4.</span></span>

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

### <span data-ttu-id="15631-158">-Vertraging</span><span class="sxs-lookup"><span data-stu-id="15631-158">-Delay</span></span>

<span data-ttu-id="15631-159">Hiermee geeft u het interval tussen pings op, in seconden.</span><span class="sxs-lookup"><span data-stu-id="15631-159">Specifies the interval between pings, in seconds.</span></span>

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

### <span data-ttu-id="15631-160">-DontFragment</span><span class="sxs-lookup"><span data-stu-id="15631-160">-DontFragment</span></span>

<span data-ttu-id="15631-161">Met deze para meter wordt de vlag **don't fragment** in de IP-header ingesteld.</span><span class="sxs-lookup"><span data-stu-id="15631-161">This parameter sets the **Don't Fragment** flag in the IP header.</span></span> <span data-ttu-id="15631-162">U kunt deze para meter met de waarde **BufferSize** gebruiken om de grootte van het pad MTU te testen.</span><span class="sxs-lookup"><span data-stu-id="15631-162">You can use this parameter with the **BufferSize** parameter to test the Path MTU size.</span></span> <span data-ttu-id="15631-163">Zie het artikel [Path MTU Discovery](https://wikipedia.org/wiki/Path_MTU_Discovery) in Wikipedia voor meer informatie over Path MTU.</span><span class="sxs-lookup"><span data-stu-id="15631-163">For more information about Path MTU, see the [Path MTU Discovery](https://wikipedia.org/wiki/Path_MTU_Discovery) article in wikipedia.</span></span>

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

### <span data-ttu-id="15631-164">-IPv4</span><span class="sxs-lookup"><span data-stu-id="15631-164">-IPv4</span></span>

<span data-ttu-id="15631-165">Hiermee wordt de cmdlet gedwongen het IPv4-protocol voor de test te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="15631-165">Forces the cmdlet to use the IPv4 protocol for the test.</span></span>

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

### <span data-ttu-id="15631-166">-IPv6</span><span class="sxs-lookup"><span data-stu-id="15631-166">-IPv6</span></span>

<span data-ttu-id="15631-167">Hiermee wordt de cmdlet gedwongen het IPv6-protocol voor de test te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="15631-167">Forces the cmdlet to use the IPv6 protocol for the test.</span></span>

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

### <span data-ttu-id="15631-168">-MaxHops</span><span class="sxs-lookup"><span data-stu-id="15631-168">-MaxHops</span></span>

<span data-ttu-id="15631-169">Hiermee stelt u het maximum aantal hops in dat een ICMP-aanvraag bericht kan worden verzonden.</span><span class="sxs-lookup"><span data-stu-id="15631-169">Sets the maximum number of hops that an ICMP request message can be sent.</span></span> <span data-ttu-id="15631-170">De standaard waarde wordt beheerd door het besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="15631-170">The default value is controlled by the operating system.</span></span> <span data-ttu-id="15631-171">De standaard waarde voor Windows 10 is 128 hops.</span><span class="sxs-lookup"><span data-stu-id="15631-171">The default value for Windows 10 is 128 hops.</span></span>

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

### <span data-ttu-id="15631-172">-Ping</span><span class="sxs-lookup"><span data-stu-id="15631-172">-Ping</span></span>

<span data-ttu-id="15631-173">Zorgt ervoor dat de cmdlet een ping-test doet.</span><span class="sxs-lookup"><span data-stu-id="15631-173">Causes the cmdlet to do a ping test.</span></span> <span data-ttu-id="15631-174">Dit is de standaard modus voor de `Test-Connection` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="15631-174">This is the default mode for the `Test-Connection` cmdlet.</span></span>

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

### <span data-ttu-id="15631-175">-Quiet</span><span class="sxs-lookup"><span data-stu-id="15631-175">-Quiet</span></span>

<span data-ttu-id="15631-176">De **stille** para meter retourneert een **Booleaanse** waarde.</span><span class="sxs-lookup"><span data-stu-id="15631-176">The **Quiet** parameter returns a **Boolean** value.</span></span> <span data-ttu-id="15631-177">Als u deze para meter gebruikt, worden alle fouten onderdrukt.</span><span class="sxs-lookup"><span data-stu-id="15631-177">Using this parameter suppresses all errors.</span></span>

<span data-ttu-id="15631-178">Elke geteste verbinding retourneert een **Booleaanse** waarde.</span><span class="sxs-lookup"><span data-stu-id="15631-178">Each connection that's tested returns a **Boolean** value.</span></span> <span data-ttu-id="15631-179">Als de **TargetName** -para meter meerdere computers opgeeft, wordt een matrix met **Boole** -waarden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="15631-179">If the **TargetName** parameter specifies multiple computers, an array of **Boolean** values is returned.</span></span>

<span data-ttu-id="15631-180">Als **een** ping naar een bepaald doel slaagt, `$True` wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="15631-180">If **any** ping to a given target succeeds, `$True` is returned.</span></span>

<span data-ttu-id="15631-181">Als **alle** pings naar een bepaald doel mislukken, `$False` wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="15631-181">If **all** pings to a given target fail, `$False` is returned.</span></span>

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

### <span data-ttu-id="15631-182">-ResolveDestination</span><span class="sxs-lookup"><span data-stu-id="15631-182">-ResolveDestination</span></span>

<span data-ttu-id="15631-183">Zorgt ervoor dat de cmdlet probeert de DNS-naam van het doel op te lossen.</span><span class="sxs-lookup"><span data-stu-id="15631-183">Causes the cmdlet to attempt to resolve the DNS name of the target.</span></span> <span data-ttu-id="15631-184">Bij gebruik in combi natie met de para meter **traceroute** worden ook de DNS-namen van alle tussenliggende hosts opgehaald, indien mogelijk.</span><span class="sxs-lookup"><span data-stu-id="15631-184">When used in conjunction with the **Traceroute** parameter, the DNS names of all intermediate hosts will also be retrieved, if possible.</span></span>

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

### <span data-ttu-id="15631-185">-Source</span><span class="sxs-lookup"><span data-stu-id="15631-185">-Source</span></span>

<span data-ttu-id="15631-186">Hiermee geeft u de namen van de computers waarvan de ping afkomstig is.</span><span class="sxs-lookup"><span data-stu-id="15631-186">Specifies the names of the computers where the ping originates.</span></span> <span data-ttu-id="15631-187">Voer een door komma's gescheiden lijst met computer namen in.</span><span class="sxs-lookup"><span data-stu-id="15631-187">Enter a comma-separated list of computer names.</span></span> <span data-ttu-id="15631-188">Standaard is dit de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="15631-188">The default is the local computer.</span></span>

<span data-ttu-id="15631-189">**Opmerking:** Deze para meter is niet functioneel in Power shell versie 6 en hoger.</span><span class="sxs-lookup"><span data-stu-id="15631-189">**NOTE:** This parameter is not functional in PowerShell versions 6 and up.</span></span>
<span data-ttu-id="15631-190">Het opgeven van deze para meter heeft geen effect op de opdracht.</span><span class="sxs-lookup"><span data-stu-id="15631-190">Supplying this parameter will have no effect on the command.</span></span>

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

### <span data-ttu-id="15631-191">-Doel naam</span><span class="sxs-lookup"><span data-stu-id="15631-191">-TargetName</span></span>

<span data-ttu-id="15631-192">Hiermee geeft u de computer (s) op die u wilt testen.</span><span class="sxs-lookup"><span data-stu-id="15631-192">Specifies the computer(s) to test.</span></span> <span data-ttu-id="15631-193">Typ de computer namen of typ de IP-adressen in de IPv4-of IPv6-indeling.</span><span class="sxs-lookup"><span data-stu-id="15631-193">Type the computer names or type IP addresses in IPv4 or IPv6 format.</span></span>

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

### <span data-ttu-id="15631-194">-TimeoutSeconds</span><span class="sxs-lookup"><span data-stu-id="15631-194">-TimeoutSeconds</span></span>

<span data-ttu-id="15631-195">Hiermee stelt u de time-outwaarde voor de test.</span><span class="sxs-lookup"><span data-stu-id="15631-195">Sets the timeout value for the test.</span></span> <span data-ttu-id="15631-196">De test mislukt als er geen antwoord wordt ontvangen voordat de time-out is verstreken.</span><span class="sxs-lookup"><span data-stu-id="15631-196">The test fails if a response isn't received before the timeout expires.</span></span> <span data-ttu-id="15631-197">De standaard waarde is vijf seconden.</span><span class="sxs-lookup"><span data-stu-id="15631-197">The default is five seconds.</span></span>

<span data-ttu-id="15631-198">Deze para meter is geïntroduceerd in Power shell 6,0.</span><span class="sxs-lookup"><span data-stu-id="15631-198">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="15631-199">-Traceroute</span><span class="sxs-lookup"><span data-stu-id="15631-199">-Traceroute</span></span>

<span data-ttu-id="15631-200">Zorgt ervoor dat de cmdlet een traceroute-test doet.</span><span class="sxs-lookup"><span data-stu-id="15631-200">Causes the cmdlet to do a traceroute test.</span></span> <span data-ttu-id="15631-201">Als deze para meter wordt gebruikt, retourneert de cmdlet een- `TestConnectionCommand+TraceStatus` object.</span><span class="sxs-lookup"><span data-stu-id="15631-201">When this parameter is used, the cmdlet returns a `TestConnectionCommand+TraceStatus` object.</span></span>

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

### <span data-ttu-id="15631-202">-MtuSize</span><span class="sxs-lookup"><span data-stu-id="15631-202">-MtuSize</span></span>

<span data-ttu-id="15631-203">Deze para meter wordt gebruikt om de MTU-grootte van het pad te detecteren.</span><span class="sxs-lookup"><span data-stu-id="15631-203">This parameter is used to discover the Path MTU size.</span></span> <span data-ttu-id="15631-204">De cmdlet retourneert een **PingReply # MTUSize** -object dat de MTU-grootte van het pad naar het doel bevat.</span><span class="sxs-lookup"><span data-stu-id="15631-204">The cmdlet returns a **PingReply#MTUSize** object that contains the Path MTU size to the target.</span></span> <span data-ttu-id="15631-205">Zie het artikel [Path MTU Discovery](https://wikipedia.org/wiki/Path_MTU_Discovery) in Wikipedia voor meer informatie over Path MTU.</span><span class="sxs-lookup"><span data-stu-id="15631-205">For more information about Path MTU, see the [Path MTU Discovery](https://wikipedia.org/wiki/Path_MTU_Discovery) article in wikipedia.</span></span>

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

### <span data-ttu-id="15631-206">-TcpPort</span><span class="sxs-lookup"><span data-stu-id="15631-206">-TcpPort</span></span>

<span data-ttu-id="15631-207">Hiermee geeft u het TCP-poort nummer op het doel dat moet worden gebruikt in de TCP-verbindings test.</span><span class="sxs-lookup"><span data-stu-id="15631-207">Specifies the TCP port number on the target to be used in the TCP connection test.</span></span> <span data-ttu-id="15631-208">De cmdlet probeert een TCP-verbinding tot stand te brengen met de opgegeven poort op het doel.</span><span class="sxs-lookup"><span data-stu-id="15631-208">The cmdlet will attempt to make a TCP connection to the specified port on the target.</span></span>

<span data-ttu-id="15631-209">Als er een verbinding kan worden gemaakt, `$True` wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="15631-209">If a connection can be made, `$True` will be returned.</span></span>

<span data-ttu-id="15631-210">Als er geen verbinding kan worden gemaakt, `$False` wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="15631-210">If a connection cannot be made, `$False` will be returned.</span></span>

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

### <span data-ttu-id="15631-211">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="15631-211">CommonParameters</span></span>

<span data-ttu-id="15631-212">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="15631-212">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="15631-213">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="15631-213">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="15631-214">INVOER</span><span class="sxs-lookup"><span data-stu-id="15631-214">INPUTS</span></span>

### <span data-ttu-id="15631-215">Geen</span><span class="sxs-lookup"><span data-stu-id="15631-215">None</span></span>

<span data-ttu-id="15631-216">U kunt invoer niet naar deze cmdlet pipeen.</span><span class="sxs-lookup"><span data-stu-id="15631-216">You can't pipe input to this cmdlet.</span></span>

## <span data-ttu-id="15631-217">UITVOER</span><span class="sxs-lookup"><span data-stu-id="15631-217">OUTPUTS</span></span>

### <span data-ttu-id="15631-218">TestConnectionCommand + PingStatus, TestConnectionCommand + TraceStatus, Boolean, TestConnectionCommand + PingMtuStatus</span><span class="sxs-lookup"><span data-stu-id="15631-218">TestConnectionCommand+PingStatus, TestConnectionCommand+TraceStatus, Boolean, TestConnectionCommand+PingMtuStatus</span></span>

<span data-ttu-id="15631-219">`Test-Connection`Retourneert standaard een **TestConnectionCommand + PingStatus** -object voor elk ping-antwoord.</span><span class="sxs-lookup"><span data-stu-id="15631-219">By default, `Test-Connection` returns a **TestConnectionCommand+PingStatus** object for each ping reply.</span></span>

<span data-ttu-id="15631-220">Als u de para meter **traceroute** opgeeft, retourneert de cmdlet een **TestConnectionCommand + TraceStatus** -object voor elk ping-antwoord op de route.</span><span class="sxs-lookup"><span data-stu-id="15631-220">If you specify the **Traceroute** parameter, the cmdlet will return a **TestConnectionCommand+TraceStatus** object for each ping reply along the route.</span></span>

<span data-ttu-id="15631-221">Als u de para meters **quiet** of **TcpPort** opgeeft, wordt een **Booleaanse** waarde geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="15631-221">If you specify the **Quiet** or **TcpPort** parameters, it returns a **Boolean** value.</span></span> <span data-ttu-id="15631-222">Als er meerdere verbindingen worden getest, wordt een matrix met **Boole** -waarden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="15631-222">If multiple connections are tested, an array of **Boolean** values is returned.</span></span>

## <span data-ttu-id="15631-223">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="15631-223">NOTES</span></span>

## <span data-ttu-id="15631-224">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="15631-224">RELATED LINKS</span></span>

[<span data-ttu-id="15631-225">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="15631-225">Restart-Computer</span></span>](Restart-Computer.md)

[<span data-ttu-id="15631-226">Stop-computer</span><span class="sxs-lookup"><span data-stu-id="15631-226">Stop-Computer</span></span>](Stop-Computer.md)

