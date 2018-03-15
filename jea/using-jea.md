---
ms.date: 2017-06-12
author: rpsqrd
ms.topic: conceptual
keywords: jea powershell beveiliging
title: Met behulp van JEA
ms.openlocfilehash: f0c22bf0f823b9fafa203e7f98049a6a6b3b7c05
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/15/2018
---
# <a name="using-jea"></a>Met behulp van JEA

> Van toepassing op: Windows PowerShell 5.0

In dit onderwerp beschrijft de verschillende manieren kunt u verbinding maken met en een eindpunt JEA gebruiken.

## <a name="using-jea-interactively"></a>JEA interactief gebruiken

Als u de configuratie van uw JEA testen wilt of eenvoudige taken zijn voor gebruikers om uit te voeren, kunt u JEA dezelfde manier als u een PowerShell-sessie voor reguliere remoting doet.
Voor externe communicatie van complexe taken, is het raadzaam te gebruiken [impliciete remoting](#using-jea-with-implicit-remoting) in plaats daarvan om het gemakkelijker voor gebruikers omdat gebruikers kunnen werken met de gegevens objecten lokaal.

JEA als interactief wilt gebruiken, moet u:
- De naam van de computer die u verbinding maakt (kunnen zijn voor de lokale computer)
- De naam van het eindpunt JEA is geregistreerd op die computer
- Referenties voor de computer die toegang tot het eindpunt JEA hebben

Met deze informatie beschikt, kunt u starten een JEA-sessie met [New-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSSession) of [Enter-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/enter-pssession).

```powershell
$nonAdminCred = Get-Credential
Enter-PSSession -ComputerName localhost -ConfigurationName JEAMaintenance -Credential $nonAdminCred
```

Als het account dat u bent momenteel aangemeld als toegang tot het eindpunt JEA heeft, kunt u weglaten de `-Credential` parameter.

Wanneer de PowerShell prompt voor wijzigingen in `[localhost]: PS>` weet u dat u nu met de externe JEA-sessie communiceert.
U kunt uitvoeren `Get-Command` om te controleren welke opdrachten beschikbaar zijn.
U moet Neem contact op met uw beheerder voor meer informatie over als er beperkingen op de beschikbare parameters of toegestane parameterwaarden.

Als een herinnering werken JEA sessies in NoLanguage modus, zodat een aantal manieren waarop die u doorgaans PowerShell gebruiken mogelijk niet beschikbaar.
U kunt variabelen bijvoorbeeld niet gebruiken voor het opslaan van gegevens of Controleer de eigenschappen van objecten die zijn geretourneerd door cmdlets.
Het onderstaande voorbeeld ziet u een voorbeeld van hoe u mogelijk gebruikmaken van PowerShell vandaag en twee benaderingen voor dezelfde opdracht in de modus NoLanguage werkt.

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

Voor complexere opdracht aanroepen die moeilijk maken om deze benadering kunt u overwegen [impliciete remoting](#using-jea-with-implicit-remoting) of [maken van aangepaste functies](role-capabilities.md#creating-custom-functions) die de functionaliteit die u wenst teruglopen.

## <a name="using-jea-with-implicit-remoting"></a>Met behulp van JEA met impliciete voor externe toegang

PowerShell ondersteunt een alternatieve remoting model waarin u webtoepassingsproxy-cmdlets importeren uit een externe computer op uw lokale computer en ermee alsof ze lokaal opdrachten.
Dit impliciete remoting wordt aangeroepen en wordt uitgelegd in goed [dit *artikel van Hey, Scripting Guy!* blogbericht](https://blogs.technet.microsoft.com/heyscriptingguy/2013/09/08/remoting-the-implicit-way/).
Impliciete remoting is bijzonder nuttig bij het werken met JEA omdat deze kunt u werken met JEA cmdlets in een taalmodus voor volledig.
Dit betekent dat gebruik tab-aanvulling, variabelen, objecten bewerken en zelfs lokale scripts gebruiken voor het voor een eindpunt JEA gemakkelijker worden geautomatiseerd.
Telkens wanneer u een proxy-opdracht aanroepen, worden de gegevens verzonden naar het eindpunt JEA op de externe computer en er wordt uitgevoerd.

Impliciete remoting werkt door cmdlets importeren uit een bestaande PowerShell-sessie.
U kunt eventueel als voorvoegsel voor de woorden van elke cmdlet proxy met een tekenreeks van uw keuze te onderscheiden welke opdrachten zijn voor het externe systeem.
Een tijdelijke scriptmodule met alle van de proxy-opdrachten wordt gemaakt en kan worden gebruikt voor de duur van uw lokale PowerShell-sessie.

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Import the entire PSSession and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA'

# Invoke "Get-Command" on the remote JEA endpoint using the proxy cmdlet
Get-JEACommand
```

> [!IMPORTANT]
> Sommige systemen kan mogelijk niet een hele JEA-sessie als gevolg van beperkingen in de standaard JEA cmdlets importeren.
> Om dit probleem omzeilen alleen importeren de opdrachten die u moet uit de sessie JEA door expliciet hun namen voor de `-CommandName` parameter.
> Een toekomstige update heeft betrekking op het probleem met het importeren van de hele JEA sessies op de geïnfecteerde systemen.

Als u niet voor het importeren van een sessie JEA vanwege beperkingen voor de standaardparameters voor JEA, kunt u de volgende stappen om de standaardopdrachten van de geïmporteerde set uitfilteren volgen.
U zich nog steeds gebruik van opdrachten zoals `Select-Object` --u alleen de lokale versie is geïnstalleerd op uw computer in plaats van het externe certificaat in de sessie JEA.

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

U kunt ook deze persistent maken de cmdlets via een proxyserver doorgestuurd vanuit impliciete remoting met [Export-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/Export-PSSession).
Bekijk voor meer informatie over impliciete remoting, de documentatie voor [Import-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/import-pssession) en [Import-Module](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/import-module).

## <a name="using-jea-programatically"></a>Met behulp van JEA via programmacode

JEA kan ook worden gebruikt in automation-systemen en gebruikerstoepassingen, zoals intern helpdesk apps en websites.
De aanpak is hetzelfde als die voor het bouwen van apps die Neem op met onbeperkte PowerShell eindpunten, hoewel contact dat het programma moet rekening houden JEA beperken van de opdrachten die in de externe sessie kunnen worden uitgevoerd.

U kunt gebruiken voor eenvoudige eenmalige taken, [Invoke-Command](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/invoke-command) een set van JEA-opdrachten uitvoeren.

```powershell
Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Process; Get-Service }
```

Uitvoeren om te zien welke opdrachten zijn beschikbaar voor gebruik wanneer u verbinding met een sessie JEA maakt, `Get-Command` en de resultaten om te controleren voor de toegestane parameters doorlopen.

```powershell
$allowedCommands = Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Command }
$allowedCommands | Where-Object { $_.CommandType -in 'Function', 'Cmdlet' } | Format-Table Name, Parameters
```

Als u een C#-app maakt, kunt u een PowerShell-runspace die verbinding met een JEA-sessie maakt door te geven van de configuratienaam van de in een [WSManConnectionInfo](https://msdn.microsoft.com/en-us/library/system.management.automation.runspaces.wsmanconnectioninfo(v=vs.85).aspx) object.

```csharp

// using System.Management.Automation;
var computerName = "SERVER01";
var configName   = "JEAMaintenance";
var creds        = // create a PSCredential object here (https://msdn.microsoft.com/en-us/library/system.management.automation.pscredential(v=vs.85).aspx)

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

## <a name="using-jea-with-powershell-direct"></a>JEA met PowerShell Direct gebruiken

Hyper-V in Windows 10 en Windows Server 2016 biedt [PowerShell Direct](https://msdn.microsoft.com/en-us/virtualization/hyperv_on_windows/user_guide/vmsession), een functie waarmee Hyper-V-Administrators kunnen virtuele machines met PowerShell ongeacht de netwerkconfiguratie of beheer op afstand beheren de instellingen op de virtuele machine.

U kunt PowerShell Direct met JEA een Hyper-V-beheerder beperkte toegang geven tot uw virtuele machine, die nuttig kunnen zijn als u een datacenter-beheerder hebt om op te lossen de netwerkinstellingen en netwerkverbinding wordt verbroken met uw virtuele machine.

Geen aanvullende configuratie is vereist voor het gebruik van JEA via PowerShell directe, maar het besturingssysteem op de virtuele machine Windows 10 of Windows Server 2016 moet.
De Hyper-V-beheer verbinding kan maken met het eindpunt JEA met behulp van de `-VMName` of `-VMId` parameters op PSRemoting-cmdlets:

```powershell
# Entering a JEA session using PowerShell Direct when the VM name is unique
Enter-PSSession -VMName 'SQL01' -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'

# Entering a JEA session using PowerShell Direct using VM ids
$vm = Get-VM -VMName 'MyVM' | Select-Object -First 1
Enter-PSSession -VMId $vm.VMId -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'
```

Het is raadzaam dat u een specifieke lokale gebruiker met geen andere rechten gemaakt voor het beheren van het systeem voor uw Hyper-V-beheerders om te gebruiken.
Houd er rekening mee dat zelfs een onbevoegde gebruiker zich nog steeds bij een Windows-machine standaard aanmelden kan, inclusief het gebruik van onbeperkte PowerShell.
Waarmee ze om te bladeren (enkele van) het bestandssysteem en meer informatie over uw OS-omgeving.
Als u wilt vergrendelen tot een virtuele machine met behulp van PowerShell Direct met JEA heeft alleen toegang tot een beheerder van de Hyper-V, moet u lokale aanmeldingsrechten aan de Hyper-V-beheer JEA account weigeren.

