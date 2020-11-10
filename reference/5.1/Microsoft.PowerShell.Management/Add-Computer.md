---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/add-computer?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-Computer
ms.openlocfilehash: e3d1c5c071a334bddbfbc547ef2cc07e9e5c90aa
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388345"
---
# <span data-ttu-id="21596-103">Add-Computer</span><span class="sxs-lookup"><span data-stu-id="21596-103">Add-Computer</span></span>

## <span data-ttu-id="21596-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="21596-104">SYNOPSIS</span></span>
<span data-ttu-id="21596-105">De lokale computer toevoegen aan een domein of werk groep.</span><span class="sxs-lookup"><span data-stu-id="21596-105">Add the local computer to a domain or workgroup.</span></span>

## <span data-ttu-id="21596-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="21596-106">SYNTAX</span></span>

### <span data-ttu-id="21596-107">Domein (standaard)</span><span class="sxs-lookup"><span data-stu-id="21596-107">Domain (Default)</span></span>

```
Add-Computer [-ComputerName <String[]>] [-LocalCredential <PSCredential>]
 [-UnjoinDomainCredential <PSCredential>] -Credential <PSCredential> [-DomainName] <String> [-OUPath <String>]
 [-Server <String>] [-Unsecure] [-Options <JoinOptions>] [-Restart] [-PassThru] [-NewName <String>] [-Force]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="21596-108">Werkgroep</span><span class="sxs-lookup"><span data-stu-id="21596-108">Workgroup</span></span>

```
Add-Computer [-ComputerName <String[]>] [-LocalCredential <PSCredential>] [-Credential <PSCredential>]
 [-WorkgroupName] <String> [-Restart] [-PassThru] [-NewName <String>] [-Force] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="21596-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="21596-109">DESCRIPTION</span></span>

<span data-ttu-id="21596-110">De `Add-Computer` cmdlet voegt de lokale computer of externe computers toe aan een domein of werk groep, of verplaatst ze van het ene domein naar het andere.</span><span class="sxs-lookup"><span data-stu-id="21596-110">The `Add-Computer` cmdlet adds the local computer or remote computers to a domain or workgroup, or moves them from one domain to another.</span></span> <span data-ttu-id="21596-111">Er wordt ook een domein account gemaakt als de computer wordt toegevoegd aan het domein zonder een account.</span><span class="sxs-lookup"><span data-stu-id="21596-111">It also creates a domain account if the computer is added to the domain without an account.</span></span>

<span data-ttu-id="21596-112">U kunt de para meters van deze cmdlet gebruiken om een organisatie-eenheid (OE) en domein controller op te geven of een niet-beveiligde samen voeging uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="21596-112">You can use the parameters of this cmdlet to specify an organizational unit (OU) and domain controller or to perform an unsecure join.</span></span>

<span data-ttu-id="21596-113">Als u de resultaten van de opdracht wilt weer geven, gebruikt u de para meters **uitgebreid** en **PassThru** .</span><span class="sxs-lookup"><span data-stu-id="21596-113">To get the results of the command, use the **Verbose** and **PassThru** parameters.</span></span>

## <span data-ttu-id="21596-114">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="21596-114">EXAMPLES</span></span>

### <span data-ttu-id="21596-115">Voor beeld 1: een lokale computer toevoegen aan een domein en de computer opnieuw opstarten</span><span class="sxs-lookup"><span data-stu-id="21596-115">Example 1: Add a local computer to a domain then restart the computer</span></span>

```powershell
Add-Computer -DomainName Domain01 -Restart
```

<span data-ttu-id="21596-116">Met deze opdracht wordt de lokale computer aan het domein Domain01 toegevoegd en wordt de computer opnieuw opgestart om de wijziging van kracht te laten worden.</span><span class="sxs-lookup"><span data-stu-id="21596-116">This command adds the local computer to the Domain01 domain and then restarts the computer to make the change effective.</span></span>

### <span data-ttu-id="21596-117">Voor beeld 2: een lokale computer toevoegen aan een werk groep</span><span class="sxs-lookup"><span data-stu-id="21596-117">Example 2: Add a local computer to a workgroup</span></span>

```powershell
Add-Computer -WorkgroupName WORKGROUP-A
```

<span data-ttu-id="21596-118">Met deze opdracht wordt de lokale computer toegevoegd aan de werk groep-een werk groep.</span><span class="sxs-lookup"><span data-stu-id="21596-118">This command adds the local computer to the Workgroup-A workgroup.</span></span>

### <span data-ttu-id="21596-119">Voor beeld 3: een lokale computer toevoegen aan een domein</span><span class="sxs-lookup"><span data-stu-id="21596-119">Example 3: Add a local computer to a domain</span></span>

```powershell
Add-Computer -DomainName Domain01 -Server Domain01\DC01 -PassThru -Verbose
```

<span data-ttu-id="21596-120">Met deze opdracht wordt de lokale computer aan het Domain01-domein toegevoegd met behulp van de Domain01\DC01-domein controller.</span><span class="sxs-lookup"><span data-stu-id="21596-120">This command adds the local computer to the Domain01 domain by using the Domain01\DC01 domain controller.</span></span>

