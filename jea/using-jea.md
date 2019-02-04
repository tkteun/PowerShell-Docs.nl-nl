---
ms.date: 06/12/2017
keywords: jea, powershell, beveiliging
title: JEA gebruiken
ms.openlocfilehash: 539d280aff0b2656a5e9c710acfa468057753027
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686857"
---
# <a name="using-jea"></a>JEA gebruiken

> Van toepassing op: Windows PowerShell 5.0

Dit onderwerp beschrijft de verschillende manieren waarop u kunt verbinding maken met en gebruiken van een JEA-eindpunt.

## <a name="using-jea-interactively"></a>JEA interactief gebruiken

Als u de JEA-configuratie testen wilt of eenvoudige taken voor gebruikers om uit te voeren, kunt u de dezelfde manier als een reguliere PowerShell voor externe toegang-sessie JEA gebruiken.
Voor externe communicatie van complexe taken, is het raadzaam te gebruiken [impliciete externe communicatie](#using-jea-with-implicit-remoting) in plaats daarvan te vereenvoudigen voor uw gebruikers doordat gebruikers werken met de gegevens objecten lokaal.

Voor het gebruik van JEA interactief, gaat u te werk:
- De naam van de computer die u verbinding maakt (kan de lokale computer zijn)
- De naam van de JEA-eindpunt dat is geregistreerd op die computer
- Referenties voor de computer die toegang tot de JEA-eindpunt hebben

Met deze informatie beschikt, kunt u starten een JEA-sessie met [New-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSSession) of [Enter-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/enter-pssession).

```powershell
$nonAdminCred = Get-Credential
Enter-PSSession -ComputerName localhost -ConfigurationName JEAMaintenance -Credential $nonAdminCred
```

Als het account dat u bent momenteel aangemeld als toegang tot de JEA-eindpunt heeft, kunt u weglaten de `-Credential` parameter.

Wanneer de PowerShell wijzigingen aan vragen `[localhost]: PS>` weet u dat u nu met de externe JEA-sessie communiceert.
U kunt uitvoeren `Get-Command` om te controleren welke opdrachten zijn beschikbaar.
U moet Neem contact op met uw beheerder voor meer informatie als er beperkingen voor de beschikbare parameters of de toegestane parameterwaarden.

Als een herinnering werken JEA-sessies in de modus NoLanguage, zodat sommige van de manieren die doorgaans u PowerShell gebruikt niet meer beschikbaar zijn.
U kunt de variabelen bijvoorbeeld niet gebruiken voor het opslaan van gegevens of Controleer de eigenschappen van objecten die zijn geretourneerd door cmdlets.
Het onderstaande voorbeeld ziet u een voorbeeld van hoe u gebruikt PowerShell vandaag nog en twee methoden voor het ophalen van dezelfde opdracht in de modus NoLanguage werkt.

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

Voor complexere aanroepen van de opdracht die deze benadering moeilijk maken, kunt u overwegen [impliciete externe communicatie](#using-jea-with-implicit-remoting) of [maken van aangepaste functies](role-capabilities.md#creating-custom-functions) die de gewenste functionaliteit verpakken.

## <a name="using-jea-with-implicit-remoting"></a>JEA gebruiken met impliciete externe communicatie

PowerShell ondersteunt een alternatief voor externe toegang-model kunt u cmdlets van webtoepassingsproxy importeren vanaf een externe computer op uw lokale computer en er interactie mee alsof deze lokaal opdrachten.
Dit heet impliciete externe communicatie, en wordt uitgelegd in goed [dit *Hallo, Scripting Guy!* blogbericht](https://blogs.technet.microsoft.com/heyscriptingguy/2013/09/08/remoting-the-implicit-way/).
Impliciete externe communicatie is met name handig bij het werken met JEA omdat Hiermee kunt u werken met de JEA-cmdlets in een taalmodus voor volledig.
Dit betekent dat u kunt gebruiken tab-aanvulling, variabelen, objecten bewerken, en zelfs lokale scripts gebruiken om het eenvoudig automatiseren op basis van een JEA-eindpunt.
Telkens wanneer u een proxy-opdracht aanroepen, worden de gegevens verzonden naar de JEA-eindpunt op de externe computer en er wordt uitgevoerd.

Impliciete externe communicatie werkt door het importeren van de cmdlets van een bestaande PowerShell-sessie.
U kunt eventueel aan het voorvoegsel van de zelfstandige naamwoorden van elke cmdlet proxy met een tekenreeks van uw keuze te onderscheiden welke opdrachten zijn voor het externe systeem.
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
> Sommige systemen kunnen pas weer voor het importeren van een hele JEA-sessie vanwege beperkingen in de standaard JEA-cmdlets.
> Als u lost dit, alleen importeren opdrachten die u nodig van de JEA-sessie door expliciet hun namen naar de `-CommandName` parameter.
> Een toekomstige update heeft betrekking op het probleem met het importeren van volledige JEA-sessies op de geïnfecteerde systemen.

Als u zich niet voor het importeren van een JEA-sessie vanwege beperkingen met betrekking tot de standaardparameters van JEA, kunt u de volgende stappen voor het filteren van de opdrachten die standaard in de geïmporteerde verzameling.
Kunt u zich nog steeds gebruik van opdrachten zoals `Select-Object` --u alleen de lokale versie is geïnstalleerd op uw computer in plaats van het externe certificaat in de JEA-sessie.

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

U kunt ook de via proxy-cmdlets van het gebruik van de impliciete externe communicatie behouden [Export-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/Export-PSSession).
Voor meer informatie over de impliciete externe communicatie, bekijkt u de help-documentatie voor [Import-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/import-pssession) en [Import-Module](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/import-module).

## <a name="using-jea-programatically"></a>Programmatisch met behulp van JEA

JEA kan ook worden gebruikt in automation-systemen en toepassingen, zoals interne helpdesk-apps en websites.
De aanpak is hetzelfde als die voor het bouwen van apps die met onbeperkte PowerShell-eindpunten, met het voorbehoud communiceren dat het programma moet rekening houden JEA beperken van de opdrachten die kunnen worden uitgevoerd in de externe sessie.

Voor eenvoudige eenmalige taken, kunt u [Invoke-Command](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/invoke-command) om uit te voeren van een reeks opdrachten JEA gebruiken.

```powershell
Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Process; Get-Service }
```

Uitvoeren als u wilt controleren welke opdrachten zijn beschikbaar voor gebruik wanneer u verbinding met een JEA-sessie maakt, `Get-Command` en de resultaten om te controleren voor de toegestane parameters doorlopen.

```powershell
$allowedCommands = Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Command }
$allowedCommands | Where-Object { $_.CommandType -in 'Function', 'Cmdlet' } | Format-Table Name, Parameters
```

Als u een C#-app bouwt, kunt u een PowerShell-runspace die verbinding met een JEA-sessie maakt door op te geven de configuratienaam van de in een [WSManConnectionInfo](https://msdn.microsoft.com/library/system.management.automation.runspaces.wsmanconnectioninfo(v=vs.85).aspx) object.

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

## <a name="using-jea-with-powershell-direct"></a>JEA gebruiken met PowerShell Direct

Hyper-V in Windows 10 en Windows Server 2016 biedt [PowerShell Direct](https://msdn.microsoft.com/virtualization/hyperv_on_windows/user_guide/vmsession), een functie waarmee Hyper-V-administrators voor het beheren van virtuele machines met PowerShell, ongeacht de netwerkconfiguratie of extern beheer de instellingen op de virtuele machine.

U kunt PowerShell Direct met JEA gebruiken een Hyper-V beperkte beheerder om toegang te geven aan uw virtuele machine, die kan nuttig zijn als u verbinding met het netwerk met uw virtuele machine verloren en een datacenter-beheerder moet oplossen om de netwerkinstellingen.

Er is geen aanvullende configuratie vereist voor het gebruik van JEA via PowerShell Direct, maar het besturingssysteem wordt uitgevoerd in de virtuele machine Windows 10 of Windows Server 2016 moet.
De Hyper-V-beheerder kan verbinding maken met de JEA-eindpunt met behulp van de `-VMName` of `-VMId` parameters op PSRemoting-cmdlets:

```powershell
# Entering a JEA session using PowerShell Direct when the VM name is unique
Enter-PSSession -VMName 'SQL01' -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'

# Entering a JEA session using PowerShell Direct using VM ids
$vm = Get-VM -VMName 'MyVM' | Select-Object -First 1
Enter-PSSession -VMId $vm.VMId -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'
```

Het is raadzaam dat u een toegewezen lokale gebruiker met geen andere rechten maken voor het beheren van het systeem uw Hyper-V-beheerders moeten gebruiken.
Houd er rekening mee dat zelfs een niet-gemachtigde gebruiker nog steeds zich bij een Windows-machine standaard aanmelden kan, inclusief het gebruik van onbeperkte PowerShell.
Die hen om te bladeren (aantal) in staat het bestandssysteem en meer informatie over de omgeving van uw besturingssysteem.
Als u wilt de beheerder van een Hyper-V alleen toegang tot een virtuele machine met behulp van PowerShell Direct met JEA vergrendelen, moet u lokale aanmeldingsrechten naar JEA-account van de Hyper-V-beheerder weigeren.