---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 12/20/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-pssession?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSSession
ms.openlocfilehash: 4b40d765002791f45f093c7912b8f9ba58248da9
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706187"
---
# <span data-ttu-id="3c35a-102">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="3c35a-102">New-PSSession</span></span>

## <span data-ttu-id="3c35a-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="3c35a-103">SYNOPSIS</span></span>
<span data-ttu-id="3c35a-104">Hiermee maakt u een permanente verbinding met een lokale of externe computer.</span><span class="sxs-lookup"><span data-stu-id="3c35a-104">Creates a persistent connection to a local or remote computer.</span></span>

## <span data-ttu-id="3c35a-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="3c35a-105">SYNTAX</span></span>

### <span data-ttu-id="3c35a-106">Computer naam (standaard)</span><span class="sxs-lookup"><span data-stu-id="3c35a-106">ComputerName (Default)</span></span>

```
New-PSSession [[-ComputerName] <String[]>] [-Credential <PSCredential>] [-Name <String[]>]
 [-EnableNetworkAccess] [-ConfigurationName <String>] [-Port <Int32>] [-UseSSL]
 [-ApplicationName <String>] [-ThrottleLimit <Int32>] [-SessionOption <PSSessionOption>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="3c35a-107">URI</span><span class="sxs-lookup"><span data-stu-id="3c35a-107">Uri</span></span>

```
New-PSSession [-Credential <PSCredential>] [-Name <String[]>] [-EnableNetworkAccess]
 [-ConfigurationName <String>] [-ThrottleLimit <Int32>] [-ConnectionUri] <Uri[]> [-AllowRedirection]
 [-SessionOption <PSSessionOption>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="3c35a-108">VMId</span><span class="sxs-lookup"><span data-stu-id="3c35a-108">VMId</span></span>

```
New-PSSession -Credential <PSCredential> [-Name <String[]>] [-ConfigurationName <String>]
 [-VMId] <Guid[]> [-ThrottleLimit <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="3c35a-109">VMName</span><span class="sxs-lookup"><span data-stu-id="3c35a-109">VMName</span></span>

```
New-PSSession -Credential <PSCredential> [-Name <String[]>] [-ConfigurationName <String>]
 -VMName <String[]> [-ThrottleLimit <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="3c35a-110">Sessie</span><span class="sxs-lookup"><span data-stu-id="3c35a-110">Session</span></span>

```
New-PSSession [[-Session] <PSSession[]>] [-Name <String[]>] [-EnableNetworkAccess]
 [-ThrottleLimit <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="3c35a-111">ContainerId</span><span class="sxs-lookup"><span data-stu-id="3c35a-111">ContainerId</span></span>

```
New-PSSession [-Name <String[]>] [-ConfigurationName <String>] -ContainerId <String[]>
 [-RunAsAdministrator] [-ThrottleLimit <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="3c35a-112">UseWindowsPowerShellParameterSet</span><span class="sxs-lookup"><span data-stu-id="3c35a-112">UseWindowsPowerShellParameterSet</span></span>

```
New-PSSession [-Name <String[]>] [-UseWindowsPowerShell] [<CommonParameters>]
```

### <span data-ttu-id="3c35a-113">SSHHost</span><span class="sxs-lookup"><span data-stu-id="3c35a-113">SSHHost</span></span>

```
New-PSSession [-Name <String[]>] [-Port <Int32>] [-HostName] <String[]> [-UserName <String>]
 [-KeyFilePath <String>] [-SSHTransport] [-Subsystem <String>] [<CommonParameters>]
```

### <span data-ttu-id="3c35a-114">SSHHostHashParam</span><span class="sxs-lookup"><span data-stu-id="3c35a-114">SSHHostHashParam</span></span>

```
New-PSSession [-Name <String[]>] -SSHConnection <Hashtable[]> [<CommonParameters>]
```

## <span data-ttu-id="3c35a-115">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="3c35a-115">DESCRIPTION</span></span>

<span data-ttu-id="3c35a-116">`New-PSSession`Met de cmdlet maakt u een Power shell-sessie (**PSSession**) op een lokale of externe computer.</span><span class="sxs-lookup"><span data-stu-id="3c35a-116">The `New-PSSession` cmdlet creates a PowerShell session (**PSSession**) on a local or remote computer.</span></span> <span data-ttu-id="3c35a-117">Wanneer u een **PSSession** maakt, brengt Power shell een permanente verbinding met de externe computer tot stand.</span><span class="sxs-lookup"><span data-stu-id="3c35a-117">When you create a **PSSession**, PowerShell establishes a persistent connection to the remote computer.</span></span>

<span data-ttu-id="3c35a-118">Gebruik een **PSSession** om meerdere opdrachten uit te voeren die gegevens delen, zoals een functie of de waarde van een variabele.</span><span class="sxs-lookup"><span data-stu-id="3c35a-118">Use a **PSSession** to run multiple commands that share data, such as a function or the value of a variable.</span></span> <span data-ttu-id="3c35a-119">Gebruik de cmdlet om opdrachten uit te voeren in een **PSSession** `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="3c35a-119">To run commands in a **PSSession**, use the `Invoke-Command` cmdlet.</span></span> <span data-ttu-id="3c35a-120">Als u de **PSSession** wilt gebruiken om rechtstreeks te communiceren met een externe computer, gebruikt u de `Enter-PSSession` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3c35a-120">To use the **PSSession** to interact directly with a remote computer, use the `Enter-PSSession` cmdlet.</span></span> <span data-ttu-id="3c35a-121">Zie [about_PSSessions](about/about_PSSessions.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="3c35a-121">For more information, see [about_PSSessions](about/about_PSSessions.md).</span></span>

<span data-ttu-id="3c35a-122">U kunt opdrachten uitvoeren op een externe computer zonder een **PSSession** te maken met behulp van de **ComputerName** -para meters van `Enter-PSSession` of `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="3c35a-122">You can run commands on a remote computer without creating a **PSSession** by using the **ComputerName** parameters of `Enter-PSSession` or `Invoke-Command`.</span></span> <span data-ttu-id="3c35a-123">Wanneer u de para meter **ComputerName** gebruikt, maakt Power shell een tijdelijke verbinding die wordt gebruikt voor de opdracht en vervolgens gesloten.</span><span class="sxs-lookup"><span data-stu-id="3c35a-123">When you use the **ComputerName** parameter, PowerShell creates a temporary connection that is used for the command and is then closed.</span></span>

<span data-ttu-id="3c35a-124">Vanaf Power shell 6,0 kunt u Secure Shell (SSH) gebruiken om verbinding te maken met een sessie op een externe computer, als SSH beschikbaar is op de lokale computer en de externe computer is geconfigureerd met een Power shell-SSH-eind punt.</span><span class="sxs-lookup"><span data-stu-id="3c35a-124">Starting with PowerShell 6.0 you can use Secure Shell (SSH) to establish a connection to and create a session on a remote computer, if SSH is available on the local computer and the remote computer is configured with a PowerShell SSH endpoint.</span></span> <span data-ttu-id="3c35a-125">Het voor deel van een op SSH gebaseerde Power shell-externe sessie is dat deze op meerdere platformen (Windows, Linux, macOS) kan werken.</span><span class="sxs-lookup"><span data-stu-id="3c35a-125">The benefit of an SSH based PowerShell remote session is that it can work across multiple platforms (Windows, Linux, macOS).</span></span> <span data-ttu-id="3c35a-126">Voor op SSH gebaseerde sessies gebruikt u de para meter **hostname** of **SSHConnection** om de externe computer en de relevante verbindings gegevens op te geven.</span><span class="sxs-lookup"><span data-stu-id="3c35a-126">For SSH based sessions you use the **HostName** or **SSHConnection** parameter set to specify the remote computer and relevant connection information.</span></span> <span data-ttu-id="3c35a-127">Zie voor meer informatie over het instellen van externe toegang tot Power shell [via SSH Power shell](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span><span class="sxs-lookup"><span data-stu-id="3c35a-127">For more information about how to set up PowerShell SSH remoting, see [PowerShell Remoting Over SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span></span>

> [!NOTE]
> <span data-ttu-id="3c35a-128">Bij gebruik van WSMan externe toegang vanaf een Linux-of macOS-client met een HTTPS-eind punt waar het server certificaat niet wordt vertrouwd (bijvoorbeeld een zelfondertekend certificaat).</span><span class="sxs-lookup"><span data-stu-id="3c35a-128">When using WSMan remoting from a Linux or macOS client with a HTTPS endpoint where the server certificate is not trusted (e.g., a self-signed certificate).</span></span> <span data-ttu-id="3c35a-129">U moet een `PSSessionOption` met de- `-SkipCACheck` en- `-SkipCNCheck` koppeling opgeven om de verbinding tot stand te brengen.</span><span class="sxs-lookup"><span data-stu-id="3c35a-129">You must provide a `PSSessionOption` that includes `-SkipCACheck` and `-SkipCNCheck` to successfully establish the connection.</span></span> <span data-ttu-id="3c35a-130">Doe dit alleen als u zich in een omgeving bevindt waarin u zeker van het server certificaat en de netwerk verbinding met het doel systeem kunt zijn.</span><span class="sxs-lookup"><span data-stu-id="3c35a-130">Only do this if you are in an environment where you can be certain of the server certificate and the network connection to the target system.</span></span>

## <span data-ttu-id="3c35a-131">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="3c35a-131">EXAMPLES</span></span>

### <span data-ttu-id="3c35a-132">Voor beeld 1: een sessie op de lokale computer maken</span><span class="sxs-lookup"><span data-stu-id="3c35a-132">Example 1: Create a session on the local computer</span></span>

```powershell
$s = New-PSSession
```

<span data-ttu-id="3c35a-133">Met deze opdracht maakt u een nieuwe **PSSession** op de lokale computer en slaat de **PSSession** op in de `$s` variabele.</span><span class="sxs-lookup"><span data-stu-id="3c35a-133">This command creates a new **PSSession** on the local computer and saves the **PSSession** in the `$s` variable.</span></span>

<span data-ttu-id="3c35a-134">U kunt deze **PSSession** nu gebruiken om opdrachten uit te voeren op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="3c35a-134">You can now use this **PSSession** to run commands on the local computer.</span></span>

### <span data-ttu-id="3c35a-135">Voor beeld 2: een sessie op een externe computer maken</span><span class="sxs-lookup"><span data-stu-id="3c35a-135">Example 2: Create a session on a remote computer</span></span>

```powershell
$Server01 = New-PSSession -ComputerName Server01
```

<span data-ttu-id="3c35a-136">Met deze opdracht maakt u een nieuwe **PSSession** op de Server01-computer en slaat deze op in de `$Server01` variabele.</span><span class="sxs-lookup"><span data-stu-id="3c35a-136">This command creates a new **PSSession** on the Server01 computer and saves it in the `$Server01` variable.</span></span>

<span data-ttu-id="3c35a-137">Wanneer u meerdere **PSSession** -objecten maakt, moet u deze toewijzen aan variabelen met nuttige namen.</span><span class="sxs-lookup"><span data-stu-id="3c35a-137">When creating multiple **PSSession** objects, assign them to variables with useful names.</span></span> <span data-ttu-id="3c35a-138">Dit helpt u bij het beheren van de **PSSession** -objecten in volgende opdrachten.</span><span class="sxs-lookup"><span data-stu-id="3c35a-138">This will help you manage the **PSSession** objects in subsequent commands.</span></span>

### <span data-ttu-id="3c35a-139">Voor beeld 3: sessies op meerdere computers maken</span><span class="sxs-lookup"><span data-stu-id="3c35a-139">Example 3: Create sessions on multiple computers</span></span>

```powershell
$s1, $s2, $s3 = New-PSSession -ComputerName Server01,Server02,Server03
```

<span data-ttu-id="3c35a-140">Met deze opdracht worden drie **PSSession** -objecten gemaakt, één op elke computer die is opgegeven door de para meter **ComputerName** .</span><span class="sxs-lookup"><span data-stu-id="3c35a-140">This command creates three **PSSession** objects, one on each of the computers specified by the **ComputerName** parameter.</span></span>

<span data-ttu-id="3c35a-141">De opdracht gebruikt de toewijzings operator (=) om de nieuwe **PSSession** -objecten toe te wijzen aan variabelen: `$s1` , `$s2` , `$s3` .</span><span class="sxs-lookup"><span data-stu-id="3c35a-141">The command uses the assignment operator (=) to assign the new **PSSession** objects to variables: `$s1`, `$s2`, `$s3`.</span></span> <span data-ttu-id="3c35a-142">De Server01 **PSSession** wordt toegewezen aan `$s1` , de Server02 **PSSession** aan `$s2` en de Server03 **PSSession** tot `$s3` .</span><span class="sxs-lookup"><span data-stu-id="3c35a-142">It assigns the Server01 **PSSession** to `$s1`, the Server02 **PSSession** to `$s2`, and the Server03 **PSSession** to `$s3`.</span></span>

<span data-ttu-id="3c35a-143">Wanneer u meerdere objecten toewijst aan een reeks variabelen, wijst Power shell elk object toe aan een variabele in de reeks.</span><span class="sxs-lookup"><span data-stu-id="3c35a-143">When you assign multiple objects to a series of variables, PowerShell assigns each object to a variable in the series respectively.</span></span> <span data-ttu-id="3c35a-144">Als er meer objecten zijn dan variabelen, worden alle resterende objecten toegewezen aan de laatste variabele.</span><span class="sxs-lookup"><span data-stu-id="3c35a-144">If there are more objects than variables, all remaining objects are assigned to the last variable.</span></span> <span data-ttu-id="3c35a-145">Als er meer variabelen zijn dan objecten, zijn de resterende variabelen leeg (null).</span><span class="sxs-lookup"><span data-stu-id="3c35a-145">If there are more variables than objects, the remaining variables are empty (null).</span></span>

### <span data-ttu-id="3c35a-146">Voor beeld 4: een sessie met een opgegeven poort maken</span><span class="sxs-lookup"><span data-stu-id="3c35a-146">Example 4: Create a session with a specified port</span></span>

```powershell
New-PSSession -ComputerName Server01 -Port 8081 -UseSSL -ConfigurationName E12
```

<span data-ttu-id="3c35a-147">Met deze opdracht maakt u een nieuwe **PSSession** op de Server01-computer die verbinding maakt met server poort 8081 en gebruikmaakt van het SSL-protocol.</span><span class="sxs-lookup"><span data-stu-id="3c35a-147">This command creates a new **PSSession** on the Server01 computer that connects to server port 8081 and uses the SSL protocol.</span></span> <span data-ttu-id="3c35a-148">De nieuwe **PSSession** gebruikt een alternatieve sessie configuratie met de naam E12.</span><span class="sxs-lookup"><span data-stu-id="3c35a-148">The new **PSSession** uses an alternative session configuration called E12.</span></span>

<span data-ttu-id="3c35a-149">Voordat u de poort instelt, moet u de WinRM-listener op de externe computer configureren om te Luis teren op poort 8081.</span><span class="sxs-lookup"><span data-stu-id="3c35a-149">Before setting the port, you must configure the WinRM listener on the remote computer to listen on port 8081.</span></span> <span data-ttu-id="3c35a-150">Zie de beschrijving van de **poort** parameter voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="3c35a-150">For more information, see the description of the **Port** parameter.</span></span>

### <span data-ttu-id="3c35a-151">Voor beeld 5: een sessie maken op basis van een bestaande sessie</span><span class="sxs-lookup"><span data-stu-id="3c35a-151">Example 5: Create a session based on an existing session</span></span>

```powershell
New-PSSession -Session $s -Credential Domain01\User01
```

<span data-ttu-id="3c35a-152">Met deze opdracht maakt u een **PSSession** met dezelfde eigenschappen als een bestaande **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="3c35a-152">This command creates a **PSSession** with the same properties as an existing **PSSession**.</span></span> <span data-ttu-id="3c35a-153">U kunt deze opdracht indeling gebruiken wanneer de resources van een bestaand **PSSession** uitgeput zijn en er een nieuwe **PSSession** nodig is om een deel van de vraag te offloaden.</span><span class="sxs-lookup"><span data-stu-id="3c35a-153">You can use this command format when the resources of an existing **PSSession** are exhausted and a new **PSSession** is needed to offload some of the demand.</span></span>

<span data-ttu-id="3c35a-154">De opdracht gebruikt de **sessie** parameter van `New-PSSession` om de **PSSession** op te geven die is opgeslagen in de `$s` variabele.</span><span class="sxs-lookup"><span data-stu-id="3c35a-154">The command uses the **Session** parameter of `New-PSSession` to specify the **PSSession** saved in the `$s` variable.</span></span> <span data-ttu-id="3c35a-155">Het gebruikt de referenties van de Domain1\Admin01-gebruiker om de opdracht te volt ooien.</span><span class="sxs-lookup"><span data-stu-id="3c35a-155">It uses the credentials of the Domain1\Admin01 user to complete the command.</span></span>

### <span data-ttu-id="3c35a-156">Voor beeld 6: een sessie met een globaal bereik in een ander domein maken</span><span class="sxs-lookup"><span data-stu-id="3c35a-156">Example 6: Create a session with a global scope in a different domain</span></span>

```powershell
$global:s = New-PSSession -ComputerName Server1.Domain44.Corpnet.Fabrikam.com -Credential Domain01\Admin01
```

<span data-ttu-id="3c35a-157">In dit voor beeld ziet u hoe u een **PSSession** maakt met een globaal bereik op een computer in een ander domein.</span><span class="sxs-lookup"><span data-stu-id="3c35a-157">This example shows how to create a **PSSession** with a global scope on a computer in a different domain.</span></span>

<span data-ttu-id="3c35a-158">**PSSession** -objecten die zijn gemaakt op de opdracht regel, worden standaard gemaakt met een lokale scope en **PSSession** -objecten die zijn gemaakt in een script, hebben een script bereik.</span><span class="sxs-lookup"><span data-stu-id="3c35a-158">By default, **PSSession** objects created at the command line are created with local scope and **PSSession** objects created in a script have script scope.</span></span>

<span data-ttu-id="3c35a-159">Als u een **PSSession** met een globaal bereik wilt maken, maakt u een nieuwe **PSSession** en slaat u vervolgens de **PSSession** op in een variabele die wordt geconverteerd naar een globaal bereik.</span><span class="sxs-lookup"><span data-stu-id="3c35a-159">To create a **PSSession** with global scope, create a new **PSSession** and then store the **PSSession** in a variable that is cast to a global scope.</span></span> <span data-ttu-id="3c35a-160">In dit geval wordt de `$s` variabele geconverteerd naar een globaal bereik.</span><span class="sxs-lookup"><span data-stu-id="3c35a-160">In this case, the `$s` variable is cast to a global scope.</span></span>

<span data-ttu-id="3c35a-161">De opdracht gebruikt de para meter **ComputerName** om de externe computer op te geven.</span><span class="sxs-lookup"><span data-stu-id="3c35a-161">The command uses the **ComputerName** parameter to specify the remote computer.</span></span> <span data-ttu-id="3c35a-162">Omdat de computer zich in een ander domein bevindt dan het gebruikers account, wordt de volledige naam van de computer opgegeven samen met de referenties van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="3c35a-162">Because the computer is in a different domain than the user account, the full name of the computer is specified together with the credentials of the user.</span></span>

### <span data-ttu-id="3c35a-163">Voor beeld 7: sessies maken voor veel computers</span><span class="sxs-lookup"><span data-stu-id="3c35a-163">Example 7: Create sessions for many computers</span></span>

```powershell
$rs = Get-Content C:\Test\Servers.txt | New-PSSession -ThrottleLimit 50
```

<span data-ttu-id="3c35a-164">Met deze opdracht maakt u een **PSSession** op elk van de 200-computers die worden vermeld in het Servers.txt-bestand en wordt de resulterende **PSSession** in de `$rs` variabele opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="3c35a-164">This command creates a **PSSession** on each of the 200 computers listed in the Servers.txt file and it stores the resulting **PSSession** in the `$rs` variable.</span></span> <span data-ttu-id="3c35a-165">De **PSSession** -objecten hebben een beperkings limiet van 50.</span><span class="sxs-lookup"><span data-stu-id="3c35a-165">The **PSSession** objects have a throttle limit of 50.</span></span>

<span data-ttu-id="3c35a-166">U kunt deze opdracht indeling gebruiken wanneer de namen van computers worden opgeslagen in een Data Base, een werk blad, een tekst bestand of een andere Converteer bare tekst indeling.</span><span class="sxs-lookup"><span data-stu-id="3c35a-166">You can use this command format when the names of computers are stored in a database, spreadsheet, text file, or other text-convertible format.</span></span>

### <span data-ttu-id="3c35a-167">Voor beeld 8: een sessie maken met behulp van een URI</span><span class="sxs-lookup"><span data-stu-id="3c35a-167">Example 8: Create a session by using a URI</span></span>

```powershell
$s = New-PSSession -URI http://Server01:91/NewSession -Credential Domain01\User01
```

<span data-ttu-id="3c35a-168">Met deze opdracht maakt u een **PSSession** op de Server01-computer en slaat u deze op in de `$s` variabele.</span><span class="sxs-lookup"><span data-stu-id="3c35a-168">This command creates a **PSSession** on the Server01 computer and stores it in the `$s` variable.</span></span> <span data-ttu-id="3c35a-169">De para meter **URI** wordt gebruikt om het transport protocol, de externe computer, de poort en een alternatieve sessie configuratie op te geven.</span><span class="sxs-lookup"><span data-stu-id="3c35a-169">It uses the **URI** parameter to specify the transport protocol, the remote computer, the port, and an alternate session configuration.</span></span> <span data-ttu-id="3c35a-170">Ook wordt de para meter **Credential** gebruikt om een gebruikers account op te geven dat gemachtigd is om een sessie te maken op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="3c35a-170">It also uses the **Credential** parameter to specify a user account that has permission to create a session on the remote computer.</span></span>

### <span data-ttu-id="3c35a-171">Voor beeld 9: een achtergrond taak uitvoeren in een reeks sessies</span><span class="sxs-lookup"><span data-stu-id="3c35a-171">Example 9: Run a background job in a set of sessions</span></span>

```powershell
$s = New-PSSession -ComputerName (Get-Content Servers.txt) -Credential Domain01\Admin01 -ThrottleLimit 16
Invoke-Command -Session $s -ScriptBlock {Get-Process PowerShell} -AsJob
```

<span data-ttu-id="3c35a-172">Met deze opdrachten maakt u een set **PSSession** -objecten en voert u vervolgens een achtergrond taak uit in elk van de **PSSession** -objecten.</span><span class="sxs-lookup"><span data-stu-id="3c35a-172">These commands create a set of **PSSession** objects and then run a background job in each of the **PSSession** objects.</span></span>

<span data-ttu-id="3c35a-173">Met de eerste opdracht maakt u een nieuwe **PSSession** op elke computer die wordt vermeld in het Servers.txt-bestand.</span><span class="sxs-lookup"><span data-stu-id="3c35a-173">The first command creates a new **PSSession** on each of the computers listed in the Servers.txt file.</span></span> <span data-ttu-id="3c35a-174">De cmdlet wordt gebruikt `New-PSSession` om de **PSSession** te maken.</span><span class="sxs-lookup"><span data-stu-id="3c35a-174">It uses the `New-PSSession` cmdlet to create the **PSSession**.</span></span> <span data-ttu-id="3c35a-175">De waarde van de para meter **ComputerName** is een opdracht die gebruikmaakt `Get-Content` van de cmdlet om de lijst met computer namen op te halen in het Servers.txt-bestand.</span><span class="sxs-lookup"><span data-stu-id="3c35a-175">The value of the **ComputerName** parameter is a command that uses the `Get-Content` cmdlet to get the list of computer names the Servers.txt file.</span></span>

<span data-ttu-id="3c35a-176">De opdracht gebruikt de para meter **Credential** om de **PSSession** -objecten te maken die de machtiging van een domein beheerder hebben en de para meter **ThrottleLimit** wordt gebruikt om de opdracht te beperken tot 16 gelijktijdige verbindingen.</span><span class="sxs-lookup"><span data-stu-id="3c35a-176">The command uses the **Credential** parameter to create the **PSSession** objects that have the permission of a domain administrator, and it uses the **ThrottleLimit** parameter to limit the command to 16 concurrent connections.</span></span> <span data-ttu-id="3c35a-177">Met de opdracht worden de **PSSession** -objecten in de `$s` variabele opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="3c35a-177">The command saves the **PSSession** objects in the `$s` variable.</span></span>

<span data-ttu-id="3c35a-178">De tweede opdracht maakt gebruik van de para meter **AsJob** van de `Invoke-Command` cmdlet om een achtergrond taak te starten die een `Get-Process PowerShell` opdracht uitvoert in elk van de **PSSession** -objecten in `$s` .</span><span class="sxs-lookup"><span data-stu-id="3c35a-178">The second command uses the **AsJob** parameter of the `Invoke-Command` cmdlet to start a background job that runs a `Get-Process PowerShell` command in each of the **PSSession** objects in `$s`.</span></span>

<span data-ttu-id="3c35a-179">Zie [about_Jobs](About/about_Jobs.md) en [about_Remote_Jobs](About/about_Remote_Jobs.md)voor meer informatie over Power shell-achtergrond taken.</span><span class="sxs-lookup"><span data-stu-id="3c35a-179">For more information about PowerShell background jobs, see [about_Jobs](About/about_Jobs.md) and [about_Remote_Jobs](About/about_Remote_Jobs.md).</span></span>

### <span data-ttu-id="3c35a-180">Voor beeld 10: een sessie maken voor een computer met behulp van de bijbehorende URI</span><span class="sxs-lookup"><span data-stu-id="3c35a-180">Example 10: Create a session for a computer by using its URI</span></span>

```powershell
New-PSSession -ConnectionURI https://management.exchangelabs.com/Management
```

<span data-ttu-id="3c35a-181">Met deze opdracht maakt u een **PSSession** -object dat verbinding maakt met een computer die is opgegeven met een URI in plaats van een computer naam.</span><span class="sxs-lookup"><span data-stu-id="3c35a-181">This command creates a **PSSession** objects that connects to a computer that is specified by a URI instead of a computer name.</span></span>

### <span data-ttu-id="3c35a-182">Voor beeld 11: een sessie optie maken</span><span class="sxs-lookup"><span data-stu-id="3c35a-182">Example 11: Create a session option</span></span>

```powershell
$so = New-PSSessionOption -SkipCACheck
New-PSSession -ConnectionUri https://management.exchangelabs.com/Management -SessionOption $so -Credential Server01\Admin01
```

<span data-ttu-id="3c35a-183">In dit voor beeld ziet u hoe u een sessie optie object maakt en hoe u de para meter **SessionOption** .</span><span class="sxs-lookup"><span data-stu-id="3c35a-183">This example shows how to create a session option object and use the **SessionOption** parameter.</span></span>

<span data-ttu-id="3c35a-184">De eerste opdracht gebruikt de `New-PSSessionOption` cmdlet om een sessie optie te maken.</span><span class="sxs-lookup"><span data-stu-id="3c35a-184">The first command uses the `New-PSSessionOption` cmdlet to create a session option.</span></span> <span data-ttu-id="3c35a-185">Hiermee wordt het resulterende **SessionOption** -object in de `$so` variabele opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="3c35a-185">It saves the resulting **SessionOption** object in the `$so` variable.</span></span>

<span data-ttu-id="3c35a-186">Met de tweede opdracht wordt de optie in een nieuwe sessie gebruikt.</span><span class="sxs-lookup"><span data-stu-id="3c35a-186">The second command uses the option in a new session.</span></span> <span data-ttu-id="3c35a-187">De opdracht gebruikt de `New-PSSession` cmdlet om een nieuwe sessie te maken.</span><span class="sxs-lookup"><span data-stu-id="3c35a-187">The command uses the `New-PSSession` cmdlet to create a new session.</span></span> <span data-ttu-id="3c35a-188">De waarde van de para meter SessionOption is het object **SessionOption** in de `$so` variabele.</span><span class="sxs-lookup"><span data-stu-id="3c35a-188">The value of the SessionOption parameter is the **SessionOption** object in the `$so` variable.</span></span>

### <span data-ttu-id="3c35a-189">Voor beeld 12: een sessie maken met SSH</span><span class="sxs-lookup"><span data-stu-id="3c35a-189">Example 12: Create a session using SSH</span></span>

```powershell
New-PSSession -HostName UserA@LinuxServer01
```

<span data-ttu-id="3c35a-190">In dit voor beeld ziet u hoe u een nieuwe **PSSession** maakt met behulp van Secure Shell (SSH).</span><span class="sxs-lookup"><span data-stu-id="3c35a-190">This example shows how to create a new **PSSession** using Secure Shell (SSH).</span></span> <span data-ttu-id="3c35a-191">Als SSH op de externe computer is geconfigureerd om te vragen om wacht woorden, wordt u gevraagd om een wacht woord op te geven.</span><span class="sxs-lookup"><span data-stu-id="3c35a-191">If SSH is configured on the remote computer to prompt for passwords then you will get a password prompt.</span></span> <span data-ttu-id="3c35a-192">Anders moet u gebruikmaken van SSH-sleutel op basis van gebruikers verificatie.</span><span class="sxs-lookup"><span data-stu-id="3c35a-192">Otherwise you will have to use SSH key based user authentication.</span></span>

### <span data-ttu-id="3c35a-193">Voor beeld 13: een sessie maken met SSH en de poort en gebruikers verificatie sleutel opgeven</span><span class="sxs-lookup"><span data-stu-id="3c35a-193">Example 13: Create a session using SSH and specify the port and user authentication key</span></span>

```powershell
New-PSSession -HostName UserA@LinuxServer01:22 -KeyFilePath c:\<path>\userAKey_rsa
```

<span data-ttu-id="3c35a-194">In dit voor beeld ziet u hoe u een **PSSession** maakt met behulp van Secure Shell (SSH).</span><span class="sxs-lookup"><span data-stu-id="3c35a-194">This example shows how to create a **PSSession** using Secure Shell (SSH).</span></span> <span data-ttu-id="3c35a-195">De para meter **poort** wordt gebruikt om de te gebruiken poort op te geven **en de para** meter voor het sleutelpad om een RSA-sleutel op te geven die wordt gebruikt voor het identificeren en verifiëren van de gebruiker op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="3c35a-195">It uses the **Port** parameter to specify the port to use and the **KeyFilePath** parameter to specify an RSA key used to identify and authenticate the user on the remote computer.</span></span>

### <span data-ttu-id="3c35a-196">Voor beeld 14: meerdere sessies maken met SSH</span><span class="sxs-lookup"><span data-stu-id="3c35a-196">Example 14: Create multiple sessions using SSH</span></span>

```powershell
$sshConnections = @{ HostName="WinServer1"; UserName="domain\userA"; KeyFilePath="c:\users\UserA\id_rsa" }, @{ HostName="UserB@LinuxServer5"; KeyFilePath="c:\UserB\<path>\id_rsa" }
New-PSSession -SSHConnection $sshConnections
```

<span data-ttu-id="3c35a-197">In dit voor beeld ziet u hoe u meerdere sessies maakt met behulp van Secure Shell (SSH) en de para meter **SSHConnection** .</span><span class="sxs-lookup"><span data-stu-id="3c35a-197">This example shows how to create multiple sessions using Secure Shell (SSH) and the **SSHConnection** parameter set.</span></span> <span data-ttu-id="3c35a-198">De para meter **SSHConnection** gebruikt een matrix van hash-tabellen die verbindings gegevens voor elke sessie bevatten.</span><span class="sxs-lookup"><span data-stu-id="3c35a-198">The **SSHConnection** parameter takes an array of hash tables that contain connection information for each session.</span></span> <span data-ttu-id="3c35a-199">Houd er rekening mee dat in dit voor beeld moet SSH zijn geconfigureerd voor de externe computers met de doel groep voor verificatie op basis van sleutels.</span><span class="sxs-lookup"><span data-stu-id="3c35a-199">Note that this example requires that the target remote computers have SSH configured to support key based user authentication.</span></span>

## <span data-ttu-id="3c35a-200">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3c35a-200">PARAMETERS</span></span>

### <span data-ttu-id="3c35a-201">-AllowRedirection</span><span class="sxs-lookup"><span data-stu-id="3c35a-201">-AllowRedirection</span></span>

<span data-ttu-id="3c35a-202">Geeft aan dat deze cmdlet omleiding van deze verbinding met een alternatieve URI (Uniform Resource Identifier) mogelijk maakt.</span><span class="sxs-lookup"><span data-stu-id="3c35a-202">Indicates that this cmdlet allows redirection of this connection to an alternate Uniform Resource Identifier (URI).</span></span>

<span data-ttu-id="3c35a-203">Wanneer u de para meter **ConnectionURI** gebruikt, kan de externe bestemming een instructie retour neren die wordt omgeleid naar een andere URI.</span><span class="sxs-lookup"><span data-stu-id="3c35a-203">When you use the **ConnectionURI** parameter, the remote destination can return an instruction to redirect to a different URI.</span></span> <span data-ttu-id="3c35a-204">Standaard worden verbindingen niet door Power shell omgeleid, maar u kunt deze para meter gebruiken om de verbinding te omleiden.</span><span class="sxs-lookup"><span data-stu-id="3c35a-204">By default, PowerShell does not redirect connections, but you can use this parameter to enable it to redirect the connection.</span></span>

<span data-ttu-id="3c35a-205">U kunt ook het aantal keren beperken dat de verbinding wordt omgeleid door de waarde van de **MaximumConnectionRedirectionCount** -sessie optie te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="3c35a-205">You can also limit the number of times the connection is redirected by changing the **MaximumConnectionRedirectionCount** session option value.</span></span> <span data-ttu-id="3c35a-206">Gebruik de para meter **MaximumRedirection** van de `New-PSSessionOption` cmdlet of stel de eigenschap **MaximumConnectionRedirectionCount** van de voorkeurs variabele **$PSSessionOption** in.</span><span class="sxs-lookup"><span data-stu-id="3c35a-206">Use the **MaximumRedirection** parameter of the `New-PSSessionOption` cmdlet or set the **MaximumConnectionRedirectionCount** property of the **$PSSessionOption** preference variable.</span></span> <span data-ttu-id="3c35a-207">De standaard waarde is 5.</span><span class="sxs-lookup"><span data-stu-id="3c35a-207">The default value is 5.</span></span>

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

### <span data-ttu-id="3c35a-208">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="3c35a-208">-ApplicationName</span></span>

<span data-ttu-id="3c35a-209">Hiermee geeft u het segment van de toepassings naam van de verbindings-URI op.</span><span class="sxs-lookup"><span data-stu-id="3c35a-209">Specifies the application name segment of the connection URI.</span></span> <span data-ttu-id="3c35a-210">Gebruik deze para meter om de naam van de toepassing op te geven wanneer u de para meter **ConnectionURI** niet gebruikt in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="3c35a-210">Use this parameter to specify the application name when you are not using the **ConnectionURI** parameter in the command.</span></span>

<span data-ttu-id="3c35a-211">De standaard waarde is de waarde van de `$PSSessionApplicationName` Voorkeurs variabele op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="3c35a-211">The default value is the value of the `$PSSessionApplicationName` preference variable on the local computer.</span></span> <span data-ttu-id="3c35a-212">Als deze voorkeurs variabele niet is gedefinieerd, is de standaard waarde WSMAN.</span><span class="sxs-lookup"><span data-stu-id="3c35a-212">If this preference variable is not defined, the default value is WSMAN.</span></span> <span data-ttu-id="3c35a-213">Deze waarde is geschikt voor de meeste toepassingen.</span><span class="sxs-lookup"><span data-stu-id="3c35a-213">This value is appropriate for most uses.</span></span> <span data-ttu-id="3c35a-214">Zie [about_Preference_Variables](About/about_Preference_Variables.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="3c35a-214">For more information, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="3c35a-215">De WinRM-service gebruikt de naam van de toepassing om een listener te selecteren om de verbindings aanvraag te onderhouden.</span><span class="sxs-lookup"><span data-stu-id="3c35a-215">The WinRM service uses the application name to select a listener to service the connection request.</span></span>
<span data-ttu-id="3c35a-216">De waarde van deze para meter moet overeenkomen met de waarde van de eigenschap **URLPrefix** van een listener op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="3c35a-216">The value of this parameter should match the value of the **URLPrefix** property of a listener on the remote computer.</span></span>

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

### <span data-ttu-id="3c35a-217">-Verificatie</span><span class="sxs-lookup"><span data-stu-id="3c35a-217">-Authentication</span></span>

<span data-ttu-id="3c35a-218">Hiermee geeft u het mechanisme op dat wordt gebruikt om de referenties van de gebruiker te verifiëren.</span><span class="sxs-lookup"><span data-stu-id="3c35a-218">Specifies the mechanism that is used to authenticate the user's credentials.</span></span>
<span data-ttu-id="3c35a-219">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="3c35a-219">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="3c35a-220">Standaard</span><span class="sxs-lookup"><span data-stu-id="3c35a-220">Default</span></span>
- <span data-ttu-id="3c35a-221">Basic</span><span class="sxs-lookup"><span data-stu-id="3c35a-221">Basic</span></span>
- <span data-ttu-id="3c35a-222">CredSSP</span><span class="sxs-lookup"><span data-stu-id="3c35a-222">Credssp</span></span>
- <span data-ttu-id="3c35a-223">Samenvatting</span><span class="sxs-lookup"><span data-stu-id="3c35a-223">Digest</span></span>
- <span data-ttu-id="3c35a-224">Kerberos</span><span class="sxs-lookup"><span data-stu-id="3c35a-224">Kerberos</span></span>
- <span data-ttu-id="3c35a-225">Negotiate</span><span class="sxs-lookup"><span data-stu-id="3c35a-225">Negotiate</span></span>
- <span data-ttu-id="3c35a-226">NegotiateWithImplicitCredential</span><span class="sxs-lookup"><span data-stu-id="3c35a-226">NegotiateWithImplicitCredential</span></span>

<span data-ttu-id="3c35a-227">De standaard waarde is standaard.</span><span class="sxs-lookup"><span data-stu-id="3c35a-227">The default value is Default.</span></span>

<span data-ttu-id="3c35a-228">Zie [AuthenticationMechanism Enumeration (Engelstalig)](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)voor meer informatie over de waarden van deze para meter.</span><span class="sxs-lookup"><span data-stu-id="3c35a-228">For more information about the values of this parameter, see [AuthenticationMechanism Enumeration](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!CAUTION]
> <span data-ttu-id="3c35a-229">CredSSP-verificatie (Credential Security Support Provider), waarbij de gebruikers referenties worden door gegeven aan een externe computer die moet worden geverifieerd, is ontworpen voor opdrachten waarvoor verificatie is vereist voor meer dan één bron, zoals het openen van een externe netwerk share.</span><span class="sxs-lookup"><span data-stu-id="3c35a-229">Credential Security Support Provider (CredSSP) authentication, in which the user credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="3c35a-230">Dit mechanisme verhoogt het beveiligings risico van de externe bewerking.</span><span class="sxs-lookup"><span data-stu-id="3c35a-230">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="3c35a-231">Als er is geknoeid met de externe computer, kunnen de referenties die aan worden door gegeven, worden gebruikt om de netwerk sessie te beheren.</span><span class="sxs-lookup"><span data-stu-id="3c35a-231">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

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

### <span data-ttu-id="3c35a-232">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="3c35a-232">-CertificateThumbprint</span></span>

<span data-ttu-id="3c35a-233">Hiermee geeft u het digitale open bare-sleutel certificaat (x509) op van een gebruikers account dat is gemachtigd om deze actie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="3c35a-233">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span> <span data-ttu-id="3c35a-234">Voer de vinger afdruk van het certificaat in.</span><span class="sxs-lookup"><span data-stu-id="3c35a-234">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="3c35a-235">Certificaten worden gebruikt in authenticatie op basis van client certificaten.</span><span class="sxs-lookup"><span data-stu-id="3c35a-235">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="3c35a-236">Ze kunnen alleen worden toegewezen aan lokale gebruikers accounts. ze werken niet met domein accounts.</span><span class="sxs-lookup"><span data-stu-id="3c35a-236">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="3c35a-237">Als u een certificaat wilt ophalen, gebruikt u de `Get-Item` of- `Get-ChildItem` opdracht in het Power shell-certificaat: station.</span><span class="sxs-lookup"><span data-stu-id="3c35a-237">To get a certificate, use the `Get-Item` or `Get-ChildItem` command in the PowerShell Cert: drive.</span></span>

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

### <span data-ttu-id="3c35a-238">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="3c35a-238">-ComputerName</span></span>

<span data-ttu-id="3c35a-239">Hiermee geeft u een matrix met namen van computers op.</span><span class="sxs-lookup"><span data-stu-id="3c35a-239">Specifies an array of names of computers.</span></span> <span data-ttu-id="3c35a-240">Met deze cmdlet wordt een permanente verbinding (**PSSession**) gemaakt met de opgegeven computer.</span><span class="sxs-lookup"><span data-stu-id="3c35a-240">This cmdlet creates a persistent connection (**PSSession**) to the specified computer.</span></span> <span data-ttu-id="3c35a-241">Als u meerdere computer namen opgeeft, `New-PSSession` maakt meerdere **PSSession** -objecten, één voor elke computer.</span><span class="sxs-lookup"><span data-stu-id="3c35a-241">If you enter multiple computer names, `New-PSSession` creates multiple **PSSession** objects, one for each computer.</span></span> <span data-ttu-id="3c35a-242">Standaard is dit de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="3c35a-242">The default is the local computer.</span></span>

<span data-ttu-id="3c35a-243">Typ de NetBIOS-naam, een IP-adres of een Fully Qualified Domain Name van een of meer externe computers.</span><span class="sxs-lookup"><span data-stu-id="3c35a-243">Type the NetBIOS name, an IP address, or a fully qualified domain name of one or more remote computers.</span></span> <span data-ttu-id="3c35a-244">Typ de computer naam, localhost of een punt (.) om de lokale computer op te geven.</span><span class="sxs-lookup"><span data-stu-id="3c35a-244">To specify the local computer, type the computer name, localhost, or a dot (.).</span></span> <span data-ttu-id="3c35a-245">Wanneer de computer zich in een ander domein bevindt dan de gebruiker, is de Fully Qualified Domain Name vereist.</span><span class="sxs-lookup"><span data-stu-id="3c35a-245">When the computer is in a different domain than the user, the fully qualified domain name is required.</span></span> <span data-ttu-id="3c35a-246">U kunt ook een computer naam (tussen aanhalings tekens) door sluizen naar `New-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="3c35a-246">You can also pipe a computer name, in quotation marks, to `New-PSSession`.</span></span>

<span data-ttu-id="3c35a-247">Als u een IP-adres wilt gebruiken in de waarde van de para meter **ComputerName** , moet de opdracht de para meter **Credential** bevatten.</span><span class="sxs-lookup"><span data-stu-id="3c35a-247">To use an IP address in the value of the **ComputerName** parameter, the command must include the **Credential** parameter.</span></span> <span data-ttu-id="3c35a-248">De computer moet ook worden geconfigureerd voor HTTPS-Trans Port of het IP-adres van de externe computer moet worden opgenomen in de WinRM TrustedHosts-lijst op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="3c35a-248">Also, the computer must be configured for HTTPS transport or the IP address of the remote computer must be included in the WinRM TrustedHosts list on the local computer.</span></span> <span data-ttu-id="3c35a-249">Zie "een computer toevoegen aan de lijst met vertrouwde hosts" in [about_Remote_Troubleshooting](about/about_Remote_Troubleshooting.md)voor instructies voor het toevoegen van een computer naam aan de lijst TrustedHosts.</span><span class="sxs-lookup"><span data-stu-id="3c35a-249">For instructions for adding a computer name to the TrustedHosts list, see "How to Add a Computer to the Trusted Host List" in [about_Remote_Troubleshooting](about/about_Remote_Troubleshooting.md).</span></span>

<span data-ttu-id="3c35a-250">Als u de lokale computer in de waarde van de para meter **ComputerName** wilt gebruiken, start u Windows Power shell met de optie als administrator uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="3c35a-250">To include the local computer in the value of the **ComputerName** parameter, start Windows PowerShell by using the Run as administrator option.</span></span>

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

### <span data-ttu-id="3c35a-251">-Configuratiepad</span><span class="sxs-lookup"><span data-stu-id="3c35a-251">-ConfigurationName</span></span>

<span data-ttu-id="3c35a-252">Hiermee geeft u de sessie configuratie op die wordt gebruikt voor de nieuwe **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="3c35a-252">Specifies the session configuration that is used for the new **PSSession**.</span></span>

<span data-ttu-id="3c35a-253">Voer een configuratie naam of de volledig gekwalificeerde resource-URI in voor een sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="3c35a-253">Enter a configuration name or the fully qualified resource URI for a session configuration.</span></span> <span data-ttu-id="3c35a-254">Als u alleen de configuratie naam opgeeft, wordt de volgende schema-URI voor voegsel: `http://schemas.microsoft.com/PowerShell` .</span><span class="sxs-lookup"><span data-stu-id="3c35a-254">If you specify only the configuration name, the following schema URI is prepended: `http://schemas.microsoft.com/PowerShell`.</span></span>

<span data-ttu-id="3c35a-255">De sessie configuratie voor een sessie bevindt zich op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="3c35a-255">The session configuration for a session is located on the remote computer.</span></span> <span data-ttu-id="3c35a-256">Als de opgegeven sessie configuratie niet bestaat op de externe computer, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="3c35a-256">If the specified session configuration does not exist on the remote computer, the command fails.</span></span>

<span data-ttu-id="3c35a-257">De standaard waarde is de waarde van de `$PSSessionConfigurationName` Voorkeurs variabele op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="3c35a-257">The default value is the value of the `$PSSessionConfigurationName` preference variable on the local computer.</span></span> <span data-ttu-id="3c35a-258">Als deze voorkeurs variabele niet is ingesteld, is de standaard instelling micro soft. Power shell.</span><span class="sxs-lookup"><span data-stu-id="3c35a-258">If this preference variable is not set, the default is Microsoft.PowerShell.</span></span> <span data-ttu-id="3c35a-259">Zie [about_Preference_Variables](About/about_Preference_Variables.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="3c35a-259">For more information, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

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

### <span data-ttu-id="3c35a-260">-ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="3c35a-260">-ConnectionUri</span></span>

<span data-ttu-id="3c35a-261">Hiermee geeft u een URI op die het verbindings eindpunt voor de sessie definieert.</span><span class="sxs-lookup"><span data-stu-id="3c35a-261">Specifies a URI that defines the connection endpoint for the session.</span></span> <span data-ttu-id="3c35a-262">De URI moet volledig gekwalificeerd zijn.</span><span class="sxs-lookup"><span data-stu-id="3c35a-262">The URI must be fully qualified.</span></span> <span data-ttu-id="3c35a-263">De indeling van deze teken reeks is als volgt:</span><span class="sxs-lookup"><span data-stu-id="3c35a-263">The format of this string is as follows:</span></span>

`<Transport>://<ComputerName>:<Port>/<ApplicationName>`

<span data-ttu-id="3c35a-264">De standaard waarde is als volgt:</span><span class="sxs-lookup"><span data-stu-id="3c35a-264">The default value is as follows:</span></span>

`http://localhost:5985/WSMAN`

<span data-ttu-id="3c35a-265">Als u geen **ConnectionURI** opgeeft, kunt u de para meters **UseSSL**, **ComputerName**, **Port** en **ApplicationName** gebruiken om de **ConnectionURI** -waarden op te geven.</span><span class="sxs-lookup"><span data-stu-id="3c35a-265">If you do not specify a **ConnectionURI**, you can use the **UseSSL**, **ComputerName**, **Port**, and **ApplicationName** parameters to specify the **ConnectionURI** values.</span></span>

<span data-ttu-id="3c35a-266">Geldige waarden voor het transport segment van de URI zijn HTTP en HTTPS.</span><span class="sxs-lookup"><span data-stu-id="3c35a-266">Valid values for the Transport segment of the URI are HTTP and HTTPS.</span></span> <span data-ttu-id="3c35a-267">Als u een verbindings-URI met een transport segment opgeeft, maar geen poort opgeeft, wordt de sessie gemaakt met standaard poorten: 80 voor HTTP en 443 voor HTTPS.</span><span class="sxs-lookup"><span data-stu-id="3c35a-267">If you specify a connection URI with a Transport segment, but do not specify a port, the session is created with standards ports: 80 for HTTP and 443 for HTTPS.</span></span> <span data-ttu-id="3c35a-268">Als u de standaard poorten voor externe communicatie van Power shell wilt gebruiken, geeft u poort 5985 voor HTTP of 5986 op voor HTTPS.</span><span class="sxs-lookup"><span data-stu-id="3c35a-268">To use the default ports for PowerShell remoting, specify port 5985 for HTTP or 5986 for HTTPS.</span></span>

<span data-ttu-id="3c35a-269">Als de doel computer de verbinding omleidt naar een andere URI, wordt de omleiding door Power shell voor komen, tenzij u de para meter **AllowRedirection** in de opdracht gebruikt.</span><span class="sxs-lookup"><span data-stu-id="3c35a-269">If the destination computer redirects the connection to a different URI, PowerShell prevents the redirection unless you use the **AllowRedirection** parameter in the command.</span></span>

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

### <span data-ttu-id="3c35a-270">-ContainerId</span><span class="sxs-lookup"><span data-stu-id="3c35a-270">-ContainerId</span></span>

<span data-ttu-id="3c35a-271">Hiermee geeft u een matrix met Id's van containers op.</span><span class="sxs-lookup"><span data-stu-id="3c35a-271">Specifies an array of IDs of containers.</span></span> <span data-ttu-id="3c35a-272">Met deze cmdlet wordt een interactieve sessie gestart met elk van de opgegeven containers.</span><span class="sxs-lookup"><span data-stu-id="3c35a-272">This cmdlet starts an interactive session with each of the specified containers.</span></span> <span data-ttu-id="3c35a-273">Gebruik de `docker ps` opdracht om een lijst met container-id's op te halen.</span><span class="sxs-lookup"><span data-stu-id="3c35a-273">Use the `docker ps` command to get a list of container IDs.</span></span> <span data-ttu-id="3c35a-274">Zie de Help voor de opdracht [docker PS](https://docs.docker.com/engine/reference/commandline/ps/) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="3c35a-274">For more information, see the help for the [docker ps](https://docs.docker.com/engine/reference/commandline/ps/) command.</span></span>

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

### <span data-ttu-id="3c35a-275">-Credential</span><span class="sxs-lookup"><span data-stu-id="3c35a-275">-Credential</span></span>

<span data-ttu-id="3c35a-276">Hiermee geeft u een gebruikers account op dat gemachtigd is om deze actie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="3c35a-276">Specifies a user account that has permission to do this action.</span></span> <span data-ttu-id="3c35a-277">Standaard is dit de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="3c35a-277">The default is the current user.</span></span>

<span data-ttu-id="3c35a-278">Typ een gebruikers naam, zoals **gebruiker01** of **Domain01\User01**, of voer een **PSCredential** -object in dat door de cmdlet wordt gegenereerd `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="3c35a-278">Type a user name, such as **User01** or **Domain01\User01**, or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="3c35a-279">Als u een gebruikers naam typt, wordt u gevraagd het wacht woord in te voeren.</span><span class="sxs-lookup"><span data-stu-id="3c35a-279">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="3c35a-280">Referenties worden opgeslagen in een [PSCredential](/dotnet/api/system.management.automation.pscredential) -object en het wacht woord wordt opgeslagen als [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="3c35a-280">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="3c35a-281">Zie [Hoe veilig is securestring?](/dotnet/api/system.security.securestring#how-secure-is-securestring)voor meer informatie over **securestring** Data Protection.</span><span class="sxs-lookup"><span data-stu-id="3c35a-281">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="3c35a-282">-EnableNetworkAccess</span><span class="sxs-lookup"><span data-stu-id="3c35a-282">-EnableNetworkAccess</span></span>

<span data-ttu-id="3c35a-283">Geeft aan dat met deze cmdlet een interactief beveiligings token wordt toegevoegd aan loop Back-sessies.</span><span class="sxs-lookup"><span data-stu-id="3c35a-283">Indicates that this cmdlet adds an interactive security token to loopback sessions.</span></span> <span data-ttu-id="3c35a-284">Met het interactieve token kunt u opdrachten uitvoeren in de loop back-sessie die gegevens van andere computers ophalen.</span><span class="sxs-lookup"><span data-stu-id="3c35a-284">The interactive token lets you run commands in the loopback session that get data from other computers.</span></span> <span data-ttu-id="3c35a-285">U kunt bijvoorbeeld een opdracht uitvoeren in de sessie waarmee XML-bestanden van een externe computer naar de lokale computer worden gekopieerd.</span><span class="sxs-lookup"><span data-stu-id="3c35a-285">For example, you can run a command in the session that copies XML files from a remote computer to the local computer.</span></span>

<span data-ttu-id="3c35a-286">Een loop back-sessie is een **PSSession** die afkomstig is van en eindigt op dezelfde computer.</span><span class="sxs-lookup"><span data-stu-id="3c35a-286">A loopback session is a **PSSession** that originates and ends on the same computer.</span></span> <span data-ttu-id="3c35a-287">Als u een loop back-sessie wilt maken, laat u de para meter **ComputerName** weg of stelt u de waarde in op punt (.), localhost of de naam van de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="3c35a-287">To create a loopback session, omit the **ComputerName** parameter or set its value to dot (.), localhost, or the name of the local computer.</span></span>

<span data-ttu-id="3c35a-288">Met deze cmdlet worden standaard loop Back-sessies gemaakt met behulp van een netwerk token, dat mogelijk niet voldoende machtigingen biedt om te verifiëren bij externe computers.</span><span class="sxs-lookup"><span data-stu-id="3c35a-288">By default, this cmdlet creates loopback sessions by using a network token, which might not provide sufficient permission to authenticate to remote computers.</span></span>

<span data-ttu-id="3c35a-289">De para meter **EnableNetworkAccess** is alleen effectief in loop Back-sessies.</span><span class="sxs-lookup"><span data-stu-id="3c35a-289">The **EnableNetworkAccess** parameter is effective only in loopback sessions.</span></span> <span data-ttu-id="3c35a-290">Als u **EnableNetworkAccess** gebruikt wanneer u een sessie op een externe computer maakt, mislukt de opdracht, maar wordt de para meter genegeerd.</span><span class="sxs-lookup"><span data-stu-id="3c35a-290">If you use **EnableNetworkAccess** when you create a session on a remote computer, the command succeeds, but the parameter is ignored.</span></span>

<span data-ttu-id="3c35a-291">U kunt ook externe toegang inschakelen in een loop back-sessie met behulp van de CredSSP-waarde van de para meter **Authentication** , waarmee de sessie referenties worden overgedragen aan andere computers.</span><span class="sxs-lookup"><span data-stu-id="3c35a-291">You can also enable remote access in a loopback session by using the CredSSP value of the **Authentication** parameter, which delegates the session credentials to other computers.</span></span>

<span data-ttu-id="3c35a-292">Om de computer te beschermen tegen kwaad aardige toegang, kunnen niet-verbonden loop Back-sessies met interactieve tokens, die zijn gemaakt met behulp van de para meter **EnableNetworkAccess** , alleen opnieuw worden aangesloten op de computer waarop de sessie is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="3c35a-292">To protect the computer from malicious access, disconnected loopback sessions that have interactive tokens, which are those created by using the **EnableNetworkAccess** parameter, can be reconnected only from the computer on which the session was created.</span></span> <span data-ttu-id="3c35a-293">Verbroken sessies die gebruikmaken van CredSSP-verificatie, kunnen opnieuw worden aangesloten op andere computers.</span><span class="sxs-lookup"><span data-stu-id="3c35a-293">Disconnected sessions that use CredSSP authentication can be reconnected from other computers.</span></span> <span data-ttu-id="3c35a-294">Voor meer informatie raadpleegt u `Disconnect-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="3c35a-294">For more information, see `Disconnect-PSSession`.</span></span>

<span data-ttu-id="3c35a-295">Deze para meter is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="3c35a-295">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="3c35a-296">-Hostnaam</span><span class="sxs-lookup"><span data-stu-id="3c35a-296">-HostName</span></span>

<span data-ttu-id="3c35a-297">Hiermee geeft u een matrix van computer namen voor een verbinding op basis van SSH (Secure Shell).</span><span class="sxs-lookup"><span data-stu-id="3c35a-297">Specifies an array of computer names for a Secure Shell (SSH) based connection.</span></span> <span data-ttu-id="3c35a-298">Dit is vergelijkbaar met de para meter ComputerName, behalve dat de verbinding met de externe computer wordt gemaakt met behulp van SSH in plaats van Windows WinRM.</span><span class="sxs-lookup"><span data-stu-id="3c35a-298">This is similar to the ComputerName parameter except that the connection to the remote computer is made using SSH rather than Windows WinRM.</span></span>

<span data-ttu-id="3c35a-299">Deze para meter is geïntroduceerd in Power shell 6,0.</span><span class="sxs-lookup"><span data-stu-id="3c35a-299">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.String[]
Parameter Sets: SSHHost
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3c35a-300">-Bestandspad</span><span class="sxs-lookup"><span data-stu-id="3c35a-300">-KeyFilePath</span></span>

<span data-ttu-id="3c35a-301">Hiermee geeft u een pad naar een sleutel bestand dat door een Secure Shell (SSH) wordt gebruikt om een gebruiker op een externe computer te verifiëren.</span><span class="sxs-lookup"><span data-stu-id="3c35a-301">Specifies a key file path used by Secure Shell (SSH) to authenticate a user on a remote computer.</span></span>

<span data-ttu-id="3c35a-302">Met SSH kan gebruikers verificatie worden uitgevoerd via persoonlijke/open bare sleutels als alternatief voor de basis wachtwoord verificatie.</span><span class="sxs-lookup"><span data-stu-id="3c35a-302">SSH allows user authentication to be performed via private/public keys as an alternative to basic password authentication.</span></span> <span data-ttu-id="3c35a-303">Als de externe computer is geconfigureerd voor sleutel verificatie, kan deze para meter worden gebruikt om de sleutel op te geven waarmee de gebruiker wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="3c35a-303">If the remote computer is configured for key authentication then this parameter can be used to provide the key that identifies the user.</span></span>

<span data-ttu-id="3c35a-304">Deze para meter is geïntroduceerd in Power shell 6,0.</span><span class="sxs-lookup"><span data-stu-id="3c35a-304">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.String
Parameter Sets: SSHHost
Aliases: IdentityFilePath

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3c35a-305">-Name</span><span class="sxs-lookup"><span data-stu-id="3c35a-305">-Name</span></span>

<span data-ttu-id="3c35a-306">Hiermee geeft u een beschrijvende naam op voor de **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="3c35a-306">Specifies a friendly name for the **PSSession**.</span></span>

<span data-ttu-id="3c35a-307">U kunt de naam gebruiken om te verwijzen naar de **PSSession** wanneer u andere cmdlets gebruikt, zoals `Get-PSSession` en `Enter-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="3c35a-307">You can use the name to refer to the **PSSession** when you use other cmdlets, such as `Get-PSSession` and `Enter-PSSession`.</span></span> <span data-ttu-id="3c35a-308">De naam hoeft niet uniek te zijn voor de computer of de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="3c35a-308">The name is not required to be unique to the computer or the current session.</span></span>

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

### <span data-ttu-id="3c35a-309">-Port</span><span class="sxs-lookup"><span data-stu-id="3c35a-309">-Port</span></span>

<span data-ttu-id="3c35a-310">Hiermee geeft u de netwerk poort op de externe computer op die voor deze verbinding wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="3c35a-310">Specifies the network port on the remote computer that is used for this connection.</span></span> <span data-ttu-id="3c35a-311">Als u verbinding wilt maken met een externe computer, moet op de externe computer worden geluisterd op de poort die door de verbinding wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="3c35a-311">To connect to a remote computer, the remote computer must be listening on the port that the connection uses.</span></span> <span data-ttu-id="3c35a-312">De standaard poorten zijn 5985, de WinRM-poort voor HTTP en 5986, de WinRM-poort voor HTTPS.</span><span class="sxs-lookup"><span data-stu-id="3c35a-312">The default ports are 5985, which is the WinRM port for HTTP, and 5986, which is the WinRM port for HTTPS.</span></span>

<span data-ttu-id="3c35a-313">Voordat u een andere poort gebruikt, moet u de WinRM-listener op de externe computer configureren om op die poort te Luis teren.</span><span class="sxs-lookup"><span data-stu-id="3c35a-313">Before using another port, you must configure the WinRM listener on the remote computer to listen at that port.</span></span> <span data-ttu-id="3c35a-314">Gebruik de volgende opdrachten om de listener te configureren:</span><span class="sxs-lookup"><span data-stu-id="3c35a-314">Use the following commands to configure the listener:</span></span>

1. `winrm delete winrm/config/listener?Address=*+Transport=HTTP`
2. `winrm create winrm/config/listener?Address=*+Transport=HTTP @{Port="\<port-number\>"}`

<span data-ttu-id="3c35a-315">Gebruik de para meter **poort** alleen als dat nodig is.</span><span class="sxs-lookup"><span data-stu-id="3c35a-315">Do not use the **Port** parameter unless you must.</span></span> <span data-ttu-id="3c35a-316">De poort instelling in de opdracht is van toepassing op alle computers of sessies waarop de opdracht wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="3c35a-316">The port setting in the command applies to all computers or sessions on which the command runs.</span></span> <span data-ttu-id="3c35a-317">Een alternatieve poort instelling kan verhinderen dat de opdracht wordt uitgevoerd op alle computers.</span><span class="sxs-lookup"><span data-stu-id="3c35a-317">An alternate port setting might prevent the command from running on all computers.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ComputerName, SSHHost
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3c35a-318">-RunAsAdministrator</span><span class="sxs-lookup"><span data-stu-id="3c35a-318">-RunAsAdministrator</span></span>

<span data-ttu-id="3c35a-319">Geeft aan dat de **PSSession** wordt uitgevoerd als beheerder.</span><span class="sxs-lookup"><span data-stu-id="3c35a-319">Indicates that the **PSSession** runs as administrator.</span></span>

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

### <span data-ttu-id="3c35a-320">-Sessie</span><span class="sxs-lookup"><span data-stu-id="3c35a-320">-Session</span></span>

<span data-ttu-id="3c35a-321">Hiermee geeft u een matrix met **PSSession** -objecten op die met deze cmdlet als model voor de nieuwe **PSSession** wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="3c35a-321">Specifies an array of **PSSession** objects that this cmdlet uses as a model for the new **PSSession**.</span></span> <span data-ttu-id="3c35a-322">Met deze para meter maakt u nieuwe **PSSession** -objecten die dezelfde eigenschappen hebben als de opgegeven **PSSession** -objecten.</span><span class="sxs-lookup"><span data-stu-id="3c35a-322">This parameter creates new **PSSession** objects that have the same properties as the specified **PSSession** objects.</span></span>

<span data-ttu-id="3c35a-323">Voer een variabele in die de **PSSession** -objecten bevat of een opdracht waarmee de **PSSession** -objecten, zoals een of-opdracht, worden gemaakt of opgehaald `New-PSSession` `Get-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="3c35a-323">Enter a variable that contains the **PSSession** objects or a command that creates or gets the **PSSession** objects, such as a `New-PSSession` or `Get-PSSession` command.</span></span>

<span data-ttu-id="3c35a-324">De resulterende **PSSession** -objecten hebben dezelfde computer naam, toepassings naam, VERBINDINGS-URI, poort, configuratie naam, beperkings limiet en Secure Sockets Layer (SSL) als de oorspronkelijke waarden, maar ze hebben een andere weergave naam, id en exemplaar-id (GUID).</span><span class="sxs-lookup"><span data-stu-id="3c35a-324">The resulting **PSSession** objects have the same computer name, application name, connection URI, port, configuration name, throttle limit, and Secure Sockets Layer (SSL) value as the originals, but they have a different display name, ID, and instance ID (GUID).</span></span>

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

### <span data-ttu-id="3c35a-325">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="3c35a-325">-SessionOption</span></span>

<span data-ttu-id="3c35a-326">Hiermee geeft u geavanceerde opties voor de sessie op.</span><span class="sxs-lookup"><span data-stu-id="3c35a-326">Specifies advanced options for the session.</span></span> <span data-ttu-id="3c35a-327">Voer een **SessionOption** -object in, zoals het, dat u maakt met behulp van de `New-PSSessionOption` cmdlet of een hash-tabel waarin de sleutels de naam van de sessie optie zijn en de waarden voor de waarden van de sessie.</span><span class="sxs-lookup"><span data-stu-id="3c35a-327">Enter a **SessionOption** object, such as one that you create by using the `New-PSSessionOption` cmdlet, or a hash table in which the keys are session option names and the values are session option values.</span></span>

<span data-ttu-id="3c35a-328">De standaard waarden voor de opties worden bepaald door de waarde van de `$PSSessionOption` Voorkeurs variabele, als deze is ingesteld.</span><span class="sxs-lookup"><span data-stu-id="3c35a-328">The default values for the options are determined by the value of the `$PSSessionOption` preference variable, if it is set.</span></span> <span data-ttu-id="3c35a-329">Anders worden de standaard waarden bepaald door opties die zijn ingesteld in de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="3c35a-329">Otherwise, the default values are established by options set in the session configuration.</span></span>

<span data-ttu-id="3c35a-330">De waarden van de sessie optie hebben voor rang op de standaard waarden voor sessies die zijn ingesteld in de `$PSSessionOption` Voorkeurs variabele en in de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="3c35a-330">The session option values take precedence over default values for sessions set in the `$PSSessionOption` preference variable and in the session configuration.</span></span> <span data-ttu-id="3c35a-331">Ze hebben echter geen voor rang op de maximum waarden, quota's of limieten die zijn ingesteld in de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="3c35a-331">However, they do not take precedence over maximum values, quotas or limits set in the session configuration.</span></span>

<span data-ttu-id="3c35a-332">Zie voor een beschrijving van de sessie opties die de standaard waarden bevatten `New-PSSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="3c35a-332">For a description of the session options that includes the default values, see `New-PSSessionOption`.</span></span> <span data-ttu-id="3c35a-333">Zie about_Preference_Variables voor meer informatie over de `$PSSessionOption` voorkeurs [](About/about_Preference_Variables.md)variabele.</span><span class="sxs-lookup"><span data-stu-id="3c35a-333">For information about the `$PSSessionOption` preference variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span> <span data-ttu-id="3c35a-334">Zie [about_Session_Configurations](About/about_Session_Configurations.md) (Engelstalig) voor meer informatie over sessieconfiguraties.</span><span class="sxs-lookup"><span data-stu-id="3c35a-334">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

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

### <span data-ttu-id="3c35a-335">-SSHConnection</span><span class="sxs-lookup"><span data-stu-id="3c35a-335">-SSHConnection</span></span>

<span data-ttu-id="3c35a-336">Deze para meter gebruikt een matrix met hashtabellen waarbij elke hashtabel een of meer verbindings parameters bevat die nodig zijn om een SSH-verbinding (Secure Shell) tot stand te brengen (hostnaam, poort, gebruikers naam, FilePath).</span><span class="sxs-lookup"><span data-stu-id="3c35a-336">This parameter takes an array of hashtables where each hashtable contains one or more connection parameters needed to establish a Secure Shell (SSH) connection (HostName, Port, UserName, KeyFilePath).</span></span>

<span data-ttu-id="3c35a-337">De para meters voor de hashtabel-verbinding zijn hetzelfde als die voor de para meter van de **hostnaam** zijn ingesteld.</span><span class="sxs-lookup"><span data-stu-id="3c35a-337">The hashtable connection parameters are the same as defined for the **HostName** parameter set.</span></span>

<span data-ttu-id="3c35a-338">De **SSHConnection** -para meter is handig voor het maken van meerdere sessies waarbij voor elke sessie verschillende verbindings gegevens zijn vereist.</span><span class="sxs-lookup"><span data-stu-id="3c35a-338">The **SSHConnection** parameter is useful for creating multiple sessions where each session requires different connection information.</span></span>

<span data-ttu-id="3c35a-339">Deze para meter is geïntroduceerd in Power shell 6,0.</span><span class="sxs-lookup"><span data-stu-id="3c35a-339">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Collections.Hashtable[]
Parameter Sets: SSHHostHashParam
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3c35a-340">-SSHTransport</span><span class="sxs-lookup"><span data-stu-id="3c35a-340">-SSHTransport</span></span>

<span data-ttu-id="3c35a-341">Geeft aan dat de externe verbinding tot stand is gebracht met behulp van Secure Shell (SSH).</span><span class="sxs-lookup"><span data-stu-id="3c35a-341">Indicates that the remote connection is established using Secure Shell (SSH).</span></span>

<span data-ttu-id="3c35a-342">Power Shell maakt standaard gebruik van Windows WinRM om verbinding te maken met een externe computer.</span><span class="sxs-lookup"><span data-stu-id="3c35a-342">By default PowerShell uses Windows WinRM to connect to a remote computer.</span></span> <span data-ttu-id="3c35a-343">Met deze switch wordt Power shell gedwongen de para meter HostName te gebruiken die is ingesteld voor het maken van een externe SSH-verbinding.</span><span class="sxs-lookup"><span data-stu-id="3c35a-343">This switch forces PowerShell to use the HostName parameter set for establishing an SSH based remote connection.</span></span>

<span data-ttu-id="3c35a-344">Deze para meter is geïntroduceerd in Power shell 6,0.</span><span class="sxs-lookup"><span data-stu-id="3c35a-344">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: SSHHost
Aliases:
Accepted values: true

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3c35a-345">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="3c35a-345">-ThrottleLimit</span></span>

<span data-ttu-id="3c35a-346">Hiermee geeft u het maximum aantal gelijktijdige verbindingen op dat tot stand kan worden gebracht om deze opdracht uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="3c35a-346">Specifies the maximum number of concurrent connections that can be established to run this command.</span></span>
<span data-ttu-id="3c35a-347">Als u deze para meter weglaat of een waarde van 0 (nul) opgeeft, wordt de standaard waarde 32 gebruikt.</span><span class="sxs-lookup"><span data-stu-id="3c35a-347">If you omit this parameter or enter a value of 0 (zero), the default value, 32, is used.</span></span>

<span data-ttu-id="3c35a-348">De beperkings limiet geldt alleen voor de huidige opdracht, niet voor de sessie of voor de computer.</span><span class="sxs-lookup"><span data-stu-id="3c35a-348">The throttle limit applies only to the current command, not to the session or to the computer.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ComputerName, Uri, VMId, VMName, Session, ContainerId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3c35a-349">-GebruikersNaam</span><span class="sxs-lookup"><span data-stu-id="3c35a-349">-UserName</span></span>

<span data-ttu-id="3c35a-350">Hiermee geeft u de gebruikers naam op voor het account dat wordt gebruikt om een sessie te maken op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="3c35a-350">Specifies the user name for the account used to create a session on the remote computer.</span></span> <span data-ttu-id="3c35a-351">De verificatie methode voor de gebruiker is afhankelijk van hoe Secure Shell (SSH) is geconfigureerd op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="3c35a-351">User authentication method will depend on how Secure Shell (SSH) is configured on the remote computer.</span></span>

<span data-ttu-id="3c35a-352">Als SSH is geconfigureerd voor basis wachtwoord verificatie, wordt u gevraagd om het wacht woord van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="3c35a-352">If SSH is configured for basic password authentication then you will be prompted for the user password.</span></span>

<span data-ttu-id="3c35a-353">Als SSH is geconfigureerd voor sleutel op basis van gebruikers verificatie, kan een pad naar een sleutel bestand worden opgegeven via de para meter voor het sleutelpad en er wordt geen wachtwoord prompt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="3c35a-353">If SSH is configured for key based user authentication then a key file path can be provided via the KeyFilePath parameter and no password prompt will occur.</span></span> <span data-ttu-id="3c35a-354">Houd er rekening mee dat als het sleutel bestand van de client gebruiker zich bevindt op een bekende SSH-locatie, de para meter voor het bestandspad niet nodig is voor op sleutels gebaseerde verificatie en de gebruikers verificatie automatisch wordt uitgevoerd op basis van de gebruikers naam.</span><span class="sxs-lookup"><span data-stu-id="3c35a-354">Note that if the client user key file is located in an SSH known location then the KeyFilePath parameter is not needed for key based authentication, and user authentication will occur automatically based on the user name.</span></span> <span data-ttu-id="3c35a-355">Raadpleeg SSH-documentatie over op sleutels gebaseerde gebruikers verificatie voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="3c35a-355">See SSH documentation about key based user authentication for more information.</span></span>

<span data-ttu-id="3c35a-356">Dit is geen vereiste para meter.</span><span class="sxs-lookup"><span data-stu-id="3c35a-356">This is not a required parameter.</span></span> <span data-ttu-id="3c35a-357">Als er geen UserName-para meter is opgegeven, wordt de naam van de huidige aanmeldings gebruiker gebruikt voor de verbinding.</span><span class="sxs-lookup"><span data-stu-id="3c35a-357">If no UserName parameter is specified then the current log on user name is used for the connection.</span></span>

<span data-ttu-id="3c35a-358">Deze para meter is geïntroduceerd in Power shell 6,0.</span><span class="sxs-lookup"><span data-stu-id="3c35a-358">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.String
Parameter Sets: SSHHost
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3c35a-359">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="3c35a-359">-UseSSL</span></span>

<span data-ttu-id="3c35a-360">Geeft aan dat deze cmdlet het SSL-protocol gebruikt om verbinding te maken met de externe computer.</span><span class="sxs-lookup"><span data-stu-id="3c35a-360">Indicates that this cmdlet uses the SSL protocol to establish a connection to the remote computer.</span></span>
<span data-ttu-id="3c35a-361">Standaard wordt SSL niet gebruikt.</span><span class="sxs-lookup"><span data-stu-id="3c35a-361">By default, SSL is not used.</span></span>

<span data-ttu-id="3c35a-362">WS-Management versleutelt alle Power shell-inhoud die via het netwerk wordt verzonden.</span><span class="sxs-lookup"><span data-stu-id="3c35a-362">WS-Management encrypts all PowerShell content transmitted over the network.</span></span> <span data-ttu-id="3c35a-363">De para meter **UseSSL** biedt een extra beveiliging voor het verzenden van de gegevens via een HTTPS-verbinding in plaats van een http-verbinding.</span><span class="sxs-lookup"><span data-stu-id="3c35a-363">The **UseSSL** parameter offers an additional protection that sends the data across an HTTPS connection instead of an HTTP connection.</span></span>

<span data-ttu-id="3c35a-364">Als u deze para meter gebruikt, maar SSL is niet beschikbaar op de poort die wordt gebruikt voor de opdracht, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="3c35a-364">If you use this parameter, but SSL is not available on the port that is used for the command, the command fails.</span></span>

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

### <span data-ttu-id="3c35a-365">-VMId</span><span class="sxs-lookup"><span data-stu-id="3c35a-365">-VMId</span></span>

<span data-ttu-id="3c35a-366">Hiermee geeft u een ID-matrix van virtuele machines op.</span><span class="sxs-lookup"><span data-stu-id="3c35a-366">Specifies an array of ID of virtual machines.</span></span> <span data-ttu-id="3c35a-367">Met deze cmdlet wordt een interactieve sessie gestart met elk van de opgegeven virtuele machines.</span><span class="sxs-lookup"><span data-stu-id="3c35a-367">This cmdlet starts an interactive session with each of the specified virtual machines.</span></span> <span data-ttu-id="3c35a-368">Als u de virtuele machines wilt zien die voor u beschikbaar zijn, gebruikt u de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="3c35a-368">To see the virtual machines that are available to you, use the following command:</span></span>

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

### <span data-ttu-id="3c35a-369">-VMName</span><span class="sxs-lookup"><span data-stu-id="3c35a-369">-VMName</span></span>

<span data-ttu-id="3c35a-370">Hiermee geeft u een matrix met namen van virtuele machines op.</span><span class="sxs-lookup"><span data-stu-id="3c35a-370">Specifies an array of names of virtual machines.</span></span> <span data-ttu-id="3c35a-371">Met deze cmdlet wordt een interactieve sessie gestart met elk van de opgegeven virtuele machines.</span><span class="sxs-lookup"><span data-stu-id="3c35a-371">This cmdlet starts an interactive session with each of the specified virtual machines.</span></span> <span data-ttu-id="3c35a-372">Gebruik de cmdlet om de virtuele machines weer te geven die voor u beschikbaar zijn `Get-VM` .</span><span class="sxs-lookup"><span data-stu-id="3c35a-372">To see the virtual machines that are available to you, use the `Get-VM` cmdlet.</span></span>

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

### <span data-ttu-id="3c35a-373">-Subsysteem</span><span class="sxs-lookup"><span data-stu-id="3c35a-373">-Subsystem</span></span>

<span data-ttu-id="3c35a-374">Hiermee geeft u het SSH-subsysteem op dat wordt gebruikt voor de nieuwe **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="3c35a-374">Specifies the SSH subsystem used for the new **PSSession**.</span></span>

<span data-ttu-id="3c35a-375">Hiermee geeft u het subsysteem op dat moet worden gebruikt op het doel zoals gedefinieerd in sshd_config.</span><span class="sxs-lookup"><span data-stu-id="3c35a-375">This specifies the subsystem to use on the target as defined in sshd_config.</span></span>
<span data-ttu-id="3c35a-376">Het subsysteem start een specifieke versie van Power shell met vooraf gedefinieerde para meters.</span><span class="sxs-lookup"><span data-stu-id="3c35a-376">The subsystem starts a specific version of PowerShell with predefined parameters.</span></span>
<span data-ttu-id="3c35a-377">Als het opgegeven subsysteem niet bestaat op de externe computer, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="3c35a-377">If the specified subsystem does not exist on the remote computer, the command fails.</span></span>

<span data-ttu-id="3c35a-378">Als deze para meter niet wordt gebruikt, is de standaard het subsysteem Power shell.</span><span class="sxs-lookup"><span data-stu-id="3c35a-378">If this parameter is not used, the default is the 'powershell' subsystem.</span></span>

```yaml
Type: System.String
Parameter Sets: SSHHost
Aliases:

Required: False
Position: Named
Default value: powershell
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="3c35a-379">-UseWindowsPowerShell</span><span class="sxs-lookup"><span data-stu-id="3c35a-379">-UseWindowsPowerShell</span></span>

<span data-ttu-id="3c35a-380">{{Opvulling UseWindowsPowerShell beschrijving}}</span><span class="sxs-lookup"><span data-stu-id="3c35a-380">{{ Fill UseWindowsPowerShell Description }}</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: UseWindowsPowerShellParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3c35a-381">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3c35a-381">CommonParameters</span></span>

<span data-ttu-id="3c35a-382">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3c35a-382">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3c35a-383">Zie about_CommonParameters (voor meer informatie https://go.microsoft.com/fwlink/?LinkID=113216) .</span><span class="sxs-lookup"><span data-stu-id="3c35a-383">For more information, see about_CommonParameters (https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3c35a-384">INVOER</span><span class="sxs-lookup"><span data-stu-id="3c35a-384">INPUTS</span></span>

### <span data-ttu-id="3c35a-385">System. String, System. URI, System. Management. Automation. Runspaces. PSSession</span><span class="sxs-lookup"><span data-stu-id="3c35a-385">System.String, System.URI, System.Management.Automation.Runspaces.PSSession</span></span>

<span data-ttu-id="3c35a-386">U kunt een teken reeks, URI of sessie object door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3c35a-386">You can pipe a string, URI, or session object to this cmdlet.</span></span>

## <span data-ttu-id="3c35a-387">UITVOER</span><span class="sxs-lookup"><span data-stu-id="3c35a-387">OUTPUTS</span></span>

### <span data-ttu-id="3c35a-388">System. Management. Automation. Runspaces. PSSession</span><span class="sxs-lookup"><span data-stu-id="3c35a-388">System.Management.Automation.Runspaces.PSSession</span></span>

## <span data-ttu-id="3c35a-389">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="3c35a-389">NOTES</span></span>

- <span data-ttu-id="3c35a-390">Deze cmdlet maakt gebruik van de externe infra structuur van Power shell.</span><span class="sxs-lookup"><span data-stu-id="3c35a-390">This cmdlet uses the PowerShell remoting infrastructure.</span></span> <span data-ttu-id="3c35a-391">Als u deze cmdlet wilt gebruiken, moeten de lokale computer en alle externe computers worden geconfigureerd voor externe communicatie met Power shell.</span><span class="sxs-lookup"><span data-stu-id="3c35a-391">To use this cmdlet, the local computer and any remote computers must be configured for PowerShell remoting.</span></span> <span data-ttu-id="3c35a-392">Zie [about_Remote_Requirements](About/about_Remote_Requirements.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="3c35a-392">For more information, see [about_Remote_Requirements](About/about_Remote_Requirements.md).</span></span>
- <span data-ttu-id="3c35a-393">Als u een **PSSession** op de lokale computer wilt maken, start u Power shell met de optie als administrator uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="3c35a-393">To create a **PSSession** on the local computer, start PowerShell with the Run as administrator option.</span></span>
- <span data-ttu-id="3c35a-394">Wanneer u klaar bent met de **PSSession**, gebruikt u de `Remove-PSSession` cmdlet om de **PSSession** te verwijderen en de bijbehorende resources vrij te geven.</span><span class="sxs-lookup"><span data-stu-id="3c35a-394">When you are finished with the **PSSession**, use the `Remove-PSSession` cmdlet to delete the **PSSession** and release its resources.</span></span>
- <span data-ttu-id="3c35a-395">De para meters **hostname** en **SSHConnection** zijn opgenomen vanaf Power shell 6,0.</span><span class="sxs-lookup"><span data-stu-id="3c35a-395">The **HostName** and **SSHConnection** parameter sets were included starting with PowerShell 6.0.</span></span>
  <span data-ttu-id="3c35a-396">Ze zijn toegevoegd om Power shell Remoting te bieden op basis van de Secure Shell (SSH).</span><span class="sxs-lookup"><span data-stu-id="3c35a-396">They were added to provide PowerShell remoting based on Secure Shell (SSH).</span></span> <span data-ttu-id="3c35a-397">SSH en Power shell worden ondersteund op meerdere platformen (Windows, Linux, macOS) en externe communicatie met Power shell werkt op deze platforms waarin Power shell en SSH zijn geïnstalleerd en geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="3c35a-397">Both SSH and PowerShell are supported on multiple platforms (Windows, Linux, macOS) and PowerShell remoting will work over these platforms where PowerShell and SSH are installed and configured.</span></span> <span data-ttu-id="3c35a-398">Dit is gescheiden van de vorige Windows-functie voor externe toegang die is gebaseerd op WinRM en veel van de specifieke WinRM-functies en-beperkingen zijn niet van toepassing.</span><span class="sxs-lookup"><span data-stu-id="3c35a-398">This is separate from the previous Windows only remoting that is based on WinRM and much of the WinRM specific features and limitations do not apply.</span></span> <span data-ttu-id="3c35a-399">Bijvoorbeeld: op WinRM gebaseerde quota's, sessie opties, aangepaste eindpunt configuratie en functies voor ontkoppelen/opnieuw verbinden worden op dit moment niet ondersteund.</span><span class="sxs-lookup"><span data-stu-id="3c35a-399">For example WinRM based quotas, session options, custom endpoint configuration, and disconnect/reconnect features are currently not supported.</span></span> <span data-ttu-id="3c35a-400">Zie voor meer informatie over het instellen van externe toegang tot Power shell [via SSH Power shell](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span><span class="sxs-lookup"><span data-stu-id="3c35a-400">For more information about how to set up PowerShell SSH remoting, see [PowerShell Remoting Over SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span></span>

## <span data-ttu-id="3c35a-401">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="3c35a-401">RELATED LINKS</span></span>

[<span data-ttu-id="3c35a-402">Connect-PSSession</span><span class="sxs-lookup"><span data-stu-id="3c35a-402">Connect-PSSession</span></span>](Connect-PSSession.md)

[<span data-ttu-id="3c35a-403">Verbinding verbreken-PSSession</span><span class="sxs-lookup"><span data-stu-id="3c35a-403">Disconnect-PSSession</span></span>](Disconnect-PSSession.md)

[<span data-ttu-id="3c35a-404">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="3c35a-404">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="3c35a-405">Afsluiten-PSSession</span><span class="sxs-lookup"><span data-stu-id="3c35a-405">Exit-PSSession</span></span>](Exit-PSSession.md)

[<span data-ttu-id="3c35a-406">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="3c35a-406">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="3c35a-407">Invoke-opdracht</span><span class="sxs-lookup"><span data-stu-id="3c35a-407">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="3c35a-408">Receive-PSSession</span><span class="sxs-lookup"><span data-stu-id="3c35a-408">Receive-PSSession</span></span>](Receive-PSSession.md)

[<span data-ttu-id="3c35a-409">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="3c35a-409">Remove-PSSession</span></span>](Remove-PSSession.md)