<span data-ttu-id="21596-121">De opdracht gebruikt de para meter **PassThru** en **uitgebreid** om gedetailleerde informatie over de resultaten van de opdracht op te halen.</span><span class="sxs-lookup"><span data-stu-id="21596-121">The command uses the **PassThru** and **Verbose** parameters to get detailed information about the results of the command.</span></span>

### <span data-ttu-id="21596-122">Voor beeld 4: een lokale computer aan een domein toevoegen met behulp van de para meter OUPath</span><span class="sxs-lookup"><span data-stu-id="21596-122">Example 4: Add a local computer to a domain using the OUPath parameter</span></span>

```powershell
Add-Computer -DomainName Domain02 -OUPath "OU=testOU,DC=domain,DC=Domain,DC=com"
```

<span data-ttu-id="21596-123">Met deze opdracht wordt de lokale computer aan het domein Domain02 toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="21596-123">This command adds the local computer to the Domain02 domain.</span></span>
<span data-ttu-id="21596-124">De para meter OUPath wordt gebruikt om de organisatie-eenheid voor de nieuwe accounts op te geven.</span><span class="sxs-lookup"><span data-stu-id="21596-124">It uses the OUPath parameter to specify the organizational unit for the new accounts.</span></span>

### <span data-ttu-id="21596-125">Voor beeld 5: een lokale computer toevoegen aan een domein met behulp van referenties</span><span class="sxs-lookup"><span data-stu-id="21596-125">Example 5: Add a local computer to a domain using credentials</span></span>

```powershell
Add-Computer -ComputerName Server01 -LocalCredential Server01\Admin01 -DomainName Domain02 -Credential Domain02\Admin02 -Restart -Force
```

<span data-ttu-id="21596-126">Met deze opdracht wordt de Server01-computer toegevoegd aan het domein Domain02.</span><span class="sxs-lookup"><span data-stu-id="21596-126">This command adds the Server01 computer to the Domain02 domain.</span></span> <span data-ttu-id="21596-127">De para meter **LocalCredential** wordt gebruikt om een gebruikers account op te geven dat is gemachtigd om verbinding te maken met de Server01-computer.</span><span class="sxs-lookup"><span data-stu-id="21596-127">It uses the **LocalCredential** parameter to specify a user account that has permission to connect to the Server01 computer.</span></span> <span data-ttu-id="21596-128">De para meter **Credential** wordt gebruikt om een gebruikers account op te geven dat gemachtigd is om computers aan het domein toe te voegen.</span><span class="sxs-lookup"><span data-stu-id="21596-128">It uses the **Credential** parameter to specify a user account that has permission to join computers to the domain.</span></span> <span data-ttu-id="21596-129">De para meter **restart** wordt gebruikt om de computer opnieuw op te starten nadat de samen voeging is voltooid en de para meter **Force** om bevestigings berichten van gebruikers te onderdrukken.</span><span class="sxs-lookup"><span data-stu-id="21596-129">It uses the **Restart** parameter to restart the computer after the join operation completes and the **Force** parameter to suppress user confirmation messages.</span></span>

### <span data-ttu-id="21596-130">Voor beeld 6: een groep computers verplaatsen naar een nieuw domein</span><span class="sxs-lookup"><span data-stu-id="21596-130">Example 6: Move a group of computers to a new domain</span></span>

```powershell
Add-Computer -ComputerName Server01, Server02, localhost -DomainName Domain02 -LocalCredential Domain01\User01 -UnjoinDomainCredential Domain01\Admin01 -Credential Domain02\Admin01 -Restart
```

<span data-ttu-id="21596-131">Met deze opdracht worden de Server01-en Server02-computers en de lokale computer verplaatst van Domain01 naar Domain02.</span><span class="sxs-lookup"><span data-stu-id="21596-131">This command moves the Server01 and Server02 computers, and the local computer, from Domain01 to Domain02.</span></span>

<span data-ttu-id="21596-132">De para meter **LocalCredential** wordt gebruikt om een gebruikers account op te geven dat is gemachtigd om verbinding te maken met de drie betrokken computers.</span><span class="sxs-lookup"><span data-stu-id="21596-132">It uses the **LocalCredential** parameter to specify a user account that has permission to connect to the three affected computers.</span></span> <span data-ttu-id="21596-133">De para meter **UnjoinDomainCredential** wordt gebruikt om een gebruikers account op te geven dat gemachtigd is om de computers uit het domein Domain01 te ontkoppelen en de para meter **Credential** om een gebruikers account op te geven dat gemachtigd is om de computers toe te voegen aan het Domain02-domein.</span><span class="sxs-lookup"><span data-stu-id="21596-133">It uses the **UnjoinDomainCredential** parameter to specify a user account that has permission to unjoin the computers from the Domain01 domain and the **Credential** parameter to specify a user account that has permission to join the computers to the Domain02 domain.</span></span> <span data-ttu-id="21596-134">De para meter **restart** wordt gebruikt om alle drie de computers opnieuw op te starten nadat de verplaatsing is voltooid.</span><span class="sxs-lookup"><span data-stu-id="21596-134">It uses the **Restart** parameter to restart all three computers after the move is complete.</span></span>

