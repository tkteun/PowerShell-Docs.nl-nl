---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/1/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/rename-computer?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Rename-Computer
ms.openlocfilehash: 1c8cde77d16452c9488ce3af62e8b5f761213c80
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93249836"
---
# <span data-ttu-id="b3d9c-103">Rename-Computer</span><span class="sxs-lookup"><span data-stu-id="b3d9c-103">Rename-Computer</span></span>

## <span data-ttu-id="b3d9c-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="b3d9c-104">SYNOPSIS</span></span>
<span data-ttu-id="b3d9c-105">De naam van een computer wijzigen.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-105">Renames a computer.</span></span>

## <span data-ttu-id="b3d9c-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="b3d9c-106">SYNTAX</span></span>

```
Rename-Computer [-ComputerName <String>] [-PassThru] [-DomainCredential <PSCredential>]
 [-LocalCredential <PSCredential>] [-NewName] <String> [-Force] [-Restart] [-WsmanAuthentication <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="b3d9c-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="b3d9c-107">DESCRIPTION</span></span>

<span data-ttu-id="b3d9c-108">De `Rename-Computer` cmdlet hernoemt de naam van de lokale computer of een externe computer.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-108">The `Rename-Computer` cmdlet renames the local computer or a remote computer.</span></span>
<span data-ttu-id="b3d9c-109">De naam van een computer in elke opdracht wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-109">It renames one computer in each command.</span></span>

<span data-ttu-id="b3d9c-110">Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-110">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="b3d9c-111">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="b3d9c-111">EXAMPLES</span></span>

### <span data-ttu-id="b3d9c-112">Voor beeld 1: de naam van de lokale computer wijzigen</span><span class="sxs-lookup"><span data-stu-id="b3d9c-112">Example 1: Rename the local computer</span></span>

<span data-ttu-id="b3d9c-113">Met deze opdracht wordt de naam van de lokale computer gewijzigd in `Server044` en wordt deze opnieuw opgestart om de wijziging van kracht te laten worden.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-113">This command renames the local computer to `Server044` and then restarts it to make the change effective.</span></span>

```powershell
Rename-Computer -NewName "Server044" -DomainCredential Domain01\Admin01 -Restart
```

### <span data-ttu-id="b3d9c-114">Voor beeld 2: de naam van een externe computer wijzigen</span><span class="sxs-lookup"><span data-stu-id="b3d9c-114">Example 2: Rename a remote computer</span></span>

<span data-ttu-id="b3d9c-115">Met deze opdracht wordt de naam van de `Srv01` computer gewijzigd in `Server001` .</span><span class="sxs-lookup"><span data-stu-id="b3d9c-115">This command renames the `Srv01` computer to `Server001`.</span></span> <span data-ttu-id="b3d9c-116">De computer is niet opnieuw opgestart.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-116">The computer is not restarted.</span></span>

<span data-ttu-id="b3d9c-117">De **DomainCredential** para meter geeft u de referenties op van een gebruiker die gemachtigd is om de naam van computers in het domein te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-117">The **DomainCredential** parameter specifies the credentials of a user who has permission to rename computers in the domain.</span></span>

<span data-ttu-id="b3d9c-118">De **Force** -para meter onderdrukt de bevestigings prompt.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-118">The **Force** parameter suppresses the confirmation prompt.</span></span>

```powershell
Rename-Computer -ComputerName "Srv01" -NewName "Server001" -DomainCredential Domain01\Admin01 -Force
```

## <span data-ttu-id="b3d9c-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b3d9c-119">PARAMETERS</span></span>

### <span data-ttu-id="b3d9c-120">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="b3d9c-120">-ComputerName</span></span>

<span data-ttu-id="b3d9c-121">De naam van de opgegeven externe computer.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-121">Renames the specified remote computer.</span></span>
<span data-ttu-id="b3d9c-122">Standaard is dit de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-122">The default is the local computer.</span></span>

<span data-ttu-id="b3d9c-123">Typ de NetBIOS-naam, een IP-adres of een Fully Qualified Domain Name van een externe computer.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-123">Type the NetBIOS name, an IP address, or a fully qualified domain name of a remote computer.</span></span>
<span data-ttu-id="b3d9c-124">Als u de lokale computer wilt opgeven, typt u de naam van de computer, een punt ( `.` ) of `localhost` .</span><span class="sxs-lookup"><span data-stu-id="b3d9c-124">To specify the local computer, type the computer name, a dot (`.`), or `localhost`.</span></span>

<span data-ttu-id="b3d9c-125">Deze para meter is niet afhankelijk van externe communicatie met Power shell.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-125">This parameter does not rely on PowerShell remoting.</span></span>
<span data-ttu-id="b3d9c-126">U kunt de para meter **ComputerName** gebruiken `Rename-Computer` , zelfs als uw computer niet is geconfigureerd om externe opdrachten uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-126">You can use the **ComputerName** parameter of `Rename-Computer` even if your computer is not configured to run remote commands.</span></span>

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

### <span data-ttu-id="b3d9c-127">-DomainCredential</span><span class="sxs-lookup"><span data-stu-id="b3d9c-127">-DomainCredential</span></span>

<span data-ttu-id="b3d9c-128">Hiermee geeft u een gebruikers account op dat is gemachtigd om verbinding te maken met het domein.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-128">Specifies a user account that has permission to connect to the domain.</span></span>
<span data-ttu-id="b3d9c-129">Er zijn expliciete referenties vereist voor het wijzigen van de naam van een computer die lid is van een domein.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-129">Explicit credentials are required to rename a computer that is joined to a domain.</span></span>

<span data-ttu-id="b3d9c-130">Typ een gebruikers naam, zoals `User01` of `Domain01\User01` , of voer een **PSCredential** -object in, zoals het certificaat dat is gegenereerd door de `Get-Credential` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-130">Type a user name, such as `User01` or `Domain01\User01`, or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="b3d9c-131">Als u een gebruikers naam typt, vraagt deze cmdlet u om een wacht woord.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-131">If you type a user name, this cmdlet prompts you for a password.</span></span>

<span data-ttu-id="b3d9c-132">Als u een gebruikers account wilt opgeven dat is gemachtigd om verbinding te maken met de computer die is opgegeven door de para meter **ComputerName** , gebruikt u de para meter **LocalCredential** .</span><span class="sxs-lookup"><span data-stu-id="b3d9c-132">To specify a user account that has permission to connect to the computer that is specified by the **ComputerName** parameter, use the **LocalCredential** parameter.</span></span>

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

### <span data-ttu-id="b3d9c-133">-Force</span><span class="sxs-lookup"><span data-stu-id="b3d9c-133">-Force</span></span>

<span data-ttu-id="b3d9c-134">Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-134">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="b3d9c-135">-LocalCredential</span><span class="sxs-lookup"><span data-stu-id="b3d9c-135">-LocalCredential</span></span>

<span data-ttu-id="b3d9c-136">Hiermee geeft u een gebruikers account op dat is gemachtigd om verbinding te maken met de computer die is opgegeven door de para meter **ComputerName** .</span><span class="sxs-lookup"><span data-stu-id="b3d9c-136">Specifies a user account that has permission to connect to the computer specified by the **ComputerName** parameter.</span></span> <span data-ttu-id="b3d9c-137">Standaard is dit de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-137">The default is the current user.</span></span>

<span data-ttu-id="b3d9c-138">Typ een gebruikers naam, zoals `User01` of `Domain01\User01` , of voer een **PSCredential** -object in, zoals het certificaat dat is gegenereerd door de `Get-Credential` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-138">Type a user name, such as `User01` or `Domain01\User01`, or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="b3d9c-139">Als u een gebruikers naam typt, vraagt deze cmdlet u om een wacht woord.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-139">If you type a user name, this cmdlet prompts you for a password.</span></span>

<span data-ttu-id="b3d9c-140">Als u een gebruikers account wilt opgeven dat is gemachtigd om verbinding te maken met het domein, gebruikt u de para meter **DomainCredential** .</span><span class="sxs-lookup"><span data-stu-id="b3d9c-140">To specify a user account that has permission to connect to the domain, use the **DomainCredential** parameter.</span></span>

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

### <span data-ttu-id="b3d9c-141">-NewName</span><span class="sxs-lookup"><span data-stu-id="b3d9c-141">-NewName</span></span>

<span data-ttu-id="b3d9c-142">Hiermee geeft u een nieuwe naam voor de computer op.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-142">Specifies a new name for the computer.</span></span>
<span data-ttu-id="b3d9c-143">Deze parameter is vereist.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-143">This parameter is required.</span></span>

<span data-ttu-id="b3d9c-144">Standaard namen mogen letters ( `a-z` ), ( `A-Z` ), cijfers ( `0-9` ) en afbreek streepjes ( `-` ), maar geen spaties of punten () bevatten `.` .</span><span class="sxs-lookup"><span data-stu-id="b3d9c-144">Standard names may contain letters (`a-z`), (`A-Z`), numbers (`0-9`), and hyphens (`-`), but no spaces or periods (`.`).</span></span> <span data-ttu-id="b3d9c-145">De naam mag niet volledig uit cijfers bestaan en mag niet langer zijn dan 63 tekens</span><span class="sxs-lookup"><span data-stu-id="b3d9c-145">The name may not consist entirely of digits, and may not be longer than 63 characters</span></span>

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

### <span data-ttu-id="b3d9c-146">-PassThru</span><span class="sxs-lookup"><span data-stu-id="b3d9c-146">-PassThru</span></span>

<span data-ttu-id="b3d9c-147">Retourneert de resultaten van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-147">Returns the results of the command.</span></span>
<span data-ttu-id="b3d9c-148">Anders wordt met deze cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-148">Otherwise, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="b3d9c-149">-Restart</span><span class="sxs-lookup"><span data-stu-id="b3d9c-149">-Restart</span></span>

<span data-ttu-id="b3d9c-150">Geeft aan dat deze cmdlet de computer opnieuw opstart waarvan de naam is gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-150">Indicates that this cmdlet restarts the computer that was renamed.</span></span>
<span data-ttu-id="b3d9c-151">Het is vaak nood zakelijk om opnieuw op te starten om de wijziging van kracht te laten worden.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-151">A restart is often required to make the change effective.</span></span>

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

### <span data-ttu-id="b3d9c-152">-WsmanAuthentication</span><span class="sxs-lookup"><span data-stu-id="b3d9c-152">-WsmanAuthentication</span></span>

<span data-ttu-id="b3d9c-153">Hiermee geeft u het mechanisme op dat wordt gebruikt voor het verifiëren van de gebruikers referenties wanneer deze cmdlet gebruikmaakt van het WSMan-protocol.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-153">Specifies the mechanism that is used to authenticate the user credentials when this cmdlet uses the WSMan protocol.</span></span> <span data-ttu-id="b3d9c-154">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="b3d9c-154">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="b3d9c-155">**Basic**</span><span class="sxs-lookup"><span data-stu-id="b3d9c-155">**Basic**</span></span>
- <span data-ttu-id="b3d9c-156">**CredSSP**</span><span class="sxs-lookup"><span data-stu-id="b3d9c-156">**CredSSP**</span></span>
- <span data-ttu-id="b3d9c-157">**Prijs**</span><span class="sxs-lookup"><span data-stu-id="b3d9c-157">**Default**</span></span>
- <span data-ttu-id="b3d9c-158">**Samenvatting**</span><span class="sxs-lookup"><span data-stu-id="b3d9c-158">**Digest**</span></span>
- <span data-ttu-id="b3d9c-159">**Kerberos**</span><span class="sxs-lookup"><span data-stu-id="b3d9c-159">**Kerberos**</span></span>
- <span data-ttu-id="b3d9c-160">**Afspraken**</span><span class="sxs-lookup"><span data-stu-id="b3d9c-160">**Negotiate**</span></span>

<span data-ttu-id="b3d9c-161">De standaard waarde is **standaard**.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-161">The default value is **Default**.</span></span>

<span data-ttu-id="b3d9c-162">Zie [AuthenticationMechanism Enumeration (Engelstalig)](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)voor meer informatie over de waarden van deze para meter.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-162">For more information about the values of this parameter, see [AuthenticationMechanism Enumeration](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!WARNING]
> <span data-ttu-id="b3d9c-163">CredSSP-verificatie (Credential Security service provider), waarbij de gebruikers referenties worden door gegeven aan een externe computer die moet worden geverifieerd, is ontworpen voor opdrachten waarvoor verificatie is vereist voor meer dan één bron, zoals het openen van een externe netwerk share.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-163">Credential Security Service Provider (CredSSP) authentication, in which the user credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span>
> <span data-ttu-id="b3d9c-164">Dit mechanisme verhoogt het beveiligings risico van de externe bewerking.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-164">This mechanism increases the security risk of the remote operation.</span></span>
> <span data-ttu-id="b3d9c-165">Als er is geknoeid met de externe computer, kunnen de referenties die aan worden door gegeven, worden gebruikt om > de netwerk sessie te beheren.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-165">If the remote computer is compromised, the credentials that are passed to it can be used to control > the network session.</span></span>

<span data-ttu-id="b3d9c-166">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-166">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="b3d9c-167">-Confirm</span><span class="sxs-lookup"><span data-stu-id="b3d9c-167">-Confirm</span></span>

<span data-ttu-id="b3d9c-168">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-168">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="b3d9c-169">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="b3d9c-169">-WhatIf</span></span>

<span data-ttu-id="b3d9c-170">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-170">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="b3d9c-171">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-171">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="b3d9c-172">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b3d9c-172">CommonParameters</span></span>

<span data-ttu-id="b3d9c-173">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-173">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b3d9c-174">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-174">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="b3d9c-175">INVOER</span><span class="sxs-lookup"><span data-stu-id="b3d9c-175">INPUTS</span></span>

### <span data-ttu-id="b3d9c-176">Geen</span><span class="sxs-lookup"><span data-stu-id="b3d9c-176">None</span></span>

<span data-ttu-id="b3d9c-177">Deze cmdlet heeft geen para meters die invoer door waarde krijgen.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-177">This cmdlet does not have parameters that take input by value.</span></span>
<span data-ttu-id="b3d9c-178">U kunt de waarden van de eigenschappen **ComputerName** en **newname** van objecten echter door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-178">However, you can pipe the values of the **ComputerName** and **NewName** properties of objects to this cmdlet.</span></span>

## <span data-ttu-id="b3d9c-179">UITVOER</span><span class="sxs-lookup"><span data-stu-id="b3d9c-179">OUTPUTS</span></span>

### <span data-ttu-id="b3d9c-180">Micro soft. Power shell. commands. ComputerChangeInfo</span><span class="sxs-lookup"><span data-stu-id="b3d9c-180">Microsoft.PowerShell.Commands.ComputerChangeInfo</span></span>

<span data-ttu-id="b3d9c-181">Met deze cmdlet wordt een **ComputerChangeInfo** -object geretourneerd als u de para meter **PassThru** opgeeft.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-181">This cmdlet returns a **ComputerChangeInfo** object, if you specify the **PassThru** parameter.</span></span>
<span data-ttu-id="b3d9c-182">Anders wordt er geen uitvoer geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="b3d9c-182">Otherwise, it does not return any output.</span></span>

## <span data-ttu-id="b3d9c-183">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="b3d9c-183">NOTES</span></span>

## <span data-ttu-id="b3d9c-184">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="b3d9c-184">RELATED LINKS</span></span>

[<span data-ttu-id="b3d9c-185">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="b3d9c-185">Restart-Computer</span></span>](Restart-Computer.md)

[<span data-ttu-id="b3d9c-186">Stop-computer</span><span class="sxs-lookup"><span data-stu-id="b3d9c-186">Stop-Computer</span></span>](Stop-Computer.md)
