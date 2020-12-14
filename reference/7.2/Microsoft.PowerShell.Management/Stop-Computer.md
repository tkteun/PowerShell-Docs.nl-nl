---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/11/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/stop-computer?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Computer
ms.openlocfilehash: f6d31980e27b73e884b46168606ab8255a64efb9
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94704753"
---
# <span data-ttu-id="44189-102">Stop-Computer</span><span class="sxs-lookup"><span data-stu-id="44189-102">Stop-Computer</span></span>

## <span data-ttu-id="44189-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="44189-103">SYNOPSIS</span></span>
<span data-ttu-id="44189-104">Stopt (wordt afgesloten) van lokale en externe computers.</span><span class="sxs-lookup"><span data-stu-id="44189-104">Stops (shuts down) local and remote computers.</span></span>

## <span data-ttu-id="44189-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="44189-105">SYNTAX</span></span>

### <span data-ttu-id="44189-106">Alles</span><span class="sxs-lookup"><span data-stu-id="44189-106">All</span></span>

```
Stop-Computer [-WsmanAuthentication <String>] [[-ComputerName] <String[]>]
 [[-Credential] <PSCredential>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="44189-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="44189-107">DESCRIPTION</span></span>

<span data-ttu-id="44189-108">De `Stop-Computer` cmdlet sluit de lokale computer en externe computers.</span><span class="sxs-lookup"><span data-stu-id="44189-108">The `Stop-Computer` cmdlet shuts down the local computer and remote computers.</span></span>

<span data-ttu-id="44189-109">U kunt de para meters van gebruiken `Stop-Computer` om de verificatie niveaus en alternatieve referenties op te geven en een onmiddellijke afsluit actie af te dwingen.</span><span class="sxs-lookup"><span data-stu-id="44189-109">You can use the parameters of `Stop-Computer` to specify the authentication levels and alternate credentials, and to force an immediate shut down.</span></span>

<span data-ttu-id="44189-110">In Power shell 7,1 `Stop-Computer` is toegevoegd voor Linux en macOS.</span><span class="sxs-lookup"><span data-stu-id="44189-110">In PowerShell 7.1, `Stop-Computer` was added for Linux and macOS.</span></span> <span data-ttu-id="44189-111">De para meters hebben geen effect op deze platforms.</span><span class="sxs-lookup"><span data-stu-id="44189-111">The parameters have no effect on these platforms.</span></span> <span data-ttu-id="44189-112">De cmdlet roept alleen de systeem eigen opdracht aan `/sbin/shutdown` .</span><span class="sxs-lookup"><span data-stu-id="44189-112">The cmdlet is just calling the native command `/sbin/shutdown`.</span></span>

## <span data-ttu-id="44189-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="44189-113">EXAMPLES</span></span>

### <span data-ttu-id="44189-114">Voor beeld 1: de lokale computer uitschakelen</span><span class="sxs-lookup"><span data-stu-id="44189-114">Example 1: Shut down the local computer</span></span>

<span data-ttu-id="44189-115">In dit voor beeld wordt de lokale computer afgesloten.</span><span class="sxs-lookup"><span data-stu-id="44189-115">This example shuts down the local computer.</span></span>

```powershell
Stop-Computer -ComputerName localhost
```

### <span data-ttu-id="44189-116">Voor beeld 2: twee externe computers en de lokale computer uitschakelen</span><span class="sxs-lookup"><span data-stu-id="44189-116">Example 2: Shut down two remote computers and the local computer</span></span>

<span data-ttu-id="44189-117">In dit voor beeld worden twee externe computers en de lokale computer gestopt.</span><span class="sxs-lookup"><span data-stu-id="44189-117">This example stops two remote computers and the local computer.</span></span>

```powershell
Stop-Computer -ComputerName "Server01", "Server02", "localhost"
```

<span data-ttu-id="44189-118">`Stop-Computer` maakt gebruik van de para meter **ComputerName** om twee externe computers en de lokale computer op te geven.</span><span class="sxs-lookup"><span data-stu-id="44189-118">`Stop-Computer` uses the **ComputerName** parameter to specify two remote computers and the local computer.</span></span> <span data-ttu-id="44189-119">Elke computer wordt afgesloten.</span><span class="sxs-lookup"><span data-stu-id="44189-119">Each computer is shut down.</span></span>

### <span data-ttu-id="44189-120">Voor beeld 3: externe computers afsluiten als achtergrond taak</span><span class="sxs-lookup"><span data-stu-id="44189-120">Example 3: Shut down remote computers as a background job</span></span>

<span data-ttu-id="44189-121">In dit voor beeld `Stop-Computer` wordt uitgevoerd als een achtergrond taak op twee externe computers.</span><span class="sxs-lookup"><span data-stu-id="44189-121">In this example, `Stop-Computer` runs as a background job on two remote computers.</span></span>

<span data-ttu-id="44189-122">De operator achtergrond `&` voert de `Stop-Computer` opdracht uit als achtergrond taak.</span><span class="sxs-lookup"><span data-stu-id="44189-122">The background operator `&` runs the `Stop-Computer` command as a background job.</span></span> <span data-ttu-id="44189-123">Zie [about_Operators](../microsoft.powershell.core/about/about_operators.md#background-operator-)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="44189-123">For more information, see [about_Operators](../microsoft.powershell.core/about/about_operators.md#background-operator-).</span></span>

```powershell
$j = Stop-Computer -ComputerName "Server01", "Server02" &
$results = $j | Receive-Job
$results
```

<span data-ttu-id="44189-124">`Stop-Computer` maakt gebruik van de para meter **ComputerName** om twee externe computers op te geven.</span><span class="sxs-lookup"><span data-stu-id="44189-124">`Stop-Computer` uses the **ComputerName** parameter to specify two remote computers.</span></span> <span data-ttu-id="44189-125">De `&` operator achtergrond voert de opdracht uit als achtergrond taak.</span><span class="sxs-lookup"><span data-stu-id="44189-125">The `&` background operator runs the command as a background job.</span></span> <span data-ttu-id="44189-126">De taak objecten worden opgeslagen in de `$j` variabele.</span><span class="sxs-lookup"><span data-stu-id="44189-126">The job objects are stored in the `$j` variable.</span></span>

<span data-ttu-id="44189-127">De taak objecten in de `$j` variabele worden verzonden naar de pijp lijn naar `Receive-Job` , waardoor de taak resultaten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="44189-127">The job objects in the `$j` variable are sent down the pipeline to `Receive-Job`, which gets the job results.</span></span> <span data-ttu-id="44189-128">De objecten worden opgeslagen in de `$results` variabele.</span><span class="sxs-lookup"><span data-stu-id="44189-128">The objects are stored in the `$results` variable.</span></span> <span data-ttu-id="44189-129">`$results`Met de variabele wordt de taak informatie in de Power shell-console weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="44189-129">The `$results` variable displays the job information in the PowerShell console.</span></span>

### <span data-ttu-id="44189-130">Voor beeld 4: een externe computer afsluiten</span><span class="sxs-lookup"><span data-stu-id="44189-130">Example 4: Shut down a remote computer</span></span>

<span data-ttu-id="44189-131">In dit voor beeld wordt een externe computer met opgegeven verificatie afgesloten.</span><span class="sxs-lookup"><span data-stu-id="44189-131">This example shuts down a remote computer using specified authentication.</span></span>

```powershell
Stop-Computer -ComputerName "Server01" -WsmanAuthentication Kerberos
```

<span data-ttu-id="44189-132">`Stop-Computer` maakt gebruik van de para meter **ComputerName** om de externe computer op te geven.</span><span class="sxs-lookup"><span data-stu-id="44189-132">`Stop-Computer` uses the **ComputerName** parameter to specify the remote computer.</span></span> <span data-ttu-id="44189-133">De para meter **WsmanAuthentication** geeft aan dat Kerberos moet worden gebruikt om een externe verbinding tot stand te brengen.</span><span class="sxs-lookup"><span data-stu-id="44189-133">The **WsmanAuthentication** parameter specifies to use Kerberos to establish a remote connection.</span></span>

### <span data-ttu-id="44189-134">Voor beeld 5: computers afsluiten in een domein</span><span class="sxs-lookup"><span data-stu-id="44189-134">Example 5: Shut down computers in a domain</span></span>

<span data-ttu-id="44189-135">In dit voor beeld forceren de opdrachten een onmiddellijke afsluiting van alle computers in een opgegeven domein.</span><span class="sxs-lookup"><span data-stu-id="44189-135">In this example, the commands force an immediate shut down of all computers in a specified domain.</span></span>

```powershell
$s = Get-Content -Path ./Domain01.txt
$c = Get-Credential -Credential Domain01\Admin01
Stop-Computer -ComputerName $s -Force -Credential $c
```

<span data-ttu-id="44189-136">`Get-Content` gebruikt de para meter **Path** om een bestand in de huidige map op te halen met de lijst van domein computers.</span><span class="sxs-lookup"><span data-stu-id="44189-136">`Get-Content` uses the **Path** parameter to get a file in the current directory with the list of domain computers.</span></span> <span data-ttu-id="44189-137">De objecten worden opgeslagen in de `$s` variabele.</span><span class="sxs-lookup"><span data-stu-id="44189-137">The objects are stored in the `$s` variable.</span></span>

<span data-ttu-id="44189-138">`Get-Credential` maakt gebruik van de para meter **Credential** om de referenties van een domein beheerder op te geven.</span><span class="sxs-lookup"><span data-stu-id="44189-138">`Get-Credential` uses the **Credential** parameter to specify the credentials of a domain administrator.</span></span> <span data-ttu-id="44189-139">De referenties worden opgeslagen in de `$c` variabele.</span><span class="sxs-lookup"><span data-stu-id="44189-139">The credentials are stored in the `$c` variable.</span></span>

<span data-ttu-id="44189-140">`Stop-Computer` de computers die zijn opgegeven met de **computer naam** parameter lijst van computers in de variabele worden afgesloten `$s` .</span><span class="sxs-lookup"><span data-stu-id="44189-140">`Stop-Computer` shuts down the computers specified with the **ComputerName** parameter's list of computers in the `$s` variable.</span></span> <span data-ttu-id="44189-141">Met de **Force** -para meter wordt direct afsluiten afgedwongen.</span><span class="sxs-lookup"><span data-stu-id="44189-141">The **Force** parameter forces an immediate shutdown.</span></span> <span data-ttu-id="44189-142">De **referentie** parameter verzendt de referenties die zijn opgeslagen in de `$c` variabele.</span><span class="sxs-lookup"><span data-stu-id="44189-142">The **Credential** parameter submits the credentials saved in the `$c` variable.</span></span>

## <span data-ttu-id="44189-143">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="44189-143">PARAMETERS</span></span>

### <span data-ttu-id="44189-144">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="44189-144">-ComputerName</span></span>

<span data-ttu-id="44189-145">Hiermee geeft u de computers op die moeten worden gestopt.</span><span class="sxs-lookup"><span data-stu-id="44189-145">Specifies the computers to stop.</span></span> <span data-ttu-id="44189-146">Standaard is dit de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="44189-146">The default is the local computer.</span></span>

<span data-ttu-id="44189-147">Typ de NETBIOS-naam, het IP-adres of de Fully Qualified Domain Name van een of meer computers in een lijst met door komma's gescheiden waarden.</span><span class="sxs-lookup"><span data-stu-id="44189-147">Type the NETBIOS name, IP address, or fully qualified domain name of one or more computers in a comma-separated list.</span></span> <span data-ttu-id="44189-148">Als u de lokale computer wilt opgeven, typt u de naam van de computer of localhost.</span><span class="sxs-lookup"><span data-stu-id="44189-148">To specify the local computer, type the computer name or localhost.</span></span>

<span data-ttu-id="44189-149">Deze para meter is niet afhankelijk van externe communicatie met Power shell.</span><span class="sxs-lookup"><span data-stu-id="44189-149">This parameter doesn't rely on PowerShell remoting.</span></span> <span data-ttu-id="44189-150">U kunt de para meter **ComputerName** ook gebruiken als uw computer niet is geconfigureerd om externe opdrachten uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="44189-150">You can use the **ComputerName** parameter even if your computer isn't configured to run remote commands.</span></span>

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

### <span data-ttu-id="44189-151">-Confirm</span><span class="sxs-lookup"><span data-stu-id="44189-151">-Confirm</span></span>

<span data-ttu-id="44189-152">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="44189-152">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="44189-153">-Credential</span><span class="sxs-lookup"><span data-stu-id="44189-153">-Credential</span></span>

<span data-ttu-id="44189-154">Hiermee geeft u een gebruikers account op dat gemachtigd is om deze actie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="44189-154">Specifies a user account that has permission to do this action.</span></span> <span data-ttu-id="44189-155">Standaard is dit de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="44189-155">The default is the current user.</span></span>

<span data-ttu-id="44189-156">Typ een gebruikers naam, zoals **gebruiker01** of **Domain01\User01**, of voer een **PSCredential** -object in dat door de cmdlet wordt gegenereerd `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="44189-156">Type a user name, such as **User01** or **Domain01\User01**, or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="44189-157">Als u een gebruikers naam typt, wordt u gevraagd het wacht woord in te voeren.</span><span class="sxs-lookup"><span data-stu-id="44189-157">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="44189-158">Referenties worden opgeslagen in een [PSCredential](/dotnet/api/system.management.automation.pscredential) -object en het wacht woord wordt opgeslagen als [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="44189-158">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="44189-159">Zie [Hoe veilig is securestring?](/dotnet/api/system.security.securestring#how-secure-is-securestring)voor meer informatie over **securestring** Data Protection.</span><span class="sxs-lookup"><span data-stu-id="44189-159">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="44189-160">-Force</span><span class="sxs-lookup"><span data-stu-id="44189-160">-Force</span></span>

<span data-ttu-id="44189-161">Hiermee wordt de computer onmiddellijk afgesloten.</span><span class="sxs-lookup"><span data-stu-id="44189-161">Forces an immediate shut down of the computer.</span></span>

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

### <span data-ttu-id="44189-162">-WsmanAuthentication</span><span class="sxs-lookup"><span data-stu-id="44189-162">-WsmanAuthentication</span></span>

<span data-ttu-id="44189-163">Hiermee geeft u het mechanisme op dat wordt gebruikt voor het verifiëren van de gebruikers referenties wanneer deze cmdlet gebruikmaakt van het WSMan-protocol.</span><span class="sxs-lookup"><span data-stu-id="44189-163">Specifies the mechanism that is used to authenticate the user credentials when this cmdlet uses the WSMan protocol.</span></span> <span data-ttu-id="44189-164">De standaard waarde is **standaard**.</span><span class="sxs-lookup"><span data-stu-id="44189-164">The default value is **Default**.</span></span>

<span data-ttu-id="44189-165">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="44189-165">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="44189-166">Basic</span><span class="sxs-lookup"><span data-stu-id="44189-166">Basic</span></span>
- <span data-ttu-id="44189-167">CredSSP</span><span class="sxs-lookup"><span data-stu-id="44189-167">CredSSP</span></span>
- <span data-ttu-id="44189-168">Standaard</span><span class="sxs-lookup"><span data-stu-id="44189-168">Default</span></span>
- <span data-ttu-id="44189-169">Samenvatting</span><span class="sxs-lookup"><span data-stu-id="44189-169">Digest</span></span>
- <span data-ttu-id="44189-170">Kerberos</span><span class="sxs-lookup"><span data-stu-id="44189-170">Kerberos</span></span>
- <span data-ttu-id="44189-171">Afspraken.</span><span class="sxs-lookup"><span data-stu-id="44189-171">Negotiate.</span></span>

<span data-ttu-id="44189-172">Zie [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)voor meer informatie over de waarden van deze para meter.</span><span class="sxs-lookup"><span data-stu-id="44189-172">For more information about the values of this parameter, see [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!CAUTION]
> <span data-ttu-id="44189-173">CredSSP-verificatie (Credential Security service provider), waarbij de gebruikers referenties worden door gegeven aan een externe computer die moet worden geverifieerd, is ontworpen voor opdrachten waarvoor verificatie is vereist voor meer dan één bron, zoals het openen van een externe netwerk share.</span><span class="sxs-lookup"><span data-stu-id="44189-173">Credential Security Service Provider (CredSSP) authentication, in which the user credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="44189-174">Dit mechanisme verhoogt het beveiligings risico van de externe bewerking.</span><span class="sxs-lookup"><span data-stu-id="44189-174">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="44189-175">Als er is geknoeid met de externe computer, kunnen de referenties die aan worden door gegeven, worden gebruikt om de netwerk sessie te beheren.</span><span class="sxs-lookup"><span data-stu-id="44189-175">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

<span data-ttu-id="44189-176">Deze para meter is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="44189-176">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="44189-177">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="44189-177">-WhatIf</span></span>

<span data-ttu-id="44189-178">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="44189-178">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="44189-179">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="44189-179">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="44189-180">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="44189-180">CommonParameters</span></span>

<span data-ttu-id="44189-181">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="44189-181">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="44189-182">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="44189-182">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="44189-183">INVOER</span><span class="sxs-lookup"><span data-stu-id="44189-183">INPUTS</span></span>

### <span data-ttu-id="44189-184">Geen</span><span class="sxs-lookup"><span data-stu-id="44189-184">None</span></span>

<span data-ttu-id="44189-185">U kunt invoer niet naar deze cmdlet pipeen.</span><span class="sxs-lookup"><span data-stu-id="44189-185">You can't pipe input to this cmdlet.</span></span>

## <span data-ttu-id="44189-186">UITVOER</span><span class="sxs-lookup"><span data-stu-id="44189-186">OUTPUTS</span></span>

### <span data-ttu-id="44189-187">Geen</span><span class="sxs-lookup"><span data-stu-id="44189-187">None</span></span>

## <span data-ttu-id="44189-188">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="44189-188">NOTES</span></span>

<span data-ttu-id="44189-189">Deze cmdlet maakt gebruik van de methode **Win32Shutdown** van de WMI-klasse **Win32_OperatingSystem** .</span><span class="sxs-lookup"><span data-stu-id="44189-189">This cmdlet uses the **Win32Shutdown** method of the **Win32_OperatingSystem** WMI class.</span></span> <span data-ttu-id="44189-190">Voor deze methode moet de bevoegdheid **SeShutdownPrivilege** zijn ingeschakeld voor het gebruikers account dat wordt gebruikt om de computer opnieuw op te starten.</span><span class="sxs-lookup"><span data-stu-id="44189-190">This method requires the **SeShutdownPrivilege** privilege be enabled for the user account used to restart the machine.</span></span>

<span data-ttu-id="44189-191">In Power shell 7,1 `Stop-Computer` is toegevoegd voor Linux en macOS.</span><span class="sxs-lookup"><span data-stu-id="44189-191">In PowerShell 7.1, `Stop-Computer` was added for Linux and macOS.</span></span> <span data-ttu-id="44189-192">Voor deze platorms roept de cmdlet de systeem eigen opdracht aan `/sbin/shutdown` .</span><span class="sxs-lookup"><span data-stu-id="44189-192">For these platorms, the cmdlet calls the native command `/sbin/shutdown`.</span></span>

## <span data-ttu-id="44189-193">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="44189-193">RELATED LINKS</span></span>

[<span data-ttu-id="44189-194">Naam wijzigen-computer</span><span class="sxs-lookup"><span data-stu-id="44189-194">Rename-Computer</span></span>](Rename-Computer.md)

[<span data-ttu-id="44189-195">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="44189-195">Restart-Computer</span></span>](Restart-Computer.md)

[<span data-ttu-id="44189-196">Test-Connection</span><span class="sxs-lookup"><span data-stu-id="44189-196">Test-Connection</span></span>](Test-Connection.md)