### <span data-ttu-id="21596-135">Voor beeld 7: een computer verplaatsen naar een nieuw domein en de naam van de computer wijzigen</span><span class="sxs-lookup"><span data-stu-id="21596-135">Example 7: Move a computer to a new domain and change the name of the computer</span></span>

```powershell
Add-Computer -ComputerName Server01 -DomainName Domain02 -NewName Server044 -Credential Domain02\Admin01 -Restart
```

<span data-ttu-id="21596-136">Met deze opdracht wordt de Server01-computer verplaatst naar de Domain02 en wordt de naam van de computer gewijzigd in Server044.</span><span class="sxs-lookup"><span data-stu-id="21596-136">This command moves the Server01 computer to the Domain02 and changes the machine name to Server044.</span></span>

<span data-ttu-id="21596-137">Met de opdracht wordt de referentie van de huidige gebruiker gebruikt om verbinding te maken met de Server01-computer en ontkoppelt van het huidige domein.</span><span class="sxs-lookup"><span data-stu-id="21596-137">The command uses the credential of the current user to connect to the Server01 computer and unjoin it from its current domain.</span></span> <span data-ttu-id="21596-138">De para meter **Credential** wordt gebruikt om een gebruikers account op te geven dat gemachtigd is om de computer toe te voegen aan het domein Domain02.</span><span class="sxs-lookup"><span data-stu-id="21596-138">It uses the **Credential** parameter to specify a user account that has permission to join the computer to the Domain02 domain.</span></span>

### <span data-ttu-id="21596-139">Voor beeld 8: computers die worden vermeld in een bestand toevoegen aan een nieuw domein</span><span class="sxs-lookup"><span data-stu-id="21596-139">Example 8: Add computers listed in a file to a new domain</span></span>

```powershell
Add-Computer -ComputerName (Get-Content Servers.txt) -DomainName Domain02 -Credential Domain02\Admin02 -Options Win9xUpgrade  -Restart
```

<span data-ttu-id="21596-140">Met deze opdracht worden de computers die worden vermeld in het Servers.txt-bestand toegevoegd aan het domein Domain02.</span><span class="sxs-lookup"><span data-stu-id="21596-140">This command adds the computers that are listed in the Servers.txt file to the Domain02 domain.</span></span> <span data-ttu-id="21596-141">De para meter **Options** wordt gebruikt om de optie **Win9xUpgrade** op te geven.</span><span class="sxs-lookup"><span data-stu-id="21596-141">It uses the **Options** parameter to specify the **Win9xUpgrade** option.</span></span> <span data-ttu-id="21596-142">Met de para meter **restart** worden alle pas toegevoegde computers opnieuw opgestart nadat de samen voeging is voltooid.</span><span class="sxs-lookup"><span data-stu-id="21596-142">The **Restart** parameter restarts all of the newly added computers after the join operation completes.</span></span>

### <span data-ttu-id="21596-143">Voor beeld 9: een computer toevoegen aan een domein met behulp van vooraf gedefinieerde computer referenties</span><span class="sxs-lookup"><span data-stu-id="21596-143">Example 9: Add a computer to a domain using predefined computer credentials</span></span>

<span data-ttu-id="21596-144">Deze eerste opdracht moet worden uitgevoerd door een beheerder vanaf een computer die al is toegevoegd aan het domein `Domain03` :</span><span class="sxs-lookup"><span data-stu-id="21596-144">This first command should be run by an administrator from a computer that is already joined to domain `Domain03`:</span></span>

```powershell
New-ADComputer -Name "Server02" -AccountPassword (ConvertTo-SecureString -String 'TempJoinPA$$' -AsPlainText -Force)

# Then this command is run from `Server02` which is not yet domain-joined:

$joinCred = New-Object pscredential -ArgumentList ([pscustomobject]@{
    UserName = $null
    Password = (ConvertTo-SecureString -String 'TempJoinPA$$' -AsPlainText -Force)[0]
})
Add-Computer -Domain "Domain03" -Options UnsecuredJoin,PasswordPass -Credential $joinCred
```

<span data-ttu-id="21596-145">Met deze combi natie van opdrachten maakt u een nieuw computer account met een vooraf gedefinieerde naam en een tijdelijk wacht woord voor samen voegen in een domein met een bestaande computer die lid is van een domein.</span><span class="sxs-lookup"><span data-stu-id="21596-145">This combination of commands creates a new computer account with a predefined name and temporary join password in a domain using an existing domain-joined computer.</span></span> <span data-ttu-id="21596-146">Vervolgens wordt de computer met de vooraf gedefinieerde naam afzonderlijk toegevoegd aan het domein met alleen de computer naam en het tijdelijke wacht woord voor samen voegen.</span><span class="sxs-lookup"><span data-stu-id="21596-146">Then separately, a computer with the predefined name joins the domain using only the computer name and the temporary join password.</span></span>
<span data-ttu-id="21596-147">Het vooraf gedefinieerde wacht woord wordt alleen gebruikt ter ondersteuning van de koppelings bewerking en wordt vervangen als onderdeel van de normale procedure voor computer accounts nadat de verbinding met de computer is voltooid.</span><span class="sxs-lookup"><span data-stu-id="21596-147">The predefined password is only used to support the join operation and is replaced as part of normal computer account procedures after the computer completes the join.</span></span>

