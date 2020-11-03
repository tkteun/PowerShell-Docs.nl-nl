---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/11/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/stop-computer?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Computer
ms.openlocfilehash: e7732c1eb243c0a4737c3f08a413fd20bbf2bf38
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/23/2020
ms.locfileid: "93251586"
---
# <span data-ttu-id="150ee-103">Stop-Computer</span><span class="sxs-lookup"><span data-stu-id="150ee-103">Stop-Computer</span></span>

## <span data-ttu-id="150ee-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="150ee-104">SYNOPSIS</span></span>
<span data-ttu-id="150ee-105">Stopt (wordt afgesloten) van lokale en externe computers.</span><span class="sxs-lookup"><span data-stu-id="150ee-105">Stops (shuts down) local and remote computers.</span></span>

## <span data-ttu-id="150ee-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="150ee-106">SYNTAX</span></span>

### <span data-ttu-id="150ee-107">Alles</span><span class="sxs-lookup"><span data-stu-id="150ee-107">All</span></span>

```
Stop-Computer [-WsmanAuthentication <String>] [[-ComputerName] <String[]>]
 [[-Credential] <PSCredential>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="150ee-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="150ee-108">DESCRIPTION</span></span>

<span data-ttu-id="150ee-109">De `Stop-Computer` cmdlet sluit de lokale computer en externe computers.</span><span class="sxs-lookup"><span data-stu-id="150ee-109">The `Stop-Computer` cmdlet shuts down the local computer and remote computers.</span></span>

<span data-ttu-id="150ee-110">U kunt de para meters van gebruiken `Stop-Computer` om de verificatie niveaus en alternatieve referenties op te geven en een onmiddellijke afsluit actie af te dwingen.</span><span class="sxs-lookup"><span data-stu-id="150ee-110">You can use the parameters of `Stop-Computer` to specify the authentication levels and alternate credentials, and to force an immediate shut down.</span></span>

## <span data-ttu-id="150ee-111">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="150ee-111">EXAMPLES</span></span>

### <span data-ttu-id="150ee-112">Voor beeld 1: de lokale computer uitschakelen</span><span class="sxs-lookup"><span data-stu-id="150ee-112">Example 1: Shut down the local computer</span></span>

<span data-ttu-id="150ee-113">In dit voor beeld wordt de lokale computer afgesloten.</span><span class="sxs-lookup"><span data-stu-id="150ee-113">This example shuts down the local computer.</span></span>

```powershell
Stop-Computer -ComputerName localhost
```

### <span data-ttu-id="150ee-114">Voor beeld 2: twee externe computers en de lokale computer uitschakelen</span><span class="sxs-lookup"><span data-stu-id="150ee-114">Example 2: Shut down two remote computers and the local computer</span></span>

<span data-ttu-id="150ee-115">In dit voor beeld worden twee externe computers en de lokale computer gestopt.</span><span class="sxs-lookup"><span data-stu-id="150ee-115">This example stops two remote computers and the local computer.</span></span>

```powershell
Stop-Computer -ComputerName "Server01", "Server02", "localhost"
```

<span data-ttu-id="150ee-116">`Stop-Computer` maakt gebruik van de para meter **ComputerName** om twee externe computers en de lokale computer op te geven.</span><span class="sxs-lookup"><span data-stu-id="150ee-116">`Stop-Computer` uses the **ComputerName** parameter to specify two remote computers and the local computer.</span></span> <span data-ttu-id="150ee-117">Elke computer wordt afgesloten.</span><span class="sxs-lookup"><span data-stu-id="150ee-117">Each computer is shut down.</span></span>

### <span data-ttu-id="150ee-118">Voor beeld 3: externe computers afsluiten als achtergrond taak</span><span class="sxs-lookup"><span data-stu-id="150ee-118">Example 3: Shut down remote computers as a background job</span></span>

<span data-ttu-id="150ee-119">In dit voor beeld `Stop-Computer` wordt uitgevoerd als een achtergrond taak op twee externe computers.</span><span class="sxs-lookup"><span data-stu-id="150ee-119">In this example, `Stop-Computer` runs as a background job on two remote computers.</span></span>

<span data-ttu-id="150ee-120">De operator achtergrond `&` voert de `Stop-Computer` opdracht uit als achtergrond taak.</span><span class="sxs-lookup"><span data-stu-id="150ee-120">The background operator `&` runs the `Stop-Computer` command as a background job.</span></span> <span data-ttu-id="150ee-121">Zie [about_Operators](../microsoft.powershell.core/about/about_operators.md#background-operator-)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="150ee-121">For more information, see [about_Operators](../microsoft.powershell.core/about/about_operators.md#background-operator-).</span></span>

```powershell
$j = Stop-Computer -ComputerName "Server01", "Server02" &
$results = $j | Receive-Job
$results
```

<span data-ttu-id="150ee-122">`Stop-Computer` maakt gebruik van de para meter **ComputerName** om twee externe computers op te geven.</span><span class="sxs-lookup"><span data-stu-id="150ee-122">`Stop-Computer` uses the **ComputerName** parameter to specify two remote computers.</span></span> <span data-ttu-id="150ee-123">De `&` operator achtergrond voert de opdracht uit als achtergrond taak.</span><span class="sxs-lookup"><span data-stu-id="150ee-123">The `&` background operator runs the command as a background job.</span></span> <span data-ttu-id="150ee-124">De taak objecten worden opgeslagen in de `$j` variabele.</span><span class="sxs-lookup"><span data-stu-id="150ee-124">The job objects are stored in the `$j` variable.</span></span>

<span data-ttu-id="150ee-125">De taak objecten in de `$j` variabele worden verzonden naar de pijp lijn naar `Receive-Job` , waardoor de taak resultaten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="150ee-125">The job objects in the `$j` variable are sent down the pipeline to `Receive-Job`, which gets the job results.</span></span> <span data-ttu-id="150ee-126">De objecten worden opgeslagen in de `$results` variabele.</span><span class="sxs-lookup"><span data-stu-id="150ee-126">The objects are stored in the `$results` variable.</span></span> <span data-ttu-id="150ee-127">`$results`Met de variabele wordt de taak informatie in de Power shell-console weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="150ee-127">The `$results` variable displays the job information in the PowerShell console.</span></span>

### <span data-ttu-id="150ee-128">Voor beeld 4: een externe computer afsluiten</span><span class="sxs-lookup"><span data-stu-id="150ee-128">Example 4: Shut down a remote computer</span></span>

<span data-ttu-id="150ee-129">In dit voor beeld wordt een externe computer met opgegeven verificatie afgesloten.</span><span class="sxs-lookup"><span data-stu-id="150ee-129">This example shuts down a remote computer using specified authentication.</span></span>

```powershell
Stop-Computer -ComputerName "Server01" -WsmanAuthentication Kerberos
```

<span data-ttu-id="150ee-130">`Stop-Computer` maakt gebruik van de para meter **ComputerName** om de externe computer op te geven.</span><span class="sxs-lookup"><span data-stu-id="150ee-130">`Stop-Computer` uses the **ComputerName** parameter to specify the remote computer.</span></span> <span data-ttu-id="150ee-131">De para meter **WsmanAuthentication** geeft aan dat Kerberos moet worden gebruikt om een externe verbinding tot stand te brengen.</span><span class="sxs-lookup"><span data-stu-id="150ee-131">The **WsmanAuthentication** parameter specifies to use Kerberos to establish a remote connection.</span></span>

### <span data-ttu-id="150ee-132">Voor beeld 5: computers afsluiten in een domein</span><span class="sxs-lookup"><span data-stu-id="150ee-132">Example 5: Shut down computers in a domain</span></span>

<span data-ttu-id="150ee-133">In dit voor beeld forceren de opdrachten een onmiddellijke afsluiting van alle computers in een opgegeven domein.</span><span class="sxs-lookup"><span data-stu-id="150ee-133">In this example, the commands force an immediate shut down of all computers in a specified domain.</span></span>

```powershell
$s = Get-Content -Path ./Domain01.txt
$c = Get-Credential -Credential Domain01\Admin01
Stop-Computer -ComputerName $s -Force -Credential $c
```

<span data-ttu-id="150ee-134">`Get-Content` gebruikt de para meter **Path** om een bestand in de huidige map op te halen met de lijst van domein computers.</span><span class="sxs-lookup"><span data-stu-id="150ee-134">`Get-Content` uses the **Path** parameter to get a file in the current directory with the list of domain computers.</span></span> <span data-ttu-id="150ee-135">De objecten worden opgeslagen in de `$s` variabele.</span><span class="sxs-lookup"><span data-stu-id="150ee-135">The objects are stored in the `$s` variable.</span></span>

<span data-ttu-id="150ee-136">`Get-Credential` maakt gebruik van de para meter **Credential** om de referenties van een domein beheerder op te geven.</span><span class="sxs-lookup"><span data-stu-id="150ee-136">`Get-Credential` uses the **Credential** parameter to specify the credentials of a domain administrator.</span></span> <span data-ttu-id="150ee-137">De referenties worden opgeslagen in de `$c` variabele.</span><span class="sxs-lookup"><span data-stu-id="150ee-137">The credentials are stored in the `$c` variable.</span></span>

<span data-ttu-id="150ee-138">`Stop-Computer` de computers die zijn opgegeven met de **computer naam** parameter lijst van computers in de variabele worden afgesloten `$s` .</span><span class="sxs-lookup"><span data-stu-id="150ee-138">`Stop-Computer` shuts down the computers specified with the **ComputerName** parameter's list of computers in the `$s` variable.</span></span> <span data-ttu-id="150ee-139">Met de **Force** -para meter wordt direct afsluiten afgedwongen.</span><span class="sxs-lookup"><span data-stu-id="150ee-139">The **Force** parameter forces an immediate shutdown.</span></span> <span data-ttu-id="150ee-140">De **referentie** parameter verzendt de referenties die zijn opgeslagen in de `$c` variabele.</span><span class="sxs-lookup"><span data-stu-id="150ee-140">The **Credential** parameter submits the credentials saved in the `$c` variable.</span></span>

## <span data-ttu-id="150ee-141">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="150ee-141">PARAMETERS</span></span>

### <span data-ttu-id="150ee-142">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="150ee-142">-ComputerName</span></span>

<span data-ttu-id="150ee-143">Hiermee geeft u de computers op die moeten worden gestopt.</span><span class="sxs-lookup"><span data-stu-id="150ee-143">Specifies the computers to stop.</span></span> <span data-ttu-id="150ee-144">Standaard is dit de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="150ee-144">The default is the local computer.</span></span>

<span data-ttu-id="150ee-145">Typ de NETBIOS-naam, het IP-adres of de Fully Qualified Domain Name van een of meer computers in een lijst met door komma's gescheiden waarden.</span><span class="sxs-lookup"><span data-stu-id="150ee-145">Type the NETBIOS name, IP address, or fully qualified domain name of one or more computers in a comma-separated list.</span></span> <span data-ttu-id="150ee-146">Als u de lokale computer wilt opgeven, typt u de naam van de computer of localhost.</span><span class="sxs-lookup"><span data-stu-id="150ee-146">To specify the local computer, type the computer name or localhost.</span></span>

<span data-ttu-id="150ee-147">Deze para meter is niet afhankelijk van externe communicatie met Power shell.</span><span class="sxs-lookup"><span data-stu-id="150ee-147">This parameter doesn't rely on PowerShell remoting.</span></span> <span data-ttu-id="150ee-148">U kunt de para meter **ComputerName** ook gebruiken als uw computer niet is geconfigureerd om externe opdrachten uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="150ee-148">You can use the **ComputerName** parameter even if your computer isn't configured to run remote commands.</span></span>

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

### <span data-ttu-id="150ee-149">-Confirm</span><span class="sxs-lookup"><span data-stu-id="150ee-149">-Confirm</span></span>

<span data-ttu-id="150ee-150">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="150ee-150">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="150ee-151">-Credential</span><span class="sxs-lookup"><span data-stu-id="150ee-151">-Credential</span></span>

<span data-ttu-id="150ee-152">Hiermee geeft u een gebruikers account op dat gemachtigd is om deze actie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="150ee-152">Specifies a user account that has permission to do this action.</span></span> <span data-ttu-id="150ee-153">Standaard is dit de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="150ee-153">The default is the current user.</span></span>

<span data-ttu-id="150ee-154">Typ een gebruikers naam, zoals **gebruiker01** of **Domain01\User01** , of voer een **PSCredential** -object in dat door de cmdlet wordt gegenereerd `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="150ee-154">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="150ee-155">Als u een gebruikers naam typt, wordt u gevraagd het wacht woord in te voeren.</span><span class="sxs-lookup"><span data-stu-id="150ee-155">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="150ee-156">Referenties worden opgeslagen in een [PSCredential](/dotnet/api/system.management.automation.pscredential) -object en het wacht woord wordt opgeslagen als [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="150ee-156">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="150ee-157">Zie [Hoe veilig is securestring?](/dotnet/api/system.security.securestring#how-secure-is-securestring)voor meer informatie over **securestring** Data Protection.</span><span class="sxs-lookup"><span data-stu-id="150ee-157">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="150ee-158">-Force</span><span class="sxs-lookup"><span data-stu-id="150ee-158">-Force</span></span>

<span data-ttu-id="150ee-159">Hiermee wordt de computer onmiddellijk afgesloten.</span><span class="sxs-lookup"><span data-stu-id="150ee-159">Forces an immediate shut down of the computer.</span></span>

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

### <span data-ttu-id="150ee-160">-WsmanAuthentication</span><span class="sxs-lookup"><span data-stu-id="150ee-160">-WsmanAuthentication</span></span>

<span data-ttu-id="150ee-161">Hiermee geeft u het mechanisme op dat wordt gebruikt voor het verifiëren van de gebruikers referenties wanneer deze cmdlet gebruikmaakt van het WSMan-protocol.</span><span class="sxs-lookup"><span data-stu-id="150ee-161">Specifies the mechanism that is used to authenticate the user credentials when this cmdlet uses the WSMan protocol.</span></span> <span data-ttu-id="150ee-162">De standaard waarde is **standaard**.</span><span class="sxs-lookup"><span data-stu-id="150ee-162">The default value is **Default**.</span></span>

<span data-ttu-id="150ee-163">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="150ee-163">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="150ee-164">Basic</span><span class="sxs-lookup"><span data-stu-id="150ee-164">Basic</span></span>
- <span data-ttu-id="150ee-165">CredSSP</span><span class="sxs-lookup"><span data-stu-id="150ee-165">CredSSP</span></span>
- <span data-ttu-id="150ee-166">Standaard</span><span class="sxs-lookup"><span data-stu-id="150ee-166">Default</span></span>
- <span data-ttu-id="150ee-167">Samenvatting</span><span class="sxs-lookup"><span data-stu-id="150ee-167">Digest</span></span>
- <span data-ttu-id="150ee-168">Kerberos</span><span class="sxs-lookup"><span data-stu-id="150ee-168">Kerberos</span></span>
- <span data-ttu-id="150ee-169">Afspraken.</span><span class="sxs-lookup"><span data-stu-id="150ee-169">Negotiate.</span></span>

<span data-ttu-id="150ee-170">Zie [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)voor meer informatie over de waarden van deze para meter.</span><span class="sxs-lookup"><span data-stu-id="150ee-170">For more information about the values of this parameter, see [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!CAUTION]
> <span data-ttu-id="150ee-171">CredSSP-verificatie (Credential Security service provider), waarbij de gebruikers referenties worden door gegeven aan een externe computer die moet worden geverifieerd, is ontworpen voor opdrachten waarvoor verificatie is vereist voor meer dan één bron, zoals het openen van een externe netwerk share.</span><span class="sxs-lookup"><span data-stu-id="150ee-171">Credential Security Service Provider (CredSSP) authentication, in which the user credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="150ee-172">Dit mechanisme verhoogt het beveiligings risico van de externe bewerking.</span><span class="sxs-lookup"><span data-stu-id="150ee-172">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="150ee-173">Als er is geknoeid met de externe computer, kunnen de referenties die aan worden door gegeven, worden gebruikt om de netwerk sessie te beheren.</span><span class="sxs-lookup"><span data-stu-id="150ee-173">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

<span data-ttu-id="150ee-174">Deze para meter is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="150ee-174">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="150ee-175">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="150ee-175">-WhatIf</span></span>

<span data-ttu-id="150ee-176">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="150ee-176">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="150ee-177">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="150ee-177">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="150ee-178">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="150ee-178">CommonParameters</span></span>

<span data-ttu-id="150ee-179">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="150ee-179">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="150ee-180">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="150ee-180">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="150ee-181">INVOER</span><span class="sxs-lookup"><span data-stu-id="150ee-181">INPUTS</span></span>

### <span data-ttu-id="150ee-182">Geen</span><span class="sxs-lookup"><span data-stu-id="150ee-182">None</span></span>

<span data-ttu-id="150ee-183">U kunt invoer niet naar deze cmdlet pipeen.</span><span class="sxs-lookup"><span data-stu-id="150ee-183">You can't pipe input to this cmdlet.</span></span>

## <span data-ttu-id="150ee-184">UITVOER</span><span class="sxs-lookup"><span data-stu-id="150ee-184">OUTPUTS</span></span>

### <span data-ttu-id="150ee-185">Geen</span><span class="sxs-lookup"><span data-stu-id="150ee-185">None</span></span>

## <span data-ttu-id="150ee-186">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="150ee-186">NOTES</span></span>

<span data-ttu-id="150ee-187">Deze cmdlet werkt alleen in Windows en maakt gebruik van de methode **Win32Shutdown** van de WMI-klasse **Win32_OperatingSystem** .</span><span class="sxs-lookup"><span data-stu-id="150ee-187">This cmdlet only works on Windows and uses the **Win32Shutdown** method of the **Win32_OperatingSystem** WMI class.</span></span> <span data-ttu-id="150ee-188">Voor deze methode moet de bevoegdheid **SeShutdownPrivilege** zijn ingeschakeld voor het gebruikers account dat wordt gebruikt om de computer opnieuw op te starten.</span><span class="sxs-lookup"><span data-stu-id="150ee-188">This method requires the **SeShutdownPrivilege** privilege be enabled for the user account used to restart the machine.</span></span>

## <span data-ttu-id="150ee-189">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="150ee-189">RELATED LINKS</span></span>

[<span data-ttu-id="150ee-190">Naam wijzigen-computer</span><span class="sxs-lookup"><span data-stu-id="150ee-190">Rename-Computer</span></span>](Rename-Computer.md)

[<span data-ttu-id="150ee-191">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="150ee-191">Restart-Computer</span></span>](Restart-Computer.md)

[<span data-ttu-id="150ee-192">Test-Connection</span><span class="sxs-lookup"><span data-stu-id="150ee-192">Test-Connection</span></span>](Test-Connection.md)
