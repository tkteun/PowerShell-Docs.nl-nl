---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 6/17/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/restart-computer?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Restart-Computer
ms.openlocfilehash: 623b7bb0084c7fe7822509081d141ddcccf0057a
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/07/2020
ms.locfileid: "94347326"
---
# <span data-ttu-id="f1f18-103">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="f1f18-103">Restart-Computer</span></span>

## <span data-ttu-id="f1f18-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="f1f18-104">SYNOPSIS</span></span>
<span data-ttu-id="f1f18-105">Hiermee wordt het besturings systeem opnieuw opgestart op lokale en externe computers.</span><span class="sxs-lookup"><span data-stu-id="f1f18-105">Restarts the operating system on local and remote computers.</span></span>

## <span data-ttu-id="f1f18-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="f1f18-106">SYNTAX</span></span>

### <span data-ttu-id="f1f18-107">Standaardset (standaard)</span><span class="sxs-lookup"><span data-stu-id="f1f18-107">DefaultSet (Default)</span></span>

```
Restart-Computer [-WsmanAuthentication <String>] [[-ComputerName] <String[]>]
 [[-Credential]<PSCredential>] [-Force] [-Wait] [-Timeout <Int32>] [-For <WaitForServiceTypes>]
 [-Delay <Int16>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="f1f18-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="f1f18-108">DESCRIPTION</span></span>

<span data-ttu-id="f1f18-109">`Restart-Computer`Met de cmdlet wordt het besturings systeem opnieuw gestart op de lokale en externe computers.</span><span class="sxs-lookup"><span data-stu-id="f1f18-109">The `Restart-Computer` cmdlet restarts the operating system on the local and remote computers.</span></span>

<span data-ttu-id="f1f18-110">U kunt de para meters van gebruiken `Restart-Computer` om de bewerkingen voor opnieuw opstarten uit te voeren, de verificatie niveaus en alternatieve referenties op te geven, om de bewerkingen die tegelijkertijd worden uitgevoerd, te beperken en onmiddellijk opnieuw op te starten.</span><span class="sxs-lookup"><span data-stu-id="f1f18-110">You can use the parameters of `Restart-Computer` to run the restart operations, to specify the authentication levels and alternate credentials, to limit the operations that run at the same time, and to force an immediate restart.</span></span>

<span data-ttu-id="f1f18-111">Vanaf Windows Power Shell 3,0 kunt u wachten tot de herstart is voltooid voordat u de volgende opdracht uitvoert.</span><span class="sxs-lookup"><span data-stu-id="f1f18-111">Starting in Windows PowerShell 3.0, you can wait for the restart to complete before you run the next command.</span></span> <span data-ttu-id="f1f18-112">Geef een time-out op voor de wacht tijd en het query-interval, en wacht totdat bepaalde services beschikbaar zijn op de computer die opnieuw is opgestart.</span><span class="sxs-lookup"><span data-stu-id="f1f18-112">Specify a waiting time-out and query interval, and wait for particular services to be available on the restarted computer.</span></span> <span data-ttu-id="f1f18-113">Deze functie maakt het handig om te gebruiken `Restart-Computer` in scripts en functies.</span><span class="sxs-lookup"><span data-stu-id="f1f18-113">This feature makes it practical to use `Restart-Computer` in scripts and functions.</span></span>

## <span data-ttu-id="f1f18-114">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="f1f18-114">EXAMPLES</span></span>

### <span data-ttu-id="f1f18-115">Voor beeld 1: de lokale computer opnieuw opstarten</span><span class="sxs-lookup"><span data-stu-id="f1f18-115">Example 1: Restart the local computer</span></span>

<span data-ttu-id="f1f18-116">`Restart-Computer` Hiermee wordt de lokale computer opnieuw opgestart.</span><span class="sxs-lookup"><span data-stu-id="f1f18-116">`Restart-Computer` restarts the local computer.</span></span>

```powershell
Restart-Computer
```

### <span data-ttu-id="f1f18-117">Voor beeld 2: meerdere computers opnieuw opstarten</span><span class="sxs-lookup"><span data-stu-id="f1f18-117">Example 2: Restart multiple computers</span></span>

<span data-ttu-id="f1f18-118">`Restart-Computer` externe en lokale computers kunnen opnieuw worden gestart.</span><span class="sxs-lookup"><span data-stu-id="f1f18-118">`Restart-Computer` can restart remote and local computers.</span></span> <span data-ttu-id="f1f18-119">De para meter **ComputerName** accepteert een matrix met computer namen.</span><span class="sxs-lookup"><span data-stu-id="f1f18-119">The **ComputerName** parameter accepts an array of computer names.</span></span>

```powershell
Restart-Computer -ComputerName Server01, Server02, localhost
```

### <span data-ttu-id="f1f18-120">Voor beeld 3: computer namen uit een tekst bestand ophalen</span><span class="sxs-lookup"><span data-stu-id="f1f18-120">Example 3: Get computer names from a text file</span></span>

<span data-ttu-id="f1f18-121">`Restart-Computer` Hiermee wordt een lijst met computer namen opgehaald uit een tekst bestand en worden de computers opnieuw opgestart.</span><span class="sxs-lookup"><span data-stu-id="f1f18-121">`Restart-Computer` gets a list of computer names from a text file and restarts the computers.</span></span> <span data-ttu-id="f1f18-122">De para meter **ComputerName** is niet opgegeven.</span><span class="sxs-lookup"><span data-stu-id="f1f18-122">The **ComputerName** parameter isn't specified.</span></span> <span data-ttu-id="f1f18-123">Maar omdat het de eerste positie parameter is, accepteert de computer namen van het tekst bestand dat naar de pijp lijn wordt verzonden.</span><span class="sxs-lookup"><span data-stu-id="f1f18-123">But because it's the first position parameter, it accepts the computer names from the text file that are sent down the pipeline.</span></span>

```powershell
Get-Content -Path C:\Domain01.txt | Restart-Computer
```

<span data-ttu-id="f1f18-124">`Get-Content` gebruikt de para meter **Path** voor het ophalen van een lijst met computer namen uit een tekst bestand **Domain01.txt**.</span><span class="sxs-lookup"><span data-stu-id="f1f18-124">`Get-Content` uses the **Path** parameter to get a list of computer names from a text file, **Domain01.txt**.</span></span> <span data-ttu-id="f1f18-125">De computer namen worden verzonden naar de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="f1f18-125">The computer names are sent down the pipeline.</span></span> <span data-ttu-id="f1f18-126">`Restart-Computer` Hiermee wordt elke computer opnieuw opgestart.</span><span class="sxs-lookup"><span data-stu-id="f1f18-126">`Restart-Computer` restarts each computer.</span></span>

### <span data-ttu-id="f1f18-127">Voor beeld 4: opnieuw opstarten afdwingen van computers die worden vermeld in een tekst bestand</span><span class="sxs-lookup"><span data-stu-id="f1f18-127">Example 4: Force restart of computers listed in a text file</span></span>

<span data-ttu-id="f1f18-128">In dit voor beeld wordt een onmiddellijke herstart van de computers die in het bestand worden vermeld, geforceerd `Domain01.txt` .</span><span class="sxs-lookup"><span data-stu-id="f1f18-128">This example forces an immediate restart of the computers listed in the `Domain01.txt` file.</span></span> <span data-ttu-id="f1f18-129">De computer namen uit het tekst bestand worden opgeslagen in een variabele.</span><span class="sxs-lookup"><span data-stu-id="f1f18-129">The computer names from the text file are stored in a variable.</span></span> <span data-ttu-id="f1f18-130">De **Force** -para meter dwingt onmiddellijk opnieuw op te starten.</span><span class="sxs-lookup"><span data-stu-id="f1f18-130">The **Force** parameter forces an immediate restart.</span></span>

```powershell
$Names = Get-Content -Path C:\Domain01.txt
$Creds = Get-Credential
Restart-Computer -ComputerName $Names -Credential $Creds -Force
```

<span data-ttu-id="f1f18-131">`Get-Content` gebruikt de para meter **Path** voor het ophalen van een lijst met computer namen uit een tekst bestand **Domain01.txt**.</span><span class="sxs-lookup"><span data-stu-id="f1f18-131">`Get-Content` uses the **Path** parameter to get a list of computer names from a text file, **Domain01.txt**.</span></span> <span data-ttu-id="f1f18-132">De computer namen worden opgeslagen in de variabele `$Names` .</span><span class="sxs-lookup"><span data-stu-id="f1f18-132">The computer names are stored in the variable `$Names`.</span></span> <span data-ttu-id="f1f18-133">`Get-Credential` vraagt u om een gebruikers naam en wacht woord en slaat de waarden op in de variabele `$Creds` .</span><span class="sxs-lookup"><span data-stu-id="f1f18-133">`Get-Credential` prompts you for a username and password and stores the values in the variable `$Creds`.</span></span> <span data-ttu-id="f1f18-134">`Restart-Computer` maakt gebruik van de **computer naam** en de **referentie** parameters met hun variabelen.</span><span class="sxs-lookup"><span data-stu-id="f1f18-134">`Restart-Computer` uses the **ComputerName** and **Credential** parameters with their variables.</span></span> <span data-ttu-id="f1f18-135">De para meter **Force** zorgt ervoor dat elke computer direct opnieuw wordt opgestart.</span><span class="sxs-lookup"><span data-stu-id="f1f18-135">The **Force** parameter causes an immediate restart of each computer.</span></span>

### <span data-ttu-id="f1f18-136">Voor beeld 6: een externe computer opnieuw opstarten en wachten op Power shell</span><span class="sxs-lookup"><span data-stu-id="f1f18-136">Example 6: Restart a remote computer and wait for PowerShell</span></span>

<span data-ttu-id="f1f18-137">`Restart-Computer` Start de externe computer opnieuw op en wacht vijf minuten (300 seconden), waarna Power shell beschikbaar wordt op de computer die opnieuw is opgestart voordat deze doorgaat.</span><span class="sxs-lookup"><span data-stu-id="f1f18-137">`Restart-Computer` restarts the remote computer and then waits up to 5 minutes (300 seconds) for PowerShell to become available on the restarted computer before it continues.</span></span>

```powershell
Restart-Computer -ComputerName Server01 -Wait -For PowerShell -Timeout 300 -Delay 2
```

<span data-ttu-id="f1f18-138">`Restart-Computer` maakt gebruik van de para meter **ComputerName** om **Server01** op te geven.</span><span class="sxs-lookup"><span data-stu-id="f1f18-138">`Restart-Computer` uses the **ComputerName** parameter to specify **Server01**.</span></span> <span data-ttu-id="f1f18-139">De **wait** -para meter wacht totdat de herstart is voltooid.</span><span class="sxs-lookup"><span data-stu-id="f1f18-139">The **Wait** parameter waits for the restart to finish.</span></span> <span data-ttu-id="f1f18-140">Met de **for** geeft u op dat Power shell opdrachten kan uitvoeren op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="f1f18-140">The **For** specifies that PowerShell can run commands on the remote computer.</span></span> <span data-ttu-id="f1f18-141">De **time-** outpara meter geeft een wacht tijd van vijf minuten.</span><span class="sxs-lookup"><span data-stu-id="f1f18-141">The **Timeout** parameter specifies a five-minute wait.</span></span> <span data-ttu-id="f1f18-142">De **vertragings** parameter voert elke twee seconden een query uit op de externe computer om vast te stellen of deze opnieuw wordt opgestart.</span><span class="sxs-lookup"><span data-stu-id="f1f18-142">The **Delay** parameter queries the remote computer every two seconds to determine whether it's restarted.</span></span>

### <span data-ttu-id="f1f18-143">Voor beeld 7: een computer opnieuw opstarten met behulp van WsmanAuthentication</span><span class="sxs-lookup"><span data-stu-id="f1f18-143">Example 7: Restart a computer by using WsmanAuthentication</span></span>

<span data-ttu-id="f1f18-144">`Restart-Computer` Hiermee wordt de externe computer opnieuw opgestart met behulp van het **WsmanAuthentication** -mechanisme.</span><span class="sxs-lookup"><span data-stu-id="f1f18-144">`Restart-Computer` restarts the remote computer using the **WsmanAuthentication** mechanism.</span></span>
<span data-ttu-id="f1f18-145">Met Kerberos-verificatie wordt bepaald of de huidige gebruiker gemachtigd is om de externe computer opnieuw op te starten.</span><span class="sxs-lookup"><span data-stu-id="f1f18-145">Kerberos authentication determines whether the current user has permission to restart the remote computer.</span></span> <span data-ttu-id="f1f18-146">Zie [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="f1f18-146">For more information, see [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

```powershell
Restart-Computer -ComputerName Server01 -WsmanAuthentication Kerberos
```

<span data-ttu-id="f1f18-147">`Restart-Computer` maakt gebruik van de para meter **ComputerName** om de externe computer op te geven, **Server01**.</span><span class="sxs-lookup"><span data-stu-id="f1f18-147">`Restart-Computer` uses the **ComputerName** parameter to specify the remote computer, **Server01**.</span></span>
<span data-ttu-id="f1f18-148">De **WsmanAuthentication** para meter geeft u de verificatie methode op als **Kerberos**.</span><span class="sxs-lookup"><span data-stu-id="f1f18-148">The **WsmanAuthentication** parameter specifies the authentication method as **Kerberos**.</span></span>

## <span data-ttu-id="f1f18-149">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f1f18-149">PARAMETERS</span></span>

### <span data-ttu-id="f1f18-150">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="f1f18-150">-ComputerName</span></span>

<span data-ttu-id="f1f18-151">Hiermee geeft u een computer naam of een door komma's gescheiden matrix van computer namen op.</span><span class="sxs-lookup"><span data-stu-id="f1f18-151">Specifies one computer name or a comma-separated array of computer names.</span></span> <span data-ttu-id="f1f18-152">`Restart-Computer` Hiermee worden **computer naam** objecten van de pijp lijn of variabelen geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="f1f18-152">`Restart-Computer` accepts **ComputerName** objects from the pipeline or variables.</span></span>

<span data-ttu-id="f1f18-153">Typ de NetBIOS-naam, een IP-adres of een Fully Qualified Domain Name van een externe computer.</span><span class="sxs-lookup"><span data-stu-id="f1f18-153">Type the NetBIOS name, an IP address, or a fully qualified domain name of a remote computer.</span></span> <span data-ttu-id="f1f18-154">Als u de lokale computer wilt opgeven, typt u de naam van de computer, een punt `.` of localhost.</span><span class="sxs-lookup"><span data-stu-id="f1f18-154">To specify the local computer, type the computer name, a dot `.`, or localhost.</span></span>

<span data-ttu-id="f1f18-155">Deze para meter is niet afhankelijk van externe communicatie met Power shell.</span><span class="sxs-lookup"><span data-stu-id="f1f18-155">This parameter doesn't rely on PowerShell remoting.</span></span> <span data-ttu-id="f1f18-156">U kunt de para meter **ComputerName** ook gebruiken als uw computer niet is geconfigureerd om externe opdrachten uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="f1f18-156">You can use the **ComputerName** parameter even if your computer isn't configured to run remote commands.</span></span>

<span data-ttu-id="f1f18-157">Als de para meter **ComputerName** niet is opgegeven, wordt `Restart-Computer` de lokale computer opnieuw opgestart.</span><span class="sxs-lookup"><span data-stu-id="f1f18-157">If the **ComputerName** parameter isn't specified, `Restart-Computer` restarts the local computer.</span></span>

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

### <span data-ttu-id="f1f18-158">-Credential</span><span class="sxs-lookup"><span data-stu-id="f1f18-158">-Credential</span></span>

<span data-ttu-id="f1f18-159">Hiermee geeft u een gebruikers account op dat gemachtigd is om deze actie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="f1f18-159">Specifies a user account that has permission to do this action.</span></span> <span data-ttu-id="f1f18-160">Standaard is dit de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="f1f18-160">The default is the current user.</span></span>

<span data-ttu-id="f1f18-161">Typ een gebruikers naam, zoals **gebruiker01** of **Domain01\User01** , of voer een **PSCredential** -object in dat door de cmdlet wordt gegenereerd `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="f1f18-161">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="f1f18-162">Als u een gebruikers naam typt, wordt u gevraagd het wacht woord in te voeren.</span><span class="sxs-lookup"><span data-stu-id="f1f18-162">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="f1f18-163">Referenties worden opgeslagen in een [PSCredential](/dotnet/api/system.management.automation.pscredential) -object en het wacht woord wordt opgeslagen als [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="f1f18-163">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="f1f18-164">Zie [Hoe veilig is securestring?](/dotnet/api/system.security.securestring#how-secure-is-securestring)voor meer informatie over **securestring** Data Protection.</span><span class="sxs-lookup"><span data-stu-id="f1f18-164">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="f1f18-165">-Vertraging</span><span class="sxs-lookup"><span data-stu-id="f1f18-165">-Delay</span></span>

<span data-ttu-id="f1f18-166">Hiermee geeft u de frequentie van query's in seconden.</span><span class="sxs-lookup"><span data-stu-id="f1f18-166">Specifies the frequency of queries, in seconds.</span></span> <span data-ttu-id="f1f18-167">Power shell vraagt de service op die is opgegeven door de para meter **for** om te bepalen of de service beschikbaar is nadat de computer opnieuw is opgestart.</span><span class="sxs-lookup"><span data-stu-id="f1f18-167">PowerShell queries the service specified by the **For** parameter to determine whether the service is available after the computer is restarted.</span></span>

<span data-ttu-id="f1f18-168">Deze para meter is alleen geldig in combi natie met de **wacht** **-en-** para meters.</span><span class="sxs-lookup"><span data-stu-id="f1f18-168">This parameter is valid only together with the **Wait** and **For** parameters.</span></span>

<span data-ttu-id="f1f18-169">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="f1f18-169">This parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="f1f18-170">Als de para meter **Delay** niet is opgegeven, `Restart-Computer` wordt een vertraging van vijf seconden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="f1f18-170">If the **Delay** parameter isn't specified, `Restart-Computer` uses a five second delay.</span></span>

```yaml
Type: System.Int16
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f1f18-171">-Voor</span><span class="sxs-lookup"><span data-stu-id="f1f18-171">-For</span></span>

<span data-ttu-id="f1f18-172">Hiermee wordt het gedrag van Power shell opgegeven wanneer wordt gewacht tot de opgegeven service of functie beschikbaar is nadat de computer opnieuw is opgestart.</span><span class="sxs-lookup"><span data-stu-id="f1f18-172">Specifies the behavior of PowerShell as it waits for the specified service or feature to become available after the computer restarts.</span></span> <span data-ttu-id="f1f18-173">Deze para meter is alleen geldig met de para meter **wait** .</span><span class="sxs-lookup"><span data-stu-id="f1f18-173">This parameter is only valid with the **Wait** parameter.</span></span>

<span data-ttu-id="f1f18-174">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="f1f18-174">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="f1f18-175">**Standaard** : er wordt gewacht tot Power shell opnieuw is opgestart.</span><span class="sxs-lookup"><span data-stu-id="f1f18-175">**Default** : Waits for PowerShell to restart.</span></span>
- <span data-ttu-id="f1f18-176">**Power shell** : opdrachten kunnen uitvoeren in een externe Power shell-sessie op de computer.</span><span class="sxs-lookup"><span data-stu-id="f1f18-176">**PowerShell** : Can run commands in a PowerShell remote session on the computer.</span></span>
- <span data-ttu-id="f1f18-177">**WMI** : ontvangt een antwoord op een Win32_ComputerSystem-query voor de computer.</span><span class="sxs-lookup"><span data-stu-id="f1f18-177">**WMI** : Receives a reply to a Win32_ComputerSystem query for the computer.</span></span>
- <span data-ttu-id="f1f18-178">**WinRM** : kan een externe sessie met de computer tot stand brengen met behulp van WS-Management.</span><span class="sxs-lookup"><span data-stu-id="f1f18-178">**WinRM** : Can establish a remote session to the computer by using WS-Management.</span></span>

<span data-ttu-id="f1f18-179">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="f1f18-179">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.WaitForServiceTypes
Parameter Sets: (All)
Aliases:
Accepted values: Wmi, WinRM, PowerShell

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f1f18-180">-Force</span><span class="sxs-lookup"><span data-stu-id="f1f18-180">-Force</span></span>

<span data-ttu-id="f1f18-181">Hiermee wordt de computer direct opnieuw opgestart.</span><span class="sxs-lookup"><span data-stu-id="f1f18-181">Forces an immediate restart of the computer.</span></span>

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

### <span data-ttu-id="f1f18-182">-Time-out</span><span class="sxs-lookup"><span data-stu-id="f1f18-182">-Timeout</span></span>

<span data-ttu-id="f1f18-183">Hiermee geeft u de duur van de wacht tijd in seconden.</span><span class="sxs-lookup"><span data-stu-id="f1f18-183">Specifies the duration of the wait, in seconds.</span></span> <span data-ttu-id="f1f18-184">Wanneer de time-out is verstreken, `Restart-Computer` keert u terug naar de opdracht prompt, zelfs als de computers niet opnieuw worden opgestart.</span><span class="sxs-lookup"><span data-stu-id="f1f18-184">When the timeout elapses, `Restart-Computer` returns to the command prompt, even if the computers aren't restarted.</span></span>

<span data-ttu-id="f1f18-185">De **time-** outparameter is alleen geldig met de **wait** -para meter.</span><span class="sxs-lookup"><span data-stu-id="f1f18-185">The **Timeout** parameter is only valid with the **Wait** parameter.</span></span> <span data-ttu-id="f1f18-186">**Time-out** overschrijft de onbepaalde wacht tijd van de **wait** -para meter.</span><span class="sxs-lookup"><span data-stu-id="f1f18-186">**Timeout** overrides the **Wait** parameter's indefinite waiting period.</span></span>

<span data-ttu-id="f1f18-187">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="f1f18-187">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: TimeoutSec

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f1f18-188">-Wachten</span><span class="sxs-lookup"><span data-stu-id="f1f18-188">-Wait</span></span>

<span data-ttu-id="f1f18-189">`Restart-Computer` onderdrukt de Power shell-prompt en blokkeert de pijp lijn totdat de computers opnieuw zijn opgestart.</span><span class="sxs-lookup"><span data-stu-id="f1f18-189">`Restart-Computer` suppresses the PowerShell prompt and blocks the pipeline until the computers have restarted.</span></span> <span data-ttu-id="f1f18-190">U kunt deze para meter in een script gebruiken om computers opnieuw op te starten en vervolgens door gaan met het proces wanneer het opnieuw opstarten is voltooid.</span><span class="sxs-lookup"><span data-stu-id="f1f18-190">You can use this parameter in a script to restart computers and then continue to process when the restart is finished.</span></span>

<span data-ttu-id="f1f18-191">De **wacht** parameter voor onbepaalde tijd wacht op het opnieuw opstarten van de computers.</span><span class="sxs-lookup"><span data-stu-id="f1f18-191">The **Wait** parameter waits indefinitely for the computers to restart.</span></span> <span data-ttu-id="f1f18-192">U kunt **time-out** gebruiken om de timing en de para meters **voor** en **uitstel** in te stellen om te wachten tot bepaalde services beschikbaar zijn op de computers die opnieuw worden opgestart.</span><span class="sxs-lookup"><span data-stu-id="f1f18-192">You can use **Timeout** to adjust the timing and the **For** and **Delay** parameters to wait for particular services to become available on the restarted computers.</span></span>

<span data-ttu-id="f1f18-193">De **wait** -para meter is niet geldig wanneer u de lokale computer opnieuw opstart.</span><span class="sxs-lookup"><span data-stu-id="f1f18-193">The **Wait** parameter isn't valid when you're restarting the local computer.</span></span> <span data-ttu-id="f1f18-194">Als de waarde van de para meter **ComputerName** de namen van externe computers en de lokale computer bevat, wordt `Restart-Computer` er een niet-afsluit fout gegenereerd voor **wachten** op de lokale computer, maar wordt gewacht tot de externe computers opnieuw worden opgestart.</span><span class="sxs-lookup"><span data-stu-id="f1f18-194">If the value of the **ComputerName** parameter contains the names of remote computers and the local computer, `Restart-Computer` generates a non-terminating error for **Wait** on the local computer, but waits for the remote computers to restart.</span></span>

<span data-ttu-id="f1f18-195">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="f1f18-195">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f1f18-196">-WsmanAuthentication</span><span class="sxs-lookup"><span data-stu-id="f1f18-196">-WsmanAuthentication</span></span>

<span data-ttu-id="f1f18-197">Hiermee geeft u het mechanisme op dat wordt gebruikt voor het verifiëren van de gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="f1f18-197">Specifies the mechanism that is used to authenticate the user credentials.</span></span> <span data-ttu-id="f1f18-198">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="f1f18-198">This parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="f1f18-199">De acceptabele waarden voor deze para meter zijn: **Basic** , **CredSSP** , **default** , **Digest** , **Kerberos** en **Negotiate**.</span><span class="sxs-lookup"><span data-stu-id="f1f18-199">The acceptable values for this parameter are: **Basic** , **CredSSP** , **Default** , **Digest** , **Kerberos** , and **Negotiate**.</span></span>

<span data-ttu-id="f1f18-200">Zie [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="f1f18-200">For more information, see [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!WARNING]
> <span data-ttu-id="f1f18-201">CredSSP-verificatie (Credential Security service provider), waarbij de gebruikers referenties worden door gegeven aan een externe computer die moet worden geverifieerd, is ontworpen voor opdrachten waarvoor verificatie is vereist voor meer dan één bron, zoals het openen van een externe netwerk share.</span><span class="sxs-lookup"><span data-stu-id="f1f18-201">Credential Security Service Provider (CredSSP) authentication, in which the user credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="f1f18-202">Dit mechanisme verhoogt het beveiligings risico van de externe bewerking.</span><span class="sxs-lookup"><span data-stu-id="f1f18-202">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="f1f18-203">Als er is geknoeid met de externe computer, kunnen de referenties die aan worden door gegeven, worden gebruikt om de netwerk sessie te beheren.</span><span class="sxs-lookup"><span data-stu-id="f1f18-203">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Basic, CredSSP, Default, Digest, Kerberos, Negotiate

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f1f18-204">-Confirm</span><span class="sxs-lookup"><span data-stu-id="f1f18-204">-Confirm</span></span>

<span data-ttu-id="f1f18-205">Vraagt u om bevestiging voordat deze wordt uitgevoerd `Restart-Computer` .</span><span class="sxs-lookup"><span data-stu-id="f1f18-205">Prompts you for confirmation before running `Restart-Computer`.</span></span>

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

### <span data-ttu-id="f1f18-206">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="f1f18-206">-WhatIf</span></span>

<span data-ttu-id="f1f18-207">Laat zien wat er zou gebeuren als de `Restart-Computer` uitvoeringen wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="f1f18-207">Shows what would happen if the `Restart-Computer` runs.</span></span> <span data-ttu-id="f1f18-208">De `Restart-Computer` cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="f1f18-208">The `Restart-Computer` cmdlet isn't run.</span></span>

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

### <span data-ttu-id="f1f18-209">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f1f18-209">CommonParameters</span></span>

<span data-ttu-id="f1f18-210">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f1f18-210">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f1f18-211">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="f1f18-211">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f1f18-212">INVOER</span><span class="sxs-lookup"><span data-stu-id="f1f18-212">INPUTS</span></span>

### <span data-ttu-id="f1f18-213">System. String</span><span class="sxs-lookup"><span data-stu-id="f1f18-213">System.String</span></span>

<span data-ttu-id="f1f18-214">`Restart-Computer` Hiermee worden computer namen van de pijp lijn of variabelen geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="f1f18-214">`Restart-Computer` accepts computer names from the pipeline or variables.</span></span>

## <span data-ttu-id="f1f18-215">UITVOER</span><span class="sxs-lookup"><span data-stu-id="f1f18-215">OUTPUTS</span></span>

### <span data-ttu-id="f1f18-216">Geen</span><span class="sxs-lookup"><span data-stu-id="f1f18-216">None</span></span>

<span data-ttu-id="f1f18-217">`Restart-Computer` Er wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="f1f18-217">`Restart-Computer` doesn't generate any output.</span></span>

## <span data-ttu-id="f1f18-218">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="f1f18-218">NOTES</span></span>

<span data-ttu-id="f1f18-219">Deze cmdlet is alleen beschikbaar op Windows-platforms.</span><span class="sxs-lookup"><span data-stu-id="f1f18-219">This cmdlet is only available on Windows platforms.</span></span>

- <span data-ttu-id="f1f18-220">`Restart-Computer` werkt alleen op computers met Windows en vereist WinRM en WMI om een systeem af te afsluiten, inclusief het lokale systeem.</span><span class="sxs-lookup"><span data-stu-id="f1f18-220">`Restart-Computer` only works on computers running Windows and requires WinRM and WMI to shutdown a system, including the local system.</span></span>
- <span data-ttu-id="f1f18-221">`Restart-Computer` maakt gebruik van de [methode Win32Shutdown](/windows/desktop/CIMWin32Prov/win32shutdown-method-in-class-win32-operatingsystem) van de klasse Windows Management INSTRUMENTATION (WMI) [Win32_OperatingSystem](/windows/desktop/CIMWin32Prov/win32-operatingsystem) .</span><span class="sxs-lookup"><span data-stu-id="f1f18-221">`Restart-Computer` uses the [Win32Shutdown method](/windows/desktop/CIMWin32Prov/win32shutdown-method-in-class-win32-operatingsystem) of the Windows Management Instrumentation (WMI) [Win32_OperatingSystem](/windows/desktop/CIMWin32Prov/win32-operatingsystem) class.</span></span> <span data-ttu-id="f1f18-222">Voor deze methode moet de bevoegdheid **SeShutdownPrivilege** zijn ingeschakeld voor het gebruikers account dat wordt gebruikt om de computer opnieuw op te starten.</span><span class="sxs-lookup"><span data-stu-id="f1f18-222">This method requires the **SeShutdownPrivilege** privilege be enabled for the user account used to restart the machine.</span></span>

## <span data-ttu-id="f1f18-223">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="f1f18-223">RELATED LINKS</span></span>

[<span data-ttu-id="f1f18-224">Over Windows Remote Management</span><span class="sxs-lookup"><span data-stu-id="f1f18-224">About Windows Remote Management</span></span>](/windows/desktop/WinRM/about-windows-remote-management)

[<span data-ttu-id="f1f18-225">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="f1f18-225">Get-Credential</span></span>](../Microsoft.PowerShell.Security/Get-Credential.md)

[<span data-ttu-id="f1f18-226">WS-Management-protocol</span><span class="sxs-lookup"><span data-stu-id="f1f18-226">WS-Management Protocol</span></span>](/windows/desktop/WinRM/ws-management-protocol)