## <span data-ttu-id="21596-148">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="21596-148">PARAMETERS</span></span>

### <span data-ttu-id="21596-149">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="21596-149">-ComputerName</span></span>

<span data-ttu-id="21596-150">Specificeert de computers die aan een domein of werk groep moeten worden toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="21596-150">Specifies the computers to add to a domain or workgroup.</span></span>
<span data-ttu-id="21596-151">Standaard is dit de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="21596-151">The default is the local computer.</span></span>

<span data-ttu-id="21596-152">Typ de NetBIOS-naam, een Internet Protocol IP-adres of een Fully Qualified Domain Name van elke externe computer.</span><span class="sxs-lookup"><span data-stu-id="21596-152">Type the NetBIOS name, an Internet Protocol (IP) address, or a fully qualified domain name of each of the remote computers.</span></span> <span data-ttu-id="21596-153">Typ de computer naam, een punt ( `.` ) of ' localhost ' om de lokale computer op te geven.</span><span class="sxs-lookup"><span data-stu-id="21596-153">To specify the local computer, type the computer name, a dot (`.`), or "localhost".</span></span>

<span data-ttu-id="21596-154">Deze para meter is niet gebaseerd op externe communicatie met Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="21596-154">This parameter does not rely on Windows PowerShell remoting.</span></span> <span data-ttu-id="21596-155">U kunt de para meter **ComputerName** gebruiken `Add-Computer` , zelfs als uw computer niet is geconfigureerd om externe opdrachten uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="21596-155">You can use the **ComputerName** parameter of `Add-Computer` even if your computer is not configured to run remote commands.</span></span>

<span data-ttu-id="21596-156">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="21596-156">This parameter is introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Local computer
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="21596-157">-Credential</span><span class="sxs-lookup"><span data-stu-id="21596-157">-Credential</span></span>

<span data-ttu-id="21596-158">Hiermee geeft u een gebruikers account op dat gemachtigd is om de computers toe te voegen aan een nieuw domein.</span><span class="sxs-lookup"><span data-stu-id="21596-158">Specifies a user account that has permission to join the computers to a new domain.</span></span>
<span data-ttu-id="21596-159">Standaard is dit de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="21596-159">The default is the current user.</span></span>

<span data-ttu-id="21596-160">Typ een gebruikers naam, zoals "gebruiker01" of "Domain01\User01", of voer een **PSCredential** -object in, zoals het account dat is gegenereerd door de `Get-Credential` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="21596-160">Type a user name, such as "User01" or "Domain01\User01", or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="21596-161">Als u een gebruikers naam typt, wordt u gevraagd een wacht woord op te vragen.</span><span class="sxs-lookup"><span data-stu-id="21596-161">If you type a user name, you will be prompted for a password.</span></span>

<span data-ttu-id="21596-162">Als u een gebruikers account wilt opgeven dat is gemachtigd om de computer uit het huidige domein te verwijderen, gebruikt u de para meter **UnjoinDomainCredential** .</span><span class="sxs-lookup"><span data-stu-id="21596-162">To specify a user account that has permission to remove the computer from its current domain, use the **UnjoinDomainCredential** parameter.</span></span> <span data-ttu-id="21596-163">Als u een gebruikers account wilt opgeven dat is gemachtigd om verbinding te maken met een externe computer, gebruikt u de para meter **LocalCredential** .</span><span class="sxs-lookup"><span data-stu-id="21596-163">To specify a user account that has permission to connect to a remote computer, use the **LocalCredential** parameter.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: Domain, Workgroup
Aliases: DomainCredential

Required: True (Domain), False (Workgroup)
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="21596-164">-DomainName</span><span class="sxs-lookup"><span data-stu-id="21596-164">-DomainName</span></span>

<span data-ttu-id="21596-165">Hiermee geeft u het domein waaraan de computers worden toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="21596-165">Specifies the domain to which the computers are added.</span></span> <span data-ttu-id="21596-166">Deze para meter is vereist bij het toevoegen van de computers aan een domein.</span><span class="sxs-lookup"><span data-stu-id="21596-166">This parameter is required when adding the computers to a domain.</span></span>

