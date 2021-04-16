---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/test-connection?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-Connection
ms.openlocfilehash: f859ed0fd704ccdaf2561db9c952cbada88f18d8
ms.sourcegitcommit: 366304d096c1caf52f0e17962f6ed23d20f86e7b
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/16/2021
ms.locfileid: "107543760"
---
# <span data-ttu-id="50b5f-102">Test-Connection</span><span class="sxs-lookup"><span data-stu-id="50b5f-102">Test-Connection</span></span>

## <span data-ttu-id="50b5f-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="50b5f-103">SYNOPSIS</span></span>
<span data-ttu-id="50b5f-104">VERZENDT ICMP-echoaanvraagpakketten of pings naar een of meer computers.</span><span class="sxs-lookup"><span data-stu-id="50b5f-104">Sends ICMP echo request packets, or pings, to one or more computers.</span></span>

## <span data-ttu-id="50b5f-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="50b5f-105">SYNTAX</span></span>

### <span data-ttu-id="50b5f-106">DefaultPing (standaard)</span><span class="sxs-lookup"><span data-stu-id="50b5f-106">DefaultPing (Default)</span></span>

```
Test-Connection [-TargetName] <string[]> [-Ping] [-IPv4] [-IPv6] [-ResolveDestination]
 [-Source <string>] [-MaxHops <int>] [-Count <int>] [-Delay <int>] [-BufferSize <int>]
 [-DontFragment] [-TimeoutSeconds <int>] [-Quiet] [<CommonParameters>]
```

### <span data-ttu-id="50b5f-107">RepeatPing</span><span class="sxs-lookup"><span data-stu-id="50b5f-107">RepeatPing</span></span>

```
Test-Connection [-TargetName] <string[]> -Repeat [-Ping] [-IPv4] [-IPv6] [-ResolveDestination]
 [-Source <string>] [-MaxHops <int>] [-Delay <int>] [-BufferSize <int>] [-DontFragment]
 [-TimeoutSeconds <int>] [-Quiet] [<CommonParameters>]
```

### <span data-ttu-id="50b5f-108">MtuSizeDetect</span><span class="sxs-lookup"><span data-stu-id="50b5f-108">MtuSizeDetect</span></span>

```
Test-Connection [-TargetName] <string[]> -MtuSize [-IPv4] [-IPv6] [-ResolveDestination]
 [-TimeoutSeconds <int>] [-Quiet] [<CommonParameters>]
```

### <span data-ttu-id="50b5f-109">Traceroute</span><span class="sxs-lookup"><span data-stu-id="50b5f-109">TraceRoute</span></span>

```
Test-Connection [-TargetName] <string[]> -Traceroute [-IPv4] [-IPv6] [-ResolveDestination]
 [-Source <string>] [-MaxHops <int>] [-TimeoutSeconds <int>] [-Quiet] [<CommonParameters>]
```

### <span data-ttu-id="50b5f-110">TcpPort</span><span class="sxs-lookup"><span data-stu-id="50b5f-110">TcpPort</span></span>

```
Test-Connection [-TargetName] <string[]> -TcpPort <int> [-IPv4] [-IPv6] [-ResolveDestination]
 [-Source <string>] [-TimeoutSeconds <int>] [-Quiet] [<CommonParameters>]
```

## <span data-ttu-id="50b5f-111">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="50b5f-111">DESCRIPTION</span></span>

<span data-ttu-id="50b5f-112">De `Test-Connection` cmdlet verzendt Internet Control Message Protocol (ICMP) echoaanvraagpakketten, of pings, naar een of meer externe computers en retourneert de antwoorden op de echoreactie.</span><span class="sxs-lookup"><span data-stu-id="50b5f-112">The `Test-Connection` cmdlet sends Internet Control Message Protocol (ICMP) echo request packets, or pings, to one or more remote computers and returns the echo response replies.</span></span> <span data-ttu-id="50b5f-113">U kunt deze cmdlet gebruiken om te bepalen of er contact kan worden gemaakt met een bepaalde computer via een IP-netwerk.</span><span class="sxs-lookup"><span data-stu-id="50b5f-113">You can use this cmdlet to determine whether a particular computer can be contacted across an IP network.</span></span>

