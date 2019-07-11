---
ms.date: 07/10/2019
keywords: jea, powershell, beveiliging
title: Configuraties van JEA registreren
ms.openlocfilehash: c85eddea2196e4db4bbeea54bde11074f3d1c927
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726625"
---
# <a name="registering-jea-configurations"></a>Configuraties van JEA registreren

Zodra u hebt uw [rolmogelijkheden](role-capabilities.md) en [sessie configuratiebestand](session-configurations.md) gemaakt, de laatste stap bestaat uit het registreren van de JEA-eindpunt. De JEA-eindpunt registreren met het systeem, wordt het eindpunt beschikbaar voor gebruik door gebruikers en automation-engines.

## <a name="single-machine-configuration"></a>De configuratie van één machine

Voor kleine omgevingen, kunt u JEA implementeren door het registreren van de sessie configuratie bestand met de [Register-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/register-pssessionconfiguration) cmdlet.

Voordat u begint, zorg ervoor dat de volgende vereisten wordt voldaan:

- Een of meer rollen zijn gemaakt en geplaatst de **RoleCapabilities** map van een PowerShell-module.
- Een configuratiebestand voor de sessie is gemaakt en getest.
- De gebruiker die de configuratie van de JEA registreren heeft beheerdersrechten op het systeem.
- U kunt een naam voor uw JEA-eindpunt hebt geselecteerd.

De naam van de JEA-eindpunt is vereist wanneer gebruikers verbinding maken met het systeem JEA gebruiken. De [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) cmdlet worden de namen van de eindpunten in een systeem. Eindpunten die met beginnen `microsoft` worden doorgaans geleverd met Windows. De `microsoft.powershell` -eindpunt is de standaardeindpunt dat wordt gebruikt bij het verbinden met een externe PowerShell-eindpunt.

```powershell
Get-PSSessionConfiguration | Select-Object Name
```

```Output
Name
----
microsoft.powershell
microsoft.powershell.workflow
microsoft.powershell32
```

Voer de volgende opdracht om het registreren van het eindpunt.

```powershell
Register-PSSessionConfiguration -Path .\MyJEAConfig.pssc -Name 'JEAMaintenance' -Force
```

> [!WARNING]
> De vorige opdracht de WinRM-service op het systeem opnieuw is opgestart. Dit wordt beëindigd voor alle PowerShell-sessies voor externe toegang en alle lopende DSC-configuraties. Wij raden dat u productiemachines offline nemen voordat de opdracht uit om te voorkomen dat zakelijke verstoren.

Na de registratie, kunt u [JEA gebruiken](using-jea.md). U kunt het configuratiebestand van de sessie op elk gewenst moment verwijderen. Het configuratiebestand wordt niet na de registratie van het eindpunt gebruikt.

## <a name="multi-machine-configuration-with-dsc"></a>Configuratie met meerdere machines met DSC

Bij het implementeren van JEA op meerdere machines, het eenvoudigste implementatiemodel gebruikmaakt van de JEA [Desired State Configuration (DSC)](/powershell/dsc/overview) resource die u wilt snel en consistent JEA implementeren op elke computer.

Voor het implementeren van JEA met DSC, zorg ervoor dat de volgende vereisten wordt voldaan:

- Een of meer rolmogelijkheden zijn gemaakt en toegevoegd aan een PowerShell-module.
- De PowerShell-module met de rollen die zijn opgeslagen op een toegankelijke (alleen-lezen) bestandsshare elke machine.
- Instellingen voor de sessieconfiguratie van de zijn vastgesteld. U hoeft te maken van een configuratiebestand voor de sessie bij het gebruik van de JEA-DSC-resource.
- Hebt u referenties waarmee administratieve taken op elke computer of de toegang tot de DSC-pull-server gebruikt voor het beheren van de virtuele machines.
- U hebt gedownload de [JEA DSC-resource](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource).

