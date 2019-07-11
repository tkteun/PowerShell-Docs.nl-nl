---
ms.date: 07/10/2019
keywords: jea, powershell, beveiliging
title: JEA gebruiken
ms.openlocfilehash: 8f3cc9186c61a2ae5b64eb3dc4f72ca83f1a58c5
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734215"
---
# <a name="using-jea"></a><span data-ttu-id="df1ed-103">JEA gebruiken</span><span class="sxs-lookup"><span data-stu-id="df1ed-103">Using JEA</span></span>

<span data-ttu-id="df1ed-104">Dit artikel beschrijft de verschillende manieren waarop u kunt verbinding maken met en gebruiken van een JEA-eindpunt.</span><span class="sxs-lookup"><span data-stu-id="df1ed-104">This article describes the various ways you can connect to and use a JEA endpoint.</span></span>

## <a name="using-jea-interactively"></a><span data-ttu-id="df1ed-105">JEA interactief gebruiken</span><span class="sxs-lookup"><span data-stu-id="df1ed-105">Using JEA interactively</span></span>

<span data-ttu-id="df1ed-106">Als u de configuratie van uw JEA test of eenvoudige taken voor gebruikers hebt, kunt u de dezelfde manier als een reguliere PowerShell voor externe toegang-sessie JEA gebruiken.</span><span class="sxs-lookup"><span data-stu-id="df1ed-106">If you're testing your JEA configuration or have simple tasks for users, you can use JEA the same way you would a regular PowerShell remoting session.</span></span> <span data-ttu-id="df1ed-107">Voor externe communicatie van complexe taken, is het raadzaam te gebruiken [impliciete externe communicatie](#using-jea-with-implicit-remoting).</span><span class="sxs-lookup"><span data-stu-id="df1ed-107">For complex remoting tasks, it's recommended to use [implicit remoting](#using-jea-with-implicit-remoting).</span></span> <span data-ttu-id="df1ed-108">Impliciete externe communicatie kan gebruikers met de gegevensobjecten lokaal werken.</span><span class="sxs-lookup"><span data-stu-id="df1ed-108">Implicit remoting allows users to operate with the data objects locally.</span></span>

<span data-ttu-id="df1ed-109">Voor het gebruik van JEA interactief, hebt u het volgende nodig:</span><span class="sxs-lookup"><span data-stu-id="df1ed-109">To use JEA interactively, you need:</span></span>

- <span data-ttu-id="df1ed-110">De naam van de computer waarmee u verbinding (kan de lokale computer zijn)</span><span class="sxs-lookup"><span data-stu-id="df1ed-110">The name of the computer you're connecting to (can be the local machine)</span></span>
- <span data-ttu-id="df1ed-111">De naam van de JEA-eindpunt dat is geregistreerd op die computer</span><span class="sxs-lookup"><span data-stu-id="df1ed-111">The name of the JEA endpoint registered on that computer</span></span>
- <span data-ttu-id="df1ed-112">De referenties die toegang tot de JEA-eindpunt op die computer hebben</span><span class="sxs-lookup"><span data-stu-id="df1ed-112">Credentials that have access to the JEA endpoint on that computer</span></span>

<span data-ttu-id="df1ed-113">Deze informatie verstrekt, kunt u start een JEA-sessie met de [New-PSSession](/powershell/module/microsoft.powershell.core/New-PSSession) of [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) cmdlets.</span><span class="sxs-lookup"><span data-stu-id="df1ed-113">Given that information, you can start a JEA session using the [New-PSSession](/powershell/module/microsoft.powershell.core/New-PSSession) or [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) cmdlets.</span></span>

```powershell
$nonAdminCred = Get-Credential
Enter-PSSession -ComputerName localhost -ConfigurationName JEAMaintenance -Credential $nonAdminCred
```

<span data-ttu-id="df1ed-114">Als het account van de huidige gebruiker toegang tot de JEA-eindpunt heeft, kunt u weglaten de **referentie** parameter.</span><span class="sxs-lookup"><span data-stu-id="df1ed-114">If the current user account has access to the JEA endpoint, you can omit the **Credential** parameter.</span></span>

<span data-ttu-id="df1ed-115">Wanneer de PowerShell wijzigingen aan vragen `[localhost]: PS>` u weet dat u bent nu interactie is met de externe JEA-sessie.</span><span class="sxs-lookup"><span data-stu-id="df1ed-115">When the PowerShell prompt changes to `[localhost]: PS>` you know that you're now interacting with the remote JEA session.</span></span> <span data-ttu-id="df1ed-116">U kunt uitvoeren `Get-Command` om te controleren welke opdrachten zijn beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="df1ed-116">You can run `Get-Command` to check which commands are available.</span></span> <span data-ttu-id="df1ed-117">Neem contact op met uw beheerder voor meer informatie of er beperkingen voor de beschikbare parameters of de toegestane waarden zijn.</span><span class="sxs-lookup"><span data-stu-id="df1ed-117">Consult with your administrator to learn if there are any restrictions on the available parameters or allowed parameter values.</span></span>

<span data-ttu-id="df1ed-118">Let op: JEA-sessies in NoLanguage modus werken.</span><span class="sxs-lookup"><span data-stu-id="df1ed-118">Remember, JEA sessions operate in NoLanguage mode.</span></span> <span data-ttu-id="df1ed-119">Aantal manieren waarop die u doorgaans gebruik van PowerShell is mogelijk niet beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="df1ed-119">Some of the ways you typically use PowerShell may not be available.</span></span> <span data-ttu-id="df1ed-120">U kunt de variabelen bijvoorbeeld niet gebruiken voor het opslaan van gegevens of Controleer de eigenschappen van objecten die zijn geretourneerd door cmdlets.</span><span class="sxs-lookup"><span data-stu-id="df1ed-120">For instance, you can't use variables to store data or inspect the properties on objects returned from cmdlets.</span></span> <span data-ttu-id="df1ed-121">Het volgende voorbeeld ziet twee methoden voor het ophalen van dezelfde opdrachten NoLanguage modus.</span><span class="sxs-lookup"><span data-stu-id="df1ed-121">The following example shows two approaches to get the same commands to work in NoLanguage mode.</span></span>

```powershell
# Using variables is prohibited in NoLanguage mode. The following will not work:
# $vm = Get-VM -Name 'SQL01'
# Start-VM -VM $vm

# You can use pipes to pass data through to commands that accept input from the pipeline
Get-VM -Name 'SQL01' | Start-VM

# You can also wrap subcommands in parentheses and enter them inline as arguments
Start-VM -VM (Get-VM -Name 'SQL01')

# You can also use parameter sets that don't require extra data to be passed in
Start-VM -VMName 'SQL01'
```

<span data-ttu-id="df1ed-122">Voor complexere aanroepen van de opdracht die deze benadering moeilijk maken, kunt u overwegen [impliciete externe communicatie](#using-jea-with-implicit-remoting) of [maken van aangepaste functies](role-capabilities.md#creating-custom-functions) die verpakken met de functionaliteit die u nodig hebt.</span><span class="sxs-lookup"><span data-stu-id="df1ed-122">For more complex command invocations that make this approach difficult, consider using [implicit remoting](#using-jea-with-implicit-remoting) or [creating custom functions](role-capabilities.md#creating-custom-functions) that wrap the functionality you require.</span></span>

## <a name="using-jea-with-implicit-remoting"></a><span data-ttu-id="df1ed-123">JEA gebruiken met impliciete externe communicatie</span><span class="sxs-lookup"><span data-stu-id="df1ed-123">Using JEA with implicit remoting</span></span>

<span data-ttu-id="df1ed-124">PowerShell is een impliciete externe communicatie-model waarmee u cmdlets van webtoepassingsproxy importeren vanaf een externe computer en er interactie mee alsof deze lokaal opdrachten.</span><span class="sxs-lookup"><span data-stu-id="df1ed-124">PowerShell has an implicit remoting model that lets you import proxy cmdlets from a remote machine and interact with them as if they were local commands.</span></span> <span data-ttu-id="df1ed-125">Impliciete externe communicatie wordt uitgelegd in deze **Hallo, Scripting Guy!**</span><span class="sxs-lookup"><span data-stu-id="df1ed-125">Implicit remoting is explained in this **Hey, Scripting Guy!**</span></span> <span data-ttu-id="df1ed-126">[blogbericht](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/).</span><span class="sxs-lookup"><span data-stu-id="df1ed-126">[blog post](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/).</span></span>
<span data-ttu-id="df1ed-127">Impliciete externe communicatie is handig bij het werken met JEA omdat Hiermee kunt u werken met de JEA-cmdlets in een taalmodus voor volledig.</span><span class="sxs-lookup"><span data-stu-id="df1ed-127">Implicit remoting is useful when working with JEA because it allows you to work with JEA cmdlets in a full language mode.</span></span> <span data-ttu-id="df1ed-128">U kunt tabvoltooiing, variabelen, manipuleren van objecten en zelfs lokale scripts gebruiken voor het automatiseren van taken in een JEA-eindpunt.</span><span class="sxs-lookup"><span data-stu-id="df1ed-128">You can use tab completion, variables, manipulate objects, and even use local scripts to automate tasks against a JEA endpoint.</span></span> <span data-ttu-id="df1ed-129">Telkens wanneer u een proxy-opdracht aanroepen, worden de gegevens worden verzonden naar de JEA-eindpunt op de externe computer en er wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="df1ed-129">Anytime you invoke a proxy command, the data is sent to the JEA endpoint on the remote machine and executed there.</span></span>

<span data-ttu-id="df1ed-130">Impliciete externe communicatie werkt door het importeren van de cmdlets van een bestaande PowerShell-sessie.</span><span class="sxs-lookup"><span data-stu-id="df1ed-130">Implicit remoting works by importing cmdlets from an existing PowerShell session.</span></span> <span data-ttu-id="df1ed-131">U kunt eventueel aan het voorvoegsel van de zelfstandige naamwoorden van elke cmdlet proxy met een tekenreeks van uw keuze.</span><span class="sxs-lookup"><span data-stu-id="df1ed-131">You can optionally choose to prefix the nouns of each proxy cmdlet with a string of your choosing.</span></span> <span data-ttu-id="df1ed-132">Het voorvoegsel kunt u te onderscheiden van de opdrachten die bestemd voor het externe systeem zijn.</span><span class="sxs-lookup"><span data-stu-id="df1ed-132">The prefix allows you to distinguish the commands that are for the remote system.</span></span> <span data-ttu-id="df1ed-133">Een tijdelijke scriptmodule met alle opdrachten die de proxy is gemaakt en geïmporteerd voor de duur van uw lokale PowerShell-sessie.</span><span class="sxs-lookup"><span data-stu-id="df1ed-133">A temporary script module containing all the proxy commands is created and imported for the duration of your local PowerShell session.</span></span>

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Import the entire PSSession and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA'

# Invoke "Get-Command" on the remote JEA endpoint using the proxy cmdlet
Get-JEACommand
```

> [!IMPORTANT]
> <span data-ttu-id="df1ed-134">Sommige systemen kunnen pas weer voor het importeren van een hele JEA-sessie vanwege beperkingen in de standaard JEA-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="df1ed-134">Some systems may not be able to import an entire JEA session due to constraints in the default JEA cmdlets.</span></span> <span data-ttu-id="df1ed-135">Als u lost dit, alleen importeren opdrachten die u nodig van de JEA-sessie door expliciet hun namen naar de `-CommandName` parameter.</span><span class="sxs-lookup"><span data-stu-id="df1ed-135">To get around this, only import the commands you need from the JEA session by explicitly providing their names to the `-CommandName` parameter.</span></span> <span data-ttu-id="df1ed-136">Een toekomstige update heeft betrekking op het probleem met het importeren van volledige JEA-sessies op de geïnfecteerde systemen.</span><span class="sxs-lookup"><span data-stu-id="df1ed-136">A future update will address the issue with importing entire JEA sessions on affected systems.</span></span>

<span data-ttu-id="df1ed-137">Als u niet voor het importeren van een JEA-sessie vanwege beperkingen in de standaardparameters JEA, de volgende stappen voor het filteren van de opdrachten die standaard in de geïmporteerde verzameling.</span><span class="sxs-lookup"><span data-stu-id="df1ed-137">If you're unable to import a JEA session because of JEA constraints on the default parameters, follow the steps below to filter out the default commands from the imported set.</span></span> <span data-ttu-id="df1ed-138">U kunt doorgaan met de opdrachten, zoals `Select-Object`, maar u alleen de lokale versie is geïnstalleerd op uw computer in plaats van een geïmporteerd uit de externe JEA-sessie.</span><span class="sxs-lookup"><span data-stu-id="df1ed-138">You can continue use commands like `Select-Object`, but you'll just use the local version installed on your computer instead of the one imported from the remote JEA session.</span></span>

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

<span data-ttu-id="df1ed-139">U kunt ook de via proxy-cmdlets van het gebruik van de impliciete externe communicatie behouden [Export-PSSession](/powershell/microsoft.powershell.utility/Export-PSSession).</span><span class="sxs-lookup"><span data-stu-id="df1ed-139">You can also persist the proxied cmdlets from implicit remoting using [Export-PSSession](/powershell/microsoft.powershell.utility/Export-PSSession).</span></span>
<span data-ttu-id="df1ed-140">Voor meer informatie over de impliciete externe communicatie, Zie de documentatie voor [Import-PSSession](/powershell/microsoft.powershell.utility/import-pssession) en [Import-Module](/powershell/microsoft.powershell.core/import-module).</span><span class="sxs-lookup"><span data-stu-id="df1ed-140">For more information about implicit remoting, see the documentation for [Import-PSSession](/powershell/microsoft.powershell.utility/import-pssession) and [Import-Module](/powershell/microsoft.powershell.core/import-module).</span></span>

## <a name="using-jea-programmatically"></a><span data-ttu-id="df1ed-141">JEA via een programma gebruiken</span><span class="sxs-lookup"><span data-stu-id="df1ed-141">Using JEA programmatically</span></span>

<span data-ttu-id="df1ed-142">JEA kan ook worden gebruikt in automation-systemen en toepassingen, zoals interne helpdesk-apps en websites.</span><span class="sxs-lookup"><span data-stu-id="df1ed-142">JEA can also be used in automation systems and in user applications, such as in-house helpdesk apps and websites.</span></span> <span data-ttu-id="df1ed-143">De aanpak is hetzelfde als die voor het bouwen van apps die met onbeperkte PowerShell-eindpunten communiceren.</span><span class="sxs-lookup"><span data-stu-id="df1ed-143">The approach is the same as that for building apps that talk to unconstrained PowerShell endpoints.</span></span> <span data-ttu-id="df1ed-144">Zorg ervoor dat het programma is ontworpen voor gebruik met de beperking die zijn opgelegd door JEA.</span><span class="sxs-lookup"><span data-stu-id="df1ed-144">Ensure the program is designed to work with limitation imposed by JEA.</span></span>

<span data-ttu-id="df1ed-145">Voor eenvoudige eenmalige taken, kunt u [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) opdrachten kunt uitvoeren in een JEA-sessie.</span><span class="sxs-lookup"><span data-stu-id="df1ed-145">For simple, one-off tasks, you can use [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) to run commands in a JEA session.</span></span>

```powershell
Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Process; Get-Service }
```

<span data-ttu-id="df1ed-146">Uitvoeren als u wilt controleren welke opdrachten zijn beschikbaar voor gebruik wanneer u verbinding met een JEA-sessie maakt, `Get-Command` en de resultaten om te controleren voor de toegestane parameters doorlopen.</span><span class="sxs-lookup"><span data-stu-id="df1ed-146">To check which commands are available for use when you connect to a JEA session, run `Get-Command` and iterate through the results to check for the allowed parameters.</span></span>

```powershell
$allowedCommands = Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Command }
$allowedCommands | Where-Object { $_.CommandType -in 'Function', 'Cmdlet' } | Format-Table Name, Parameters
```

<span data-ttu-id="df1ed-147">Als u een C# app, kunt u een PowerShell-runspace die verbinding met een JEA-sessie maakt door op te geven de configuratienaam van de in een [WSManConnectionInfo](/dotnet/api/system.management.automation.runspaces.wsmanconnectioninfo) object.</span><span class="sxs-lookup"><span data-stu-id="df1ed-147">If you're building a C# app, you can create a PowerShell runspace that connects to a JEA session by specifying the configuration name in a [WSManConnectionInfo](/dotnet/api/system.management.automation.runspaces.wsmanconnectioninfo) object.</span></span>

```csharp
// using System.Management.Automation;
var computerName = "SERVER01";
var configName   = "JEAMaintenance";
// See https://docs.microsoft.com/dotnet/api/system.management.automation.pscredential
var creds        = // create a PSCredential object here

