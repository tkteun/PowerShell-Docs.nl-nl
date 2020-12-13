---
ms.date: 07/10/2019
keywords: JEA, Power shell, beveiliging
title: JEA gebruiken
description: In dit artikel worden de verschillende manieren beschreven waarop u verbinding kunt maken met een JEA-eind punt.
ms.openlocfilehash: b3d81cc0aa76549c81136e5a1a5af28df9c6fa7a
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92501538"
---
# <a name="using-jea"></a>JEA gebruiken

In dit artikel worden de verschillende manieren beschreven waarop u verbinding kunt maken met een JEA-eind punt.

## <a name="using-jea-interactively"></a>JEA interactief gebruiken

Als u uw JEA-configuratie test of eenvoudige taken voor gebruikers hebt, kunt u JEA op dezelfde manier gebruiken als een normale externe Power shell-sessie. Voor complexe externe taken is het raadzaam [impliciete externe communicatie](#using-jea-with-implicit-remoting)te gebruiken. Met impliciete externe toegang kunnen gebruikers lokaal met de gegevens objecten worden gewerkt.

Als u JEA interactief wilt gebruiken, hebt u het volgende nodig:

- De naam van de computer waarmee u verbinding maakt (kan de lokale computer zijn)
- De naam van het JEA-eind punt dat op die computer is geregistreerd
- Referenties die toegang hebben tot het JEA-eind punt op die computer

Op basis van deze informatie kunt u een JEA-sessie starten met de cmdlets [New-PSSession](/powershell/module/microsoft.powershell.core/New-PSSession) of [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) .

```powershell
$nonAdminCred = Get-Credential
Enter-PSSession -ComputerName localhost -ConfigurationName JEAMaintenance -Credential $nonAdminCred
```

Als het huidige gebruikers account toegang heeft tot het JEA-eind punt, kunt u de **referentie** parameter weglaten.

Wanneer de Power shell-prompt wordt gewijzigd, `[localhost]: PS>` weet u zeker dat u nu met de externe JEA-sessie werkt. U kunt uitvoeren `Get-Command` om te controleren welke opdrachten beschikbaar zijn. Neem contact op met uw beheerder om te zien of er beperkingen gelden voor de beschik bare para meters of toegestane parameter waarden.

Houd er rekening mee dat JEA-sessies in de modus voor niet-taal worden uitgevoerd. Sommige manieren waarop u Power shell normaal gesp roken gebruikt, zijn mogelijk niet beschikbaar. U kunt bijvoorbeeld geen variabelen gebruiken om gegevens op te slaan of de eigenschappen te controleren op objecten die worden geretourneerd door cmdlets. In het volgende voor beeld ziet u twee benaderingen waarmee u dezelfde opdrachten kunt gebruiken om te werken in de modus niet-taal.

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

Voor complexere opdracht aanroepen die ervoor zorgen dat deze aanpak lastig wordt, kunt u overwegen [impliciet externe communicatie](#using-jea-with-implicit-remoting) te gebruiken of [aangepaste functies te maken](role-capabilities.md#creating-custom-functions) waarmee de functionaliteit die u nodig hebt, wordt gereduceerd.

## <a name="using-jea-with-implicit-remoting"></a>JEA gebruiken met impliciete externe communicatie

Power Shell heeft een impliciet extern model waarmee u proxy-cmdlets kunt importeren vanaf een externe computer en met hen communiceert alsof het lokale opdrachten zijn. Impliciete externe communicatie wordt uitgelegd in deze **Hey, Scripting Guy!** [blog bericht](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/).
Impliciete externe toegang is handig bij het werken met JEA omdat u hiermee kunt werken met JEA-cmdlets in een volledige taal modus. U kunt tabblad aanvulling, variabelen, objecten bewerken en zelfs lokale scripts gebruiken om taken te automatiseren op basis van een JEA-eind punt. Telkens wanneer u een proxy opdracht aanroept, worden de gegevens naar het JEA-eind punt op de externe computer verzonden en daar uitgevoerd.

Impliciete externe toegang werkt door cmdlets uit een bestaande Power shell-sessie te importeren. U kunt desgewenst kiezen voor het voor voegsel van de naam woorden van elke proxy-cmdlet met een teken reeks van uw keuze. Met het voor voegsel kunt u de opdrachten van het externe systeem onderscheiden. Er wordt een tijdelijke script module met alle proxy opdrachten gemaakt en geïmporteerd voor de duur van uw lokale Power shell-sessie.

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Import the entire PSSession and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA'

# Invoke "Get-Command" on the remote JEA endpoint using the proxy cmdlet
Get-JEACommand
```

> [!IMPORTANT]
> Sommige systemen kunnen mogelijk geen hele JEA-sessie importeren vanwege beperkingen in de standaard-JEA-cmdlets. Als u dit wilt omzeilen, importeert u alleen de opdrachten die u nodig hebt uit de JEA-sessie door expliciet hun namen te verstrekken aan de `-CommandName` para meter. In een toekomstige update wordt het probleem opgelost waarbij hele JEA-sessies op betrokken systemen worden geïmporteerd.

Als u een JEA-sessie niet kunt importeren vanwege JEA-beperkingen voor de standaard parameters, volgt u de onderstaande stappen om de standaard opdrachten uit de geïmporteerde set uit te filteren. U kunt opdrachten zoals gebruiken `Select-Object` , maar u gebruikt gewoon de lokale versie die op uw computer is geïnstalleerd, in plaats van het item dat is geïmporteerd uit de externe JEA-sessie.

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

U kunt ook de proxy-cmdlets van impliciete externe communicatie met [export-PSSession](/powershell/module/microsoft.powershell.utility/Export-PSSession)behouden.
Zie de documentatie voor [import-PSSession](/powershell/module/microsoft.powershell.utility/import-pssession) en [import-module](/powershell/module/microsoft.powershell.core/import-module)voor meer informatie over impliciete externe communicatie.

## <a name="using-jea-programmatically"></a>JEA via een programma gebruiken

JEA kan ook worden gebruikt in automation-systemen en in gebruikers toepassingen, zoals interne helpdesk-apps en websites. De benadering is hetzelfde als die voor het bouwen van apps die praten met onbeperkte Power shell-eind punten. Zorg ervoor dat het programma is ontworpen om te werken met beperkingen die zijn opgelegd door JEA.

Voor eenvoudige, eenmalige taken kunt u [invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) gebruiken om opdrachten uit te voeren in een JEA-sessie.

```powershell
Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Process; Get-Service }
```

Als u wilt controleren welke opdrachten beschikbaar zijn voor gebruik wanneer u verbinding maakt met een JEA-sessie, voert u uit `Get-Command` en herhaalt u de resultaten om te controleren of de para meters zijn toegestaan.

```powershell
$allowedCommands = Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Command }
$allowedCommands | Where-Object { $_.CommandType -in 'Function', 'Cmdlet' } | Format-Table Name, Parameters
```

Als u een C#-app bouwt, kunt u een Power shell-runs Pace maken die verbinding maakt met een JEA-sessie door de configuratie naam op te geven in een [WSManConnectionInfo](/dotnet/api/system.management.automation.runspaces.wsmanconnectioninfo) -object.

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

## <a name="using-jea-with-powershell-direct"></a>JEA gebruiken met Power shell direct

Hyper-V in Windows 10 en Windows Server 2016 biedt [Power shell direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct), een functie waarmee Hyper-V-beheerders virtuele machines met Power shell kunnen beheren, ongeacht de instellingen van de netwerk configuratie of extern beheer op de virtuele machine.

U kunt Power shell direct met JEA gebruiken om een Hyper-V-beheerder beperkte toegang tot uw virtuele machine te geven.
Dit kan handig zijn als u de netwerk verbinding met uw virtuele machine kwijtraakt en een datacenter beheerder nodig hebt om de netwerk instellingen te herstellen.

Er is geen aanvullende configuratie vereist om JEA te gebruiken via Power shell direct. Het gast besturingssysteem dat wordt uitgevoerd in de virtuele machine moet echter Windows 10, Windows Server 2016 of hoger zijn. De Hyper-V-beheerder kan verbinding maken met het JEA-eind punt met behulp van de `-VMName` `-VMId` para meters of in PSRemoting-cmdlets:

```powershell
# Entering a JEA session using PowerShell Direct when the VM name is unique
Enter-PSSession -VMName 'SQL01' -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'

# Entering a JEA session using PowerShell Direct using VM ids
$vm = Get-VM -VMName 'MyVM' | Select-Object -First 1
Enter-PSSession -VMId $vm.VMId -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'
```

U kunt het beste een speciaal gebruikers account maken met de minimale rechten die nodig zijn om het systeem te beheren voor gebruik door een Hyper-V-beheerder. Houd er rekening mee dat zelfs een niet-gemachtigde gebruiker zich standaard kan aanmelden bij een Windows-computer, met inbegrip van een onbeperkte Power shell. Op die manier kunnen ze door het bestands systeem bladeren en meer informatie krijgen over uw besturings systeem. Als u een Hyper-V-beheerder wilt vergren delen en deze alleen wilt gebruiken om toegang te krijgen tot een virtuele machine met behulp van Power shell direct met JEA, moet u lokale aanmeldings rechten voor het JEA-account van de Hyper-V-beheerder weigeren.