<span data-ttu-id="50b5f-114">U kunt de parameters van gebruiken om zowel de verzendende als ontvangende computers op te geven, de opdracht uit te voeren als achtergrondopdracht, een time-out en aantal pings in te stellen en de verbinding en verificatie `Test-Connection` te configureren.</span><span class="sxs-lookup"><span data-stu-id="50b5f-114">You can use the parameters of `Test-Connection` to specify both the sending and receiving computers, to run the command as a background job, to set a time-out and number of pings, and to configure the connection and authentication.</span></span>

<span data-ttu-id="50b5f-115">In tegenstelling tot de **bekende ping** opdracht `Test-Connection` retourneert een **TestConnectionCommand + PingStatus-object** dat u kunt onderzoeken in PowerShell.</span><span class="sxs-lookup"><span data-stu-id="50b5f-115">Unlike the familiar **ping** command, `Test-Connection` returns a **TestConnectionCommand+PingStatus** object that you can investigate in PowerShell.</span></span> <span data-ttu-id="50b5f-116">De **parameter Quiet** retourneert een **Booleaanse waarde** in een **System.Boolean-object** voor elke geteste verbinding.</span><span class="sxs-lookup"><span data-stu-id="50b5f-116">The **Quiet** parameter returns a **Boolean** value in a **System.Boolean** object for each tested connection.</span></span> <span data-ttu-id="50b5f-117">Als meerdere verbindingen worden getest, wordt een matrix met **Booleaanse** waarden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="50b5f-117">If multiple connections are tested, an array of **Boolean** values is returned.</span></span>

## <span data-ttu-id="50b5f-118">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="50b5f-118">EXAMPLES</span></span>

### <span data-ttu-id="50b5f-119">Voorbeeld 1: Echoaanvragen verzenden naar een externe computer</span><span class="sxs-lookup"><span data-stu-id="50b5f-119">Example 1: Send echo requests to a remote computer</span></span>

<span data-ttu-id="50b5f-120">In dit voorbeeld verzendt echoaanvraagpakketten van de lokale computer naar de computer Server01.</span><span class="sxs-lookup"><span data-stu-id="50b5f-120">This example sends echo request packets from the local computer to the Server01 computer.</span></span>

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

<span data-ttu-id="50b5f-121">`Test-Connection` gebruikt de **TargetName** parameter opgeven voor de Server01-computer.</span><span class="sxs-lookup"><span data-stu-id="50b5f-121">`Test-Connection` uses the **TargetName** parameter to specify the Server01 computer.</span></span> <span data-ttu-id="50b5f-122">De **IPv4** parameter geeft u het protocol voor de test.</span><span class="sxs-lookup"><span data-stu-id="50b5f-122">The **IPv4** parameter specifies the protocol for the test.</span></span>

<span data-ttu-id="50b5f-123">Er wordt een **reeks TestConnectionCommand+PingStatus-objecten** verzonden naar de uitvoerstroom, één object per pingantwoord van de doelmachine.</span><span class="sxs-lookup"><span data-stu-id="50b5f-123">A series of **TestConnectionCommand+PingStatus** objects are sent to the output stream, one object per ping reply from the target machine.</span></span>

### <span data-ttu-id="50b5f-124">Voorbeeld 2: Echoaanvragen verzenden naar verschillende computers</span><span class="sxs-lookup"><span data-stu-id="50b5f-124">Example 2: Send echo requests to several computers</span></span>

<span data-ttu-id="50b5f-125">In dit voorbeeld worden pings vanaf de lokale computer naar verschillende externe computers verzendt.</span><span class="sxs-lookup"><span data-stu-id="50b5f-125">This example sends pings from the local computer to several remote computers.</span></span>

```powershell
Test-Connection -TargetName Server01, Server02, Server12
```

### <span data-ttu-id="50b5f-126">Voorbeeld 3: Parameters gebruiken om de testopdracht aan te passen</span><span class="sxs-lookup"><span data-stu-id="50b5f-126">Example 3: Use parameters to customize the test command</span></span>

