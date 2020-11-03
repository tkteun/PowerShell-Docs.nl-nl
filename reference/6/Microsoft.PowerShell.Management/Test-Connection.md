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
# <span data-ttu-id="8fc61-103">Test-Connection</span><span class="sxs-lookup"><span data-stu-id="8fc61-103">Test-Connection</span></span>

## <span data-ttu-id="8fc61-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="8fc61-104">SYNOPSIS</span></span>
<span data-ttu-id="8fc61-105">Verzendt ICMP echo aanvraag pakketten of pings naar een of meer computers.</span><span class="sxs-lookup"><span data-stu-id="8fc61-105">Sends ICMP echo request packets, or pings, to one or more computers.</span></span>

## <span data-ttu-id="8fc61-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="8fc61-106">SYNTAX</span></span>

### <span data-ttu-id="8fc61-107">PingCount (standaard)</span><span class="sxs-lookup"><span data-stu-id="8fc61-107">PingCount (Default)</span></span>

```
Test-Connection [-Ping] [-IPv4] [-IPv6] [-ResolveDestination] [-Source <String>] [-MaxHops <Int32>]
 [-Count <Int32>] [-Delay <Int32>] [-BufferSize <Int32>] [-DontFragment] [-TimeoutSeconds <Int32>]
 [-TargetName] <String[]> [-Quiet] [<CommonParameters>]
```

### <span data-ttu-id="8fc61-108">PingContinues</span><span class="sxs-lookup"><span data-stu-id="8fc61-108">PingContinues</span></span>

```
Test-Connection [-Ping] [-IPv4] [-IPv6] [-ResolveDestination] [-Source <String>] [-MaxHops <Int32>]
 [-Delay <Int32>] [-BufferSize <Int32>] [-DontFragment] [-Continues] [-TimeoutSeconds <Int32>]
 [-TargetName] <String[]> [-Quiet] [<CommonParameters>]
```

### <span data-ttu-id="8fc61-109">DetectionOfMTUSize</span><span class="sxs-lookup"><span data-stu-id="8fc61-109">DetectionOfMTUSize</span></span>

```
Test-Connection [-IPv4] [-IPv6] [-ResolveDestination] [-TimeoutSeconds <Int32>]
 [-TargetName] <String[]> -MTUSizeDetect [-Quiet] [<CommonParameters>]
```

### <span data-ttu-id="8fc61-110">TraceRoute</span><span class="sxs-lookup"><span data-stu-id="8fc61-110">TraceRoute</span></span>

```
Test-Connection [-IPv4] [-IPv6] [-ResolveDestination] [-Source <String>] [-MaxHops <Int32>]
 [-TimeoutSeconds <Int32>] [-TargetName] <String[]> -Traceroute [-Quiet] [<CommonParameters>]
```

### <span data-ttu-id="8fc61-111">ConnectionByTCPPort</span><span class="sxs-lookup"><span data-stu-id="8fc61-111">ConnectionByTCPPort</span></span>

```
Test-Connection [-IPv4] [-IPv6] [-ResolveDestination] [-Source <String>] [-TimeoutSeconds <Int32>]
 [-TargetName] <String[]> -TCPPort <Int32> [-Quiet] [<CommonParameters>]
```

## <span data-ttu-id="8fc61-112">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="8fc61-112">DESCRIPTION</span></span>

<span data-ttu-id="8fc61-113">De `Test-Connection` cmdlet stuurt Internet Control Message Protocol (ICMP) Echo aanvraag pakketten of pings naar een of meer externe computers en retourneert de antwoorden op de echo reactie.</span><span class="sxs-lookup"><span data-stu-id="8fc61-113">The `Test-Connection` cmdlet sends Internet Control Message Protocol (ICMP) echo request packets, or pings, to one or more remote computers and returns the echo response replies.</span></span> <span data-ttu-id="8fc61-114">U kunt deze cmdlet gebruiken om te bepalen of er verbinding kan worden gemaakt met een bepaalde computer via een IP-netwerk.</span><span class="sxs-lookup"><span data-stu-id="8fc61-114">You can use this cmdlet to determine whether a particular computer can be contacted across an IP network.</span></span>

