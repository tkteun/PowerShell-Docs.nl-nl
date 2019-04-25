---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: Het bouwen van een pijplijn voor continue integratie en continue implementatie met DSC
ms.openlocfilehash: 012057a32ccf85b0d15e76a332cadda4b226180a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076464"
---
# <a name="building-a-continuous-integration-and-continuous-deployment-pipeline-with-dsc"></a>Het bouwen van een pijplijn voor continue integratie en continue implementatie met DSC

In dit voorbeeld wordt gedemonstreerd hoe u een pijplijn voor continue integratie/continue implementatie (CI/CD) met behulp van PowerShell, DSC, Pester en Visual Studio Team Foundation Server (TFS).

Nadat de pijplijn is gebouwd en geconfigureerd, kunt u deze kunt gebruiken voor volledig implementeren, configureren en testen van een DNS-server en host-records die zijn gekoppeld.
Dit proces simuleert het eerste deel van een pijplijn die moet worden gebruikt in een ontwikkelomgeving.

Een geautomatiseerde CI/CD-pijplijn helpt u bij het bijwerken van software sneller en betrouwbaarder, ervoor te zorgen dat alle code is getest en dat een huidige versie van uw code is beschikbaar te allen tijde.

## <a name="prerequisites"></a>Vereisten

Als u wilt gebruiken in dit voorbeeld, moet u bekend bent met het volgende:

- CI-CD-concepten. Een goede referentie kunt u vinden op [Model van de Release-pijplijn](http://aka.ms/thereleasepipelinemodelpdf).
- [GIT](https://git-scm.com/) van bronbeheer
- De [Pester](https://github.com/pester/Pester) testframework
- [Team Foundation Server](https://www.visualstudio.com/tfs/)

## <a name="what-you-will-need"></a>Wat u nodig hebt

Als u wilt bouwen en uitvoeren van dit voorbeeld, moet u een omgeving met meerdere computers en/of virtuele machines.

### <a name="client"></a>Client

Dit is de computer waar u al het werk instellen en het voorbeeld uitvoert, doet.

De clientcomputer moet een Windows-computer met het volgende zijn geïnstalleerd:

- [Git](https://git-scm.com/)
- een lokale git-opslagplaats gekloond vanuit https://github.com/PowerShell/Demo_CI
- een teksteditor, zoals [Visual Studio Code](https://code.visualstudio.com/)

### <a name="tfssrv1"></a>TFSSrv1

De computer die als host fungeert voor de TFS-server waar u uw build definieert en release.
Deze computer moet hebben [Team Foundation Server 2017](https://www.visualstudio.com/tfs/) geïnstalleerd.

### <a name="buildagent"></a>BuildAgent

De computer met de Windows-agent die wordt gemaakt van het project bouwen.
Deze computer moet een agent geïnstalleerd en uitgevoerd bouwen Windows hebben.
Zie [implementeren van een agent op Windows](/azure/devops/pipelines/agents/v2-windows) voor instructies over het installeren en uitvoeren van een Windows agent bouwen.

U moet ook installeren op zowel de `xDnsServer` en `xNetworking` DSC-modules op deze computer.

### <a name="testagent1"></a>TestAgent1

Dit is de computer die is geconfigureerd als een DNS-server door de DSC-configuratie in dit voorbeeld.
De computer moet worden uitgevoerd [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).

### <a name="testagent2"></a>TestAgent2

Dit is de computer die als host fungeert voor de website van die dit voorbeeld wordt geconfigureerd.
De computer moet worden uitgevoerd [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).

## <a name="add-the-code-to-tfs"></a>Voeg de code toe aan TFS

We beginnen af door het maken van een Git-opslagplaats in TFS en importeren van de code van uw lokale opslagplaats op de clientcomputer.
Als u al niet de Demo_CI opslagplaats hebt gekloond naar uw client-computer, dit nu doen door het uitvoeren van de volgende git-opdracht:

`git clone https://github.com/PowerShell/Demo_CI`

1. Navigeer naar de TFS-server in een webbrowser op uw clientcomputer.
1. In TFS, [maken van een nieuw teamproject](/azure/devops/organizations/projects/create-project) Demo_CI met de naam.

   Zorg ervoor dat **versiebeheer** is ingesteld op **Git**.
1. Op de clientcomputer toevoegen een externe naar de opslagplaats die u zojuist hebt gemaakt in TFS met de volgende opdracht:

   `git remote add tfs <YourTFSRepoURL>`

   Waar `<YourTFSRepoURL>` is de kloon-URL naar de TFS-opslagplaats die u in de vorige stap hebt gemaakt.

   Als u niet waar u kunt deze URL vinden weet, raadpleegt u [klonen van een bestaande Git-repo](/azure/devops/repos/git/clone).
1. De code vanuit uw lokale opslagplaats pushen naar uw TFS-opslagplaats met de volgende opdracht:

   `git push tfs --all`
1. De TFS-opslagplaats worden ingevuld met de code Demo_CI.

> [!NOTE]
> In dit voorbeeld wordt de code in de `ci-cd-example` vertakking van de Git-opslagplaats.
> Zorg ervoor dat u deze vertakking opgeven als de standaardvertakking in de TFS-project en u voor de CI/CD-triggers maken.

## <a name="understanding-the-code"></a>Inzicht krijgen in de code

Voordat we de bouw en implementeer pijplijnen maken, laten we bekijken enkele van de code om te begrijpen wat er gebeurt.
Open uw favoriete teksteditor en gaat u naar de hoofdmap van uw Demo_CI Git-opslagplaats op uw clientcomputer.

### <a name="the-dsc-configuration"></a>De DSC-configuratie

Open het bestand `DNSServer.ps1` (in de hoofdmap van de lokale opslagplaats Demo_CI `./InfraDNS/Configs/DNSServer.ps1`).

Dit bestand bevat de DSC-configuratie die u de DNS-server stelt. Dit is in zijn geheel toe:

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

U ziet dat de `Node` instructie:

```powershell
Node $AllNodes.Where{$_.Role -eq 'DNSServer'}.NodeName
```

Dit vindt alle knooppunten die zijn gedefinieerd als een functie van `DNSServer` in de [configuratiegegevens](../configurations/configData.md), die is gemaakt door de `DevEnv.ps1` script.

U kunt meer lezen over de `Where` methode in [about_arrays](/powershell/reference/3.0/Microsoft.PowerShell.Core/About/about_Arrays.md)

Met behulp van de configuratiegegevens voor het definiëren van knooppunten is belangrijk bij het uitvoeren van CI omdat knooppuntgegevens waarschijnlijk tussen omgevingen veranderen zullen en configuratiegegevens, kunt u eenvoudig wijzigingen aanbrengen in knooppunt informatie zonder de configuratiecode te wijzigen.

In de eerste resource blok, de configuratie van de roept de **WindowsFeature** om ervoor te zorgen dat de DNS-functie is ingeschakeld.
De resource-blokken die volgen op resources van de aanroep van de [xDnsServer](https://github.com/PowerShell/xDnsServer) module voor het configureren van de primaire zone en DNS-records.

U ziet dat de twee `xDnsRecord` blokken worden verpakt in `foreach` lussen die matrices in de configuratiegegevens doorlopen.
Nogmaals, de configuratiegegevens wordt gemaakt door de `DevEnv.ps1` script, dat we naar volgende kijken.

### <a name="configuration-data"></a>Configuratiegegevens

De `DevEnv.ps1` bestand (in de hoofdmap van de lokale opslagplaats Demo_CI `./InfraDNS/DevEnv.ps1`) Hiermee geeft u de omgeving-specifieke configuratiegegevens in een hash-tabel en vervolgens worden doorgegeven dat hashtabel aan een aanroep naar de `New-DscConfigurationDataDocument` functie, die is gedefinieerd in `DscPipelineTools.psm` (`./Assets/DscPipelineTools/DscPipelineTools.psm1`).

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

De `New-DscConfigurationDataDocument` functie (gedefinieerd in `\Assets\DscPipelineTools\DscPipelineTools.psm1`) via een programma maakt een configuratiebestand voor de gegevens van de hash-tabel (knooppuntgegevens) en de matrix (niet-knooppuntgegevens) die worden doorgegeven als de `RawEnvData` en `OtherEnvData` parameters.

In ons geval alleen de `RawEnvData` parameter wordt gebruikt.

### <a name="the-psake-build-script"></a>Het bouwscript psake

De [psake](https://github.com/psake/psake) build script gedefinieerd in `Build.ps1` (in de hoofdmap van de opslagplaats Demo_CI `./InfraDNS/Build.ps1`) definieert de taken die deel van de build uitmaken.
Het definieert ook welke andere taken die afhankelijk van elke taak.
Wordt aangeroepen, het script psake zorgt ervoor dat de opgegeven taak (of de taak met de naam `Default` als er niets is opgegeven) wordt uitgevoerd en dat alle afhankelijkheden ook worden uitgevoerd (dit is recursief, zodat de afhankelijkheden van afhankelijkheden worden uitgevoerd, enzovoort).

In dit voorbeeld wordt de `Default` taak wordt gedefinieerd als:

```powershell
Task Default -depends UnitTests
```

De `Default` taak heeft geen implementatie zelf, maar is afhankelijk van de `CompileConfigs` taak.
De resulterende reeks taakafhankelijkheden zorgt ervoor dat alle taken in de build-script worden uitgevoerd.

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

Wanneer we de build-definitie voor het voorbeeld in TFS maken, geven we onze psake scriptbestand als de `fileName` parameter voor dit script.

Het bouwscript definieert de volgende taken:

#### <a name="generateenvironmentfiles"></a>GenerateEnvironmentFiles

Uitvoeringen `DevEnv.ps1`, die het configuratiebestand van de gegevens worden gegenereerd.

#### <a name="installmodules"></a>InstallModules

Installeert de modules die zijn vereist voor de configuratie van de `DNSServer.ps1`.

#### <a name="scriptanalysis"></a>ScriptAnalysis

Aanroepen van de [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer).

#### <a name="unittests"></a>UnitTests

Uitvoeringen van de [Pester](https://github.com/pester/Pester/wiki) eenheidstests.

#### <a name="compileconfigs"></a>CompileConfigs

Compileert de configuratie (`DNSServer.ps1`) naar een MOF-bestand met behulp van de configuratiegegevens die zijn gegenereerd door de `GenerateEnvironmentFiles` taak.

#### <a name="clean"></a>Opruimen

De mappen die worden gebruikt voor het voorbeeld maakt en Hiermee verwijdert u alle testresultaten, configuratiebestanden gegevens en -modules uit eerdere uitvoeringen.

### <a name="the-psake-deploy-script"></a>De psake script implementeren

De [psake](https://github.com/psake/psake) gedefinieerd in een script voor implementatie `Deploy.ps1` (in de hoofdmap van de opslagplaats Demo_CI `./InfraDNS/Deploy.ps1`) taken die implementeren en uitvoeren van de configuratie definieert.

`Deploy.ps1` definieert de volgende taken:

#### <a name="deploymodules"></a>DeployModules

Start een PowerShell-sessie op `TestAgent1` en installeert u de modules met de DSC-resources die vereist zijn voor de configuratie.

#### <a name="deployconfigs"></a>DeployConfigs

Aanroepen van de [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet uit te voeren van de configuratie op `TestAgent1`.

#### <a name="integrationtests"></a>IntegrationTests

Uitvoeringen van de [Pester](https://github.com/pester/Pester/wiki) integratietests.

#### <a name="acceptancetests"></a>AcceptanceTests

Uitvoeringen van de [Pester](https://github.com/pester/Pester/wiki) acceptatietesten uit.

#### <a name="clean"></a>Opruimen

Hiermee verwijdert u alle modules geïnstalleerd in de vorige uitvoeringen en zorgt ervoor dat de test resultaat-map bestaat.

### <a name="test-scripts"></a>Scripts testen

Acceptatie, integratie, en moduletests zijn gedefinieerd in scripts in de `Tests` map (in de hoofdmap van de opslagplaats Demo_CI `./InfraDNS/Tests`), elk in bestanden met de naam `DNSServer.tests.ps1` in hun respectieve mappen.

De test-scripts gebruiken [Pester](https://github.com/pester/Pester/wiki) en [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntaxis.

#### <a name="unit-tests"></a>Eenheidstests

De eenheid test de DSC-testconfiguraties zelf om ervoor te zorgen dat de configuraties wat er wordt verwacht doet wanneer ze worden uitgevoerd.
De eenheid maakt gebruik van script testen [Pester](https://github.com/pester/Pester/wiki).

#### <a name="integration-tests"></a>Integratietests

De integratietests testen van de configuratie van het systeem om ervoor te zorgen dat wanneer geïntegreerd met andere onderdelen, het systeem is geconfigureerd zoals verwacht. Deze tests uitgevoerd op het doelknooppunt nadat deze is geconfigureerd met DSC.
Het testscript integratie maakt gebruik van een combinatie van [Pester](https://github.com/pester/Pester/wiki) en [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntaxis.

#### <a name="acceptance-tests"></a>Acceptatietesten uit

Acceptatietesten uit test het systeem om ervoor te zorgen dat deze werkt zoals verwacht.
Bijvoorbeeld: deze test om te controleren of dat een webpagina retourneert de juiste informatie wanneer een query uitgevoerd.
Deze tests uitvoeren op afstand van het doelknooppunt om te kunnen testen praktijkscenario's.
Het testscript integratie maakt gebruik van een combinatie van [Pester](https://github.com/pester/Pester/wiki) en [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntaxis.

## <a name="define-the-build"></a>De build definiëren

Nu dat we onze code hebt geüpload naar TFS en bekeken wat het doet, gaan we onze build definiëren.

Hier aan bod de build-stappen die u aan de build toevoegen zult. Zie voor instructies over het maken van een build-definitie in TFS [maken en wachtrij een build-definitie](/azure/devops/pipelines/get-started-designer).

Maak een nieuwe build-definitie (Selecteer de **leeg** sjabloon) met de naam 'InfraDNS'.
Voeg dat de volgende stappen uit voor u build-definitie:

- PowerShell-Script
- De resultaten publiceren
- Bestanden kopiëren
- Artefacten publiceren

Na het toevoegen van deze stappen bouwen, bewerk de eigenschappen van elke stap als volgt:

### <a name="powershell-script"></a>PowerShell-Script

1. Stel de **Type** eigenschap `File Path`.
1. Stel de **scriptpad** eigenschap `initiate.ps1`.
1. Voeg `-fileName build` naar de **argumenten** eigenschap.

Deze build-stap wordt uitgevoerd de `initiate.ps1` bestand, die de psake build-script aanroept.

### <a name="publish-test-results"></a>De resultaten publiceren

1. Stel **Resultaatindeling testen** naar `NUnit`
1. Stel **testresultaten bestanden** naar `InfraDNS/Tests/Results/*.xml`
1. Stel **testen uitvoeren titel** naar `Unit`.
1. Zorg ervoor dat **beheeropties** **ingeschakeld** en **altijd uitgevoerd** worden beide geselecteerd.

Deze build-stap de eenheidstests in het script Pester is eerder wordt uitgevoerd, en slaat de resultaten in de `InfraDNS/Tests/Results/*.xml` map.

### <a name="copy-files"></a>Bestanden kopiëren

1. Elk van de volgende regels toevoegen **inhoud**:

   ```
   initiate.ps1
   **\deploy.ps1
   **\Acceptance\**
   **\Integration\**
   ```

1. Stel **TargetFolder** aan `$(Build.ArtifactStagingDirectory)\`

Deze stap worden gekopieerd van de build en test scripts naar de staging-map zodat die de kan worden gepubliceerd als build-artefacten door de volgende stap.

### <a name="publish-artifact"></a>Artefacten publiceren

1. Stel **pad om te publiceren** naar `$(Build.ArtifactStagingDirectory)\`
1. Stel **Artefactnaam** aan `Deploy`
1. Stel **Artefacttype** naar `Server`
1. Selecteer `Enabled` in **opties beheren**

## <a name="enable-continuous-integration"></a>Inschakelen van continue integratie

Nu we een trigger die ervoor zorgt het project stellen dat te bouwen van elk gewenst moment een wijziging wordt ingecheckt bij de `ci-cd-example` vertakking van de git-opslagplaats.

1. In TFS, klikt u op de **Build & Release** tabblad
1. Selecteer de `DNS Infra` build-definitie en klikt u op **bewerken**
1. Klik op de **Triggers** tabblad
1. Selecteer **continue integratie (CI)**, en selecteer `refs/heads/ci-cd-example` in de vervolgkeuzelijst vertakking
1. Klik op **opslaan** en vervolgens **OK**

Nu wijziging een in de TFS-triggers voor git-opslagplaats een geautomatiseerde build.

## <a name="create-the-release-definition"></a>De release-definitie maken

Laten we een release-definitie maken zodat het project wordt geïmplementeerd voor de ontwikkelomgeving met elke check code in.

Om dit te doen, Voeg een nieuwe release-definitie die is gekoppeld aan de `InfraDNS` build-definitie die u eerder hebt gemaakt.
Zorg ervoor dat u selecteert **continue implementatie** zodat een nieuwe versie wordt geactiveerd telkens wanneer een nieuwe build is voltooid.
([Wat release-pijplijnen zijn? ](/azure/devops/pipelines/release/what-is-release-management)) en configureer deze als volgt:

De volgende stappen toevoegen aan de release-definitie:

- PowerShell-Script
- De resultaten publiceren
- De resultaten publiceren

Bewerken als volgt de stappen uit:

### <a name="powershell-script"></a>PowerShell-Script

1. Stel de **scriptpad** veld `$(Build.DefinitionName)\Deploy\initiate.ps1"`
1. Stel de **argumenten** veld `-fileName Deploy`

### <a name="first-publish-test-results"></a>Eerst publiceren testresultaten

1. Selecteer `NUnit` voor de **Test Resultaatindeling** veld
1. Stel de **resultaat testbestanden** veld `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Integration*.xml`
1. Stel de **testen uitvoeren titel** naar `Integration`
1. Onder **beheeropties**, Controleer **altijd worden uitgevoerd**

### <a name="second-publish-test-results"></a>De resultaten van het tweede publiceren

1. Selecteer `NUnit` voor de **Test Resultaatindeling** veld
1. Stel de **resultaat testbestanden** veld `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Acceptance*.xml`
1. Stel de **testen uitvoeren titel** naar `Acceptance`
1. Onder **beheeropties**, Controleer **altijd worden uitgevoerd**

## <a name="verify-your-results"></a>Uw resultaten controleren

Nu, telkens wanneer u via push wijzigingen de `ci-cd-example` vertakking naar TFS, een nieuwe build wordt gestart.
Als de build voltooid is, wordt een nieuwe implementatie geactiveerd.

U kunt het resultaat van de implementatie controleren door een browser op de clientcomputer openen en te navigeren naar `www.contoso.com`.

## <a name="next-steps"></a>Volgende stappen

In dit voorbeeld configureert de DNS-server `TestAgent1` zodat de URL `www.contoso.com` wordt omgezet naar `TestAgent2`, maar er wordt een website niet daadwerkelijk geïmplementeerd.
De basis voor het in dat geval is opgegeven in de opslagplaats onder de `WebApp` map.
Dit is de standaardinstelling voor het maken van psake scripts, Pester tests en DSC-configuraties kunt u uw eigen website kunt implementeren.
