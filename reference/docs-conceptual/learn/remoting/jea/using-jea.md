---
ms.date: 07/10/2019
keywords: JEA, Power shell, beveiliging
title: JEA gebruiken
ms.openlocfilehash: 912e7a3c46be40ff5b5dfa37fe92b67bab5f98dc
ms.sourcegitcommit: bc9a4904c2b1561386d748fc9ac242699d2f1694
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/04/2020
ms.locfileid: "76995429"
---
# <a name="using-jea"></a><span data-ttu-id="6d9ba-103">JEA gebruiken</span><span class="sxs-lookup"><span data-stu-id="6d9ba-103">Using JEA</span></span>

<span data-ttu-id="6d9ba-104">In dit artikel worden de verschillende manieren beschreven waarop u verbinding kunt maken met een JEA-eind punt.</span><span class="sxs-lookup"><span data-stu-id="6d9ba-104">This article describes the various ways you can connect to and use a JEA endpoint.</span></span>

## <a name="using-jea-interactively"></a><span data-ttu-id="6d9ba-105">JEA interactief gebruiken</span><span class="sxs-lookup"><span data-stu-id="6d9ba-105">Using JEA interactively</span></span>

<span data-ttu-id="6d9ba-106">Als u uw JEA-configuratie test of eenvoudige taken voor gebruikers hebt, kunt u JEA op dezelfde manier gebruiken als een normale externe Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="6d9ba-106">If you're testing your JEA configuration or have simple tasks for users, you can use JEA the same way you would a regular PowerShell remoting session.</span></span> <span data-ttu-id="6d9ba-107">Voor complexe externe taken is het raadzaam [impliciete externe communicatie](#using-jea-with-implicit-remoting)te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="6d9ba-107">For complex remoting tasks, it's recommended to use [implicit remoting](#using-jea-with-implicit-remoting).</span></span> <span data-ttu-id="6d9ba-108">Met impliciete externe toegang kunnen gebruikers lokaal met de gegevens objecten worden gewerkt.</span><span class="sxs-lookup"><span data-stu-id="6d9ba-108">Implicit remoting allows users to operate with the data objects locally.</span></span>

<span data-ttu-id="6d9ba-109">Als u JEA interactief wilt gebruiken, hebt u het volgende nodig:</span><span class="sxs-lookup"><span data-stu-id="6d9ba-109">To use JEA interactively, you need:</span></span>

- <span data-ttu-id="6d9ba-110">De naam van de computer waarmee u verbinding maakt (kan de lokale computer zijn)</span><span class="sxs-lookup"><span data-stu-id="6d9ba-110">The name of the computer you're connecting to (can be the local machine)</span></span>
- <span data-ttu-id="6d9ba-111">De naam van het JEA-eind punt dat op die computer is geregistreerd</span><span class="sxs-lookup"><span data-stu-id="6d9ba-111">The name of the JEA endpoint registered on that computer</span></span>
- <span data-ttu-id="6d9ba-112">Referenties die toegang hebben tot het JEA-eind punt op die computer</span><span class="sxs-lookup"><span data-stu-id="6d9ba-112">Credentials that have access to the JEA endpoint on that computer</span></span>

<span data-ttu-id="6d9ba-113">Op basis van deze informatie kunt u een JEA-sessie starten met de cmdlets [New-PSSession](/powershell/module/microsoft.powershell.core/New-PSSession) of [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) .</span><span class="sxs-lookup"><span data-stu-id="6d9ba-113">Given that information, you can start a JEA session using the [New-PSSession](/powershell/module/microsoft.powershell.core/New-PSSession) or [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) cmdlets.</span></span>

```powershell
$nonAdminCred = Get-Credential
Enter-PSSession -ComputerName localhost -ConfigurationName JEAMaintenance -Credential $nonAdminCred
```

<span data-ttu-id="6d9ba-114">Als het huidige gebruikers account toegang heeft tot het JEA-eind punt, kunt u de **referentie** parameter weglaten.</span><span class="sxs-lookup"><span data-stu-id="6d9ba-114">If the current user account has access to the JEA endpoint, you can omit the **Credential** parameter.</span></span>

<span data-ttu-id="6d9ba-115">Wanneer de Power shell-prompt wordt gewijzigd in `[localhost]: PS>` weet u dat u nu met de externe JEA-sessie werkt.</span><span class="sxs-lookup"><span data-stu-id="6d9ba-115">When the PowerShell prompt changes to `[localhost]: PS>` you know that you're now interacting with the remote JEA session.</span></span> <span data-ttu-id="6d9ba-116">U kunt `Get-Command` uitvoeren om te controleren welke opdrachten beschikbaar zijn.</span><span class="sxs-lookup"><span data-stu-id="6d9ba-116">You can run `Get-Command` to check which commands are available.</span></span> <span data-ttu-id="6d9ba-117">Neem contact op met uw beheerder om te zien of er beperkingen gelden voor de beschik bare para meters of toegestane parameter waarden.</span><span class="sxs-lookup"><span data-stu-id="6d9ba-117">Consult with your administrator to learn if there are any restrictions on the available parameters or allowed parameter values.</span></span>

<span data-ttu-id="6d9ba-118">Houd er rekening mee dat JEA-sessies in de modus voor niet-taal worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="6d9ba-118">Remember, JEA sessions operate in NoLanguage mode.</span></span> <span data-ttu-id="6d9ba-119">Sommige manieren waarop u Power shell normaal gesp roken gebruikt, zijn mogelijk niet beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="6d9ba-119">Some of the ways you typically use PowerShell may not be available.</span></span> <span data-ttu-id="6d9ba-120">U kunt bijvoorbeeld geen variabelen gebruiken om gegevens op te slaan of de eigenschappen te controleren op objecten die worden geretourneerd door cmdlets.</span><span class="sxs-lookup"><span data-stu-id="6d9ba-120">For instance, you can't use variables to store data or inspect the properties on objects returned from cmdlets.</span></span> <span data-ttu-id="6d9ba-121">In het volgende voor beeld ziet u twee benaderingen waarmee u dezelfde opdrachten kunt gebruiken om te werken in de modus niet-taal.</span><span class="sxs-lookup"><span data-stu-id="6d9ba-121">The following example shows two approaches to get the same commands to work in NoLanguage mode.</span></span>

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

<span data-ttu-id="6d9ba-122">Voor complexere opdracht aanroepen die ervoor zorgen dat deze aanpak lastig wordt, kunt u overwegen [impliciet externe communicatie](#using-jea-with-implicit-remoting) te gebruiken of [aangepaste functies te maken](role-capabilities.md#creating-custom-functions) waarmee de functionaliteit die u nodig hebt, wordt gereduceerd.</span><span class="sxs-lookup"><span data-stu-id="6d9ba-122">For more complex command invocations that make this approach difficult, consider using [implicit remoting](#using-jea-with-implicit-remoting) or [creating custom functions](role-capabilities.md#creating-custom-functions) that wrap the functionality you require.</span></span>

## <a name="using-jea-with-implicit-remoting"></a><span data-ttu-id="6d9ba-123">JEA gebruiken met impliciete externe communicatie</span><span class="sxs-lookup"><span data-stu-id="6d9ba-123">Using JEA with implicit remoting</span></span>

<span data-ttu-id="6d9ba-124">Power Shell heeft een impliciet extern model waarmee u proxy-cmdlets kunt importeren vanaf een externe computer en met hen communiceert alsof het lokale opdrachten zijn.</span><span class="sxs-lookup"><span data-stu-id="6d9ba-124">PowerShell has an implicit remoting model that lets you import proxy cmdlets from a remote machine and interact with them as if they were local commands.</span></span> <span data-ttu-id="6d9ba-125">Impliciete externe communicatie wordt uitgelegd in deze **Hey, Scripting Guy!**</span><span class="sxs-lookup"><span data-stu-id="6d9ba-125">Implicit remoting is explained in this **Hey, Scripting Guy!**</span></span> <span data-ttu-id="6d9ba-126">[blog bericht](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/).</span><span class="sxs-lookup"><span data-stu-id="6d9ba-126">[blog post](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/).</span></span>
<span data-ttu-id="6d9ba-127">Impliciete externe toegang is handig bij het werken met JEA omdat u hiermee kunt werken met JEA-cmdlets in een volledige taal modus.</span><span class="sxs-lookup"><span data-stu-id="6d9ba-127">Implicit remoting is useful when working with JEA because it allows you to work with JEA cmdlets in a full language mode.</span></span> <span data-ttu-id="6d9ba-128">U kunt tabblad aanvulling, variabelen, objecten bewerken en zelfs lokale scripts gebruiken om taken te automatiseren op basis van een JEA-eind punt.</span><span class="sxs-lookup"><span data-stu-id="6d9ba-128">You can use tab completion, variables, manipulate objects, and even use local scripts to automate tasks against a JEA endpoint.</span></span> <span data-ttu-id="6d9ba-129">Telkens wanneer u een proxy opdracht aanroept, worden de gegevens naar het JEA-eind punt op de externe computer verzonden en daar uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="6d9ba-129">Anytime you invoke a proxy command, the data is sent to the JEA endpoint on the remote machine and executed there.</span></span>

<span data-ttu-id="6d9ba-130">Impliciete externe toegang werkt door cmdlets uit een bestaande Power shell-sessie te importeren.</span><span class="sxs-lookup"><span data-stu-id="6d9ba-130">Implicit remoting works by importing cmdlets from an existing PowerShell session.</span></span> <span data-ttu-id="6d9ba-131">U kunt desgewenst kiezen voor het voor voegsel van de naam woorden van elke proxy-cmdlet met een teken reeks van uw keuze.</span><span class="sxs-lookup"><span data-stu-id="6d9ba-131">You can optionally choose to prefix the nouns of each proxy cmdlet with a string of your choosing.</span></span> <span data-ttu-id="6d9ba-132">Met het voor voegsel kunt u de opdrachten van het externe systeem onderscheiden.</span><span class="sxs-lookup"><span data-stu-id="6d9ba-132">The prefix allows you to distinguish the commands that are for the remote system.</span></span> <span data-ttu-id="6d9ba-133">Er wordt een tijdelijke script module met alle proxy opdrachten gemaakt en geïmporteerd voor de duur van uw lokale Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="6d9ba-133">A temporary script module containing all the proxy commands is created and imported for the duration of your local PowerShell session.</span></span>

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Import the entire PSSession and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA'

# Invoke "Get-Command" on the remote JEA endpoint using the proxy cmdlet
Get-JEACommand
```

> [!IMPORTANT]
> <span data-ttu-id="6d9ba-134">Sommige systemen kunnen mogelijk geen hele JEA-sessie importeren vanwege beperkingen in de standaard-JEA-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="6d9ba-134">Some systems may not be able to import an entire JEA session due to constraints in the default JEA cmdlets.</span></span> <span data-ttu-id="6d9ba-135">Als u dit wilt omzeilen, importeert u alleen de opdrachten die u nodig hebt uit de JEA-sessie door expliciet hun namen te verstrekken aan de para meter `-CommandName`.</span><span class="sxs-lookup"><span data-stu-id="6d9ba-135">To get around this, only import the commands you need from the JEA session by explicitly providing their names to the `-CommandName` parameter.</span></span> <span data-ttu-id="6d9ba-136">In een toekomstige update wordt het probleem opgelost waarbij hele JEA-sessies op betrokken systemen worden geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="6d9ba-136">A future update will address the issue with importing entire JEA sessions on affected systems.</span></span>

<span data-ttu-id="6d9ba-137">Als u een JEA-sessie niet kunt importeren vanwege JEA-beperkingen voor de standaard parameters, volgt u de onderstaande stappen om de standaard opdrachten uit de geïmporteerde set uit te filteren.</span><span class="sxs-lookup"><span data-stu-id="6d9ba-137">If you're unable to import a JEA session because of JEA constraints on the default parameters, follow the steps below to filter out the default commands from the imported set.</span></span> <span data-ttu-id="6d9ba-138">U kunt opdrachten als `Select-Object`blijven gebruiken, maar u gebruikt gewoon de lokale versie die op uw computer is geïnstalleerd, in plaats van het item dat is geïmporteerd uit de sessie voor externe JEA.</span><span class="sxs-lookup"><span data-stu-id="6d9ba-138">You can continue use commands like `Select-Object`, but you'll just use the local version installed on your computer instead of the one imported from the remote JEA session.</span></span>

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

<span data-ttu-id="6d9ba-139">U kunt ook de proxy-cmdlets van impliciete externe communicatie met [export-PSSession](/powershell/microsoft.powershell.utility/Export-PSSession)behouden.</span><span class="sxs-lookup"><span data-stu-id="6d9ba-139">You can also persist the proxied cmdlets from implicit remoting using [Export-PSSession](/powershell/microsoft.powershell.utility/Export-PSSession).</span></span>
<span data-ttu-id="6d9ba-140">Zie de documentatie voor [import-PSSession](/powershell/microsoft.powershell.utility/import-pssession) en [import-module](/powershell/microsoft.powershell.core/import-module)voor meer informatie over impliciete externe communicatie.</span><span class="sxs-lookup"><span data-stu-id="6d9ba-140">For more information about implicit remoting, see the documentation for [Import-PSSession](/powershell/microsoft.powershell.utility/import-pssession) and [Import-Module](/powershell/microsoft.powershell.core/import-module).</span></span>

## <a name="using-jea-programmatically"></a><span data-ttu-id="6d9ba-141">JEA via een programma gebruiken</span><span class="sxs-lookup"><span data-stu-id="6d9ba-141">Using JEA programmatically</span></span>

<span data-ttu-id="6d9ba-142">JEA kan ook worden gebruikt in automation-systemen en in gebruikers toepassingen, zoals interne helpdesk-apps en websites.</span><span class="sxs-lookup"><span data-stu-id="6d9ba-142">JEA can also be used in automation systems and in user applications, such as in-house helpdesk apps and websites.</span></span> <span data-ttu-id="6d9ba-143">De benadering is hetzelfde als die voor het bouwen van apps die praten met onbeperkte Power shell-eind punten.</span><span class="sxs-lookup"><span data-stu-id="6d9ba-143">The approach is the same as that for building apps that talk to unconstrained PowerShell endpoints.</span></span> <span data-ttu-id="6d9ba-144">Zorg ervoor dat het programma is ontworpen om te werken met beperkingen die zijn opgelegd door JEA.</span><span class="sxs-lookup"><span data-stu-id="6d9ba-144">Ensure the program is designed to work with limitation imposed by JEA.</span></span>

<span data-ttu-id="6d9ba-145">Voor eenvoudige, eenmalige taken kunt u [invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) gebruiken om opdrachten uit te voeren in een JEA-sessie.</span><span class="sxs-lookup"><span data-stu-id="6d9ba-145">For simple, one-off tasks, you can use [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) to run commands in a JEA session.</span></span>

```powershell
Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Process; Get-Service }
```

<span data-ttu-id="6d9ba-146">Als u wilt controleren welke opdrachten beschikbaar zijn voor gebruik wanneer u verbinding maakt met een JEA-sessie, voert u `Get-Command` uit en herhaalt u de resultaten om te controleren of de para meters zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="6d9ba-146">To check which commands are available for use when you connect to a JEA session, run `Get-Command` and iterate through the results to check for the allowed parameters.</span></span>

```powershell
$allowedCommands = Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Command }
$allowedCommands | Where-Object { $_.CommandType -in 'Function', 'Cmdlet' } | Format-Table Name, Parameters
```

<span data-ttu-id="6d9ba-147">Als u een C# app bouwt, kunt u een Power shell-runs Pace maken die verbinding maakt met een JEA-sessie door de configuratie naam op te geven in een [WSManConnectionInfo](/dotnet/api/system.management.automation.runspaces.wsmanconnectioninfo) -object.</span><span class="sxs-lookup"><span data-stu-id="6d9ba-147">If you're building a C# app, you can create a PowerShell runspace that connects to a JEA session by specifying the configuration name in a [WSManConnectionInfo](/dotnet/api/system.management.automation.runspaces.wsmanconnectioninfo) object.</span></span>

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
    string.Format(CultureInfo.InvariantCulture, "https://schemas.microsoft.com/powershell/{0}", configName),
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

## <a name="using-jea-with-powershell-direct"></a><span data-ttu-id="6d9ba-148">JEA gebruiken met Power shell direct</span><span class="sxs-lookup"><span data-stu-id="6d9ba-148">Using JEA with PowerShell Direct</span></span>

<span data-ttu-id="6d9ba-149">Hyper-V in Windows 10 en Windows Server 2016 biedt [Power shell direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct), een functie waarmee Hyper-V-beheerders virtuele machines met Power shell kunnen beheren, ongeacht de instellingen van de netwerk configuratie of extern beheer op de virtuele machine.</span><span class="sxs-lookup"><span data-stu-id="6d9ba-149">Hyper-V in Windows 10 and Windows Server 2016 offers [PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct), a feature that allows Hyper-V administrators to manage virtual machines with PowerShell regardless of the network configuration or remote management settings on the virtual machine.</span></span>

<span data-ttu-id="6d9ba-150">U kunt Power shell direct met JEA gebruiken om een Hyper-V-beheerder beperkte toegang tot uw virtuele machine te geven.</span><span class="sxs-lookup"><span data-stu-id="6d9ba-150">You can use PowerShell Direct with JEA to give a Hyper-V administrator limited access to your VM.</span></span>
<span data-ttu-id="6d9ba-151">Dit kan handig zijn als u de netwerk verbinding met uw virtuele machine kwijtraakt en een datacenter beheerder nodig hebt om de netwerk instellingen te herstellen.</span><span class="sxs-lookup"><span data-stu-id="6d9ba-151">This can be useful if you lose network connectivity to your VM and need a datacenter admin to fix the network settings.</span></span>

<span data-ttu-id="6d9ba-152">Er is geen aanvullende configuratie vereist om JEA te gebruiken via Power shell direct.</span><span class="sxs-lookup"><span data-stu-id="6d9ba-152">No additional configuration is required to use JEA over PowerShell Direct.</span></span> <span data-ttu-id="6d9ba-153">Het gast besturingssysteem dat wordt uitgevoerd in de virtuele machine moet echter Windows 10, Windows Server 2016 of hoger zijn.</span><span class="sxs-lookup"><span data-stu-id="6d9ba-153">However, the guest operating system running inside the virtual machine must be Windows 10, Windows Server 2016, or higher.</span></span> <span data-ttu-id="6d9ba-154">De Hyper-V-beheerder kan verbinding maken met het JEA-eind punt met behulp van de `-VMName`-of `-VMId`-para meters in PSRemoting-cmdlets:</span><span class="sxs-lookup"><span data-stu-id="6d9ba-154">The Hyper-V admin can connect to the JEA endpoint by using the `-VMName` or `-VMId` parameters on PSRemoting cmdlets:</span></span>

```powershell
# Entering a JEA session using PowerShell Direct when the VM name is unique
Enter-PSSession -VMName 'SQL01' -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'