<span data-ttu-id="8fc61-115">U kunt de para meters van gebruiken `Test-Connection` om zowel de verzendende als ontvangende computers op te geven om de opdracht als achtergrond taak uit te voeren, om een time-out en een aantal pings in te stellen en om de verbinding en verificatie te configureren.</span><span class="sxs-lookup"><span data-stu-id="8fc61-115">You can use the parameters of `Test-Connection` to specify both the sending and receiving computers, to run the command as a background job, to set a time-out and number of pings, and to configure the connection and authentication.</span></span>

<span data-ttu-id="8fc61-116">In tegens telling tot de bekende **ping** -opdracht `Test-Connection` retourneert een **TestConnectionCommand + PingReport** -object dat u kunt onderzoeken in Power shell.</span><span class="sxs-lookup"><span data-stu-id="8fc61-116">Unlike the familiar **ping** command, `Test-Connection` returns a **TestConnectionCommand+PingReport** object that you can investigate in PowerShell.</span></span> <span data-ttu-id="8fc61-117">De **stille** para meter retourneert een **Boole** -waarde in een object **System. Boolean** voor elke geteste verbinding.</span><span class="sxs-lookup"><span data-stu-id="8fc61-117">The **Quiet** parameter returns a **Boolean** value in a **System.Boolean** object for each tested connection.</span></span> <span data-ttu-id="8fc61-118">Als er meerdere verbindingen worden getest, wordt een matrix met **Boole** -waarden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="8fc61-118">If multiple connections are tested, an array of **Boolean** values is returned.</span></span>

## <span data-ttu-id="8fc61-119">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="8fc61-119">EXAMPLES</span></span>

### <span data-ttu-id="8fc61-120">Voor beeld 1: ECHO aanvragen verzenden naar een externe computer</span><span class="sxs-lookup"><span data-stu-id="8fc61-120">Example 1: Send echo requests to a remote computer</span></span>

<span data-ttu-id="8fc61-121">In dit voor beeld worden ECHO aanvraag pakketten van de lokale computer verzonden naar de Server01-computer.</span><span class="sxs-lookup"><span data-stu-id="8fc61-121">This example sends echo request packets from the local computer to the Server01 computer.</span></span>

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

<span data-ttu-id="8fc61-122">`Test-Connection` maakt gebruik van de **TargetName** -para meter om de Server01-computer op te geven.</span><span class="sxs-lookup"><span data-stu-id="8fc61-122">`Test-Connection` uses the **TargetName** parameter to specify the Server01 computer.</span></span> <span data-ttu-id="8fc61-123">De **IPv4** -para meter geeft u het protocol voor de test op.</span><span class="sxs-lookup"><span data-stu-id="8fc61-123">The **IPv4** parameter specifies the protocol for the test.</span></span>

<span data-ttu-id="8fc61-124">De ping-uitvoer wordt verzonden naar de **informatie** stroom terwijl het **TestConnectionCommand + PingReport** -object wordt verzonden naar de stroom van **slagen** .</span><span class="sxs-lookup"><span data-stu-id="8fc61-124">The ping output is sent to the **Information** stream while the **TestConnectionCommand+PingReport** object sent to the **Success** stream.</span></span> <span data-ttu-id="8fc61-125">Zie [about_Redirection](../microsoft.powershell.core/about/about_redirection.md)voor meer informatie over de uitvoer stromen.</span><span class="sxs-lookup"><span data-stu-id="8fc61-125">For more information about the output streams, see [about_Redirection](../microsoft.powershell.core/about/about_redirection.md).</span></span>

### <span data-ttu-id="8fc61-126">Voor beeld 2: ECHO aanvragen verzenden naar verschillende computers</span><span class="sxs-lookup"><span data-stu-id="8fc61-126">Example 2: Send echo requests to several computers</span></span>

<span data-ttu-id="8fc61-127">In dit voor beeld worden pings van de lokale computer naar verschillende externe computers verzonden.</span><span class="sxs-lookup"><span data-stu-id="8fc61-127">This example sends pings from the local computer to several remote computers.</span></span>

```powershell
Test-Connection -TargetName Server01, Server02, Server12
```

### <span data-ttu-id="8fc61-128">Voor beeld 3: ECHO aanvragen van verschillende computers verzenden naar een computer</span><span class="sxs-lookup"><span data-stu-id="8fc61-128">Example 3: Send echo requests from several computers to a computer</span></span>

