---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie, setup
title: Het bouwen van een pijplijn continue integratie en continue implementatie met DSC
ms.openlocfilehash: faeef5022cbd984cab0620b69db19de8b84cca0e
ms.sourcegitcommit: 68093cc12a7a22c53d11ce7d33c18622921a0dd1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/26/2018
ms.locfileid: "36940341"
---
# <a name="building-a-continuous-integration-and-continuous-deployment-pipeline-with-dsc"></a>Het bouwen van een pijplijn continue integratie en continue implementatie met DSC

In dit voorbeeld laat zien hoe een continue integratie met doorlopend implementatie (CI/CD)-pijplijn maken met behulp van PowerShell, DSC, Pester en Visual Studio Team Foundation Server (TFS).

Nadat de pijplijn is gemaakt en geconfigureerd, kunt u gebruiken deze volledig implementeren, configureren en testen van een DNS-server en host-records die zijn gekoppeld.
Dit proces wordt het eerste deel van een pijplijn die moet worden gebruikt in een ontwikkelingsomgeving gesimuleerd.

Een geautomatiseerde CI/CD-pijplijn, kunt u software sneller en betrouwbaarder, ervoor te zorgen dat alle code wordt getest en dat er een huidige build van uw code is beschikbaar te allen tijde.

## <a name="prerequisites"></a>Vereisten

Dit voorbeeld kunt gebruiken, moet u bekend bent met het volgende:

- Concepten van CI-CD. De verwijzing naar een goede kan worden gevonden op [de Release pijplijn Model](http://aka.ms/thereleasepipelinemodelpdf).
- [GIT](https://git-scm.com/) besturingselement voor de gegevensbron
- De [Pester](https://github.com/pester/Pester) framework testen
- [Team Foundation Server](https://www.visualstudio.com/tfs/)

## <a name="what-you-will-need"></a>Wat u nodig hebt

Voor het bouwen en uitvoeren van dit voorbeeld, moet u een omgeving met meerdere computers en/of virtuele machines.

### <a name="client"></a>Client

Dit is de computer waar u doet al het werk instellen en uitvoeren in het voorbeeld.

De clientcomputer moet een Windows-computer met het volgende zijn geïnstalleerd:

- [GIT](https://git-scm.com/)
- een lokale git-opslagplaats gekloond van https://github.com/PowerShell/Demo_CI
- een teksteditor, zoals [Visual Studio Code](https://code.visualstudio.com/)

### <a name="tfssrv1"></a>TFSSrv1

De computer die als host fungeert voor de TFS-server waar u uw build definieert en release.
Deze computer [Team Foundation Server 2017](https://www.visualstudio.com/tfs/) geïnstalleerd.

### <a name="buildagent"></a>BuildAgent

De computer met de Windows-agent die wordt gemaakt van het project bouwen.
Deze computer moet een agent geïnstalleerd en uitgevoerd bouwen Windows hebben.
Zie [implementeren van een agent op Windows](https://www.visualstudio.com/en-us/docs/build/actions/agents/v2-windows) voor instructies over het installeren en uitvoeren van een Windows-build agent.

U moet ook installeren op zowel de `xDnsServer` en `xNetworking` DSC-modules op deze computer.

### <a name="testagent1"></a>TestAgent1

Dit is de computer die is geconfigureerd als een DNS-server door de DSC-configuratie in dit voorbeeld.
De computer moet worden uitgevoerd [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).

### <a name="testagent2"></a>TestAgent2

Dit is de computer die als host fungeert voor de website die in dit voorbeeld configureert.
De computer moet worden uitgevoerd [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).

## <a name="add-the-code-to-tfs"></a>Voeg de code naar TFS

We beginnen uit door het maken van een Git-opslagplaats in TFS en importeren van de code van uw lokale opslagplaats op de clientcomputer.
Als u de opslagplaats Demo_CI hebt niet op uw clientcomputer hebt gekloond, dit nu doen met de volgende git-opdracht:

`git clone https://github.com/PowerShell/Demo_CI`

1. Navigeer naar de TFS-server in een webbrowser op de clientcomputer.
1. In TFS, [maken van een nieuw teamproject](https://www.visualstudio.com/en-us/docs/setup-admin/create-team-project) Demo_CI met de naam.

   Zorg ervoor dat **versiebeheer** is ingesteld op **Git**.
1. Op de clientcomputer voegt u een externe toe aan de opslagplaats die u zojuist hebt gemaakt in TFS met de volgende opdracht:

   `git remote add tfs <YourTFSRepoURL>`

   Waar `<YourTFSRepoURL>` de kloon-URL naar de TFS-opslagplaats die u in de vorige stap hebt gemaakt.

   Als u niet waar deze URL zoeken weet, Zie [klonen van een bestaande Git-opslagplaats](https://www.visualstudio.com/en-us/docs/git/tutorial/clone).
1. De code van uw lokale opslagplaats pushen naar uw opslagplaats TFS met de volgende opdracht:

   `git push tfs --all`
1. De opslagplaats TFS worden ingevuld met de code Demo_CI.

> [!NOTE]
> In dit voorbeeld wordt de code in de `ci-cd-example` vertakking van de Git-opslagplaats.
> Zorg ervoor dat de vertakking opgeven als de standaardvertakking in TFS-project en voor de CI/CD-triggers die u maakt.

## <a name="understanding-the-code"></a>Wat is de code?

Voordat we het build- en pijplijnen maken, bekijken we enkele van de code te begrijpen wat er gebeurt.
Open uw favoriete teksteditor op de clientcomputer en navigeer naar de hoofdmap van uw Demo_CI Git-opslagplaats.

### <a name="the-dsc-configuration"></a>De DSC-configuratie

Open het bestand `DNSServer.ps1` (in de hoofdmap van de lokale Demo_CI opslagplaats `./InfraDNS/Configs/DNSServer.ps1`).

Dit bestand bevat de DSC-configuratie instellen van de DNS-server. Dit is in zijn geheel:

```powershell
configuration DNSServer
{
    Import-DscResource -module 'xDnsServer','xNetworking', 'PSDesiredStateConfiguration'

    Node $AllNodes.Where{$_.Role -eq 'DNSServer'}.NodeName
    {
        WindowsFeature DNS
        {
            Ensure  = 'Present'
            Name    = 'DNS'
        }

        xDnsServerPrimaryZone $Node.zone
        {
            Ensure    = 'Present'
            Name      = $Node.Zone
            DependsOn = '[WindowsFeature]DNS'
        }

        foreach ($ARec in $Node.ARecords.keys) {
            xDnsRecord $ARec
            {
                Ensure    = 'Present'
                Name      = $ARec
                Zone      = $Node.Zone
                Type      = 'ARecord'
                Target    = $Node.ARecords[$ARec]
                DependsOn = '[WindowsFeature]DNS'
            }
        }

        foreach ($CName in $Node.CNameRecords.keys) {
            xDnsRecord $CName
            {
                Ensure    = 'Present'
                Name      = $CName
                Zone      = $Node.Zone
                Type      = 'CName'
                Target    = $Node.CNameRecords[$CName]
                DependsOn = '[WindowsFeature]DNS'
            }
        }
    }
}
```

U ziet de `Node` instructie:

```powershell
Node $AllNodes.Where{$_.Role -eq 'DNSServer'}.NodeName
```

Hiermee vindt u alle knooppunten die zijn gedefinieerd als bestanden met de rol `DNSServer` in de [configuratiegegevens](configData.md), die wordt gemaakt door de `DevEnv.ps1` script.

U kunt meer lezen over de `Where` methode in [about_arrays](/powershell/reference/3.0/Microsoft.PowerShell.Core/About/about_Arrays.md)

Met behulp van de configuratiegegevens voor het definiëren van knooppunten is belangrijk bij het uitvoeren van CI omdat knooppunt informatie waarschijnlijk tussen omgevingen veranderen zullen en configuratiegegevens met kunt u gemakkelijk wijzigingen aanbrengen in knooppunt informatie zonder de configuratiecode te wijzigen.

In de eerste resource blok, de configuratie roept de [WindowsFeature](windowsFeatureResource.md) om ervoor te zorgen dat de DNS-functie is ingeschakeld.
De resource-blokken die resources van de aanroep van volgen de [xDnsServer](https://github.com/PowerShell/xDnsServer) module voor het configureren van de primaire zone en DNS-records.

U ziet dat de twee `xDnsRecord` blokken zijn samengevoegd in `foreach` lussen die matrices in de configuratiegegevens doorlopen.
De configuratiegegevens wordt opnieuw gemaakt door de `DevEnv.ps1` script, dat zullen we op volgende.

### <a name="configuration-data"></a>Configuratiegegevens

De `DevEnv.ps1` bestand (in de hoofdmap van de lokale Demo_CI opslagplaats `./InfraDNS/DevEnv.ps1`) Hiermee geeft u de omgeving-specifieke configuratiegegevens in een hashtabel en vervolgens die hashtabel doorgegeven aan een aanroep van de `New-DscConfigurationDataDocument` functie, die is gedefinieerd in `DscPipelineTools.psm` (`./Assets/DscPipelineTools/DscPipelineTools.psm1`).

De `DevEnv.ps1` bestand:

```powershell
param(
    [parameter(Mandatory=$true)]
    [string]
    $OutputPath
)

Import-Module $PSScriptRoot\..\Assets\DscPipelineTools\DscPipelineTools.psd1 -Force

# Define Unit Test Environment
$DevEnvironment = @{
    Name                        = 'DevEnv';
    Roles = @(
        @{  Role                = 'DNSServer';
            VMName              = 'TestAgent1';
            Zone                = 'Contoso.com';
            ARecords            = @{'TFSSrv1'= '10.0.0.10';'Client'='10.0.0.15';'BuildAgent'='10.0.0.30';'TestAgent1'='10.0.0.40';'TestAgent2'='10.0.0.50'};
            CNameRecords        = @{'DNS' = 'TestAgent1.contoso.com'};
        }
    )
}

Return New-DscConfigurationDataDocument -RawEnvData $DevEnvironment -OutputPath $OutputPath
```

De `New-DscConfigurationDataDocument` functie (gedefinieerd in `\Assets\DscPipelineTools\DscPipelineTools.psm1`) via een programma maakt een configuratiebestand voor de gegevens van de hash-tabel (knooppuntgegevens) en de matrix (niet-knooppunt gegevens) die worden doorgegeven als de `RawEnvData` en `OtherEnvData` parameters.

In ons geval alleen de `RawEnvData` parameter wordt gebruikt.

### <a name="the-psake-build-script"></a>Het psake build script

De [psake](https://github.com/psake/psake) bouwen script gedefinieerd in `Build.ps1` (in de hoofdmap van de opslagplaats Demo_CI `./InfraDNS/Build.ps1`) taken die deel van de build uitmaken definieert.
Het definieert ook welke andere elke taak afhankelijk van is taken.
Als deze wordt aangeroepen, het script psake zorgt ervoor dat de opgegeven taak (of de taak met de naam `Default` als niets wordt opgegeven) wordt uitgevoerd en dat alle afhankelijkheden ook uitvoeren (dit is recursieve, zodat de afhankelijkheden van afhankelijkheden hebt uitgevoerd, enzovoort).

In dit voorbeeld wordt de `Default` taak is gedefinieerd als:

```powershell
Task Default -depends UnitTests
```

De `Default` taak geen implementatie zelf, maar afhankelijk is van de `CompileConfigs` taak.
De resulterende reeks taakafhankelijkheden zorgt ervoor dat alle taken in het build-script worden uitgevoerd.

In dit voorbeeld wordt het script psake opgeroepen door een aanroep naar `Invoke-PSake` in de `Initiate.ps1` bestand (te vinden in de hoofdmap van de opslagplaats Demo_CI):

```powershell
param(
    [parameter()]
    [ValidateSet('Build','Deploy')]
    [string]
    $fileName
)

#$Error.Clear()

Invoke-PSake $PSScriptRoot\InfraDNS\$fileName.ps1

<#if($Error.count)
{
    Throw "$fileName script failed. Check logs for failure details."
}
#>
```

Wanneer de build-definitie we in ons voorbeeld in TFS maken, geven we onze scriptbestand psake als de `fileName` parameter voor dit script.

Het script build definieert de volgende taken:

#### <a name="generateenvironmentfiles"></a>GenerateEnvironmentFiles

Wordt uitgevoerd `DevEnv.ps1`, die het bestand met configuratiegegevens genereert.

#### <a name="installmodules"></a>InstallModules

De door de configuratie van de vereiste modules installeert `DNSServer.ps1`.

#### <a name="scriptanalysis"></a>ScriptAnalysis

Aanroepen van de [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer).

#### <a name="unittests"></a>UnitTests

Voert de [Pester](https://github.com/pester/Pester/wiki) eenheidstests.

#### <a name="compileconfigs"></a>CompileConfigs

De configuratie wordt gecompileerd (`DNSServer.ps1`) naar een MOF-bestand met behulp van de configuratiegegevens die worden gegenereerd door de `GenerateEnvironmentFiles` taak.

#### <a name="clean"></a>Opruimen

De mappen die wordt gebruikt voor het voorbeeld maakt en verwijdert u alle testresultaten, gegevens configuratiebestanden en modules uit vorige wordt uitgevoerd.

### <a name="the-psake-deploy-script"></a>De psake script wilt implementeren

De [psake](https://github.com/psake/psake) gedefinieerd in een script voor implementatie `Deploy.ps1` (in de hoofdmap van de opslagplaats Demo_CI `./InfraDNS/Deploy.ps1`) taken die implementeren en uitvoeren van de configuratie definieert.

`Deploy.ps1` definieert de volgende taken:

#### <a name="deploymodules"></a>DeployModules

Een PowerShell-sessie begint op `TestAgent1` en installeert u de modules die met de DSC-resources die vereist zijn voor de configuratie.

#### <a name="deployconfigs"></a>DeployConfigs

Aanroepen van de [Start DscConfiguration](/reference/5.1/PSDesiredStateConfiguration/Start-DscConfiguration.md) cmdlet uit te voeren van de configuratie op `TestAgent1`.

#### <a name="integrationtests"></a>IntegrationTests

Voert de [Pester](https://github.com/pester/Pester/wiki) integratie tests.

#### <a name="acceptancetests"></a>AcceptanceTests

Voert de [Pester](https://github.com/pester/Pester/wiki) acceptatie tests.

#### <a name="clean"></a>Opruimen

Hiermee verwijdert u alle modules geïnstalleerd in de vorige wordt uitgevoerd en zorgt ervoor dat de map test resultaat bestaat.

### <a name="test-scripts"></a>Scripts testen

Acceptatie, integratie en eenheid tests worden gedefinieerd in scripts in de `Tests` map (in de hoofdmap van de opslagplaats Demo_CI `./InfraDNS/Tests`), elk in bestanden met de naam `DNSServer.tests.ps1` in de bijbehorende mappen.

De test scripts gebruik [Pester](https://github.com/pester/Pester/wiki) en [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntaxis.

#### <a name="unit-tests"></a>Eenheidstests

De eenheid test test de DSC-configuraties zelf om ervoor te zorgen dat de configuraties wordt verwacht doet wanneer ze worden uitgevoerd.
De eenheid testen script gebruikt [Pester](https://github.com/pester/Pester/wiki).

#### <a name="integration-tests"></a>Integratie-tests

De tests integratie test de configuratie van het systeem om ervoor te zorgen dat indien geïntegreerd met andere onderdelen, het systeem is geconfigureerd zoals verwacht. Deze tests uitgevoerd op het doelknooppunt nadat deze is geconfigureerd met DSC.
Het testscript integratie maakt gebruik van een combinatie van [Pester](https://github.com/pester/Pester/wiki) en [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntaxis.

#### <a name="acceptance-tests"></a>Acceptatie van de tests

Acceptatie van de tests test het systeem om ervoor te zorgen dat deze functie werkt zoals verwacht.
Bijvoorbeeld: test om te controleren of dat een webpagina retourneert de juiste informatie wanneer opgevraagd.
Deze tests uitvoeren op afstand vanaf het doelknooppunt real-world scenario's testen.
Het testscript integratie maakt gebruik van een combinatie van [Pester](https://github.com/pester/Pester/wiki) en [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntaxis.

## <a name="define-the-build"></a>Definieer de build

Nu dat we onze code hebt geüpload naar TFS en bekeken wat het geval is, gaan we onze build definiëren.

Hier komen aan bod de build-stappen die u aan de build toevoegen zult. Zie voor instructies over het maken van een definitie van de build in TFS [maken en de definitie van een build wachtrij](https://www.visualstudio.com/en-us/docs/build/define/create).

Een nieuwe build-definitie maken (Selecteer de **leeg** sjabloon) met de naam 'InfraDNS'.
Voeg dat de volgende stappen uit om u te bouwen definitie:

- PowerShell-Script
- Testresultaten publiceren
- Bestanden kopiëren
- Publiceren van artefacten

Na het toevoegen van deze stappen te bouwen, bewerk de eigenschappen van elke stap als volgt:

### <a name="powershell-script"></a>PowerShell-Script

1. Stel de **Type** eigenschap `File Path`.
1. Stel de **scriptpad** eigenschap `initiate.ps1`.
1. Voeg `-fileName build` naar de **argumenten** eigenschap.

Deze stap build wordt uitgevoerd de `initiate.ps1` -bestand, dat het psake build script aanroept.

### <a name="publish-test-results"></a>Testresultaten publiceren

1. Stel **Resultaatindeling testen** naar `NUnit`
1. Stel **testresultaten bestanden** naar `InfraDNS/Tests/Results/*.xml`
1. Stel **testen uitvoeren titel** naar `Unit`.
1. Zorg ervoor dat **beheeropties** **ingeschakeld** en **altijd uitgevoerd** zijn beide ingeschakeld.

Deze stap build wordt uitgevoerd de eenheidstests in het Pester-script dat we eerder bekeken en slaat de resultaten in de `InfraDNS/Tests/Results/*.xml` map.

### <a name="copy-files"></a>Bestanden kopiëren

1. Elk van de volgende regels toevoegen **inhoud**:

   ```
   initiate.ps1
   **\deploy.ps1
   **\Acceptance\**
   **\Integration\**
   ```

1. Stel **TargetFolder** naar `$(Build.ArtifactStagingDirectory)\`

Deze stap kopieert de build en test scripts aan de staging-map zodanig dat het kan worden gepubliceerd als artefacten bouwen door de volgende stap.

### <a name="publish-artifact"></a>Publiceren van artefacten

1. Stel **pad voor het publiceren van** naar `$(Build.ArtifactStagingDirectory)\`
1. Stel **artefact naam** naar `Deploy`
1. Stel **artefact Type** naar `Server`
1. Selecteer `Enabled` in **opties instellen**

## <a name="enable-continuous-integration"></a>Continue integratie inschakelen

Nu we een trigger die ervoor zorgt het project stellen dat voor het bouwen van elk gewenst moment een wijziging wordt ingecheckt bij de `ci-cd-example` vertakking van de git-opslagplaats.

1. In TFS, klikt u op de **bouwen & Release** tabblad
1. Selecteer de `DNS Infra` definitie bouwen en klikt u op **bewerken**
1. Klik op de **Triggers** tabblad
1. Selecteer **continue integratie (CI)**, en selecteer `refs/heads/ci-cd-example` in de vervolgkeuzelijst vertakking
1. Klik op **opslaan** en vervolgens **OK**

Nu wijziging elke in de TFS git-opslagplaats triggers een geautomatiseerde build.

## <a name="create-the-release-definition"></a>De release-definitie maken

De definitie van een release we maken zodat het project wordt geïmplementeerd op de ontwikkelomgeving met elke code incheckt.

U doet dit door een nieuwe toevoegen release die zijn gekoppeld aan de `InfraDNS` bouwen definitie die u eerder hebt gemaakt.
Selecteer **continue implementatie** zodat een nieuwe release geactiveerd elk gewenst moment een nieuwe build is voltooid.
([How to: werken met release definities](https://www.visualstudio.com/en-us/docs/build/actions/work-with-release-definitions)) en configureer deze als volgt:

De volgende stappen toevoegen aan de definitie van de release:

- PowerShell-Script
- Testresultaten publiceren
- Testresultaten publiceren

Bewerk de stappen uit als volgt:

### <a name="powershell-script"></a>PowerShell-Script

1. Stel de **scriptpad** veld `$(Build.DefinitionName)\Deploy\initiate.ps1"`
1. Stel de **argumenten** veld `-fileName Deploy`

### <a name="first-publish-test-results"></a>Testresultaten eerst publiceren

1. Selecteer `NUnit` voor de **Resultaatindeling Test** veld
1. Stel de **resultaat testbestanden** veld `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Integration*.xml`
1. Stel de **testen uitvoeren titel** naar `Integration`
1. Onder **beheeropties**, Controleer **altijd worden uitgevoerd**

### <a name="second-publish-test-results"></a>Tweede publiceren testresultaten

1. Selecteer `NUnit` voor de **Resultaatindeling Test** veld
1. Stel de **resultaat testbestanden** veld `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Acceptance*.xml`
1. Stel de **testen uitvoeren titel** naar `Acceptance`
1. Onder **beheeropties**, Controleer **altijd worden uitgevoerd**

## <a name="verify-your-results"></a>De resultaten controleren

Nu elk gewenst moment u push-wijzigingen de `ci-cd-example` vertakking naar TFS, een nieuwe build wordt gestart.
Als de build voltooid is, wordt een nieuwe implementatie wordt geactiveerd.

U kunt het resultaat van de implementatie controleren door een browser op de clientcomputer openen en te navigeren naar `www.contoso.com`.

## <a name="next-steps"></a>Volgende stappen

In dit voorbeeld configureert de DNS-server `TestAgent1` zodat de URL `www.contoso.com` wordt omgezet naar `TestAgent2`, maar deze een website niet daadwerkelijk implementeren.
Het basisproject hiertoe vindt u in de opslagplaats onder de `WebApp` map.
U kunt de stubs voor het maken van psake scripts, Pester tests en DSC-configuraties gebruiken voor het implementeren van uw eigen website.