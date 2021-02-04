---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 05/01/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/rename-computer?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Rename-Computer
ms.openlocfilehash: 070a428530f4f3eecceb0ae3f520ad565097c1e0
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705877"
---
# <span data-ttu-id="aa2f4-102">Rename-Computer</span><span class="sxs-lookup"><span data-stu-id="aa2f4-102">Rename-Computer</span></span>

## <span data-ttu-id="aa2f4-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="aa2f4-103">SYNOPSIS</span></span>
<span data-ttu-id="aa2f4-104">De naam van een computer wijzigen.</span><span class="sxs-lookup"><span data-stu-id="aa2f4-104">Renames a computer.</span></span>

## <span data-ttu-id="aa2f4-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="aa2f4-105">SYNTAX</span></span>

```
Rename-Computer [-ComputerName <String>] [-PassThru] [-DomainCredential <PSCredential>]
 [-LocalCredential <PSCredential>] [-NewName] <String> [-Force] [-Restart] [-WsmanAuthentication <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="aa2f4-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="aa2f4-106">DESCRIPTION</span></span>

<span data-ttu-id="aa2f4-107">De `Rename-Computer` cmdlet hernoemt de naam van de lokale computer of een externe computer.</span><span class="sxs-lookup"><span data-stu-id="aa2f4-107">The `Rename-Computer` cmdlet renames the local computer or a remote computer.</span></span>
<span data-ttu-id="aa2f4-108">De naam van een computer in elke opdracht wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="aa2f4-108">It renames one computer in each command.</span></span>

<span data-ttu-id="aa2f4-109">Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="aa2f4-109">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="aa2f4-110">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="aa2f4-110">EXAMPLES</span></span>

### <span data-ttu-id="aa2f4-111">Voor beeld 1: de naam van de lokale computer wijzigen</span><span class="sxs-lookup"><span data-stu-id="aa2f4-111">Example 1: Rename the local computer</span></span>

<span data-ttu-id="aa2f4-112">Met deze opdracht wordt de naam van de lokale computer gewijzigd in `Server044` en wordt deze opnieuw opgestart om de wijziging van kracht te laten worden.</span><span class="sxs-lookup"><span data-stu-id="aa2f4-112">This command renames the local computer to `Server044` and then restarts it to make the change effective.</span></span>

```powershell
Rename-Computer -NewName "Server044" -DomainCredential Domain01\Admin01 -Restart
```

### <span data-ttu-id="aa2f4-113">Voor beeld 2: de naam van een externe computer wijzigen</span><span class="sxs-lookup"><span data-stu-id="aa2f4-113">Example 2: Rename a remote computer</span></span>

<span data-ttu-id="aa2f4-114">Met deze opdracht wordt de naam van de `Srv01` computer gewijzigd in `Server001` .</span><span class="sxs-lookup"><span data-stu-id="aa2f4-114">This command renames the `Srv01` computer to `Server001`.</span></span> <span data-ttu-id="aa2f4-115">De computer is niet opnieuw opgestart.</span><span class="sxs-lookup"><span data-stu-id="aa2f4-115">The computer is not restarted.</span></span>

<span data-ttu-id="aa2f4-116">De **DomainCredential** para meter geeft u de referenties op van een gebruiker die gemachtigd is om de naam van computers in het domein te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="aa2f4-116">The **DomainCredential** parameter specifies the credentials of a user who has permission to rename computers in the domain.</span></span>

<span data-ttu-id="aa2f4-117">De **Force** -para meter onderdrukt de bevestigings prompt.</span><span class="sxs-lookup"><span data-stu-id="aa2f4-117">The **Force** parameter suppresses the confirmation prompt.</span></span>

```powershell
Rename-Computer -ComputerName "Srv01" -NewName "Server001" -DomainCredential Domain01\Admin01 -Force
```

## <span data-ttu-id="aa2f4-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="aa2f4-118">PARAMETERS</span></span>

### <span data-ttu-id="aa2f4-119">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="aa2f4-119">-ComputerName</span></span>

<span data-ttu-id="aa2f4-120">De naam van de opgegeven externe computer.</span><span class="sxs-lookup"><span data-stu-id="aa2f4-120">Renames the specified remote computer.</span></span>
<span data-ttu-id="aa2f4-121">Standaard is dit de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="aa2f4-121">The default is the local computer.</span></span>

<span data-ttu-id="aa2f4-122">Typ de NetBIOS-naam, een IP-adres of een Fully Qualified Domain Name van een externe computer.</span><span class="sxs-lookup"><span data-stu-id="aa2f4-122">Type the NetBIOS name, an IP address, or a fully qualified domain name of a remote computer.</span></span>
<span data-ttu-id="aa2f4-123">Als u de lokale computer wilt opgeven, typt u de naam van de computer, een punt ( `.` ) of `localhost` .</span><span class="sxs-lookup"><span data-stu-id="aa2f4-123">To specify the local computer, type the computer name, a dot (`.`), or `localhost`.</span></span>

<span data-ttu-id="aa2f4-124">Deze para meter is niet afhankelijk van externe communicatie met Power shell.</span><span class="sxs-lookup"><span data-stu-id="aa2f4-124">This parameter does not rely on PowerShell remoting.</span></span>
<span data-ttu-id="aa2f4-125">U kunt de para meter **ComputerName** gebruiken `Rename-Computer` , zelfs als uw computer niet is geconfigureerd om externe opdrachten uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="aa2f4-125">You can use the **ComputerName** parameter of `Rename-Computer` even if your computer is not configured to run remote commands.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Local Computer
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="aa2f4-126">-DomainCredential</span><span class="sxs-lookup"><span data-stu-id="aa2f4-126">-DomainCredential</span></span>

<span data-ttu-id="aa2f4-127">Hiermee geeft u een gebruikers account op dat is gemachtigd om verbinding te maken met het domein.</span><span class="sxs-lookup"><span data-stu-id="aa2f4-127">Specifies a user account that has permission to connect to the domain.</span></span>
<span data-ttu-id="aa2f4-128">Er zijn expliciete referenties vereist voor het wijzigen van de naam van een computer die lid is van een domein.</span><span class="sxs-lookup"><span data-stu-id="aa2f4-128">Explicit credentials are required to rename a computer that is joined to a domain.</span></span>

<span data-ttu-id="aa2f4-129">Typ een gebruikers naam, zoals `User01` of `Domain01\User01` , of voer een **PSCredential** -object in, zoals het certificaat dat is gegenereerd door de `Get-Credential` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="aa2f4-129">Type a user name, such as `User01` or `Domain01\User01`, or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="aa2f4-130">Als u een gebruikers naam typt, vraagt deze cmdlet u om een wacht woord.</span><span class="sxs-lookup"><span data-stu-id="aa2f4-130">If you type a user name, this cmdlet prompts you for a password.</span></span>

<span data-ttu-id="aa2f4-131">Als u een gebruikers account wilt opgeven dat is gemachtigd om verbinding te maken met de computer die is opgegeven door de para meter **ComputerName** , gebruikt u de para meter **LocalCredential** .</span><span class="sxs-lookup"><span data-stu-id="aa2f4-131">To specify a user account that has permission to connect to the computer that is specified by the **ComputerName** parameter, use the **LocalCredential** parameter.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="aa2f4-132">-Force</span><span class="sxs-lookup"><span data-stu-id="aa2f4-132">-Force</span></span>

<span data-ttu-id="aa2f4-133">Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="aa2f4-133">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="aa2f4-134">-LocalCredential</span><span class="sxs-lookup"><span data-stu-id="aa2f4-134">-LocalCredential</span></span>

<span data-ttu-id="aa2f4-135">Hiermee geeft u een gebruikers account op dat is gemachtigd om verbinding te maken met de computer die is opgegeven door de para meter **ComputerName** .</span><span class="sxs-lookup"><span data-stu-id="aa2f4-135">Specifies a user account that has permission to connect to the computer specified by the **ComputerName** parameter.</span></span> <span data-ttu-id="aa2f4-136">Standaard is dit de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="aa2f4-136">The default is the current user.</span></span>

<span data-ttu-id="aa2f4-137">Typ een gebruikers naam, zoals `User01` of `Domain01\User01` , of voer een **PSCredential** -object in, zoals het certificaat dat is gegenereerd door de `Get-Credential` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="aa2f4-137">Type a user name, such as `User01` or `Domain01\User01`, or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="aa2f4-138">Als u een gebruikers naam typt, vraagt deze cmdlet u om een wacht woord.</span><span class="sxs-lookup"><span data-stu-id="aa2f4-138">If you type a user name, this cmdlet prompts you for a password.</span></span>

<span data-ttu-id="aa2f4-139">Als u een gebruikers account wilt opgeven dat is gemachtigd om verbinding te maken met het domein, gebruikt u de para meter **DomainCredential** .</span><span class="sxs-lookup"><span data-stu-id="aa2f4-139">To specify a user account that has permission to connect to the domain, use the **DomainCredential** parameter.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current User
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="aa2f4-140">-NewName</span><span class="sxs-lookup"><span data-stu-id="aa2f4-140">-NewName</span></span>

<span data-ttu-id="aa2f4-141">Hiermee geeft u een nieuwe naam voor de computer op.</span><span class="sxs-lookup"><span data-stu-id="aa2f4-141">Specifies a new name for the computer.</span></span>
<span data-ttu-id="aa2f4-142">Deze parameter is vereist.</span><span class="sxs-lookup"><span data-stu-id="aa2f4-142">This parameter is required.</span></span>

<span data-ttu-id="aa2f4-143">Standaard namen mogen letters ( `a-z` ), ( `A-Z` ), cijfers ( `0-9` ) en afbreek streepjes ( `-` ), maar geen spaties of punten () bevatten `.` .</span><span class="sxs-lookup"><span data-stu-id="aa2f4-143">Standard names may contain letters (`a-z`), (`A-Z`), numbers (`0-9`), and hyphens (`-`), but no spaces or periods (`.`).</span></span> <span data-ttu-id="aa2f4-144">De naam mag niet volledig uit cijfers bestaan en mag niet langer zijn dan 63 tekens</span><span class="sxs-lookup"><span data-stu-id="aa2f4-144">The name may not consist entirely of digits, and may not be longer than 63 characters</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="aa2f4-145">-PassThru</span><span class="sxs-lookup"><span data-stu-id="aa2f4-145">-PassThru</span></span>

<span data-ttu-id="aa2f4-146">Retourneert de resultaten van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="aa2f4-146">Returns the results of the command.</span></span>
<span data-ttu-id="aa2f4-147">Anders wordt met deze cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="aa2f4-147">Otherwise, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="aa2f4-148">-Restart</span><span class="sxs-lookup"><span data-stu-id="aa2f4-148">-Restart</span></span>

<span data-ttu-id="aa2f4-149">Geeft aan dat deze cmdlet de computer opnieuw opstart waarvan de naam is gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="aa2f4-149">Indicates that this cmdlet restarts the computer that was renamed.</span></span>
<span data-ttu-id="aa2f4-150">Het is vaak nood zakelijk om opnieuw op te starten om de wijziging van kracht te laten worden.</span><span class="sxs-lookup"><span data-stu-id="aa2f4-150">A restart is often required to make the change effective.</span></span>

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

### <span data-ttu-id="aa2f4-151">-WsmanAuthentication</span><span class="sxs-lookup"><span data-stu-id="aa2f4-151">-WsmanAuthentication</span></span>

<span data-ttu-id="aa2f4-152">Hiermee geeft u het mechanisme op dat wordt gebruikt voor het verifiëren van de gebruikers referenties wanneer deze cmdlet gebruikmaakt van het WSMan-protocol.</span><span class="sxs-lookup"><span data-stu-id="aa2f4-152">Specifies the mechanism that is used to authenticate the user credentials when this cmdlet uses the WSMan protocol.</span></span> <span data-ttu-id="aa2f4-153">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="aa2f4-153">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="aa2f4-154">**Basic**</span><span class="sxs-lookup"><span data-stu-id="aa2f4-154">**Basic**</span></span>
- <span data-ttu-id="aa2f4-155">**CredSSP**</span><span class="sxs-lookup"><span data-stu-id="aa2f4-155">**CredSSP**</span></span>
- <span data-ttu-id="aa2f4-156">**Standaard**</span><span class="sxs-lookup"><span data-stu-id="aa2f4-156">**Default**</span></span>
- <span data-ttu-id="aa2f4-157">**Samenvatting**</span><span class="sxs-lookup"><span data-stu-id="aa2f4-157">**Digest**</span></span>
- <span data-ttu-id="aa2f4-158">**Kerberos**</span><span class="sxs-lookup"><span data-stu-id="aa2f4-158">**Kerberos**</span></span>
- <span data-ttu-id="aa2f4-159">**Afspraken**</span><span class="sxs-lookup"><span data-stu-id="aa2f4-159">**Negotiate**</span></span>

<span data-ttu-id="aa2f4-160">De standaard waarde is **standaard**.</span><span class="sxs-lookup"><span data-stu-id="aa2f4-160">The default value is **Default**.</span></span>

<span data-ttu-id="aa2f4-161">Zie [AuthenticationMechanism Enumeration (Engelstalig)](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)voor meer informatie over de waarden van deze para meter.</span><span class="sxs-lookup"><span data-stu-id="aa2f4-161">For more information about the values of this parameter, see [AuthenticationMechanism Enumeration](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!WARNING]
> <span data-ttu-id="aa2f4-162">CredSSP-verificatie (Credential Security service provider), waarbij de gebruikers referenties worden door gegeven aan een externe computer die moet worden geverifieerd, is ontworpen voor opdrachten waarvoor verificatie is vereist voor meer dan één bron, zoals het openen van een externe netwerk share.</span><span class="sxs-lookup"><span data-stu-id="aa2f4-162">Credential Security Service Provider (CredSSP) authentication, in which the user credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span>
> <span data-ttu-id="aa2f4-163">Dit mechanisme verhoogt het beveiligings risico van de externe bewerking.</span><span class="sxs-lookup"><span data-stu-id="aa2f4-163">This mechanism increases the security risk of the remote operation.</span></span>
> <span data-ttu-id="aa2f4-164">Als er is geknoeid met de externe computer, kunnen de referenties die aan worden door gegeven, worden gebruikt om > de netwerk sessie te beheren.</span><span class="sxs-lookup"><span data-stu-id="aa2f4-164">If the remote computer is compromised, the credentials that are passed to it can be used to control > the network session.</span></span>

<span data-ttu-id="aa2f4-165">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="aa2f4-165">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Default, Basic, Negotiate, CredSSP, Digest, Kerberos

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="aa2f4-166">-Confirm</span><span class="sxs-lookup"><span data-stu-id="aa2f4-166">-Confirm</span></span>

<span data-ttu-id="aa2f4-167">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="aa2f4-167">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="aa2f4-168">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="aa2f4-168">-WhatIf</span></span>

<span data-ttu-id="aa2f4-169">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="aa2f4-169">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="aa2f4-170">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="aa2f4-170">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="aa2f4-171">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="aa2f4-171">CommonParameters</span></span>

<span data-ttu-id="aa2f4-172">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="aa2f4-172">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="aa2f4-173">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="aa2f4-173">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="aa2f4-174">INVOER</span><span class="sxs-lookup"><span data-stu-id="aa2f4-174">INPUTS</span></span>

### <span data-ttu-id="aa2f4-175">Geen</span><span class="sxs-lookup"><span data-stu-id="aa2f4-175">None</span></span>

<span data-ttu-id="aa2f4-176">Deze cmdlet heeft geen para meters die invoer door waarde krijgen.</span><span class="sxs-lookup"><span data-stu-id="aa2f4-176">This cmdlet does not have parameters that take input by value.</span></span> <span data-ttu-id="aa2f4-177">U kunt de waarden van de eigenschappen **ComputerName** en **newname** van objecten echter door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="aa2f4-177">However, you can pipe the values of the **ComputerName** and **NewName** properties of objects to this cmdlet.</span></span>

## <span data-ttu-id="aa2f4-178">UITVOER</span><span class="sxs-lookup"><span data-stu-id="aa2f4-178">OUTPUTS</span></span>

### <span data-ttu-id="aa2f4-179">Micro soft. Power shell. commands. ComputerChangeInfo</span><span class="sxs-lookup"><span data-stu-id="aa2f4-179">Microsoft.PowerShell.Commands.ComputerChangeInfo</span></span>

<span data-ttu-id="aa2f4-180">Met deze cmdlet wordt een **ComputerChangeInfo** -object geretourneerd als u de para meter **PassThru** opgeeft.</span><span class="sxs-lookup"><span data-stu-id="aa2f4-180">This cmdlet returns a **ComputerChangeInfo** object, if you specify the **PassThru** parameter.</span></span>
<span data-ttu-id="aa2f4-181">Anders wordt er geen uitvoer geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="aa2f4-181">Otherwise, it does not return any output.</span></span>

## <span data-ttu-id="aa2f4-182">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="aa2f4-182">NOTES</span></span>

<span data-ttu-id="aa2f4-183">Deze cmdlet is alleen beschikbaar op Windows-platforms.</span><span class="sxs-lookup"><span data-stu-id="aa2f4-183">This cmdlet is only available on Windows platforms.</span></span>

## <span data-ttu-id="aa2f4-184">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="aa2f4-184">RELATED LINKS</span></span>

[<span data-ttu-id="aa2f4-185">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="aa2f4-185">Restart-Computer</span></span>](Restart-Computer.md)

[<span data-ttu-id="aa2f4-186">Stop-computer</span><span class="sxs-lookup"><span data-stu-id="aa2f4-186">Stop-Computer</span></span>](Stop-Computer.md)