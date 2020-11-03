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
# <span data-ttu-id="64ea1-103">Test-Connection</span><span class="sxs-lookup"><span data-stu-id="64ea1-103">Test-Connection</span></span>

## <span data-ttu-id="64ea1-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="64ea1-104">SYNOPSIS</span></span>
<span data-ttu-id="64ea1-105">Verzendt ICMP echo aanvraag pakketten of pings naar een of meer computers.</span><span class="sxs-lookup"><span data-stu-id="64ea1-105">Sends ICMP echo request packets, or pings, to one or more computers.</span></span>

## <span data-ttu-id="64ea1-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="64ea1-106">SYNTAX</span></span>

### <span data-ttu-id="64ea1-107">Standaard (standaard instelling)</span><span class="sxs-lookup"><span data-stu-id="64ea1-107">Default (Default)</span></span>

```
Test-Connection [-AsJob] [-DcomAuthentication <AuthenticationLevel>] [-WsmanAuthentication <String>]
 [-Protocol <String>] [-BufferSize <Int32>] [-ComputerName] <String[]> [-Count <Int32>]
 [-Impersonation <ImpersonationLevel>] [-ThrottleLimit <Int32>] [-TimeToLive <Int32>]
 [-Delay <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="64ea1-108">Bron</span><span class="sxs-lookup"><span data-stu-id="64ea1-108">Source</span></span>

```
Test-Connection [-AsJob] [-DcomAuthentication <AuthenticationLevel>] [-WsmanAuthentication <String>]
 [-Protocol <String>] [-BufferSize <Int32>] [-ComputerName] <String[]> [-Count <Int32>]
 [-Credential <PSCredential>] [-Source] <String[]> [-Impersonation <ImpersonationLevel>]
 [-ThrottleLimit <Int32>] [-TimeToLive <Int32>] [-Delay <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="64ea1-109">Quiet</span><span class="sxs-lookup"><span data-stu-id="64ea1-109">Quiet</span></span>

```
Test-Connection [-DcomAuthentication <AuthenticationLevel>] [-WsmanAuthentication <String>]
 [-Protocol <String>] [-BufferSize <Int32>] [-ComputerName] <String[]> [-Count <Int32>]
 [-Impersonation <ImpersonationLevel>] [-TimeToLive <Int32>] [-Delay <Int32>] [-Quiet]
 [<CommonParameters>]
```

## <span data-ttu-id="64ea1-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="64ea1-110">DESCRIPTION</span></span>

<span data-ttu-id="64ea1-111">De `Test-Connection` cmdlet stuurt Internet Control Message Protocol (ICMP) Echo aanvraag pakketten of pings naar een of meer externe computers en retourneert de antwoorden op de echo reactie.</span><span class="sxs-lookup"><span data-stu-id="64ea1-111">The `Test-Connection` cmdlet sends Internet Control Message Protocol (ICMP) echo request packets, or pings, to one or more remote computers and returns the echo response replies.</span></span> <span data-ttu-id="64ea1-112">U kunt deze cmdlet gebruiken om te bepalen of er verbinding kan worden gemaakt met een bepaalde computer via een IP-netwerk.</span><span class="sxs-lookup"><span data-stu-id="64ea1-112">You can use this cmdlet to determine whether a particular computer can be contacted across an IP network.</span></span>

<span data-ttu-id="64ea1-113">U kunt de para meters van gebruiken `Test-Connection` om zowel de verzendende als ontvangende computers op te geven om de opdracht als achtergrond taak uit te voeren, om een time-out en een aantal pings in te stellen en om de verbinding en verificatie te configureren.</span><span class="sxs-lookup"><span data-stu-id="64ea1-113">You can use the parameters of `Test-Connection` to specify both the sending and receiving computers, to run the command as a background job, to set a time-out and number of pings, and to configure the connection and authentication.</span></span>

<span data-ttu-id="64ea1-114">In tegens telling tot de bekende **ping** -opdracht `Test-Connection` retourneert een **Win32_PingStatus** -object dat u kunt onderzoeken in Power shell.</span><span class="sxs-lookup"><span data-stu-id="64ea1-114">Unlike the familiar **ping** command, `Test-Connection` returns a **Win32_PingStatus** object that you can investigate in PowerShell.</span></span> <span data-ttu-id="64ea1-115">De **stille** para meter retourneert een **Boole** -waarde in een object **System. Boolean** voor elke geteste verbinding.</span><span class="sxs-lookup"><span data-stu-id="64ea1-115">The **Quiet** parameter returns a **Boolean** value in a **System.Boolean** object for each tested connection.</span></span> <span data-ttu-id="64ea1-116">Als er meerdere verbindingen worden getest, wordt een matrix met **Boole** -waarden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="64ea1-116">If multiple connections are tested, an array of **Boolean** values is returned.</span></span>

## <span data-ttu-id="64ea1-117">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="64ea1-117">EXAMPLES</span></span>

### <span data-ttu-id="64ea1-118">Voor beeld 1: ECHO aanvragen verzenden naar een externe computer</span><span class="sxs-lookup"><span data-stu-id="64ea1-118">Example 1: Send echo requests to a remote computer</span></span>

<span data-ttu-id="64ea1-119">In dit voor beeld worden ECHO aanvraag pakketten van de lokale computer verzonden naar de Server01-computer.</span><span class="sxs-lookup"><span data-stu-id="64ea1-119">This example sends echo request packets from the local computer to the Server01 computer.</span></span>

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

<span data-ttu-id="64ea1-120">`Test-Connection` maakt gebruik van de para meter **ComputerName** om de Server01-computer op te geven.</span><span class="sxs-lookup"><span data-stu-id="64ea1-120">`Test-Connection` uses the **ComputerName** parameter to specify the Server01 computer.</span></span>

### <span data-ttu-id="64ea1-121">Voor beeld 2: ECHO aanvragen verzenden naar verschillende computers</span><span class="sxs-lookup"><span data-stu-id="64ea1-121">Example 2: Send echo requests to several computers</span></span>

<span data-ttu-id="64ea1-122">In dit voor beeld worden pings van de lokale computer naar verschillende externe computers verzonden.</span><span class="sxs-lookup"><span data-stu-id="64ea1-122">This example sends pings from the local computer to several remote computers.</span></span>

```powershell
Test-Connection -ComputerName Server01, Server02, Server12
```

### <span data-ttu-id="64ea1-123">Voor beeld 3: ECHO aanvragen van verschillende computers verzenden naar een computer</span><span class="sxs-lookup"><span data-stu-id="64ea1-123">Example 3: Send echo requests from several computers to a computer</span></span>

<span data-ttu-id="64ea1-124">In dit voor beeld worden pings van verschillende bron computers verzonden naar één externe computer, Server01.</span><span class="sxs-lookup"><span data-stu-id="64ea1-124">This example sends pings from different source computers to a single remote computer, Server01.</span></span>

```powershell
Test-Connection -Source Server02, Server12, localhost -ComputerName Server01 -Credential Domain01\Admin01
```

<span data-ttu-id="64ea1-125">`Test-Connection` maakt gebruik van de para meter **Credential** om de referenties op te geven van een gebruiker die gemachtigd is om een ping-aanvraag van de bron computers te verzenden.</span><span class="sxs-lookup"><span data-stu-id="64ea1-125">`Test-Connection` uses the **Credential** parameter to specify the credentials of a user who has permission to send a ping request from the source computers.</span></span> <span data-ttu-id="64ea1-126">Gebruik deze opdracht indeling om de latentie van verbindingen vanaf meerdere punten te testen.</span><span class="sxs-lookup"><span data-stu-id="64ea1-126">Use this command format to test the latency of connections from multiple points.</span></span>

### <span data-ttu-id="64ea1-127">Voor beeld 4: para meters gebruiken om de test opdracht aan te passen</span><span class="sxs-lookup"><span data-stu-id="64ea1-127">Example 4: Use parameters to customize the test command</span></span>

<span data-ttu-id="64ea1-128">In dit voor beeld worden de para meters van gebruikt `Test-Connection` voor het aanpassen van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="64ea1-128">This example uses the parameters of `Test-Connection` to customize the command.</span></span> <span data-ttu-id="64ea1-129">De lokale computer verzendt een ping-test naar een externe computer.</span><span class="sxs-lookup"><span data-stu-id="64ea1-129">The local computer sends a ping test to a remote computer.</span></span>

```powershell
Test-Connection -ComputerName Server01 -Count 3 -Delay 2 -TTL 255 -BufferSize 256 -ThrottleLimit 32
```

<span data-ttu-id="64ea1-130">`Test-Connection` maakt gebruik van de para meter **ComputerName** om Server01 op te geven.</span><span class="sxs-lookup"><span data-stu-id="64ea1-130">`Test-Connection` uses the **ComputerName** parameter to specify Server01.</span></span> <span data-ttu-id="64ea1-131">De para meter **aantal** geeft aan dat drie pings worden verzonden naar de Server01-computer, met een **vertraging** van twee seconden intervallen.</span><span class="sxs-lookup"><span data-stu-id="64ea1-131">The **Count** parameter specifies three pings are sent to the Server01 computer with a **Delay** of 2-second intervals.</span></span>

<span data-ttu-id="64ea1-132">U kunt deze opties gebruiken wanneer het ping-antwoord naar verwachting langer duurt dan normaal, ofwel vanwege een uitgebreid aantal hops of een netwerk toestand met een hoog verkeer.</span><span class="sxs-lookup"><span data-stu-id="64ea1-132">You might use these options when the ping response is expected to take longer than usual, either because of an extended number of hops or a high-traffic network condition.</span></span>

### <span data-ttu-id="64ea1-133">Voor beeld 5: een test uitvoeren als een achtergrond taak</span><span class="sxs-lookup"><span data-stu-id="64ea1-133">Example 5: Run a test as a background job</span></span>

<span data-ttu-id="64ea1-134">In dit voor beeld ziet u hoe u een `Test-Connection` opdracht uitvoert als een Power shell-achtergrond taak.</span><span class="sxs-lookup"><span data-stu-id="64ea1-134">This example shows how to run a `Test-Connection` command as a PowerShell background job.</span></span>

```powershell
$job = Test-Connection -ComputerName (Get-Content Servers.txt) -AsJob
if ($job.JobStateInfo.State -ne "Running") {$Results = Receive-Job $job}
```

<span data-ttu-id="64ea1-135">De `Test-Connection` opdracht pingt veel computers in een onderneming.</span><span class="sxs-lookup"><span data-stu-id="64ea1-135">The `Test-Connection` command pings many computers in an enterprise.</span></span> <span data-ttu-id="64ea1-136">De waarde van de para meter **ComputerName** is een `Get-Content` opdracht die een lijst met computer namen uit de heeft gelezen `Servers.txt file` .</span><span class="sxs-lookup"><span data-stu-id="64ea1-136">The value of the **ComputerName** parameter is a `Get-Content` command that reads a list of computer names from the `Servers.txt file`.</span></span> <span data-ttu-id="64ea1-137">De opdracht gebruikt de para meter **AsJob** om de opdracht uit te voeren als een achtergrond taak en de taak wordt opgeslagen in de `$job` variabele.</span><span class="sxs-lookup"><span data-stu-id="64ea1-137">The command uses the **AsJob** parameter to run the command as a background job and it saves the job in the `$job` variable.</span></span>

<span data-ttu-id="64ea1-138">De `if` opdracht controleert of de taak nog niet wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="64ea1-138">The `if` command checks to see that the job isn't still running.</span></span> <span data-ttu-id="64ea1-139">Als de taak niet wordt uitgevoerd, `Receive-Job` worden de resultaten opgehaald en opgeslagen in de `$Results` variabele.</span><span class="sxs-lookup"><span data-stu-id="64ea1-139">If the job isn't running, `Receive-Job` gets the results and stores them in the `$Results` variable.</span></span>

### <span data-ttu-id="64ea1-140">Voor beeld 6: een externe computer met referenties pingen</span><span class="sxs-lookup"><span data-stu-id="64ea1-140">Example 6: Ping a remote computer with credentials</span></span>

<span data-ttu-id="64ea1-141">Met deze opdracht wordt de `Test-Connection` cmdlet gebruikt voor het pingen van een externe computer.</span><span class="sxs-lookup"><span data-stu-id="64ea1-141">This command uses the `Test-Connection` cmdlet to ping a remote computer.</span></span>

```powershell
Test-Connection Server55 -Credential Domain55\User01 -Impersonation Identify
```

<span data-ttu-id="64ea1-142">De opdracht gebruikt de para meter **Credential** om een gebruikers account op te geven dat is gemachtigd voor het pingen van de externe computer en de **imitatie** parameter om het imitatie niveau te wijzigen in **identificeren**.</span><span class="sxs-lookup"><span data-stu-id="64ea1-142">The command uses the **Credential** parameter to specify a user account that has permission to ping the remote computer and the **Impersonation** parameter to change the impersonation level to **Identify**.</span></span>

### <span data-ttu-id="64ea1-143">Voor beeld 7: een sessie alleen maken als de verbindings test is geslaagd</span><span class="sxs-lookup"><span data-stu-id="64ea1-143">Example 7: Create a session only if a connection test succeeds</span></span>

<span data-ttu-id="64ea1-144">In dit voor beeld wordt alleen een sessie op de Server01-computer gemaakt als ten minste één van de pings die naar de computer worden verzonden, slaagt.</span><span class="sxs-lookup"><span data-stu-id="64ea1-144">This example creates a session on the Server01 computer only if at least one of the pings sent to the computer succeeds.</span></span>

```powershell
if (Test-Connection -ComputerName Server01 -Quiet) {New-PSSession Server01}
```

<span data-ttu-id="64ea1-145">De `if` opdracht gebruikt de `Test-Connection` cmdlet om de Server01-computer te pingen.</span><span class="sxs-lookup"><span data-stu-id="64ea1-145">The `if` command uses the `Test-Connection` cmdlet to ping the Server01 computer.</span></span> <span data-ttu-id="64ea1-146">De opdracht maakt gebruik van de **stille** para meter, waarmee een **Booleaanse** waarde wordt geretourneerd in plaats van een **Win32_PingStatus** -object.</span><span class="sxs-lookup"><span data-stu-id="64ea1-146">The command uses the **Quiet** parameter, which returns a **Boolean** value, instead of a **Win32_PingStatus** object.</span></span> <span data-ttu-id="64ea1-147">De waarde is `$True` als een van de vier pings slaagt en, anders, `$False` .</span><span class="sxs-lookup"><span data-stu-id="64ea1-147">The value is `$True` if any of the four pings succeed and is, otherwise, `$False`.</span></span>

<span data-ttu-id="64ea1-148">Als de `Test-Connection` opdracht een waarde retourneert `$True` , gebruikt de opdracht de `New-PSSession` cmdlet om de **PSSession** te maken.</span><span class="sxs-lookup"><span data-stu-id="64ea1-148">If the `Test-Connection` command returns a value of `$True`, the command uses the `New-PSSession` cmdlet to create the **PSSession**.</span></span>

## <span data-ttu-id="64ea1-149">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="64ea1-149">PARAMETERS</span></span>

### <span data-ttu-id="64ea1-150">-AsJob</span><span class="sxs-lookup"><span data-stu-id="64ea1-150">-AsJob</span></span>

<span data-ttu-id="64ea1-151">Geeft aan dat deze cmdlet wordt uitgevoerd als een achtergrond taak.</span><span class="sxs-lookup"><span data-stu-id="64ea1-151">Indicates that this cmdlet runs as a background job.</span></span>

<span data-ttu-id="64ea1-152">Als u deze para meter wilt gebruiken, moeten de lokale en externe computers worden geconfigureerd voor externe toegang en, onder Windows Vista en latere versies van het Windows-besturings systeem, moet u Power shell openen met de optie **als administrator uitvoeren** .</span><span class="sxs-lookup"><span data-stu-id="64ea1-152">To use this parameter, the local and remote computers must be configured for remoting and, on Windows Vista and later versions of the Windows operating system, you must open PowerShell by using the **Run as administrator** option.</span></span> <span data-ttu-id="64ea1-153">Zie [about_Remote_Requirements](../microsoft.powershell.core/about/about_remote_requirements.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="64ea1-153">For more information, see [about_Remote_Requirements](../microsoft.powershell.core/about/about_remote_requirements.md).</span></span>

<span data-ttu-id="64ea1-154">Wanneer u de para meter **AsJob** opgeeft, retourneert de opdracht direct een object dat de achtergrond taak vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="64ea1-154">When you specify the **AsJob** parameter, the command immediately returns an object that represents the background job.</span></span> <span data-ttu-id="64ea1-155">U kunt in de sessie blijven werken terwijl de taak is voltooid.</span><span class="sxs-lookup"><span data-stu-id="64ea1-155">You can continue to work in the session while the job finishes.</span></span> <span data-ttu-id="64ea1-156">De taak wordt gemaakt op de lokale computer en de resultaten van externe computers worden automatisch geretourneerd naar de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="64ea1-156">The job is created on the local computer and the results from remote computers are automatically returned to the local computer.</span></span> <span data-ttu-id="64ea1-157">Gebruik de cmdlet om de taak resultaten te verkrijgen `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="64ea1-157">To get the job results, use the `Receive-Job` cmdlet.</span></span>

<span data-ttu-id="64ea1-158">Zie [about_Jobs](../Microsoft.PowerShell.Core/About/about_jobs.md) en [about_Remote_Jobs](../Microsoft.PowerShell.Core/About/about_remote_jobs.md)voor meer informatie over Power shell-achtergrond taken.</span><span class="sxs-lookup"><span data-stu-id="64ea1-158">For more information about PowerShell background jobs, see [about_Jobs](../Microsoft.PowerShell.Core/About/about_jobs.md) and [about_Remote_Jobs](../Microsoft.PowerShell.Core/About/about_remote_jobs.md).</span></span>

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

### <span data-ttu-id="64ea1-159">-BufferSize</span><span class="sxs-lookup"><span data-stu-id="64ea1-159">-BufferSize</span></span>

<span data-ttu-id="64ea1-160">Hiermee geeft u de grootte, in bytes, van de buffer die met deze opdracht wordt verzonden.</span><span class="sxs-lookup"><span data-stu-id="64ea1-160">Specifies the size, in bytes, of the buffer sent with this command.</span></span> <span data-ttu-id="64ea1-161">De standaard waarde is 32.</span><span class="sxs-lookup"><span data-stu-id="64ea1-161">The default value is 32.</span></span>

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

### <span data-ttu-id="64ea1-162">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="64ea1-162">-ComputerName</span></span>

<span data-ttu-id="64ea1-163">Hiermee geeft u de computers op die moeten worden gepingd.</span><span class="sxs-lookup"><span data-stu-id="64ea1-163">Specifies the computers to ping.</span></span> <span data-ttu-id="64ea1-164">Typ de computer namen of typ de IP-adressen in de IPv4-of IPv6-indeling.</span><span class="sxs-lookup"><span data-stu-id="64ea1-164">Type the computer names or type IP addresses in IPv4 or IPv6 format.</span></span> <span data-ttu-id="64ea1-165">Joker tekens zijn niet toegestaan.</span><span class="sxs-lookup"><span data-stu-id="64ea1-165">Wildcard characters are not permitted.</span></span> <span data-ttu-id="64ea1-166">Deze parameter is vereist.</span><span class="sxs-lookup"><span data-stu-id="64ea1-166">This parameter is required.</span></span>

<span data-ttu-id="64ea1-167">Deze para meter is niet afhankelijk van externe communicatie met Power shell.</span><span class="sxs-lookup"><span data-stu-id="64ea1-167">This parameter doesn't rely on PowerShell remoting.</span></span> <span data-ttu-id="64ea1-168">U kunt de para meter **ComputerName** ook gebruiken als uw computer niet is geconfigureerd om externe opdrachten uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="64ea1-168">You can use the **ComputerName** parameter even if your computer isn't configured to run remote commands.</span></span>

> [!NOTE]
> <span data-ttu-id="64ea1-169">De naam van de para meter **ComputerName** wordt gewijzigd in **TargetName** in Power shell 6,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="64ea1-169">The **ComputerName** parameter is renamed to **TargetName** in PowerShell 6.0 and above.</span></span>

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

### <span data-ttu-id="64ea1-170">-Aantal</span><span class="sxs-lookup"><span data-stu-id="64ea1-170">-Count</span></span>

<span data-ttu-id="64ea1-171">Hiermee geeft u het aantal ECHO aanvragen dat moet worden verzonden.</span><span class="sxs-lookup"><span data-stu-id="64ea1-171">Specifies the number of echo requests to send.</span></span> <span data-ttu-id="64ea1-172">De standaardwaarde is 4.</span><span class="sxs-lookup"><span data-stu-id="64ea1-172">The default value is 4.</span></span>

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

### <span data-ttu-id="64ea1-173">-Credential</span><span class="sxs-lookup"><span data-stu-id="64ea1-173">-Credential</span></span>

<span data-ttu-id="64ea1-174">Hiermee geeft u een gebruikers account op dat gemachtigd is om een ping-aanvraag van de bron computer te verzenden.</span><span class="sxs-lookup"><span data-stu-id="64ea1-174">Specifies a user account that has permission to send a ping request from the source computer.</span></span> <span data-ttu-id="64ea1-175">Typ een gebruikers naam, zoals gebruiker01 of Domain01\User01, of voer een **PSCredential** -object in, bijvoorbeeld een van de `Get-Credential` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="64ea1-175">Type a user name, such as User01 or Domain01\User01, or enter a **PSCredential** object, such as one from the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="64ea1-176">De para meter **Credential** is alleen geldig als de para meter **Source** wordt gebruikt in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="64ea1-176">The **Credential** parameter is valid only when the **Source** parameter is used in the command.</span></span> <span data-ttu-id="64ea1-177">De referenties hebben geen invloed op de doel computer.</span><span class="sxs-lookup"><span data-stu-id="64ea1-177">The credentials don't affect the destination computer.</span></span>

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

### <span data-ttu-id="64ea1-178">-DcomAuthentication</span><span class="sxs-lookup"><span data-stu-id="64ea1-178">-DcomAuthentication</span></span>

<span data-ttu-id="64ea1-179">Hiermee geeft u het verificatie niveau op dat met deze cmdlet wordt gebruikt met WMI.</span><span class="sxs-lookup"><span data-stu-id="64ea1-179">Specifies the authentication level that this cmdlet uses with WMI.</span></span>
<span data-ttu-id="64ea1-180">`Test-Connection` maakt gebruik van WMI.</span><span class="sxs-lookup"><span data-stu-id="64ea1-180">`Test-Connection` uses WMI.</span></span>
<span data-ttu-id="64ea1-181">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="64ea1-181">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="64ea1-182">**Standaard instelling**.</span><span class="sxs-lookup"><span data-stu-id="64ea1-182">**Default**.</span></span> <span data-ttu-id="64ea1-183">Windows-verificatie</span><span class="sxs-lookup"><span data-stu-id="64ea1-183">Windows Authentication</span></span>
- <span data-ttu-id="64ea1-184">**Geen**.</span><span class="sxs-lookup"><span data-stu-id="64ea1-184">**None**.</span></span> <span data-ttu-id="64ea1-185">Geen COM-verificatie</span><span class="sxs-lookup"><span data-stu-id="64ea1-185">No COM authentication</span></span>
- <span data-ttu-id="64ea1-186">**Verbinding maken**.</span><span class="sxs-lookup"><span data-stu-id="64ea1-186">**Connect**.</span></span> <span data-ttu-id="64ea1-187">COM-verificatie op verbindings niveau</span><span class="sxs-lookup"><span data-stu-id="64ea1-187">Connect-level COM authentication</span></span>
- <span data-ttu-id="64ea1-188">**Aanroep**.</span><span class="sxs-lookup"><span data-stu-id="64ea1-188">**Call**.</span></span> <span data-ttu-id="64ea1-189">COM-verificatie op aanroepen niveau</span><span class="sxs-lookup"><span data-stu-id="64ea1-189">Call-level COM authentication</span></span>
- <span data-ttu-id="64ea1-190">**Pakket**.</span><span class="sxs-lookup"><span data-stu-id="64ea1-190">**Packet**.</span></span> <span data-ttu-id="64ea1-191">COM-verificatie op pakket niveau</span><span class="sxs-lookup"><span data-stu-id="64ea1-191">Packet-level COM authentication</span></span>
- <span data-ttu-id="64ea1-192">**PacketIntegrity**.</span><span class="sxs-lookup"><span data-stu-id="64ea1-192">**PacketIntegrity**.</span></span> <span data-ttu-id="64ea1-193">COM-verificatie op pakket integriteit-niveau</span><span class="sxs-lookup"><span data-stu-id="64ea1-193">Packet Integrity-level COM authentication</span></span>
- <span data-ttu-id="64ea1-194">**PacketPrivacy**.</span><span class="sxs-lookup"><span data-stu-id="64ea1-194">**PacketPrivacy**.</span></span> <span data-ttu-id="64ea1-195">COM-verificatie op privacyniveau op pakket niveau</span><span class="sxs-lookup"><span data-stu-id="64ea1-195">Packet Privacy-level COM authentication</span></span>
- <span data-ttu-id="64ea1-196">**Ongewijzigd**.</span><span class="sxs-lookup"><span data-stu-id="64ea1-196">**Unchanged**.</span></span> <span data-ttu-id="64ea1-197">Hetzelfde als de vorige opdracht</span><span class="sxs-lookup"><span data-stu-id="64ea1-197">Same as the previous command</span></span>

<span data-ttu-id="64ea1-198">De standaard waarde is **pakket** met een opsommings waarde van **4**.</span><span class="sxs-lookup"><span data-stu-id="64ea1-198">The default value is **Packet** that has an enumerated value of **4**.</span></span> <span data-ttu-id="64ea1-199">Zie [authenticationLevel](/dotnet/api/system.management.authenticationlevel) Enumeration (Engelstalig) voor meer informatie over de waarden van deze para meter.</span><span class="sxs-lookup"><span data-stu-id="64ea1-199">For more information about the values of this parameter, see [AuthenticationLevel](/dotnet/api/system.management.authenticationlevel) enumeration.</span></span>

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

### <span data-ttu-id="64ea1-200">-Vertraging</span><span class="sxs-lookup"><span data-stu-id="64ea1-200">-Delay</span></span>

<span data-ttu-id="64ea1-201">Hiermee geeft u het interval tussen pings op, in seconden.</span><span class="sxs-lookup"><span data-stu-id="64ea1-201">Specifies the interval between pings, in seconds.</span></span>

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

### <span data-ttu-id="64ea1-202">-Imitatie</span><span class="sxs-lookup"><span data-stu-id="64ea1-202">-Impersonation</span></span>

<span data-ttu-id="64ea1-203">Hiermee geeft u het imitatie niveau op dat moet worden gebruikt wanneer deze cmdlet WMI aanroept.</span><span class="sxs-lookup"><span data-stu-id="64ea1-203">Specifies the impersonation level to use when this cmdlet calls WMI.</span></span> <span data-ttu-id="64ea1-204">`Test-Connection` maakt gebruik van WMI.</span><span class="sxs-lookup"><span data-stu-id="64ea1-204">`Test-Connection` uses WMI.</span></span>

<span data-ttu-id="64ea1-205">De acceptabele waarden voor deze para meter zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="64ea1-205">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="64ea1-206">**Standaard instelling**.</span><span class="sxs-lookup"><span data-stu-id="64ea1-206">**Default**.</span></span> <span data-ttu-id="64ea1-207">Standaard imitatie.</span><span class="sxs-lookup"><span data-stu-id="64ea1-207">Default impersonation.</span></span>
- <span data-ttu-id="64ea1-208">**Anoniem**.</span><span class="sxs-lookup"><span data-stu-id="64ea1-208">**Anonymous**.</span></span> <span data-ttu-id="64ea1-209">Hiermee verbergt u de identiteit van de aanroeper.</span><span class="sxs-lookup"><span data-stu-id="64ea1-209">Hides the identity of the caller.</span></span>
- <span data-ttu-id="64ea1-210">**Identificeren**.</span><span class="sxs-lookup"><span data-stu-id="64ea1-210">**Identify**.</span></span> <span data-ttu-id="64ea1-211">Hiermee kunnen objecten query's uitvoeren op de referenties van de aanroeper.</span><span class="sxs-lookup"><span data-stu-id="64ea1-211">Allows objects to query the credentials of the caller.</span></span>
- <span data-ttu-id="64ea1-212">**Imiteren**.</span><span class="sxs-lookup"><span data-stu-id="64ea1-212">**Impersonate**.</span></span> <span data-ttu-id="64ea1-213">Toestaan dat objecten de referenties van de aanroep functie gebruiken.</span><span class="sxs-lookup"><span data-stu-id="64ea1-213">Allows objects to use the credentials of the caller.</span></span>

<span data-ttu-id="64ea1-214">De standaard waarde is **imiteren**.</span><span class="sxs-lookup"><span data-stu-id="64ea1-214">The default value is **Impersonate**.</span></span>

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

### <span data-ttu-id="64ea1-215">-Protocol</span><span class="sxs-lookup"><span data-stu-id="64ea1-215">-Protocol</span></span>

<span data-ttu-id="64ea1-216">Hiermee geeft u een protocol.</span><span class="sxs-lookup"><span data-stu-id="64ea1-216">Specifies a protocol.</span></span> <span data-ttu-id="64ea1-217">De acceptabele waarden voor deze para meter zijn DCOM en WSMan.</span><span class="sxs-lookup"><span data-stu-id="64ea1-217">The acceptable values for this parameter are DCOM and WSMan.</span></span>

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

### <span data-ttu-id="64ea1-218">-Quiet</span><span class="sxs-lookup"><span data-stu-id="64ea1-218">-Quiet</span></span>

<span data-ttu-id="64ea1-219">De **stille** para meter retourneert een **Booleaanse** waarde in een object **System. Boolean** .</span><span class="sxs-lookup"><span data-stu-id="64ea1-219">The **Quiet** parameter returns a **Boolean** value in a **System.Boolean** object.</span></span> <span data-ttu-id="64ea1-220">Als u deze para meter gebruikt, worden alle fouten onderdrukt.</span><span class="sxs-lookup"><span data-stu-id="64ea1-220">Using this parameter suppresses all errors.</span></span>

<span data-ttu-id="64ea1-221">Elke geteste verbinding retourneert een **Booleaanse** waarde.</span><span class="sxs-lookup"><span data-stu-id="64ea1-221">Each connection that's tested returns a **Boolean** value.</span></span> <span data-ttu-id="64ea1-222">Als de para meter **ComputerName** meerdere computers bevat, wordt een matrix met **Boole** -waarden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="64ea1-222">If the **ComputerName** parameter specifies multiple computers, an array of **Boolean** values is returned.</span></span>

<span data-ttu-id="64ea1-223">Als **een** ping slaagt, `$True` wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="64ea1-223">If **any** ping succeeds, `$True` is returned.</span></span>

<span data-ttu-id="64ea1-224">Als **alle** pings mislukken, `$False` wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="64ea1-224">If **all** pings fail, `$False` is returned.</span></span>

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

### <span data-ttu-id="64ea1-225">-Source</span><span class="sxs-lookup"><span data-stu-id="64ea1-225">-Source</span></span>

<span data-ttu-id="64ea1-226">Hiermee geeft u de namen van de computers waarvan de ping afkomstig is.</span><span class="sxs-lookup"><span data-stu-id="64ea1-226">Specifies the names of the computers where the ping originates.</span></span> <span data-ttu-id="64ea1-227">Voer een door komma's gescheiden lijst met computer namen in.</span><span class="sxs-lookup"><span data-stu-id="64ea1-227">Enter a comma-separated list of computer names.</span></span> <span data-ttu-id="64ea1-228">Standaard is dit de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="64ea1-228">The default is the local computer.</span></span>

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

### <span data-ttu-id="64ea1-229">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="64ea1-229">-ThrottleLimit</span></span>

<span data-ttu-id="64ea1-230">Hiermee geeft u het maximum aantal gelijktijdige verbindingen op dat tot stand kan worden gebracht om deze opdracht uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="64ea1-230">Specifies the maximum number of concurrent connections that can be established to run this command.</span></span>
<span data-ttu-id="64ea1-231">Als u deze para meter weglaat of een waarde van 0 invoert, wordt de standaard waarde 32 gebruikt.</span><span class="sxs-lookup"><span data-stu-id="64ea1-231">If you omit this parameter or enter a value of 0, the default value, 32, is used.</span></span>

<span data-ttu-id="64ea1-232">De beperkings limiet geldt alleen voor de huidige opdracht, niet voor de sessie of voor de computer.</span><span class="sxs-lookup"><span data-stu-id="64ea1-232">The throttle limit applies only to the current command, not to the session or to the computer.</span></span>

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

### <span data-ttu-id="64ea1-233">-TimeToLive</span><span class="sxs-lookup"><span data-stu-id="64ea1-233">-TimeToLive</span></span>

<span data-ttu-id="64ea1-234">Hiermee geeft u het maximum aantal keren op dat een pakket kan worden doorgestuurd.</span><span class="sxs-lookup"><span data-stu-id="64ea1-234">Specifies the maximum times a packet can be forwarded.</span></span> <span data-ttu-id="64ea1-235">Voor elke hop in gateways, routers enzovoort. de waarde van **TimeToLive** wordt met één verlaagd.</span><span class="sxs-lookup"><span data-stu-id="64ea1-235">For every hop in gateways, routers etc. the **TimeToLive** value is decreased by one.</span></span> <span data-ttu-id="64ea1-236">Bij nul wordt het pakket verwijderd en wordt er een fout geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="64ea1-236">At zero the packet is discarded and an error is returned.</span></span>
<span data-ttu-id="64ea1-237">In **Windows** is de standaard waarde **128**.</span><span class="sxs-lookup"><span data-stu-id="64ea1-237">In **Windows** , The default value is **128**.</span></span> <span data-ttu-id="64ea1-238">De alias van de para meter **TimeToLive** is **TTL**.</span><span class="sxs-lookup"><span data-stu-id="64ea1-238">The alias of the **TimeToLive** parameter is **TTL**.</span></span>

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

### <span data-ttu-id="64ea1-239">-WsmanAuthentication</span><span class="sxs-lookup"><span data-stu-id="64ea1-239">-WsmanAuthentication</span></span>

<span data-ttu-id="64ea1-240">Hiermee geeft u het mechanisme op dat wordt gebruikt voor het verifiëren van de gebruikers referenties wanneer deze cmdlet gebruikmaakt van het WSMan-protocol.</span><span class="sxs-lookup"><span data-stu-id="64ea1-240">Specifies the mechanism that is used to authenticate the user credentials when this cmdlet uses the WSMan protocol.</span></span>
<span data-ttu-id="64ea1-241">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="64ea1-241">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="64ea1-242">Basic</span><span class="sxs-lookup"><span data-stu-id="64ea1-242">Basic</span></span>
- <span data-ttu-id="64ea1-243">CredSSP</span><span class="sxs-lookup"><span data-stu-id="64ea1-243">CredSSP</span></span>
- <span data-ttu-id="64ea1-244">Standaard</span><span class="sxs-lookup"><span data-stu-id="64ea1-244">Default</span></span>
- <span data-ttu-id="64ea1-245">Samenvatting</span><span class="sxs-lookup"><span data-stu-id="64ea1-245">Digest</span></span>
- <span data-ttu-id="64ea1-246">Kerberos</span><span class="sxs-lookup"><span data-stu-id="64ea1-246">Kerberos</span></span>
- <span data-ttu-id="64ea1-247">Afspraken.</span><span class="sxs-lookup"><span data-stu-id="64ea1-247">Negotiate.</span></span>

<span data-ttu-id="64ea1-248">De standaard waarde is standaard.</span><span class="sxs-lookup"><span data-stu-id="64ea1-248">The default value is Default.</span></span>

<span data-ttu-id="64ea1-249">Zie [AuthenticationMechanism Enumeration (Engelstalig)](/dotnet/api/system.management.automation.runspaces.authenticationmechanism?view=powershellsdk-1.1.0)voor meer informatie over de waarden van deze para meter.</span><span class="sxs-lookup"><span data-stu-id="64ea1-249">For more information about the values of this parameter, see [AuthenticationMechanism Enumeration](/dotnet/api/system.management.automation.runspaces.authenticationmechanism?view=powershellsdk-1.1.0).</span></span>

<span data-ttu-id="64ea1-250">Let op: de verificatie van de Credential Security service provider (CredSSP), waarbij de gebruikers referenties worden door gegeven aan een externe computer die moet worden geverifieerd, is ontworpen voor opdrachten die verificatie vereisen voor meer dan één bron, zoals het openen van een externe netwerk share.</span><span class="sxs-lookup"><span data-stu-id="64ea1-250">Caution: Credential Security Service Provider (CredSSP) authentication, in which the user credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span>
<span data-ttu-id="64ea1-251">Dit mechanisme verhoogt het beveiligings risico van de externe bewerking.</span><span class="sxs-lookup"><span data-stu-id="64ea1-251">This mechanism increases the security risk of the remote operation.</span></span>
<span data-ttu-id="64ea1-252">Als er is geknoeid met de externe computer, kunnen de referenties die aan worden door gegeven, worden gebruikt om de netwerk sessie te beheren.</span><span class="sxs-lookup"><span data-stu-id="64ea1-252">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

<span data-ttu-id="64ea1-253">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="64ea1-253">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="64ea1-254">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="64ea1-254">CommonParameters</span></span>

<span data-ttu-id="64ea1-255">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="64ea1-255">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="64ea1-256">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="64ea1-256">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="64ea1-257">INVOER</span><span class="sxs-lookup"><span data-stu-id="64ea1-257">INPUTS</span></span>

### <span data-ttu-id="64ea1-258">Geen</span><span class="sxs-lookup"><span data-stu-id="64ea1-258">None</span></span>

<span data-ttu-id="64ea1-259">U kunt invoer niet naar deze cmdlet pipeen.</span><span class="sxs-lookup"><span data-stu-id="64ea1-259">You can't pipe input to this cmdlet.</span></span>

## <span data-ttu-id="64ea1-260">UITVOER</span><span class="sxs-lookup"><span data-stu-id="64ea1-260">OUTPUTS</span></span>

### <span data-ttu-id="64ea1-261">System. Management. ManagementObject # root\cimv2\ Win32_PingStatus, System. Management. Automation. RemotingJob, System. Boolean</span><span class="sxs-lookup"><span data-stu-id="64ea1-261">System.Management.ManagementObject#root\cimv2\Win32_PingStatus, System.Management.Automation.RemotingJob, System.Boolean</span></span>

<span data-ttu-id="64ea1-262">Met deze cmdlet wordt een taak object geretourneerd als u de para meter **AsJob** opgeeft.</span><span class="sxs-lookup"><span data-stu-id="64ea1-262">This cmdlet returns a job object, if you specify the **AsJob** parameter.</span></span>

<span data-ttu-id="64ea1-263">Als u de **stille** para meter opgeeft, wordt een **Booleaanse** waarde geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="64ea1-263">If you specify the **Quiet** parameter, it returns a **Boolean** value.</span></span> <span data-ttu-id="64ea1-264">Als er meerdere verbindingen worden getest, wordt een matrix met **Boole** -waarden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="64ea1-264">If multiple connections are tested, an array of **Boolean** values is returned.</span></span> <span data-ttu-id="64ea1-265">Anders `Test-Connection` retourneert een **Win32_PingStatus** -object voor elke ping.</span><span class="sxs-lookup"><span data-stu-id="64ea1-265">Otherwise, `Test-Connection` returns a **Win32_PingStatus** object for each ping.</span></span>

## <span data-ttu-id="64ea1-266">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="64ea1-266">NOTES</span></span>

<span data-ttu-id="64ea1-267">Deze cmdlet maakt gebruik van de **Win32_PingStatus** -klasse.</span><span class="sxs-lookup"><span data-stu-id="64ea1-267">This cmdlet uses the **Win32_PingStatus** class.</span></span> <span data-ttu-id="64ea1-268">Een `Get-WMIObject Win32_PingStatus` opdracht is gelijk aan een `Test-Connection` opdracht.</span><span class="sxs-lookup"><span data-stu-id="64ea1-268">A `Get-WMIObject Win32_PingStatus` command is equivalent to a `Test-Connection` command.</span></span>

<span data-ttu-id="64ea1-269">De para meter set van de **bron** is geïntroduceerd in power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="64ea1-269">The **Source** parameter set was introduced in PowerShell 3.0.</span></span>

## <span data-ttu-id="64ea1-270">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="64ea1-270">RELATED LINKS</span></span>

[<span data-ttu-id="64ea1-271">Add-computer</span><span class="sxs-lookup"><span data-stu-id="64ea1-271">Add-Computer</span></span>](Add-Computer.md)

[<span data-ttu-id="64ea1-272">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="64ea1-272">Restart-Computer</span></span>](Restart-Computer.md)

[<span data-ttu-id="64ea1-273">Stop-computer</span><span class="sxs-lookup"><span data-stu-id="64ea1-273">Stop-Computer</span></span>](Stop-Computer.md)
