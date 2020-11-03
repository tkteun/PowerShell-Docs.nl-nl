---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 04/04/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-computer?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Computer
ms.openlocfilehash: 89e43220a8d5ac675ea232db09cf3edec2ca2b97
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250583"
---
# <span data-ttu-id="0896c-103">Remove-Computer</span><span class="sxs-lookup"><span data-stu-id="0896c-103">Remove-Computer</span></span>

## <span data-ttu-id="0896c-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="0896c-104">SYNOPSIS</span></span>
<span data-ttu-id="0896c-105">Hiermee verwijdert u de lokale computer uit het domein.</span><span class="sxs-lookup"><span data-stu-id="0896c-105">Removes the local computer from its domain.</span></span>

## <span data-ttu-id="0896c-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="0896c-106">SYNTAX</span></span>

### <span data-ttu-id="0896c-107">Lokaal (standaard)</span><span class="sxs-lookup"><span data-stu-id="0896c-107">Local (Default)</span></span>

```
Remove-Computer [[-UnjoinDomainCredential] <PSCredential>] [-Restart] [-Force] [-PassThru]
 [-WorkgroupName <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="0896c-108">Extern</span><span class="sxs-lookup"><span data-stu-id="0896c-108">Remote</span></span>

```
Remove-Computer -UnjoinDomainCredential <PSCredential> [-LocalCredential <PSCredential>] [-Restart]
 [-ComputerName <String[]>] [-Force] [-PassThru] [-WorkgroupName <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="0896c-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="0896c-109">DESCRIPTION</span></span>

<span data-ttu-id="0896c-110">De `Remove-Computer` cmdlet verwijdert de lokale computer en de externe computers uit hun huidige domeinen.</span><span class="sxs-lookup"><span data-stu-id="0896c-110">The `Remove-Computer` cmdlet removes the local computer and remote computers from their current domains.</span></span>

<span data-ttu-id="0896c-111">Wanneer u een computer uit een domein verwijdert, `Remove-Computer` schakelt u ook het domein account van de computer uit.</span><span class="sxs-lookup"><span data-stu-id="0896c-111">When you remove a computer from a domain, `Remove-Computer` also disables the domain account of the computer.</span></span> <span data-ttu-id="0896c-112">U moet expliciete referenties opgeven om de computer uit het domein te ontkoppelen, zelfs wanneer de referenties van de huidige gebruiker zijn.</span><span class="sxs-lookup"><span data-stu-id="0896c-112">You must provide explicit credentials to unjoin the computer from its domain, even when they are the credentials of the current user.</span></span> <span data-ttu-id="0896c-113">U moet de computer opnieuw opstarten om de wijziging van kracht te laten worden.</span><span class="sxs-lookup"><span data-stu-id="0896c-113">You must restart the computer to make the change effective.</span></span> <span data-ttu-id="0896c-114">Wanneer u een computer uit een domein verwijdert, moet u ook deze naar een werk groep verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="0896c-114">Also, when you remove a computer from a domain, you must move it to a workgroup.</span></span> <span data-ttu-id="0896c-115">Gebruik de para meter **werkgroepsjablonen** om de werk groep op te geven.</span><span class="sxs-lookup"><span data-stu-id="0896c-115">Use the **WorkgroupName** parameter to specify the workgroup.</span></span>

<span data-ttu-id="0896c-116">Als u een computer wilt verplaatsen van een werk groep naar een domein, van de ene werk groep naar een andere of van het ene naar het andere domein, gebruikt u de `Add-Computer` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0896c-116">To move a computer from a workgroup to a domain, from one workgroup to another, or from one domain to another, use the `Add-Computer` cmdlet.</span></span>

<span data-ttu-id="0896c-117">Als u de resultaten van de opdracht wilt weer geven, gebruikt u de para meters **uitgebreid** en **PassThru** .</span><span class="sxs-lookup"><span data-stu-id="0896c-117">To get the results of the command, use the **Verbose** and **PassThru** parameters.</span></span> <span data-ttu-id="0896c-118">Gebruik de para meter **Force** om de gebruikers prompt te onderdrukken.</span><span class="sxs-lookup"><span data-stu-id="0896c-118">To suppress the user prompt, use the **Force** parameter.</span></span>

<span data-ttu-id="0896c-119">`Remove-Computer` Hiermee verwijdert u de lokale computer en de externe computers uit domeinen.</span><span class="sxs-lookup"><span data-stu-id="0896c-119">`Remove-Computer` removes the local computer and remote computers from domains.</span></span> <span data-ttu-id="0896c-120">Het bevat referentie parameters waarmee alternatieve referenties worden opgegeven voor het maken van verbinding met externe computers en het ontkoppelen van een domein, een **restart** -para meter voor het opnieuw opstarten van de betrokken computers en een **werkgroeps** parameter voor het opgeven van de naam van de werk groep waaraan computers worden toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="0896c-120">It includes credential parameters that specify alternate credentials for connecting to remote computers, and unjoining from a domain, a **Restart** parameter for restarting the affected computers, and a **WorkgroupName** parameter for specifying the name of the workgroup to which computers are added.</span></span>

## <span data-ttu-id="0896c-121">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="0896c-121">EXAMPLES</span></span>

### <span data-ttu-id="0896c-122">Voor beeld 1: de lokale computer uit het domein verwijderen</span><span class="sxs-lookup"><span data-stu-id="0896c-122">Example 1: Remove the local computer from its domain</span></span>

<span data-ttu-id="0896c-123">In dit voor beeld wordt de lokale computer verwijderd van het domein waaraan deze is gekoppeld.</span><span class="sxs-lookup"><span data-stu-id="0896c-123">This example removes the local computer from the domain to which it is joined.</span></span>

```powershell
Remove-Computer -UnjoinDomaincredential Domain01\Admin01 -PassThru -Verbose -Restart
```

<span data-ttu-id="0896c-124">De para meter **UnjoinDomainCredential** geeft de referenties van een domein beheerder.</span><span class="sxs-lookup"><span data-stu-id="0896c-124">The **UnjoinDomainCredential** parameter provides the credentials of a domain administrator.</span></span> <span data-ttu-id="0896c-125">De **PassThru** -en de **uitgebreide** para meters geven informatie weer over het slagen of mislukken van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="0896c-125">The **PassThru** and the **Verbose** common parameters display information about the success or failure of the command.</span></span> <span data-ttu-id="0896c-126">Met de para meter **restart** wordt de computer opnieuw opgestart om de Verwijder bewerking te volt ooien.</span><span class="sxs-lookup"><span data-stu-id="0896c-126">The **Restart** parameter restarts the computer to complete the remove operation.</span></span>

<span data-ttu-id="0896c-127">Als er geen werkgroepnaam is opgegeven, wordt de computer verplaatst naar de werk groep met de naam nadat deze is verwijderd uit het domein.</span><span class="sxs-lookup"><span data-stu-id="0896c-127">When no workgroup name is specified, the computer is moved to the workgroup named after it is removed from its domain.</span></span>

### <span data-ttu-id="0896c-128">Voor beeld 2: meerdere computers verplaatsen naar een verouderde werk groep</span><span class="sxs-lookup"><span data-stu-id="0896c-128">Example 2: Move several computers to a legacy workgroup</span></span>

<span data-ttu-id="0896c-129">In dit voor beeld worden alle computers die worden vermeld in het `OldServers.txt` bestand uit hun domeinen verwijderd en verplaatst naar de **verouderde** werk groep.</span><span class="sxs-lookup"><span data-stu-id="0896c-129">This example removes all the computers listed in the `OldServers.txt` file from their domains and moves them into the **Legacy** workgroup.</span></span>

```powershell
Remove-Computer -ComputerName (Get-Content OldServers.txt) -LocalCredential Domain01\Admin01 -UnJoinDomainCredential Domain01\Admin01 -WorkgroupName "Legacy" -Force -Restart
```

<span data-ttu-id="0896c-130">De para meter **LocalCredential** geeft de referenties van een gebruiker die gemachtigd is om verbinding te maken met externe computers.</span><span class="sxs-lookup"><span data-stu-id="0896c-130">The **LocalCredential** parameter provides the credentials of a user who has permission to connect to remote computers.</span></span> <span data-ttu-id="0896c-131">De para meter **UnjoinDomainCredential** biedt de referenties van een gebruiker die gemachtigd is om de computers uit hun domeinen te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="0896c-131">The **UnjoinDomainCredential** parameter provides the credentials of a user who has permission to remove the computers from their domains.</span></span> <span data-ttu-id="0896c-132">De **Force** -para meter onderdrukt de bevestigings prompts voor elke computer.</span><span class="sxs-lookup"><span data-stu-id="0896c-132">The **Force** parameter suppresses the confirmation prompts for each computer.</span></span> <span data-ttu-id="0896c-133">De para meter **restart** start elke computer opnieuw op nadat deze is verwijderd uit het domein.</span><span class="sxs-lookup"><span data-stu-id="0896c-133">The **Restart** parameter restarts each of the computers after it is removed from its domain.</span></span>

### <span data-ttu-id="0896c-134">Voor beeld 3: computers verwijderen uit een werk groep zonder bevestiging</span><span class="sxs-lookup"><span data-stu-id="0896c-134">Example 3: Remove computers from a workgroup without confirmation</span></span>

<span data-ttu-id="0896c-135">In dit voor beeld worden de externe computer, Server01 en de lokale computer uit hun domeinen verwijderd en toegevoegd aan de **lokale** werk groep.</span><span class="sxs-lookup"><span data-stu-id="0896c-135">This example removes the remote computer, Server01, and the local computer from their domains and adds them to the **Local** workgroup.</span></span>

```powershell
Remove-Computer -ComputerName "Server01", "localhost" -UnjoinDomainCredential Domain01\Admin01 -WorkgroupName "Local" -Restart -Force
```

<span data-ttu-id="0896c-136">De **Force** -para meter onderdrukt de bevestigings prompt voor elke computer.</span><span class="sxs-lookup"><span data-stu-id="0896c-136">The **Force** parameter suppresses the confirmation prompt for each computer.</span></span> <span data-ttu-id="0896c-137">De para meter **restart** start de computers opnieuw op om de wijziging van kracht te laten worden.</span><span class="sxs-lookup"><span data-stu-id="0896c-137">The **Restart** parameter restarts the computers to make the change effective.</span></span>

## <span data-ttu-id="0896c-138">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="0896c-138">PARAMETERS</span></span>

### <span data-ttu-id="0896c-139">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="0896c-139">-ComputerName</span></span>

<span data-ttu-id="0896c-140">Hiermee geeft u de computers op die uit hun domeinen moeten worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="0896c-140">Specifies the computers to be removed from their domains.</span></span> <span data-ttu-id="0896c-141">Standaard is dit de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="0896c-141">The default is the local computer.</span></span>

<span data-ttu-id="0896c-142">Typ de NetBIOS-naam, een IP-adres of een Fully Qualified Domain Name (FQDN) van de externe computers.</span><span class="sxs-lookup"><span data-stu-id="0896c-142">Type the NetBIOS name, an IP address, or a fully qualified domain name (FQDN) of the remote computers.</span></span> <span data-ttu-id="0896c-143">Als u de lokale computer wilt opgeven, typt u de naam van de computer, een punt (.) of localhost.</span><span class="sxs-lookup"><span data-stu-id="0896c-143">To specify the local computer, type the computer name, a dot (.), or localhost.</span></span>

<span data-ttu-id="0896c-144">Deze para meter is niet afhankelijk van externe communicatie met Power shell.</span><span class="sxs-lookup"><span data-stu-id="0896c-144">This parameter does not rely on PowerShell remoting.</span></span> <span data-ttu-id="0896c-145">U kunt de para meter **ComputerName** gebruiken `Remove-Computer` , zelfs als uw computer niet is geconfigureerd om externe opdrachten uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="0896c-145">You can use the **ComputerName** parameter of `Remove-Computer` even if your computer is not configured to run remote commands.</span></span>

<span data-ttu-id="0896c-146">Deze para meter is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="0896c-146">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Remote
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="0896c-147">-Force</span><span class="sxs-lookup"><span data-stu-id="0896c-147">-Force</span></span>

<span data-ttu-id="0896c-148">Onderdrukt de gebruikers prompt.</span><span class="sxs-lookup"><span data-stu-id="0896c-148">Suppresses the user prompt.</span></span> <span data-ttu-id="0896c-149">Standaard wordt `Remove-Computer` u gevraagd om bevestiging voordat elke computer wordt verwijderd.</span><span class="sxs-lookup"><span data-stu-id="0896c-149">By default, `Remove-Computer` prompts you for confirmation before removing each computer.</span></span>

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

### <span data-ttu-id="0896c-150">-LocalCredential</span><span class="sxs-lookup"><span data-stu-id="0896c-150">-LocalCredential</span></span>

<span data-ttu-id="0896c-151">Hiermee geeft u een gebruikers account op dat is gemachtigd om verbinding te maken met de computers die door de para meter **ComputerName** worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="0896c-151">Specifies a user account that has permission to connect to the computers that the **ComputerName** parameter specifies.</span></span> <span data-ttu-id="0896c-152">Standaard is dit de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="0896c-152">The default is the current user.</span></span>

<span data-ttu-id="0896c-153">Typ een gebruikers naam, zoals `User01` of `Domain01\User01` , of voer een **PSCredential** -object in, zoals het certificaat dat is gegenereerd door de `Get-Credential` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0896c-153">Type a user name, such as `User01` or `Domain01\User01`, or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="0896c-154">Als u een gebruikers naam typt, wordt u door de cmdlet gevraagd om een wacht woord.</span><span class="sxs-lookup"><span data-stu-id="0896c-154">If you type a user name, the cmdlet prompts you for a password.</span></span> <span data-ttu-id="0896c-155">Als u een gebruikers account wilt opgeven dat is gemachtigd om de computer uit het huidige domein te verwijderen, gebruikt u de para meter **UnjoinDomainCredential** .</span><span class="sxs-lookup"><span data-stu-id="0896c-155">To specify a user account that has permission to remove the computer from its current domain, use the **UnjoinDomainCredential** parameter.</span></span>

<span data-ttu-id="0896c-156">Deze para meter is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="0896c-156">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: Remote
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0896c-157">-PassThru</span><span class="sxs-lookup"><span data-stu-id="0896c-157">-PassThru</span></span>

<span data-ttu-id="0896c-158">Retourneert de resultaten van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="0896c-158">Returns the results of the command.</span></span> <span data-ttu-id="0896c-159">Anders wordt met deze cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="0896c-159">Otherwise, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="0896c-160">-Restart</span><span class="sxs-lookup"><span data-stu-id="0896c-160">-Restart</span></span>

<span data-ttu-id="0896c-161">Geeft aan dat met deze cmdlet de computers worden gestart die worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="0896c-161">Indicates that this cmdlet restarts the computers that are being removed.</span></span> <span data-ttu-id="0896c-162">Het is vaak nood zakelijk om opnieuw op te starten om de wijziging van kracht te laten worden.</span><span class="sxs-lookup"><span data-stu-id="0896c-162">A restart is often required to make the change effective.</span></span>

<span data-ttu-id="0896c-163">Deze para meter is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="0896c-163">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="0896c-164">-UnjoinDomainCredential</span><span class="sxs-lookup"><span data-stu-id="0896c-164">-UnjoinDomainCredential</span></span>

<span data-ttu-id="0896c-165">Hiermee geeft u een gebruikers account op dat gemachtigd is om de computers uit hun huidige domeinen te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="0896c-165">Specifies a user account that has permission to remove the computers from their current domains.</span></span>
<span data-ttu-id="0896c-166">Expliciete referenties, zoals opgegeven door deze para meter, zijn vereist voor het verwijderen van externe computers uit een domein, zelfs wanneer de waarde de referenties van de huidige gebruiker is.</span><span class="sxs-lookup"><span data-stu-id="0896c-166">Explicit credentials, as provided by this parameter, are required to remove remote computers from a domain, even when the value is the credentials of the current user.</span></span>

<span data-ttu-id="0896c-167">Typ een gebruikers naam, zoals gebruiker01 of Domain01\User01, of voer een **PSCredential** -object in, bijvoorbeeld het account dat door wordt gegenereerd `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="0896c-167">Type a user name, such as User01 or Domain01\User01, or enter a **PSCredential** object, such as one generated by `Get-Credential`.</span></span> <span data-ttu-id="0896c-168">Als u een gebruikers naam typt, vraagt deze cmdlet u om een wacht woord.</span><span class="sxs-lookup"><span data-stu-id="0896c-168">If you type a user name, this cmdlet prompts you for a password.</span></span>

<span data-ttu-id="0896c-169">Als u een gebruikers account wilt opgeven dat is gemachtigd om verbinding te maken met de externe computers, gebruikt u de para meter **LocalCredential** .</span><span class="sxs-lookup"><span data-stu-id="0896c-169">To specify a user account that has permission to connect to the remote computers, use the **LocalCredential** parameter.</span></span>

<span data-ttu-id="0896c-170">Deze para meter is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="0896c-170">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: Local, Remote
Aliases: Credential

Required: False (Local), True (Remote)
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0896c-171">-Werkgroepnaam</span><span class="sxs-lookup"><span data-stu-id="0896c-171">-WorkgroupName</span></span>

<span data-ttu-id="0896c-172">Hiermee geeft u de naam van een werk groep waaraan de computers worden toegevoegd wanneer deze uit hun domeinen worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="0896c-172">Specifies the name of a workgroup to which the computers are added when they are removed from their domains.</span></span> <span data-ttu-id="0896c-173">De standaard waarde is **werk groep**.</span><span class="sxs-lookup"><span data-stu-id="0896c-173">The default value is **WORKGROUP**.</span></span> <span data-ttu-id="0896c-174">Wanneer u een computer uit een domein verwijdert, moet u deze toevoegen aan een werk groep.</span><span class="sxs-lookup"><span data-stu-id="0896c-174">When you remove a computer from a domain, you must add it to a workgroup.</span></span>

<span data-ttu-id="0896c-175">Deze para meter is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="0896c-175">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0896c-176">-Confirm</span><span class="sxs-lookup"><span data-stu-id="0896c-176">-Confirm</span></span>

<span data-ttu-id="0896c-177">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="0896c-177">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="0896c-178">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="0896c-178">-WhatIf</span></span>

<span data-ttu-id="0896c-179">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="0896c-179">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="0896c-180">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="0896c-180">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="0896c-181">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0896c-181">CommonParameters</span></span>

<span data-ttu-id="0896c-182">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="0896c-182">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0896c-183">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="0896c-183">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="0896c-184">INVOER</span><span class="sxs-lookup"><span data-stu-id="0896c-184">INPUTS</span></span>

### <span data-ttu-id="0896c-185">System. String</span><span class="sxs-lookup"><span data-stu-id="0896c-185">System.String</span></span>

<span data-ttu-id="0896c-186">U kunt computer namen door sluizen naar thiscmdlet.</span><span class="sxs-lookup"><span data-stu-id="0896c-186">You can pipe computer names to thiscmdlet.</span></span>

## <span data-ttu-id="0896c-187">UITVOER</span><span class="sxs-lookup"><span data-stu-id="0896c-187">OUTPUTS</span></span>

### <span data-ttu-id="0896c-188">Micro soft. Power shell. commands. ComputerChangeInfo</span><span class="sxs-lookup"><span data-stu-id="0896c-188">Microsoft.PowerShell.Commands.ComputerChangeInfo</span></span>

<span data-ttu-id="0896c-189">Wanneer u de para meter **PassThru** gebruikt, `Remove-Computer` wordt een **ComputerChangeInfo** -object geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="0896c-189">When you use the **PassThru** parameter, `Remove-Computer` returns a **ComputerChangeInfo** object.</span></span>
<span data-ttu-id="0896c-190">Anders wordt met deze cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="0896c-190">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="0896c-191">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="0896c-191">NOTES</span></span>

<span data-ttu-id="0896c-192">Met deze cmdlet worden geen computers uit werk groepen verwijderd.</span><span class="sxs-lookup"><span data-stu-id="0896c-192">This cmdlet does not remove computers from workgroups.</span></span>

## <span data-ttu-id="0896c-193">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="0896c-193">RELATED LINKS</span></span>

[<span data-ttu-id="0896c-194">Add-computer</span><span class="sxs-lookup"><span data-stu-id="0896c-194">Add-Computer</span></span>](Add-Computer.md)

[<span data-ttu-id="0896c-195">Checkpoint-Computer</span><span class="sxs-lookup"><span data-stu-id="0896c-195">Checkpoint-Computer</span></span>](Checkpoint-Computer.md)

[<span data-ttu-id="0896c-196">Verwijderen-computer</span><span class="sxs-lookup"><span data-stu-id="0896c-196">Remove-Computer</span></span>](Remove-Computer.md)

[<span data-ttu-id="0896c-197">Naam wijzigen-computer</span><span class="sxs-lookup"><span data-stu-id="0896c-197">Rename-Computer</span></span>](Rename-Computer.md)

[<span data-ttu-id="0896c-198">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="0896c-198">Restart-Computer</span></span>](Restart-Computer.md)

[<span data-ttu-id="0896c-199">Herstellen-computer</span><span class="sxs-lookup"><span data-stu-id="0896c-199">Restore-Computer</span></span>](Restore-Computer.md)

[<span data-ttu-id="0896c-200">Stop-computer</span><span class="sxs-lookup"><span data-stu-id="0896c-200">Stop-Computer</span></span>](Stop-Computer.md)

[<span data-ttu-id="0896c-201">Test-Connection</span><span class="sxs-lookup"><span data-stu-id="0896c-201">Test-Connection</span></span>](Test-Connection.md)
