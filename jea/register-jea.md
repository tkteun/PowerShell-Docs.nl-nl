---
ms.date: 2017-06-12
author: rpsqrd
ms.topic: conceptual
keywords: jea powershell beveiliging
title: JEA configuraties registreren
ms.openlocfilehash: d6b007fed97be6470bfe4cf4d42f72cb4edc3a45
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/15/2018
---
# <a name="registering-jea-configurations"></a>JEA configuraties registreren

> Van toepassing op: Windows PowerShell 5.0

De laatste stap voordat u JEA kunt zodra u hebt uw [rol mogelijkheden](role-capabilities.md) en [sessie configuratiebestand](session-configurations.md) gemaakt is voor het registreren van het eindpunt JEA.
Dit proces de sessie-configuratie-informatie is van toepassing op het systeem en het eindpunt beschikbaar voor gebruik door gebruikers en de automation-engines.

## <a name="single-machine-configuration"></a>Configuratie van één machine

Voor kleine omgevingen, kunt u JEA implementeren via het registreren van de sessie configuratie bestand met de [Register-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/register-pssessionconfiguration) cmdlet.

Zorg ervoor dat de volgende vereisten is voldaan voordat u begint:
- Een of meer rollen is gemaakt en opgeslagen in de map 'RoleCapabilities' van een geldig PowerShell-module.
- Een sessie-configuratiebestand is gemaakt en getest.
- De gebruiker registreren van de configuratie van de JEA heeft administrator-rechten op de systemen.

U moet ook een naam voor uw eindpunt JEA selecteren.
De naam van het eindpunt JEA is vereist wanneer gebruikers verbinding wilt maken met het systeem met JEA.
U kunt de [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet om de namen van bestaande eindpunten op het systeem te controleren.
Eindpunten die met 'microsoft beginnen' zijn doorgaans geleverd bij Windows.
Het eindpunt 'microsoft.powershell' is het standaardeindpunt gebruikt bij het verbinden met een externe PowerShell-eindpunt.

```powershell
PS C:\> Get-PSSessionConfiguration | Select-Object Name

Name
----
microsoft.powershell
microsoft.powershell.workflow
microsoft.powershell32
```

Wanneer u een passende naam voor uw eindpunt JEA hebt vastgesteld, voert u de volgende opdracht voor het registreren van het eindpunt.

```powershell
Register-PSSessionConfiguration -Path .\MyJEAConfig.pssc -Name 'JEAMaintenance' -Force
```

> [!WARNING]
> De bovenstaande opdracht wordt de WinRM-service op het systeem opnieuw opstarten
> Dit wordt beëindigd op alle externe communicatie van PowerShell-sessies, evenals een eventuele lopende DSC-configuraties.
> Het is raadzaam dat u eventuele productiemachines offline uitvoeren voordat u de opdracht uit te voeren om te voorkomen dat zakelijke activiteiten verstoren.

Als de registratie gelukt is, bent u klaar om [JEA gebruiken](using-jea.md).
U kunt het configuratiebestand van de sessie op elk gewenst moment; verwijderen Dit wordt niet gebruikt na de registratie.

## <a name="multi-machine-configuration-with-dsc"></a>Meerdere machines met DSC-configuratie

Als u JEA op meerdere machines implementeert, wordt het eenvoudigste implementatiemodel is het gebruik van de JEA [Desired State Configuration](https://msdn.microsoft.com/en-us/powershell/dsc/overview) resource snel en consistent JEA implementeren op elke machine.

Als u wilt implementeren JEA met DSC, moet u moet dat de volgende vereisten worden voldaan:
- Een of meer rollen mogelijkheden zijn gemaakt en toegevoegd aan een geldig PowerShell-module.
- De PowerShell-module met de rollen is opgeslagen op een (alleen-lezen) bestandsshare die toegankelijk door elke computer.
- Instellingen voor de sessieconfiguratie van de zijn vastgesteld. U hoeft niet te maken van een configuratiebestand sessie bij het gebruik van de JEA DSC-resource.
- U hebt de referenties die u kunt u beheeracties uitvoeren op elke machine of toegang hebben tot een DSC-pull-server gebruikt voor het beheren van de machines.
- U hebt gedownload de [JEA DSC-resource](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource)

Maak een DSC-configuratie voor uw eindpunt JEA op een doel-machine (of pull-server, als u van een gebruikmaakt).
In deze configuratie gebruikt u de JustEnoughAdministration DSC-resource voor het instellen van het configuratiebestand van de sessie en de resource bestand kopiëren over de mogelijkheden van de rol van de bestandsshare.

De volgende eigenschappen kunnen worden geconfigureerd met behulp van de DSC-resource:
- Roldefinities
- Groepen met virtuele
- De naam van groep beheerd serviceaccount gebruiken
- De tekst van directory
- Schijf van de gebruiker
- Regels voor voorwaardelijke toegang
- Opstartscripts voor de sessie JEA

De syntaxis voor elk van deze eigenschappen in een DSC-configuratie komt overeen met het configuratiebestand van de PowerShell-sessie.

Hieronder volgt een voorbeeld DSC-configuratie voor een algemene server Onderhoud module.

Er wordt ervan uitgegaan dat een geldig PowerShell-module met de mogelijkheden van de rol in een submap 'RoleCapabilities' bevindt zich op de '\\\\myfileshare\\JEA' bestandsshare.


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

Deze configuratie kan vervolgens worden toegepast op een systeem door [rechtstreeks aanroepen van de lokale Configuration Manager](https://msdn.microsoft.com/en-us/powershell/dsc/metaconfig) of bijwerken van de [pull-serverconfiguratie](https://msdn.microsoft.com/en-us/powershell/dsc/pullserver).

De DSC-resource kunt u het standaardeindpunt van Microsoft.PowerShell remoting vervangen.
Als u dit doet, wordt automatisch een back-unconstrainted-eindpunt met de naam 'Microsoft.PowerShell.Restricted' met de standaardinstellingen van de WinRM-ACL (zodat gebruikers van extern beheer en lokale beheerders groepsleden om deze te openen) geregistreerd in de resource.

## <a name="unregistering-jea-configurations"></a>Registratie JEA-configuraties

U kunt een JEA-eindpunt op een systeem met de [Unregister-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet.
De registratie van een eindpunt JEA wordt voorkomen dat nieuwe gebruikers maken van nieuwe JEA sessies op het systeem.
Ook kunt u de configuratie van een JEA bijwerken door een bijgewerkte sessie-configuratiebestand met dezelfde naam van het eindpunt opnieuw te registreren.

```powershell
# Unregister the JEA endpoint called "ContosoMaintenance"
Unregister-PSSessionConfiguration -Name 'ContosoMaintenance' -Force
```

> [!WARNING]
> De registratie van een JEA eindpunt zorgt ervoor dat de WinRM-service opnieuw op te starten.
> Hiermee wordt de meeste RAS beheerbewerkingen in voortgang, inclusief andere PowerShell-sessies, WMI-aanroepen en sommige beheerhulpprogramma's onderbroken.
> Alleen de PowerShell-eindpunten registratie tijdens gepland onderhoud.

## <a name="next-steps"></a>Volgende stappen

- [Het eindpunt JEA testen](using-jea.md)

