---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 12/20/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-pssession?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSSession
ms.openlocfilehash: 1af271c164b4478bf57132046affb4276e541108
ms.sourcegitcommit: b10731301412afd4111743b85da95e8c25583533
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/20/2021
ms.locfileid: "107756304"
---
# <span data-ttu-id="c3654-102">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="c3654-102">New-PSSession</span></span>

## <span data-ttu-id="c3654-103">Synopsis</span><span class="sxs-lookup"><span data-stu-id="c3654-103">Synopsis</span></span>
<span data-ttu-id="c3654-104">Hiermee maakt u een permanente verbinding met een lokale of externe computer.</span><span class="sxs-lookup"><span data-stu-id="c3654-104">Creates a persistent connection to a local or remote computer.</span></span>

## <span data-ttu-id="c3654-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="c3654-105">Syntax</span></span>

### <span data-ttu-id="c3654-106">ComputerName (standaard)</span><span class="sxs-lookup"><span data-stu-id="c3654-106">ComputerName (Default)</span></span>

```
New-PSSession [[-ComputerName] <String[]>] [-Credential <PSCredential>] [-Name <String[]>]
 [-EnableNetworkAccess] [-ConfigurationName <String>] [-Port <Int32>] [-UseSSL]
 [-ApplicationName <String>] [-ThrottleLimit <Int32>] [-SessionOption <PSSessionOption>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="c3654-107">Uri</span><span class="sxs-lookup"><span data-stu-id="c3654-107">Uri</span></span>

```
New-PSSession [-Credential <PSCredential>] [-Name <String[]>] [-EnableNetworkAccess]
 [-ConfigurationName <String>] [-ThrottleLimit <Int32>] [-ConnectionUri] <Uri[]> [-AllowRedirection]
 [-SessionOption <PSSessionOption>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="c3654-108">VMId</span><span class="sxs-lookup"><span data-stu-id="c3654-108">VMId</span></span>

```
New-PSSession -Credential <PSCredential> [-Name <String[]>] [-ConfigurationName <String>]
 [-VMId] <Guid[]> [-ThrottleLimit <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="c3654-109">VMName</span><span class="sxs-lookup"><span data-stu-id="c3654-109">VMName</span></span>

```
New-PSSession -Credential <PSCredential> [-Name <String[]>] [-ConfigurationName <String>]
 -VMName <String[]> [-ThrottleLimit <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="c3654-110">Sessie</span><span class="sxs-lookup"><span data-stu-id="c3654-110">Session</span></span>

```
New-PSSession [[-Session] <PSSession[]>] [-Name <String[]>] [-EnableNetworkAccess]
 [-ThrottleLimit <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="c3654-111">ContainerId</span><span class="sxs-lookup"><span data-stu-id="c3654-111">ContainerId</span></span>

```
New-PSSession [-Name <String[]>] [-ConfigurationName <String>] -ContainerId <String[]>
 [-RunAsAdministrator] [-ThrottleLimit <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="c3654-112">UseWindowsPowerShellParameterSet</span><span class="sxs-lookup"><span data-stu-id="c3654-112">UseWindowsPowerShellParameterSet</span></span>

```
New-PSSession [-Name <String[]>] [-UseWindowsPowerShell] [<CommonParameters>]
```

### <span data-ttu-id="c3654-113">SSHHost</span><span class="sxs-lookup"><span data-stu-id="c3654-113">SSHHost</span></span>

```
New-PSSession [-Name <String[]>] [-Port <Int32>] [-HostName] <String[]> [-UserName <String>] [-KeyFilePath <String>]
[-SSHTransport] [-Subsystem <String>] [-ConnectingTimeout <int>] [<CommonParameters>]
```

### <span data-ttu-id="c3654-114">SSHHostHashParam</span><span class="sxs-lookup"><span data-stu-id="c3654-114">SSHHostHashParam</span></span>

```
New-PSSession [-Name <String[]>] -SSHConnection <Hashtable[]> [<CommonParameters>]
```

## <span data-ttu-id="c3654-115">Description</span><span class="sxs-lookup"><span data-stu-id="c3654-115">Description</span></span>

<span data-ttu-id="c3654-116">De `New-PSSession` cmdlet maakt een PowerShell-sessie **(PSSession)** op een lokale of externe computer.</span><span class="sxs-lookup"><span data-stu-id="c3654-116">The `New-PSSession` cmdlet creates a PowerShell session (**PSSession**) on a local or remote computer.</span></span> <span data-ttu-id="c3654-117">Wanneer u een **PSSession maakt,** maakt PowerShell een permanente verbinding met de externe computer.</span><span class="sxs-lookup"><span data-stu-id="c3654-117">When you create a **PSSession**, PowerShell establishes a persistent connection to the remote computer.</span></span>

<span data-ttu-id="c3654-118">Gebruik een **PSSession om** meerdere opdrachten uit te voeren die gegevens delen, zoals een functie of de waarde van een variabele.</span><span class="sxs-lookup"><span data-stu-id="c3654-118">Use a **PSSession** to run multiple commands that share data, such as a function or the value of a variable.</span></span> <span data-ttu-id="c3654-119">Gebruik de cmdlet om opdrachten uit te voeren in een **PSSession.** `Invoke-Command`</span><span class="sxs-lookup"><span data-stu-id="c3654-119">To run commands in a **PSSession**, use the `Invoke-Command` cmdlet.</span></span> <span data-ttu-id="c3654-120">Als u **pssession wilt gebruiken om** rechtstreeks met een externe computer te communiceren, gebruikt u de `Enter-PSSession` cmdlet .</span><span class="sxs-lookup"><span data-stu-id="c3654-120">To use the **PSSession** to interact directly with a remote computer, use the `Enter-PSSession` cmdlet.</span></span> <span data-ttu-id="c3654-121">Zie voor meer informatie [about_PSSessions](about/about_PSSessions.md).</span><span class="sxs-lookup"><span data-stu-id="c3654-121">For more information, see [about_PSSessions](about/about_PSSessions.md).</span></span>

<span data-ttu-id="c3654-122">U kunt opdrachten uitvoeren op een externe computer zonder een **PSSession te maken** met behulp van de **ComputerName-parameters** van of `Enter-PSSession` `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="c3654-122">You can run commands on a remote computer without creating a **PSSession** by using the **ComputerName** parameters of `Enter-PSSession` or `Invoke-Command`.</span></span> <span data-ttu-id="c3654-123">Wanneer u de **parameter ComputerName** gebruikt, maakt PowerShell een tijdelijke verbinding die wordt gebruikt voor de opdracht en vervolgens wordt gesloten.</span><span class="sxs-lookup"><span data-stu-id="c3654-123">When you use the **ComputerName** parameter, PowerShell creates a temporary connection that is used for the command and is then closed.</span></span>

<span data-ttu-id="c3654-124">Vanaf PowerShell 6.0 kunt u Secure Shell (SSH) gebruiken om een verbinding tot stand te brengen en een sessie te maken op een externe computer, als SSH beschikbaar is op de lokale computer en de externe computer is geconfigureerd met een PowerShell SSH-eindpunt.</span><span class="sxs-lookup"><span data-stu-id="c3654-124">Starting with PowerShell 6.0 you can use Secure Shell (SSH) to establish a connection to and create a session on a remote computer, if SSH is available on the local computer and the remote computer is configured with a PowerShell SSH endpoint.</span></span> <span data-ttu-id="c3654-125">Het voordeel van een externe PowerShell-sessie op basis van SSH is dat deze kan werken op meerdere platforms (Windows, Linux, macOS).</span><span class="sxs-lookup"><span data-stu-id="c3654-125">The benefit of an SSH based PowerShell remote session is that it can work across multiple platforms (Windows, Linux, macOS).</span></span> <span data-ttu-id="c3654-126">Voor SSH-sessies gebruikt u de parameter **HostName** of **SSHConnection** om de externe computer en relevante verbindingsgegevens op te geven.</span><span class="sxs-lookup"><span data-stu-id="c3654-126">For SSH based sessions you use the **HostName** or **SSHConnection** parameter set to specify the remote computer and relevant connection information.</span></span> <span data-ttu-id="c3654-127">Zie Voor meer informatie over het instellen van SSH-remoting voor [PowerShell Via SSH.](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core)</span><span class="sxs-lookup"><span data-stu-id="c3654-127">For more information about how to set up PowerShell SSH remoting, see [PowerShell Remoting Over SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span></span>

> [!NOTE]
> <span data-ttu-id="c3654-128">Wanneer u WSMan gebruikt voor remoting vanaf een Linux- of macOS-client met een HTTPS-eindpunt waarop het servercertificaat niet wordt vertrouwd (bijvoorbeeld een zelf-ondertekend certificaat).</span><span class="sxs-lookup"><span data-stu-id="c3654-128">When using WSMan remoting from a Linux or macOS client with a HTTPS endpoint where the server certificate is not trusted (e.g., a self-signed certificate).</span></span> <span data-ttu-id="c3654-129">U moet een met `PSSessionOption` en verstrekken om de verbinding tot stand te `-SkipCACheck` `-SkipCNCheck` brengen.</span><span class="sxs-lookup"><span data-stu-id="c3654-129">You must provide a `PSSessionOption` that includes `-SkipCACheck` and `-SkipCNCheck` to successfully establish the connection.</span></span> <span data-ttu-id="c3654-130">Dit doet u alleen als u zich in een omgeving waar u zeker van het servercertificaat en de netwerkverbinding met het doelsysteem kunt zijn.</span><span class="sxs-lookup"><span data-stu-id="c3654-130">Only do this if you are in an environment where you can be certain of the server certificate and the network connection to the target system.</span></span>

## <span data-ttu-id="c3654-131">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="c3654-131">Examples</span></span>

### <span data-ttu-id="c3654-132">Voorbeeld 1: Een sessie maken op de lokale computer</span><span class="sxs-lookup"><span data-stu-id="c3654-132">Example 1: Create a session on the local computer</span></span>

```powershell
$s = New-PSSession
```

<span data-ttu-id="c3654-133">Met deze opdracht maakt u een **nieuwe PSSession** op de lokale computer en slaat u **de PSSession** op in de `$s` variabele .</span><span class="sxs-lookup"><span data-stu-id="c3654-133">This command creates a new **PSSession** on the local computer and saves the **PSSession** in the `$s` variable.</span></span>

<span data-ttu-id="c3654-134">U kunt deze **PSSession nu gebruiken om** opdrachten uit te voeren op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="c3654-134">You can now use this **PSSession** to run commands on the local computer.</span></span>

### <span data-ttu-id="c3654-135">Voorbeeld 2: Een sessie maken op een externe computer</span><span class="sxs-lookup"><span data-stu-id="c3654-135">Example 2: Create a session on a remote computer</span></span>

```powershell
$Server01 = New-PSSession -ComputerName Server01
```

<span data-ttu-id="c3654-136">Met deze opdracht maakt u een **nieuwe PSSession** op de computer Server01 en slaat u deze op in de `$Server01` variabele .</span><span class="sxs-lookup"><span data-stu-id="c3654-136">This command creates a new **PSSession** on the Server01 computer and saves it in the `$Server01` variable.</span></span>

<span data-ttu-id="c3654-137">Wanneer u meerdere **PSSession-objecten maakt,** wijst u deze toe aan variabelen met nuttige namen.</span><span class="sxs-lookup"><span data-stu-id="c3654-137">When creating multiple **PSSession** objects, assign them to variables with useful names.</span></span> <span data-ttu-id="c3654-138">Dit helpt u bij het beheren van **de PSSession-objecten** in volgende opdrachten.</span><span class="sxs-lookup"><span data-stu-id="c3654-138">This will help you manage the **PSSession** objects in subsequent commands.</span></span>

### <span data-ttu-id="c3654-139">Voorbeeld 3: Sessies maken op meerdere computers</span><span class="sxs-lookup"><span data-stu-id="c3654-139">Example 3: Create sessions on multiple computers</span></span>

```powershell
$s1, $s2, $s3 = New-PSSession -ComputerName Server01,Server02,Server03
```

<span data-ttu-id="c3654-140">Met deze opdracht maakt u **drie PSSession-objecten,** één op elk van de computers die zijn opgegeven door de **ComputerName** parameter.</span><span class="sxs-lookup"><span data-stu-id="c3654-140">This command creates three **PSSession** objects, one on each of the computers specified by the **ComputerName** parameter.</span></span>

<span data-ttu-id="c3654-141">De opdracht gebruikt de toewijzingsoperator (=) om de nieuwe **PSSession-objecten** toe te wijzen aan variabelen: `$s1` , , `$s2` `$s3` .</span><span class="sxs-lookup"><span data-stu-id="c3654-141">The command uses the assignment operator (=) to assign the new **PSSession** objects to variables: `$s1`, `$s2`, `$s3`.</span></span> <span data-ttu-id="c3654-142">De Server01 **PSSession** wordt toegewezen aan `$s1` , de Server02 **PSSession** aan `$s2` en de Server03 **PSSession** aan `$s3` .</span><span class="sxs-lookup"><span data-stu-id="c3654-142">It assigns the Server01 **PSSession** to `$s1`, the Server02 **PSSession** to `$s2`, and the Server03 **PSSession** to `$s3`.</span></span>

<span data-ttu-id="c3654-143">Wanneer u meerdere objecten toewijst aan een reeks variabelen, wijst PowerShell elk object toe aan een variabele in de reeks.</span><span class="sxs-lookup"><span data-stu-id="c3654-143">When you assign multiple objects to a series of variables, PowerShell assigns each object to a variable in the series respectively.</span></span> <span data-ttu-id="c3654-144">Als er meer objecten dan variabelen zijn, worden alle resterende objecten toegewezen aan de laatste variabele.</span><span class="sxs-lookup"><span data-stu-id="c3654-144">If there are more objects than variables, all remaining objects are assigned to the last variable.</span></span> <span data-ttu-id="c3654-145">Als er meer variabelen dan objecten zijn, zijn de resterende variabelen leeg (null).</span><span class="sxs-lookup"><span data-stu-id="c3654-145">If there are more variables than objects, the remaining variables are empty (null).</span></span>

### <span data-ttu-id="c3654-146">Voorbeeld 4: Een sessie maken met een opgegeven poort</span><span class="sxs-lookup"><span data-stu-id="c3654-146">Example 4: Create a session with a specified port</span></span>

```powershell
New-PSSession -ComputerName Server01 -Port 8081 -UseSSL -ConfigurationName E12
```

<span data-ttu-id="c3654-147">Met deze opdracht maakt u een nieuwe **PSSession** op de computer Server01 die verbinding maakt met serverpoort 8081 en het SSL-protocol gebruikt.</span><span class="sxs-lookup"><span data-stu-id="c3654-147">This command creates a new **PSSession** on the Server01 computer that connects to server port 8081 and uses the SSL protocol.</span></span> <span data-ttu-id="c3654-148">De nieuwe **PSSession maakt gebruik** van een alternatieve sessieconfiguratie met de naam E12.</span><span class="sxs-lookup"><span data-stu-id="c3654-148">The new **PSSession** uses an alternative session configuration called E12.</span></span>

<span data-ttu-id="c3654-149">Voordat u de poort instelt, moet u de WinRM-listener op de externe computer configureren om te luisteren op poort 8081.</span><span class="sxs-lookup"><span data-stu-id="c3654-149">Before setting the port, you must configure the WinRM listener on the remote computer to listen on port 8081.</span></span> <span data-ttu-id="c3654-150">Zie de beschrijving van de parameter **Port voor meer** informatie.</span><span class="sxs-lookup"><span data-stu-id="c3654-150">For more information, see the description of the **Port** parameter.</span></span>

### <span data-ttu-id="c3654-151">Voorbeeld 5: een sessie maken op basis van een bestaande sessie</span><span class="sxs-lookup"><span data-stu-id="c3654-151">Example 5: Create a session based on an existing session</span></span>

```powershell
New-PSSession -Session $s -Credential Domain01\User01
```

<span data-ttu-id="c3654-152">Met deze opdracht maakt **u een PSSession** met dezelfde eigenschappen als een bestaande **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="c3654-152">This command creates a **PSSession** with the same properties as an existing **PSSession**.</span></span> <span data-ttu-id="c3654-153">U kunt deze opdrachtindeling gebruiken wanneer de resources van een bestaande **PSSession** zijn uitgeput en een nieuwe **PSSession** nodig is om een deel van de vraag te offloaden.</span><span class="sxs-lookup"><span data-stu-id="c3654-153">You can use this command format when the resources of an existing **PSSession** are exhausted and a new **PSSession** is needed to offload some of the demand.</span></span>

<span data-ttu-id="c3654-154">De opdracht gebruikt de **sessieparameter** van `New-PSSession` om de **PSSession op te geven die** is opgeslagen in de variabele `$s` .</span><span class="sxs-lookup"><span data-stu-id="c3654-154">The command uses the **Session** parameter of `New-PSSession` to specify the **PSSession** saved in the `$s` variable.</span></span> <span data-ttu-id="c3654-155">Deze gebruikt de referenties van de gebruiker Domain1\Admin01 om de opdracht uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="c3654-155">It uses the credentials of the Domain1\Admin01 user to complete the command.</span></span>

### <span data-ttu-id="c3654-156">Voorbeeld 6: Een sessie maken met een globaal bereik in een ander domein</span><span class="sxs-lookup"><span data-stu-id="c3654-156">Example 6: Create a session with a global scope in a different domain</span></span>

```powershell
$global:s = New-PSSession -ComputerName Server1.Domain44.Corpnet.Fabrikam.com -Credential Domain01\Admin01
```

<span data-ttu-id="c3654-157">In dit voorbeeld ziet u hoe u een **PSSession** maakt met een globaal bereik op een computer in een ander domein.</span><span class="sxs-lookup"><span data-stu-id="c3654-157">This example shows how to create a **PSSession** with a global scope on a computer in a different domain.</span></span>

<span data-ttu-id="c3654-158">**PSSession-objecten die zijn** gemaakt op de opdrachtregel, worden standaard gemaakt met een lokaal bereik en **PSSession-objecten** die in een script zijn gemaakt, hebben een scriptbereik.</span><span class="sxs-lookup"><span data-stu-id="c3654-158">By default, **PSSession** objects created at the command line are created with local scope and **PSSession** objects created in a script have script scope.</span></span>

<span data-ttu-id="c3654-159">Als u een **PSSession wilt** maken met een globaal bereik, maakt u een nieuwe **PSSession** en sla u de **PSSession** op in een variabele die wordt gecast naar een globaal bereik.</span><span class="sxs-lookup"><span data-stu-id="c3654-159">To create a **PSSession** with global scope, create a new **PSSession** and then store the **PSSession** in a variable that is cast to a global scope.</span></span> <span data-ttu-id="c3654-160">In dit geval wordt de `$s` variabele gecast naar een globaal bereik.</span><span class="sxs-lookup"><span data-stu-id="c3654-160">In this case, the `$s` variable is cast to a global scope.</span></span>

<span data-ttu-id="c3654-161">De opdracht gebruikt de **ComputerName** parameter opgeven voor de externe computer.</span><span class="sxs-lookup"><span data-stu-id="c3654-161">The command uses the **ComputerName** parameter to specify the remote computer.</span></span> <span data-ttu-id="c3654-162">Omdat de computer zich in een ander domein dan het gebruikersaccount, wordt de volledige naam van de computer samen met de referenties van de gebruiker opgegeven.</span><span class="sxs-lookup"><span data-stu-id="c3654-162">Because the computer is in a different domain than the user account, the full name of the computer is specified together with the credentials of the user.</span></span>

### <span data-ttu-id="c3654-163">Voorbeeld 7: Sessies maken voor veel computers</span><span class="sxs-lookup"><span data-stu-id="c3654-163">Example 7: Create sessions for many computers</span></span>

```powershell
$rs = Get-Content C:\Test\Servers.txt | New-PSSession -ThrottleLimit 50
```

<span data-ttu-id="c3654-164">Met deze opdracht maakt u **een PSSession** op elk van de 200 computers die worden vermeld in het Servers.txt-bestand en wordt de resulterende **PSSession** opgeslagen in de `$rs` variabele .</span><span class="sxs-lookup"><span data-stu-id="c3654-164">This command creates a **PSSession** on each of the 200 computers listed in the Servers.txt file and it stores the resulting **PSSession** in the `$rs` variable.</span></span> <span data-ttu-id="c3654-165">De **PSSession-objecten** hebben een limiet van 50.</span><span class="sxs-lookup"><span data-stu-id="c3654-165">The **PSSession** objects have a throttle limit of 50.</span></span>

<span data-ttu-id="c3654-166">U kunt deze opdrachtindeling gebruiken wanneer de namen van computers worden opgeslagen in een database, spreadsheet, tekstbestand of andere tekstindeling.</span><span class="sxs-lookup"><span data-stu-id="c3654-166">You can use this command format when the names of computers are stored in a database, spreadsheet, text file, or other text-convertible format.</span></span>

### <span data-ttu-id="c3654-167">Voorbeeld 8: Een sessie maken met behulp van een URI</span><span class="sxs-lookup"><span data-stu-id="c3654-167">Example 8: Create a session by using a URI</span></span>

```powershell
$s = New-PSSession -URI http://Server01:91/NewSession -Credential Domain01\User01
```

<span data-ttu-id="c3654-168">Met deze opdracht maakt **u een PSSession** op de computer Server01 en slaat u deze op in de `$s` variabele .</span><span class="sxs-lookup"><span data-stu-id="c3654-168">This command creates a **PSSession** on the Server01 computer and stores it in the `$s` variable.</span></span> <span data-ttu-id="c3654-169">Hierbij de **URI parameter** opgeven voor het transportprotocol, de externe computer, de poort en een alternatieve sessieconfiguratie.</span><span class="sxs-lookup"><span data-stu-id="c3654-169">It uses the **URI** parameter to specify the transport protocol, the remote computer, the port, and an alternate session configuration.</span></span> <span data-ttu-id="c3654-170">Ook wordt de **referentie** parameter opgeven voor een gebruikersaccount dat is machtiging voor het maken van een sessie op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="c3654-170">It also uses the **Credential** parameter to specify a user account that has permission to create a session on the remote computer.</span></span>

### <span data-ttu-id="c3654-171">Voorbeeld 9: Een achtergrond job uitvoeren in een reeks sessies</span><span class="sxs-lookup"><span data-stu-id="c3654-171">Example 9: Run a background job in a set of sessions</span></span>

```powershell
$s = New-PSSession -ComputerName (Get-Content Servers.txt) -Credential Domain01\Admin01 -ThrottleLimit 16
Invoke-Command -Session $s -ScriptBlock {Get-Process PowerShell} -AsJob
```

<span data-ttu-id="c3654-172">Met deze opdrachten maakt u een set **PSSession-objecten** en voert u vervolgens een achtergrond-taak uit in elk van de **PSSession-objecten.**</span><span class="sxs-lookup"><span data-stu-id="c3654-172">These commands create a set of **PSSession** objects and then run a background job in each of the **PSSession** objects.</span></span>

<span data-ttu-id="c3654-173">Met de eerste opdracht maakt u een **nieuwe PSSession** op elk van de computers die worden vermeld in het Servers.txt bestand.</span><span class="sxs-lookup"><span data-stu-id="c3654-173">The first command creates a new **PSSession** on each of the computers listed in the Servers.txt file.</span></span> <span data-ttu-id="c3654-174">De `New-PSSession` cmdlet wordt gebruikt om de **PSSession te maken.**</span><span class="sxs-lookup"><span data-stu-id="c3654-174">It uses the `New-PSSession` cmdlet to create the **PSSession**.</span></span> <span data-ttu-id="c3654-175">De waarde van de **ComputerName** parameter is een opdracht die gebruikmaakt van de cmdlet om op te halen van de lijst met `Get-Content` computernamen Servers.txt bestand.</span><span class="sxs-lookup"><span data-stu-id="c3654-175">The value of the **ComputerName** parameter is a command that uses the `Get-Content` cmdlet to get the list of computer names the Servers.txt file.</span></span>

<span data-ttu-id="c3654-176">De opdracht gebruikt de **referentie** parameter voor het maken van de **PSSession-objecten** die de machtiging van een domeinbeheerder en gebruikt de **ThrottleLimit** parameter voor het beperken van de opdracht tot 16 gelijktijdige verbindingen.</span><span class="sxs-lookup"><span data-stu-id="c3654-176">The command uses the **Credential** parameter to create the **PSSession** objects that have the permission of a domain administrator, and it uses the **ThrottleLimit** parameter to limit the command to 16 concurrent connections.</span></span> <span data-ttu-id="c3654-177">De opdracht slaat de **PSSession-objecten** op in de `$s` variabele .</span><span class="sxs-lookup"><span data-stu-id="c3654-177">The command saves the **PSSession** objects in the `$s` variable.</span></span>

<span data-ttu-id="c3654-178">De tweede opdracht maakt gebruik van de **parameter AsJob** van de cmdlet om een achtergrondopdracht te starten die een opdracht in elk van de `Invoke-Command` `Get-Process PowerShell` **PSSession-objecten** in wordt `$s` uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="c3654-178">The second command uses the **AsJob** parameter of the `Invoke-Command` cmdlet to start a background job that runs a `Get-Process PowerShell` command in each of the **PSSession** objects in `$s`.</span></span>

<span data-ttu-id="c3654-179">Zie PowerShell-achtergrondtaken voor meer [informatie about_Jobs](About/about_Jobs.md) en [about_Remote_Jobs.](About/about_Remote_Jobs.md)</span><span class="sxs-lookup"><span data-stu-id="c3654-179">For more information about PowerShell background jobs, see [about_Jobs](About/about_Jobs.md) and [about_Remote_Jobs](About/about_Remote_Jobs.md).</span></span>

### <span data-ttu-id="c3654-180">Voorbeeld 10: Een sessie voor een computer maken met behulp van de URI</span><span class="sxs-lookup"><span data-stu-id="c3654-180">Example 10: Create a session for a computer by using its URI</span></span>

```powershell
New-PSSession -ConnectionURI https://management.exchangelabs.com/Management
```

<span data-ttu-id="c3654-181">Met deze opdracht maakt u **een PSSession-objecten** die verbinding maken met een computer die is opgegeven door een URI in plaats van een computernaam.</span><span class="sxs-lookup"><span data-stu-id="c3654-181">This command creates a **PSSession** objects that connects to a computer that is specified by a URI instead of a computer name.</span></span>

### <span data-ttu-id="c3654-182">Voorbeeld 11: Een sessieoptie maken</span><span class="sxs-lookup"><span data-stu-id="c3654-182">Example 11: Create a session option</span></span>

```powershell
$so = New-PSSessionOption -SkipCACheck
New-PSSession -ConnectionUri https://management.exchangelabs.com/Management -SessionOption $so -Credential Server01\Admin01
```

<span data-ttu-id="c3654-183">In dit voorbeeld ziet u hoe u een sessieoptieobject maakt en de parameter **SessionOption** gebruikt.</span><span class="sxs-lookup"><span data-stu-id="c3654-183">This example shows how to create a session option object and use the **SessionOption** parameter.</span></span>

<span data-ttu-id="c3654-184">De eerste opdracht maakt gebruik van `New-PSSessionOption` de cmdlet om een sessieoptie te maken.</span><span class="sxs-lookup"><span data-stu-id="c3654-184">The first command uses the `New-PSSessionOption` cmdlet to create a session option.</span></span> <span data-ttu-id="c3654-185">Hiermee slaat u het **resulterende SessionOption-object** op in de `$so` variabele .</span><span class="sxs-lookup"><span data-stu-id="c3654-185">It saves the resulting **SessionOption** object in the `$so` variable.</span></span>

<span data-ttu-id="c3654-186">De tweede opdracht maakt gebruik van de optie in een nieuwe sessie.</span><span class="sxs-lookup"><span data-stu-id="c3654-186">The second command uses the option in a new session.</span></span> <span data-ttu-id="c3654-187">De opdracht maakt gebruik van `New-PSSession` de cmdlet om een nieuwe sessie te maken.</span><span class="sxs-lookup"><span data-stu-id="c3654-187">The command uses the `New-PSSession` cmdlet to create a new session.</span></span> <span data-ttu-id="c3654-188">De waarde van de parameter SessionOption is het **object SessionOption** in de `$so` variabele .</span><span class="sxs-lookup"><span data-stu-id="c3654-188">The value of the SessionOption parameter is the **SessionOption** object in the `$so` variable.</span></span>

### <span data-ttu-id="c3654-189">Voorbeeld 12: Een sessie maken met SSH</span><span class="sxs-lookup"><span data-stu-id="c3654-189">Example 12: Create a session using SSH</span></span>

```powershell
New-PSSession -HostName UserA@LinuxServer01
```

<span data-ttu-id="c3654-190">In dit voorbeeld ziet u hoe u een nieuwe **PSSession maakt** met behulp van Secure Shell (SSH).</span><span class="sxs-lookup"><span data-stu-id="c3654-190">This example shows how to create a new **PSSession** using Secure Shell (SSH).</span></span> <span data-ttu-id="c3654-191">Als SSH is geconfigureerd op de externe computer om te vragen om wachtwoorden, krijgt u een wachtwoordprompt.</span><span class="sxs-lookup"><span data-stu-id="c3654-191">If SSH is configured on the remote computer to prompt for passwords then you will get a password prompt.</span></span> <span data-ttu-id="c3654-192">Anders moet u gebruikersverificatie op basis van een SSH-sleutel gebruiken.</span><span class="sxs-lookup"><span data-stu-id="c3654-192">Otherwise you will have to use SSH key based user authentication.</span></span>

### <span data-ttu-id="c3654-193">Voorbeeld 13: een sessie maken met SSH en de poort- en gebruikersverificatiesleutel opgeven</span><span class="sxs-lookup"><span data-stu-id="c3654-193">Example 13: Create a session using SSH and specify the port and user authentication key</span></span>

```powershell
New-PSSession -HostName UserA@LinuxServer01:22 -KeyFilePath c:\<path>\userAKey_rsa
```

<span data-ttu-id="c3654-194">In dit voorbeeld ziet u hoe u een **PSSession maakt** met behulp van Secure Shell (SSH).</span><span class="sxs-lookup"><span data-stu-id="c3654-194">This example shows how to create a **PSSession** using Secure Shell (SSH).</span></span> <span data-ttu-id="c3654-195">De parameter **Port** wordt gebruikt om de poort op te geven die moet worden gebruikt en de parameter **KeyFilePath** om een RSA-sleutel op te geven die wordt gebruikt om de gebruiker op de externe computer te identificeren en te verifiëren.</span><span class="sxs-lookup"><span data-stu-id="c3654-195">It uses the **Port** parameter to specify the port to use and the **KeyFilePath** parameter to specify an RSA key used to identify and authenticate the user on the remote computer.</span></span>

### <span data-ttu-id="c3654-196">Voorbeeld 14: Meerdere sessies maken met SSH</span><span class="sxs-lookup"><span data-stu-id="c3654-196">Example 14: Create multiple sessions using SSH</span></span>

```powershell
$sshConnections = @{ HostName="WinServer1"; UserName="domain\userA"; KeyFilePath="c:\users\UserA\id_rsa" }, @{ HostName="UserB@LinuxServer5"; KeyFilePath="c:\UserB\<path>\id_rsa" }
New-PSSession -SSHConnection $sshConnections
```

<span data-ttu-id="c3654-197">In dit voorbeeld ziet u hoe u meerdere sessies maakt met behulp van Secure Shell (SSH) en de **parameterset SSHConnection.**</span><span class="sxs-lookup"><span data-stu-id="c3654-197">This example shows how to create multiple sessions using Secure Shell (SSH) and the **SSHConnection** parameter set.</span></span> <span data-ttu-id="c3654-198">De **parameter SSHConnection** maakt gebruik van een matrix met hashtabellen die verbindingsgegevens voor elke sessie bevatten.</span><span class="sxs-lookup"><span data-stu-id="c3654-198">The **SSHConnection** parameter takes an array of hash tables that contain connection information for each session.</span></span> <span data-ttu-id="c3654-199">Houd er rekening mee dat voor dit voorbeeld SSH is geconfigureerd voor de doel-externe computers ter ondersteuning van gebruikersverificatie op basis van sleutels.</span><span class="sxs-lookup"><span data-stu-id="c3654-199">Note that this example requires that the target remote computers have SSH configured to support key based user authentication.</span></span>

## <span data-ttu-id="c3654-200">Parameters</span><span class="sxs-lookup"><span data-stu-id="c3654-200">Parameters</span></span>

### <span data-ttu-id="c3654-201">-AllowRedirection</span><span class="sxs-lookup"><span data-stu-id="c3654-201">-AllowRedirection</span></span>

<span data-ttu-id="c3654-202">Geeft aan dat deze cmdlet omleiding van deze verbinding naar een alternatieve Uniform Resource Identifier (URI) toestaat.</span><span class="sxs-lookup"><span data-stu-id="c3654-202">Indicates that this cmdlet allows redirection of this connection to an alternate Uniform Resource Identifier (URI).</span></span>

<span data-ttu-id="c3654-203">Wanneer u de **parameter ConnectionURI** gebruikt, kan de externe bestemming een instructie retourneren om om te leiden naar een andere URI.</span><span class="sxs-lookup"><span data-stu-id="c3654-203">When you use the **ConnectionURI** parameter, the remote destination can return an instruction to redirect to a different URI.</span></span> <span data-ttu-id="c3654-204">PowerShell leidt verbindingen standaard niet om, maar u kunt deze parameter gebruiken om de verbinding om te leiden.</span><span class="sxs-lookup"><span data-stu-id="c3654-204">By default, PowerShell does not redirect connections, but you can use this parameter to enable it to redirect the connection.</span></span>

<span data-ttu-id="c3654-205">U kunt ook het aantal keren beperken dat de verbinding wordt omgeleid door de **optiewaarde maximumConnectionRedirectionCount-sessie** te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="c3654-205">You can also limit the number of times the connection is redirected by changing the **MaximumConnectionRedirectionCount** session option value.</span></span> <span data-ttu-id="c3654-206">Gebruik de **parameter MaximumRedirection** van de cmdlet of stel de eigenschap `New-PSSessionOption` **MaximumConnectionRedirectionCount** van de **$PSSessionOption** voorkeursvariabele in.</span><span class="sxs-lookup"><span data-stu-id="c3654-206">Use the **MaximumRedirection** parameter of the `New-PSSessionOption` cmdlet or set the **MaximumConnectionRedirectionCount** property of the **$PSSessionOption** preference variable.</span></span> <span data-ttu-id="c3654-207">De standaardwaarde is 5.</span><span class="sxs-lookup"><span data-stu-id="c3654-207">The default value is 5.</span></span>

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

### <span data-ttu-id="c3654-208">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="c3654-208">-ApplicationName</span></span>

<span data-ttu-id="c3654-209">Hiermee geeft u het toepassingsnaamsegment van de verbindings-URI op.</span><span class="sxs-lookup"><span data-stu-id="c3654-209">Specifies the application name segment of the connection URI.</span></span> <span data-ttu-id="c3654-210">Gebruik deze parameter om de naam van de toepassing op te geven wanneer u de **parameter ConnectionURI** niet gebruikt in de opdracht .</span><span class="sxs-lookup"><span data-stu-id="c3654-210">Use this parameter to specify the application name when you are not using the **ConnectionURI** parameter in the command.</span></span>

<span data-ttu-id="c3654-211">De standaardwaarde is de waarde van de `$PSSessionApplicationName` voorkeursvariabele op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="c3654-211">The default value is the value of the `$PSSessionApplicationName` preference variable on the local computer.</span></span> <span data-ttu-id="c3654-212">Als deze voorkeursvariabele niet is gedefinieerd, is de standaardwaarde WSMAN.</span><span class="sxs-lookup"><span data-stu-id="c3654-212">If this preference variable is not defined, the default value is WSMAN.</span></span> <span data-ttu-id="c3654-213">Deze waarde is geschikt voor de meeste toepassingen.</span><span class="sxs-lookup"><span data-stu-id="c3654-213">This value is appropriate for most uses.</span></span> <span data-ttu-id="c3654-214">Zie voor meer informatie [about_Preference_Variables](About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="c3654-214">For more information, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="c3654-215">De WinRM-service gebruikt de toepassingsnaam om een listener te selecteren om de verbindingsaanvraag te verwerken.</span><span class="sxs-lookup"><span data-stu-id="c3654-215">The WinRM service uses the application name to select a listener to service the connection request.</span></span>
<span data-ttu-id="c3654-216">De waarde van deze parameter moet overeenkomen met de waarde van de **eigenschap URLPrefix** van een listener op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="c3654-216">The value of this parameter should match the value of the **URLPrefix** property of a listener on the remote computer.</span></span>

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

### <span data-ttu-id="c3654-217">-Verificatie</span><span class="sxs-lookup"><span data-stu-id="c3654-217">-Authentication</span></span>

<span data-ttu-id="c3654-218">Hiermee geeft u het mechanisme op dat wordt gebruikt om de referenties van de gebruiker te verifiëren.</span><span class="sxs-lookup"><span data-stu-id="c3654-218">Specifies the mechanism that is used to authenticate the user's credentials.</span></span>
<span data-ttu-id="c3654-219">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="c3654-219">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="c3654-220">Standaard</span><span class="sxs-lookup"><span data-stu-id="c3654-220">Default</span></span>
- <span data-ttu-id="c3654-221">Basic</span><span class="sxs-lookup"><span data-stu-id="c3654-221">Basic</span></span>
- <span data-ttu-id="c3654-222">Credssp</span><span class="sxs-lookup"><span data-stu-id="c3654-222">Credssp</span></span>
- <span data-ttu-id="c3654-223">Samenvatting</span><span class="sxs-lookup"><span data-stu-id="c3654-223">Digest</span></span>
- <span data-ttu-id="c3654-224">Kerberos</span><span class="sxs-lookup"><span data-stu-id="c3654-224">Kerberos</span></span>
- <span data-ttu-id="c3654-225">Negotiate</span><span class="sxs-lookup"><span data-stu-id="c3654-225">Negotiate</span></span>
- <span data-ttu-id="c3654-226">NegotiateWithImplicitCredential</span><span class="sxs-lookup"><span data-stu-id="c3654-226">NegotiateWithImplicitCredential</span></span>

<span data-ttu-id="c3654-227">De standaardwaarde is Standaard.</span><span class="sxs-lookup"><span data-stu-id="c3654-227">The default value is Default.</span></span>

<span data-ttu-id="c3654-228">Zie [AuthenticationMechanism Enumeration](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)voor meer informatie over de waarden van deze parameter.</span><span class="sxs-lookup"><span data-stu-id="c3654-228">For more information about the values of this parameter, see [AuthenticationMechanism Enumeration](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!CAUTION]
> <span data-ttu-id="c3654-229">CredSSP-verificatie (Credential Security Support Provider), waarbij de gebruikersreferenties worden doorgegeven aan een externe computer die moet worden geverifieerd, is ontworpen voor opdrachten waarvoor verificatie op meer dan één resource is vereist, zoals toegang tot een externe netwerk share.</span><span class="sxs-lookup"><span data-stu-id="c3654-229">Credential Security Support Provider (CredSSP) authentication, in which the user credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="c3654-230">Dit mechanisme verhoogt het beveiligingsrisico van de externe bewerking.</span><span class="sxs-lookup"><span data-stu-id="c3654-230">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="c3654-231">Als de externe computer is gecompromitteerd, kunnen de referenties die worden doorgegeven aan de computer worden gebruikt voor het beheer van de netwerksessie.</span><span class="sxs-lookup"><span data-stu-id="c3654-231">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

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

### <span data-ttu-id="c3654-232">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="c3654-232">-CertificateThumbprint</span></span>

<span data-ttu-id="c3654-233">Hiermee geeft u het digitale openbare-sleutelcertificaat (X509) op van een gebruikersaccount dat is machtigingen heeft om deze actie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="c3654-233">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span> <span data-ttu-id="c3654-234">Voer de vingerafdruk van het certificaat in.</span><span class="sxs-lookup"><span data-stu-id="c3654-234">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="c3654-235">Certificaten worden gebruikt in verificatie op basis van clientcertificaten.</span><span class="sxs-lookup"><span data-stu-id="c3654-235">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="c3654-236">Ze kunnen alleen worden toe te staan aan lokale gebruikersaccounts; ze werken niet met domeinaccounts.</span><span class="sxs-lookup"><span data-stu-id="c3654-236">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="c3654-237">Als u een certificaat wilt verkrijgen, gebruikt u `Get-Item` de opdracht of in het `Get-ChildItem` PowerShell-station Certificaat: .</span><span class="sxs-lookup"><span data-stu-id="c3654-237">To get a certificate, use the `Get-Item` or `Get-ChildItem` command in the PowerShell Cert: drive.</span></span>

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

### <span data-ttu-id="c3654-238">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="c3654-238">-ComputerName</span></span>

<span data-ttu-id="c3654-239">Hiermee geeft u een matrix met namen van computers.</span><span class="sxs-lookup"><span data-stu-id="c3654-239">Specifies an array of names of computers.</span></span> <span data-ttu-id="c3654-240">Met deze cmdlet maakt u een permanente verbinding **(PSSession)** met de opgegeven computer.</span><span class="sxs-lookup"><span data-stu-id="c3654-240">This cmdlet creates a persistent connection (**PSSession**) to the specified computer.</span></span> <span data-ttu-id="c3654-241">Als u meerdere computernamen op te geven, `New-PSSession` maakt meerdere **PSSession-objecten,** één voor elke computer.</span><span class="sxs-lookup"><span data-stu-id="c3654-241">If you enter multiple computer names, `New-PSSession` creates multiple **PSSession** objects, one for each computer.</span></span> <span data-ttu-id="c3654-242">Standaard is dit de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="c3654-242">The default is the local computer.</span></span>

<span data-ttu-id="c3654-243">Typ de NetBIOS-naam, een IP-adres of een volledig gekwalificeerde domeinnaam van een of meer externe computers.</span><span class="sxs-lookup"><span data-stu-id="c3654-243">Type the NetBIOS name, an IP address, or a fully qualified domain name of one or more remote computers.</span></span> <span data-ttu-id="c3654-244">Als u de lokale computer wilt opgeven, typt u de computernaam, localhost of een punt (.).</span><span class="sxs-lookup"><span data-stu-id="c3654-244">To specify the local computer, type the computer name, localhost, or a dot (.).</span></span> <span data-ttu-id="c3654-245">Wanneer de computer zich in een ander domein dan de gebruiker, de volledig gekwalificeerde domeinnaam is vereist.</span><span class="sxs-lookup"><span data-stu-id="c3654-245">When the computer is in a different domain than the user, the fully qualified domain name is required.</span></span> <span data-ttu-id="c3654-246">U kunt een computernaam ook tussen aanhalingstekens doorseen naar `New-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="c3654-246">You can also pipe a computer name, in quotation marks, to `New-PSSession`.</span></span>

<span data-ttu-id="c3654-247">Als u een IP-adres wilt gebruiken in de waarde van de parameter **ComputerName,** moet de opdracht de parameter **Credential** bevatten.</span><span class="sxs-lookup"><span data-stu-id="c3654-247">To use an IP address in the value of the **ComputerName** parameter, the command must include the **Credential** parameter.</span></span> <span data-ttu-id="c3654-248">De computer moet ook worden geconfigureerd voor HTTPS-transport of het IP-adres van de externe computer moet worden opgenomen in de WinRM TrustedHosts-lijst op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="c3654-248">Also, the computer must be configured for HTTPS transport or the IP address of the remote computer must be included in the WinRM TrustedHosts list on the local computer.</span></span> <span data-ttu-id="c3654-249">Zie voor instructies voor het toevoegen van een computernaam aan de lijst TrustedHosts "How to Add a Computer to the Trusted Host List" in [about_Remote_Troubleshooting](about/about_Remote_Troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="c3654-249">For instructions for adding a computer name to the TrustedHosts list, see "How to Add a Computer to the Trusted Host List" in [about_Remote_Troubleshooting](about/about_Remote_Troubleshooting.md).</span></span>

<span data-ttu-id="c3654-250">Als u de lokale computer wilt opnemen in de waarde van de parameter **ComputerName,** start Windows PowerShell met de optie Als administrator uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="c3654-250">To include the local computer in the value of the **ComputerName** parameter, start Windows PowerShell by using the Run as administrator option.</span></span>

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

### <span data-ttu-id="c3654-251">-ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="c3654-251">-ConfigurationName</span></span>

<span data-ttu-id="c3654-252">Hiermee geeft u de sessieconfiguratie op die wordt gebruikt voor de nieuwe **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="c3654-252">Specifies the session configuration that is used for the new **PSSession**.</span></span>

<span data-ttu-id="c3654-253">Voer een configuratienaam of de volledig gekwalificeerde resource-URI in voor een sessieconfiguratie.</span><span class="sxs-lookup"><span data-stu-id="c3654-253">Enter a configuration name or the fully qualified resource URI for a session configuration.</span></span> <span data-ttu-id="c3654-254">Als u alleen de configuratienaam opgeeft, wordt de volgende schema-URI toegevoegd: `http://schemas.microsoft.com/PowerShell` .</span><span class="sxs-lookup"><span data-stu-id="c3654-254">If you specify only the configuration name, the following schema URI is prepended: `http://schemas.microsoft.com/PowerShell`.</span></span>

<span data-ttu-id="c3654-255">De sessieconfiguratie voor een sessie bevindt zich op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="c3654-255">The session configuration for a session is located on the remote computer.</span></span> <span data-ttu-id="c3654-256">Als de opgegeven sessieconfiguratie niet bestaat op de externe computer, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="c3654-256">If the specified session configuration does not exist on the remote computer, the command fails.</span></span>

<span data-ttu-id="c3654-257">De standaardwaarde is de waarde van de `$PSSessionConfigurationName` voorkeursvariabele op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="c3654-257">The default value is the value of the `$PSSessionConfigurationName` preference variable on the local computer.</span></span> <span data-ttu-id="c3654-258">Als deze voorkeursvariabele niet is ingesteld, is de standaardwaarde Microsoft.PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c3654-258">If this preference variable is not set, the default is Microsoft.PowerShell.</span></span> <span data-ttu-id="c3654-259">Zie voor meer informatie [about_Preference_Variables](About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="c3654-259">For more information, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

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

### <span data-ttu-id="c3654-260">-ConnectingTimeout</span><span class="sxs-lookup"><span data-stu-id="c3654-260">-ConnectingTimeout</span></span>

<span data-ttu-id="c3654-261">Hiermee geeft u de hoeveelheid tijd in milliseconden op die is toegestaan voor het voltooien van de eerste SSH-verbinding.</span><span class="sxs-lookup"><span data-stu-id="c3654-261">Specifies the amount of time in milliseconds allowed for the initial SSH connection to complete.</span></span> <span data-ttu-id="c3654-262">Als de verbinding niet binnen de opgegeven tijd is voltooid, wordt er een fout geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="c3654-262">If the connection doesn't complete within the specified time, an error is returned.</span></span>

<span data-ttu-id="c3654-263">Deze parameter is geïntroduceerd in PowerShell 7.2</span><span class="sxs-lookup"><span data-stu-id="c3654-263">This parameter was introduced in PowerShell 7.2</span></span>

```yaml
Type: System.Int32
Parameter Sets: SSHHost
Aliases:

Required: False
Position: Named
Default value: unlimited
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c3654-264">-ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="c3654-264">-ConnectionUri</span></span>

<span data-ttu-id="c3654-265">Hiermee geeft u een URI op die het verbindings-eindpunt voor de sessie definieert.</span><span class="sxs-lookup"><span data-stu-id="c3654-265">Specifies a URI that defines the connection endpoint for the session.</span></span> <span data-ttu-id="c3654-266">De URI moet volledig gekwalificeerd zijn.</span><span class="sxs-lookup"><span data-stu-id="c3654-266">The URI must be fully qualified.</span></span> <span data-ttu-id="c3654-267">De indeling van deze tekenreeks is als volgt:</span><span class="sxs-lookup"><span data-stu-id="c3654-267">The format of this string is as follows:</span></span>

`<Transport>://<ComputerName>:<Port>/<ApplicationName>`

<span data-ttu-id="c3654-268">De standaardwaarde is als volgt:</span><span class="sxs-lookup"><span data-stu-id="c3654-268">The default value is as follows:</span></span>

`http://localhost:5985/WSMAN`

<span data-ttu-id="c3654-269">Als u geen **ConnectionURI** opgeeft, kunt u de parameters **UseSSL,** **ComputerName,** **Port** en **ApplicationName** gebruiken om de **ConnectionURI-waarden op te** geven.</span><span class="sxs-lookup"><span data-stu-id="c3654-269">If you do not specify a **ConnectionURI**, you can use the **UseSSL**, **ComputerName**, **Port**, and **ApplicationName** parameters to specify the **ConnectionURI** values.</span></span>

<span data-ttu-id="c3654-270">Geldige waarden voor het segment Transport van de URI zijn HTTP en HTTPS.</span><span class="sxs-lookup"><span data-stu-id="c3654-270">Valid values for the Transport segment of the URI are HTTP and HTTPS.</span></span> <span data-ttu-id="c3654-271">Als u een verbindings-URI opgeeft met een Transport-segment, maar geen poort opgeeft, wordt de sessie gemaakt met standaardenpoorten: 80 voor HTTP en 443 voor HTTPS.</span><span class="sxs-lookup"><span data-stu-id="c3654-271">If you specify a connection URI with a Transport segment, but do not specify a port, the session is created with standards ports: 80 for HTTP and 443 for HTTPS.</span></span> <span data-ttu-id="c3654-272">Geef poort 5985 voor HTTP of 5986 voor HTTPS op als u de standaardpoorten wilt gebruiken voor het op andere locatie gebruiken van PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c3654-272">To use the default ports for PowerShell remoting, specify port 5985 for HTTP or 5986 for HTTPS.</span></span>

<span data-ttu-id="c3654-273">Als de doelcomputer de verbinding omleiden naar een andere URI, PowerShell voorkomt de omleiding, tenzij u de **parameter AllowRedirection** in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="c3654-273">If the destination computer redirects the connection to a different URI, PowerShell prevents the redirection unless you use the **AllowRedirection** parameter in the command.</span></span>

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

### <span data-ttu-id="c3654-274">-ContainerId</span><span class="sxs-lookup"><span data-stu-id="c3654-274">-ContainerId</span></span>

<span data-ttu-id="c3654-275">Hiermee geeft u een matrix met ID's van containers op.</span><span class="sxs-lookup"><span data-stu-id="c3654-275">Specifies an array of IDs of containers.</span></span> <span data-ttu-id="c3654-276">Met deze cmdlet wordt een interactieve sessie gestart met elk van de opgegeven containers.</span><span class="sxs-lookup"><span data-stu-id="c3654-276">This cmdlet starts an interactive session with each of the specified containers.</span></span> <span data-ttu-id="c3654-277">Gebruik de `docker ps` opdracht om een lijst met container-ID's op te halen.</span><span class="sxs-lookup"><span data-stu-id="c3654-277">Use the `docker ps` command to get a list of container IDs.</span></span> <span data-ttu-id="c3654-278">Zie de Help voor de opdracht [docker ps](https://docs.docker.com/engine/reference/commandline/ps/) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c3654-278">For more information, see the help for the [docker ps](https://docs.docker.com/engine/reference/commandline/ps/) command.</span></span>

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

### <span data-ttu-id="c3654-279">-Credential</span><span class="sxs-lookup"><span data-stu-id="c3654-279">-Credential</span></span>

<span data-ttu-id="c3654-280">Hiermee geeft u een gebruikersaccount op dat is machtigingen heeft om deze actie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="c3654-280">Specifies a user account that has permission to do this action.</span></span> <span data-ttu-id="c3654-281">Standaard is dit de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="c3654-281">The default is the current user.</span></span>

<span data-ttu-id="c3654-282">Typ een gebruikersnaam, zoals **User01** of **Domain01\User01,** of voer een **PSCredential-object** in dat door de `Get-Credential` cmdlet is gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="c3654-282">Type a user name, such as **User01** or **Domain01\User01**, or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="c3654-283">Als u een gebruikersnaam typt, wordt u gevraagd het wachtwoord in te voeren.</span><span class="sxs-lookup"><span data-stu-id="c3654-283">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="c3654-284">Referenties worden opgeslagen in een [PSCredential-object](/dotnet/api/system.management.automation.pscredential) en het wachtwoord wordt opgeslagen als een [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="c3654-284">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="c3654-285">Zie How secure is **SecureString?** (Hoe veilig is SecureString?) voor meer informatie over [SecureString-gegevensbeveiliging.](/dotnet/api/system.security.securestring#how-secure-is-securestring)</span><span class="sxs-lookup"><span data-stu-id="c3654-285">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="c3654-286">-EnableNetworkAccess</span><span class="sxs-lookup"><span data-stu-id="c3654-286">-EnableNetworkAccess</span></span>

<span data-ttu-id="c3654-287">Geeft aan dat deze cmdlet een interactief beveiliging token toevoegt aan loopback-sessies.</span><span class="sxs-lookup"><span data-stu-id="c3654-287">Indicates that this cmdlet adds an interactive security token to loopback sessions.</span></span> <span data-ttu-id="c3654-288">Met het interactieve token kunt u opdrachten uitvoeren in de loopback-sessie die gegevens van andere computers op halen.</span><span class="sxs-lookup"><span data-stu-id="c3654-288">The interactive token lets you run commands in the loopback session that get data from other computers.</span></span> <span data-ttu-id="c3654-289">U kunt bijvoorbeeld een opdracht uitvoeren in de sessie die XML-bestanden kopieert van een externe computer naar de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="c3654-289">For example, you can run a command in the session that copies XML files from a remote computer to the local computer.</span></span>

<span data-ttu-id="c3654-290">Een loopback-sessie is **een PSSession** die afkomstig is van en eindigt op dezelfde computer.</span><span class="sxs-lookup"><span data-stu-id="c3654-290">A loopback session is a **PSSession** that originates and ends on the same computer.</span></span> <span data-ttu-id="c3654-291">Als u een loopbacksessie wilt maken, laat u de parameter **ComputerName** weg of stelt u de waarde ervan in op punt (.), localhost of de naam van de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="c3654-291">To create a loopback session, omit the **ComputerName** parameter or set its value to dot (.), localhost, or the name of the local computer.</span></span>

<span data-ttu-id="c3654-292">Standaard maakt deze cmdlet loopback-sessies met behulp van een netwerk-token, die mogelijk onvoldoende machtigingen biedt voor verificatie bij externe computers.</span><span class="sxs-lookup"><span data-stu-id="c3654-292">By default, this cmdlet creates loopback sessions by using a network token, which might not provide sufficient permission to authenticate to remote computers.</span></span>

<span data-ttu-id="c3654-293">De **parameter EnableNetworkAccess** is alleen van kracht in loopback-sessies.</span><span class="sxs-lookup"><span data-stu-id="c3654-293">The **EnableNetworkAccess** parameter is effective only in loopback sessions.</span></span> <span data-ttu-id="c3654-294">Als u **EnableNetworkAccess** gebruikt wanneer u een sessie op een externe computer maakt, slaagt de opdracht, maar de parameter wordt genegeerd.</span><span class="sxs-lookup"><span data-stu-id="c3654-294">If you use **EnableNetworkAccess** when you create a session on a remote computer, the command succeeds, but the parameter is ignored.</span></span>

<span data-ttu-id="c3654-295">U kunt ook externe toegang inschakelen in een loopback-sessie  met behulp van de CredSSP-waarde van de verificatieparameter, die de sessiereferenties delegeert naar andere computers.</span><span class="sxs-lookup"><span data-stu-id="c3654-295">You can also enable remote access in a loopback session by using the CredSSP value of the **Authentication** parameter, which delegates the session credentials to other computers.</span></span>

<span data-ttu-id="c3654-296">Om de computer te beschermen tegen schadelijke toegang, kunnen losgekoppelde loopback-sessies met interactieve tokens, die zijn gemaakt met de parameter **EnableNetworkAccess,** alleen opnieuw worden verbonden vanaf de computer waarop de sessie is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="c3654-296">To protect the computer from malicious access, disconnected loopback sessions that have interactive tokens, which are those created by using the **EnableNetworkAccess** parameter, can be reconnected only from the computer on which the session was created.</span></span> <span data-ttu-id="c3654-297">Niet-verbonden sessies die gebruikmaken van CredSSP-verificatie kunnen opnieuw worden verbonden vanaf andere computers.</span><span class="sxs-lookup"><span data-stu-id="c3654-297">Disconnected sessions that use CredSSP authentication can be reconnected from other computers.</span></span> <span data-ttu-id="c3654-298">Voor meer informatie raadpleegt u `Disconnect-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="c3654-298">For more information, see `Disconnect-PSSession`.</span></span>

<span data-ttu-id="c3654-299">Deze parameter is geïntroduceerd in PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="c3654-299">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="c3654-300">-HostName</span><span class="sxs-lookup"><span data-stu-id="c3654-300">-HostName</span></span>

<span data-ttu-id="c3654-301">Hiermee geeft u een matrix met computernamen op voor een SSH-verbinding (Secure Shell).</span><span class="sxs-lookup"><span data-stu-id="c3654-301">Specifies an array of computer names for a Secure Shell (SSH) based connection.</span></span> <span data-ttu-id="c3654-302">Dit is vergelijkbaar met de ComputerName parameter behalve dat de verbinding met de externe computer wordt gemaakt met behulp van SSH in plaats van Windows WinRM.</span><span class="sxs-lookup"><span data-stu-id="c3654-302">This is similar to the ComputerName parameter except that the connection to the remote computer is made using SSH rather than Windows WinRM.</span></span>

<span data-ttu-id="c3654-303">Deze parameter is geïntroduceerd in PowerShell 6.0.</span><span class="sxs-lookup"><span data-stu-id="c3654-303">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="c3654-304">-KeyFilePath</span><span class="sxs-lookup"><span data-stu-id="c3654-304">-KeyFilePath</span></span>

<span data-ttu-id="c3654-305">Hiermee geeft u een sleutelbestandspad op dat wordt gebruikt door Secure Shell (SSH) om een gebruiker op een externe computer te verifiëren.</span><span class="sxs-lookup"><span data-stu-id="c3654-305">Specifies a key file path used by Secure Shell (SSH) to authenticate a user on a remote computer.</span></span>

<span data-ttu-id="c3654-306">Met SSH kan gebruikersverificatie worden uitgevoerd via persoonlijke/openbare sleutels als alternatief voor basisverificatie van wachtwoorden.</span><span class="sxs-lookup"><span data-stu-id="c3654-306">SSH allows user authentication to be performed via private/public keys as an alternative to basic password authentication.</span></span> <span data-ttu-id="c3654-307">Als de externe computer is geconfigureerd voor sleutelverificatie, kan deze parameter worden gebruikt om de sleutel op te geven waarmee de gebruiker wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="c3654-307">If the remote computer is configured for key authentication then this parameter can be used to provide the key that identifies the user.</span></span>

<span data-ttu-id="c3654-308">Deze parameter is geïntroduceerd in PowerShell 6.0.</span><span class="sxs-lookup"><span data-stu-id="c3654-308">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="c3654-309">-Name</span><span class="sxs-lookup"><span data-stu-id="c3654-309">-Name</span></span>

<span data-ttu-id="c3654-310">Hiermee geeft u een gebruiksvriendelijke naam op voor **de PSSession**.</span><span class="sxs-lookup"><span data-stu-id="c3654-310">Specifies a friendly name for the **PSSession**.</span></span>

<span data-ttu-id="c3654-311">U kunt de naam gebruiken om naar de **PSSession te** verwijzen wanneer u andere cmdlets gebruikt, zoals `Get-PSSession` en `Enter-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="c3654-311">You can use the name to refer to the **PSSession** when you use other cmdlets, such as `Get-PSSession` and `Enter-PSSession`.</span></span> <span data-ttu-id="c3654-312">De naam is niet vereist om uniek te zijn voor de computer of de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="c3654-312">The name is not required to be unique to the computer or the current session.</span></span>

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

### <span data-ttu-id="c3654-313">-Port</span><span class="sxs-lookup"><span data-stu-id="c3654-313">-Port</span></span>

<span data-ttu-id="c3654-314">Hiermee geeft u de netwerkpoort op de externe computer die wordt gebruikt voor deze verbinding.</span><span class="sxs-lookup"><span data-stu-id="c3654-314">Specifies the network port on the remote computer that is used for this connection.</span></span> <span data-ttu-id="c3654-315">Als u verbinding wilt maken met een externe computer, moet de externe computer luisteren op de poort die de verbinding gebruikt.</span><span class="sxs-lookup"><span data-stu-id="c3654-315">To connect to a remote computer, the remote computer must be listening on the port that the connection uses.</span></span> <span data-ttu-id="c3654-316">De standaardpoorten zijn 5985, de WinRM-poort voor HTTP, en 5986, de WinRM-poort voor HTTPS.</span><span class="sxs-lookup"><span data-stu-id="c3654-316">The default ports are 5985, which is the WinRM port for HTTP, and 5986, which is the WinRM port for HTTPS.</span></span>

<span data-ttu-id="c3654-317">Voordat u een andere poort gebruikt, moet u de WinRM-listener op de externe computer configureren om naar die poort te luisteren.</span><span class="sxs-lookup"><span data-stu-id="c3654-317">Before using another port, you must configure the WinRM listener on the remote computer to listen at that port.</span></span> <span data-ttu-id="c3654-318">Gebruik de volgende opdrachten om de listener te configureren:</span><span class="sxs-lookup"><span data-stu-id="c3654-318">Use the following commands to configure the listener:</span></span>

1. `winrm delete winrm/config/listener?Address=*+Transport=HTTP`
2. `winrm create winrm/config/listener?Address=*+Transport=HTTP @{Port="\<port-number\>"}`

<span data-ttu-id="c3654-319">Gebruik de parameter **Poort alleen als** dat nodig is.</span><span class="sxs-lookup"><span data-stu-id="c3654-319">Do not use the **Port** parameter unless you must.</span></span> <span data-ttu-id="c3654-320">De poortinstelling in de opdracht is van toepassing op alle computers of sessies waarop de opdracht wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="c3654-320">The port setting in the command applies to all computers or sessions on which the command runs.</span></span> <span data-ttu-id="c3654-321">Een alternatieve poortinstelling kan verhinderen dat de opdracht op alle computers wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="c3654-321">An alternate port setting might prevent the command from running on all computers.</span></span>

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

### <span data-ttu-id="c3654-322">-RunAsAdministrator</span><span class="sxs-lookup"><span data-stu-id="c3654-322">-RunAsAdministrator</span></span>

<span data-ttu-id="c3654-323">Geeft aan dat **pssession wordt uitgevoerd** als beheerder.</span><span class="sxs-lookup"><span data-stu-id="c3654-323">Indicates that the **PSSession** runs as administrator.</span></span>

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

### <span data-ttu-id="c3654-324">-Sessie</span><span class="sxs-lookup"><span data-stu-id="c3654-324">-Session</span></span>

<span data-ttu-id="c3654-325">Hiermee geeft u een matrix **van PSSession-objecten** op die deze cmdlet gebruikt als model voor de nieuwe **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="c3654-325">Specifies an array of **PSSession** objects that this cmdlet uses as a model for the new **PSSession**.</span></span> <span data-ttu-id="c3654-326">Met deze parameter maakt u **nieuwe PSSession-objecten** met dezelfde eigenschappen als de opgegeven **PSSession-objecten.**</span><span class="sxs-lookup"><span data-stu-id="c3654-326">This parameter creates new **PSSession** objects that have the same properties as the specified **PSSession** objects.</span></span>

<span data-ttu-id="c3654-327">Voer een variabele in die de **PSSession-objecten** bevat of een opdracht die de **PSSession-objecten** maakt of op haalt, zoals een `New-PSSession` - of `Get-PSSession` -opdracht.</span><span class="sxs-lookup"><span data-stu-id="c3654-327">Enter a variable that contains the **PSSession** objects or a command that creates or gets the **PSSession** objects, such as a `New-PSSession` or `Get-PSSession` command.</span></span>

<span data-ttu-id="c3654-328">De resulterende **PSSession-objecten** hebben dezelfde computernaam, toepassingsnaam, verbindings-URI, poort, configuratienaam, beperkingslimiet en SSL-waarde (Secure Sockets Layer), maar ze hebben een andere weergavenaam, id en exemplaar-id (GUID).</span><span class="sxs-lookup"><span data-stu-id="c3654-328">The resulting **PSSession** objects have the same computer name, application name, connection URI, port, configuration name, throttle limit, and Secure Sockets Layer (SSL) value as the originals, but they have a different display name, ID, and instance ID (GUID).</span></span>

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

### <span data-ttu-id="c3654-329">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="c3654-329">-SessionOption</span></span>

<span data-ttu-id="c3654-330">Hiermee geeft u geavanceerde opties voor de sessie.</span><span class="sxs-lookup"><span data-stu-id="c3654-330">Specifies advanced options for the session.</span></span> <span data-ttu-id="c3654-331">Voer een **SessionOption-object** in, zoals een object dat u maakt met behulp van de cmdlet of een hash-tabel waarin de sleutels sessieoptienamen zijn en de waarden `New-PSSessionOption` sessieoptiewaarden zijn.</span><span class="sxs-lookup"><span data-stu-id="c3654-331">Enter a **SessionOption** object, such as one that you create by using the `New-PSSessionOption` cmdlet, or a hash table in which the keys are session option names and the values are session option values.</span></span>

<span data-ttu-id="c3654-332">De standaardwaarden voor de opties worden bepaald door de waarde van de `$PSSessionOption` voorkeursvariabele als deze is ingesteld.</span><span class="sxs-lookup"><span data-stu-id="c3654-332">The default values for the options are determined by the value of the `$PSSessionOption` preference variable, if it is set.</span></span> <span data-ttu-id="c3654-333">Anders worden de standaardwaarden ingesteld door opties die zijn ingesteld in de sessieconfiguratie.</span><span class="sxs-lookup"><span data-stu-id="c3654-333">Otherwise, the default values are established by options set in the session configuration.</span></span>

<span data-ttu-id="c3654-334">De waarden van de sessieoptie hebben voorrang op de standaardwaarden voor sessies die zijn ingesteld in de `$PSSessionOption` voorkeursvariabele en in de sessieconfiguratie.</span><span class="sxs-lookup"><span data-stu-id="c3654-334">The session option values take precedence over default values for sessions set in the `$PSSessionOption` preference variable and in the session configuration.</span></span> <span data-ttu-id="c3654-335">Ze hebben echter geen voorrang op maximumwaarden, quota of limieten die zijn ingesteld in de sessieconfiguratie.</span><span class="sxs-lookup"><span data-stu-id="c3654-335">However, they do not take precedence over maximum values, quotas or limits set in the session configuration.</span></span>

<span data-ttu-id="c3654-336">Zie voor een beschrijving van de sessieopties die de standaardwaarden `New-PSSessionOption` bevatten.</span><span class="sxs-lookup"><span data-stu-id="c3654-336">For a description of the session options that includes the default values, see `New-PSSessionOption`.</span></span> <span data-ttu-id="c3654-337">Zie voor meer informatie `$PSSessionOption` over de voorkeursvariabele [about_Preference_Variables.](About/about_Preference_Variables.md)</span><span class="sxs-lookup"><span data-stu-id="c3654-337">For information about the `$PSSessionOption` preference variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span> <span data-ttu-id="c3654-338">Zie [about_Session_Configurations](About/about_Session_Configurations.md) (Engelstalig) voor meer informatie over sessieconfiguraties.</span><span class="sxs-lookup"><span data-stu-id="c3654-338">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

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

### <span data-ttu-id="c3654-339">-SSHConnection</span><span class="sxs-lookup"><span data-stu-id="c3654-339">-SSHConnection</span></span>

<span data-ttu-id="c3654-340">Deze parameter maakt gebruik van een matrix met hashtabels waarbij elke hashtabel een of meer verbindingsparameters bevat die nodig zijn om een SSH-verbinding (Secure Shell) tot stand te brengen (HostName, Port, UserName, KeyFilePath).</span><span class="sxs-lookup"><span data-stu-id="c3654-340">This parameter takes an array of hashtables where each hashtable contains one or more connection parameters needed to establish a Secure Shell (SSH) connection (HostName, Port, UserName, KeyFilePath).</span></span>

<span data-ttu-id="c3654-341">De hashtabelverbindingsparameters zijn hetzelfde als die zijn gedefinieerd voor de **parameterset HostName.**</span><span class="sxs-lookup"><span data-stu-id="c3654-341">The hashtable connection parameters are the same as defined for the **HostName** parameter set.</span></span>

<span data-ttu-id="c3654-342">De **parameter SSHConnection** is handig voor het maken van meerdere sessies waarbij elke sessie andere verbindingsgegevens vereist.</span><span class="sxs-lookup"><span data-stu-id="c3654-342">The **SSHConnection** parameter is useful for creating multiple sessions where each session requires different connection information.</span></span>

<span data-ttu-id="c3654-343">Deze parameter is geïntroduceerd in PowerShell 6.0.</span><span class="sxs-lookup"><span data-stu-id="c3654-343">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="c3654-344">-SSHTransport</span><span class="sxs-lookup"><span data-stu-id="c3654-344">-SSHTransport</span></span>

<span data-ttu-id="c3654-345">Geeft aan dat de externe verbinding tot stand is gebracht met behulp van Secure Shell (SSH).</span><span class="sxs-lookup"><span data-stu-id="c3654-345">Indicates that the remote connection is established using Secure Shell (SSH).</span></span>

<span data-ttu-id="c3654-346">PowerShell maakt standaard gebruik van Windows WinRM om verbinding te maken met een externe computer.</span><span class="sxs-lookup"><span data-stu-id="c3654-346">By default PowerShell uses Windows WinRM to connect to a remote computer.</span></span> <span data-ttu-id="c3654-347">Deze schakelknop dwingt PowerShell om de parameterset HostName te gebruiken voor het tot stand brengen van een externe SSH-verbinding.</span><span class="sxs-lookup"><span data-stu-id="c3654-347">This switch forces PowerShell to use the HostName parameter set for establishing an SSH based remote connection.</span></span>

<span data-ttu-id="c3654-348">Deze parameter is geïntroduceerd in PowerShell 6.0.</span><span class="sxs-lookup"><span data-stu-id="c3654-348">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="c3654-349">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="c3654-349">-ThrottleLimit</span></span>

<span data-ttu-id="c3654-350">Hiermee geeft u het maximum aantal gelijktijdige verbindingen die kunnen worden ingesteld voor het uitvoeren van deze opdracht.</span><span class="sxs-lookup"><span data-stu-id="c3654-350">Specifies the maximum number of concurrent connections that can be established to run this command.</span></span>
<span data-ttu-id="c3654-351">Als u deze parameter weglaten of een waarde van 0 (nul), de standaardwaarde, 32, wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="c3654-351">If you omit this parameter or enter a value of 0 (zero), the default value, 32, is used.</span></span>

<span data-ttu-id="c3654-352">De beperkingslimiet geldt alleen voor de huidige opdracht, niet voor de sessie of voor de computer.</span><span class="sxs-lookup"><span data-stu-id="c3654-352">The throttle limit applies only to the current command, not to the session or to the computer.</span></span>

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

### <span data-ttu-id="c3654-353">-GebruikersNaam</span><span class="sxs-lookup"><span data-stu-id="c3654-353">-UserName</span></span>

<span data-ttu-id="c3654-354">Hiermee geeft u de gebruikersnaam voor het account dat wordt gebruikt voor het maken van een sessie op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="c3654-354">Specifies the user name for the account used to create a session on the remote computer.</span></span> <span data-ttu-id="c3654-355">De verificatiemethode voor gebruikers is afhankelijk van hoe Secure Shell (SSH) is geconfigureerd op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="c3654-355">User authentication method will depend on how Secure Shell (SSH) is configured on the remote computer.</span></span>

<span data-ttu-id="c3654-356">Als SSH is geconfigureerd voor basisverificatie van wachtwoorden, wordt u gevraagd om het gebruikerswachtwoord.</span><span class="sxs-lookup"><span data-stu-id="c3654-356">If SSH is configured for basic password authentication then you will be prompted for the user password.</span></span>

<span data-ttu-id="c3654-357">Als SSH is geconfigureerd voor gebruikersverificatie op basis van sleutels, kan er een pad naar een sleutelbestand worden opgegeven via de parameter KeyFilePath en wordt er geen wachtwoordprompt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="c3654-357">If SSH is configured for key based user authentication then a key file path can be provided via the KeyFilePath parameter and no password prompt will occur.</span></span> <span data-ttu-id="c3654-358">Houd er rekening mee dat als het clientgebruikerssleutelbestand zich op een bekende SSH-locatie bevindt, de parameter KeyFilePath niet nodig is voor verificatie op basis van sleutels en dat gebruikersverificatie automatisch wordt uitgevoerd op basis van de gebruikersnaam.</span><span class="sxs-lookup"><span data-stu-id="c3654-358">Note that if the client user key file is located in an SSH known location then the KeyFilePath parameter is not needed for key based authentication, and user authentication will occur automatically based on the user name.</span></span> <span data-ttu-id="c3654-359">Zie SSH-documentatie over op sleutels gebaseerde gebruikersverificatie voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c3654-359">See SSH documentation about key based user authentication for more information.</span></span>

<span data-ttu-id="c3654-360">Dit is geen vereiste parameter.</span><span class="sxs-lookup"><span data-stu-id="c3654-360">This is not a required parameter.</span></span> <span data-ttu-id="c3654-361">Als er geen userName parameter is opgegeven, wordt de huidige gebruikersnaam voor het aanmelden gebruikt voor de verbinding.</span><span class="sxs-lookup"><span data-stu-id="c3654-361">If no UserName parameter is specified then the current log on user name is used for the connection.</span></span>

<span data-ttu-id="c3654-362">Deze parameter is geïntroduceerd in PowerShell 6.0.</span><span class="sxs-lookup"><span data-stu-id="c3654-362">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="c3654-363">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="c3654-363">-UseSSL</span></span>

<span data-ttu-id="c3654-364">Geeft aan dat deze cmdlet het SSL-protocol gebruikt om een verbinding met de externe computer tot stand te brengen.</span><span class="sxs-lookup"><span data-stu-id="c3654-364">Indicates that this cmdlet uses the SSL protocol to establish a connection to the remote computer.</span></span>
<span data-ttu-id="c3654-365">Standaard wordt SSL niet gebruikt.</span><span class="sxs-lookup"><span data-stu-id="c3654-365">By default, SSL is not used.</span></span>

<span data-ttu-id="c3654-366">WS-Management versleutelt alle PowerShell-inhoud die via het netwerk wordt verzonden.</span><span class="sxs-lookup"><span data-stu-id="c3654-366">WS-Management encrypts all PowerShell content transmitted over the network.</span></span> <span data-ttu-id="c3654-367">De **parameter UseSSL** biedt een extra beveiliging die de gegevens via een HTTPS-verbinding verzendt in plaats van een HTTP-verbinding.</span><span class="sxs-lookup"><span data-stu-id="c3654-367">The **UseSSL** parameter offers an additional protection that sends the data across an HTTPS connection instead of an HTTP connection.</span></span>

<span data-ttu-id="c3654-368">Als u deze parameter gebruikt, maar SSL niet beschikbaar is op de poort die wordt gebruikt voor de opdracht, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="c3654-368">If you use this parameter, but SSL is not available on the port that is used for the command, the command fails.</span></span>

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

### <span data-ttu-id="c3654-369">-VMId</span><span class="sxs-lookup"><span data-stu-id="c3654-369">-VMId</span></span>

<span data-ttu-id="c3654-370">Hiermee geeft u een matrix van id van virtuele machines.</span><span class="sxs-lookup"><span data-stu-id="c3654-370">Specifies an array of ID of virtual machines.</span></span> <span data-ttu-id="c3654-371">Met deze cmdlet wordt een interactieve sessie gestart met elk van de opgegeven virtuele machines.</span><span class="sxs-lookup"><span data-stu-id="c3654-371">This cmdlet starts an interactive session with each of the specified virtual machines.</span></span> <span data-ttu-id="c3654-372">Als u de virtuele machines wilt zien die voor u beschikbaar zijn, gebruikt u de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="c3654-372">To see the virtual machines that are available to you, use the following command:</span></span>

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

### <span data-ttu-id="c3654-373">-VMName</span><span class="sxs-lookup"><span data-stu-id="c3654-373">-VMName</span></span>

<span data-ttu-id="c3654-374">Hiermee geeft u een matrix met namen van virtuele machines.</span><span class="sxs-lookup"><span data-stu-id="c3654-374">Specifies an array of names of virtual machines.</span></span> <span data-ttu-id="c3654-375">Met deze cmdlet wordt een interactieve sessie gestart met elk van de opgegeven virtuele machines.</span><span class="sxs-lookup"><span data-stu-id="c3654-375">This cmdlet starts an interactive session with each of the specified virtual machines.</span></span> <span data-ttu-id="c3654-376">Als u de virtuele machines wilt zien die voor u beschikbaar zijn, gebruikt u `Get-VM` de cmdlet .</span><span class="sxs-lookup"><span data-stu-id="c3654-376">To see the virtual machines that are available to you, use the `Get-VM` cmdlet.</span></span>

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

### <span data-ttu-id="c3654-377">-Subsysteem</span><span class="sxs-lookup"><span data-stu-id="c3654-377">-Subsystem</span></span>

<span data-ttu-id="c3654-378">Hiermee geeft u het SSH-subsysteem op dat wordt gebruikt voor de nieuwe **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="c3654-378">Specifies the SSH subsystem used for the new **PSSession**.</span></span>

<span data-ttu-id="c3654-379">Hiermee geeft u het subsysteem op dat op het doel moet worden gebruikt, zoals gedefinieerd in sshd_config.</span><span class="sxs-lookup"><span data-stu-id="c3654-379">This specifies the subsystem to use on the target as defined in sshd_config.</span></span>
<span data-ttu-id="c3654-380">Het subsysteem start een specifieke versie van PowerShell met vooraf gedefinieerde parameters.</span><span class="sxs-lookup"><span data-stu-id="c3654-380">The subsystem starts a specific version of PowerShell with predefined parameters.</span></span>
<span data-ttu-id="c3654-381">Als het opgegeven subsysteem niet bestaat op de externe computer, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="c3654-381">If the specified subsystem does not exist on the remote computer, the command fails.</span></span>

<span data-ttu-id="c3654-382">Als deze parameter niet wordt gebruikt, is de standaardwaarde het subsysteem 'powershell'.</span><span class="sxs-lookup"><span data-stu-id="c3654-382">If this parameter is not used, the default is the 'powershell' subsystem.</span></span>

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

### <span data-ttu-id="c3654-383">-UseWindowsPowerShell</span><span class="sxs-lookup"><span data-stu-id="c3654-383">-UseWindowsPowerShell</span></span>

<span data-ttu-id="c3654-384">{{ Fill UseWindowsPowerShell Description }}</span><span class="sxs-lookup"><span data-stu-id="c3654-384">{{ Fill UseWindowsPowerShell Description }}</span></span>

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

### <span data-ttu-id="c3654-385">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c3654-385">CommonParameters</span></span>

<span data-ttu-id="c3654-386">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c3654-386">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c3654-387">Zie voor meer informatie about_CommonParameters ( https://go.microsoft.com/fwlink/?LinkID=113216) .</span><span class="sxs-lookup"><span data-stu-id="c3654-387">For more information, see about_CommonParameters (https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c3654-388">Invoerwaarden</span><span class="sxs-lookup"><span data-stu-id="c3654-388">Inputs</span></span>

### <span data-ttu-id="c3654-389">System.String, System.URI, System.Management.Automation.Runspaces.PSSession</span><span class="sxs-lookup"><span data-stu-id="c3654-389">System.String, System.URI, System.Management.Automation.Runspaces.PSSession</span></span>

<span data-ttu-id="c3654-390">U kunt een tekenreeks, URI of sessieobject doorsleesen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c3654-390">You can pipe a string, URI, or session object to this cmdlet.</span></span>

## <span data-ttu-id="c3654-391">Uitvoerwaarden</span><span class="sxs-lookup"><span data-stu-id="c3654-391">Outputs</span></span>

### <span data-ttu-id="c3654-392">System.Management.Automation.Runspaces.PSSession</span><span class="sxs-lookup"><span data-stu-id="c3654-392">System.Management.Automation.Runspaces.PSSession</span></span>

## <span data-ttu-id="c3654-393">Notities</span><span class="sxs-lookup"><span data-stu-id="c3654-393">Notes</span></span>

- <span data-ttu-id="c3654-394">Deze cmdlet maakt gebruik van de infrastructuur voor remoting van PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c3654-394">This cmdlet uses the PowerShell remoting infrastructure.</span></span> <span data-ttu-id="c3654-395">Als u deze cmdlet wilt gebruiken, moeten de lokale computer en alle externe computers worden geconfigureerd voor externe toegang van PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c3654-395">To use this cmdlet, the local computer and any remote computers must be configured for PowerShell remoting.</span></span> <span data-ttu-id="c3654-396">Zie voor meer informatie [about_Remote_Requirements](About/about_Remote_Requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3654-396">For more information, see [about_Remote_Requirements](About/about_Remote_Requirements.md).</span></span>
- <span data-ttu-id="c3654-397">Als u een **PSSession wilt maken** op de lokale computer, start u PowerShell met de optie Als administrator uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="c3654-397">To create a **PSSession** on the local computer, start PowerShell with the Run as administrator option.</span></span>
- <span data-ttu-id="c3654-398">Wanneer u klaar bent met de **PSSession,** gebruikt u de `Remove-PSSession` cmdlet om de **PSSession** te verwijderen en de resources vrij te geven.</span><span class="sxs-lookup"><span data-stu-id="c3654-398">When you are finished with the **PSSession**, use the `Remove-PSSession` cmdlet to delete the **PSSession** and release its resources.</span></span>
- <span data-ttu-id="c3654-399">De **parametersets HostName** en **SSHConnection** zijn opgenomen vanaf PowerShell 6.0.</span><span class="sxs-lookup"><span data-stu-id="c3654-399">The **HostName** and **SSHConnection** parameter sets were included starting with PowerShell 6.0.</span></span>
  <span data-ttu-id="c3654-400">Ze zijn toegevoegd om Toegang tot PowerShell te bieden op basis van Secure Shell (SSH).</span><span class="sxs-lookup"><span data-stu-id="c3654-400">They were added to provide PowerShell remoting based on Secure Shell (SSH).</span></span> <span data-ttu-id="c3654-401">Zowel SSH als PowerShell worden ondersteund op meerdere platforms (Windows, Linux, macOS) en voor het voor mobiele gebruik van PowerShell worden deze platformen gebruikt waarop PowerShell en SSH zijn geïnstalleerd en geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="c3654-401">Both SSH and PowerShell are supported on multiple platforms (Windows, Linux, macOS) and PowerShell remoting will work over these platforms where PowerShell and SSH are installed and configured.</span></span> <span data-ttu-id="c3654-402">Dit staat los van de vorige windows-remoting die is gebaseerd op WinRM en veel specifieke WinRM-functies en -beperkingen zijn niet van toepassing.</span><span class="sxs-lookup"><span data-stu-id="c3654-402">This is separate from the previous Windows only remoting that is based on WinRM and much of the WinRM specific features and limitations do not apply.</span></span> <span data-ttu-id="c3654-403">Bijvoorbeeld quota op basis van WinRM, sessieopties, aangepaste eindpuntconfiguratie en functies voor verbreken/opnieuw verbinden worden momenteel niet ondersteund.</span><span class="sxs-lookup"><span data-stu-id="c3654-403">For example WinRM based quotas, session options, custom endpoint configuration, and disconnect/reconnect features are currently not supported.</span></span> <span data-ttu-id="c3654-404">Zie Voor meer informatie over het instellen van SSH-remoting voor [PowerShell Via SSH.](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core)</span><span class="sxs-lookup"><span data-stu-id="c3654-404">For more information about how to set up PowerShell SSH remoting, see [PowerShell Remoting Over SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span></span>

## <span data-ttu-id="c3654-405">Verwante koppelingen</span><span class="sxs-lookup"><span data-stu-id="c3654-405">Related Links</span></span>

[<span data-ttu-id="c3654-406">Connect-PSSession</span><span class="sxs-lookup"><span data-stu-id="c3654-406">Connect-PSSession</span></span>](Connect-PSSession.md)

[<span data-ttu-id="c3654-407">Verbinding verbreken met PSSession</span><span class="sxs-lookup"><span data-stu-id="c3654-407">Disconnect-PSSession</span></span>](Disconnect-PSSession.md)

[<span data-ttu-id="c3654-408">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="c3654-408">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="c3654-409">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="c3654-409">Exit-PSSession</span></span>](Exit-PSSession.md)

[<span data-ttu-id="c3654-410">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="c3654-410">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="c3654-411">Invoke-opdracht</span><span class="sxs-lookup"><span data-stu-id="c3654-411">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="c3654-412">Receive-PSSession</span><span class="sxs-lookup"><span data-stu-id="c3654-412">Receive-PSSession</span></span>](Receive-PSSession.md)

[<span data-ttu-id="c3654-413">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="c3654-413">Remove-PSSession</span></span>](Remove-PSSession.md)
