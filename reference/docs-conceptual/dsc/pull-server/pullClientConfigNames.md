---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: Een pull-client instellen met behulp van configuratie namen in Power shell 5,0 en hoger
ms.openlocfilehash: d591e2a757130ccecaf4eaf9f363f607fca82b93
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "71941717"
---
# <a name="set-up-a-pull-client-using-configuration-names-in-powershell-50-and-later"></a>Een pull-client instellen met behulp van configuratie namen in Power shell 5,0 en hoger

> Van toepassing op: Windows Power shell 5,0

> [!IMPORTANT]
> De pull-server (Windows *-functie DSC-service*) is een ondersteund onderdeel van Windows Server, maar er zijn geen plannen om nieuwe functies of mogelijkheden aan te bieden. Het wordt aangeraden om te beginnen met het overschakelen van beheerde clients naar [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inclusief functies die verder gaan dan pull server op Windows Server) of een van de [hieronder vermelde Community](pullserver.md#community-solutions-for-pull-service)-oplossingen.

Voordat u een pull-client instelt, moet u een pull-server instellen. Deze volg orde is niet vereist, maar helpt bij het oplossen van problemen en helpt u ervoor te zorgen dat de registratie is geslaagd. U kunt de volgende hand leidingen gebruiken om een pull-server in te stellen:

- [Een DSC SMB-pull-server instellen](pullServerSmb.md)
- [Een DSC HTTP-pull-server instellen](pullServer.md)

Elk doel knooppunt kan worden geconfigureerd voor het downloaden van configuraties, resources en zelfs het rapporteren van de status ervan. In de volgende secties ziet u hoe u een pull-client kunt configureren met een SMB-share of een HTTP DSC-pull-server. Wanneer de LCM van het knoop punt wordt vernieuwd, neemt het contact op met de geconfigureerde locatie voor het downloaden van toegewezen configuraties. Als er vereiste bronnen niet aanwezig zijn op het knoop punt, worden deze automatisch gedownload vanaf de geconfigureerde locatie. Als het knoop punt is geconfigureerd met een [rapport server](reportServer.md), wordt de status van de bewerking gerapporteerd.

> [!NOTE]
> Dit onderwerp is van toepassing op Power shell 5,0.
> Zie [een pull-client instellen met configuratie-ID in Power shell 4,0](pullClientConfigID4.md) voor informatie over het instellen van een pull-client in power Shell 4,0

## <a name="configure-the-pull-client-lcm"></a>De pull-client LCM configureren

Als u een van de onderstaande voor beelden uitvoert, maakt u een nieuwe uitvoermap met de naam **PullClientConfigName** en plaatst u daar een MOF-bestand met de meta configuratie. In dit geval wordt het MOF-bestand van de meta configuratie `localhost.meta.mof`aangeduid met de naam.

Als u de configuratie wilt Toep assen, roept u de cmdlet **set-DscLocalConfigurationManager** aan, waarbij het **pad** is ingesteld op de locatie van het MOF-bestand met de meta configuratie. Bijvoorbeeld:

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigName –Verbose.
```

## <a name="configuration-name"></a>Configuratie naam

In de onderstaande voor beelden wordt de eigenschap **configuratiepad** van de LCM ingesteld op de naam van een eerder gecompileerde configuratie die is gemaakt voor dit doel. De **configuratie** naam is wat de LCM gebruikt om de juiste configuratie op de pull-server te vinden. Het MOF-configuratie bestand op de pull-server moet `<ConfigurationName>.mof`een naam hebben, in dit geval ' ClientConfig. mof '. Zie [configuraties publiceren naar een pull-server (v4/V5)](publishConfigs.md)voor meer informatie.

## <a name="set-up-a-pull-client-to-download-configurations"></a>Een pull-client instellen om configuraties te downloaden

Elke client moet worden geconfigureerd in de **pull** -modus en krijgt de URL van de pull-server waar de configuratie is opgeslagen. Hiervoor moet u de lokale Configuration Manager (LCM) configureren met de benodigde gegevens. Als u de LCM wilt configureren, maakt u een speciaal type configuratie, gedecoreerd met het kenmerk **DSCLocalConfigurationManager** . Zie [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md)(Engelstalig) voor meer informatie over het configureren van de LCM.

Met het volgende script wordt de LCM geconfigureerd voor het ophalen van configuraties van een server met de naam ' CONTOSO-PullSrv '.

- In het script definieert de pull-server in het **ConfigurationRepositoryWeb** -blok. De eigenschap **ServerURL** geeft u het eind punt voor de pull-server op.

- De eigenschap **RegistrationKey** is een gedeelde sleutel tussen alle client knooppunten voor een pull-server en die pull-server. Dezelfde waarde wordt opgeslagen in een bestand op de pull-server.
  > [!NOTE]
  > Registratie sleutels werken alleen met **Web** -pull-servers. U moet **ConfigurationID** nog steeds gebruiken met een **SMB** -pull-server.
  > Zie [een pull-client instellen met behulp van de configuratie-ID](pullClientConfigId.md) voor meer informatie over het configureren van een pull-server met behulp van **ConfigurationID**

- De eigenschap **ConfigurationNames** is een matrix die de namen specificeert van de configuraties die zijn bedoeld voor het client knooppunt.
  >**Opmerking:** Als u meer dan één waarde in de **ConfigurationNames**opgeeft, moet u ook **PartialConfiguration** -blokken in uw configuratie opgeven.
  >Zie voor meer informatie over gedeeltelijke configuraties de gedeeltelijke configuratie van de [desired state Configuration van Power shell](partialConfigs.md).

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

## <a name="set-up-a-pull-client-to-download-resources"></a>Een pull-client instellen om resources te downloaden

Als u alleen een **ConfigurationRepositoryWeb** -of **ConfigurationRepositoryShare** -blok in uw LCM-configuratie opgeeft (zoals in het voor gaande voor beeld), haalt de pull-client bronnen van dezelfde locatie op waar uw mof-bestanden worden opgeslagen. U kunt ook verschillende locaties opgeven waar clients bronnen kunnen downloaden. Als u een bron server wilt opgeven, gebruikt u een **ResourceRepositoryWeb** (voor een webpull-server) of een **ResourceRepositoryShare** -blok (voor een SMB-pull-server).

In het volgende voor beeld ziet u een-configuratie die een client instelt voor het downloaden van configuraties van een pull-server en bronnen van een SMB-share.

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

## <a name="set-up-a-pull-client-to-report-status"></a>Een pull-client instellen om de status te rapporteren

U kunt één pull-server gebruiken voor configuraties, resources en rapportage. Rapportage is standaard niet geconfigureerd voor clients. Als u een client wilt configureren voor het rapporteren van de status, moet u een **ReportRepositoryWeb** -blok maken. In het volgende voor beeld ziet u een-configuratie die een client instelt voor het ophalen van configuraties en resources, en het verzenden van rapportage gegevens naar één pull-server.

> [!NOTE]
> Een rapport server kan geen SMB-share zijn.

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
* [Een DSC Web-pull-server instellen](pullServer.md)