<span data-ttu-id="8fc61-129">In dit voor beeld worden pings van verschillende bron computers verzonden naar één externe computer, Server01.</span><span class="sxs-lookup"><span data-stu-id="8fc61-129">This example sends pings from different source computers to a single remote computer, Server01.</span></span>

```powershell
Test-Connection -Source Server02, Server12, localhost -TargetName Server01
```

<span data-ttu-id="8fc61-130">Gebruik deze opdracht indeling om de latentie van verbindingen vanaf meerdere punten te testen.</span><span class="sxs-lookup"><span data-stu-id="8fc61-130">Use this command format to test the latency of connections from multiple points.</span></span>

### <span data-ttu-id="8fc61-131">Voor beeld 4: para meters gebruiken om de test opdracht aan te passen</span><span class="sxs-lookup"><span data-stu-id="8fc61-131">Example 4: Use parameters to customize the test command</span></span>

<span data-ttu-id="8fc61-132">In dit voor beeld worden de para meters van gebruikt `Test-Connection` voor het aanpassen van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="8fc61-132">This example uses the parameters of `Test-Connection` to customize the command.</span></span> <span data-ttu-id="8fc61-133">De lokale computer verzendt een ping-test naar een externe computer.</span><span class="sxs-lookup"><span data-stu-id="8fc61-133">The local computer sends a ping test to a remote computer.</span></span>

```powershell
Test-Connection -TargetName Server01 -Count 3 -Delay 2 -MaxHops 255 -BufferSize 256
```

<span data-ttu-id="8fc61-134">`Test-Connection` maakt gebruik van de para meter **TargetName** om Server01 op te geven.</span><span class="sxs-lookup"><span data-stu-id="8fc61-134">`Test-Connection` uses the **TargetName** parameter to specify Server01.</span></span> <span data-ttu-id="8fc61-135">De para meter **aantal** geeft aan dat drie pings worden verzonden naar de Server01-computer, met een **vertraging** van twee seconden intervallen.</span><span class="sxs-lookup"><span data-stu-id="8fc61-135">The **Count** parameter specifies three pings are sent to the Server01 computer with a **Delay** of 2-second intervals.</span></span>

<span data-ttu-id="8fc61-136">U kunt deze opties gebruiken wanneer het ping-antwoord naar verwachting langer duurt dan normaal, ofwel vanwege een uitgebreid aantal hops of een netwerk toestand met een hoog verkeer.</span><span class="sxs-lookup"><span data-stu-id="8fc61-136">You might use these options when the ping response is expected to take longer than usual, either because of an extended number of hops or a high-traffic network condition.</span></span>

### <span data-ttu-id="8fc61-137">Voor beeld 5: een test uitvoeren als een achtergrond taak</span><span class="sxs-lookup"><span data-stu-id="8fc61-137">Example 5: Run a test as a background job</span></span>

<span data-ttu-id="8fc61-138">In dit voor beeld ziet u hoe u een `Test-Connection` opdracht uitvoert als een Power shell-achtergrond taak.</span><span class="sxs-lookup"><span data-stu-id="8fc61-138">This example shows how to run a `Test-Connection` command as a PowerShell background job.</span></span>

```powershell
$job = Start-Job -ScriptBlock { Test-Connection -TargetName (Get-Content "Servers.txt") }
if ($job.JobStateInfo.State -ne "Running") { $Results = Receive-Job $job }
```

<span data-ttu-id="8fc61-139">De `Start-Job` opdracht gebruikt de `Test-Connection` cmdlet voor het pingen van veel computers in een onderneming.</span><span class="sxs-lookup"><span data-stu-id="8fc61-139">The `Start-Job` command uses the `Test-Connection` cmdlet to ping many computers in an enterprise.</span></span>
<span data-ttu-id="8fc61-140">De waarde van de **TargetName** -para meter is een `Get-Content` opdracht waarmee een lijst met computer namen uit het `Servers.txt` bestand wordt gelezen.</span><span class="sxs-lookup"><span data-stu-id="8fc61-140">The value of the **TargetName** parameter is a `Get-Content` command that reads a list of computer names from the `Servers.txt` file.</span></span> <span data-ttu-id="8fc61-141">De opdracht gebruikt de `Start-Job` cmdlet om de opdracht uit te voeren als een achtergrond taak en de taak wordt opgeslagen in de `$job` variabele.</span><span class="sxs-lookup"><span data-stu-id="8fc61-141">The command uses the `Start-Job` cmdlet to run the command as a background job and it saves the job in the `$job` variable.</span></span>

