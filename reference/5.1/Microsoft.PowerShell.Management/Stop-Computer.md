---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/11/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/stop-computer?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Computer
ms.openlocfilehash: 8062210aa94cb46d5e5557ede1bac672cae39622
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/23/2020
ms.locfileid: "93251497"
---
# <span data-ttu-id="efb17-103">Stop-Computer</span><span class="sxs-lookup"><span data-stu-id="efb17-103">Stop-Computer</span></span>

## <span data-ttu-id="efb17-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="efb17-104">SYNOPSIS</span></span>
<span data-ttu-id="efb17-105">Stopt (wordt afgesloten) van lokale en externe computers.</span><span class="sxs-lookup"><span data-stu-id="efb17-105">Stops (shuts down) local and remote computers.</span></span>

## <span data-ttu-id="efb17-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="efb17-106">SYNTAX</span></span>

### <span data-ttu-id="efb17-107">Alles</span><span class="sxs-lookup"><span data-stu-id="efb17-107">All</span></span>

```
Stop-Computer [-AsJob] [-DcomAuthentication <AuthenticationLevel>] [-WsmanAuthentication <String>]
 [-Protocol <String>] [[-ComputerName] <String[]>] [[-Credential] <PSCredential>]
 [-Impersonation <ImpersonationLevel>] [-ThrottleLimit <Int32>] [-Force] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="efb17-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="efb17-108">DESCRIPTION</span></span>

<span data-ttu-id="efb17-109">De `Stop-Computer` cmdlet sluit de lokale computer en externe computers.</span><span class="sxs-lookup"><span data-stu-id="efb17-109">The `Stop-Computer` cmdlet shuts down the local computer and remote computers.</span></span>

<span data-ttu-id="efb17-110">U kunt de para meters van gebruiken `Stop-Computer` om de afsluit bewerkingen uit te voeren als achtergrond taak, om de verificatie niveaus en alternatieve referenties op te geven, om de gelijktijdige verbindingen te beperken die worden gemaakt om de opdracht uit te voeren en om een onmiddellijke afsluit bewerking af te dwingen.</span><span class="sxs-lookup"><span data-stu-id="efb17-110">You can use the parameters of `Stop-Computer` to run the shutdown operations as a background job, to specify the authentication levels and alternate credentials, to limit the concurrent connections that are created to run the command, and to force an immediate shut down.</span></span>

<span data-ttu-id="efb17-111">Voor deze cmdlet is geen externe Power shell-communicatie vereist tenzij u de para meter **AsJob** gebruikt.</span><span class="sxs-lookup"><span data-stu-id="efb17-111">This cmdlet doesn't require PowerShell remoting unless you use the **AsJob** parameter.</span></span>

## <span data-ttu-id="efb17-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="efb17-112">EXAMPLES</span></span>

### <span data-ttu-id="efb17-113">Voor beeld 1: de lokale computer uitschakelen</span><span class="sxs-lookup"><span data-stu-id="efb17-113">Example 1: Shut down the local computer</span></span>

<span data-ttu-id="efb17-114">In dit voor beeld wordt de lokale computer afgesloten.</span><span class="sxs-lookup"><span data-stu-id="efb17-114">This example shuts down the local computer.</span></span>

```powershell
Stop-Computer -ComputerName localhost
```

### <span data-ttu-id="efb17-115">Voor beeld 2: twee externe computers en de lokale computer uitschakelen</span><span class="sxs-lookup"><span data-stu-id="efb17-115">Example 2: Shut down two remote computers and the local computer</span></span>

<span data-ttu-id="efb17-116">In dit voor beeld worden twee externe computers en de lokale computer gestopt.</span><span class="sxs-lookup"><span data-stu-id="efb17-116">This example stops two remote computers and the local computer.</span></span>

```powershell
Stop-Computer -ComputerName "Server01", "Server02", "localhost"
```

<span data-ttu-id="efb17-117">`Stop-Computer` maakt gebruik van de para meter **ComputerName** om twee externe computers en de lokale computer op te geven.</span><span class="sxs-lookup"><span data-stu-id="efb17-117">`Stop-Computer` uses the **ComputerName** parameter to specify two remote computers and the local computer.</span></span> <span data-ttu-id="efb17-118">Elke computer wordt afgesloten.</span><span class="sxs-lookup"><span data-stu-id="efb17-118">Each computer is shut down.</span></span>

### <span data-ttu-id="efb17-119">Voor beeld 3: externe computers afsluiten als achtergrond taak</span><span class="sxs-lookup"><span data-stu-id="efb17-119">Example 3: Shut down remote computers as a background job</span></span>

<span data-ttu-id="efb17-120">In dit voor beeld `Stop-Computer` wordt uitgevoerd als een achtergrond taak op twee externe computers.</span><span class="sxs-lookup"><span data-stu-id="efb17-120">In this example, `Stop-Computer` runs as a background job on two remote computers.</span></span>

```powershell
$j = Stop-Computer -ComputerName "Server01", "Server02" -AsJob
$results = $j | Receive-Job
$results
```

<span data-ttu-id="efb17-121">`Stop-Computer` maakt gebruik van de para meter **ComputerName** om twee externe computers op te geven.</span><span class="sxs-lookup"><span data-stu-id="efb17-121">`Stop-Computer` uses the **ComputerName** parameter to specify two remote computers.</span></span> <span data-ttu-id="efb17-122">De **AsJob** para meter voert de opdracht uit als achtergrond taak.</span><span class="sxs-lookup"><span data-stu-id="efb17-122">The **AsJob** parameter runs the command as a background job.</span></span> <span data-ttu-id="efb17-123">De taak objecten worden opgeslagen in de `$j` variabele.</span><span class="sxs-lookup"><span data-stu-id="efb17-123">The job objects are stored in the `$j` variable.</span></span>

<span data-ttu-id="efb17-124">De taak objecten in de `$j` variabele worden verzonden naar de pijp lijn naar `Receive-Job` , waardoor de taak resultaten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="efb17-124">The job objects in the `$j` variable are sent down the pipeline to `Receive-Job`, which gets the job results.</span></span> <span data-ttu-id="efb17-125">De objecten worden opgeslagen in de `$results` variabele.</span><span class="sxs-lookup"><span data-stu-id="efb17-125">The objects are stored in the `$results` variable.</span></span> <span data-ttu-id="efb17-126">`$results`Met de variabele wordt de taak informatie in de Power shell-console weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="efb17-126">The `$results` variable displays the job information in the PowerShell console.</span></span>

<span data-ttu-id="efb17-127">Omdat **AsJob** de taak op de lokale computer maakt en automatisch de resultaten naar de lokale computer retourneert, kunt u uitvoeren `Receive-Job` als een lokale opdracht.</span><span class="sxs-lookup"><span data-stu-id="efb17-127">Because **AsJob** creates the job on the local computer and automatically returns the results to the local computer, you can run `Receive-Job` as a local command.</span></span>

### <span data-ttu-id="efb17-128">Voor beeld 4: een externe computer afsluiten</span><span class="sxs-lookup"><span data-stu-id="efb17-128">Example 4: Shut down a remote computer</span></span>

<span data-ttu-id="efb17-129">In dit voor beeld wordt een externe computer met opgegeven verificatie afgesloten.</span><span class="sxs-lookup"><span data-stu-id="efb17-129">This example shuts down a remote computer using specified authentication.</span></span>

```powershell
Stop-Computer -ComputerName "Server01" -Impersonation Anonymous -DcomAuthentication PacketIntegrity
```

<span data-ttu-id="efb17-130">`Stop-Computer` maakt gebruik van de para meter **ComputerName** om de externe computer op te geven.</span><span class="sxs-lookup"><span data-stu-id="efb17-130">`Stop-Computer` uses the **ComputerName** parameter to specify the remote computer.</span></span> <span data-ttu-id="efb17-131">De **imitatie** parameter geeft een aangepaste imitatie op en de para meter **DcomAuthentication** geeft instellingen voor verificatie niveau.</span><span class="sxs-lookup"><span data-stu-id="efb17-131">The **Impersonation** parameter specifies a customized impersonation and the **DcomAuthentication** parameter specifies authentication-level settings.</span></span>

### <span data-ttu-id="efb17-132">Voor beeld 5: computers afsluiten in een domein</span><span class="sxs-lookup"><span data-stu-id="efb17-132">Example 5: Shut down computers in a domain</span></span>

<span data-ttu-id="efb17-133">In dit voor beeld forceren de opdrachten een onmiddellijke afsluiting van alle computers in een opgegeven domein.</span><span class="sxs-lookup"><span data-stu-id="efb17-133">In this example, the commands force an immediate shut down of all computers in a specified domain.</span></span>

```powershell
$s = Get-Content -Path ./Domain01.txt
$c = Get-Credential -Credential Domain01\Admin01
Stop-Computer -ComputerName $s -Force -ThrottleLimit 10 -Credential $c
```

<span data-ttu-id="efb17-134">`Get-Content` gebruikt de para meter **Path** om een bestand in de huidige map op te halen met de lijst van domein computers.</span><span class="sxs-lookup"><span data-stu-id="efb17-134">`Get-Content` uses the **Path** parameter to get a file in the current directory with the list of domain computers.</span></span> <span data-ttu-id="efb17-135">De objecten worden opgeslagen in de `$s` variabele.</span><span class="sxs-lookup"><span data-stu-id="efb17-135">The objects are stored in the `$s` variable.</span></span>

<span data-ttu-id="efb17-136">`Get-Credential` maakt gebruik van de para meter **Credential** om de referenties van een domein beheerder op te geven.</span><span class="sxs-lookup"><span data-stu-id="efb17-136">`Get-Credential` uses the **Credential** parameter to specify the credentials of a domain administrator.</span></span> <span data-ttu-id="efb17-137">De referenties worden opgeslagen in de `$c` variabele.</span><span class="sxs-lookup"><span data-stu-id="efb17-137">The credentials are stored in the `$c` variable.</span></span>

<span data-ttu-id="efb17-138">`Stop-Computer` de computers die zijn opgegeven met de **computer naam** parameter lijst van computers in de variabele worden afgesloten `$s` .</span><span class="sxs-lookup"><span data-stu-id="efb17-138">`Stop-Computer` shuts down the computers specified with the **ComputerName** parameter's list of computers in the `$s` variable.</span></span> <span data-ttu-id="efb17-139">Met de **Force** -para meter wordt direct afsluiten afgedwongen.</span><span class="sxs-lookup"><span data-stu-id="efb17-139">The **Force** parameter forces an immediate shutdown.</span></span> <span data-ttu-id="efb17-140">De para meter **ThrottleLimit** beperkt de opdracht tot tien gelijktijdige verbindingen.</span><span class="sxs-lookup"><span data-stu-id="efb17-140">The **ThrottleLimit** parameter limits the command to 10 concurrent connections.</span></span> <span data-ttu-id="efb17-141">De **referentie** parameter verzendt de referenties die zijn opgeslagen in de `$c` variabele.</span><span class="sxs-lookup"><span data-stu-id="efb17-141">The **Credential** parameter submits the credentials saved in the `$c` variable.</span></span>

## <span data-ttu-id="efb17-142">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="efb17-142">PARAMETERS</span></span>

### <span data-ttu-id="efb17-143">-AsJob</span><span class="sxs-lookup"><span data-stu-id="efb17-143">-AsJob</span></span>

<span data-ttu-id="efb17-144">Geeft aan dat deze cmdlet wordt uitgevoerd als een achtergrond taak.</span><span class="sxs-lookup"><span data-stu-id="efb17-144">Indicates that this cmdlet runs as a background job.</span></span>

<span data-ttu-id="efb17-145">Als u deze para meter wilt gebruiken, moeten de lokale en externe computers worden geconfigureerd voor externe toegang en, onder Windows Vista en latere versies van het Windows-besturings systeem, moet u Power shell openen met de optie **als administrator uitvoeren** .</span><span class="sxs-lookup"><span data-stu-id="efb17-145">To use this parameter, the local and remote computers must be configured for remoting and, on Windows Vista and later versions of the Windows operating system, you must open PowerShell by using the **Run as administrator** option.</span></span> <span data-ttu-id="efb17-146">Zie [about_Remote_Requirements](..//microsoft.powershell.core/about/about_remote_requirements.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="efb17-146">For more information, see [about_Remote_Requirements](..//microsoft.powershell.core/about/about_remote_requirements.md).</span></span>

<span data-ttu-id="efb17-147">Wanneer u de para meter **AsJob** opgeeft, retourneert de opdracht direct een object dat de achtergrond taak vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="efb17-147">When you specify the **AsJob** parameter, the command immediately returns an object that represents the background job.</span></span> <span data-ttu-id="efb17-148">U kunt in de sessie blijven werken terwijl de taak is voltooid.</span><span class="sxs-lookup"><span data-stu-id="efb17-148">You can continue to work in the session while the job finishes.</span></span> <span data-ttu-id="efb17-149">De taak wordt gemaakt op de lokale computer en de resultaten van externe computers worden automatisch geretourneerd naar de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="efb17-149">The job is created on the local computer and the results from remote computers are automatically returned to the local computer.</span></span> <span data-ttu-id="efb17-150">Gebruik de cmdlet om de taak resultaten te verkrijgen `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="efb17-150">To get the job results, use the `Receive-Job` cmdlet.</span></span>