<span data-ttu-id="50b5f-127">In dit voorbeeld worden de parameters van gebruikt `Test-Connection` om de opdracht aan te passen.</span><span class="sxs-lookup"><span data-stu-id="50b5f-127">This example uses the parameters of `Test-Connection` to customize the command.</span></span> <span data-ttu-id="50b5f-128">De lokale computer verzendt een pingtest naar een externe computer.</span><span class="sxs-lookup"><span data-stu-id="50b5f-128">The local computer sends a ping test to a remote computer.</span></span>

```powershell
Test-Connection -TargetName Server01 -Count 3 -Delay 2 -MaxHops 255 -BufferSize 256
```

<span data-ttu-id="50b5f-129">`Test-Connection` gebruikt de **TargetName** parameter server01 opgeven.</span><span class="sxs-lookup"><span data-stu-id="50b5f-129">`Test-Connection` uses the **TargetName** parameter to specify Server01.</span></span> <span data-ttu-id="50b5f-130">De **aantal** parameter geeft u drie pings worden verzonden naar de server01 computer met een **vertraging** van 2 seconden intervallen.</span><span class="sxs-lookup"><span data-stu-id="50b5f-130">The **Count** parameter specifies three pings are sent to the Server01 computer with a **Delay** of 2-second intervals.</span></span>

<span data-ttu-id="50b5f-131">U kunt deze opties gebruiken wanneer het ping-antwoord naar verwachting langer duurt dan normaal, vanwege een groot aantal hops of een netwerkvoorwaarde met veel verkeer.</span><span class="sxs-lookup"><span data-stu-id="50b5f-131">You might use these options when the ping response is expected to take longer than usual, either because of an extended number of hops or a high-traffic network condition.</span></span>

### <span data-ttu-id="50b5f-132">Voorbeeld 4: Een test uitvoeren als achtergrond job</span><span class="sxs-lookup"><span data-stu-id="50b5f-132">Example 4: Run a test as a background job</span></span>

<span data-ttu-id="50b5f-133">In dit voorbeeld ziet u hoe u een opdracht `Test-Connection` kunt uitvoeren als een PowerShell-achtergrondopdracht.</span><span class="sxs-lookup"><span data-stu-id="50b5f-133">This example shows how to run a `Test-Connection` command as a PowerShell background job.</span></span>

```powershell
$job = Start-Job -ScriptBlock { Test-Connection -TargetName (Get-Content -Path "Servers.txt") }
$Results = Receive-Job $job -Wait
```

<span data-ttu-id="50b5f-134">De `Start-Job` opdracht gebruikt de `Test-Connection` cmdlet om veel computers in een onderneming te pingen.</span><span class="sxs-lookup"><span data-stu-id="50b5f-134">The `Start-Job` command uses the `Test-Connection` cmdlet to ping many computers in an enterprise.</span></span>
<span data-ttu-id="50b5f-135">De waarde van de **TargetName** parameter is een opdracht die een lijst met `Get-Content` computernamen uit het bestand `Servers.txt` leest.</span><span class="sxs-lookup"><span data-stu-id="50b5f-135">The value of the **TargetName** parameter is a `Get-Content` command that reads a list of computer names from the `Servers.txt` file.</span></span> <span data-ttu-id="50b5f-136">De opdracht gebruikt de cmdlet om de opdracht als achtergrond job uit te voeren en `Start-Job` slaat de taak op in de variabele `$job` .</span><span class="sxs-lookup"><span data-stu-id="50b5f-136">The command uses the `Start-Job` cmdlet to run the command as a background job and it saves the job in the `$job` variable.</span></span>

<span data-ttu-id="50b5f-137">De `Receive-Job` opdracht wordt geïnstrueerd totdat de taak is voltooid, waarna de resultaten worden op halen `-Wait` en in de variabele worden op `$Results` slaat.</span><span class="sxs-lookup"><span data-stu-id="50b5f-137">The `Receive-Job` command is instructed to `-Wait` until the job is completed, and then gets the results and stores them in the `$Results` variable.</span></span>

### <span data-ttu-id="50b5f-138">Voorbeeld 5: Alleen een sessie maken als een verbindingstest is geslaagd</span><span class="sxs-lookup"><span data-stu-id="50b5f-138">Example 5: Create a session only if a connection test succeeds</span></span>