<span data-ttu-id="8fc61-142">De `if` opdracht controleert of de taak nog niet wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="8fc61-142">The `if` command checks to see that the job isn't still running.</span></span> <span data-ttu-id="8fc61-143">Als de taak niet wordt uitgevoerd, `Receive-Job` worden de resultaten opgehaald en opgeslagen in de `$Results` variabele.</span><span class="sxs-lookup"><span data-stu-id="8fc61-143">If the job isn't running, `Receive-Job` gets the results and stores them in the `$Results` variable.</span></span>

### <span data-ttu-id="8fc61-144">Voor beeld 6: een sessie alleen maken als de verbindings test is geslaagd</span><span class="sxs-lookup"><span data-stu-id="8fc61-144">Example 6: Create a session only if a connection test succeeds</span></span>

<span data-ttu-id="8fc61-145">In dit voor beeld wordt alleen een sessie op de Server01-computer gemaakt als ten minste één van de pings die naar de computer worden verzonden, slaagt.</span><span class="sxs-lookup"><span data-stu-id="8fc61-145">This example creates a session on the Server01 computer only if at least one of the pings sent to the computer succeeds.</span></span>

```powershell
if (Test-Connection -TargetName Server01 -Quiet) {New-PSSession Server01}
```

<span data-ttu-id="8fc61-146">De `if` opdracht gebruikt de `Test-Connection` cmdlet om de Server01-computer te pingen.</span><span class="sxs-lookup"><span data-stu-id="8fc61-146">The `if` command uses the `Test-Connection` cmdlet to ping the Server01 computer.</span></span> <span data-ttu-id="8fc61-147">De opdracht maakt gebruik van de **stille** para meter, waarmee een **Booleaanse** waarde wordt geretourneerd in plaats van een **TestConnectionCommand + PingReport** -object.</span><span class="sxs-lookup"><span data-stu-id="8fc61-147">The command uses the **Quiet** parameter, which returns a **Boolean** value, instead of a **TestConnectionCommand+PingReport** object.</span></span>

<span data-ttu-id="8fc61-148">De waarde is `$True` als een van de vier pings slaagt.</span><span class="sxs-lookup"><span data-stu-id="8fc61-148">The value is `$True` if any of the four pings succeed.</span></span> <span data-ttu-id="8fc61-149">Als geen van de pings slaagt, is de waarde `$False` .</span><span class="sxs-lookup"><span data-stu-id="8fc61-149">If none of the pings succeed, the value is `$False`.</span></span>

<span data-ttu-id="8fc61-150">Als de `Test-Connection` opdracht een waarde retourneert `$True` , gebruikt de opdracht de `New-PSSession` cmdlet om de **PSSession** te maken.</span><span class="sxs-lookup"><span data-stu-id="8fc61-150">If the `Test-Connection` command returns a value of `$True`, the command uses the `New-PSSession` cmdlet to create the **PSSession**.</span></span>

### <span data-ttu-id="8fc61-151">Voor beeld 7: de para meter traceroute gebruiken</span><span class="sxs-lookup"><span data-stu-id="8fc61-151">Example 7: Use the Traceroute parameter</span></span>

<span data-ttu-id="8fc61-152">Vanaf Power shell 6,0 wijst de para meter **traceroute** een route toe tussen de lokale computer en de externe bestemming die u opgeeft met de para meter **TargetName** .</span><span class="sxs-lookup"><span data-stu-id="8fc61-152">Beginning in PowerShell 6.0, the **Traceroute** parameter maps a route between the local computer and the remote destination you specify with the **TargetName** parameter.</span></span>

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