<span data-ttu-id="efb17-151">Zie [about_Jobs](..//microsoft.powershell.core/about/about_jobs.md) en [about_Remote_Jobs](../microsoft.powershell.core/about/about_remote_jobs.md)voor meer informatie over Power shell-achtergrond taken.</span><span class="sxs-lookup"><span data-stu-id="efb17-151">For more information about PowerShell background jobs, see [about_Jobs](..//microsoft.powershell.core/about/about_jobs.md) and [about_Remote_Jobs](../microsoft.powershell.core/about/about_remote_jobs.md).</span></span>

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

### <span data-ttu-id="efb17-152">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="efb17-152">-ComputerName</span></span>

<span data-ttu-id="efb17-153">Hiermee geeft u de computers op die moeten worden gestopt.</span><span class="sxs-lookup"><span data-stu-id="efb17-153">Specifies the computers to stop.</span></span> <span data-ttu-id="efb17-154">Standaard is dit de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="efb17-154">The default is the local computer.</span></span>

<span data-ttu-id="efb17-155">Typ de NETBIOS-naam, het IP-adres of de Fully Qualified Domain Name van een of meer computers in een lijst met door komma's gescheiden waarden.</span><span class="sxs-lookup"><span data-stu-id="efb17-155">Type the NETBIOS name, IP address, or fully qualified domain name of one or more computers in a comma-separated list.</span></span> <span data-ttu-id="efb17-156">Als u de lokale computer wilt opgeven, typt u de naam van de computer of localhost.</span><span class="sxs-lookup"><span data-stu-id="efb17-156">To specify the local computer, type the computer name or localhost.</span></span>

<span data-ttu-id="efb17-157">Deze para meter is niet afhankelijk van externe communicatie met Power shell.</span><span class="sxs-lookup"><span data-stu-id="efb17-157">This parameter doesn't rely on PowerShell remoting.</span></span> <span data-ttu-id="efb17-158">U kunt de para meter **ComputerName** ook gebruiken als uw computer niet is geconfigureerd om externe opdrachten uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="efb17-158">You can use the **ComputerName** parameter even if your computer isn't configured to run remote commands.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN, __SERVER, Server, IPAddress

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="efb17-159">-Confirm</span><span class="sxs-lookup"><span data-stu-id="efb17-159">-Confirm</span></span>

<span data-ttu-id="efb17-160">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="efb17-160">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="efb17-161">-Credential</span><span class="sxs-lookup"><span data-stu-id="efb17-161">-Credential</span></span>

<span data-ttu-id="efb17-162">Hiermee geeft u een gebruikers account op dat gemachtigd is om deze actie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="efb17-162">Specifies a user account that has permission to do this action.</span></span> <span data-ttu-id="efb17-163">Standaard is dit de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="efb17-163">The default is the current user.</span></span>

<span data-ttu-id="efb17-164">Typ een gebruikers naam, zoals **gebruiker01** of **Domain01\User01** , of voer een **PSCredential** -object in dat door de cmdlet wordt gegenereerd `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="efb17-164">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="efb17-165">Als u een gebruikers naam typt, wordt u gevraagd het wacht woord in te voeren.</span><span class="sxs-lookup"><span data-stu-id="efb17-165">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="efb17-166">Referenties worden opgeslagen in een [PSCredential](/dotnet/api/system.management.automation.pscredential) -object en het wacht woord wordt opgeslagen als [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="efb17-166">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="efb17-167">Zie [Hoe veilig is securestring?](/dotnet/api/system.security.securestring#how-secure-is-securestring)voor meer informatie over **securestring** Data Protection.</span><span class="sxs-lookup"><span data-stu-id="efb17-167">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="efb17-168">-DcomAuthentication</span><span class="sxs-lookup"><span data-stu-id="efb17-168">-DcomAuthentication</span></span>

<span data-ttu-id="efb17-169">Hiermee geeft u het verificatie niveau op dat met deze cmdlet wordt gebruikt met WMI.</span><span class="sxs-lookup"><span data-stu-id="efb17-169">Specifies the authentication level that this cmdlet uses with WMI.</span></span> <span data-ttu-id="efb17-170">`Stop-Computer` maakt gebruik van WMI.</span><span class="sxs-lookup"><span data-stu-id="efb17-170">`Stop-Computer` uses WMI.</span></span> <span data-ttu-id="efb17-171">De standaard waarde is **pakket**.</span><span class="sxs-lookup"><span data-stu-id="efb17-171">The default value is **Packet**.</span></span>

<span data-ttu-id="efb17-172">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="efb17-172">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="efb17-173">**Standaard** : Windows-verificatie.</span><span class="sxs-lookup"><span data-stu-id="efb17-173">**Default** : Windows Authentication.</span></span>
- <span data-ttu-id="efb17-174">**Geen** : geen com-verificatie.</span><span class="sxs-lookup"><span data-stu-id="efb17-174">**None** : No COM authentication.</span></span>
- <span data-ttu-id="efb17-175">**Verbinding maken** : com-verificatie op verbinding niveau.</span><span class="sxs-lookup"><span data-stu-id="efb17-175">**Connect** : Connect-level COM authentication.</span></span>
- <span data-ttu-id="efb17-176">**Aanroep** : com-verificatie op aanroepen niveau.</span><span class="sxs-lookup"><span data-stu-id="efb17-176">**Call** : Call-level COM authentication.</span></span>
- <span data-ttu-id="efb17-177">**Pakket** : com-verificatie op pakket niveau.</span><span class="sxs-lookup"><span data-stu-id="efb17-177">**Packet** : Packet-level COM authentication.</span></span>
- <span data-ttu-id="efb17-178">**PacketIntegrity** : com-verificatie op pakket integriteit-niveau.</span><span class="sxs-lookup"><span data-stu-id="efb17-178">**PacketIntegrity** : Packet Integrity-level COM authentication.</span></span>
- <span data-ttu-id="efb17-179">**PacketPrivacy** : com-verificatie op privacyniveau op pakket niveau.</span><span class="sxs-lookup"><span data-stu-id="efb17-179">**PacketPrivacy** : Packet Privacy-level COM authentication.</span></span>
- <span data-ttu-id="efb17-180">**Ongewijzigd** : hetzelfde als de vorige opdracht.</span><span class="sxs-lookup"><span data-stu-id="efb17-180">**Unchanged** : Same as the previous command.</span></span>

<span data-ttu-id="efb17-181">Zie [authenticationLevel](/dotnet/api/system.management.authenticationlevel)voor meer informatie over de waarden van deze para meter.</span><span class="sxs-lookup"><span data-stu-id="efb17-181">For more information about the values of this parameter, see [AuthenticationLevel](/dotnet/api/system.management.authenticationlevel).</span></span>

```yaml
Type: System.Management.AuthenticationLevel
Parameter Sets: (All)
Aliases: Authentication
Accepted values: Default, None, Connect, Call, Packet, PacketIntegrity, PacketPrivacy, Unchanged

Required: False
Position: Named
Default value: Packet
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="efb17-182">-Force</span><span class="sxs-lookup"><span data-stu-id="efb17-182">-Force</span></span>

<span data-ttu-id="efb17-183">Hiermee wordt de computer onmiddellijk afgesloten.</span><span class="sxs-lookup"><span data-stu-id="efb17-183">Forces an immediate shut down of the computer.</span></span>

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

### <span data-ttu-id="efb17-184">-Imitatie</span><span class="sxs-lookup"><span data-stu-id="efb17-184">-Impersonation</span></span>

<span data-ttu-id="efb17-185">Hiermee geeft u het imitatie niveau op dat moet worden gebruikt wanneer deze cmdlet WMI aanroept.</span><span class="sxs-lookup"><span data-stu-id="efb17-185">Specifies the impersonation level to use when this cmdlet calls WMI.</span></span> <span data-ttu-id="efb17-186">De standaard waarde is **imiteren**.</span><span class="sxs-lookup"><span data-stu-id="efb17-186">The default value is **Impersonate**.</span></span>

<span data-ttu-id="efb17-187">`Stop-Computer` maakt gebruik van WMI.</span><span class="sxs-lookup"><span data-stu-id="efb17-187">`Stop-Computer` uses WMI.</span></span> <span data-ttu-id="efb17-188">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="efb17-188">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="efb17-189">**Standaard** : standaard imitatie.</span><span class="sxs-lookup"><span data-stu-id="efb17-189">**Default** : Default impersonation.</span></span>
- <span data-ttu-id="efb17-190">**Anoniem** : Hiermee verbergt u de identiteit van de aanroeper.</span><span class="sxs-lookup"><span data-stu-id="efb17-190">**Anonymous** : Hides the identity of the caller.</span></span>
- <span data-ttu-id="efb17-191">**Identify** : Hiermee kunnen objecten query's uitvoeren op de referenties van de aanroeper.</span><span class="sxs-lookup"><span data-stu-id="efb17-191">**Identify** : Allows objects to query the credentials of the caller.</span></span>
- <span data-ttu-id="efb17-192">**Nabooten** : Hiermee staat u toe dat objecten gebruikmaken van de referenties van de aanroeper.</span><span class="sxs-lookup"><span data-stu-id="efb17-192">**Impersonate** : Allows objects to use the credentials of the caller.</span></span>

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

### <span data-ttu-id="efb17-193">-Protocol</span><span class="sxs-lookup"><span data-stu-id="efb17-193">-Protocol</span></span>

<span data-ttu-id="efb17-194">Hiermee geeft u het protocol op dat moet worden gebruikt om de computers opnieuw op te starten.</span><span class="sxs-lookup"><span data-stu-id="efb17-194">Specifies which protocol to use to restart the computers.</span></span> <span data-ttu-id="efb17-195">De acceptabele waarden voor deze para meter zijn: **WSMan** en **DCOM**.</span><span class="sxs-lookup"><span data-stu-id="efb17-195">The acceptable values for this parameter are: **WSMan** and **DCOM**.</span></span> <span data-ttu-id="efb17-196">De standaard waarde is **DCOM**.</span><span class="sxs-lookup"><span data-stu-id="efb17-196">The default value is **DCOM**.</span></span>

<span data-ttu-id="efb17-197">Deze para meter is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="efb17-197">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: DCOM, WSMan

Required: False
Position: Named
Default value: DCOM
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="efb17-198">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="efb17-198">-ThrottleLimit</span></span>

<span data-ttu-id="efb17-199">Hiermee geeft u het maximum aantal gelijktijdige verbindingen op dat tot stand kan worden gebracht om deze opdracht uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="efb17-199">Specifies the maximum number of concurrent connections that can be established to run this command.</span></span>
<span data-ttu-id="efb17-200">Als u deze para meter weglaat of een waarde van 0 invoert, wordt de standaard waarde 32 gebruikt.</span><span class="sxs-lookup"><span data-stu-id="efb17-200">If you omit this parameter or enter a value of 0, the default value, 32, is used.</span></span>

<span data-ttu-id="efb17-201">De beperkings limiet geldt alleen voor de huidige opdracht, niet voor de sessie of voor de computer.</span><span class="sxs-lookup"><span data-stu-id="efb17-201">The throttle limit applies only to the current command, not to the session or to the computer.</span></span>

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

### <span data-ttu-id="efb17-202">-WsmanAuthentication</span><span class="sxs-lookup"><span data-stu-id="efb17-202">-WsmanAuthentication</span></span>

<span data-ttu-id="efb17-203">Hiermee geeft u het mechanisme op dat wordt gebruikt voor het verifiëren van de gebruikers referenties wanneer deze cmdlet gebruikmaakt van het WSMan-protocol.</span><span class="sxs-lookup"><span data-stu-id="efb17-203">Specifies the mechanism that is used to authenticate the user credentials when this cmdlet uses the WSMan protocol.</span></span> <span data-ttu-id="efb17-204">De standaard waarde is **standaard**.</span><span class="sxs-lookup"><span data-stu-id="efb17-204">The default value is **Default**.</span></span>

<span data-ttu-id="efb17-205">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="efb17-205">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="efb17-206">Basic</span><span class="sxs-lookup"><span data-stu-id="efb17-206">Basic</span></span>
- <span data-ttu-id="efb17-207">CredSSP</span><span class="sxs-lookup"><span data-stu-id="efb17-207">CredSSP</span></span>
- <span data-ttu-id="efb17-208">Standaard</span><span class="sxs-lookup"><span data-stu-id="efb17-208">Default</span></span>
- <span data-ttu-id="efb17-209">Samenvatting</span><span class="sxs-lookup"><span data-stu-id="efb17-209">Digest</span></span>
- <span data-ttu-id="efb17-210">Kerberos</span><span class="sxs-lookup"><span data-stu-id="efb17-210">Kerberos</span></span>
- <span data-ttu-id="efb17-211">Afspraken.</span><span class="sxs-lookup"><span data-stu-id="efb17-211">Negotiate.</span></span>

<span data-ttu-id="efb17-212">Zie [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)voor meer informatie over de waarden van deze para meter.</span><span class="sxs-lookup"><span data-stu-id="efb17-212">For more information about the values of this parameter, see [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!CAUTION]
> <span data-ttu-id="efb17-213">CredSSP-verificatie (Credential Security service provider), waarbij de gebruikers referenties worden door gegeven aan een externe computer die moet worden geverifieerd, is ontworpen voor opdrachten waarvoor verificatie is vereist voor meer dan één bron, zoals het openen van een externe netwerk share.</span><span class="sxs-lookup"><span data-stu-id="efb17-213">Credential Security Service Provider (CredSSP) authentication, in which the user credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="efb17-214">Dit mechanisme verhoogt het beveiligings risico van de externe bewerking.</span><span class="sxs-lookup"><span data-stu-id="efb17-214">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="efb17-215">Als er is geknoeid met de externe computer, kunnen de referenties die aan worden door gegeven, worden gebruikt om de netwerk sessie te beheren.</span><span class="sxs-lookup"><span data-stu-id="efb17-215">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

<span data-ttu-id="efb17-216">Deze para meter is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="efb17-216">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="efb17-217">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="efb17-217">-WhatIf</span></span>

<span data-ttu-id="efb17-218">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="efb17-218">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="efb17-219">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="efb17-219">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="efb17-220">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="efb17-220">CommonParameters</span></span>

<span data-ttu-id="efb17-221">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="efb17-221">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="efb17-222">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="efb17-222">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="efb17-223">INVOER</span><span class="sxs-lookup"><span data-stu-id="efb17-223">INPUTS</span></span>

### <span data-ttu-id="efb17-224">Geen</span><span class="sxs-lookup"><span data-stu-id="efb17-224">None</span></span>

<span data-ttu-id="efb17-225">U kunt invoer niet naar deze cmdlet pipeen.</span><span class="sxs-lookup"><span data-stu-id="efb17-225">You can't pipe input to this cmdlet.</span></span>

## <span data-ttu-id="efb17-226">UITVOER</span><span class="sxs-lookup"><span data-stu-id="efb17-226">OUTPUTS</span></span>

### <span data-ttu-id="efb17-227">Geen of System. Management. Automation. RemotingJob</span><span class="sxs-lookup"><span data-stu-id="efb17-227">None or System.Management.Automation.RemotingJob</span></span>

<span data-ttu-id="efb17-228">De cmdlet retourneert een **System. Management. Automation. RemotingJob** -object, als u de para meter **AsJob** opgeeft.</span><span class="sxs-lookup"><span data-stu-id="efb17-228">The cmdlet returns a **System.Management.Automation.RemotingJob** object, if you specify the **AsJob** parameter.</span></span> <span data-ttu-id="efb17-229">Anders wordt er geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="efb17-229">Otherwise, it doesn't generate any output.</span></span>

## <span data-ttu-id="efb17-230">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="efb17-230">NOTES</span></span>

<span data-ttu-id="efb17-231">Deze cmdlet maakt gebruik van de methode **Win32Shutdown** van de WMI-klasse **Win32_OperatingSystem** .</span><span class="sxs-lookup"><span data-stu-id="efb17-231">This cmdlet uses the **Win32Shutdown** method of the **Win32_OperatingSystem** WMI class.</span></span> <span data-ttu-id="efb17-232">Voor deze methode moet de bevoegdheid **SeShutdownPrivilege** zijn ingeschakeld voor het gebruikers account dat wordt gebruikt om de computer opnieuw op te starten.</span><span class="sxs-lookup"><span data-stu-id="efb17-232">This method requires the **SeShutdownPrivilege** privilege be enabled for the user account used to restart the machine.</span></span>

## <span data-ttu-id="efb17-233">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="efb17-233">RELATED LINKS</span></span>

[<span data-ttu-id="efb17-234">Add-computer</span><span class="sxs-lookup"><span data-stu-id="efb17-234">Add-Computer</span></span>](Add-Computer.md)

[<span data-ttu-id="efb17-235">Checkpoint-Computer</span><span class="sxs-lookup"><span data-stu-id="efb17-235">Checkpoint-Computer</span></span>](Checkpoint-Computer.md)

[<span data-ttu-id="efb17-236">Verwijderen-computer</span><span class="sxs-lookup"><span data-stu-id="efb17-236">Remove-Computer</span></span>](Remove-Computer.md)

[<span data-ttu-id="efb17-237">Naam wijzigen-computer</span><span class="sxs-lookup"><span data-stu-id="efb17-237">Rename-Computer</span></span>](Rename-Computer.md)

[<span data-ttu-id="efb17-238">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="efb17-238">Restart-Computer</span></span>](Restart-Computer.md)

[<span data-ttu-id="efb17-239">Herstellen-computer</span><span class="sxs-lookup"><span data-stu-id="efb17-239">Restore-Computer</span></span>](Restore-Computer.md)

[<span data-ttu-id="efb17-240">Test-Connection</span><span class="sxs-lookup"><span data-stu-id="efb17-240">Test-Connection</span></span>](Test-Connection.md)