<span data-ttu-id="50b5f-139">In dit voorbeeld maakt u een sessie op de computer Server01 alleen als ten minste een van de pings verzonden naar de computer slaagt.</span><span class="sxs-lookup"><span data-stu-id="50b5f-139">This example creates a session on the Server01 computer only if at least one of the pings sent to the computer succeeds.</span></span>

```powershell
if (Test-Connection -TargetName Server01 -Quiet) { New-PSSession -ComputerName Server01 }
```

<span data-ttu-id="50b5f-140">De `Test-Connection` cmdlet pingt de `Server01` computer, met de **parameter Quiet** opgegeven.</span><span class="sxs-lookup"><span data-stu-id="50b5f-140">The `Test-Connection` cmdlet pings the `Server01` computer, with the **Quiet** parameter provided.</span></span>
<span data-ttu-id="50b5f-141">De resulterende waarde is `$True` als een van de vier pings slaagt.</span><span class="sxs-lookup"><span data-stu-id="50b5f-141">The resulting value is `$True` if any of the four pings succeed.</span></span> <span data-ttu-id="50b5f-142">Als geen van de pings slaagt, is de waarde `$False` .</span><span class="sxs-lookup"><span data-stu-id="50b5f-142">If none of the pings succeed, the value is `$False`.</span></span>

<span data-ttu-id="50b5f-143">Als de `Test-Connection` opdracht een waarde van retourneert, gebruikt de opdracht de `$True` `New-PSSession` cmdlet om de **PSSession te maken.**</span><span class="sxs-lookup"><span data-stu-id="50b5f-143">If the `Test-Connection` command returns a value of `$True`, the command uses the `New-PSSession` cmdlet to create the **PSSession**.</span></span>

### <span data-ttu-id="50b5f-144">Voorbeeld 6: De parameter Traceroute gebruiken</span><span class="sxs-lookup"><span data-stu-id="50b5f-144">Example 6: Use the Traceroute parameter</span></span>

<span data-ttu-id="50b5f-145">De parameter **Traceroute,** geïntroduceerd in PowerShell 6.0, wijs een route toe tussen de lokale computer en de externe bestemming die u opgeeft met de parameter **TargetName.**</span><span class="sxs-lookup"><span data-stu-id="50b5f-145">Introduced in PowerShell 6.0, the **Traceroute** parameter maps a route between the local computer and the remote destination you specify with the **TargetName** parameter.</span></span>

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

<span data-ttu-id="50b5f-146">De `Test-Connection` opdracht wordt aangeroepen met de parameter **Traceroute.**</span><span class="sxs-lookup"><span data-stu-id="50b5f-146">The `Test-Connection` command is called with the **Traceroute** parameter.</span></span> <span data-ttu-id="50b5f-147">De resultaten, die objecten `[Microsoft.PowerShell.Commands.TestConnectionCommand+TraceStatus]` zijn, worden uitgevoerd naar de **uitvoerstroom Geslaagd.**</span><span class="sxs-lookup"><span data-stu-id="50b5f-147">The results, which are `[Microsoft.PowerShell.Commands.TestConnectionCommand+TraceStatus]` objects, are output to the **Success** output stream.</span></span>

## <span data-ttu-id="50b5f-148">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="50b5f-148">PARAMETERS</span></span>

### <span data-ttu-id="50b5f-149">-BufferSize</span><span class="sxs-lookup"><span data-stu-id="50b5f-149">-BufferSize</span></span>

<span data-ttu-id="50b5f-150">Hiermee geeft u de grootte, in bytes, van de buffer verzonden met deze opdracht.</span><span class="sxs-lookup"><span data-stu-id="50b5f-150">Specifies the size, in bytes, of the buffer sent with this command.</span></span> <span data-ttu-id="50b5f-151">De standaardwaarde is 32.</span><span class="sxs-lookup"><span data-stu-id="50b5f-151">The default value is 32.</span></span>

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

### <span data-ttu-id="50b5f-152">-Herhalen</span><span class="sxs-lookup"><span data-stu-id="50b5f-152">-Repeat</span></span>