<span data-ttu-id="8fc61-153">De `Test-Connection` opdracht maakt gebruik van de para meter **traceroute** .</span><span class="sxs-lookup"><span data-stu-id="8fc61-153">The `Test-Connection` command uses the **Traceroute** parameter.</span></span> <span data-ttu-id="8fc61-154">De resultaten, die `[Microsoft.PowerShell.Commands.TestConnectionCommand+TraceRouteResult]` objecten zijn, worden door gegeven aan de `ForEach-Object` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8fc61-154">The results, which are `[Microsoft.PowerShell.Commands.TestConnectionCommand+TraceRouteResult]` objects, are piped to the `ForEach-Object` cmdlet.</span></span> <span data-ttu-id="8fc61-155">`ForEach-Object` Hiermee maakt u een gestructureerde uitvoer van de Inge sloten `[Microsoft.PowerShell.Commands.TestConnectionCommand+TraceRouteReply]` objecten en de volgende `[System.Net.NetworkInformation.PingReply]` objecten.</span><span class="sxs-lookup"><span data-stu-id="8fc61-155">`ForEach-Object` creates a structured output of the contained `[Microsoft.PowerShell.Commands.TestConnectionCommand+TraceRouteReply]` objects and subsequent `[System.Net.NetworkInformation.PingReply]` objects.</span></span>

## <span data-ttu-id="8fc61-156">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8fc61-156">PARAMETERS</span></span>

### <span data-ttu-id="8fc61-157">-BufferSize</span><span class="sxs-lookup"><span data-stu-id="8fc61-157">-BufferSize</span></span>

<span data-ttu-id="8fc61-158">Hiermee geeft u de grootte, in bytes, van de buffer die met deze opdracht wordt verzonden.</span><span class="sxs-lookup"><span data-stu-id="8fc61-158">Specifies the size, in bytes, of the buffer sent with this command.</span></span> <span data-ttu-id="8fc61-159">De standaard waarde is 32.</span><span class="sxs-lookup"><span data-stu-id="8fc61-159">The default value is 32.</span></span>

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

### <span data-ttu-id="8fc61-160">-Aantal</span><span class="sxs-lookup"><span data-stu-id="8fc61-160">-Count</span></span>

<span data-ttu-id="8fc61-161">Hiermee geeft u het aantal ECHO aanvragen dat moet worden verzonden.</span><span class="sxs-lookup"><span data-stu-id="8fc61-161">Specifies the number of echo requests to send.</span></span> <span data-ttu-id="8fc61-162">De standaardwaarde is 4.</span><span class="sxs-lookup"><span data-stu-id="8fc61-162">The default value is 4.</span></span>

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

### <span data-ttu-id="8fc61-163">-Vertraging</span><span class="sxs-lookup"><span data-stu-id="8fc61-163">-Delay</span></span>

<span data-ttu-id="8fc61-164">Hiermee geeft u het interval tussen pings op, in seconden.</span><span class="sxs-lookup"><span data-stu-id="8fc61-164">Specifies the interval between pings, in seconds.</span></span>

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

### <span data-ttu-id="8fc61-165">-DontFragment</span><span class="sxs-lookup"><span data-stu-id="8fc61-165">-DontFragment</span></span>