# Entering a JEA session using PowerShell Direct using VM ids
$vm = Get-VM -VMName 'MyVM' | Select-Object -First 1
Enter-PSSession -VMId $vm.VMId -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'
```

<span data-ttu-id="6d9ba-155">U kunt het beste een speciaal gebruikers account maken met de minimale rechten die nodig zijn om het systeem te beheren voor gebruik door een Hyper-V-beheerder.</span><span class="sxs-lookup"><span data-stu-id="6d9ba-155">It's recommended you create a dedicated user account with the minimum rights needed to manage the system for use by a Hyper-V administrator.</span></span> <span data-ttu-id="6d9ba-156">Houd er rekening mee dat zelfs een niet-gemachtigde gebruiker zich standaard kan aanmelden bij een Windows-computer, met inbegrip van een onbeperkte Power shell.</span><span class="sxs-lookup"><span data-stu-id="6d9ba-156">Remember, even an unprivileged user can sign into a Windows machine by default, including using unconstrained PowerShell.</span></span> <span data-ttu-id="6d9ba-157">Op die manier kunnen ze door het bestands systeem bladeren en meer informatie krijgen over uw besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="6d9ba-157">That allows them to browse the file system and learn more about your OS environment.</span></span> <span data-ttu-id="6d9ba-158">Als u een Hyper-V-beheerder wilt vergren delen en deze alleen wilt gebruiken om toegang te krijgen tot een virtuele machine met behulp van Power shell direct met JEA, moet u lokale aanmeldings rechten voor het JEA-account van de Hyper-V-beheerder weigeren.</span><span class="sxs-lookup"><span data-stu-id="6d9ba-158">To lock down a Hyper-V administrator and limit them to only access a VM using PowerShell Direct with JEA, you must deny local logon rights to the Hyper-V admin's JEA account.</span></span>