<span data-ttu-id="50b5f-153">Zorgt ervoor dat de cmdlet continu ping-aanvragen verzendt.</span><span class="sxs-lookup"><span data-stu-id="50b5f-153">Causes the cmdlet to send ping requests continuously.</span></span> <span data-ttu-id="50b5f-154">Deze parameter kan niet worden gebruikt met de parameter **Count.**</span><span class="sxs-lookup"><span data-stu-id="50b5f-154">This parameter can't be used with the **Count** parameter.</span></span>

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

### <span data-ttu-id="50b5f-155">-Aantal</span><span class="sxs-lookup"><span data-stu-id="50b5f-155">-Count</span></span>

<span data-ttu-id="50b5f-156">Hiermee geeft u het aantal echoaanvragen te verzenden.</span><span class="sxs-lookup"><span data-stu-id="50b5f-156">Specifies the number of echo requests to send.</span></span> <span data-ttu-id="50b5f-157">De standaardwaarde is 4.</span><span class="sxs-lookup"><span data-stu-id="50b5f-157">The default value is 4.</span></span>

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

### <span data-ttu-id="50b5f-158">-Vertraging</span><span class="sxs-lookup"><span data-stu-id="50b5f-158">-Delay</span></span>

<span data-ttu-id="50b5f-159">Hiermee geeft u het interval tussen pings, in seconden.</span><span class="sxs-lookup"><span data-stu-id="50b5f-159">Specifies the interval between pings, in seconds.</span></span>

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

### <span data-ttu-id="50b5f-160">-DontFragment</span><span class="sxs-lookup"><span data-stu-id="50b5f-160">-DontFragment</span></span>

<span data-ttu-id="50b5f-161">Met deze parameter stelt u **de vlag Niet fragment in** de IP-header in.</span><span class="sxs-lookup"><span data-stu-id="50b5f-161">This parameter sets the **Don't Fragment** flag in the IP header.</span></span> <span data-ttu-id="50b5f-162">U kunt deze parameter gebruiken met de **parameter BufferSize** om de MTU-grootte van het pad te testen.</span><span class="sxs-lookup"><span data-stu-id="50b5f-162">You can use this parameter with the **BufferSize** parameter to test the Path MTU size.</span></span> <span data-ttu-id="50b5f-163">Zie het artikel Path MTU Discovery (MTU-detectiepad) op Wikipedia voor meer informatie over Path [MTU.](https://wikipedia.org/wiki/Path_MTU_Discovery)</span><span class="sxs-lookup"><span data-stu-id="50b5f-163">For more information about Path MTU, see the [Path MTU Discovery](https://wikipedia.org/wiki/Path_MTU_Discovery) article in wikipedia.</span></span>

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

### <span data-ttu-id="50b5f-164">-IPv4</span><span class="sxs-lookup"><span data-stu-id="50b5f-164">-IPv4</span></span>

<span data-ttu-id="50b5f-165">Dwingt de cmdlet om het IPv4-protocol voor de test te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="50b5f-165">Forces the cmdlet to use the IPv4 protocol for the test.</span></span>

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

### <span data-ttu-id="50b5f-166">-IPv6</span><span class="sxs-lookup"><span data-stu-id="50b5f-166">-IPv6</span></span>

<span data-ttu-id="50b5f-167">Dwingt de cmdlet om het IPv6-protocol voor de test te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="50b5f-167">Forces the cmdlet to use the IPv6 protocol for the test.</span></span>

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

### <span data-ttu-id="50b5f-168">-MaxHops</span><span class="sxs-lookup"><span data-stu-id="50b5f-168">-MaxHops</span></span>

<span data-ttu-id="50b5f-169">Hiermee stelt u het maximum aantal hops in dat een ICMP-aanvraagbericht kan worden verzonden.</span><span class="sxs-lookup"><span data-stu-id="50b5f-169">Sets the maximum number of hops that an ICMP request message can be sent.</span></span> <span data-ttu-id="50b5f-170">De standaardwaarde wordt bepaald door het besturingssysteem.</span><span class="sxs-lookup"><span data-stu-id="50b5f-170">The default value is controlled by the operating system.</span></span> <span data-ttu-id="50b5f-171">De standaardwaarde voor Windows 10 is 128 hops.</span><span class="sxs-lookup"><span data-stu-id="50b5f-171">The default value for Windows 10 is 128 hops.</span></span>

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