```yaml
Type: System.String
Parameter Sets: Domain
Aliases: DN, Domain

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="21596-167">-Force</span><span class="sxs-lookup"><span data-stu-id="21596-167">-Force</span></span>

<span data-ttu-id="21596-168">Onderdrukt de vraag om bevestiging van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="21596-168">Suppresses the user confirmation prompt.</span></span> <span data-ttu-id="21596-169">Als u deze para meter niet opgeeft, `Add-Computer` moet u de toevoeging van elke computer bevestigen.</span><span class="sxs-lookup"><span data-stu-id="21596-169">Without this parameter, `Add-Computer` requires you to confirm the addition of each computer.</span></span>

<span data-ttu-id="21596-170">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="21596-170">This parameter is introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="21596-171">-LocalCredential</span><span class="sxs-lookup"><span data-stu-id="21596-171">-LocalCredential</span></span>

<span data-ttu-id="21596-172">Hiermee geeft u een gebruikers account op dat is gemachtigd om verbinding te maken met de computers die zijn opgegeven door de para meter **ComputerName** .</span><span class="sxs-lookup"><span data-stu-id="21596-172">Specifies a user account that has permission to connect to the computers that are specified by the **ComputerName** parameter.</span></span> <span data-ttu-id="21596-173">Standaard is dit de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="21596-173">The default is the current user.</span></span>

<span data-ttu-id="21596-174">Typ een gebruikers naam, zoals "gebruiker01" of "Domain01\User01", of voer een **PSCredential** -object in, zoals het account dat is gegenereerd door de `Get-Credential` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="21596-174">Type a user name, such as "User01" or "Domain01\User01", or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="21596-175">Als u een gebruikers naam typt, wordt u gevraagd een wacht woord op te vragen.</span><span class="sxs-lookup"><span data-stu-id="21596-175">If you type a user name, you will be prompted for a password.</span></span>

<span data-ttu-id="21596-176">Als u een gebruikers account wilt opgeven dat gemachtigd is om de computers toe te voegen aan een nieuw domein, gebruikt u de para meter **Credential** .</span><span class="sxs-lookup"><span data-stu-id="21596-176">To specify a user account that has permission to add the computers to a new domain, use the **Credential** parameter.</span></span> <span data-ttu-id="21596-177">Als u een gebruikers account wilt opgeven dat gemachtigd is om de computers uit hun huidige domein te verwijderen, gebruikt u de para meter **UnjoinDomainCredential** .</span><span class="sxs-lookup"><span data-stu-id="21596-177">To specify a user account that has permission to remove the computers from their current domain, use the **UnjoinDomainCredential** parameter.</span></span>

<span data-ttu-id="21596-178">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="21596-178">This parameter is introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="21596-179">-NewName</span><span class="sxs-lookup"><span data-stu-id="21596-179">-NewName</span></span>

<span data-ttu-id="21596-180">Hiermee geeft u een nieuwe naam voor de computer in het nieuwe domein.</span><span class="sxs-lookup"><span data-stu-id="21596-180">Specifies a new name for the computer in the new domain.</span></span> <span data-ttu-id="21596-181">Deze para meter is alleen geldig wanneer er één computer wordt toegevoegd of verplaatst.</span><span class="sxs-lookup"><span data-stu-id="21596-181">This parameter is valid only when one computer is being added or moved.</span></span>

<span data-ttu-id="21596-182">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="21596-182">This parameter is introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="21596-183">-Opties</span><span class="sxs-lookup"><span data-stu-id="21596-183">-Options</span></span>

<span data-ttu-id="21596-184">Hiermee geeft u geavanceerde opties op voor de **toevoeg bewerking toevoegen** aan de computer.</span><span class="sxs-lookup"><span data-stu-id="21596-184">Specifies advanced options for the **Add-Computer** join operation.</span></span> <span data-ttu-id="21596-185">Voer een of meer waarden in een door komma's gescheiden teken reeks in.</span><span class="sxs-lookup"><span data-stu-id="21596-185">Enter one or more values in a comma-separated string.</span></span>

<span data-ttu-id="21596-186">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="21596-186">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="21596-187">**AccountCreate** : Hiermee wordt een domein account gemaakt.</span><span class="sxs-lookup"><span data-stu-id="21596-187">**AccountCreate** : Creates a domain account.</span></span> <span data-ttu-id="21596-188">De cmdlet **add-computer** maakt automatisch een domein account wanneer een computer wordt toegevoegd aan een domein.</span><span class="sxs-lookup"><span data-stu-id="21596-188">The **Add-Computer** cmdlet automatically creates a domain account when it adds a computer to a domain.</span></span> <span data-ttu-id="21596-189">Deze optie is opgenomen voor volledigheid.</span><span class="sxs-lookup"><span data-stu-id="21596-189">This option is included for completeness.</span></span>

- <span data-ttu-id="21596-190">**Win9XUpgrade** : geeft aan dat de koppelings bewerking deel uitmaakt van een upgrade van het Windows-besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="21596-190">**Win9XUpgrade** : Indicates that the join operation is part of a Windows operating system upgrade.</span></span>

- <span data-ttu-id="21596-191">**UnsecuredJoin** : voert een niet-beveiligde samen voeging uit.</span><span class="sxs-lookup"><span data-stu-id="21596-191">**UnsecuredJoin** : Performs an unsecured join.</span></span> <span data-ttu-id="21596-192">Als u een niet-beveiligde samen voeging wilt aanvragen, gebruikt u de para meter *unsecure* of deze optie.</span><span class="sxs-lookup"><span data-stu-id="21596-192">To request an unsecured join, use the *Unsecure* parameter or this option.</span></span> <span data-ttu-id="21596-193">Als u een computer wachtwoord wilt door geven, moet u deze optie gebruiken in combi natie met `PasswordPass` optie.</span><span class="sxs-lookup"><span data-stu-id="21596-193">If you want to pass a machine password, then you must use this option in combination with `PasswordPass` option.</span></span>

- <span data-ttu-id="21596-194">**PasswordPass** : het computer wachtwoord wordt ingesteld op de waarde van de para meter *Credential* (DomainCredential) nadat een niet-beveiligde samen voeging is uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="21596-194">**PasswordPass** : Sets the machine password to the value of the *Credential* (DomainCredential) parameter after performing an unsecured join.</span></span> <span data-ttu-id="21596-195">Deze optie geeft ook aan dat de waarde van de *referentie* -para meter (DomainCredential) een computer wachtwoord is, niet een gebruikers wachtwoord.</span><span class="sxs-lookup"><span data-stu-id="21596-195">This option also indicates that the value of the *Credential* (DomainCredential) parameter is a machine password, not a user password.</span></span> <span data-ttu-id="21596-196">Deze optie is alleen geldig als de `UnsecuredJoin` optie is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="21596-196">This option is valid only when the `UnsecuredJoin` option is specified.</span></span> <span data-ttu-id="21596-197">Wanneer u deze optie gebruikt, moet de referentie die aan de `-Credential` para meter is gegeven, een null-gebruikers naam hebben. *must*</span><span class="sxs-lookup"><span data-stu-id="21596-197">When using this option, the credential provided to the `-Credential` parameter *must* have a null username.</span></span>

- <span data-ttu-id="21596-198">**JoinWithNewName** : de naam van de computer naam in het nieuwe domein wordt gewijzigd in de naam die is opgegeven met de para meter *newname* .</span><span class="sxs-lookup"><span data-stu-id="21596-198">**JoinWithNewName** : Renames the computer name in the new domain to the name specified by the *NewName* parameter.</span></span> <span data-ttu-id="21596-199">Wanneer u de para meter *newname* gebruikt, wordt deze optie automatisch ingesteld.</span><span class="sxs-lookup"><span data-stu-id="21596-199">When you use the *NewName* parameter, this option is set automatically.</span></span> <span data-ttu-id="21596-200">Deze optie is ontworpen om te worden gebruikt met de cmdlet Rename-Computer.</span><span class="sxs-lookup"><span data-stu-id="21596-200">This option is designed to be used with the Rename-Computer cmdlet.</span></span> <span data-ttu-id="21596-201">Als u de naam van de computer wijzigt met de cmdlet **Rename-computer** , maar de computer niet opnieuw opstart om de wijziging van kracht te laten worden, kunt u deze para meter gebruiken om de computer toe te voegen aan een domein met de nieuwe naam.</span><span class="sxs-lookup"><span data-stu-id="21596-201">If you use the **Rename-Computer** cmdlet to rename the computer, but do not restart the computer to make the change effective, you can use this parameter to join the computer to a domain with its new name.</span></span>

- <span data-ttu-id="21596-202">**JoinReadOnly** : gebruikt een bestaand machine account om de computer toe te voegen aan een alleen-lezen domein controller.</span><span class="sxs-lookup"><span data-stu-id="21596-202">**JoinReadOnly** : Uses an existing machine account to join the computer to a read-only domain controller.</span></span> <span data-ttu-id="21596-203">Het computer account moet worden toegevoegd aan de lijst met toegestane accounts voor het beleid voor wachtwoord replicatie en het account wachtwoord moet worden gerepliceerd naar de alleen-lezen domein controller vóór de koppelings bewerking.</span><span class="sxs-lookup"><span data-stu-id="21596-203">The machine account must be added to the allowed list for password replication policy and the account password must be replicated to the read-only domain controller prior to the join operation.</span></span>

- <span data-ttu-id="21596-204">**InstallInvoke** : stelt de vlaggen Create (0x2) en Delete (0x4) van de para meter **FJoinOptions** van de methode **JoinDomainOrWorkgroup** in.</span><span class="sxs-lookup"><span data-stu-id="21596-204">**InstallInvoke** : Sets the create (0x2) and delete (0x4) flags of the **FJoinOptions** parameter of the **JoinDomainOrWorkgroup** method.</span></span> <span data-ttu-id="21596-205">Zie de [methode JoinDomainOrWorkgroup van de klasse Win32_ComputerSystem](/windows/win32/cimwin32prov/joindomainorworkgroup-method-in-class-win32-computersystem)voor meer informatie over de methode **JoinDomainOrWorkgroup** .</span><span class="sxs-lookup"><span data-stu-id="21596-205">For more information about the **JoinDomainOrWorkgroup** method, see [JoinDomainOrWorkgroup method of the Win32_ComputerSystem class](/windows/win32/cimwin32prov/joindomainorworkgroup-method-in-class-win32-computersystem).</span></span>
  <span data-ttu-id="21596-206">Zie de [functie NetJoinDomain](/windows/win32/api/lmjoin/nf-lmjoin-netjoindomain)voor meer informatie over deze opties.</span><span class="sxs-lookup"><span data-stu-id="21596-206">For more information about these options, see [NetJoinDomain function](/windows/win32/api/lmjoin/nf-lmjoin-netjoindomain).</span></span>

<span data-ttu-id="21596-207">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="21596-207">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.JoinOptions
Parameter Sets: Domain
Aliases:
Accepted values: AccountCreate, Win9XUpgrade, UnsecuredJoin, PasswordPass, DeferSPNSet, JoinWithNewName, JoinReadOnly, InstallInvoke

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="21596-208">-OUPath</span><span class="sxs-lookup"><span data-stu-id="21596-208">-OUPath</span></span>

<span data-ttu-id="21596-209">Hiermee geeft u een organisatie-eenheid (OE) voor het domein account op.</span><span class="sxs-lookup"><span data-stu-id="21596-209">Specifies an organizational unit (OU) for the domain account.</span></span> <span data-ttu-id="21596-210">Voer tussen aanhalings tekens de volledige DN-naam van de organisatie-eenheid in.</span><span class="sxs-lookup"><span data-stu-id="21596-210">Enter the full distinguished name of the OU in quotation marks.</span></span> <span data-ttu-id="21596-211">De standaard waarde is de standaard organisatie-eenheid voor computer objecten in het domein.</span><span class="sxs-lookup"><span data-stu-id="21596-211">The default value is the default OU for machine objects in the domain.</span></span>

```yaml
Type: System.String
Parameter Sets: Domain
Aliases: OU

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="21596-212">-PassThru</span><span class="sxs-lookup"><span data-stu-id="21596-212">-PassThru</span></span>

