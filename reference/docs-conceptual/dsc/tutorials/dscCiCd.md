---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: Een continue integratie en een pijp lijn voor continue implementatie bouwen met DSC
ms.openlocfilehash: 2d049cd640f0df9b018a88ad106e59dbeed7bcee
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "71942144"
---
# <a name="building-a-continuous-integration-and-continuous-deployment-pipeline-with-dsc"></a>Een continue integratie en een pijp lijn voor continue implementatie bouwen met DSC

Dit voor beeld laat zien hoe u met behulp van Power shell, DSC, pester en Visual Studio Team Foundation Server (TFS) een continue integratie/CD-pijp lijn kunt maken.

Nadat de pijp lijn is gebouwd en geconfigureerd, kunt u deze gebruiken om een DNS-server en bijbehorende host-records volledig te implementeren, te configureren en te testen.
Dit proces simuleert het eerste deel van een pijp lijn dat in een ontwikkel omgeving zou worden gebruikt.

Een geautomatiseerde CI/CD-pijp lijn helpt u software sneller en betrouwbaarder bij te werken, zodat alle code wordt getest en dat de huidige versie van uw code altijd beschikbaar is.

## <a name="prerequisites"></a>Vereisten

Als u dit voor beeld wilt gebruiken, moet u vertrouwd zijn met het volgende:

- CI-CD-concepten. Een goede verwijzing vindt u in [het model van de release pijplijn](https://aka.ms/thereleasepipelinemodelpdf).
- [Git](https://git-scm.com/) -bron beheer
- Het [ziekte](https://github.com/pester/Pester) test-framework
- [Team Foundation Server](https://visualstudio.microsoft.com/tfs/)

## <a name="what-you-will-need"></a>Wat u nodig hebt

Als u dit voor beeld wilt bouwen en uitvoeren, hebt u een omgeving met meerdere computers en/of virtuele machines nodig.

### <a name="client"></a>Client

Dit is de computer waarop u alle werk instellingen gaat uitvoeren en het voor beeld uitvoert.

De client computer moet een Windows-computer zijn waarop het volgende is geïnstalleerd:

- [Git](https://git-scm.com/)
- een lokale Git-opslag plaats die is gekloond van https://github.com/PowerShell/Demo_CI
- een tekst editor, zoals [Visual Studio code](https://code.visualstudio.com/)

### <a name="tfssrv1"></a>TFSSrv1

De computer die als host fungeert voor de TFS-server waarop u uw build en release wilt definiëren.
Op deze computer moet [Team Foundation Server 2017](https://visualstudio.microsoft.com/tfs/) zijn geïnstalleerd.

### <a name="buildagent"></a>BuildAgent

De computer waarop de Windows Build-agent wordt uitgevoerd, die het project bouwt.
Op deze computer moet een Windows-Build-agent zijn geïnstalleerd en worden uitgevoerd.
Zie [een agent implementeren in Windows](/azure/devops/pipelines/agents/v2-windows) voor instructies over het installeren en uitvoeren van een Windows Build-agent.

U moet ook de `xDnsServer`-en `xNetworking` DSC-modules op deze computer installeren.

### <a name="testagent1"></a>TestAgent1

Dit is de computer die is geconfigureerd als een DNS-server door de DSC-configuratie in dit voor beeld.
Op de computer moet [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016)worden uitgevoerd.

### <a name="testagent2"></a>TestAgent2

Dit is de computer die als host fungeert voor de website in dit voor beeld.
Op de computer moet [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016)worden uitgevoerd.

## <a name="add-the-code-to-tfs"></a>De code toevoegen aan TFS

We beginnen met het maken van een Git-opslag plaats in TFS en het importeren van de code uit de lokale opslag plaats op de client computer.
Als u de Demo_CI opslag plaats nog niet hebt gekloond op uw client computer, doet u dat nu door de volgende Git-opdracht uit te voeren:

`git clone https://github.com/PowerShell/Demo_CI`

1. Ga op de client computer naar uw TFS-server in een webbrowser.
1. Maak in TFS [een nieuw team project met de](/azure/devops/organizations/projects/create-project) naam Demo_CI.

   Zorg ervoor dat **versie beheer** is ingesteld op **Git**.
1. Voeg op de client computer een extern onderdeel toe aan de opslag plaats die u zojuist hebt gemaakt in TFS met de volgende opdracht:

   `git remote add tfs <YourTFSRepoURL>`

   Waarbij `<YourTFSRepoURL>` de kloon-URL is van de TFS-opslag plaats die u in de vorige stap hebt gemaakt.

   Zie [een bestaand Git-opslag plaats klonen](/azure/devops/repos/git/clone)als u niet weet waar u deze URL kunt vinden.
1. Push de code van uw lokale opslag plaats naar uw TFS-opslag plaats met de volgende opdracht:

   `git push tfs --all`
1. De TFS-opslag plaats wordt gevuld met de Demo_CI-code.

> [!NOTE]
> In dit voor beeld wordt de code in de `ci-cd-example` vertakking van het git-opslag plaats gebruikt.
> Zorg ervoor dat u deze vertakking opgeeft als de standaard vertakking in uw TFS-project en voor de CI/CD-triggers die u maakt.

## <a name="understanding-the-code"></a>De code begrijpen

Voordat we de builds-en implementatie pijplijnen maken, kijken we naar een aantal code om te begrijpen wat er gebeurt.
Open uw favoriete tekst editor op de client computer en ga naar de hoofdmap van uw Demo_CI Git-opslag plaats.

### <a name="the-dsc-configuration"></a>De DSC-configuratie

Open de bestands `DNSServer.ps1` (in de hoofdmap van de lokale Demo_CI opslag plaats `./InfraDNS/Configs/DNSServer.ps1`).

Dit bestand bevat de DSC-configuratie waarmee de DNS-server wordt ingesteld. Hier is het een volledige oplossing:

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

Let op de `Node`-instructie:

```powershell
Node $AllNodes.Where{$_.Role -eq 'DNSServer'}.NodeName
```

Hiermee worden knoop punten gevonden die zijn gedefinieerd als een rol van `DNSServer` in de [configuratie gegevens](../configurations/configData.md), die door het `DevEnv.ps1` script wordt gemaakt.

Meer informatie over de `Where` methode vindt u in [about_arrays](/powershell/module/microsoft.powershell.core/about/about_arrays)

Het gebruik van configuratie gegevens voor het definiëren van knoop punten is belang rijk bij het uitvoeren van CI omdat knooppunt informatie waarschijnlijk wordt gewijzigd tussen omgevingen en u met configuratie gegevens eenvoudig wijzigingen kunt aanbrengen in knooppunt gegevens zonder de configuratie code te wijzigen.

In het eerste bron blok roept de configuratie de **WindowsFeature** aan om ervoor te zorgen dat de DNS-functie is ingeschakeld.
De resource blokken die volgen resources aanroepen vanuit de [xDnsServer](https://github.com/PowerShell/xDnsServer) -module om de primaire zone en DNS-records te configureren.

U ziet dat de twee `xDnsRecord` blokken worden ingepakt in `foreach` lussen die door matrices in de configuratie gegevens worden herhaald.
Opnieuw worden de configuratie gegevens gemaakt door het `DevEnv.ps1` script, dat we nu bekijken.

### <a name="configuration-data"></a>Configuratiegegevens

Het `DevEnv.ps1` bestand (in de hoofdmap van de lokale Demo_CI opslag plaats, `./InfraDNS/DevEnv.ps1`) geeft de omgeving-specifieke configuratie gegevens in een hashtabel op en geeft die hashtabel door aan een aanroep van de functie `New-DscConfigurationDataDocument`, die is gedefinieerd in `DscPipelineTools.psm` (`./Assets/DscPipelineTools/DscPipelineTools.psm1`).

Het `DevEnv.ps1`-bestand:

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

Met de functie `New-DscConfigurationDataDocument` (gedefinieerd in `\Assets\DscPipelineTools\DscPipelineTools.psm1`) kunt u programmatisch een document met configuratie gegevens maken op basis van de hashtabel (knooppunt gegevens) en de matrix (niet-knooppunt gegevens) die worden door gegeven als de para meters `RawEnvData` en `OtherEnvData`.

In ons geval wordt alleen de para meter `RawEnvData` gebruikt.

### <a name="the-psake-build-script"></a>Het psake-bouw script

Het [psake](https://github.com/psake/psake) -bouw script dat in `Build.ps1` is gedefinieerd (in de hoofdmap van de Demo_CI opslag plaats, `./InfraDNS/Build.ps1`) definieert de taken die deel uitmaken van de build.
Er wordt ook gedefinieerd voor welke andere taken elke taak afhankelijk is.
Wanneer het psake-script wordt aangeroepen, wordt de opgegeven taak (of de taak met de naam `Default` als er geen is opgegeven) uitgevoerd en worden alle afhankelijkheden ook uitgevoerd (dit is recursief, zodat afhankelijkheden van de afhankelijkheden worden uitgevoerd, enzovoort).

In dit voor beeld wordt de `Default` taak gedefinieerd als:

```powershell
Task Default -depends UnitTests
```

De `Default` taak heeft geen implementatie zelf, maar heeft een afhankelijkheid van de `CompileConfigs` taak.
De resulterende keten van taak afhankelijkheden zorgt ervoor dat alle taken in het build-script worden uitgevoerd.

In dit voor beeld wordt het psake-script aangeroepen door een aanroep van `Invoke-PSake` in het `Initiate.ps1`-bestand (dat zich in de hoofdmap van de Demo_CI opslag plaats bevindt):

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

Wanneer we de build-definitie voor het voor beeld in TFS maken, leveren we ons psake-script bestand als de para meter `fileName` voor dit script.

Het build-script definieert de volgende taken:

#### <a name="generateenvironmentfiles"></a>GenerateEnvironmentFiles

Voert `DevEnv.ps1`uit, waardoor het bestand met configuratie gegevens wordt gegenereerd.

#### <a name="installmodules"></a>InstallModules

Installeert de modules die vereist zijn voor de configuratie `DNSServer.ps1`.

#### <a name="scriptanalysis"></a>ScriptAnalysis

Hiermee wordt de [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer)aangeroepen.

#### <a name="unittests"></a>Unit tests

Voert de tests voor de ziekte van de [Inpest](https://github.com/pester/Pester/wiki) -eenheid uit.

#### <a name="compileconfigs"></a>CompileConfigs

Compileert de configuratie (`DNSServer.ps1`) in een MOF-bestand met behulp van de configuratie gegevens die door de `GenerateEnvironmentFiles` taak zijn gegenereerd.

#### <a name="clean"></a>Opruimen

Hiermee maakt u de mappen die worden gebruikt voor het voor beeld en worden alle test resultaten, configuratie gegevensbestand en modules uit eerdere uitvoeringen verwijderd.

### <a name="the-psake-deploy-script"></a>Het psake-implementatie script

Het [psake](https://github.com/psake/psake) -implementatie script dat in `Deploy.ps1` is gedefinieerd (in de hoofdmap van de Demo_CI opslag plaats, `./InfraDNS/Deploy.ps1`) definieert taken waarmee de configuratie wordt geïmplementeerd en uitgevoerd.

`Deploy.ps1` definieert de volgende taken:

#### <a name="deploymodules"></a>DeployModules

Start een Power shell-sessie op `TestAgent1` en installeert de modules met de DSC-resources die vereist zijn voor de configuratie.

#### <a name="deployconfigs"></a>DeployConfigs

Roept de cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) op om de configuratie op `TestAgent1`uit te voeren.

#### <a name="integrationtests"></a>IntegrationTests

Voert de tests voor de integratie van de [ziekte](https://github.com/pester/Pester/wiki) uit.

#### <a name="acceptancetests"></a>AcceptanceTests

Voert de acceptatie tests van de [ziekte](https://github.com/pester/Pester/wiki) uit.

#### <a name="clean"></a>Opruimen

Hiermee verwijdert u alle modules die zijn geïnstalleerd in eerdere uitvoeringen en zorgt u ervoor dat de map test resultaat bestaat.

### <a name="test-scripts"></a>Test scripts

Acceptatie, integratie en eenheids tests worden gedefinieerd in scripts in de map `Tests` (in de hoofdmap van de Demo_CI opslag plaats `./InfraDNS/Tests`), elk in bestanden met de naam `DNSServer.tests.ps1` in hun respectieve mappen.

De test scripts gebruiken de syntaxis van [parasieten](https://github.com/pester/Pester/wiki) en [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) .

#### <a name="unit-tests"></a>Eenheids tests

De eenheids tests testen de DSC-configuraties zelf om ervoor te zorgen dat de configuraties te maken krijgen met wat er wordt verwacht wanneer ze worden uitgevoerd.
Het test script voor de eenheid maakt gebruik van [parasieten](https://github.com/pester/Pester/wiki).

#### <a name="integration-tests"></a>Integratie tests

De integratie tests testen de configuratie van het systeem om ervoor te zorgen dat het systeem zoals verwacht is geconfigureerd wanneer het is geïntegreerd met andere onderdelen. Deze tests worden uitgevoerd op het doel knooppunt nadat het is geconfigureerd met DSC.
Het integratie test script maakt gebruik van een combi natie van [ziekteloze](https://github.com/pester/Pester/wiki) en [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) -syntaxis.

#### <a name="acceptance-tests"></a>Acceptatie tests

Acceptatie tests testen het systeem om ervoor te zorgen dat deze naar verwachting werkt.
Zo wordt bijvoorbeeld getest of een webpagina de juiste informatie retourneert wanneer er een query wordt uitgevoerd.
Deze tests worden op afstand uitgevoerd vanaf het doel knooppunt om praktijk scenario's te testen.
Het integratie test script maakt gebruik van een combi natie van [ziekteloze](https://github.com/pester/Pester/wiki) en [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) -syntaxis.

## <a name="define-the-build"></a>De build definiëren

Nu onze code is geüpload naar TFS en u hebt bekeken wat er gebeurt, gaan we onze build definiëren.

Hier worden alleen de build-stappen besproken die u aan de build gaat toevoegen. Zie [een build-definitie maken en in de wachtrij plaatsen](/azure/devops/pipelines/create-first-pipeline)voor instructies over het maken van een build-definitie in tFS.

Maak een nieuwe build-definitie (Selecteer de **lege** sjabloon) met de naam ' InfraDNS '.
Voeg de volgende stappen toe om de definitie te bouwen:

- Power shell-script
- Testresultaten publiceren
- Bestanden kopiëren
- Artefact publiceren

Nadat u deze build-stappen hebt toegevoegd, bewerkt u de eigenschappen van elke stap als volgt:

### <a name="powershell-script"></a>Power shell-script

1. Stel de eigenschap **type** in op `File Path`.
1. Stel de eigenschap **script pad** in op `initiate.ps1`.
1. `-fileName build` toevoegen aan de eigenschap **Arguments** .

Met deze build-stap wordt het `initiate.ps1`-bestand uitgevoerd, dat het psake-build-script aanroept.

### <a name="publish-test-results"></a>Testresultaten publiceren

1. De **indeling van het test resultaat** instellen op `NUnit`
1. **Testresultaten-bestanden** instellen op `InfraDNS/Tests/Results/*.xml`
1. Stel de titel van de **test uitvoering** in op `Unit`.
1. Zorg ervoor dat de **optie opties** **ingeschakeld** en **altijd uitvoeren** zijn geselecteerd.

Met deze build-stap worden de eenheids tests uitgevoerd in het schadelijke script dat we eerder hebben bekeken en worden de resultaten opgeslagen in de map `InfraDNS/Tests/Results/*.xml`.

### <a name="copy-files"></a>Bestanden kopiëren

1. Voeg de volgende regels toe aan de **inhoud**:

   ```
   initiate.ps1
   **\deploy.ps1
   **\Acceptance\**
   **\Integration\**
   ```

1. **TargetFolder** instellen op `$(Build.ArtifactStagingDirectory)\`

Met deze stap worden de build-en test scripts gekopieerd naar de staging-directory, zodat de volgende stap kan worden gepubliceerd als constructie-artefacten.

### <a name="publish-artifact"></a>Artefact publiceren

1. **Pad instellen om** naar `$(Build.ArtifactStagingDirectory)\` te publiceren
1. **Artefact naam** instellen op `Deploy`
1. **Type artefact** instellen op `Server`
1. Selecteer `Enabled` in de **besturings opties**

## <a name="enable-continuous-integration"></a>Continue integratie inschakelen

Nu gaan we een trigger instellen die ervoor zorgt dat het project op elk gewenst moment een wijziging in de vertakking `ci-cd-example` van de Git-opslag plaats wordt ingecheckt.

1. Klik in TFS op het tabblad **Build & release**
1. Selecteer de definitie van de `DNS Infra` build en klik op **bewerken**
1. Klik op het tabblad **Triggers**
1. Selecteer **doorlopende integratie (CI)** en selecteer `refs/heads/ci-cd-example` in de vervolg keuzelijst vertakking
1. Klik op **Opslaan** en vervolgens op **OK**

Elke wijziging in de TFS Git-opslag plaats activeert nu een geautomatiseerde build.

## <a name="create-the-release-definition"></a>De release definitie maken

We gaan een release definitie maken zodat het project wordt geïmplementeerd in de ontwikkel omgeving met elke code inchecken.

Als u dit wilt doen, voegt u een nieuwe release definitie toe aan de `InfraDNS` build-definitie die u eerder hebt gemaakt.
Zorg ervoor dat u **doorlopende implementatie** selecteert zodat een nieuwe release wordt geactiveerd wanneer een nieuwe build wordt voltooid.
([Wat zijn release pijplijnen?](/azure/devops/pipelines/release/)) en configureer deze als volgt:

Voeg de volgende stappen toe aan de release definitie:

- Power shell-script
- Testresultaten publiceren
- Testresultaten publiceren

Bewerk de stappen als volgt:

### <a name="powershell-script"></a>Power shell-script

1. Stel het veld **scriptpad** in op `$(Build.DefinitionName)\Deploy\initiate.ps1"`
1. Stel het veld **Arguments** in op `-fileName Deploy`

### <a name="first-publish-test-results"></a>Eerste publicatie Testresultaten

1. `NUnit` selecteren voor het veld met de indeling van het **test resultaat**
1. Stel het veld **test resultaat bestanden** in op `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Integration*.xml`
1. De titel van de **test uitvoering** instellen op `Integration`
1. Schakel onder **controle opties de optie** **altijd uitvoeren**

### <a name="second-publish-test-results"></a>Tweede publicatie Testresultaten

1. `NUnit` selecteren voor het veld met de indeling van het **test resultaat**
1. Stel het veld **test resultaat bestanden** in op `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Acceptance*.xml`
1. De titel van de **test uitvoering** instellen op `Acceptance`
1. Schakel onder **controle opties de optie** **altijd uitvoeren**

## <a name="verify-your-results"></a>Uw resultaten controleren

Telkens wanneer u wijzigingen in de `ci-cd-example` vertakking naar TFS pusht, wordt een nieuwe build gestart.
Als de build is voltooid, wordt er een nieuwe implementatie geactiveerd.

U kunt het resultaat van de implementatie controleren door een browser te openen op de client computer en te navigeren naar `www.contoso.com`.

## <a name="next-steps"></a>Volgende stappen

In dit voor beeld wordt de DNS-server zo geconfigureerd `TestAgent1` dat de URL `www.contoso.com` omgezet in `TestAgent2`, maar dat er geen website wordt geïmplementeerd.
Het skelet hiervoor is te zien in de opslag plaats onder de map `WebApp`.
U kunt de beschik bare stubs gebruiken voor het maken van psake-scripts, ziekte tests en DSC-configuraties om uw eigen website te implementeren.