### <span data-ttu-id="50b5f-172">-Ping</span><span class="sxs-lookup"><span data-stu-id="50b5f-172">-Ping</span></span>

<span data-ttu-id="50b5f-173">Zorgt ervoor dat de cmdlet een ping-test uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="50b5f-173">Causes the cmdlet to do a ping test.</span></span> <span data-ttu-id="50b5f-174">Dit is de standaardmodus voor de `Test-Connection` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="50b5f-174">This is the default mode for the `Test-Connection` cmdlet.</span></span>

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

### <span data-ttu-id="50b5f-175">-Quiet</span><span class="sxs-lookup"><span data-stu-id="50b5f-175">-Quiet</span></span>

<span data-ttu-id="50b5f-176">De **parameter Quiet** retourneert een **Booleaanse** waarde.</span><span class="sxs-lookup"><span data-stu-id="50b5f-176">The **Quiet** parameter returns a **Boolean** value.</span></span> <span data-ttu-id="50b5f-177">Met deze parameter worden alle fouten onderdrukt.</span><span class="sxs-lookup"><span data-stu-id="50b5f-177">Using this parameter suppresses all errors.</span></span>

<span data-ttu-id="50b5f-178">Elke geteste verbinding retourneert een **Booleaanse** waarde.</span><span class="sxs-lookup"><span data-stu-id="50b5f-178">Each connection that's tested returns a **Boolean** value.</span></span> <span data-ttu-id="50b5f-179">Als de **parameter TargetName** meerdere computers opgeeft, wordt een matrix met **Booleaanse** waarden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="50b5f-179">If the **TargetName** parameter specifies multiple computers, an array of **Boolean** values is returned.</span></span>

<span data-ttu-id="50b5f-180">Als **een** ping naar een bepaald doel slaagt, `$True` wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="50b5f-180">If **any** ping to a given target succeeds, `$True` is returned.</span></span>

<span data-ttu-id="50b5f-181">Als **alle** pings naar een bepaald doel mislukken, `$False` wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="50b5f-181">If **all** pings to a given target fail, `$False` is returned.</span></span>

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

### <span data-ttu-id="50b5f-182">-ResolveDestination</span><span class="sxs-lookup"><span data-stu-id="50b5f-182">-ResolveDestination</span></span>

<span data-ttu-id="50b5f-183">Zorgt ervoor dat de cmdlet probeert om te lossen van de DNS-naam van het doel.</span><span class="sxs-lookup"><span data-stu-id="50b5f-183">Causes the cmdlet to attempt to resolve the DNS name of the target.</span></span> <span data-ttu-id="50b5f-184">Wanneer u deze gebruikt in combinatie met de parameter **Traceroute,** worden indien mogelijk ook de DNS-namen van alle tussenliggende hosts opgehaald.</span><span class="sxs-lookup"><span data-stu-id="50b5f-184">When used in conjunction with the **Traceroute** parameter, the DNS names of all intermediate hosts will also be retrieved, if possible.</span></span>

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

### <span data-ttu-id="50b5f-185">-Source</span><span class="sxs-lookup"><span data-stu-id="50b5f-185">-Source</span></span>

<span data-ttu-id="50b5f-186">Hiermee geeft u de namen van de computers waar de ping afkomstig is.</span><span class="sxs-lookup"><span data-stu-id="50b5f-186">Specifies the names of the computers where the ping originates.</span></span> <span data-ttu-id="50b5f-187">Voer een door komma's gescheiden lijst met computernamen in.</span><span class="sxs-lookup"><span data-stu-id="50b5f-187">Enter a comma-separated list of computer names.</span></span> <span data-ttu-id="50b5f-188">Standaard is dit de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="50b5f-188">The default is the local computer.</span></span>