<span data-ttu-id="21596-213">Retourneert een object dat het item vertegenwoordigt waarmee u werkt.</span><span class="sxs-lookup"><span data-stu-id="21596-213">Returns an object representing the item with which you are working.</span></span> <span data-ttu-id="21596-214">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="21596-214">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="21596-215">-Restart</span><span class="sxs-lookup"><span data-stu-id="21596-215">-Restart</span></span>

<span data-ttu-id="21596-216">Hiermee worden de computers die zijn toegevoegd aan het domein of de werk groep opnieuw opgestart.</span><span class="sxs-lookup"><span data-stu-id="21596-216">Restarts the computers that were added to the domain or workgroup.</span></span> <span data-ttu-id="21596-217">Het is vaak nood zakelijk om opnieuw op te starten om de wijziging van kracht te laten worden.</span><span class="sxs-lookup"><span data-stu-id="21596-217">A restart is often required to make the change effective.</span></span>

<span data-ttu-id="21596-218">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="21596-218">This parameter is introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="21596-219">-Server</span><span class="sxs-lookup"><span data-stu-id="21596-219">-Server</span></span>

<span data-ttu-id="21596-220">Hiermee geeft u de naam van een domein controller die de computer aan het domein toevoegt.</span><span class="sxs-lookup"><span data-stu-id="21596-220">Specifies the name of a domain controller that adds the computer to the domain.</span></span> <span data-ttu-id="21596-221">Geef de naam op in de DomainName\ComputerName-indeling.</span><span class="sxs-lookup"><span data-stu-id="21596-221">Enter the name in DomainName\ComputerName format.</span></span> <span data-ttu-id="21596-222">Standaard is er geen domein controller opgegeven.</span><span class="sxs-lookup"><span data-stu-id="21596-222">By default, no domain controller is specified.</span></span>

