---
ms.date: 06/12/2017
keywords: jea, powershell, beveiliging
title: JEA gebruiken
ms.openlocfilehash: fa3d3a3c8bc0090ec9ad788585ec5df933134173
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084042"
---
# <a name="using-jea"></a><span data-ttu-id="7c588-103">JEA gebruiken</span><span class="sxs-lookup"><span data-stu-id="7c588-103">Using JEA</span></span>

> <span data-ttu-id="7c588-104">Van toepassing op: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="7c588-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="7c588-105">Dit onderwerp beschrijft de verschillende manieren waarop u kunt verbinding maken met en gebruiken van een JEA-eindpunt.</span><span class="sxs-lookup"><span data-stu-id="7c588-105">This topic describes the various ways you can connect to and use a JEA endpoint.</span></span>

## <a name="using-jea-interactively"></a><span data-ttu-id="7c588-106">JEA interactief gebruiken</span><span class="sxs-lookup"><span data-stu-id="7c588-106">Using JEA interactively</span></span>

<span data-ttu-id="7c588-107">Als u de JEA-configuratie testen wilt of eenvoudige taken voor gebruikers om uit te voeren, kunt u de dezelfde manier als een reguliere PowerShell voor externe toegang-sessie JEA gebruiken.</span><span class="sxs-lookup"><span data-stu-id="7c588-107">If you are testing your JEA configuration or have simple tasks for users to perform, you can use JEA the same way you would a regular PowerShell remoting session.</span></span>
<span data-ttu-id="7c588-108">Voor externe communicatie van complexe taken, is het raadzaam te gebruiken [impliciete externe communicatie](#using-jea-with-implicit-remoting) in plaats daarvan te vereenvoudigen voor uw gebruikers doordat gebruikers werken met de gegevens objecten lokaal.</span><span class="sxs-lookup"><span data-stu-id="7c588-108">For complex remoting tasks, it is recommended to use [implicit remoting](#using-jea-with-implicit-remoting) instead to make it easier for your users by allowing users to operate with the data objects locally.</span></span>

<span data-ttu-id="7c588-109">Voor het gebruik van JEA interactief, gaat u te werk:</span><span class="sxs-lookup"><span data-stu-id="7c588-109">To use JEA interactively, you will need:</span></span>
- <span data-ttu-id="7c588-110">De naam van de computer die u verbinding maakt (kan de lokale computer zijn)</span><span class="sxs-lookup"><span data-stu-id="7c588-110">The name of the computer you are connecting to (can be the local machine)</span></span>
- <span data-ttu-id="7c588-111">De naam van de JEA-eindpunt dat is geregistreerd op die computer</span><span class="sxs-lookup"><span data-stu-id="7c588-111">The name of the JEA endpoint registered on that computer</span></span>
- <span data-ttu-id="7c588-112">Referenties voor de computer die toegang tot de JEA-eindpunt hebben</span><span class="sxs-lookup"><span data-stu-id="7c588-112">Credentials for the computer that have access to the JEA endpoint</span></span>

<span data-ttu-id="7c588-113">Met deze informatie beschikt, kunt u starten een JEA-sessie met [New-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSSession) of [Enter-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/enter-pssession).</span><span class="sxs-lookup"><span data-stu-id="7c588-113">With that information in hand, you can start a JEA session using [New-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSSession) or [Enter-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/enter-pssession).</span></span>

```powershell
$nonAdminCred = Get-Credential
Enter-PSSession -ComputerName localhost -ConfigurationName JEAMaintenance -Credential $nonAdminCred
```

<span data-ttu-id="7c588-114">Als het account dat u bent momenteel aangemeld als toegang tot de JEA-eindpunt heeft, kunt u weglaten de `-Credential` parameter.</span><span class="sxs-lookup"><span data-stu-id="7c588-114">If the account you're currently logged in as has access to the JEA endpoint, you can omit the `-Credential` parameter.</span></span>

<span data-ttu-id="7c588-115">Wanneer de PowerShell wijzigingen aan vragen `[localhost]: PS>` weet u dat u nu met de externe JEA-sessie communiceert.</span><span class="sxs-lookup"><span data-stu-id="7c588-115">When the PowerShell prompt changes to `[localhost]: PS>` you will know that you are now interacting with the remote JEA session.</span></span>
<span data-ttu-id="7c588-116">U kunt uitvoeren `Get-Command` om te controleren welke opdrachten zijn beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="7c588-116">You can run `Get-Command` to check which commands are available.</span></span>
<span data-ttu-id="7c588-117">U moet Neem contact op met uw beheerder voor meer informatie als er beperkingen voor de beschikbare parameters of de toegestane parameterwaarden.</span><span class="sxs-lookup"><span data-stu-id="7c588-117">You will need to consult with your administrator to learn if there are any restrictions on the available parameters or allowable parameter values.</span></span>

<span data-ttu-id="7c588-118">Als een herinnering werken JEA-sessies in de modus NoLanguage, zodat sommige van de manieren die doorgaans u PowerShell gebruikt niet meer beschikbaar zijn.</span><span class="sxs-lookup"><span data-stu-id="7c588-118">As a reminder, JEA sessions operate in NoLanguage mode, so some of the ways you typically use PowerShell may not be available.</span></span>
<span data-ttu-id="7c588-119">U kunt de variabelen bijvoorbeeld niet gebruiken voor het opslaan van gegevens of Controleer de eigenschappen van objecten die zijn geretourneerd door cmdlets.</span><span class="sxs-lookup"><span data-stu-id="7c588-119">For instance, you cannot use variables to store data or inspect the properties on objects returned from cmdlets.</span></span>
<span data-ttu-id="7c588-120">Het onderstaande voorbeeld ziet u een voorbeeld van hoe u gebruikt PowerShell vandaag nog en twee methoden voor het ophalen van dezelfde opdracht in de modus NoLanguage werkt.</span><span class="sxs-lookup"><span data-stu-id="7c588-120">The below example shows an example of how you may be using PowerShell today, and two approaches to get the same command working in NoLanguage mode.</span></span>

```powershell
# Using variables in NoLanguage mode is disallowed, so the following will not work
# $vm = Get-VM -Name 'SQL01'
# Start-VM -VM $vm

# You can use pipes to pass data through to commands that accept input from the pipeline
Get-VM -Name 'SQL01' | Start-VM

# You can also wrap subcommands in parentheses and enter them inline as arguments
Start-VM -VM (Get-VM -Name 'SQL01')

# Better yet, use parameter sets that don't require extra data to be passed in when possible
Start-VM -VMName 'SQL01'
```

<span data-ttu-id="7c588-121">Voor complexere aanroepen van de opdracht die deze benadering moeilijk maken, kunt u overwegen [impliciete externe communicatie](#using-jea-with-implicit-remoting) of [maken van aangepaste functies](role-capabilities.md#creating-custom-functions) die de gewenste functionaliteit verpakken.</span><span class="sxs-lookup"><span data-stu-id="7c588-121">For more complex command invocations that make this approach difficult, consider using [implicit remoting](#using-jea-with-implicit-remoting) or [creating custom functions](role-capabilities.md#creating-custom-functions) that wrap the functionality you desire.</span></span>

## <a name="using-jea-with-implicit-remoting"></a><span data-ttu-id="7c588-122">JEA gebruiken met impliciete externe communicatie</span><span class="sxs-lookup"><span data-stu-id="7c588-122">Using JEA with implicit remoting</span></span>

<span data-ttu-id="7c588-123">PowerShell ondersteunt een alternatief voor externe toegang-model kunt u cmdlets van webtoepassingsproxy importeren vanaf een externe computer op uw lokale computer en er interactie mee alsof deze lokaal opdrachten.</span><span class="sxs-lookup"><span data-stu-id="7c588-123">PowerShell supports an alternative remoting model where you can import proxy cmdlets from a remote machine on your local computer and interact with them as if they were local commands.</span></span>
<span data-ttu-id="7c588-124">Dit heet impliciete externe communicatie, en wordt uitgelegd in goed [dit *Hallo, Scripting Guy!* blogbericht](https://blogs.technet.microsoft.com/heyscriptingguy/2013/09/08/remoting-the-implicit-way/).</span><span class="sxs-lookup"><span data-stu-id="7c588-124">This is called implicit remoting, and is explained well in [this *Hey, Scripting Guy!* blog post](https://blogs.technet.microsoft.com/heyscriptingguy/2013/09/08/remoting-the-implicit-way/).</span></span>
<span data-ttu-id="7c588-125">Impliciete externe communicatie is met name handig bij het werken met JEA omdat Hiermee kunt u werken met de JEA-cmdlets in een taalmodus voor volledig.</span><span class="sxs-lookup"><span data-stu-id="7c588-125">Implicit remoting is particularly useful when working with JEA because it allows you to work with JEA cmdlets in a full language mode.</span></span>
<span data-ttu-id="7c588-126">Dit betekent dat u kunt gebruiken tab-aanvulling, variabelen, objecten bewerken, en zelfs lokale scripts gebruiken om het eenvoudig automatiseren op basis van een JEA-eindpunt.</span><span class="sxs-lookup"><span data-stu-id="7c588-126">This means you can use tab completion, variables, manipulate objects, and even use local scripts to more easily automate against a JEA endpoint.</span></span>
<span data-ttu-id="7c588-127">Telkens wanneer u een proxy-opdracht aanroepen, worden de gegevens verzonden naar de JEA-eindpunt op de externe computer en er wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="7c588-127">Anytime you invoke a proxy command, the data will be sent to the JEA endpoint on the remote machine and executed there.</span></span>

<span data-ttu-id="7c588-128">Impliciete externe communicatie werkt door het importeren van de cmdlets van een bestaande PowerShell-sessie.</span><span class="sxs-lookup"><span data-stu-id="7c588-128">Implicit remoting works by importing cmdlets from an existing PowerShell session.</span></span>
<span data-ttu-id="7c588-129">U kunt eventueel aan het voorvoegsel van de zelfstandige naamwoorden van elke cmdlet proxy met een tekenreeks van uw keuze te onderscheiden welke opdrachten zijn voor het externe systeem.</span><span class="sxs-lookup"><span data-stu-id="7c588-129">You can optionally choose to prefix the nouns of each proxy cmdlet with a string of your choosing to distinguish which commands are for the remote system.</span></span>
<span data-ttu-id="7c588-130">Een tijdelijke scriptmodule met alle van de proxy-opdrachten wordt gemaakt en kan worden gebruikt voor de duur van uw lokale PowerShell-sessie.</span><span class="sxs-lookup"><span data-stu-id="7c588-130">A temporary script module containing all of the proxy commands will be created and can be used for the duration of your local PowerShell session.</span></span>

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Import the entire PSSession and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA'

# Invoke "Get-Command" on the remote JEA endpoint using the proxy cmdlet
Get-JEACommand
```

> [!IMPORTANT]
> <span data-ttu-id="7c588-131">Sommige systemen kunnen pas weer voor het importeren van een hele JEA-sessie vanwege beperkingen in de standaard JEA-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="7c588-131">Some systems may not be able to import an entire JEA session due to constraints in the default JEA cmdlets.</span></span>
> <span data-ttu-id="7c588-132">Als u lost dit, alleen importeren opdrachten die u nodig van de JEA-sessie door expliciet hun namen naar de `-CommandName` parameter.</span><span class="sxs-lookup"><span data-stu-id="7c588-132">To get around this, only import the commands you need from the JEA session by explicitly providing their names to the `-CommandName` parameter.</span></span>
> <span data-ttu-id="7c588-133">Een toekomstige update heeft betrekking op het probleem met het importeren van volledige JEA-sessies op de geïnfecteerde systemen.</span><span class="sxs-lookup"><span data-stu-id="7c588-133">A future update will address the issue with importing entire JEA sessions on affected systems.</span></span>

<span data-ttu-id="7c588-134">Als u zich niet voor het importeren van een JEA-sessie vanwege beperkingen met betrekking tot de standaardparameters van JEA, kunt u de volgende stappen voor het filteren van de opdrachten die standaard in de geïmporteerde verzameling.</span><span class="sxs-lookup"><span data-stu-id="7c588-134">If you are unable to import a JEA session due to constraints on the default JEA parameters, you can follow the steps below to filter out the default commands from the imported set.</span></span>
<span data-ttu-id="7c588-135">Kunt u zich nog steeds gebruik van opdrachten zoals `Select-Object` --u alleen de lokale versie is geïnstalleerd op uw computer in plaats van het externe certificaat in de JEA-sessie.</span><span class="sxs-lookup"><span data-stu-id="7c588-135">You will still be able to use commands like `Select-Object` -- you'll just use the local version installed on your computer instead of the remote one in the JEA session.</span></span>

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Get a list of all the commands on the JEA endpoint
$commands = Invoke-Command -Session $jeasession -ScriptBlock { Get-Command }

# Filter out the default cmdlets
$jeaDefaultCmdlets = 'Clear-Host', 'Exit-PSSession', 'Get-Command', 'Get-FormatData', 'Get-Help', 'Measure-Object', 'Out-Default', 'Select-Object'
$filteredCommands = $commands.Name | Where-Object { $jeaDefaultCmdlets -notcontains $_ }

# Import only commands explicitly added in role capabilities and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA' -CommandName $filteredCommands
```

<span data-ttu-id="7c588-136">U kunt ook de via proxy-cmdlets van het gebruik van de impliciete externe communicatie behouden [Export-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/Export-PSSession).</span><span class="sxs-lookup"><span data-stu-id="7c588-136">You can also persist the proxied cmdlets from implicit remoting using [Export-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/Export-PSSession).</span></span>
<span data-ttu-id="7c588-137">Voor meer informatie over de impliciete externe communicatie, bekijkt u de help-documentatie voor [Import-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/import-pssession) en [Import-Module](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/import-module).</span><span class="sxs-lookup"><span data-stu-id="7c588-137">For more information about implicit remoting, check out the help documentation for [Import-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/import-pssession) and [Import-Module](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/import-module).</span></span>

## <a name="using-jea-programmatically"></a><span data-ttu-id="7c588-138">JEA via een programma gebruiken</span><span class="sxs-lookup"><span data-stu-id="7c588-138">Using JEA programmatically</span></span>

<span data-ttu-id="7c588-139">JEA kan ook worden gebruikt in automation-systemen en toepassingen, zoals interne helpdesk-apps en websites.</span><span class="sxs-lookup"><span data-stu-id="7c588-139">JEA can also be used in automation systems and in user applications, such as in-house helpdesk apps and web sites.</span></span>
<span data-ttu-id="7c588-140">De aanpak is hetzelfde als die voor het bouwen van apps die met onbeperkte PowerShell-eindpunten, met het voorbehoud communiceren dat het programma moet rekening houden JEA beperken van de opdrachten die kunnen worden uitgevoerd in de externe sessie.</span><span class="sxs-lookup"><span data-stu-id="7c588-140">The approach is the same as that for building apps that talk to unconstrained PowerShell endpoints, with the caveat that the program should be aware that JEA is limiting the commands that can be run in the remote session.</span></span>

<span data-ttu-id="7c588-141">Voor eenvoudige eenmalige taken, kunt u [Invoke-Command](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/invoke-command) om uit te voeren van een reeks opdrachten JEA gebruiken.</span><span class="sxs-lookup"><span data-stu-id="7c588-141">For simple, one-off tasks, you can use [Invoke-Command](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/invoke-command) to run a set of commands using JEA.</span></span>

```powershell
Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Process; Get-Service }
```

<span data-ttu-id="7c588-142">Uitvoeren als u wilt controleren welke opdrachten zijn beschikbaar voor gebruik wanneer u verbinding met een JEA-sessie maakt, `Get-Command` en de resultaten om te controleren voor de toegestane parameters doorlopen.</span><span class="sxs-lookup"><span data-stu-id="7c588-142">To check which commands are available for use when you connect to a JEA session, run `Get-Command` and iterate through the results to check for the allowed parameters.</span></span>

```powershell
$allowedCommands = Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Command }
$allowedCommands | Where-Object { $_.CommandType -in 'Function', 'Cmdlet' } | Format-Table Name, Parameters
```

<span data-ttu-id="7c588-143">Als u bouwt een C# app, kunt u een PowerShell-runspace die verbinding met een JEA-sessie maakt door op te geven de configuratienaam van de in een [WSManConnectionInfo](https://msdn.microsoft.com/library/system.management.automation.runspaces.wsmanconnectioninfo(v=vs.85).aspx) object.</span><span class="sxs-lookup"><span data-stu-id="7c588-143">If you are building a C# app, you can create a PowerShell runspace that connects to a JEA session by specifying the configuration name in a [WSManConnectionInfo](https://msdn.microsoft.com/library/system.management.automation.runspaces.wsmanconnectioninfo(v=vs.85).aspx) object.</span></span>

```csharp
// using System.Management.Automation;
var computerName = "SERVER01";
var configName   = "JEAMaintenance";
var creds        = // create a PSCredential object here (https://msdn.microsoft.com/library/system.management.automation.pscredential(v=vs.85).aspx)

WSManConnectionInfo connectionInfo = new WSManConnectionInfo(
                    false,                 // Use SSL
                    computerName,          // Computer name
                    5985,                  // WSMan Port
                    "/wsman",              // WSMan Path
                    string.Format(CultureInfo.InvariantCulture, "http://schemas.microsoft.com/powershell/{0}", configName),  // Connection URI with config name
                    creds);                // Credentials
// Now, use the connection info to create a runspace where you can run the commands
using (Runspace runspace = RunspaceFactory.CreateRunspace(connectionInfo))
{
    // Open the runspace
    runspace.Open();

    using (PowerShell ps = PowerShell.Create())
    {
        // Set the PowerShell object to use the JEA runspace
        ps.Runspace = runspace;

        // Now you can add and invoke commands
        ps.AddCommand("Get-Command");
        foreach (var result in ps.Invoke())
        {
            Console.WriteLine(result);
        }
    }

    // Close the runspace
    runspace.Close();
}
```

## <a name="using-jea-with-powershell-direct"></a><span data-ttu-id="7c588-144">JEA gebruiken met PowerShell Direct</span><span class="sxs-lookup"><span data-stu-id="7c588-144">Using JEA with PowerShell Direct</span></span>

<span data-ttu-id="7c588-145">Hyper-V in Windows 10 en Windows Server 2016 biedt [PowerShell Direct](https://msdn.microsoft.com/virtualization/hyperv_on_windows/user_guide/vmsession), een functie waarmee Hyper-V-administrators voor het beheren van virtuele machines met PowerShell, ongeacht de netwerkconfiguratie of extern beheer de instellingen op de virtuele machine.</span><span class="sxs-lookup"><span data-stu-id="7c588-145">Hyper-V in Windows 10 and Windows Server 2016 offers [PowerShell Direct](https://msdn.microsoft.com/virtualization/hyperv_on_windows/user_guide/vmsession), a feature which allows Hyper-V administrators to manage virtual machines with PowerShell regardless of the network configuration or remote management settings on the virtual machine.</span></span>

<span data-ttu-id="7c588-146">U kunt PowerShell Direct met JEA gebruiken een Hyper-V beperkte beheerder om toegang te geven aan uw virtuele machine, die kan nuttig zijn als u verbinding met het netwerk met uw virtuele machine verloren en een datacenter-beheerder moet oplossen om de netwerkinstellingen.</span><span class="sxs-lookup"><span data-stu-id="7c588-146">You can use PowerShell Direct with JEA to give a Hyper-V administrator limited access to your VM, which can be useful if you lose network connectivity to your VM and need a datacenter admin to fix the network settings.</span></span>

<span data-ttu-id="7c588-147">Er is geen aanvullende configuratie vereist voor het gebruik van JEA via PowerShell Direct, maar het besturingssysteem wordt uitgevoerd in de virtuele machine Windows 10 of Windows Server 2016 moet.</span><span class="sxs-lookup"><span data-stu-id="7c588-147">No additional configuration is required to use JEA over PowerShell Direct, however the operating system running inside the virtual machine must be Windows 10 or Windows Server 2016.</span></span>
<span data-ttu-id="7c588-148">De Hyper-V-beheerder kan verbinding maken met de JEA-eindpunt met behulp van de `-VMName` of `-VMId` parameters op PSRemoting-cmdlets:</span><span class="sxs-lookup"><span data-stu-id="7c588-148">The Hyper-V admin can connect to the JEA endpoint by using the `-VMName` or `-VMId` parameters on PSRemoting cmdlets:</span></span>

```powershell
# Entering a JEA session using PowerShell Direct when the VM name is unique
Enter-PSSession -VMName 'SQL01' -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'

# Entering a JEA session using PowerShell Direct using VM ids
$vm = Get-VM -VMName 'MyVM' | Select-Object -First 1
Enter-PSSession -VMId $vm.VMId -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'
```

<span data-ttu-id="7c588-149">Het is raadzaam dat u een toegewezen lokale gebruiker met geen andere rechten maken voor het beheren van het systeem uw Hyper-V-beheerders moeten gebruiken.</span><span class="sxs-lookup"><span data-stu-id="7c588-149">It is strongly recommended that you create a dedicated local user with no other rights to manage the system for your Hyper-V administrators to use.</span></span>
<span data-ttu-id="7c588-150">Houd er rekening mee dat zelfs een niet-gemachtigde gebruiker nog steeds zich bij een Windows-machine standaard aanmelden kan, inclusief het gebruik van onbeperkte PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7c588-150">Remember that even an unprivileged user can still log into a Windows machine by default, including using unconstrained PowerShell.</span></span>
<span data-ttu-id="7c588-151">Die hen om te bladeren (aantal) in staat het bestandssysteem en meer informatie over de omgeving van uw besturingssysteem.</span><span class="sxs-lookup"><span data-stu-id="7c588-151">That will allow them to browse (some of) the file system and learn more about your OS environment.</span></span>
<span data-ttu-id="7c588-152">Als u wilt de beheerder van een Hyper-V alleen toegang tot een virtuele machine met behulp van PowerShell Direct met JEA vergrendelen, moet u lokale aanmeldingsrechten naar JEA-account van de Hyper-V-beheerder weigeren.</span><span class="sxs-lookup"><span data-stu-id="7c588-152">To lock down a Hyper-V administrator to only access a VM using PowerShell Direct with JEA, you will need to deny local logon rights to the Hyper-V admin's JEA account.</span></span>