> [!NOTE]
> <span data-ttu-id="50b5f-189">Deze parameter wordt niet ondersteund in PowerShell versie 6 en nieuwe versies.</span><span class="sxs-lookup"><span data-stu-id="50b5f-189">This parameter is not supported in PowerShell versions 6 and up.</span></span> <span data-ttu-id="50b5f-190">Het opgeven van deze parameter veroorzaakt een fout.</span><span class="sxs-lookup"><span data-stu-id="50b5f-190">Supplying this parameter causes an error.</span></span>

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

### <span data-ttu-id="50b5f-191">-TargetName</span><span class="sxs-lookup"><span data-stu-id="50b5f-191">-TargetName</span></span>

<span data-ttu-id="50b5f-192">Hiermee geeft u de computer(s) te testen.</span><span class="sxs-lookup"><span data-stu-id="50b5f-192">Specifies the computer(s) to test.</span></span> <span data-ttu-id="50b5f-193">Typ de computernamen of ip-adressen in IPv4- of IPv6-indeling.</span><span class="sxs-lookup"><span data-stu-id="50b5f-193">Type the computer names or type IP addresses in IPv4 or IPv6 format.</span></span>

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

### <span data-ttu-id="50b5f-194">-TimeoutSeconds</span><span class="sxs-lookup"><span data-stu-id="50b5f-194">-TimeoutSeconds</span></span>

<span data-ttu-id="50b5f-195">Hiermee stelt u de time-outwaarde voor de test in.</span><span class="sxs-lookup"><span data-stu-id="50b5f-195">Sets the timeout value for the test.</span></span> <span data-ttu-id="50b5f-196">De test mislukt als er geen antwoord wordt ontvangen voordat de time-out verloopt.</span><span class="sxs-lookup"><span data-stu-id="50b5f-196">The test fails if a response isn't received before the timeout expires.</span></span> <span data-ttu-id="50b5f-197">De standaardwaarde is vijf seconden.</span><span class="sxs-lookup"><span data-stu-id="50b5f-197">The default is five seconds.</span></span>

<span data-ttu-id="50b5f-198">Deze parameter is geïntroduceerd in PowerShell 6.0.</span><span class="sxs-lookup"><span data-stu-id="50b5f-198">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="50b5f-199">-Traceroute</span><span class="sxs-lookup"><span data-stu-id="50b5f-199">-Traceroute</span></span>

<span data-ttu-id="50b5f-200">Zorgt ervoor dat de cmdlet een traceroute-test moet uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="50b5f-200">Causes the cmdlet to do a traceroute test.</span></span> <span data-ttu-id="50b5f-201">Wanneer deze parameter wordt gebruikt, retourneert de cmdlet een `TestConnectionCommand+TraceStatus` -object.</span><span class="sxs-lookup"><span data-stu-id="50b5f-201">When this parameter is used, the cmdlet returns a `TestConnectionCommand+TraceStatus` object.</span></span>

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

### <span data-ttu-id="50b5f-202">-MtuSize</span><span class="sxs-lookup"><span data-stu-id="50b5f-202">-MtuSize</span></span>

<span data-ttu-id="50b5f-203">Deze parameter wordt gebruikt om de MTU-grootte van het pad te ontdekken.</span><span class="sxs-lookup"><span data-stu-id="50b5f-203">This parameter is used to discover the Path MTU size.</span></span> <span data-ttu-id="50b5f-204">De cmdlet retourneert een **PingReply#MTUSize-object** dat de MTU-padgrootte naar het doel bevat.</span><span class="sxs-lookup"><span data-stu-id="50b5f-204">The cmdlet returns a **PingReply#MTUSize** object that contains the Path MTU size to the target.</span></span> <span data-ttu-id="50b5f-205">Zie het artikel Path MTU Discovery (MTU-detectiepad) op Wikipedia voor meer informatie over Path [MTU.](https://wikipedia.org/wiki/Path_MTU_Discovery)</span><span class="sxs-lookup"><span data-stu-id="50b5f-205">For more information about Path MTU, see the [Path MTU Discovery](https://wikipedia.org/wiki/Path_MTU_Discovery) article in wikipedia.</span></span>

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

### <span data-ttu-id="50b5f-206">-TcpPort</span><span class="sxs-lookup"><span data-stu-id="50b5f-206">-TcpPort</span></span>