```yaml
Type: System.String
Parameter Sets: Domain
Aliases: DC

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="21596-223">-UnjoinDomainCredential</span><span class="sxs-lookup"><span data-stu-id="21596-223">-UnjoinDomainCredential</span></span>

<span data-ttu-id="21596-224">Hiermee geeft u een gebruikers account op dat gemachtigd is om de computers uit hun huidige domeinen te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="21596-224">Specifies a user account that has permission to remove the computers from their current domains.</span></span> <span data-ttu-id="21596-225">Standaard is dit de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="21596-225">The default is the current user.</span></span>

<span data-ttu-id="21596-226">Typ een gebruikers naam, zoals "gebruiker01" of "Domain01\User01", of voer een **PSCredential** -object in, zoals het account dat is gegenereerd door de `Get-Credential` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="21596-226">Type a user name, such as "User01" or "Domain01\User01", or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="21596-227">Als u een gebruikers naam typt, wordt u gevraagd een wacht woord op te vragen.</span><span class="sxs-lookup"><span data-stu-id="21596-227">If you type a user name, you will be prompted for a password.</span></span>

<span data-ttu-id="21596-228">Gebruik deze para meter wanneer u computers verplaatst naar een ander domein.</span><span class="sxs-lookup"><span data-stu-id="21596-228">Use this parameter when you are moving computers to a different domain.</span></span> <span data-ttu-id="21596-229">Als u een gebruikers account wilt opgeven dat is gemachtigd om lid te worden van het nieuwe domein, gebruikt u de para meter **Credential** .</span><span class="sxs-lookup"><span data-stu-id="21596-229">To specify a user account that has permission to join the new domain, use the **Credential** parameter.</span></span> <span data-ttu-id="21596-230">Als u een gebruikers account wilt opgeven dat is gemachtigd om verbinding te maken met een externe computer, gebruikt u de para meter **LocalCredential** .</span><span class="sxs-lookup"><span data-stu-id="21596-230">To specify a user account that has permission to connect to a remote computer, use the **LocalCredential** parameter.</span></span>

<span data-ttu-id="21596-231">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="21596-231">This parameter is introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: Domain
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="21596-232">-Niet beveiligd</span><span class="sxs-lookup"><span data-stu-id="21596-232">-Unsecure</span></span>

<span data-ttu-id="21596-233">Hiermee wordt een niet-beveiligde koppeling naar het opgegeven domein uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="21596-233">Performs an unsecure join to the specified domain.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Domain
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="21596-234">-Werkgroepnaam</span><span class="sxs-lookup"><span data-stu-id="21596-234">-WorkgroupName</span></span>

<span data-ttu-id="21596-235">Hiermee geeft u de naam op van een werk groep waaraan de computers worden toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="21596-235">Specifies the name of a workgroup to which the computers are added.</span></span> <span data-ttu-id="21596-236">De standaard waarde is werk groep.</span><span class="sxs-lookup"><span data-stu-id="21596-236">The default value is "WORKGROUP".</span></span>

```yaml
Type: System.String
Parameter Sets: Workgroup
Aliases: WGN

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="21596-237">-Confirm</span><span class="sxs-lookup"><span data-stu-id="21596-237">-Confirm</span></span>

