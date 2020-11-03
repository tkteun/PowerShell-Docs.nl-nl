---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 6/17/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/restart-computer?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Restart-Computer
ms.openlocfilehash: 553b61c9669afab325e9feec101d701c2b9a7c83
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/23/2020
ms.locfileid: "93251499"
---
# <span data-ttu-id="cc19c-103">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="cc19c-103">Restart-Computer</span></span>

## <span data-ttu-id="cc19c-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="cc19c-104">SYNOPSIS</span></span>
<span data-ttu-id="cc19c-105">Hiermee wordt het besturings systeem opnieuw opgestart op lokale en externe computers.</span><span class="sxs-lookup"><span data-stu-id="cc19c-105">Restarts the operating system on local and remote computers.</span></span>

## <span data-ttu-id="cc19c-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="cc19c-106">SYNTAX</span></span>

### <span data-ttu-id="cc19c-107">Standaardset (standaard)</span><span class="sxs-lookup"><span data-stu-id="cc19c-107">DefaultSet (Default)</span></span>

```
Restart-Computer [-DcomAuthentication <AuthenticationLevel>] [-Impersonation <ImpersonationLevel>]
 [-WsmanAuthentication <String>] [-Protocol <String>] [[-ComputerName] <String[]>]
 [[-Credential] <PSCredential>] [-Force] [-Wait] [-Timeout <Int32>] [-For <WaitForServiceTypes>]
 [-Delay <Int16>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="cc19c-108">AsJobSet</span><span class="sxs-lookup"><span data-stu-id="cc19c-108">AsJobSet</span></span>

```
Restart-Computer [-AsJob] [-DcomAuthentication <AuthenticationLevel>]
 [-Impersonation <ImpersonationLevel>] [[-ComputerName] <String[]>] [[-Credential] <PSCredential>]
 [-Force] [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="cc19c-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="cc19c-109">DESCRIPTION</span></span>

<span data-ttu-id="cc19c-110">`Restart-Computer`Met de cmdlet wordt het besturings systeem opnieuw gestart op de lokale en externe computers.</span><span class="sxs-lookup"><span data-stu-id="cc19c-110">The `Restart-Computer` cmdlet restarts the operating system on the local and remote computers.</span></span>

<span data-ttu-id="cc19c-111">U kunt de para meters van gebruiken `Restart-Computer` om de bewerkingen voor opnieuw opstarten uit te voeren als achtergrond taak, om de verificatie niveaus en alternatieve referenties op te geven, om de bewerkingen die tegelijkertijd worden uitgevoerd, te beperken en onmiddellijk opnieuw op te starten.</span><span class="sxs-lookup"><span data-stu-id="cc19c-111">You can use the parameters of `Restart-Computer` to run the restart operations as a background job, to specify the authentication levels and alternate credentials, to limit the operations that run at the same time, and to force an immediate restart.</span></span>

<span data-ttu-id="cc19c-112">Vanaf Windows Power Shell 3,0 kunt u wachten tot de herstart is voltooid voordat u de volgende opdracht uitvoert.</span><span class="sxs-lookup"><span data-stu-id="cc19c-112">Starting in Windows PowerShell 3.0, you can wait for the restart to complete before you run the next command.</span></span> <span data-ttu-id="cc19c-113">Geef een time-out op voor de wacht tijd en het query-interval, en wacht totdat bepaalde services beschikbaar zijn op de computer die opnieuw is opgestart.</span><span class="sxs-lookup"><span data-stu-id="cc19c-113">Specify a waiting time-out and query interval, and wait for particular services to be available on the restarted computer.</span></span> <span data-ttu-id="cc19c-114">Deze functie maakt het handig om te gebruiken `Restart-Computer` in scripts en functies.</span><span class="sxs-lookup"><span data-stu-id="cc19c-114">This feature makes it practical to use `Restart-Computer` in scripts and functions.</span></span>

<span data-ttu-id="cc19c-115">U kunt het WS-Management (WSMan)-protocol gebruiken om de computer opnieuw op te starten, in gevallen waarin gedistribueerde Component Object Model (DCOM)-aanroepen worden geblokkeerd, zoals een bedrijfs firewall.</span><span class="sxs-lookup"><span data-stu-id="cc19c-115">You can use the WS-Management (WSMan) protocol to restart the computer, in case Distributed Component Object Model (DCOM) calls are blocked, such as by an enterprise firewall.</span></span> <span data-ttu-id="cc19c-116">Zie [WS-Management Protocol](/windows/desktop/WinRM/ws-management-protocol)(Engelstalig) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="cc19c-116">For more information, see [WS-Management Protocol](/windows/desktop/WinRM/ws-management-protocol).</span></span>

<span data-ttu-id="cc19c-117">Voor deze cmdlet is alleen externe toegang tot Windows Power shell vereist wanneer u de para meter **AsJob** in een opdracht gebruikt.</span><span class="sxs-lookup"><span data-stu-id="cc19c-117">This cmdlet requires Windows PowerShell remoting only when you use the **AsJob** parameter in a command.</span></span>

## <span data-ttu-id="cc19c-118">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="cc19c-118">EXAMPLES</span></span>

### <span data-ttu-id="cc19c-119">Voor beeld 1: de lokale computer opnieuw opstarten</span><span class="sxs-lookup"><span data-stu-id="cc19c-119">Example 1: Restart the local computer</span></span>

<span data-ttu-id="cc19c-120">`Restart-Computer` Hiermee wordt de lokale computer opnieuw opgestart.</span><span class="sxs-lookup"><span data-stu-id="cc19c-120">`Restart-Computer` restarts the local computer.</span></span>

```powershell
Restart-Computer
```

### <span data-ttu-id="cc19c-121">Voor beeld 2: meerdere computers opnieuw opstarten</span><span class="sxs-lookup"><span data-stu-id="cc19c-121">Example 2: Restart multiple computers</span></span>

<span data-ttu-id="cc19c-122">`Restart-Computer` externe en lokale computers kunnen opnieuw worden gestart.</span><span class="sxs-lookup"><span data-stu-id="cc19c-122">`Restart-Computer` can restart remote and local computers.</span></span> <span data-ttu-id="cc19c-123">De para meter **ComputerName** accepteert een matrix met computer namen.</span><span class="sxs-lookup"><span data-stu-id="cc19c-123">The **ComputerName** parameter accepts an array of computer names.</span></span>

```powershell
Restart-Computer -ComputerName Server01, Server02, localhost
```

### <span data-ttu-id="cc19c-124">Voor beeld 3: computers opnieuw opstarten als achtergrond taak</span><span class="sxs-lookup"><span data-stu-id="cc19c-124">Example 3: Restart computers as a background job</span></span>

<span data-ttu-id="cc19c-125">Met deze opdrachten `Restart-Computer` wordt een opdracht uitgevoerd als achtergrond taak op twee externe computers, waarna de resultaten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="cc19c-125">These commands run a `Restart-Computer` command as a background job on two remote computers, and then get the results.</span></span>

<span data-ttu-id="cc19c-126">Omdat **AsJob** de taak op de lokale computer maakt en automatisch de resultaten naar de lokale computer retourneert, kunt u uitvoeren `Receive-Job` als een lokale opdracht.</span><span class="sxs-lookup"><span data-stu-id="cc19c-126">Because **AsJob** creates the job on the local computer and automatically returns the results to the local computer, you can run `Receive-Job` as a local command.</span></span>

```powershell
$Job = Restart-Computer -ComputerName "Server01", "Server02" -AsJob
$Job | Receive-Job
```

<span data-ttu-id="cc19c-127">`Restart-Computer` maakt gebruik van de para meter **ComputerName** om **Server01** en **Server02** op te geven.</span><span class="sxs-lookup"><span data-stu-id="cc19c-127">`Restart-Computer` uses the **ComputerName** parameter to specify **Server01** and **Server02**.</span></span> <span data-ttu-id="cc19c-128">De **AsJob** para meter voert de opdracht uit als achtergrond taak.</span><span class="sxs-lookup"><span data-stu-id="cc19c-128">The **AsJob** parameter runs the command as a background job.</span></span> <span data-ttu-id="cc19c-129">Het taak object wordt opgeslagen in de `$Job` variabele.</span><span class="sxs-lookup"><span data-stu-id="cc19c-129">The job object is stored in the `$Job` variable.</span></span> <span data-ttu-id="cc19c-130">`$Job` wordt via de pijp lijn naar de `Receive-Job` cmdlet verzonden die de resultaten ophaalt.</span><span class="sxs-lookup"><span data-stu-id="cc19c-130">`$Job` is sent down the pipeline to the `Receive-Job` cmdlet that gets the results.</span></span>

### <span data-ttu-id="cc19c-131">Voor beeld 4: een externe computer opnieuw opstarten</span><span class="sxs-lookup"><span data-stu-id="cc19c-131">Example 4: Restart a remote computer</span></span>

<span data-ttu-id="cc19c-132">`Restart-Computer` Hiermee wordt een externe computer opnieuw opgestart met aangepaste imitatie-en verificatie-instellingen.</span><span class="sxs-lookup"><span data-stu-id="cc19c-132">`Restart-Computer` restarts a remote computer with customized impersonation and authentication settings.</span></span>

```powershell
Restart-Computer -ComputerName Server01 -Impersonation Anonymous -DcomAuthentication PacketIntegrity
```

<span data-ttu-id="cc19c-133">`Restart-Computer` maakt gebruik van de para meter **ComputerName** om **Server01** op te geven.</span><span class="sxs-lookup"><span data-stu-id="cc19c-133">`Restart-Computer` uses the **ComputerName** parameter to specify **Server01**.</span></span> <span data-ttu-id="cc19c-134">De **imitatie** parameter geeft anoniem op om de identiteit van de aanvrager te verbergen.</span><span class="sxs-lookup"><span data-stu-id="cc19c-134">The **Impersonation** parameter specifies Anonymous to hide the requester's identity.</span></span> <span data-ttu-id="cc19c-135">De **DcomAuthentication** para meter geeft u PacketIntegrity op als verificatie niveau van de verbinding.</span><span class="sxs-lookup"><span data-stu-id="cc19c-135">The **DcomAuthentication** parameter specifies PacketIntegrity as the connection's authentication level.</span></span>

### <span data-ttu-id="cc19c-136">Voor beeld 5: de computers die worden vermeld in een tekst bestand geforceerd opnieuw opstarten</span><span class="sxs-lookup"><span data-stu-id="cc19c-136">Example 5: Force restart of computers listed in a text file</span></span>

<span data-ttu-id="cc19c-137">In dit voor beeld wordt een onmiddellijke herstart van de computers die in het bestand worden vermeld, geforceerd `Domain01.txt` .</span><span class="sxs-lookup"><span data-stu-id="cc19c-137">This example forces an immediate restart of the computers listed in the `Domain01.txt` file.</span></span> <span data-ttu-id="cc19c-138">De computer namen uit het tekst bestand worden opgeslagen in een variabele.</span><span class="sxs-lookup"><span data-stu-id="cc19c-138">The computer names from the text file are stored in a variable.</span></span> <span data-ttu-id="cc19c-139">De **Force** -para meter forceert onmiddellijk opnieuw opstarten en de para meter **ThrottleLimit** beperkt het aantal gelijktijdige verbindingen.</span><span class="sxs-lookup"><span data-stu-id="cc19c-139">The **Force** parameter forces an immediate restart and the **ThrottleLimit** parameter limits the number of concurrent connections.</span></span>

```powershell
$Names = Get-Content -Path C:\Domain01.txt
$Creds = Get-Credential
Restart-Computer -ComputerName $Names -Credential $Creds -Force -ThrottleLimit 10
```

<span data-ttu-id="cc19c-140">`Get-Content` gebruikt de para meter **Path** voor het ophalen van een lijst met computer namen uit een tekst bestand **Domain01.txt**.</span><span class="sxs-lookup"><span data-stu-id="cc19c-140">`Get-Content` uses the **Path** parameter to get a list of computer names from a text file, **Domain01.txt**.</span></span> <span data-ttu-id="cc19c-141">De computer namen worden opgeslagen in de variabele `$Names` .</span><span class="sxs-lookup"><span data-stu-id="cc19c-141">The computer names are stored in the variable `$Names`.</span></span> <span data-ttu-id="cc19c-142">`Get-Credential` vraagt u om een gebruikers naam en wacht woord en slaat de waarden op in de variabele `$Creds` .</span><span class="sxs-lookup"><span data-stu-id="cc19c-142">`Get-Credential` prompts you for a username and password and stores the values in the variable `$Creds`.</span></span> <span data-ttu-id="cc19c-143">`Restart-Computer` maakt gebruik van de **computer naam** en de **referentie** parameters met hun variabelen.</span><span class="sxs-lookup"><span data-stu-id="cc19c-143">`Restart-Computer` uses the **ComputerName** and **Credential** parameters with their variables.</span></span> <span data-ttu-id="cc19c-144">De para meter **Force** zorgt ervoor dat elke computer direct opnieuw wordt opgestart.</span><span class="sxs-lookup"><span data-stu-id="cc19c-144">The **Force** parameter causes an immediate restart of each computer.</span></span> <span data-ttu-id="cc19c-145">De para meter **ThrottleLimit** beperkt de opdracht tot tien gelijktijdige verbindingen.</span><span class="sxs-lookup"><span data-stu-id="cc19c-145">The **ThrottleLimit** parameter limits the command to 10 concurrent connections.</span></span>

### <span data-ttu-id="cc19c-146">Voor beeld 6: een externe computer opnieuw opstarten en wachten op Power shell</span><span class="sxs-lookup"><span data-stu-id="cc19c-146">Example 6: Restart a remote computer and wait for PowerShell</span></span>

<span data-ttu-id="cc19c-147">`Restart-Computer` Start de externe computer opnieuw op en wacht vijf minuten (300 seconden), waarna Power shell beschikbaar wordt op de computer die opnieuw is opgestart voordat deze doorgaat.</span><span class="sxs-lookup"><span data-stu-id="cc19c-147">`Restart-Computer` restarts the remote computer and then waits up to 5 minutes (300 seconds) for PowerShell to become available on the restarted computer before it continues.</span></span>

```powershell
Restart-Computer -ComputerName Server01 -Wait -For PowerShell -Timeout 300 -Delay 2
```

<span data-ttu-id="cc19c-148">`Restart-Computer` maakt gebruik van de para meter **ComputerName** om **Server01** op te geven.</span><span class="sxs-lookup"><span data-stu-id="cc19c-148">`Restart-Computer` uses the **ComputerName** parameter to specify **Server01**.</span></span> <span data-ttu-id="cc19c-149">De **wait** -para meter wacht totdat de herstart is voltooid.</span><span class="sxs-lookup"><span data-stu-id="cc19c-149">The **Wait** parameter waits for the restart to finish.</span></span> <span data-ttu-id="cc19c-150">Met de **for** geeft u op dat Power shell opdrachten kan uitvoeren op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="cc19c-150">The **For** specifies that PowerShell can run commands on the remote computer.</span></span> <span data-ttu-id="cc19c-151">De **time-** outpara meter geeft een wacht tijd van vijf minuten.</span><span class="sxs-lookup"><span data-stu-id="cc19c-151">The **Timeout** parameter specifies a five-minute wait.</span></span> <span data-ttu-id="cc19c-152">De **vertragings** parameter voert elke twee seconden een query uit op de externe computer om vast te stellen of deze opnieuw wordt opgestart.</span><span class="sxs-lookup"><span data-stu-id="cc19c-152">The **Delay** parameter queries the remote computer every two seconds to determine whether it's restarted.</span></span>

### <span data-ttu-id="cc19c-153">Voor beeld 7: een computer opnieuw opstarten met behulp van het WSMan-Protocol</span><span class="sxs-lookup"><span data-stu-id="cc19c-153">Example 7: Restart a computer by using the WSMan Protocol</span></span>

<span data-ttu-id="cc19c-154">`Restart-Computer` Hiermee wordt de externe computer opnieuw opgestart met behulp van het WSMan-protocol in plaats van de standaard DCOM.</span><span class="sxs-lookup"><span data-stu-id="cc19c-154">`Restart-Computer` restarts the remote computer by using the WSMan protocol instead of the default, DCOM.</span></span> <span data-ttu-id="cc19c-155">Met Kerberos-verificatie wordt bepaald of de huidige gebruiker gemachtigd is om de externe computer opnieuw op te starten.</span><span class="sxs-lookup"><span data-stu-id="cc19c-155">Kerberos authentication determines whether the current user has permission to restart the remote computer.</span></span>

<span data-ttu-id="cc19c-156">Deze instellingen zijn ontworpen voor ondernemingen waarbij op DCOM gebaseerde herstarts mislukken omdat DCOM is geblokkeerd.</span><span class="sxs-lookup"><span data-stu-id="cc19c-156">These settings are designed for enterprises in which DCOM-based restarts fail because DCOM is blocked.</span></span> <span data-ttu-id="cc19c-157">Bijvoorbeeld door een firewall.</span><span class="sxs-lookup"><span data-stu-id="cc19c-157">For example, by a firewall.</span></span>

```powershell
Restart-Computer -ComputerName Server01 -Protocol WSMan -WsmanAuthentication Kerberos
```

<span data-ttu-id="cc19c-158">`Restart-Computer` maakt gebruik van de para meter **ComputerName** om de externe computer op te geven, **Server01**.</span><span class="sxs-lookup"><span data-stu-id="cc19c-158">`Restart-Computer` uses the **ComputerName** parameter to specify the remote computer, **Server01**.</span></span>
<span data-ttu-id="cc19c-159">De **protocol** parameter geeft aan dat het WSMan-protocol moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="cc19c-159">The **Protocol** parameter specifies to use the WSMan protocol.</span></span> <span data-ttu-id="cc19c-160">De **WsmanAuthentication** para meter geeft u de verificatie methode op als **Kerberos**.</span><span class="sxs-lookup"><span data-stu-id="cc19c-160">The **WsmanAuthentication** parameter specifies the authentication method as **Kerberos**.</span></span>

## <span data-ttu-id="cc19c-161">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="cc19c-161">PARAMETERS</span></span>

### <span data-ttu-id="cc19c-162">-AsJob</span><span class="sxs-lookup"><span data-stu-id="cc19c-162">-AsJob</span></span>

<span data-ttu-id="cc19c-163">Geeft aan dat `Restart-Computer` wordt uitgevoerd als achtergrond taak.</span><span class="sxs-lookup"><span data-stu-id="cc19c-163">Indicates that `Restart-Computer` runs as a background job.</span></span>

<span data-ttu-id="cc19c-164">Als u deze para meter wilt gebruiken, moeten de lokale en externe computers worden geconfigureerd voor externe toegang.</span><span class="sxs-lookup"><span data-stu-id="cc19c-164">To use this parameter, the local and remote computers must be configured for remoting.</span></span> <span data-ttu-id="cc19c-165">In Windows Vista en latere versies van het Windows-besturings systeem moet u Power shell openen met de optie **als administrator uitvoeren** .</span><span class="sxs-lookup"><span data-stu-id="cc19c-165">On Windows Vista and later versions of the Windows operating system, you must open PowerShell by using the **Run as Administrator** option.</span></span> <span data-ttu-id="cc19c-166">Zie [about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="cc19c-166">For more information, see [about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md).</span></span>

<span data-ttu-id="cc19c-167">Wanneer u de para meter **AsJob** opgeeft, retourneert de opdracht direct een object dat de achtergrond taak vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="cc19c-167">When you specify the **AsJob** parameter, the command immediately returns an object that represents the background job.</span></span> <span data-ttu-id="cc19c-168">U kunt in de sessie blijven werken terwijl de taak is voltooid.</span><span class="sxs-lookup"><span data-stu-id="cc19c-168">You can continue to work in the session while the job finishes.</span></span> <span data-ttu-id="cc19c-169">De taak wordt gemaakt op de lokale computer en de resultaten van externe computers worden automatisch geretourneerd naar de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="cc19c-169">The job is created on the local computer and the results from remote computers are automatically returned to the local computer.</span></span> <span data-ttu-id="cc19c-170">Gebruik de **taak** -cmdlets om de taak te beheren.</span><span class="sxs-lookup"><span data-stu-id="cc19c-170">To manage the job, use the **Job** cmdlets.</span></span> <span data-ttu-id="cc19c-171">Gebruik de cmdlet om de taak resultaten te verkrijgen `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="cc19c-171">To get the job results, use the `Receive-Job` cmdlet.</span></span>

<span data-ttu-id="cc19c-172">Zie [about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md) en [about_Remote_Jobs](../Microsoft.PowerShell.Core/About/about_Remote_Jobs.md)voor meer informatie over Windows Power shell-achtergrond taken.</span><span class="sxs-lookup"><span data-stu-id="cc19c-172">For more information about Windows PowerShell background jobs, see [about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md) and [about_Remote_Jobs](../Microsoft.PowerShell.Core/About/about_Remote_Jobs.md).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AsJobSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cc19c-173">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="cc19c-173">-ComputerName</span></span>

<span data-ttu-id="cc19c-174">Hiermee geeft u een computer naam of een door komma's gescheiden matrix van computer namen op.</span><span class="sxs-lookup"><span data-stu-id="cc19c-174">Specifies one computer name or a comma-separated array of computer names.</span></span> <span data-ttu-id="cc19c-175">`Restart-Computer` Hiermee worden **computer naam** objecten van de pijp lijn of variabelen geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="cc19c-175">`Restart-Computer` accepts **ComputerName** objects from the pipeline or variables.</span></span>

<span data-ttu-id="cc19c-176">Typ de NetBIOS-naam, een IP-adres of een Fully Qualified Domain Name van een externe computer.</span><span class="sxs-lookup"><span data-stu-id="cc19c-176">Type the NetBIOS name, an IP address, or a fully qualified domain name of a remote computer.</span></span> <span data-ttu-id="cc19c-177">Als u de lokale computer wilt opgeven, typt u de naam van de computer, een punt `.` of localhost.</span><span class="sxs-lookup"><span data-stu-id="cc19c-177">To specify the local computer, type the computer name, a dot `.`, or localhost.</span></span>

<span data-ttu-id="cc19c-178">Deze para meter is niet afhankelijk van externe communicatie met Power shell.</span><span class="sxs-lookup"><span data-stu-id="cc19c-178">This parameter doesn't rely on PowerShell remoting.</span></span> <span data-ttu-id="cc19c-179">U kunt de para meter **ComputerName** ook gebruiken als uw computer niet is geconfigureerd om externe opdrachten uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="cc19c-179">You can use the **ComputerName** parameter even if your computer isn't configured to run remote commands.</span></span>

<span data-ttu-id="cc19c-180">Als de para meter **ComputerName** niet is opgegeven, wordt `Restart-Computer` de lokale computer opnieuw opgestart.</span><span class="sxs-lookup"><span data-stu-id="cc19c-180">If the **ComputerName** parameter isn't specified, `Restart-Computer` restarts the local computer.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN, __SERVER, Server, IPAddress

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="cc19c-181">-Credential</span><span class="sxs-lookup"><span data-stu-id="cc19c-181">-Credential</span></span>

<span data-ttu-id="cc19c-182">Hiermee geeft u een gebruikers account op dat gemachtigd is om deze actie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="cc19c-182">Specifies a user account that has permission to do this action.</span></span> <span data-ttu-id="cc19c-183">Standaard is dit de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="cc19c-183">The default is the current user.</span></span>

<span data-ttu-id="cc19c-184">Typ een gebruikers naam, zoals **gebruiker01** of **Domain01\User01** , of voer een **PSCredential** -object in dat door de cmdlet wordt gegenereerd `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="cc19c-184">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="cc19c-185">Als u een gebruikers naam typt, wordt u gevraagd het wacht woord in te voeren.</span><span class="sxs-lookup"><span data-stu-id="cc19c-185">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="cc19c-186">Referenties worden opgeslagen in een [PSCredential](/dotnet/api/system.management.automation.pscredential) -object en het wacht woord wordt opgeslagen als [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="cc19c-186">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="cc19c-187">Zie [Hoe veilig is securestring?](/dotnet/api/system.security.securestring#how-secure-is-securestring)voor meer informatie over **securestring** Data Protection.</span><span class="sxs-lookup"><span data-stu-id="cc19c-187">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cc19c-188">-DcomAuthentication</span><span class="sxs-lookup"><span data-stu-id="cc19c-188">-DcomAuthentication</span></span>

<span data-ttu-id="cc19c-189">Hiermee geeft u het verificatie niveau op dat wordt gebruikt voor de WMI-verbinding.</span><span class="sxs-lookup"><span data-stu-id="cc19c-189">Specifies the authentication level that is used for the WMI connection.</span></span> <span data-ttu-id="cc19c-190">`Restart-Computer` maakt gebruik van WMI.</span><span class="sxs-lookup"><span data-stu-id="cc19c-190">`Restart-Computer` uses WMI.</span></span>

<span data-ttu-id="cc19c-191">Geldige waarden zijn:</span><span class="sxs-lookup"><span data-stu-id="cc19c-191">Valid values are:</span></span>

- <span data-ttu-id="cc19c-192">**Aanroep** : com-verificatie op aanroepen niveau</span><span class="sxs-lookup"><span data-stu-id="cc19c-192">**Call** :            Call-level COM authentication</span></span>
- <span data-ttu-id="cc19c-193">**Verbinding maken** : com-verificatie op verbindings niveau</span><span class="sxs-lookup"><span data-stu-id="cc19c-193">**Connect** :         Connect-level COM authentication</span></span>
- <span data-ttu-id="cc19c-194">**Standaard** : Windows-verificatie</span><span class="sxs-lookup"><span data-stu-id="cc19c-194">**Default** :         Windows Authentication</span></span>
- <span data-ttu-id="cc19c-195">**Geen** : geen com-verificatie</span><span class="sxs-lookup"><span data-stu-id="cc19c-195">**None** :            No COM authentication</span></span>
- <span data-ttu-id="cc19c-196">**Pakket** : com-verificatie op pakket niveau.</span><span class="sxs-lookup"><span data-stu-id="cc19c-196">**Packet** :          Packet-level COM authentication.</span></span>
- <span data-ttu-id="cc19c-197">**PacketIntegrity** : com-verificatie op pakket integriteit-niveau</span><span class="sxs-lookup"><span data-stu-id="cc19c-197">**PacketIntegrity** : Packet Integrity-level COM authentication</span></span>
- <span data-ttu-id="cc19c-198">**PacketPrivacy** : com-verificatie op privacyniveau op pakket niveau.</span><span class="sxs-lookup"><span data-stu-id="cc19c-198">**PacketPrivacy** :   Packet Privacy-level COM authentication.</span></span>
- <span data-ttu-id="cc19c-199">**Ongewijzigd** : het verificatie niveau is hetzelfde als de vorige opdracht.</span><span class="sxs-lookup"><span data-stu-id="cc19c-199">**Unchanged** :       The authentication level is the same as the previous command.</span></span>

<span data-ttu-id="cc19c-200">Zie [authenticationLevel Enumeration (Engelstalig)](/dotnet/api/system.management.authenticationlevel)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="cc19c-200">For more information, see [AuthenticationLevel Enumeration](/dotnet/api/system.management.authenticationlevel).</span></span>

<span data-ttu-id="cc19c-201">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="cc19c-201">This parameter is introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.AuthenticationLevel
Parameter Sets: (All)
Aliases: Authentication
Accepted values: Default, None, Connect, Call, Packet, PacketIntegrity, PacketPrivacy, Unchanged

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cc19c-202">-Vertraging</span><span class="sxs-lookup"><span data-stu-id="cc19c-202">-Delay</span></span>

<span data-ttu-id="cc19c-203">Hiermee geeft u de frequentie van query's in seconden.</span><span class="sxs-lookup"><span data-stu-id="cc19c-203">Specifies the frequency of queries, in seconds.</span></span> <span data-ttu-id="cc19c-204">Power shell vraagt de service op die is opgegeven door de para meter **for** om te bepalen of de service beschikbaar is nadat de computer opnieuw is opgestart.</span><span class="sxs-lookup"><span data-stu-id="cc19c-204">PowerShell queries the service specified by the **For** parameter to determine whether the service is available after the computer is restarted.</span></span>

<span data-ttu-id="cc19c-205">Deze para meter is alleen geldig in combi natie met de **wacht** **-en-** para meters.</span><span class="sxs-lookup"><span data-stu-id="cc19c-205">This parameter is valid only together with the **Wait** and **For** parameters.</span></span>

<span data-ttu-id="cc19c-206">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="cc19c-206">This parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="cc19c-207">Als de para meter **Delay** niet is opgegeven, `Restart-Computer` wordt een vertraging van vijf seconden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="cc19c-207">If the **Delay** parameter isn't specified, `Restart-Computer` uses a five second delay.</span></span>

```yaml
Type: System.Int16
Parameter Sets: DefaultSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cc19c-208">-Voor</span><span class="sxs-lookup"><span data-stu-id="cc19c-208">-For</span></span>

<span data-ttu-id="cc19c-209">Hiermee wordt het gedrag van Power shell opgegeven wanneer wordt gewacht tot de opgegeven service of functie beschikbaar is nadat de computer opnieuw is opgestart.</span><span class="sxs-lookup"><span data-stu-id="cc19c-209">Specifies the behavior of PowerShell as it waits for the specified service or feature to become available after the computer restarts.</span></span> <span data-ttu-id="cc19c-210">Deze para meter is alleen geldig met de para meter **wait** .</span><span class="sxs-lookup"><span data-stu-id="cc19c-210">This parameter is only valid with the **Wait** parameter.</span></span>

<span data-ttu-id="cc19c-211">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="cc19c-211">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="cc19c-212">**Standaard** : er wordt gewacht tot Power shell opnieuw is opgestart.</span><span class="sxs-lookup"><span data-stu-id="cc19c-212">**Default** : Waits for PowerShell to restart.</span></span>
- <span data-ttu-id="cc19c-213">**Power shell** : opdrachten kunnen uitvoeren in een externe Power shell-sessie op de computer.</span><span class="sxs-lookup"><span data-stu-id="cc19c-213">**PowerShell** : Can run commands in a PowerShell remote session on the computer.</span></span>
- <span data-ttu-id="cc19c-214">**WMI** : ontvangt een antwoord op een Win32_ComputerSystem-query voor de computer.</span><span class="sxs-lookup"><span data-stu-id="cc19c-214">**WMI** : Receives a reply to a Win32_ComputerSystem query for the computer.</span></span>
- <span data-ttu-id="cc19c-215">**WinRM** : kan een externe sessie met de computer tot stand brengen met behulp van WS-Management.</span><span class="sxs-lookup"><span data-stu-id="cc19c-215">**WinRM** : Can establish a remote session to the computer by using WS-Management.</span></span>

<span data-ttu-id="cc19c-216">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="cc19c-216">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.WaitForServiceTypes
Parameter Sets: DefaultSet
Aliases:
Accepted values: Wmi, WinRM, PowerShell

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cc19c-217">-Force</span><span class="sxs-lookup"><span data-stu-id="cc19c-217">-Force</span></span>

<span data-ttu-id="cc19c-218">Hiermee wordt de computer direct opnieuw opgestart.</span><span class="sxs-lookup"><span data-stu-id="cc19c-218">Forces an immediate restart of the computer.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: f

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cc19c-219">-Imitatie</span><span class="sxs-lookup"><span data-stu-id="cc19c-219">-Impersonation</span></span>

<span data-ttu-id="cc19c-220">Hiermee geeft u het imitatie niveau op dat met deze cmdlet wordt gebruikt om WMI aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="cc19c-220">Specifies the impersonation level that this cmdlet uses to call WMI.</span></span> <span data-ttu-id="cc19c-221">`Restart-Computer` maakt gebruik van WMI.</span><span class="sxs-lookup"><span data-stu-id="cc19c-221">`Restart-Computer` uses WMI.</span></span>
<span data-ttu-id="cc19c-222">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="cc19c-222">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="cc19c-223">**Standaard** : standaard imitatie.</span><span class="sxs-lookup"><span data-stu-id="cc19c-223">**Default** : Default impersonation.</span></span> <span data-ttu-id="cc19c-224">Ondanks de naam is dit niet de standaard waarde.</span><span class="sxs-lookup"><span data-stu-id="cc19c-224">Despite the name, this isn't the default value.</span></span>
- <span data-ttu-id="cc19c-225">**Anoniem** : Hiermee verbergt u de identiteit van de aanroeper.</span><span class="sxs-lookup"><span data-stu-id="cc19c-225">**Anonymous** : Hides the identity of the caller.</span></span>
- <span data-ttu-id="cc19c-226">**Identify** : Hiermee kunnen objecten query's uitvoeren op de referenties van de aanroeper.</span><span class="sxs-lookup"><span data-stu-id="cc19c-226">**Identify** : Allows objects to query the credentials of the caller.</span></span>
- <span data-ttu-id="cc19c-227">**Nabooten** : Hiermee staat u toe dat objecten gebruikmaken van de referenties van de aanroeper.</span><span class="sxs-lookup"><span data-stu-id="cc19c-227">**Impersonate** : Allows objects to use the credentials of the caller.</span></span>

```yaml
Type: System.Management.ImpersonationLevel
Parameter Sets: (All)
Aliases:
Accepted values: Default, Anonymous, Identify, Impersonate, Delegate

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cc19c-228">-Protocol</span><span class="sxs-lookup"><span data-stu-id="cc19c-228">-Protocol</span></span>

<span data-ttu-id="cc19c-229">Hiermee geeft u het protocol op dat moet worden gebruikt om de computers opnieuw op te starten.</span><span class="sxs-lookup"><span data-stu-id="cc19c-229">Specifies which protocol to use to restart the computers.</span></span> <span data-ttu-id="cc19c-230">De geldige waarden zijn **WSMan** en **DCOM**.</span><span class="sxs-lookup"><span data-stu-id="cc19c-230">The valid values are **WSMan** and **DCOM**.</span></span>

<span data-ttu-id="cc19c-231">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="cc19c-231">This parameter is introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: DefaultSet
Aliases:
Accepted values: DCOM, WSMan

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cc19c-232">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="cc19c-232">-ThrottleLimit</span></span>

<span data-ttu-id="cc19c-233">Hiermee geeft u het maximum aantal gelijktijdige verbindingen op dat tot stand kan worden gebracht om deze opdracht uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="cc19c-233">Specifies the maximum number of concurrent connections that can be established to run this command.</span></span>
<span data-ttu-id="cc19c-234">De beperkings limiet geldt alleen voor de huidige opdracht, niet voor de sessie of voor de computer.</span><span class="sxs-lookup"><span data-stu-id="cc19c-234">The throttle limit applies only to the current command, not to the session or to the computer.</span></span>

<span data-ttu-id="cc19c-235">Als de para meter **ThrottleLimit** niet is opgegeven of als de waarde 0 wordt gebruikt, `Restart-Computer` wordt een maximum van 32 gelijktijdige verbindingen gebruikt.</span><span class="sxs-lookup"><span data-stu-id="cc19c-235">If the **ThrottleLimit** parameter isn't specified or a value of 0 is used, `Restart-Computer` uses a maximum of 32 concurrent connections.</span></span>

```yaml
Type: System.Int32
Parameter Sets: AsJobSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cc19c-236">-Time-out</span><span class="sxs-lookup"><span data-stu-id="cc19c-236">-Timeout</span></span>

<span data-ttu-id="cc19c-237">Hiermee geeft u de duur van de wacht tijd in seconden.</span><span class="sxs-lookup"><span data-stu-id="cc19c-237">Specifies the duration of the wait, in seconds.</span></span> <span data-ttu-id="cc19c-238">Wanneer de time-out is verstreken, `Restart-Computer` keert u terug naar de opdracht prompt, zelfs als de computers niet opnieuw worden opgestart.</span><span class="sxs-lookup"><span data-stu-id="cc19c-238">When the timeout elapses, `Restart-Computer` returns to the command prompt, even if the computers aren't restarted.</span></span>

<span data-ttu-id="cc19c-239">De **time-** outparameter is alleen geldig met de **wait** -para meter.</span><span class="sxs-lookup"><span data-stu-id="cc19c-239">The **Timeout** parameter is only valid with the **Wait** parameter.</span></span> <span data-ttu-id="cc19c-240">**Time-out** overschrijft de onbepaalde wacht tijd van de **wait** -para meter.</span><span class="sxs-lookup"><span data-stu-id="cc19c-240">**Timeout** overrides the **Wait** parameter's indefinite waiting period.</span></span>

<span data-ttu-id="cc19c-241">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="cc19c-241">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: DefaultSet
Aliases: TimeoutSec

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cc19c-242">-Wachten</span><span class="sxs-lookup"><span data-stu-id="cc19c-242">-Wait</span></span>

<span data-ttu-id="cc19c-243">`Restart-Computer` onderdrukt de Power shell-prompt en blokkeert de pijp lijn totdat de computers opnieuw zijn opgestart.</span><span class="sxs-lookup"><span data-stu-id="cc19c-243">`Restart-Computer` suppresses the PowerShell prompt and blocks the pipeline until the computers have restarted.</span></span> <span data-ttu-id="cc19c-244">U kunt deze para meter in een script gebruiken om computers opnieuw op te starten en vervolgens door gaan met het proces wanneer het opnieuw opstarten is voltooid.</span><span class="sxs-lookup"><span data-stu-id="cc19c-244">You can use this parameter in a script to restart computers and then continue to process when the restart is finished.</span></span>

<span data-ttu-id="cc19c-245">De **wacht** parameter voor onbepaalde tijd wacht op het opnieuw opstarten van de computers.</span><span class="sxs-lookup"><span data-stu-id="cc19c-245">The **Wait** parameter waits indefinitely for the computers to restart.</span></span> <span data-ttu-id="cc19c-246">U kunt **time-out** gebruiken om de timing en de para meters **voor** en **uitstel** in te stellen om te wachten tot bepaalde services beschikbaar zijn op de computers die opnieuw worden opgestart.</span><span class="sxs-lookup"><span data-stu-id="cc19c-246">You can use **Timeout** to adjust the timing and the **For** and **Delay** parameters to wait for particular services to become available on the restarted computers.</span></span>

<span data-ttu-id="cc19c-247">De **wait** -para meter is niet geldig wanneer u de lokale computer opnieuw opstart.</span><span class="sxs-lookup"><span data-stu-id="cc19c-247">The **Wait** parameter isn't valid when you're restarting the local computer.</span></span> <span data-ttu-id="cc19c-248">Als de waarde van de para meter **ComputerName** de namen van externe computers en de lokale computer bevat, wordt `Restart-Computer` er een niet-afsluit fout gegenereerd voor **wachten** op de lokale computer, maar wordt gewacht tot de externe computers opnieuw worden opgestart.</span><span class="sxs-lookup"><span data-stu-id="cc19c-248">If the value of the **ComputerName** parameter contains the names of remote computers and the local computer, `Restart-Computer` generates a non-terminating error for **Wait** on the local computer, but waits for the remote computers to restart.</span></span>

<span data-ttu-id="cc19c-249">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="cc19c-249">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DefaultSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cc19c-250">-WsmanAuthentication</span><span class="sxs-lookup"><span data-stu-id="cc19c-250">-WsmanAuthentication</span></span>

<span data-ttu-id="cc19c-251">Hiermee geeft u het mechanisme op dat wordt gebruikt voor het verifiëren van de gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="cc19c-251">Specifies the mechanism that is used to authenticate the user credentials.</span></span> <span data-ttu-id="cc19c-252">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="cc19c-252">This parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="cc19c-253">De acceptabele waarden voor deze para meter zijn: **Basic** , **CredSSP** , **default** , **Digest** , **Kerberos** en **Negotiate**.</span><span class="sxs-lookup"><span data-stu-id="cc19c-253">The acceptable values for this parameter are: **Basic** , **CredSSP** , **Default** , **Digest** , **Kerberos** , and **Negotiate**.</span></span>

<span data-ttu-id="cc19c-254">Zie [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="cc19c-254">For more information, see [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!WARNING]
> <span data-ttu-id="cc19c-255">CredSSP-verificatie (Credential Security service provider), waarbij de gebruikers referenties worden door gegeven aan een externe computer die moet worden geverifieerd, is ontworpen voor opdrachten waarvoor verificatie is vereist voor meer dan één bron, zoals het openen van een externe netwerk share.</span><span class="sxs-lookup"><span data-stu-id="cc19c-255">Credential Security Service Provider (CredSSP) authentication, in which the user credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="cc19c-256">Dit mechanisme verhoogt het beveiligings risico van de externe bewerking.</span><span class="sxs-lookup"><span data-stu-id="cc19c-256">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="cc19c-257">Als er is geknoeid met de externe computer, kunnen de referenties die aan worden door gegeven, worden gebruikt om de netwerk sessie te beheren.</span><span class="sxs-lookup"><span data-stu-id="cc19c-257">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

```yaml
Type: System.String
Parameter Sets: DefaultSet
Aliases:
Accepted values: Basic, CredSSP, Default, Digest, Kerberos, Negotiate

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cc19c-258">-Confirm</span><span class="sxs-lookup"><span data-stu-id="cc19c-258">-Confirm</span></span>

<span data-ttu-id="cc19c-259">Vraagt u om bevestiging voordat deze wordt uitgevoerd `Restart-Computer` .</span><span class="sxs-lookup"><span data-stu-id="cc19c-259">Prompts you for confirmation before running `Restart-Computer`.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cc19c-260">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="cc19c-260">-WhatIf</span></span>

<span data-ttu-id="cc19c-261">Laat zien wat er zou gebeuren als de `Restart-Computer` uitvoeringen wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="cc19c-261">Shows what would happen if the `Restart-Computer` runs.</span></span> <span data-ttu-id="cc19c-262">De `Restart-Computer` cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="cc19c-262">The `Restart-Computer` cmdlet isn't run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cc19c-263">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="cc19c-263">CommonParameters</span></span>

<span data-ttu-id="cc19c-264">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="cc19c-264">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="cc19c-265">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="cc19c-265">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="cc19c-266">INVOER</span><span class="sxs-lookup"><span data-stu-id="cc19c-266">INPUTS</span></span>

### <span data-ttu-id="cc19c-267">System. String</span><span class="sxs-lookup"><span data-stu-id="cc19c-267">System.String</span></span>

<span data-ttu-id="cc19c-268">`Restart-Computer` Hiermee worden computer namen van de pijp lijn of variabelen geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="cc19c-268">`Restart-Computer` accepts computer names from the pipeline or variables.</span></span>

<span data-ttu-id="cc19c-269">In Windows Power Shell 2,0 krijgt de para meter **ComputerName** alleen invoer van de pijp lijn op basis van de naam van de eigenschap.</span><span class="sxs-lookup"><span data-stu-id="cc19c-269">In Windows PowerShell 2.0, the **ComputerName** parameter takes input from the pipeline only by property name.</span></span> <span data-ttu-id="cc19c-270">In Windows Power Shell 3,0 en hoger neemt de para meter **ComputerName** de invoer van de pijp lijn op waarde.</span><span class="sxs-lookup"><span data-stu-id="cc19c-270">In Windows PowerShell 3.0, and later, the **ComputerName** parameter takes input from the pipeline by value.</span></span>

## <span data-ttu-id="cc19c-271">UITVOER</span><span class="sxs-lookup"><span data-stu-id="cc19c-271">OUTPUTS</span></span>

### <span data-ttu-id="cc19c-272">Geen, System. Management. Automation. RemotingJob</span><span class="sxs-lookup"><span data-stu-id="cc19c-272">None, System.Management.Automation.RemotingJob</span></span>

<span data-ttu-id="cc19c-273">Als u de para meter **AsJob** opgeeft, `Restart-Computer` wordt een taak object geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="cc19c-273">If you specify the **AsJob** parameter, `Restart-Computer` returns a job object.</span></span> <span data-ttu-id="cc19c-274">Anders wordt er geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="cc19c-274">Otherwise, no output is generated.</span></span>

## <span data-ttu-id="cc19c-275">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="cc19c-275">NOTES</span></span>

- <span data-ttu-id="cc19c-276">`Restart-Computer` werk alleen op computers met Windows en vereist WinRM en WMI om een systeem te afsluiten, inclusief het lokale systeem.</span><span class="sxs-lookup"><span data-stu-id="cc19c-276">`Restart-Computer` only work on computers running Windows and requires WinRM and WMI to shutdown a system, including the local system.</span></span>
- <span data-ttu-id="cc19c-277">`Restart-Computer` maakt gebruik van de [methode Win32Shutdown](/windows/desktop/CIMWin32Prov/win32shutdown-method-in-class-win32-operatingsystem) van de klasse Windows Management INSTRUMENTATION (WMI) [Win32_OperatingSystem](/windows/desktop/CIMWin32Prov/win32-operatingsystem) .</span><span class="sxs-lookup"><span data-stu-id="cc19c-277">`Restart-Computer` uses the [Win32Shutdown method](/windows/desktop/CIMWin32Prov/win32shutdown-method-in-class-win32-operatingsystem) of the Windows Management Instrumentation (WMI) [Win32_OperatingSystem](/windows/desktop/CIMWin32Prov/win32-operatingsystem) class.</span></span>  <span data-ttu-id="cc19c-278">Voor deze methode moet de bevoegdheid **SeShutdownPrivilege** zijn ingeschakeld voor het gebruikers account dat wordt gebruikt om de computer opnieuw op te starten.</span><span class="sxs-lookup"><span data-stu-id="cc19c-278">This method requires the **SeShutdownPrivilege** privilege be enabled for the user account used to restart the machine.</span></span>

<span data-ttu-id="cc19c-279">In Windows Power Shell 2,0 werkt de para meter **AsJob** niet betrouwbaar wanneer u externe computers opnieuw opstart of stopt.</span><span class="sxs-lookup"><span data-stu-id="cc19c-279">In Windows PowerShell 2.0, the **AsJob** parameter doesn't work reliably when you are restarting or stopping remote computers.</span></span> <span data-ttu-id="cc19c-280">In Windows Power Shell 3,0 is de implementatie gewijzigd om dit probleem op te lossen.</span><span class="sxs-lookup"><span data-stu-id="cc19c-280">In Windows PowerShell 3.0, the implementation is changed to resolve this problem.</span></span>

## <span data-ttu-id="cc19c-281">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="cc19c-281">RELATED LINKS</span></span>

[<span data-ttu-id="cc19c-282">Over Windows Remote Management</span><span class="sxs-lookup"><span data-stu-id="cc19c-282">About Windows Remote Management</span></span>](/windows/desktop/WinRM/about-windows-remote-management)

[<span data-ttu-id="cc19c-283">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="cc19c-283">Get-Credential</span></span>](../Microsoft.PowerShell.Security/Get-Credential.md)

[<span data-ttu-id="cc19c-284">WS-Management-protocol</span><span class="sxs-lookup"><span data-stu-id="cc19c-284">WS-Management Protocol</span></span>](/windows/desktop/WinRM/ws-management-protocol)
