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
# <a name="using-jea"></a>JEA gebruiken

Dit artikel beschrijft de verschillende manieren waarop u kunt verbinding maken met en gebruiken van een JEA-eindpunt.

## <a name="using-jea-interactively"></a>JEA interactief gebruiken

Als u de configuratie van uw JEA test of eenvoudige taken voor gebruikers hebt, kunt u de dezelfde manier als een reguliere PowerShell voor externe toegang-sessie JEA gebruiken. Voor externe communicatie van complexe taken, is het raadzaam te gebruiken [impliciete externe communicatie](#using-jea-with-implicit-remoting). Impliciete externe communicatie kan gebruikers met de gegevensobjecten lokaal werken.

Voor het gebruik van JEA interactief, hebt u het volgende nodig:

- De naam van de computer waarmee u verbinding (kan de lokale computer zijn)
- De naam van de JEA-eindpunt dat is geregistreerd op die computer
- De referenties die toegang tot de JEA-eindpunt op die computer hebben

Deze informatie verstrekt, kunt u start een JEA-sessie met de [New-PSSession](/powershell/module/microsoft.powershell.core/New-PSSession) of [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) cmdlets.

```powershell
$nonAdminCred = Get-Credential
Enter-PSSession -ComputerName localhost -ConfigurationName JEAMaintenance -Credential $nonAdminCred
```

Als het account van de huidige gebruiker toegang tot de JEA-eindpunt heeft, kunt u weglaten de **referentie** parameter.

Wanneer de PowerShell wijzigingen aan vragen `[localhost]: PS>` u weet dat u bent nu interactie is met de externe JEA-sessie. U kunt uitvoeren `Get-Command` om te controleren welke opdrachten zijn beschikbaar. Neem contact op met uw beheerder voor meer informatie of er beperkingen voor de beschikbare parameters of de toegestane waarden zijn.

Let op: JEA-sessies in NoLanguage modus werken. Aantal manieren waarop die u doorgaans gebruik van PowerShell is mogelijk niet beschikbaar. U kunt de variabelen bijvoorbeeld niet gebruiken voor het opslaan van gegevens of Controleer de eigenschappen van objecten die zijn geretourneerd door cmdlets. Het volgende voorbeeld ziet twee methoden voor het ophalen van dezelfde opdrachten NoLanguage modus.

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

Voor complexere aanroepen van de opdracht die deze benadering moeilijk maken, kunt u overwegen [impliciete externe communicatie](#using-jea-with-implicit-remoting) of [maken van aangepaste functies](role-capabilities.md#creating-custom-functions) die verpakken met de functionaliteit die u nodig hebt.

## <a name="using-jea-with-implicit-remoting"></a>JEA gebruiken met impliciete externe communicatie

PowerShell is een impliciete externe communicatie-model waarmee u cmdlets van webtoepassingsproxy importeren vanaf een externe computer en er interactie mee alsof deze lokaal opdrachten. Impliciete externe communicatie wordt uitgelegd in deze **Hallo, Scripting Guy!** [blogbericht](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/).
Impliciete externe communicatie is handig bij het werken met JEA omdat Hiermee kunt u werken met de JEA-cmdlets in een taalmodus voor volledig. U kunt tabvoltooiing, variabelen, manipuleren van objecten en zelfs lokale scripts gebruiken voor het automatiseren van taken in een JEA-eindpunt. Telkens wanneer u een proxy-opdracht aanroepen, worden de gegevens worden verzonden naar de JEA-eindpunt op de externe computer en er wordt uitgevoerd.

Impliciete externe communicatie werkt door het importeren van de cmdlets van een bestaande PowerShell-sessie. U kunt eventueel aan het voorvoegsel van de zelfstandige naamwoorden van elke cmdlet proxy met een tekenreeks van uw keuze. Het voorvoegsel kunt u te onderscheiden van de opdrachten die bestemd voor het externe systeem zijn. Een tijdelijke scriptmodule met alle opdrachten die de proxy is gemaakt en geïmporteerd voor de duur van uw lokale PowerShell-sessie.

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Import the entire PSSession and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA'

# Invoke "Get-Command" on the remote JEA endpoint using the proxy cmdlet
Get-JEACommand
```

> [!IMPORTANT]
> Sommige systemen kunnen pas weer voor het importeren van een hele JEA-sessie vanwege beperkingen in de standaard JEA-cmdlets. Als u lost dit, alleen importeren opdrachten die u nodig van de JEA-sessie door expliciet hun namen naar de `-CommandName` parameter. Een toekomstige update heeft betrekking op het probleem met het importeren van volledige JEA-sessies op de geïnfecteerde systemen.

Als u niet voor het importeren van een JEA-sessie vanwege beperkingen in de standaardparameters JEA, de volgende stappen voor het filteren van de opdrachten die standaard in de geïmporteerde verzameling. U kunt doorgaan met de opdrachten, zoals `Select-Object`, maar u alleen de lokale versie is geïnstalleerd op uw computer in plaats van een geïmporteerd uit de externe JEA-sessie.

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

U kunt ook de via proxy-cmdlets van het gebruik van de impliciete externe communicatie behouden [Export-PSSession](/powershell/microsoft.powershell.utility/Export-PSSession).
Voor meer informatie over de impliciete externe communicatie, Zie de documentatie voor [Import-PSSession](/powershell/microsoft.powershell.utility/import-pssession) en [Import-Module](/powershell/microsoft.powershell.core/import-module).

## <a name="using-jea-programmatically"></a>JEA via een programma gebruiken

JEA kan ook worden gebruikt in automation-systemen en toepassingen, zoals interne helpdesk-apps en websites. De aanpak is hetzelfde als die voor het bouwen van apps die met onbeperkte PowerShell-eindpunten communiceren. Zorg ervoor dat het programma is ontworpen voor gebruik met de beperking die zijn opgelegd door JEA.

Voor eenvoudige eenmalige taken, kunt u [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) opdrachten kunt uitvoeren in een JEA-sessie.

```powershell
Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Process; Get-Service }
```

Uitvoeren als u wilt controleren welke opdrachten zijn beschikbaar voor gebruik wanneer u verbinding met een JEA-sessie maakt, `Get-Command` en de resultaten om te controleren voor de toegestane parameters doorlopen.

```powershell
$allowedCommands = Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Command }
$allowedCommands | Where-Object { $_.CommandType -in 'Function', 'Cmdlet' } | Format-Table Name, Parameters
```

Als u een C# app, kunt u een PowerShell-runspace die verbinding met een JEA-sessie maakt door op te geven de configuratienaam van de in een [WSManConnectionInfo](/dotnet/api/system.management.automation.runspaces.wsmanconnectioninfo) object.

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

## <a name="using-jea-with-powershell-direct"></a>JEA gebruiken met PowerShell Direct

Hyper-V in Windows 10 en Windows Server 2016 biedt [PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct), een functie waarmee Hyper-V-administrators voor het beheren van virtuele machines met PowerShell, ongeacht de netwerkconfiguratie of extern beheer de instellingen op de virtuele machine.

U kunt PowerShell Direct met JEA gebruiken op een Hyper-V-beheerder beperkte toegang geven tot uw virtuele machine.
Dit kan nuttig zijn als u hebt een datacenter-beheerder om op te lossen de netwerkinstellingen en verliest netwerkverbinding met uw virtuele machine.

Geen aanvullende configuratie is vereist voor het gebruik van JEA via PowerShell Direct. Windows 10, WindowsServer 2016 of hoger moet echter van het gastbesturingssysteem die binnen de virtuele machine wordt uitgevoerd. De Hyper-V-beheerder kan verbinding maken met de JEA-eindpunt met behulp van de `-VMName` of `-VMId` parameters op PSRemoting-cmdlets:

```powershell
# Entering a JEA session using PowerShell Direct when the VM name is unique
Enter-PSSession -VMName 'SQL01' -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'

# Entering a JEA session using PowerShell Direct using VM ids
$vm = Get-VM -VMName 'MyVM' | Select-Object -First 1
Enter-PSSession -VMId $vm.VMId -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'
```

Het wordt aanbevolen dat een specifieke gebruikersaccount te maken met de minimale rechten die nodig zijn voor het beheren van het systeem voor gebruik door de beheerder van een Hyper-V. Onthoud dat ook een niet-gemachtigde gebruikers kan zich aanmelden bij een Windows-machine standaard, inclusief het gebruik van onbeperkte PowerShell. Waarmee ze kunnen bladeren in het bestandssysteem en meer informatie over de omgeving van uw besturingssysteem. Als u wilt vergrendelen van een beheerder van een Hyper-V en beperken zodat ze alleen toegang tot een virtuele machine met behulp van PowerShell Direct met JEA, moet u lokale aanmeldingsrechten naar JEA-account van de Hyper-V-beheerder weigeren.
