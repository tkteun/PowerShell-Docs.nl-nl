---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: Instellen van een Pull-Client met behulp van configuratienamen in PowerShell 5.0 en hoger
ms.openlocfilehash: d591e2a757130ccecaf4eaf9f363f607fca82b93
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079384"
---
# <a name="set-up-a-pull-client-using-configuration-names-in-powershell-50-and-later"></a>Instellen van een Pull-Client met behulp van configuratienamen in PowerShell 5.0 en hoger

> Van toepassing op: Windows PowerShell 5.0

> [!IMPORTANT]
> De Pull-Server (Windows-functie *DSC-Service*) is een ondersteunde onderdeel van Windows Server maar er zijn geen plannen om nieuwe functies en mogelijkheden bieden. Het verdient aanbeveling om te beginnen met het overstappen clients beheerd [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inclusief functies dan Pull-Server op Windows Server) of een van de community-oplossingen die zijn opgenomen [hier](pullserver.md#community-solutions-for-pull-service).

Voordat u een pull-client instelt, moet u een pull-server instellen. Al deze order niet vereist is, helpt bij het oplossen van problemen en kunt u ervoor zorgen dat de registratie geslaagd is. Als u een pull-server instelt, kunt u de volgende handleidingen:

- [Een DSC SMB-Pull-Server instellen](pullServerSmb.md)
- [Een DSC HTTP-Pull-Server instellen](pullServer.md)

Elk doelknooppunt kan worden geconfigureerd voor het downloaden van configuraties, resources, en zelfs de status rapporteren. De volgende secties laten zien hoe u een pull-client configureren met een SMB-share of een HTTP-DSC-Pull-Server. Wanneer van het knooppunt LCM vernieuwd, wordt het contact opnemen met de geconfigureerde locatie voor het downloaden van de toegewezen configuraties. Als alle vereiste resources niet aanwezig zijn op het knooppunt, wordt deze ze automatisch downloaden van de geconfigureerde locatie. Als het knooppunt is geconfigureerd met een [Report Server](reportServer.md), deze wordt vervolgens rapporteert de status van de bewerking.

> [!NOTE]
> In dit onderwerp is van toepassing op PowerShell 5.0.
> Zie voor meer informatie over het instellen van een pull-client in PowerShell 4.0 [instellen van een pull-client met behulp van configuratie-ID in PowerShell 4.0](pullClientConfigID4.md)

## <a name="configure-the-pull-client-lcm"></a>De pull-client LCM configureren

Uitvoeren van een van de voorbeelden hieronder maakt u een nieuwe map voor uitvoer met de naam **PullClientConfigName** en er een metaconfiguration MOF-bestand geplaatst. In dit geval het metaconfiguration MOF-bestand de naam `localhost.meta.mof`.

Aanroepen om toe te passen de configuratie, de **Set-DscLocalConfigurationManager** -cmdlet met de **pad** ingesteld op de locatie van het metaconfiguration MOF-bestand. Bijvoorbeeld:

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigName –Verbose.
```

## <a name="configuration-name"></a>Naam van de configuratie

De voorbeelden hieronder wordt de **ConfigurationName** eigenschap van de LCM op de naam van een eerder gecompileerde configuratie gemaakt voor dit doel. De **ConfigurationName** is wat de LCM gebruikt om te vinden van de juiste configuratie op de pull-server. Het MOF-configuratiebestand op de pull-server moet de naam `<ConfigurationName>.mof`, in dit geval 'ClientConfig.mof'. Zie voor meer informatie, [configuraties publiceren naar een Pull-Server (v4/v5)](publishConfigs.md).

## <a name="set-up-a-pull-client-to-download-configurations"></a>Instellen van een Pull-Client voor het downloaden van configuraties

Elke client moet worden geconfigureerd in **Pull** modus en de url van de pull-server waar de configuratie is opgeslagen. Om dit te doen, moet u de lokale Configuration Manager (LCM) configureren met de benodigde informatie. Als u wilt de LCM configureren, maakt u een speciaal soort configuratie, voorzien van de **DSCLocalConfigurationManager** kenmerk. Zie voor meer informatie over het configureren van de LCM [de Local Configuration Manager configureren](../managing-nodes/metaConfig.md).

Het volgende script wordt de LCM geconfigureerd voor pull-configuraties van een server met de naam 'CONTOSO-PullSrv'.

- In het script de **ConfigurationRepositoryWeb** blok definieert de pull-server. De **ServerURL** eigenschap geeft u het eindpunt voor de pull-server.

- De **RegistrationKey** eigenschap is een gedeelde sleutel tussen alle knooppunten van de client voor een pull-server en die pull-server. De dezelfde waarde wordt opgeslagen in een bestand op de pull-server.
  > [!NOTE]
  > Registratiesleutels werken alleen met **web** pull-servers. U moet nog steeds gebruiken **ConfigurationID** met een **SMB** pull-server.
  > Voor informatie over het configureren van een pull-server met behulp van **ConfigurationID**, Zie [instellen van een pull-client met behulp van configuratie-ID](pullClientConfigId.md)

- De **ConfigurationNames** eigenschap is een matrix die Hiermee geeft u de namen van de configuraties die bestemd zijn voor de client-knooppunt.
  >**Opmerking:** Als u meer dan één waarde in de **ConfigurationNames**, moet u ook opgeven **PartialConfiguration** blokkeert in uw configuratie.
  >Zie voor meer informatie over het gedeeltelijke configuraties [PowerShell Desired State Configuration gedeeltelijke configuraties](partialConfigs.md).

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
            ConfigurationNames = @('ClientConfig')
        }
    }
}
PullClientConfigNames
```

## <a name="set-up-a-pull-client-to-download-resources"></a>Instellen van een Pull-Client voor het downloaden van Resources

Als u alleen opgeeft, een **ConfigurationRepositoryWeb** of **ConfigurationRepositoryShare** blokkeren in uw configuratie LCM (zoals in het vorige voorbeeld), de pull-client-resources van hetzelfde wordt opgehaald de locatie waar "uw MOF-bestanden worden opgeslagen. Ook kunt u verschillende locaties waar resources op clients kunnen downloaden. Als u een resource-server, u een gebruiken een **ResourceRepositoryWeb** (voor een web-pull-server) of een **ResourceRepositoryShare** blokkeren (voor een SMB-pull-server).

Het volgende voorbeeld ziet een metaconfiguration instellen van een client te downloaden van configuraties van een Pull-Server en bronnen van een SMB-share.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }

        ResourceRepositoryShare SMBResources
        {
            SourcePath = '\\SMBPullServer\Resources'
        }
    }
}
PullClientConfigNames
```

## <a name="set-up-a-pull-client-to-report-status"></a>Instellen van een Pull-Client voor statusrapportage

U kunt een enkel pull-server gebruiken voor configuraties, resources en rapportage. Rapportage is niet geconfigureerd voor clients standaard. Als u een client voor statusrapportage configureren, moet u maken een **ReportRepositoryWeb** blokkeren. Het volgende voorbeeld ziet een metaconfiguration instellen van een client pull-configuraties, resources en verzenden gegevens rapporteren aan een enkele pull-server.

> [!NOTE]
> Een rapportserver mag niet een SMB-share.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }
    }
}
PullClientConfigNames
```

## <a name="see-also"></a>Zie ook

* [Instellen van een pull-client met configuratie-ID](PullClientConfigNames.md)
* [Instellen van een DSC-pull-endwebserver](pullServer.md)
