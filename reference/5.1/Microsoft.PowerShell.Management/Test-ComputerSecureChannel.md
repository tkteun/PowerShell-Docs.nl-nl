---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/test-computersecurechannel?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-ComputerSecureChannel
ms.openlocfilehash: 20ea76e725a8ab53d7090078dc819a6297a639ff
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250529"
---
# <span data-ttu-id="0d537-103">Test-ComputerSecureChannel</span><span class="sxs-lookup"><span data-stu-id="0d537-103">Test-ComputerSecureChannel</span></span>

## <span data-ttu-id="0d537-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="0d537-104">SYNOPSIS</span></span>
<span data-ttu-id="0d537-105">Test en herstelt het beveiligde kanaal tussen de lokale computer en het bijbehorende domein.</span><span class="sxs-lookup"><span data-stu-id="0d537-105">Tests and repairs the secure channel between the local computer and its domain.</span></span>

## <span data-ttu-id="0d537-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="0d537-106">SYNTAX</span></span>

```
Test-ComputerSecureChannel [-Repair] [-Server <String>] [-Credential <PSCredential>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="0d537-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="0d537-107">DESCRIPTION</span></span>
<span data-ttu-id="0d537-108">Met de cmdlet **test-ComputerSecureChannel** wordt gecontroleerd of het kanaal tussen de lokale computer en het domein correct werkt door de status van de vertrouwens relaties te controleren.</span><span class="sxs-lookup"><span data-stu-id="0d537-108">The **Test-ComputerSecureChannel** cmdlet verifies that the channel between the local computer and its domain is working correctly by checking the status of its trust relationships.</span></span>
<span data-ttu-id="0d537-109">Als een verbinding mislukt, kunt u de *herstel* parameter gebruiken om te proberen deze te herstellen.</span><span class="sxs-lookup"><span data-stu-id="0d537-109">If a connection fails, you can use the *Repair* parameter to try to restore it.</span></span>

<span data-ttu-id="0d537-110">**Test-ComputerSecureChannel** retourneert $True als het kanaal correct werkt en $False als dat niet het geval is.</span><span class="sxs-lookup"><span data-stu-id="0d537-110">**Test-ComputerSecureChannel** returns $True if the channel is working correctly and $False if it is not.</span></span>
<span data-ttu-id="0d537-111">Dit leidt ertoe dat u de cmdlet kunt gebruiken in voorwaardelijke instructies in functies en scripts.</span><span class="sxs-lookup"><span data-stu-id="0d537-111">This result lets you use the cmdlet in conditional statements in functions and scripts.</span></span>
<span data-ttu-id="0d537-112">Gebruik de para meter *uitgebreid* om meer gedetailleerde test resultaten te krijgen.</span><span class="sxs-lookup"><span data-stu-id="0d537-112">To get more detailed test results, use the *Verbose* parameter.</span></span>

<span data-ttu-id="0d537-113">Deze cmdlet werkt op ongeveer dezelfde manier als NetDom.exe.</span><span class="sxs-lookup"><span data-stu-id="0d537-113">This cmdlet works much like NetDom.exe.</span></span>
<span data-ttu-id="0d537-114">Zowel NetDom als **test-ComputerSecureChannel** gebruiken de **Netlogon** -service om de acties uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="0d537-114">Both NetDom and **Test-ComputerSecureChannel** use the **NetLogon** service to perform the actions.</span></span>

## <span data-ttu-id="0d537-115">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="0d537-115">EXAMPLES</span></span>

### <span data-ttu-id="0d537-116">Voor beeld 1: een kanaal testen tussen de lokale computer en het bijbehorende domein</span><span class="sxs-lookup"><span data-stu-id="0d537-116">Example 1: Test a channel between the local computer and its domain</span></span>

```
PS C:\> Test-ComputerSecureChannel
True
```

<span data-ttu-id="0d537-117">Met deze opdracht wordt het kanaal getest tussen de lokale computer en het domein waarvan deze deel uitmaakt.</span><span class="sxs-lookup"><span data-stu-id="0d537-117">This command tests the channel between the local computer and the domain to which it is joined.</span></span>

### <span data-ttu-id="0d537-118">Voor beeld 2: een kanaal testen tussen de lokale computer en een domein controller</span><span class="sxs-lookup"><span data-stu-id="0d537-118">Example 2: Test a channel between the local computer and a domain controller</span></span>

```
PS C:\> Test-ComputerSecureChannel -Server "DCName.fabrikam.com"
True
```

<span data-ttu-id="0d537-119">Met deze opdracht geeft u een voorkeurs domein controller voor de test op.</span><span class="sxs-lookup"><span data-stu-id="0d537-119">This command specifies a preferred domain controller for the test.</span></span>

### <span data-ttu-id="0d537-120">Voor beeld 3: het kanaal tussen de lokale computer en het domein opnieuw instellen</span><span class="sxs-lookup"><span data-stu-id="0d537-120">Example 3: Reset the channel between the local computer and its domain</span></span>

```
PS C:\> Test-ComputerSecureChannel -Repair
True
```

<span data-ttu-id="0d537-121">Met deze opdracht wordt het kanaal tussen de lokale computer en het domein opnieuw ingesteld.</span><span class="sxs-lookup"><span data-stu-id="0d537-121">This command resets the channel between the local computer and its domain.</span></span>

### <span data-ttu-id="0d537-122">Voor beeld 4: gedetailleerde informatie over de test weer geven</span><span class="sxs-lookup"><span data-stu-id="0d537-122">Example 4: Display detailed information about the test</span></span>

```
PS C:\> Test-ComputerSecureChannel -verbose
VERBOSE: Performing operation "Test-ComputerSecureChannel" on Target "SERVER01".
True
VERBOSE: "The secure channel between 'SERVER01' and 'net.fabrikam.com' is alive and working correctly."
```

<span data-ttu-id="0d537-123">Met deze opdracht wordt de *uitgebreide* algemene para meter gebruikt om gedetailleerde berichten over de bewerking aan te vragen.</span><span class="sxs-lookup"><span data-stu-id="0d537-123">This command uses the *Verbose* common parameter to request detailed messages about the operation.</span></span>
<span data-ttu-id="0d537-124">Zie about_CommonParameters voor meer informatie over *uitgebreid*.</span><span class="sxs-lookup"><span data-stu-id="0d537-124">For more information about *Verbose* , see about_CommonParameters.</span></span>

### <span data-ttu-id="0d537-125">Voor beeld 5: een verbinding testen voordat u een script uitvoert</span><span class="sxs-lookup"><span data-stu-id="0d537-125">Example 5: Test a connection before you run a script</span></span>

```
PS C:\> Set-Alias tcsc Test-ComputerSecureChannel
if (!(tcsc))
{Write-Host "Connection failed. Reconnect and retry."}
else { &(.\Get-Servers.ps1) }
```

<span data-ttu-id="0d537-126">In dit voor beeld ziet u hoe u **test-ComputerSecureChannel** gebruikt om een verbinding te testen voordat u een script uitvoert dat de verbinding vereist.</span><span class="sxs-lookup"><span data-stu-id="0d537-126">This example shows how to use **Test-ComputerSecureChannel** to test a connection before you run a script that requires the connection.</span></span>

<span data-ttu-id="0d537-127">De eerste opdracht gebruikt de cmdlet Set-Alias om een alias te maken voor de naam van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0d537-127">The first command uses the Set-Alias cmdlet to create an alias for the cmdlet name.</span></span>
<span data-ttu-id="0d537-128">Dit bespaart ruimte en voor komt het typen van fouten.</span><span class="sxs-lookup"><span data-stu-id="0d537-128">This saves space and prevents typing errors.</span></span>

<span data-ttu-id="0d537-129">De **if** -instructie controleert de waarde die door **test-ComputerSecureChannel** wordt geretourneerd voordat een script wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="0d537-129">The **If** statement checks the value that **Test-ComputerSecureChannel** returns before it runs a script.</span></span>

## <span data-ttu-id="0d537-130">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="0d537-130">PARAMETERS</span></span>

### <span data-ttu-id="0d537-131">-Credential</span><span class="sxs-lookup"><span data-stu-id="0d537-131">-Credential</span></span>
<span data-ttu-id="0d537-132">Hiermee geeft u een gebruikers account op dat is gemachtigd om deze actie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="0d537-132">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="0d537-133">Typ een gebruikers naam, zoals gebruiker01 of Domain01\User01, of voer een **PSCredential** -object in, bijvoorbeeld een account dat door de Get-Credential cmdlet wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="0d537-133">Type a user name, such as User01 or Domain01\User01, or enter a **PSCredential** object, such as one that the Get-Credential cmdlet returns.</span></span>
<span data-ttu-id="0d537-134">De cmdlet maakt standaard gebruik van de referenties van de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="0d537-134">By default, the cmdlet uses the credentials of the current user.</span></span>

<span data-ttu-id="0d537-135">De *referentie* parameter is ontworpen voor gebruik in opdrachten die gebruikmaken van de *herstel* parameter voor het herstellen van het kanaal tussen de computer en het domein.</span><span class="sxs-lookup"><span data-stu-id="0d537-135">The *Credential* parameter is designed for use in commands that use the *Repair* parameter to repair the channel between the computer and the domain.</span></span>

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

### <span data-ttu-id="0d537-136">-Herstellen</span><span class="sxs-lookup"><span data-stu-id="0d537-136">-Repair</span></span>
<span data-ttu-id="0d537-137">Hiermee wordt aangegeven dat met deze cmdlet het kanaal dat door de NetLogon-service is ingesteld, wordt verwijderd en opnieuw gemaakt.</span><span class="sxs-lookup"><span data-stu-id="0d537-137">Indicates that this cmdlet removes and then rebuilds the channel established by the NetLogon service.</span></span>
<span data-ttu-id="0d537-138">Gebruik deze para meter om een verbinding te herstellen waarvan de test is mislukt.</span><span class="sxs-lookup"><span data-stu-id="0d537-138">Use this parameter to try to restore a connection that has failed the test.</span></span>

<span data-ttu-id="0d537-139">Als u deze para meter wilt gebruiken, moet de huidige gebruiker lid zijn van de groep Administrators op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="0d537-139">To use this parameter, the current user must be a member of the Administrators group on the local computer.</span></span>

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

### <span data-ttu-id="0d537-140">-Server</span><span class="sxs-lookup"><span data-stu-id="0d537-140">-Server</span></span>
<span data-ttu-id="0d537-141">Hiermee geeft u de domein controller waarop de opdracht moet worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="0d537-141">Specifies the domain controller to run the command.</span></span>
<span data-ttu-id="0d537-142">Als deze para meter niet wordt opgegeven, wordt met deze cmdlet een standaard domein controller voor de bewerking geselecteerd.</span><span class="sxs-lookup"><span data-stu-id="0d537-142">If this parameter is not specified, this cmdlet selects a default domain controller for the operation.</span></span>

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

### <span data-ttu-id="0d537-143">-Confirm</span><span class="sxs-lookup"><span data-stu-id="0d537-143">-Confirm</span></span>
<span data-ttu-id="0d537-144">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="0d537-144">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="0d537-145">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="0d537-145">-WhatIf</span></span>
<span data-ttu-id="0d537-146">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="0d537-146">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="0d537-147">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="0d537-147">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="0d537-148">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0d537-148">CommonParameters</span></span>
<span data-ttu-id="0d537-149">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="0d537-149">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0d537-150">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="0d537-150">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="0d537-151">INVOER</span><span class="sxs-lookup"><span data-stu-id="0d537-151">INPUTS</span></span>

### <span data-ttu-id="0d537-152">Geen</span><span class="sxs-lookup"><span data-stu-id="0d537-152">None</span></span>
<span data-ttu-id="0d537-153">U kunt geen invoer van een pipe naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0d537-153">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="0d537-154">UITVOER</span><span class="sxs-lookup"><span data-stu-id="0d537-154">OUTPUTS</span></span>

### <span data-ttu-id="0d537-155">System. Boolean</span><span class="sxs-lookup"><span data-stu-id="0d537-155">System.Boolean</span></span>
<span data-ttu-id="0d537-156">Deze cmdlet retourneert $True als de verbinding goed werkt en $False als dat niet het geval is.</span><span class="sxs-lookup"><span data-stu-id="0d537-156">This cmdlet returns $True if the connection is working correctly and $False if it is not.</span></span>

## <span data-ttu-id="0d537-157">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="0d537-157">NOTES</span></span>

* <span data-ttu-id="0d537-158">Als u een **test-ComputerSecureChannel** opdracht wilt uitvoeren in Windows Vista en latere versies van het Windows-besturings systeem, opent u Windows Power shell met de optie als administrator uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="0d537-158">To run a **Test-ComputerSecureChannel** command on Windows Vista and later versions of the Windows operating system, open Windows PowerShell by using the Run as administrator option.</span></span>
* <span data-ttu-id="0d537-159">**Test-ComputerSecureChannel** wordt geïmplementeerd met behulp van de functie **I_NetLogonControl2** , waarmee verschillende aspecten van de Netlogon-service worden beheerd.</span><span class="sxs-lookup"><span data-stu-id="0d537-159">**Test-ComputerSecureChannel** is implemented by using the **I_NetLogonControl2** function, which controls various aspects of the Netlogon service.</span></span>

## <span data-ttu-id="0d537-160">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="0d537-160">RELATED LINKS</span></span>

[<span data-ttu-id="0d537-161">Checkpoint-Computer</span><span class="sxs-lookup"><span data-stu-id="0d537-161">Checkpoint-Computer</span></span>](Checkpoint-Computer.md)

[<span data-ttu-id="0d537-162">Reset-ComputerMachinePassword</span><span class="sxs-lookup"><span data-stu-id="0d537-162">Reset-ComputerMachinePassword</span></span>](Reset-ComputerMachinePassword.md)

[<span data-ttu-id="0d537-163">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="0d537-163">Restart-Computer</span></span>](Restart-Computer.md)

[<span data-ttu-id="0d537-164">Stop-computer</span><span class="sxs-lookup"><span data-stu-id="0d537-164">Stop-Computer</span></span>](Stop-Computer.md)
