---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: Een pull-client met behulp van configuratienamen instellen
ms.openlocfilehash: 9bfcac87300d30a59b66e60ed24add32e2420e21
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2017
---
# <a name="setting-up-a-pull-client-using-configuration-names"></a>Een pull-client met behulp van configuratienamen instellen

> Van toepassing op: Windows PowerShell 5.0

Elk doelknooppunt heeft adviseert het gebruik van pull-modus en de URL opgegeven waar deze contact opnemen met de pull-server configuraties ophalen.
U moet de lokale Configuration Manager (LCM) configureren met de benodigde informatie om dit te doen.
Voor het configureren van de LCM die u maakt een speciaal soort configuratie, gedecoreerd worden met de **DSCLocalConfigurationManager** kenmerk.
Zie voor meer informatie over het configureren van de LCM [configureren van de lokale Configuration Manager](metaConfig.md).

> **Opmerking**: dit onderwerp geldt voor PowerShell 5.0.
Zie voor meer informatie over het instellen van een pull-client in PowerShell 4.0 [instellen van een pull-client met behulp van configuratie-ID in PowerShell 4.0](pullClientConfigID4.md)

Het volgende script voor het configureren van de LCM naar pull-configuraties van een server met de naam 'CONTOSO-PullSrv':

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

In het script wordt de **ConfigurationRepositoryWeb** blok definieert de pull-server.
De **ServerURL** eigenschap geeft u het eindpunt voor de pull-server.

De **RegistrationKey** eigenschap is een gedeelde sleutel tussen alle knooppunten van de client voor een pull-server en die pull-server.
Dezelfde waarde wordt opgeslagen in een bestand op de pull-server.

De **ConfigurationNames** eigenschap is een matrix die Hiermee worden de namen van de configuraties die bedoeld zijn voor de clientknooppunt.
Op de pull-server de configuratie van de MOF-bestand van dit clientknooppunt moet de naam *ConfigurationNames*MOF, waarbij *ConfigurationNames* overeenkomt met de waarde van de **ConfigurationNames**  eigenschap die u in deze metaconfiguratie instellen.

>**Opmerking:** als u opgeeft meer dan één waarde in de **ConfigurationNames**, moet u ook opgeven **PartialConfiguration** gegevensblokken die zich in uw configuratie.
Zie voor meer informatie over gedeeltelijke configuraties [PowerShell Desired State Configuration gedeeltelijke configuraties](partialConfigs.md).

Nadat dit script wordt uitgevoerd, maakt deze een nieuwe map voor uitvoer met de naam **PullClientConfigNames** en er een MOF-bestand metaconfiguratie plaatst.
In dit geval wordt het MOF-bestand metaconfiguratie worden benoemd `localhost.meta.mof`.

Aanroepen om toe te passen op de configuratie, de **Set DscLocalConfigurationManager** -cmdlet met de **pad** ingesteld op de locatie van het metaconfiguratie MOF-bestand.

```powershell
Set-DSCLocalConfigurationManager localhost –Path .\PullClientConfigNames –Verbose.
```

> **Opmerking**: registratiesleutels werken alleen met pull-webservers.
U moet nog steeds gebruiken **ConfigurationID** met een SMB-pull-server.
Voor informatie over het configureren van een pull-server met behulp van **ConfigurationID**, Zie [instellen van een pull-client met behulp van configuratie-ID](PullClientConfigNames.md)

## <a name="resource-and-report-servers"></a>Bron- en -servers

Als u alleen een **ConfigurationRepositoryWeb** of **ConfigurationRepositoryShare** blokkeren in uw configuratie LCM (zoals in het vorige voorbeeld), haalt de pull-client binnen resources uit de opgegeven server, maar wordt u rapporten niet naar verzenden.
U kunt een enkel pull-server gebruiken voor configuraties, bronnen en rapportage, maar u moet maken een **ReportRepositoryWeb** blok voor het instellen van rapportage.
Het volgende voorbeeld ziet een metaconfiguratie instellen van een client voor het pull-configuraties en resources en verzenden gegevens rapporteren aan een enkele pull-server.

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
        }
    }
}
PullClientConfigNames
```

U kunt ook verschillende pull-servers voor resources en rapportage opgeven.
Als u wilt opgeven van een resource-server u een gebruiken een **ResourceRepositoryWeb** (voor een pull-webserver) of een **ResourceRepositoryShare** blok (voor een SMB-pull-server).
Om een rapportserver die u gebruikt een **ReportRepositoryWeb** blok.
Een rapportserver mag niet een SMB-server.
De volgende metaconfiguratie configureert u een pull-client om de configuraties van **CONTOSO PullSrv** en de daarbij behorende bronnen uit **CONTOSO ResourceSrv**, en voor het verzenden van statusrapporten aan  **CONTOSO ReportSrv**:

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

        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-ResourceSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '30ef9bd8-9acf-4e01-8374-4dc35710fc90'
        }

        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL = 'https://CONTOSO-ReportSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '6b392c6a-818c-4b24-bf38-47124f1e2f14'
        }
    }
}
PullClientConfigNames
```

## <a name="see-also"></a>Zie ook

* [Instellen van een pull-client met configuratie-ID](PullClientConfigNames.md)
* [Een DSC web pull-server instellen](pullServer.md)

