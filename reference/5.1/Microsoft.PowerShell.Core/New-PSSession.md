---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 12/20/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-pssession?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSSession
ms.openlocfilehash: 1835d0bd4294161f83728a63e8da8fc64c2bf9e0
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/23/2020
ms.locfileid: "93251481"
---
# <span data-ttu-id="40742-103">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="40742-103">New-PSSession</span></span>

## <span data-ttu-id="40742-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="40742-104">SYNOPSIS</span></span>
<span data-ttu-id="40742-105">Hiermee maakt u een permanente verbinding met een lokale of externe computer.</span><span class="sxs-lookup"><span data-stu-id="40742-105">Creates a persistent connection to a local or remote computer.</span></span>

## <span data-ttu-id="40742-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="40742-106">SYNTAX</span></span>

### <span data-ttu-id="40742-107">Computer naam (standaard)</span><span class="sxs-lookup"><span data-stu-id="40742-107">ComputerName (Default)</span></span>

```
New-PSSession [[-ComputerName] <String[]>] [-Credential <PSCredential>] [-Name <String[]>]
 [-EnableNetworkAccess] [-ConfigurationName <String>] [-Port <Int32>] [-UseSSL]
 [-ApplicationName <String>] [-ThrottleLimit <Int32>] [-SessionOption <PSSessionOption>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="40742-108">URI</span><span class="sxs-lookup"><span data-stu-id="40742-108">Uri</span></span>

```
New-PSSession [-Credential <PSCredential>] [-Name <String[]>] [-EnableNetworkAccess]
 [-ConfigurationName <String>] [-ThrottleLimit <Int32>] [-ConnectionUri] <Uri[]> [-AllowRedirection]
 [-SessionOption <PSSessionOption>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="40742-109">VMId</span><span class="sxs-lookup"><span data-stu-id="40742-109">VMId</span></span>

```
New-PSSession -Credential <PSCredential> [-Name <String[]>] [-ConfigurationName <String>]
 [-VMId] <Guid[]> [-ThrottleLimit <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="40742-110">VMName</span><span class="sxs-lookup"><span data-stu-id="40742-110">VMName</span></span>

```
New-PSSession -Credential <PSCredential> [-Name <String[]>] [-ConfigurationName <String>]
 -VMName <String[]> [-ThrottleLimit <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="40742-111">Sessie</span><span class="sxs-lookup"><span data-stu-id="40742-111">Session</span></span>

```
New-PSSession [[-Session] <PSSession[]>] [-Name <String[]>] [-EnableNetworkAccess]
 [-ThrottleLimit <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="40742-112">ContainerId</span><span class="sxs-lookup"><span data-stu-id="40742-112">ContainerId</span></span>

```
New-PSSession [-Name <String[]>] [-ConfigurationName <String>] -ContainerId <String[]>
 [-RunAsAdministrator] [-ThrottleLimit <Int32>] [<CommonParameters>]
```

## <span data-ttu-id="40742-113">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="40742-113">DESCRIPTION</span></span>

<span data-ttu-id="40742-114">`New-PSSession`Met de cmdlet maakt u een Power shell-sessie ( **PSSession** ) op een lokale of externe computer.</span><span class="sxs-lookup"><span data-stu-id="40742-114">The `New-PSSession` cmdlet creates a PowerShell session ( **PSSession** ) on a local or remote computer.</span></span> <span data-ttu-id="40742-115">Wanneer u een **PSSession** maakt, brengt Power shell een permanente verbinding met de externe computer tot stand.</span><span class="sxs-lookup"><span data-stu-id="40742-115">When you create a **PSSession** , PowerShell establishes a persistent connection to the remote computer.</span></span>

<span data-ttu-id="40742-116">Gebruik een **PSSession** om meerdere opdrachten uit te voeren die gegevens delen, zoals een functie of de waarde van een variabele.</span><span class="sxs-lookup"><span data-stu-id="40742-116">Use a **PSSession** to run multiple commands that share data, such as a function or the value of a variable.</span></span> <span data-ttu-id="40742-117">Gebruik de cmdlet om opdrachten uit te voeren in een **PSSession** `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="40742-117">To run commands in a **PSSession** , use the `Invoke-Command` cmdlet.</span></span> <span data-ttu-id="40742-118">Als u de **PSSession** wilt gebruiken om rechtstreeks te communiceren met een externe computer, gebruikt u de `Enter-PSSession` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="40742-118">To use the **PSSession** to interact directly with a remote computer, use the `Enter-PSSession` cmdlet.</span></span> <span data-ttu-id="40742-119">Zie [about_PSSessions](about/about_PSSessions.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="40742-119">For more information, see [about_PSSessions](about/about_PSSessions.md).</span></span>

<span data-ttu-id="40742-120">U kunt opdrachten uitvoeren op een externe computer zonder een **PSSession** te maken met behulp van de **ComputerName** -para meters van `Enter-PSSession` of `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="40742-120">You can run commands on a remote computer without creating a **PSSession** by using the **ComputerName** parameters of `Enter-PSSession` or `Invoke-Command`.</span></span> <span data-ttu-id="40742-121">Wanneer u de para meter **ComputerName** gebruikt, maakt Power shell een tijdelijke verbinding die wordt gebruikt voor de opdracht en vervolgens gesloten.</span><span class="sxs-lookup"><span data-stu-id="40742-121">When you use the **ComputerName** parameter, PowerShell creates a temporary connection that is used for the command and is then closed.</span></span>

## <span data-ttu-id="40742-122">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="40742-122">EXAMPLES</span></span>

### <span data-ttu-id="40742-123">Voor beeld 1: een sessie op de lokale computer maken</span><span class="sxs-lookup"><span data-stu-id="40742-123">Example 1: Create a session on the local computer</span></span>

```powershell
$s = New-PSSession
```

<span data-ttu-id="40742-124">Met deze opdracht maakt u een nieuwe **PSSession** op de lokale computer en slaat de **PSSession** op in de `$s` variabele.</span><span class="sxs-lookup"><span data-stu-id="40742-124">This command creates a new **PSSession** on the local computer and saves the **PSSession** in the `$s` variable.</span></span>

<span data-ttu-id="40742-125">U kunt deze **PSSession** nu gebruiken om opdrachten uit te voeren op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="40742-125">You can now use this **PSSession** to run commands on the local computer.</span></span>

### <span data-ttu-id="40742-126">Voor beeld 2: een sessie op een externe computer maken</span><span class="sxs-lookup"><span data-stu-id="40742-126">Example 2: Create a session on a remote computer</span></span>

```powershell
$Server01 = New-PSSession -ComputerName Server01
```

<span data-ttu-id="40742-127">Met deze opdracht maakt u een nieuwe **PSSession** op de Server01-computer en slaat deze op in de `$Server01` variabele.</span><span class="sxs-lookup"><span data-stu-id="40742-127">This command creates a new **PSSession** on the Server01 computer and saves it in the `$Server01` variable.</span></span>

<span data-ttu-id="40742-128">Wanneer u meerdere **PSSession** -objecten maakt, moet u deze toewijzen aan variabelen met nuttige namen.</span><span class="sxs-lookup"><span data-stu-id="40742-128">When creating multiple **PSSession** objects, assign them to variables with useful names.</span></span> <span data-ttu-id="40742-129">Dit helpt u bij het beheren van de **PSSession** -objecten in volgende opdrachten.</span><span class="sxs-lookup"><span data-stu-id="40742-129">This will help you manage the **PSSession** objects in subsequent commands.</span></span>

### <span data-ttu-id="40742-130">Voor beeld 3: sessies op meerdere computers maken</span><span class="sxs-lookup"><span data-stu-id="40742-130">Example 3: Create sessions on multiple computers</span></span>

```powershell
$s1, $s2, $s3 = New-PSSession -ComputerName Server01,Server02,Server03
```

<span data-ttu-id="40742-131">Met deze opdracht worden drie **PSSession** -objecten gemaakt, één op elke computer die is opgegeven door de para meter **ComputerName** .</span><span class="sxs-lookup"><span data-stu-id="40742-131">This command creates three **PSSession** objects, one on each of the computers specified by the **ComputerName** parameter.</span></span>

<span data-ttu-id="40742-132">De opdracht gebruikt de toewijzings operator (=) om de nieuwe **PSSession** -objecten toe te wijzen aan variabelen: `$s1` , `$s2` , `$s3` .</span><span class="sxs-lookup"><span data-stu-id="40742-132">The command uses the assignment operator (=) to assign the new **PSSession** objects to variables: `$s1`, `$s2`, `$s3`.</span></span> <span data-ttu-id="40742-133">De Server01 **PSSession** wordt toegewezen aan `$s1` , de Server02 **PSSession** aan `$s2` en de Server03 **PSSession** tot `$s3` .</span><span class="sxs-lookup"><span data-stu-id="40742-133">It assigns the Server01 **PSSession** to `$s1`, the Server02 **PSSession** to `$s2`, and the Server03 **PSSession** to `$s3`.</span></span>

<span data-ttu-id="40742-134">Wanneer u meerdere objecten toewijst aan een reeks variabelen, wijst Power shell elk object toe aan een variabele in de reeks.</span><span class="sxs-lookup"><span data-stu-id="40742-134">When you assign multiple objects to a series of variables, PowerShell assigns each object to a variable in the series respectively.</span></span> <span data-ttu-id="40742-135">Als er meer objecten zijn dan variabelen, worden alle resterende objecten toegewezen aan de laatste variabele.</span><span class="sxs-lookup"><span data-stu-id="40742-135">If there are more objects than variables, all remaining objects are assigned to the last variable.</span></span> <span data-ttu-id="40742-136">Als er meer variabelen zijn dan objecten, zijn de resterende variabelen leeg (null).</span><span class="sxs-lookup"><span data-stu-id="40742-136">If there are more variables than objects, the remaining variables are empty (null).</span></span>

### <span data-ttu-id="40742-137">Voor beeld 4: een sessie met een opgegeven poort maken</span><span class="sxs-lookup"><span data-stu-id="40742-137">Example 4: Create a session with a specified port</span></span>

```powershell
New-PSSession -ComputerName Server01 -Port 8081 -UseSSL -ConfigurationName E12
```

<span data-ttu-id="40742-138">Met deze opdracht maakt u een nieuwe **PSSession** op de Server01-computer die verbinding maakt met server poort 8081 en gebruikmaakt van het SSL-protocol.</span><span class="sxs-lookup"><span data-stu-id="40742-138">This command creates a new **PSSession** on the Server01 computer that connects to server port 8081 and uses the SSL protocol.</span></span> <span data-ttu-id="40742-139">De nieuwe **PSSession** gebruikt een alternatieve sessie configuratie met de naam E12.</span><span class="sxs-lookup"><span data-stu-id="40742-139">The new **PSSession** uses an alternative session configuration called E12.</span></span>

<span data-ttu-id="40742-140">Voordat u de poort instelt, moet u de WinRM-listener op de externe computer configureren om te Luis teren op poort 8081.</span><span class="sxs-lookup"><span data-stu-id="40742-140">Before setting the port, you must configure the WinRM listener on the remote computer to listen on port 8081.</span></span> <span data-ttu-id="40742-141">Zie de beschrijving van de **poort** parameter voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="40742-141">For more information, see the description of the **Port** parameter.</span></span>

### <span data-ttu-id="40742-142">Voor beeld 5: een sessie maken op basis van een bestaande sessie</span><span class="sxs-lookup"><span data-stu-id="40742-142">Example 5: Create a session based on an existing session</span></span>

```powershell
New-PSSession -Session $s -Credential Domain01\User01
```

<span data-ttu-id="40742-143">Met deze opdracht maakt u een **PSSession** met dezelfde eigenschappen als een bestaande **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="40742-143">This command creates a **PSSession** with the same properties as an existing **PSSession**.</span></span> <span data-ttu-id="40742-144">U kunt deze opdracht indeling gebruiken wanneer de resources van een bestaand **PSSession** uitgeput zijn en er een nieuwe **PSSession** nodig is om een deel van de vraag te offloaden.</span><span class="sxs-lookup"><span data-stu-id="40742-144">You can use this command format when the resources of an existing **PSSession** are exhausted and a new **PSSession** is needed to offload some of the demand.</span></span>

<span data-ttu-id="40742-145">De opdracht gebruikt de **sessie** parameter van `New-PSSession` om de **PSSession** op te geven die is opgeslagen in de `$s` variabele.</span><span class="sxs-lookup"><span data-stu-id="40742-145">The command uses the **Session** parameter of `New-PSSession` to specify the **PSSession** saved in the `$s` variable.</span></span> <span data-ttu-id="40742-146">Het gebruikt de referenties van de Domain1\Admin01-gebruiker om de opdracht te volt ooien.</span><span class="sxs-lookup"><span data-stu-id="40742-146">It uses the credentials of the Domain1\Admin01 user to complete the command.</span></span>

### <span data-ttu-id="40742-147">Voor beeld 6: een sessie met een globaal bereik in een ander domein maken</span><span class="sxs-lookup"><span data-stu-id="40742-147">Example 6: Create a session with a global scope in a different domain</span></span>

```powershell
$global:s = New-PSSession -ComputerName Server1.Domain44.Corpnet.Fabrikam.com -Credential Domain01\Admin01
```

<span data-ttu-id="40742-148">In dit voor beeld ziet u hoe u een **PSSession** maakt met een globaal bereik op een computer in een ander domein.</span><span class="sxs-lookup"><span data-stu-id="40742-148">This example shows how to create a **PSSession** with a global scope on a computer in a different domain.</span></span>

<span data-ttu-id="40742-149">**PSSession** -objecten die zijn gemaakt op de opdracht regel, worden standaard gemaakt met een lokale scope en **PSSession** -objecten die zijn gemaakt in een script, hebben een script bereik.</span><span class="sxs-lookup"><span data-stu-id="40742-149">By default, **PSSession** objects created at the command line are created with local scope and **PSSession** objects created in a script have script scope.</span></span>

<span data-ttu-id="40742-150">Als u een **PSSession** met een globaal bereik wilt maken, maakt u een nieuwe **PSSession** en slaat u vervolgens de **PSSession** op in een variabele die wordt geconverteerd naar een globaal bereik.</span><span class="sxs-lookup"><span data-stu-id="40742-150">To create a **PSSession** with global scope, create a new **PSSession** and then store the **PSSession** in a variable that is cast to a global scope.</span></span> <span data-ttu-id="40742-151">In dit geval wordt de `$s` variabele geconverteerd naar een globaal bereik.</span><span class="sxs-lookup"><span data-stu-id="40742-151">In this case, the `$s` variable is cast to a global scope.</span></span>

<span data-ttu-id="40742-152">De opdracht gebruikt de para meter **ComputerName** om de externe computer op te geven.</span><span class="sxs-lookup"><span data-stu-id="40742-152">The command uses the **ComputerName** parameter to specify the remote computer.</span></span> <span data-ttu-id="40742-153">Omdat de computer zich in een ander domein bevindt dan het gebruikers account, wordt de volledige naam van de computer opgegeven samen met de referenties van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="40742-153">Because the computer is in a different domain than the user account, the full name of the computer is specified together with the credentials of the user.</span></span>

### <span data-ttu-id="40742-154">Voor beeld 7: sessies maken voor veel computers</span><span class="sxs-lookup"><span data-stu-id="40742-154">Example 7: Create sessions for many computers</span></span>

```powershell
$rs = Get-Content C:\Test\Servers.txt | New-PSSession -ThrottleLimit 50
```

<span data-ttu-id="40742-155">Met deze opdracht maakt u een **PSSession** op elk van de 200-computers die worden vermeld in het Servers.txt-bestand en wordt de resulterende **PSSession** in de `$rs` variabele opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="40742-155">This command creates a **PSSession** on each of the 200 computers listed in the Servers.txt file and it stores the resulting **PSSession** in the `$rs` variable.</span></span> <span data-ttu-id="40742-156">De **PSSession** -objecten hebben een beperkings limiet van 50.</span><span class="sxs-lookup"><span data-stu-id="40742-156">The **PSSession** objects have a throttle limit of 50.</span></span>

<span data-ttu-id="40742-157">U kunt deze opdracht indeling gebruiken wanneer de namen van computers worden opgeslagen in een Data Base, een werk blad, een tekst bestand of een andere Converteer bare tekst indeling.</span><span class="sxs-lookup"><span data-stu-id="40742-157">You can use this command format when the names of computers are stored in a database, spreadsheet, text file, or other text-convertible format.</span></span>

### <span data-ttu-id="40742-158">Voor beeld 8: een sessie maken met behulp van een URI</span><span class="sxs-lookup"><span data-stu-id="40742-158">Example 8: Create a session by using a URI</span></span>

```powershell
$s = New-PSSession -URI http://Server01:91/NewSession -Credential Domain01\User01
```

<span data-ttu-id="40742-159">Met deze opdracht maakt u een **PSSession** op de Server01-computer en slaat u deze op in de `$s` variabele.</span><span class="sxs-lookup"><span data-stu-id="40742-159">This command creates a **PSSession** on the Server01 computer and stores it in the `$s` variable.</span></span> <span data-ttu-id="40742-160">De para meter **URI** wordt gebruikt om het transport protocol, de externe computer, de poort en een alternatieve sessie configuratie op te geven.</span><span class="sxs-lookup"><span data-stu-id="40742-160">It uses the **URI** parameter to specify the transport protocol, the remote computer, the port, and an alternate session configuration.</span></span> <span data-ttu-id="40742-161">Ook wordt de para meter **Credential** gebruikt om een gebruikers account op te geven dat gemachtigd is om een sessie te maken op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="40742-161">It also uses the **Credential** parameter to specify a user account that has permission to create a session on the remote computer.</span></span>

### <span data-ttu-id="40742-162">Voor beeld 9: een achtergrond taak uitvoeren in een reeks sessies</span><span class="sxs-lookup"><span data-stu-id="40742-162">Example 9: Run a background job in a set of sessions</span></span>

```powershell
$s = New-PSSession -ComputerName (Get-Content Servers.txt) -Credential Domain01\Admin01 -ThrottleLimit 16
Invoke-Command -Session $s -ScriptBlock {Get-Process PowerShell} -AsJob
```

<span data-ttu-id="40742-163">Met deze opdrachten maakt u een set **PSSession** -objecten en voert u vervolgens een achtergrond taak uit in elk van de **PSSession** -objecten.</span><span class="sxs-lookup"><span data-stu-id="40742-163">These commands create a set of **PSSession** objects and then run a background job in each of the **PSSession** objects.</span></span>

<span data-ttu-id="40742-164">Met de eerste opdracht maakt u een nieuwe **PSSession** op elke computer die wordt vermeld in het Servers.txt-bestand.</span><span class="sxs-lookup"><span data-stu-id="40742-164">The first command creates a new **PSSession** on each of the computers listed in the Servers.txt file.</span></span> <span data-ttu-id="40742-165">De cmdlet wordt gebruikt `New-PSSession` om de **PSSession** te maken.</span><span class="sxs-lookup"><span data-stu-id="40742-165">It uses the `New-PSSession` cmdlet to create the **PSSession**.</span></span> <span data-ttu-id="40742-166">De waarde van de para meter **ComputerName** is een opdracht die gebruikmaakt `Get-Content` van de cmdlet om de lijst met computer namen op te halen in het Servers.txt-bestand.</span><span class="sxs-lookup"><span data-stu-id="40742-166">The value of the **ComputerName** parameter is a command that uses the `Get-Content` cmdlet to get the list of computer names the Servers.txt file.</span></span>

<span data-ttu-id="40742-167">De opdracht gebruikt de para meter **Credential** om de **PSSession** -objecten te maken die de machtiging van een domein beheerder hebben en de para meter **ThrottleLimit** wordt gebruikt om de opdracht te beperken tot 16 gelijktijdige verbindingen.</span><span class="sxs-lookup"><span data-stu-id="40742-167">The command uses the **Credential** parameter to create the **PSSession** objects that have the permission of a domain administrator, and it uses the **ThrottleLimit** parameter to limit the command to 16 concurrent connections.</span></span> <span data-ttu-id="40742-168">Met de opdracht worden de **PSSession** -objecten in de `$s` variabele opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="40742-168">The command saves the **PSSession** objects in the `$s` variable.</span></span>

<span data-ttu-id="40742-169">De tweede opdracht maakt gebruik van de para meter **AsJob** van de `Invoke-Command` cmdlet om een achtergrond taak te starten die een `Get-Process PowerShell` opdracht uitvoert in elk van de **PSSession** -objecten in `$s` .</span><span class="sxs-lookup"><span data-stu-id="40742-169">The second command uses the **AsJob** parameter of the `Invoke-Command` cmdlet to start a background job that runs a `Get-Process PowerShell` command in each of the **PSSession** objects in `$s`.</span></span>

<span data-ttu-id="40742-170">Zie [about_Jobs](About/about_Jobs.md) en [about_Remote_Jobs](About/about_Remote_Jobs.md)voor meer informatie over Power shell-achtergrond taken.</span><span class="sxs-lookup"><span data-stu-id="40742-170">For more information about PowerShell background jobs, see [about_Jobs](About/about_Jobs.md) and [about_Remote_Jobs](About/about_Remote_Jobs.md).</span></span>

### <span data-ttu-id="40742-171">Voor beeld 10: een sessie maken voor een computer met behulp van de bijbehorende URI</span><span class="sxs-lookup"><span data-stu-id="40742-171">Example 10: Create a session for a computer by using its URI</span></span>

```powershell
New-PSSession -ConnectionURI https://management.exchangelabs.com/Management
```

<span data-ttu-id="40742-172">Met deze opdracht maakt u een **PSSession** -object dat verbinding maakt met een computer die is opgegeven met een URI in plaats van een computer naam.</span><span class="sxs-lookup"><span data-stu-id="40742-172">This command creates a **PSSession** objects that connects to a computer that is specified by a URI instead of a computer name.</span></span>

### <span data-ttu-id="40742-173">Voor beeld 11: een sessie optie maken</span><span class="sxs-lookup"><span data-stu-id="40742-173">Example 11: Create a session option</span></span>

```powershell
$so = New-PSSessionOption -SkipCACheck
New-PSSession -ConnectionUri https://management.exchangelabs.com/Management -SessionOption $so -Credential Server01\Admin01
```

<span data-ttu-id="40742-174">In dit voor beeld ziet u hoe u een sessie optie object maakt en hoe u de para meter **SessionOption** .</span><span class="sxs-lookup"><span data-stu-id="40742-174">This example shows how to create a session option object and use the **SessionOption** parameter.</span></span>

<span data-ttu-id="40742-175">De eerste opdracht gebruikt de `New-PSSessionOption` cmdlet om een sessie optie te maken.</span><span class="sxs-lookup"><span data-stu-id="40742-175">The first command uses the `New-PSSessionOption` cmdlet to create a session option.</span></span> <span data-ttu-id="40742-176">Hiermee wordt het resulterende **SessionOption** -object in de `$so` variabele opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="40742-176">It saves the resulting **SessionOption** object in the `$so` variable.</span></span>

<span data-ttu-id="40742-177">Met de tweede opdracht wordt de optie in een nieuwe sessie gebruikt.</span><span class="sxs-lookup"><span data-stu-id="40742-177">The second command uses the option in a new session.</span></span> <span data-ttu-id="40742-178">De opdracht gebruikt de `New-PSSession` cmdlet om een nieuwe sessie te maken.</span><span class="sxs-lookup"><span data-stu-id="40742-178">The command uses the `New-PSSession` cmdlet to create a new session.</span></span> <span data-ttu-id="40742-179">De waarde van de para meter SessionOption is het object **SessionOption** in de `$so` variabele.</span><span class="sxs-lookup"><span data-stu-id="40742-179">The value of the SessionOption parameter is the **SessionOption** object in the `$so` variable.</span></span>

## <span data-ttu-id="40742-180">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="40742-180">PARAMETERS</span></span>

### <span data-ttu-id="40742-181">-AllowRedirection</span><span class="sxs-lookup"><span data-stu-id="40742-181">-AllowRedirection</span></span>

<span data-ttu-id="40742-182">Geeft aan dat deze cmdlet omleiding van deze verbinding met een alternatieve URI (Uniform Resource Identifier) mogelijk maakt.</span><span class="sxs-lookup"><span data-stu-id="40742-182">Indicates that this cmdlet allows redirection of this connection to an alternate Uniform Resource Identifier (URI).</span></span>

<span data-ttu-id="40742-183">Wanneer u de para meter **ConnectionURI** gebruikt, kan de externe bestemming een instructie retour neren die wordt omgeleid naar een andere URI.</span><span class="sxs-lookup"><span data-stu-id="40742-183">When you use the **ConnectionURI** parameter, the remote destination can return an instruction to redirect to a different URI.</span></span> <span data-ttu-id="40742-184">Standaard worden verbindingen niet door Power shell omgeleid, maar u kunt deze para meter gebruiken om de verbinding te omleiden.</span><span class="sxs-lookup"><span data-stu-id="40742-184">By default, PowerShell does not redirect connections, but you can use this parameter to enable it to redirect the connection.</span></span>

<span data-ttu-id="40742-185">U kunt ook het aantal keren beperken dat de verbinding wordt omgeleid door de waarde van de **MaximumConnectionRedirectionCount** -sessie optie te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="40742-185">You can also limit the number of times the connection is redirected by changing the **MaximumConnectionRedirectionCount** session option value.</span></span> <span data-ttu-id="40742-186">Gebruik de para meter **MaximumRedirection** van de `New-PSSessionOption` cmdlet of stel de eigenschap **MaximumConnectionRedirectionCount** van de voorkeurs variabele **$PSSessionOption** in.</span><span class="sxs-lookup"><span data-stu-id="40742-186">Use the **MaximumRedirection** parameter of the `New-PSSessionOption` cmdlet or set the **MaximumConnectionRedirectionCount** property of the **$PSSessionOption** preference variable.</span></span> <span data-ttu-id="40742-187">De standaard waarde is 5.</span><span class="sxs-lookup"><span data-stu-id="40742-187">The default value is 5.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Uri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="40742-188">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="40742-188">-ApplicationName</span></span>

<span data-ttu-id="40742-189">Hiermee geeft u het segment van de toepassings naam van de verbindings-URI op.</span><span class="sxs-lookup"><span data-stu-id="40742-189">Specifies the application name segment of the connection URI.</span></span> <span data-ttu-id="40742-190">Gebruik deze para meter om de naam van de toepassing op te geven wanneer u de para meter **ConnectionURI** niet gebruikt in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="40742-190">Use this parameter to specify the application name when you are not using the **ConnectionURI** parameter in the command.</span></span>

<span data-ttu-id="40742-191">De standaard waarde is de waarde van de `$PSSessionApplicationName` Voorkeurs variabele op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="40742-191">The default value is the value of the `$PSSessionApplicationName` preference variable on the local computer.</span></span> <span data-ttu-id="40742-192">Als deze voorkeurs variabele niet is gedefinieerd, is de standaard waarde WSMAN.</span><span class="sxs-lookup"><span data-stu-id="40742-192">If this preference variable is not defined, the default value is WSMAN.</span></span> <span data-ttu-id="40742-193">Deze waarde is geschikt voor de meeste toepassingen.</span><span class="sxs-lookup"><span data-stu-id="40742-193">This value is appropriate for most uses.</span></span> <span data-ttu-id="40742-194">Zie [about_Preference_Variables](About/about_Preference_Variables.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="40742-194">For more information, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="40742-195">De WinRM-service gebruikt de naam van de toepassing om een listener te selecteren om de verbindings aanvraag te onderhouden.</span><span class="sxs-lookup"><span data-stu-id="40742-195">The WinRM service uses the application name to select a listener to service the connection request.</span></span>
<span data-ttu-id="40742-196">De waarde van deze para meter moet overeenkomen met de waarde van de eigenschap **URLPrefix** van een listener op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="40742-196">The value of this parameter should match the value of the **URLPrefix** property of a listener on the remote computer.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="40742-197">-Verificatie</span><span class="sxs-lookup"><span data-stu-id="40742-197">-Authentication</span></span>

<span data-ttu-id="40742-198">Hiermee geeft u het mechanisme op dat wordt gebruikt om de referenties van de gebruiker te verifiëren.</span><span class="sxs-lookup"><span data-stu-id="40742-198">Specifies the mechanism that is used to authenticate the user's credentials.</span></span>
<span data-ttu-id="40742-199">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="40742-199">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="40742-200">Standaard</span><span class="sxs-lookup"><span data-stu-id="40742-200">Default</span></span>
- <span data-ttu-id="40742-201">Basic</span><span class="sxs-lookup"><span data-stu-id="40742-201">Basic</span></span>
- <span data-ttu-id="40742-202">CredSSP</span><span class="sxs-lookup"><span data-stu-id="40742-202">Credssp</span></span>
- <span data-ttu-id="40742-203">Samenvatting</span><span class="sxs-lookup"><span data-stu-id="40742-203">Digest</span></span>
- <span data-ttu-id="40742-204">Kerberos</span><span class="sxs-lookup"><span data-stu-id="40742-204">Kerberos</span></span>
- <span data-ttu-id="40742-205">Negotiate</span><span class="sxs-lookup"><span data-stu-id="40742-205">Negotiate</span></span>
- <span data-ttu-id="40742-206">NegotiateWithImplicitCredential</span><span class="sxs-lookup"><span data-stu-id="40742-206">NegotiateWithImplicitCredential</span></span>

<span data-ttu-id="40742-207">De standaard waarde is standaard.</span><span class="sxs-lookup"><span data-stu-id="40742-207">The default value is Default.</span></span>

<span data-ttu-id="40742-208">Zie [AuthenticationMechanism Enumeration (Engelstalig)](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)voor meer informatie over de waarden van deze para meter.</span><span class="sxs-lookup"><span data-stu-id="40742-208">For more information about the values of this parameter, see [AuthenticationMechanism Enumeration](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!CAUTION]
> <span data-ttu-id="40742-209">CredSSP-verificatie (Credential Security Support Provider), waarbij de gebruikers referenties worden door gegeven aan een externe computer die moet worden geverifieerd, is ontworpen voor opdrachten waarvoor verificatie is vereist voor meer dan één bron, zoals het openen van een externe netwerk share.</span><span class="sxs-lookup"><span data-stu-id="40742-209">Credential Security Support Provider (CredSSP) authentication, in which the user credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="40742-210">Dit mechanisme verhoogt het beveiligings risico van de externe bewerking.</span><span class="sxs-lookup"><span data-stu-id="40742-210">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="40742-211">Als er is geknoeid met de externe computer, kunnen de referenties die aan worden door gegeven, worden gebruikt om de netwerk sessie te beheren.</span><span class="sxs-lookup"><span data-stu-id="40742-211">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerName, Uri
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="40742-212">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="40742-212">-CertificateThumbprint</span></span>

<span data-ttu-id="40742-213">Hiermee geeft u het digitale open bare-sleutel certificaat (x509) op van een gebruikers account dat is gemachtigd om deze actie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="40742-213">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span> <span data-ttu-id="40742-214">Voer de vinger afdruk van het certificaat in.</span><span class="sxs-lookup"><span data-stu-id="40742-214">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="40742-215">Certificaten worden gebruikt in authenticatie op basis van client certificaten.</span><span class="sxs-lookup"><span data-stu-id="40742-215">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="40742-216">Ze kunnen alleen worden toegewezen aan lokale gebruikers accounts. ze werken niet met domein accounts.</span><span class="sxs-lookup"><span data-stu-id="40742-216">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="40742-217">Als u een certificaat wilt ophalen, gebruikt u de `Get-Item` of- `Get-ChildItem` opdracht in het Power shell-certificaat: station.</span><span class="sxs-lookup"><span data-stu-id="40742-217">To get a certificate, use the `Get-Item` or `Get-ChildItem` command in the PowerShell Cert: drive.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName, Uri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="40742-218">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="40742-218">-ComputerName</span></span>

<span data-ttu-id="40742-219">Hiermee geeft u een matrix met namen van computers op.</span><span class="sxs-lookup"><span data-stu-id="40742-219">Specifies an array of names of computers.</span></span> <span data-ttu-id="40742-220">Met deze cmdlet wordt een permanente verbinding ( **PSSession** ) gemaakt met de opgegeven computer.</span><span class="sxs-lookup"><span data-stu-id="40742-220">This cmdlet creates a persistent connection ( **PSSession** ) to the specified computer.</span></span> <span data-ttu-id="40742-221">Als u meerdere computer namen opgeeft, `New-PSSession` maakt meerdere **PSSession** -objecten, één voor elke computer.</span><span class="sxs-lookup"><span data-stu-id="40742-221">If you enter multiple computer names, `New-PSSession` creates multiple **PSSession** objects, one for each computer.</span></span> <span data-ttu-id="40742-222">Standaard is dit de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="40742-222">The default is the local computer.</span></span>

<span data-ttu-id="40742-223">Typ de NetBIOS-naam, een IP-adres of een Fully Qualified Domain Name van een of meer externe computers.</span><span class="sxs-lookup"><span data-stu-id="40742-223">Type the NetBIOS name, an IP address, or a fully qualified domain name of one or more remote computers.</span></span> <span data-ttu-id="40742-224">Typ de computer naam, localhost of een punt (.) om de lokale computer op te geven.</span><span class="sxs-lookup"><span data-stu-id="40742-224">To specify the local computer, type the computer name, localhost, or a dot (.).</span></span> <span data-ttu-id="40742-225">Wanneer de computer zich in een ander domein bevindt dan de gebruiker, is de Fully Qualified Domain Name vereist.</span><span class="sxs-lookup"><span data-stu-id="40742-225">When the computer is in a different domain than the user, the fully qualified domain name is required.</span></span> <span data-ttu-id="40742-226">U kunt ook een computer naam (tussen aanhalings tekens) door sluizen naar `New-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="40742-226">You can also pipe a computer name, in quotation marks, to `New-PSSession`.</span></span>

<span data-ttu-id="40742-227">Als u een IP-adres wilt gebruiken in de waarde van de para meter **ComputerName** , moet de opdracht de para meter **Credential** bevatten.</span><span class="sxs-lookup"><span data-stu-id="40742-227">To use an IP address in the value of the **ComputerName** parameter, the command must include the **Credential** parameter.</span></span> <span data-ttu-id="40742-228">De computer moet ook worden geconfigureerd voor HTTPS-Trans Port of het IP-adres van de externe computer moet worden opgenomen in de WinRM TrustedHosts-lijst op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="40742-228">Also, the computer must be configured for HTTPS transport or the IP address of the remote computer must be included in the WinRM TrustedHosts list on the local computer.</span></span> <span data-ttu-id="40742-229">Zie "een computer toevoegen aan de lijst met vertrouwde hosts" in [about_Remote_Troubleshooting](about/about_Remote_Troubleshooting.md)voor instructies voor het toevoegen van een computer naam aan de lijst TrustedHosts.</span><span class="sxs-lookup"><span data-stu-id="40742-229">For instructions for adding a computer name to the TrustedHosts list, see "How to Add a Computer to the Trusted Host List" in [about_Remote_Troubleshooting](about/about_Remote_Troubleshooting.md).</span></span>

<span data-ttu-id="40742-230">Als u de lokale computer in de waarde van de para meter **ComputerName** wilt gebruiken, start u Windows Power shell met de optie als administrator uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="40742-230">To include the local computer in the value of the **ComputerName** parameter, start Windows PowerShell by using the Run as administrator option.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerName
Aliases: Cn

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="40742-231">-Configuratiepad</span><span class="sxs-lookup"><span data-stu-id="40742-231">-ConfigurationName</span></span>

<span data-ttu-id="40742-232">Hiermee geeft u de sessie configuratie op die wordt gebruikt voor de nieuwe **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="40742-232">Specifies the session configuration that is used for the new **PSSession**.</span></span>

<span data-ttu-id="40742-233">Voer een configuratie naam of de volledig gekwalificeerde resource-URI in voor een sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="40742-233">Enter a configuration name or the fully qualified resource URI for a session configuration.</span></span> <span data-ttu-id="40742-234">Als u alleen de configuratie naam opgeeft, wordt de volgende schema-URI voor voegsel: `http://schemas.microsoft.com/PowerShell` .</span><span class="sxs-lookup"><span data-stu-id="40742-234">If you specify only the configuration name, the following schema URI is prepended: `http://schemas.microsoft.com/PowerShell`.</span></span>

<span data-ttu-id="40742-235">De sessie configuratie voor een sessie bevindt zich op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="40742-235">The session configuration for a session is located on the remote computer.</span></span> <span data-ttu-id="40742-236">Als de opgegeven sessie configuratie niet bestaat op de externe computer, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="40742-236">If the specified session configuration does not exist on the remote computer, the command fails.</span></span>

<span data-ttu-id="40742-237">De standaard waarde is de waarde van de `$PSSessionConfigurationName` Voorkeurs variabele op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="40742-237">The default value is the value of the `$PSSessionConfigurationName` preference variable on the local computer.</span></span> <span data-ttu-id="40742-238">Als deze voorkeurs variabele niet is ingesteld, is de standaard instelling micro soft. Power shell.</span><span class="sxs-lookup"><span data-stu-id="40742-238">If this preference variable is not set, the default is Microsoft.PowerShell.</span></span> <span data-ttu-id="40742-239">Zie [about_Preference_Variables](About/about_Preference_Variables.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="40742-239">For more information, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName, Uri, VMId, VMName, ContainerId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="40742-240">-ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="40742-240">-ConnectionUri</span></span>

<span data-ttu-id="40742-241">Hiermee geeft u een URI op die het verbindings eindpunt voor de sessie definieert.</span><span class="sxs-lookup"><span data-stu-id="40742-241">Specifies a URI that defines the connection endpoint for the session.</span></span> <span data-ttu-id="40742-242">De URI moet volledig gekwalificeerd zijn.</span><span class="sxs-lookup"><span data-stu-id="40742-242">The URI must be fully qualified.</span></span> <span data-ttu-id="40742-243">De indeling van deze teken reeks is als volgt:</span><span class="sxs-lookup"><span data-stu-id="40742-243">The format of this string is as follows:</span></span>

`<Transport>://<ComputerName>:<Port>/<ApplicationName>`

<span data-ttu-id="40742-244">De standaard waarde is als volgt:</span><span class="sxs-lookup"><span data-stu-id="40742-244">The default value is as follows:</span></span>

`http://localhost:5985/WSMAN`

<span data-ttu-id="40742-245">Als u geen **ConnectionURI** opgeeft, kunt u de para meters **UseSSL** , **ComputerName** , **Port** en **ApplicationName** gebruiken om de **ConnectionURI** -waarden op te geven.</span><span class="sxs-lookup"><span data-stu-id="40742-245">If you do not specify a **ConnectionURI** , you can use the **UseSSL** , **ComputerName** , **Port** , and **ApplicationName** parameters to specify the **ConnectionURI** values.</span></span>

<span data-ttu-id="40742-246">Geldige waarden voor het transport segment van de URI zijn HTTP en HTTPS.</span><span class="sxs-lookup"><span data-stu-id="40742-246">Valid values for the Transport segment of the URI are HTTP and HTTPS.</span></span> <span data-ttu-id="40742-247">Als u een verbindings-URI met een transport segment opgeeft, maar geen poort opgeeft, wordt de sessie gemaakt met standaard poorten: 80 voor HTTP en 443 voor HTTPS.</span><span class="sxs-lookup"><span data-stu-id="40742-247">If you specify a connection URI with a Transport segment, but do not specify a port, the session is created with standards ports: 80 for HTTP and 443 for HTTPS.</span></span> <span data-ttu-id="40742-248">Als u de standaard poorten voor externe communicatie van Power shell wilt gebruiken, geeft u poort 5985 voor HTTP of 5986 op voor HTTPS.</span><span class="sxs-lookup"><span data-stu-id="40742-248">To use the default ports for PowerShell remoting, specify port 5985 for HTTP or 5986 for HTTPS.</span></span>

<span data-ttu-id="40742-249">Als de doel computer de verbinding omleidt naar een andere URI, wordt de omleiding door Power shell voor komen, tenzij u de para meter **AllowRedirection** in de opdracht gebruikt.</span><span class="sxs-lookup"><span data-stu-id="40742-249">If the destination computer redirects the connection to a different URI, PowerShell prevents the redirection unless you use the **AllowRedirection** parameter in the command.</span></span>

```yaml
Type: System.Uri[]
Parameter Sets: Uri
Aliases: URI, CU

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="40742-250">-ContainerId</span><span class="sxs-lookup"><span data-stu-id="40742-250">-ContainerId</span></span>

<span data-ttu-id="40742-251">Hiermee geeft u een matrix met Id's van containers op.</span><span class="sxs-lookup"><span data-stu-id="40742-251">Specifies an array of IDs of containers.</span></span> <span data-ttu-id="40742-252">Met deze cmdlet wordt een interactieve sessie gestart met elk van de opgegeven containers.</span><span class="sxs-lookup"><span data-stu-id="40742-252">This cmdlet starts an interactive session with each of the specified containers.</span></span> <span data-ttu-id="40742-253">Gebruik de `docker ps` opdracht om een lijst met container-id's op te halen.</span><span class="sxs-lookup"><span data-stu-id="40742-253">Use the `docker ps` command to get a list of container IDs.</span></span> <span data-ttu-id="40742-254">Zie de Help voor de opdracht [docker PS](https://docs.docker.com/engine/reference/commandline/ps/) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="40742-254">For more information, see the help for the [docker ps](https://docs.docker.com/engine/reference/commandline/ps/) command.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ContainerId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="40742-255">-Credential</span><span class="sxs-lookup"><span data-stu-id="40742-255">-Credential</span></span>

<span data-ttu-id="40742-256">Hiermee geeft u een gebruikers account op dat gemachtigd is om deze actie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="40742-256">Specifies a user account that has permission to do this action.</span></span> <span data-ttu-id="40742-257">Standaard is dit de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="40742-257">The default is the current user.</span></span>

<span data-ttu-id="40742-258">Typ een gebruikers naam, zoals **gebruiker01** of **Domain01\User01** , of voer een **PSCredential** -object in dat door de cmdlet wordt gegenereerd `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="40742-258">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="40742-259">Als u een gebruikers naam typt, wordt u gevraagd het wacht woord in te voeren.</span><span class="sxs-lookup"><span data-stu-id="40742-259">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="40742-260">Referenties worden opgeslagen in een [PSCredential](/dotnet/api/system.management.automation.pscredential) -object en het wacht woord wordt opgeslagen als [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="40742-260">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="40742-261">Zie [Hoe veilig is securestring?](/dotnet/api/system.security.securestring#how-secure-is-securestring)voor meer informatie over **securestring** Data Protection.</span><span class="sxs-lookup"><span data-stu-id="40742-261">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerName, Uri, VMId, VMName
Aliases:

Required: True (VMId, VMName), False (ComputerName, Uri)
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="40742-262">-EnableNetworkAccess</span><span class="sxs-lookup"><span data-stu-id="40742-262">-EnableNetworkAccess</span></span>

<span data-ttu-id="40742-263">Geeft aan dat met deze cmdlet een interactief beveiligings token wordt toegevoegd aan loop Back-sessies.</span><span class="sxs-lookup"><span data-stu-id="40742-263">Indicates that this cmdlet adds an interactive security token to loopback sessions.</span></span> <span data-ttu-id="40742-264">Met het interactieve token kunt u opdrachten uitvoeren in de loop back-sessie die gegevens van andere computers ophalen.</span><span class="sxs-lookup"><span data-stu-id="40742-264">The interactive token lets you run commands in the loopback session that get data from other computers.</span></span> <span data-ttu-id="40742-265">U kunt bijvoorbeeld een opdracht uitvoeren in de sessie waarmee XML-bestanden van een externe computer naar de lokale computer worden gekopieerd.</span><span class="sxs-lookup"><span data-stu-id="40742-265">For example, you can run a command in the session that copies XML files from a remote computer to the local computer.</span></span>

<span data-ttu-id="40742-266">Een loop back-sessie is een **PSSession** die afkomstig is van en eindigt op dezelfde computer.</span><span class="sxs-lookup"><span data-stu-id="40742-266">A loopback session is a **PSSession** that originates and ends on the same computer.</span></span> <span data-ttu-id="40742-267">Als u een loop back-sessie wilt maken, laat u de para meter **ComputerName** weg of stelt u de waarde in op punt (.), localhost of de naam van de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="40742-267">To create a loopback session, omit the **ComputerName** parameter or set its value to dot (.), localhost, or the name of the local computer.</span></span>

<span data-ttu-id="40742-268">Met deze cmdlet worden standaard loop Back-sessies gemaakt met behulp van een netwerk token, dat mogelijk niet voldoende machtigingen biedt om te verifiëren bij externe computers.</span><span class="sxs-lookup"><span data-stu-id="40742-268">By default, this cmdlet creates loopback sessions by using a network token, which might not provide sufficient permission to authenticate to remote computers.</span></span>

<span data-ttu-id="40742-269">De para meter **EnableNetworkAccess** is alleen effectief in loop Back-sessies.</span><span class="sxs-lookup"><span data-stu-id="40742-269">The **EnableNetworkAccess** parameter is effective only in loopback sessions.</span></span> <span data-ttu-id="40742-270">Als u **EnableNetworkAccess** gebruikt wanneer u een sessie op een externe computer maakt, mislukt de opdracht, maar wordt de para meter genegeerd.</span><span class="sxs-lookup"><span data-stu-id="40742-270">If you use **EnableNetworkAccess** when you create a session on a remote computer, the command succeeds, but the parameter is ignored.</span></span>

<span data-ttu-id="40742-271">U kunt ook externe toegang inschakelen in een loop back-sessie met behulp van de CredSSP-waarde van de para meter **Authentication** , waarmee de sessie referenties worden overgedragen aan andere computers.</span><span class="sxs-lookup"><span data-stu-id="40742-271">You can also enable remote access in a loopback session by using the CredSSP value of the **Authentication** parameter, which delegates the session credentials to other computers.</span></span>

<span data-ttu-id="40742-272">Om de computer te beschermen tegen kwaad aardige toegang, kunnen niet-verbonden loop Back-sessies met interactieve tokens, die zijn gemaakt met behulp van de para meter **EnableNetworkAccess** , alleen opnieuw worden aangesloten op de computer waarop de sessie is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="40742-272">To protect the computer from malicious access, disconnected loopback sessions that have interactive tokens, which are those created by using the **EnableNetworkAccess** parameter, can be reconnected only from the computer on which the session was created.</span></span> <span data-ttu-id="40742-273">Verbroken sessies die gebruikmaken van CredSSP-verificatie, kunnen opnieuw worden aangesloten op andere computers.</span><span class="sxs-lookup"><span data-stu-id="40742-273">Disconnected sessions that use CredSSP authentication can be reconnected from other computers.</span></span> <span data-ttu-id="40742-274">Voor meer informatie raadpleegt u `Disconnect-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="40742-274">For more information, see `Disconnect-PSSession`.</span></span>

<span data-ttu-id="40742-275">Deze para meter is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="40742-275">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName, Uri, Session
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="40742-276">-Name</span><span class="sxs-lookup"><span data-stu-id="40742-276">-Name</span></span>

<span data-ttu-id="40742-277">Hiermee geeft u een beschrijvende naam op voor de **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="40742-277">Specifies a friendly name for the **PSSession**.</span></span>

<span data-ttu-id="40742-278">U kunt de naam gebruiken om te verwijzen naar de **PSSession** wanneer u andere cmdlets gebruikt, zoals `Get-PSSession` en `Enter-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="40742-278">You can use the name to refer to the **PSSession** when you use other cmdlets, such as `Get-PSSession` and `Enter-PSSession`.</span></span> <span data-ttu-id="40742-279">De naam hoeft niet uniek te zijn voor de computer of de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="40742-279">The name is not required to be unique to the computer or the current session.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="40742-280">-Port</span><span class="sxs-lookup"><span data-stu-id="40742-280">-Port</span></span>

<span data-ttu-id="40742-281">Hiermee geeft u de netwerk poort op de externe computer op die voor deze verbinding wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="40742-281">Specifies the network port on the remote computer that is used for this connection.</span></span> <span data-ttu-id="40742-282">Als u verbinding wilt maken met een externe computer, moet op de externe computer worden geluisterd op de poort die door de verbinding wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="40742-282">To connect to a remote computer, the remote computer must be listening on the port that the connection uses.</span></span> <span data-ttu-id="40742-283">De standaard poorten zijn 5985, de WinRM-poort voor HTTP en 5986, de WinRM-poort voor HTTPS.</span><span class="sxs-lookup"><span data-stu-id="40742-283">The default ports are 5985, which is the WinRM port for HTTP, and 5986, which is the WinRM port for HTTPS.</span></span>

<span data-ttu-id="40742-284">Voordat u een andere poort gebruikt, moet u de WinRM-listener op de externe computer configureren om op die poort te Luis teren.</span><span class="sxs-lookup"><span data-stu-id="40742-284">Before using another port, you must configure the WinRM listener on the remote computer to listen at that port.</span></span> <span data-ttu-id="40742-285">Gebruik de volgende opdrachten om de listener te configureren:</span><span class="sxs-lookup"><span data-stu-id="40742-285">Use the following commands to configure the listener:</span></span>

1. `winrm delete winrm/config/listener?Address=*+Transport=HTTP`
2. `winrm create winrm/config/listener?Address=*+Transport=HTTP @{Port="\<port-number\>"}`

<span data-ttu-id="40742-286">Gebruik de para meter **poort** alleen als dat nodig is.</span><span class="sxs-lookup"><span data-stu-id="40742-286">Do not use the **Port** parameter unless you must.</span></span> <span data-ttu-id="40742-287">De poort instelling in de opdracht is van toepassing op alle computers of sessies waarop de opdracht wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="40742-287">The port setting in the command applies to all computers or sessions on which the command runs.</span></span> <span data-ttu-id="40742-288">Een alternatieve poort instelling kan verhinderen dat de opdracht wordt uitgevoerd op alle computers.</span><span class="sxs-lookup"><span data-stu-id="40742-288">An alternate port setting might prevent the command from running on all computers.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="40742-289">-RunAsAdministrator</span><span class="sxs-lookup"><span data-stu-id="40742-289">-RunAsAdministrator</span></span>

<span data-ttu-id="40742-290">Geeft aan dat de **PSSession** wordt uitgevoerd als beheerder.</span><span class="sxs-lookup"><span data-stu-id="40742-290">Indicates that the **PSSession** runs as administrator.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ContainerId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="40742-291">-Sessie</span><span class="sxs-lookup"><span data-stu-id="40742-291">-Session</span></span>

<span data-ttu-id="40742-292">Hiermee geeft u een matrix met **PSSession** -objecten op die met deze cmdlet als model voor de nieuwe **PSSession** wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="40742-292">Specifies an array of **PSSession** objects that this cmdlet uses as a model for the new **PSSession**.</span></span> <span data-ttu-id="40742-293">Met deze para meter maakt u nieuwe **PSSession** -objecten die dezelfde eigenschappen hebben als de opgegeven **PSSession** -objecten.</span><span class="sxs-lookup"><span data-stu-id="40742-293">This parameter creates new **PSSession** objects that have the same properties as the specified **PSSession** objects.</span></span>

<span data-ttu-id="40742-294">Voer een variabele in die de **PSSession** -objecten bevat of een opdracht waarmee de **PSSession** -objecten, zoals een of-opdracht, worden gemaakt of opgehaald `New-PSSession` `Get-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="40742-294">Enter a variable that contains the **PSSession** objects or a command that creates or gets the **PSSession** objects, such as a `New-PSSession` or `Get-PSSession` command.</span></span>

<span data-ttu-id="40742-295">De resulterende **PSSession** -objecten hebben dezelfde computer naam, toepassings naam, VERBINDINGS-URI, poort, configuratie naam, beperkings limiet en Secure Sockets Layer (SSL) als de oorspronkelijke waarden, maar ze hebben een andere weergave naam, id en exemplaar-id (GUID).</span><span class="sxs-lookup"><span data-stu-id="40742-295">The resulting **PSSession** objects have the same computer name, application name, connection URI, port, configuration name, throttle limit, and Secure Sockets Layer (SSL) value as the originals, but they have a different display name, ID, and instance ID (GUID).</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession[]
Parameter Sets: Session
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="40742-296">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="40742-296">-SessionOption</span></span>

<span data-ttu-id="40742-297">Hiermee geeft u geavanceerde opties voor de sessie op.</span><span class="sxs-lookup"><span data-stu-id="40742-297">Specifies advanced options for the session.</span></span> <span data-ttu-id="40742-298">Voer een **SessionOption** -object in, zoals het, dat u maakt met behulp van de `New-PSSessionOption` cmdlet of een hash-tabel waarin de sleutels de naam van de sessie optie zijn en de waarden voor de waarden van de sessie.</span><span class="sxs-lookup"><span data-stu-id="40742-298">Enter a **SessionOption** object, such as one that you create by using the `New-PSSessionOption` cmdlet, or a hash table in which the keys are session option names and the values are session option values.</span></span>

<span data-ttu-id="40742-299">De standaard waarden voor de opties worden bepaald door de waarde van de `$PSSessionOption` Voorkeurs variabele, als deze is ingesteld.</span><span class="sxs-lookup"><span data-stu-id="40742-299">The default values for the options are determined by the value of the `$PSSessionOption` preference variable, if it is set.</span></span> <span data-ttu-id="40742-300">Anders worden de standaard waarden bepaald door opties die zijn ingesteld in de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="40742-300">Otherwise, the default values are established by options set in the session configuration.</span></span>

<span data-ttu-id="40742-301">De waarden van de sessie optie hebben voor rang op de standaard waarden voor sessies die zijn ingesteld in de `$PSSessionOption` Voorkeurs variabele en in de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="40742-301">The session option values take precedence over default values for sessions set in the `$PSSessionOption` preference variable and in the session configuration.</span></span> <span data-ttu-id="40742-302">Ze hebben echter geen voor rang op de maximum waarden, quota's of limieten die zijn ingesteld in de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="40742-302">However, they do not take precedence over maximum values, quotas or limits set in the session configuration.</span></span>

<span data-ttu-id="40742-303">Zie voor een beschrijving van de sessie opties die de standaard waarden bevatten `New-PSSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="40742-303">For a description of the session options that includes the default values, see `New-PSSessionOption`.</span></span> <span data-ttu-id="40742-304">Zie about_Preference_Variables voor meer informatie over de `$PSSessionOption` voorkeurs [about_Preference_Variables](About/about_Preference_Variables.md)variabele.</span><span class="sxs-lookup"><span data-stu-id="40742-304">For information about the `$PSSessionOption` preference variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span> <span data-ttu-id="40742-305">Zie [about_Session_Configurations](About/about_Session_Configurations.md) (Engelstalig) voor meer informatie over sessieconfiguraties.</span><span class="sxs-lookup"><span data-stu-id="40742-305">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: ComputerName, Uri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="40742-306">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="40742-306">-ThrottleLimit</span></span>

<span data-ttu-id="40742-307">Hiermee geeft u het maximum aantal gelijktijdige verbindingen op dat tot stand kan worden gebracht om deze opdracht uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="40742-307">Specifies the maximum number of concurrent connections that can be established to run this command.</span></span>
<span data-ttu-id="40742-308">Als u deze para meter weglaat of een waarde van 0 (nul) opgeeft, wordt de standaard waarde 32 gebruikt.</span><span class="sxs-lookup"><span data-stu-id="40742-308">If you omit this parameter or enter a value of 0 (zero), the default value, 32, is used.</span></span>

<span data-ttu-id="40742-309">De beperkings limiet geldt alleen voor de huidige opdracht, niet voor de sessie of voor de computer.</span><span class="sxs-lookup"><span data-stu-id="40742-309">The throttle limit applies only to the current command, not to the session or to the computer.</span></span>

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

### <span data-ttu-id="40742-310">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="40742-310">-UseSSL</span></span>

<span data-ttu-id="40742-311">Geeft aan dat deze cmdlet het SSL-protocol gebruikt om verbinding te maken met de externe computer.</span><span class="sxs-lookup"><span data-stu-id="40742-311">Indicates that this cmdlet uses the SSL protocol to establish a connection to the remote computer.</span></span>
<span data-ttu-id="40742-312">Standaard wordt SSL niet gebruikt.</span><span class="sxs-lookup"><span data-stu-id="40742-312">By default, SSL is not used.</span></span>

<span data-ttu-id="40742-313">WS-Management versleutelt alle Power shell-inhoud die via het netwerk wordt verzonden.</span><span class="sxs-lookup"><span data-stu-id="40742-313">WS-Management encrypts all PowerShell content transmitted over the network.</span></span> <span data-ttu-id="40742-314">De para meter **UseSSL** biedt een extra beveiliging voor het verzenden van de gegevens via een HTTPS-verbinding in plaats van een http-verbinding.</span><span class="sxs-lookup"><span data-stu-id="40742-314">The **UseSSL** parameter offers an additional protection that sends the data across an HTTPS connection instead of an HTTP connection.</span></span>

<span data-ttu-id="40742-315">Als u deze para meter gebruikt, maar SSL is niet beschikbaar op de poort die wordt gebruikt voor de opdracht, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="40742-315">If you use this parameter, but SSL is not available on the port that is used for the command, the command fails.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="40742-316">-VMId</span><span class="sxs-lookup"><span data-stu-id="40742-316">-VMId</span></span>

<span data-ttu-id="40742-317">Hiermee geeft u een ID-matrix van virtuele machines op.</span><span class="sxs-lookup"><span data-stu-id="40742-317">Specifies an array of ID of virtual machines.</span></span> <span data-ttu-id="40742-318">Met deze cmdlet wordt een interactieve sessie gestart met elk van de opgegeven virtuele machines.</span><span class="sxs-lookup"><span data-stu-id="40742-318">This cmdlet starts an interactive session with each of the specified virtual machines.</span></span> <span data-ttu-id="40742-319">Als u de virtuele machines wilt zien die voor u beschikbaar zijn, gebruikt u de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="40742-319">To see the virtual machines that are available to you, use the following command:</span></span>

`Get-VM | Select-Object -Property Name, ID`

```yaml
Type: System.Guid[]
Parameter Sets: VMId
Aliases: VMGuid

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="40742-320">-VMName</span><span class="sxs-lookup"><span data-stu-id="40742-320">-VMName</span></span>

<span data-ttu-id="40742-321">Hiermee geeft u een matrix met namen van virtuele machines op.</span><span class="sxs-lookup"><span data-stu-id="40742-321">Specifies an array of names of virtual machines.</span></span> <span data-ttu-id="40742-322">Met deze cmdlet wordt een interactieve sessie gestart met elk van de opgegeven virtuele machines.</span><span class="sxs-lookup"><span data-stu-id="40742-322">This cmdlet starts an interactive session with each of the specified virtual machines.</span></span> <span data-ttu-id="40742-323">Gebruik de cmdlet om de virtuele machines weer te geven die voor u beschikbaar zijn `Get-VM` .</span><span class="sxs-lookup"><span data-stu-id="40742-323">To see the virtual machines that are available to you, use the `Get-VM` cmdlet.</span></span>

```yaml
Type: System.String[]
Parameter Sets: VMName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="40742-324">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="40742-324">CommonParameters</span></span>

<span data-ttu-id="40742-325">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="40742-325">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="40742-326">Zie about_CommonParameters (voor meer informatie https://go.microsoft.com/fwlink/?LinkID=113216) .</span><span class="sxs-lookup"><span data-stu-id="40742-326">For more information, see about_CommonParameters (https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="40742-327">INVOER</span><span class="sxs-lookup"><span data-stu-id="40742-327">INPUTS</span></span>

### <span data-ttu-id="40742-328">System. String, System. URI, System. Management. Automation. Runspaces. PSSession</span><span class="sxs-lookup"><span data-stu-id="40742-328">System.String, System.URI, System.Management.Automation.Runspaces.PSSession</span></span>

<span data-ttu-id="40742-329">U kunt een teken reeks, URI of sessie object door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="40742-329">You can pipe a string, URI, or session object to this cmdlet.</span></span>

## <span data-ttu-id="40742-330">UITVOER</span><span class="sxs-lookup"><span data-stu-id="40742-330">OUTPUTS</span></span>

### <span data-ttu-id="40742-331">System. Management. Automation. Runspaces. PSSession</span><span class="sxs-lookup"><span data-stu-id="40742-331">System.Management.Automation.Runspaces.PSSession</span></span>

## <span data-ttu-id="40742-332">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="40742-332">NOTES</span></span>

- <span data-ttu-id="40742-333">Deze cmdlet maakt gebruik van de externe infra structuur van Power shell.</span><span class="sxs-lookup"><span data-stu-id="40742-333">This cmdlet uses the PowerShell remoting infrastructure.</span></span> <span data-ttu-id="40742-334">Als u deze cmdlet wilt gebruiken, moeten de lokale computer en alle externe computers worden geconfigureerd voor externe communicatie met Power shell.</span><span class="sxs-lookup"><span data-stu-id="40742-334">To use this cmdlet, the local computer and any remote computers must be configured for PowerShell remoting.</span></span> <span data-ttu-id="40742-335">Zie [about_Remote_Requirements](About/about_Remote_Requirements.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="40742-335">For more information, see [about_Remote_Requirements](About/about_Remote_Requirements.md).</span></span>
- <span data-ttu-id="40742-336">Als u een **PSSession** op de lokale computer wilt maken, start u Power shell met de optie als administrator uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="40742-336">To create a **PSSession** on the local computer, start PowerShell with the Run as administrator option.</span></span>
- <span data-ttu-id="40742-337">Wanneer u klaar bent met de **PSSession** , gebruikt u de `Remove-PSSession` cmdlet om de **PSSession** te verwijderen en de bijbehorende resources vrij te geven.</span><span class="sxs-lookup"><span data-stu-id="40742-337">When you are finished with the **PSSession** , use the `Remove-PSSession` cmdlet to delete the **PSSession** and release its resources.</span></span>

## <span data-ttu-id="40742-338">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="40742-338">RELATED LINKS</span></span>

[<span data-ttu-id="40742-339">Connect-PSSession</span><span class="sxs-lookup"><span data-stu-id="40742-339">Connect-PSSession</span></span>](Connect-PSSession.md)

[<span data-ttu-id="40742-340">Verbinding verbreken-PSSession</span><span class="sxs-lookup"><span data-stu-id="40742-340">Disconnect-PSSession</span></span>](Disconnect-PSSession.md)

[<span data-ttu-id="40742-341">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="40742-341">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="40742-342">Afsluiten-PSSession</span><span class="sxs-lookup"><span data-stu-id="40742-342">Exit-PSSession</span></span>](Exit-PSSession.md)

[<span data-ttu-id="40742-343">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="40742-343">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="40742-344">Invoke-opdracht</span><span class="sxs-lookup"><span data-stu-id="40742-344">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="40742-345">Receive-PSSession</span><span class="sxs-lookup"><span data-stu-id="40742-345">Receive-PSSession</span></span>](Receive-PSSession.md)

[<span data-ttu-id="40742-346">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="40742-346">Remove-PSSession</span></span>](Remove-PSSession.md)