<span data-ttu-id="8fc61-166">Met deze para meter wordt de vlag **don't fragment** in de IP-header ingesteld.</span><span class="sxs-lookup"><span data-stu-id="8fc61-166">This parameter sets the **Don't Fragment** flag in the IP header.</span></span> <span data-ttu-id="8fc61-167">U kunt deze para meter met de waarde **BufferSize** gebruiken om de grootte van het pad MTU te testen.</span><span class="sxs-lookup"><span data-stu-id="8fc61-167">You can use this parameter with the **BufferSize** parameter to test the Path MTU size.</span></span> <span data-ttu-id="8fc61-168">Zie het artikel [Path MTU Discovery](https://wikipedia.org/wiki/Path_MTU_Discovery) in Wikipedia voor meer informatie over Path MTU.</span><span class="sxs-lookup"><span data-stu-id="8fc61-168">For more information about Path MTU, see the [Path MTU Discovery](https://wikipedia.org/wiki/Path_MTU_Discovery) article in wikipedia.</span></span>

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

### <span data-ttu-id="8fc61-169">-IPv4</span><span class="sxs-lookup"><span data-stu-id="8fc61-169">-IPv4</span></span>

<span data-ttu-id="8fc61-170">Hiermee wordt de cmdlet gedwongen het IPv4-protocol voor de test te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="8fc61-170">Forces the cmdlet to use the IPv4 protocol for the test.</span></span>

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

### <span data-ttu-id="8fc61-171">-IPv6</span><span class="sxs-lookup"><span data-stu-id="8fc61-171">-IPv6</span></span>

<span data-ttu-id="8fc61-172">Hiermee wordt de cmdlet gedwongen het IPv6-protocol voor de test te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="8fc61-172">Forces the cmdlet to use the IPv6 protocol for the test.</span></span>

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

### <span data-ttu-id="8fc61-173">-MaxHops</span><span class="sxs-lookup"><span data-stu-id="8fc61-173">-MaxHops</span></span>

<span data-ttu-id="8fc61-174">Hiermee stelt u het maximum aantal hops in dat een ICMP-aanvraag bericht kan worden verzonden.</span><span class="sxs-lookup"><span data-stu-id="8fc61-174">Sets the maximum number of hops that an ICMP request message can be sent.</span></span> <span data-ttu-id="8fc61-175">De standaard waarde wordt beheerd door het besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="8fc61-175">The default value is controlled by the operating system.</span></span> <span data-ttu-id="8fc61-176">De standaard waarde voor Windows 10 is 128 hops.</span><span class="sxs-lookup"><span data-stu-id="8fc61-176">The default value for Windows 10 is 128 hops.</span></span>

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

### <span data-ttu-id="8fc61-177">-Ping</span><span class="sxs-lookup"><span data-stu-id="8fc61-177">-Ping</span></span>

<span data-ttu-id="8fc61-178">Zorgt ervoor dat de cmdlet een ping-test uitvoert. Dit is de standaard actie.</span><span class="sxs-lookup"><span data-stu-id="8fc61-178">Causes the cmdlet to do a ping test, which is the default action.</span></span>

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

### <span data-ttu-id="8fc61-179">-Quiet</span><span class="sxs-lookup"><span data-stu-id="8fc61-179">-Quiet</span></span>

<span data-ttu-id="8fc61-180">De **stille** para meter retourneert een **Booleaanse** waarde in een object **System. Boolean** .</span><span class="sxs-lookup"><span data-stu-id="8fc61-180">The **Quiet** parameter returns a **Boolean** value in a **System.Boolean** object.</span></span> <span data-ttu-id="8fc61-181">Als u deze para meter gebruikt, worden alle fouten onderdrukt.</span><span class="sxs-lookup"><span data-stu-id="8fc61-181">Using this parameter suppresses all errors.</span></span>

<span data-ttu-id="8fc61-182">Elke geteste verbinding retourneert een **Booleaanse** waarde.</span><span class="sxs-lookup"><span data-stu-id="8fc61-182">Each connection that's tested returns a **Boolean** value.</span></span> <span data-ttu-id="8fc61-183">Als de **TargetName** -para meter meerdere computers opgeeft, wordt een matrix met **Boole** -waarden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="8fc61-183">If the **TargetName** parameter specifies multiple computers, an array of **Boolean** values is returned.</span></span>

<span data-ttu-id="8fc61-184">Als **een** ping slaagt, `$True` wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="8fc61-184">If **any** ping succeeds, `$True` is returned.</span></span>

<span data-ttu-id="8fc61-185">Als **alle** pings mislukken, `$False` wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="8fc61-185">If **all** pings fail, `$False` is returned.</span></span>

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

### <span data-ttu-id="8fc61-186">-ResolveDestination</span><span class="sxs-lookup"><span data-stu-id="8fc61-186">-ResolveDestination</span></span>

<span data-ttu-id="8fc61-187">Zorgt ervoor dat de cmdlet probeert de DNS-naam van het doel op te lossen.</span><span class="sxs-lookup"><span data-stu-id="8fc61-187">Causes the cmdlet to attempt to resolve the DNS name of the target.</span></span>

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

### <span data-ttu-id="8fc61-188">-Source</span><span class="sxs-lookup"><span data-stu-id="8fc61-188">-Source</span></span>

<span data-ttu-id="8fc61-189">Hiermee geeft u de namen van de computers waarvan de ping afkomstig is.</span><span class="sxs-lookup"><span data-stu-id="8fc61-189">Specifies the names of the computers where the ping originates.</span></span> <span data-ttu-id="8fc61-190">Voer een door komma's gescheiden lijst met computer namen in.</span><span class="sxs-lookup"><span data-stu-id="8fc61-190">Enter a comma-separated list of computer names.</span></span> <span data-ttu-id="8fc61-191">Standaard is dit de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="8fc61-191">The default is the local computer.</span></span>

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

### <span data-ttu-id="8fc61-192">-Doel naam</span><span class="sxs-lookup"><span data-stu-id="8fc61-192">-TargetName</span></span>

<span data-ttu-id="8fc61-193">Hiermee geeft u de computers op die u wilt testen.</span><span class="sxs-lookup"><span data-stu-id="8fc61-193">Specifies the computers to test.</span></span> <span data-ttu-id="8fc61-194">Typ de computer namen of typ de IP-adressen in de IPv4-of IPv6-indeling.</span><span class="sxs-lookup"><span data-stu-id="8fc61-194">Type the computer names or type IP addresses in IPv4 or IPv6 format.</span></span> <span data-ttu-id="8fc61-195">Joker tekens zijn niet toegestaan.</span><span class="sxs-lookup"><span data-stu-id="8fc61-195">Wildcard characters aren't permitted.</span></span> <span data-ttu-id="8fc61-196">Deze parameter is vereist.</span><span class="sxs-lookup"><span data-stu-id="8fc61-196">This parameter is required.</span></span> <span data-ttu-id="8fc61-197">**ComputerName** is een alias voor deze para meter.</span><span class="sxs-lookup"><span data-stu-id="8fc61-197">**ComputerName** is an alias for this parameter.</span></span>

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

### <span data-ttu-id="8fc61-198">-TCPPort</span><span class="sxs-lookup"><span data-stu-id="8fc61-198">-TCPPort</span></span>

<span data-ttu-id="8fc61-199">Hiermee geeft u het TCP-poort nummer op het doel dat moet worden gebruikt in de TCP-verbindings test.</span><span class="sxs-lookup"><span data-stu-id="8fc61-199">Specifies the TCP port number on the target to be used in the TCP connection test.</span></span> <span data-ttu-id="8fc61-200">De cmdlet probeert een TCP-verbinding tot stand te brengen met de opgegeven poort op het doel.</span><span class="sxs-lookup"><span data-stu-id="8fc61-200">The cmdlet will attempt to make a TCP connection to the specified port on the target.</span></span>

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

### <span data-ttu-id="8fc61-201">-TimeoutSeconds</span><span class="sxs-lookup"><span data-stu-id="8fc61-201">-TimeoutSeconds</span></span>

<span data-ttu-id="8fc61-202">Hiermee stelt u de time-outwaarde voor de test.</span><span class="sxs-lookup"><span data-stu-id="8fc61-202">Sets the timeout value for the test.</span></span> <span data-ttu-id="8fc61-203">De test mislukt als er geen antwoord wordt ontvangen voordat de time-out is verstreken.</span><span class="sxs-lookup"><span data-stu-id="8fc61-203">The test fails if a response isn't received before the timeout expires.</span></span> <span data-ttu-id="8fc61-204">De standaard waarde is vijf seconden.</span><span class="sxs-lookup"><span data-stu-id="8fc61-204">The default is five seconds.</span></span>

<span data-ttu-id="8fc61-205">Deze para meter is geïntroduceerd in Power shell 6,0.</span><span class="sxs-lookup"><span data-stu-id="8fc61-205">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="8fc61-206">-Traceroute</span><span class="sxs-lookup"><span data-stu-id="8fc61-206">-Traceroute</span></span>

<span data-ttu-id="8fc61-207">Zorgt ervoor dat de cmdlet een traceroute-test doet.</span><span class="sxs-lookup"><span data-stu-id="8fc61-207">Causes the cmdlet to do a traceroute test.</span></span> <span data-ttu-id="8fc61-208">Als deze para meter wordt gebruikt, retourneert de cmdlet een- `TestConnectionCommand+TraceRouteResult` object.</span><span class="sxs-lookup"><span data-stu-id="8fc61-208">When this parameter is used, the cmdlet returns a `TestConnectionCommand+TraceRouteResult` object.</span></span>

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

### <span data-ttu-id="8fc61-209">-Doorgaat</span><span class="sxs-lookup"><span data-stu-id="8fc61-209">-Continues</span></span>

<span data-ttu-id="8fc61-210">Zorgt ervoor dat de cmdlet doorlopend ping-aanvragen verzendt.</span><span class="sxs-lookup"><span data-stu-id="8fc61-210">Causes the cmdlet to send ping requests continuously.</span></span> <span data-ttu-id="8fc61-211">Deze para meter kan niet worden gebruikt met de para meter **Count** .</span><span class="sxs-lookup"><span data-stu-id="8fc61-211">This parameter can't be used with the **Count** parameter.</span></span>

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

### <span data-ttu-id="8fc61-212">-MTUSizeDetect</span><span class="sxs-lookup"><span data-stu-id="8fc61-212">-MTUSizeDetect</span></span>

<span data-ttu-id="8fc61-213">Deze para meter wordt gebruikt om de MTU-grootte van het pad te detecteren.</span><span class="sxs-lookup"><span data-stu-id="8fc61-213">This parameter is used to discover the Path MTU size.</span></span> <span data-ttu-id="8fc61-214">De cmdlet retourneert een **PingReply # MTUSize** -object dat de MTU-grootte van het pad naar het doel bevat.</span><span class="sxs-lookup"><span data-stu-id="8fc61-214">The cmdlet returns a **PingReply#MTUSize** object that contains the Path MTU size to the target.</span></span> <span data-ttu-id="8fc61-215">Zie het artikel [Path MTU Discovery](https://wikipedia.org/wiki/Path_MTU_Discovery) in Wikipedia voor meer informatie over Path MTU.</span><span class="sxs-lookup"><span data-stu-id="8fc61-215">For more information about Path MTU, see the [Path MTU Discovery](https://wikipedia.org/wiki/Path_MTU_Discovery) article in wikipedia.</span></span>

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

### <span data-ttu-id="8fc61-216">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8fc61-216">CommonParameters</span></span>

<span data-ttu-id="8fc61-217">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8fc61-217">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8fc61-218">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="8fc61-218">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8fc61-219">INVOER</span><span class="sxs-lookup"><span data-stu-id="8fc61-219">INPUTS</span></span>

### <span data-ttu-id="8fc61-220">Geen</span><span class="sxs-lookup"><span data-stu-id="8fc61-220">None</span></span>

<span data-ttu-id="8fc61-221">U kunt invoer niet naar deze cmdlet pipeen.</span><span class="sxs-lookup"><span data-stu-id="8fc61-221">You can't pipe input to this cmdlet.</span></span>

## <span data-ttu-id="8fc61-222">UITVOER</span><span class="sxs-lookup"><span data-stu-id="8fc61-222">OUTPUTS</span></span>

### <span data-ttu-id="8fc61-223">TestConnectionCommand + PingReport, TestConnectionCommand + TraceRouteResult, Boolean, PingReply # MTUSize</span><span class="sxs-lookup"><span data-stu-id="8fc61-223">TestConnectionCommand+PingReport, TestConnectionCommand+TraceRouteResult, Boolean, PingReply#MTUSize</span></span>

<span data-ttu-id="8fc61-224">Als u de **stille** para meter opgeeft, wordt een **Booleaanse** waarde geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="8fc61-224">If you specify the **Quiet** parameter, it returns a **Boolean** value.</span></span> <span data-ttu-id="8fc61-225">Als er meerdere verbindingen worden getest, wordt een matrix met **Boole** -waarden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="8fc61-225">If multiple connections are tested, an array of **Boolean** values is returned.</span></span> <span data-ttu-id="8fc61-226">Als dat niet het geval is, `Test-Connection` wordt er voor elke ping een **TestConnectionCommand + PingReport** -object geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="8fc61-226">Otherwise, `Test-Connection` returns a **TestConnectionCommand+PingReport** object for each ping.</span></span>

## <span data-ttu-id="8fc61-227">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="8fc61-227">NOTES</span></span>

## <span data-ttu-id="8fc61-228">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="8fc61-228">RELATED LINKS</span></span>

[<span data-ttu-id="8fc61-229">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="8fc61-229">Restart-Computer</span></span>](Restart-Computer.md)

[<span data-ttu-id="8fc61-230">Stop-computer</span><span class="sxs-lookup"><span data-stu-id="8fc61-230">Stop-Computer</span></span>](Stop-Computer.md)