<span data-ttu-id="50b5f-207">Hiermee geeft u het TCP-poortnummer op het doel dat moet worden gebruikt in de TCP-verbindingstest.</span><span class="sxs-lookup"><span data-stu-id="50b5f-207">Specifies the TCP port number on the target to be used in the TCP connection test.</span></span> <span data-ttu-id="50b5f-208">De cmdlet probeert een TCP-verbinding te maken met de opgegeven poort op het doel.</span><span class="sxs-lookup"><span data-stu-id="50b5f-208">The cmdlet will attempt to make a TCP connection to the specified port on the target.</span></span>

<span data-ttu-id="50b5f-209">Als er een verbinding kan worden gemaakt, `$True` wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="50b5f-209">If a connection can be made, `$True` will be returned.</span></span>

<span data-ttu-id="50b5f-210">Als er geen verbinding kan worden gemaakt, `$False` wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="50b5f-210">If a connection cannot be made, `$False` will be returned.</span></span>

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

### <span data-ttu-id="50b5f-211">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="50b5f-211">CommonParameters</span></span>

<span data-ttu-id="50b5f-212">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="50b5f-212">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="50b5f-213">Zie voor meer informatie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="50b5f-213">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="50b5f-214">INVOER</span><span class="sxs-lookup"><span data-stu-id="50b5f-214">INPUTS</span></span>

### <span data-ttu-id="50b5f-215">Geen</span><span class="sxs-lookup"><span data-stu-id="50b5f-215">None</span></span>

<span data-ttu-id="50b5f-216">U kunt geen invoer doorspijpen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="50b5f-216">You can't pipe input to this cmdlet.</span></span>

## <span data-ttu-id="50b5f-217">UITVOER</span><span class="sxs-lookup"><span data-stu-id="50b5f-217">OUTPUTS</span></span>

### <span data-ttu-id="50b5f-218">TestConnectionCommand+PingStatus, TestConnectionCommand+TraceStatus, Boolean, TestConnectionCommand+PingMtuStatus</span><span class="sxs-lookup"><span data-stu-id="50b5f-218">TestConnectionCommand+PingStatus, TestConnectionCommand+TraceStatus, Boolean, TestConnectionCommand+PingMtuStatus</span></span>

<span data-ttu-id="50b5f-219">Retourneert `Test-Connection` standaard een **TestConnectionCommand +PingStatus-object** voor elk pingantwoord.</span><span class="sxs-lookup"><span data-stu-id="50b5f-219">By default, `Test-Connection` returns a **TestConnectionCommand+PingStatus** object for each ping reply.</span></span>

<span data-ttu-id="50b5f-220">Als u de **parameter Traceroute opgeeft,** retourneert de cmdlet een **TestConnectionCommand+TraceStatus-object** voor elk pingantwoord langs de route.</span><span class="sxs-lookup"><span data-stu-id="50b5f-220">If you specify the **Traceroute** parameter, the cmdlet will return a **TestConnectionCommand+TraceStatus** object for each ping reply along the route.</span></span>

<span data-ttu-id="50b5f-221">Als u de **parameters Quiet** of **TcpPort opgeeft,** wordt een **Booleaanse waarde** retourneert.</span><span class="sxs-lookup"><span data-stu-id="50b5f-221">If you specify the **Quiet** or **TcpPort** parameters, it returns a **Boolean** value.</span></span> <span data-ttu-id="50b5f-222">Als meerdere verbindingen worden getest, wordt een matrix met **Booleaanse** waarden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="50b5f-222">If multiple connections are tested, an array of **Boolean** values is returned.</span></span>

## <span data-ttu-id="50b5f-223">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="50b5f-223">NOTES</span></span>

## <span data-ttu-id="50b5f-224">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="50b5f-224">RELATED LINKS</span></span>

[<span data-ttu-id="50b5f-225">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="50b5f-225">Restart-Computer</span></span>](Restart-Computer.md)

[<span data-ttu-id="50b5f-226">Stop-Computer</span><span class="sxs-lookup"><span data-stu-id="50b5f-226">Stop-Computer</span></span>](Stop-Computer.md)

