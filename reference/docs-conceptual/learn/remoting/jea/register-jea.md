---
ms.date: 07/10/2019
keywords: JEA, Power shell, beveiliging
title: JEA-configuraties registreren
ms.openlocfilehash: 7cc67e891bc14dd667c97e9a8b550b33b4c2b874
ms.sourcegitcommit: 0a3f9945d52e963e9cba2538ffb33e42156e1395
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/27/2020
ms.locfileid: "77706203"
---
# <a name="registering-jea-configurations"></a>JEA-configuraties registreren

Zodra u uw [functie mogelijkheden](role-capabilities.md) en [sessie configuratie bestand](session-configurations.md) hebt gemaakt, is de laatste stap het JEA-eind punt te registreren. Als het JEA-eind punt wordt geregistreerd bij het systeem, wordt het eind punt beschikbaar voor gebruik door gebruikers en automatiserings engines.

## <a name="single-machine-configuration"></a>Configuratie van één computer

Voor kleine omgevingen kunt u JEA implementeren door het sessie configuratie bestand te registreren met de cmdlet [REGI ster-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/register-pssessionconfiguration) .

Voordat u begint, moet u ervoor zorgen dat aan de volgende vereisten is voldaan:

- Een of meer rollen zijn gemaakt en geplaatst in de map **RoleCapabilities** van een Power shell-module.
- Er is een sessie configuratie bestand gemaakt en getest.
- De gebruiker die de JEA-configuratie registreert, heeft beheerders rechten op het systeem.
- U hebt een naam geselecteerd voor uw JEA-eind punt.

De naam van het JEA-eind punt is vereist wanneer gebruikers verbinding maken met het systeem met behulp van JEA. De cmdlet [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) geeft de namen van de eind punten op een systeem weer. Eind punten die beginnen met `microsoft` worden doorgaans geleverd met Windows. Het `microsoft.powershell`-eind punt is het standaard eindpunt dat wordt gebruikt om verbinding te maken met een extern Power shell-eind punt.

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

Voer de volgende opdracht uit om het eind punt te registreren.

```powershell
Register-PSSessionConfiguration -Path .\MyJEAConfig.pssc -Name 'JEAMaintenance' -Force
```

> [!WARNING]
> Met de vorige opdracht wordt de WinRM-service opnieuw gestart op het systeem. Hiermee worden alle externe sessies met Power shell en alle doorlopende DSC-configuraties beëindigd. We raden u aan productie machines offline te zetten voordat u de opdracht uitvoert om te voor komen dat zakelijke activiteiten worden verstoord.

Na de registratie bent u klaar om [JEA te gebruiken](using-jea.md). U kunt het sessie configuratie bestand op elk gewenst moment verwijderen. Het configuratie bestand wordt niet gebruikt na de registratie van het eind punt.

## <a name="multi-machine-configuration-with-dsc"></a>Configuratie van meerdere machines met DSC

Bij het implementeren van JEA op meerdere computers, gebruikt het eenvoudigste implementatie model de JEA [desired state Configuration (DSC)-](../../../dsc/overview/overview.md) resource om snel en consistent JEA op elke computer te implementeren.

Als u JEA wilt implementeren met DSC, controleert u of aan de volgende vereisten wordt voldaan:

- Een of meer functie mogelijkheden zijn gemaakt en toegevoegd aan een Power shell-module.
- De Power shell-module die de rollen bevat, wordt opgeslagen op een bestands share (alleen-lezen) die toegankelijk is voor elke computer.
- De instellingen voor de sessie configuratie zijn bepaald. U hoeft geen sessie configuratie bestand te maken wanneer u de JEA DSC-resource gebruikt.
- U hebt referenties waarmee beheer acties op elke computer of toegang tot de DSC-pull-server die wordt gebruikt voor het beheren van de computers worden toegestaan.
- U hebt de [JEA DSC-resource](https://github.com/powershell/JEA/tree/master/DSC%20Resource)gedownload.

Een DSC-configuratie voor uw JEA-eind punt maken op een doel computer of pull-server. In deze configuratie definieert de **JustEnoughAdministration** DSC-resource het sessie configuratie bestand en de **Bestands** resource kopieert de functie mogelijkheden van de bestands share.

De volgende eigenschappen kunnen worden geconfigureerd met behulp van de DSC-resource:

- Roldefinities
- Virtuele-account groepen
- Naam van door groep beheerde service account
- Transcript Directory
- Gebruikers station
- Regels voor voorwaardelijke toegang
- Opstart scripts voor de JEA-sessie

De syntaxis voor elk van deze eigenschappen in een DSC-configuratie is consistent met het configuratie bestand van de Power shell-sessie.

Hieronder vindt u een voor beeld van een DSC-configuratie voor een algemene server onderhoud module. Hierbij wordt ervan uitgegaan dat een geldige Power shell-module met functie mogelijkheden zich op de `\\myfileshare\JEA` bestands share bevindt.

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

Vervolgens wordt de configuratie op een systeem toegepast door de [lokale Configuration Manager](/powershell/scripting/dsc/managing-nodes/metaConfig) rechtstreeks aan te roepen of de configuratie van de [Pull-server](/powershell/scripting/dsc/pull-server/pullServer)bij te werken.

Met de DSC-resource kunt u ook het standaard eindpunt van **micro soft. Power shell** vervangen. Wanneer deze is vervangen, registreert de resource automatisch een back-upeindpunt met de naam **micro soft. Power shell. restricted**. Het back-upeindpunt heeft de standaard-WinRM-ACL waarmee gebruikers van extern beheer en lokale beheerders groeps leden toegang kunnen krijgen.

## <a name="unregistering-jea-configurations"></a>Registratie van JEA-configuraties ongedaan maken

Met de cmdlet [unregister-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/Unregister-PSSessionConfiguration) wordt een JEA-eind punt verwijderd. Wanneer u de registratie van een JEA-eind punt ongedaan maakt, kunnen nieuwe gebruikers geen nieuwe JEA-sessies op het systeem maken. U kunt hiermee ook een JEA-configuratie bijwerken door een bijgewerkt sessie configuratie bestand opnieuw te registreren met dezelfde naam voor het eind punt.

```powershell
# Unregister the JEA endpoint called "ContosoMaintenance"
Unregister-PSSessionConfiguration -Name 'ContosoMaintenance' -Force
```

> [!WARNING]
> Bij het ongedaan maken van de registratie van een JEA-eind punt wordt de WinRM-service opnieuw gestart. Hiermee worden de meeste beheer bewerkingen van het externe Management onderbroken, waaronder andere Power shell-sessies, WMI-aanroepen en bepaalde beheer hulpprogramma's. Registreer Power shell-eind punten alleen tijdens geplande onderhouds Vensters.

## <a name="next-steps"></a>Volgende stappen

[Het JEA-eind punt testen](using-jea.md)