<span data-ttu-id="21596-238">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="21596-238">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="21596-239">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="21596-239">-WhatIf</span></span>

<span data-ttu-id="21596-240">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="21596-240">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="21596-241">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="21596-241">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="21596-242">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="21596-242">CommonParameters</span></span>

<span data-ttu-id="21596-243">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="21596-243">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="21596-244">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="21596-244">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="21596-245">INVOER</span><span class="sxs-lookup"><span data-stu-id="21596-245">INPUTS</span></span>

### <span data-ttu-id="21596-246">System. String</span><span class="sxs-lookup"><span data-stu-id="21596-246">System.String</span></span>

<span data-ttu-id="21596-247">U kunt computer namen en nieuwe namen door sluizen naar de `Add-Computer` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="21596-247">You can pipe computer names and new names to the `Add-Computer` Cmdlet.</span></span>

## <span data-ttu-id="21596-248">UITVOER</span><span class="sxs-lookup"><span data-stu-id="21596-248">OUTPUTS</span></span>

### <span data-ttu-id="21596-249">Micro soft. Power shell. commands. ComputerChangeInfo</span><span class="sxs-lookup"><span data-stu-id="21596-249">Microsoft.PowerShell.Commands.ComputerChangeInfo</span></span>

<span data-ttu-id="21596-250">Wanneer u de para meter **PassThru** gebruikt, `Add-Computer` wordt een **ComputerChangeInfo** -object geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="21596-250">When you use the **PassThru** parameter, `Add-Computer` returns a **ComputerChangeInfo** object.</span></span>
<span data-ttu-id="21596-251">Anders wordt met deze cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="21596-251">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="21596-252">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="21596-252">NOTES</span></span>

- <span data-ttu-id="21596-253">In Windows Power Shell 2,0 is de **Server** parameter van `Add-Computer` mislukt, zelfs als de server aanwezig is.</span><span class="sxs-lookup"><span data-stu-id="21596-253">In Windows PowerShell 2.0, the **Server** parameter of `Add-Computer` fails even when the server is present.</span></span> <span data-ttu-id="21596-254">In Windows Power Shell 3,0 is de implementatie van de **Server** parameter zodanig gewijzigd dat deze betrouwbaar werkt.</span><span class="sxs-lookup"><span data-stu-id="21596-254">In Windows PowerShell 3.0, the implementation of the **Server** parameter is changed so that it works reliably.</span></span>

## <span data-ttu-id="21596-255">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="21596-255">RELATED LINKS</span></span>

[<span data-ttu-id="21596-256">Checkpoint-Computer</span><span class="sxs-lookup"><span data-stu-id="21596-256">Checkpoint-Computer</span></span>](Checkpoint-Computer.md)

[<span data-ttu-id="21596-257">Verwijderen-computer</span><span class="sxs-lookup"><span data-stu-id="21596-257">Remove-Computer</span></span>](Remove-Computer.md)

[<span data-ttu-id="21596-258">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="21596-258">Restart-Computer</span></span>](Restart-Computer.md)

[<span data-ttu-id="21596-259">Naam wijzigen-computer</span><span class="sxs-lookup"><span data-stu-id="21596-259">Rename-Computer</span></span>](Rename-Computer.md)

[<span data-ttu-id="21596-260">Herstellen-computer</span><span class="sxs-lookup"><span data-stu-id="21596-260">Restore-Computer</span></span>](Restore-Computer.md)

[<span data-ttu-id="21596-261">Stop-computer</span><span class="sxs-lookup"><span data-stu-id="21596-261">Stop-Computer</span></span>](Stop-Computer.md)

[<span data-ttu-id="21596-262">Test-Connection</span><span class="sxs-lookup"><span data-stu-id="21596-262">Test-Connection</span></span>](Test-Connection.md)
