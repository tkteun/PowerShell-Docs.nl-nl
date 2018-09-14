---
ms.date: 06/12/2017
keywords: jea, powershell, beveiliging
title: Configuraties van JEA registreren
ms.openlocfilehash: 2c4a8f64c966903a6eb8fcabe4cd25ae7f98b2c4
ms.sourcegitcommit: e46b868f56f359909ff7c8230b1d1770935cce0e
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45522847"
---
# <a name="registering-jea-configurations"></a>Configuraties van JEA registreren

> Is van toepassing op: Windows PowerShell 5.0

De laatste stap voordat u JEA gebruiken kunt zodra u hebt uw [rolmogelijkheden](role-capabilities.md) en [sessie configuratiebestand](session-configurations.md) gemaakt is voor het registreren van de JEA-eindpunt.
Dit proces de sessie-configuratie-informatie is van toepassing op het systeem en het eindpunt beschikbaar voor gebruik door gebruikers en automation-engines.

## <a name="single-machine-configuration"></a>De configuratie van één machine

Voor kleine omgevingen, kunt u JEA implementeren door het registreren van de sessie configuratie bestand met de [Register-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/register-pssessionconfiguration) cmdlet.

Voordat u begint, zorg ervoor dat de volgende vereisten wordt voldaan:
- Een of meer rollen is gemaakt en opgeslagen in de map 'RoleCapabilities' van een geldig PowerShell-module.
- Een configuratiebestand voor de sessie is gemaakt en getest.
- De gebruiker die de configuratie van de JEA registreren heeft administrator-rechten op de systemen.

U moet ook een naam voor uw JEA-eindpunt selecteren.
De naam van de JEA-eindpunt is vereist wanneer gebruikers verbinding maken met het systeem JEA gebruiken.
U kunt de [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet om te controleren of de namen van bestaande eindpunten op het systeem.
Eindpunten die met 'microsoft beginnen' worden doorgaans geleverd met Windows.
Het eindpunt 'microsoft.powershell' is de standaardeindpunt dat wordt gebruikt bij het verbinden met een externe PowerShell-eindpunt.

```powershell
PS C:\> Get-PSSessionConfiguration | Select-Object Name

Name
----
microsoft.powershell
microsoft.powershell.workflow
microsoft.powershell32
```

Wanneer u een passende naam voor uw JEA-eindpunt hebt bepaald, voer de volgende opdracht voor het registreren van het eindpunt.

```powershell
Register-PSSessionConfiguration -Path .\MyJEAConfig.pssc -Name 'JEAMaintenance' -Force
```

> [!WARNING]
> De bovenstaande opdracht wordt de WinRM-service op het systeem opnieuw.
> Dit wordt beëindigd als alle externe communicatie van PowerShell-sessies, evenals alle lopende DSC-configuraties.
> Het is raadzaam dat u een productiemachines offline nemen voordat de opdracht uit om te voorkomen dat zakelijke verstoren.

Als de registratie gelukt is, bent u klaar om te [JEA gebruiken](using-jea.md).
U kunt het configuratiebestand van de sessie op elk gewenst moment; verwijderen het wordt niet gebruikt na de registratie.

## <a name="multi-machine-configuration-with-dsc"></a>Configuratie met meerdere machines met DSC

Als u JEA op meerdere machines implementeert, wordt het eenvoudigste implementatiemodel is het gebruik van de JEA [Desired State Configuration](https://msdn.microsoft.com/powershell/dsc/overview) resource die u wilt snel en consistent JEA implementeren op elke computer.

Voor het implementeren van JEA met DSC, moet u ervoor zorgen dat aan de volgende vereisten wordt voldaan:
- Een of meer rolmogelijkheden zijn gemaakt en toegevoegd aan een geldig PowerShell-module.
- De PowerShell-module met de rollen die zijn opgeslagen op een toegankelijke (alleen-lezen) bestandsshare elke machine.
- Instellingen voor de sessieconfiguratie van de zijn vastgesteld. U hoeft niet te maken van een configuratiebestand voor de sessie bij het gebruik van de JEA-DSC-resource.
- Hebt u de referenties die u kunt u beheeracties uitvoeren op elke computer of toegang hebben tot een DSC-pull-server gebruikt voor het beheren van de virtuele machines.
- U hebt gedownload de [JEA DSC-resource](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource)

Op een doel (of pull-server, als u van een gebruikmaakt), een DSC-configuratie voor de JEA-eindpunt te maken.
In deze configuratie gebruikt u de JustEnoughAdministration DSC-resource voor het instellen van het configuratiebestand van de sessie en de resource bestand moeten worden gekopieerd van de rolmogelijkheden van de bestandsshare.

De volgende eigenschappen kunnen worden geconfigureerd met behulp van de DSC-resource:
- Roldefinities
- Virtuele groepen
- Naam van groep beheerd serviceaccount
- Transcript directory
- Schijf van de gebruiker
- Regels voor voorwaardelijke toegang
- Opstartscripts voor de JEA-sessie

De syntaxis voor elk van deze eigenschappen in een DSC-configuratie is consistent met het configuratiebestand van de PowerShell-sessie.

Hieronder volgt een voorbeeld van DSC-configuratie voor een algemene server Onderhoud-module.

Hierbij wordt ervan uitgegaan dat een geldig PowerShell-module met de rolmogelijkheden in een submap 'RoleCapabilities' bevindt zich op de '\\\\myfileshare\\JEA'-bestandsshare.


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

Deze configuratie kan vervolgens worden toegepast op een systeem met [rechtstreeks aanroepen van de Local Configuration Manager](https://msdn.microsoft.com/powershell/dsc/metaconfig) of bijwerken van de [pull-serverconfiguratie](https://msdn.microsoft.com/powershell/dsc/pullserver).

De DSC-resources kunt u het standaardeindpunt voor de externe communicatie van Microsoft.PowerShell vervangen.
Als u dit doet, wordt automatisch een back-up unconstrainted-eindpunt met de naam 'Microsoft.PowerShell.Restricted' met de standaard-WinRM-ACL (zodat gebruikers van extern beheer- en lokale beheerders groepsleden om deze te openen) registreren in de resource.

## <a name="unregistering-jea-configurations"></a>De registratie JEA-configuraties

Als u wilt een JEA-eindpunt op een systeem verwijderen, gebruikt u de [Unregister-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet.
Registratie van een JEA-eindpunt wordt voorkomen dat nieuwe gebruikers het maken van nieuwe JEA-sessies op het systeem.
U kunt er ook een JEA-configuratie bijwerken door een bijgewerkte sessie-configuratiebestand met dezelfde naam van het eindpunt opnieuw te registreren.

```powershell
# Unregister the JEA endpoint called "ContosoMaintenance"
Unregister-PSSessionConfiguration -Name 'ContosoMaintenance' -Force
```

> [!WARNING]
> Een JEA registratie eindpunt zorgt ervoor dat de WinRM-service opnieuw te starten.
> Dit wordt de meeste RAS beheerbewerkingen in uitvoering, met inbegrip van andere PowerShell-sessies, WMI-aanroepen en sommige beheerhulpprogramma onderbroken.
> Alleen de registratie PowerShell eindpunten verwijderen tijdens gepland onderhoud.

## <a name="next-steps"></a>Volgende stappen

- [De JEA-eindpunt testen](using-jea.md)