WSManConnectionInfo connectionInfo = new WSManConnectionInfo(
    false,                 // Use SSL
    computerName,          // Computer name
    5985,                  // WSMan Port
    "/wsman",              // WSMan Path
                           // Connection URI with config name
    string.Format(CultureInfo.InvariantCulture, "http://schemas.microsoft.com/powershell/{0}", configName),
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

## <a name="using-jea-with-powershell-direct"></a><span data-ttu-id="df1ed-148">JEA gebruiken met PowerShell Direct</span><span class="sxs-lookup"><span data-stu-id="df1ed-148">Using JEA with PowerShell Direct</span></span>

<span data-ttu-id="df1ed-149">Hyper-V in Windows 10 en Windows Server 2016 biedt [PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct), een functie waarmee Hyper-V-administrators voor het beheren van virtuele machines met PowerShell, ongeacht de netwerkconfiguratie of extern beheer de instellingen op de virtuele machine.</span><span class="sxs-lookup"><span data-stu-id="df1ed-149">Hyper-V in Windows 10 and Windows Server 2016 offers [PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct), a feature that allows Hyper-V administrators to manage virtual machines with PowerShell regardless of the network configuration or remote management settings on the virtual machine.</span></span>

<span data-ttu-id="df1ed-150">U kunt PowerShell Direct met JEA gebruiken op een Hyper-V-beheerder beperkte toegang geven tot uw virtuele machine.</span><span class="sxs-lookup"><span data-stu-id="df1ed-150">You can use PowerShell Direct with JEA to give a Hyper-V administrator limited access to your VM.</span></span>
<span data-ttu-id="df1ed-151">Dit kan nuttig zijn als u hebt een datacenter-beheerder om op te lossen de netwerkinstellingen en verliest netwerkverbinding met uw virtuele machine.</span><span class="sxs-lookup"><span data-stu-id="df1ed-151">This can be useful if you lose network connectivity to your VM and need a datacenter admin to fix the network settings.</span></span>

<span data-ttu-id="df1ed-152">Geen aanvullende configuratie is vereist voor het gebruik van JEA via PowerShell Direct.</span><span class="sxs-lookup"><span data-stu-id="df1ed-152">No additional configuration is required to use JEA over PowerShell Direct.</span></span> <span data-ttu-id="df1ed-153">Windows 10, WindowsServer 2016 of hoger moet echter van het gastbesturingssysteem die binnen de virtuele machine wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="df1ed-153">However, the guest operating system running inside the virtual machine must be Windows 10, Windows Server 2016, or higher.</span></span> <span data-ttu-id="df1ed-154">De Hyper-V-beheerder kan verbinding maken met de JEA-eindpunt met behulp van de `-VMName` of `-VMId` parameters op PSRemoting-cmdlets:</span><span class="sxs-lookup"><span data-stu-id="df1ed-154">The Hyper-V admin can connect to the JEA endpoint by using the `-VMName` or `-VMId` parameters on PSRemoting cmdlets:</span></span>

```powershell
# Entering a JEA session using PowerShell Direct when the VM name is unique
Enter-PSSession -VMName 'SQL01' -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'

# Entering a JEA session using PowerShell Direct using VM ids
$vm = Get-VM -VMName 'MyVM' | Select-Object -First 1
Enter-PSSession -VMId $vm.VMId -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'
```

<span data-ttu-id="df1ed-155">Het wordt aanbevolen dat een specifieke gebruikersaccount te maken met de minimale rechten die nodig zijn voor het beheren van het systeem voor gebruik door de beheerder van een Hyper-V.</span><span class="sxs-lookup"><span data-stu-id="df1ed-155">It's recommended you create a dedicated user account with the minimum rights needed to manage the system for use by a Hyper-V administrator.</span></span> <span data-ttu-id="df1ed-156">Onthoud dat ook een niet-gemachtigde gebruikers kan zich aanmelden bij een Windows-machine standaard, inclusief het gebruik van onbeperkte PowerShell.</span><span class="sxs-lookup"><span data-stu-id="df1ed-156">Remember, even an unprivileged user can sign into a Windows machine by default, including using unconstrained PowerShell.</span></span> <span data-ttu-id="df1ed-157">Waarmee ze kunnen bladeren in het bestandssysteem en meer informatie over de omgeving van uw besturingssysteem.</span><span class="sxs-lookup"><span data-stu-id="df1ed-157">That allows them to browse the file system and learn more about your OS environment.</span></span> <span data-ttu-id="df1ed-158">Als u wilt vergrendelen van een beheerder van een Hyper-V en beperken zodat ze alleen toegang tot een virtuele machine met behulp van PowerShell Direct met JEA, moet u lokale aanmeldingsrechten naar JEA-account van de Hyper-V-beheerder weigeren.</span><span class="sxs-lookup"><span data-stu-id="df1ed-158">To lock down a Hyper-V administrator and limit them to only access a VM using PowerShell Direct with JEA, you must deny local logon rights to the Hyper-V admin's JEA account.</span></span>