Maak een DSC-configuratie voor de JEA-eindpunt op een computer of een pull-server. In deze configuratie de **JustEnoughAdministration** DSC-resource definieert het configuratiebestand van de sessie en de **bestand** resource kopieert de rolmogelijkheden van de bestandsshare.

De volgende eigenschappen kunnen worden geconfigureerd met behulp van de DSC-resource:

- Roldefinities
- Virtuele groepen
- Naam van groep beheerd serviceaccount
- Transcript directory
- Schijf van de gebruiker
- Regels voor voorwaardelijke toegang
- Opstartscripts voor de JEA-sessie

De syntaxis voor elk van deze eigenschappen in een DSC-configuratie is consistent met het configuratiebestand van de PowerShell-sessie.

Hieronder volgt een voorbeeld van DSC-configuratie voor een algemene server Onderhoud-module. Hierbij wordt ervan uitgegaan dat een geldig PowerShell-module met rolmogelijkheden bevindt zich op de `\\myfileshare\JEA` -bestandsshare.

```powershell
Configuration JEAMaintenance
{
    Import-DscResource -Module JustEnoughAdministration, PSDesiredStateConfiguration

    File MaintenanceModule
    {
        SourcePath = "\\myfileshare\JEA\ContosoMaintenance"
        DestinationPath = "C:\Program Files\WindowsPowerShell\Modules\ContosoMaintenance"
        Checksum = "SHA-256"
        Ensure = "Present"
        Type = "Directory"
        Recurse = $true
    }

    JeaEndpoint JEAMaintenanceEndpoint
    {
        EndpointName = "JEAMaintenance"
        RoleDefinitions = "@{ 'CONTOSO\JEAMaintenanceAuditors' = @{ RoleCapabilities = 'GeneralServerMaintenance-Audit' }; 'CONTOSO\JEAMaintenanceAdmins' = @{ RoleCapabilities = 'GeneralServerMaintenance-Audit', 'GeneralServerMaintenance-Admin' } }"
        TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
        DependsOn = '[File]MaintenanceModule'
    }
}
```

Vervolgens de configuratie is toegepast op een systeem door het rechtstreeks aanroepen van de [Local Configuration Manager](/powershell/dsc/managing-nodes/metaConfig) of bijwerken van de [pull-serverconfiguratie](/powershell/dsc/pull-server/pullServer).

De DSC-resource ook kunt u de standaard vervangen **Microsoft.PowerShell** eindpunt. Wanneer de vervangen, registreert de resource automatisch een back-eindpunt met de naam **Microsoft.PowerShell.Restricted**. Het eindpunt van de back-up is de standaard-WinRM-ACL waarmee u kunt gebruikers van extern beheer- en lokale beheerders groepsleden om deze te openen.

## <a name="unregistering-jea-configurations"></a>De registratie JEA-configuraties

De [Unregister-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet een JEA-eindpunt wordt verwijderd. Registratie van een JEA-eindpunt wordt voorkomen dat nieuwe gebruikers van het maken van nieuwe JEA-sessies op het systeem. U kunt er ook een JEA-configuratie bijwerken door een bijgewerkte sessie-configuratiebestand met dezelfde naam van het eindpunt opnieuw te registreren.

```powershell
# Unregister the JEA endpoint called "ContosoMaintenance"
Unregister-PSSessionConfiguration -Name 'ContosoMaintenance' -Force
```

> [!WARNING]
> Een JEA registratie eindpunt zorgt ervoor dat de WinRM-service opnieuw te starten. Dit meest externe bewerkingen wordt uitgevoerd, met inbegrip van andere PowerShell-sessies, WMI-aanroepen en sommige beheerprogramma's-interrupts. Alleen de registratie PowerShell eindpunten verwijderen tijdens gepland onderhoud.

## <a name="next-steps"></a>Volgende stappen

[De JEA-eindpunt testen](using-jea.md)
