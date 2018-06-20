---
ms.date: 10/12/2017
keywords: DSC, powershell, configuratie, setup
title: Configureren van de lokale Configuration Manager in eerdere versies van Windows PowerShell
ms.openlocfilehash: 05e315539e51e31b5a496e8c595ac3695d9a0c97
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189377"
---
# <a name="configuring-the-local-configuration-manager-in-previous-versions-of-windows-powershell"></a>Configureren van de lokale Configuration Manager in eerdere versies van Windows PowerShell

>Van toepassing op: Windows PowerShell 4.0

**Zie voor informatie die betrekking hebben op de Windows PowerShell 5.0 en hoger [configureren van de lokale Configuration Manager](metaConfig.md).**

Lokale Configuration Manager is de engine voor Windows PowerShell Desired State Configuration (DSC).
Deze wordt uitgevoerd op alle doelknooppunten en is verantwoordelijk voor het aanroepen van de configuratie-resources die zijn opgenomen in een DSC-configuratiescript.
Dit onderwerp worden de eigenschappen van de lokale Configuration Manager en wordt beschreven hoe u de instellingen van de lokale Configuration Manager op een doelknooppunt kunt wijzigen.

## <a name="local-configuration-manager-properties"></a>Eigenschappen van lokale Configuration Manager

Hieronder vindt u de lokale Configuration Manager-eigenschappen die u kunt instellen of ophalen.

- **AllowModuleOverwrite**: bepaalt of nieuwe configuraties van de configuration-service zijn mogen gedownload naar de oude versie in het doelknooppunt te overschrijven. Mogelijke waarden zijn True en False.
- **CertificateID**: de vingerafdruk van een certificaat gebruikt voor het beveiligen van referenties doorgegeven in een configuratie. Zie voor meer informatie [wilt beveiligen van referenties in Windows PowerShell Desired State Configuration?](http://blogs.msdn.com/b/powershell/archive/2014/01/31/want-to-secure-credentials-in-windows-powershell-desired-state-configuration.aspx).
- **ConfigurationID**: geeft een GUID die wordt gebruikt voor het ophalen van een specifieke configuratie-bestand van een pull-service. De GUID zorgt ervoor dat de juiste configuratie-bestand wordt geopend.
- **ConfigurationMode**: Hiermee geeft u op hoe de lokale Configuration Manager daadwerkelijk geldt de configuratie voor de doelknooppunten. Het kan duren voordat de volgende waarden:
  - **ApplyOnly**: met deze optie DSC geldt de configuratie en doet niets meer tenzij u een nieuwe configuratie wordt gedetecteerd, door u voor het verzenden van een nieuwe configuratie rechtstreeks naar het doelknooppunt of als u een verbinding met een pull-service en DSC een nieuwe configuratie detecteert wanneer er wordt gecontroleerd met de pull-service. Als het doelknooppunt configuratie drifts, wordt geen actie ondernomen.
  - **ApplyAndMonitor**: met deze optie (dit is de standaardinstelling), DSC eventuele nieuwe configuraties van toepassing of door u rechtstreeks naar het doelknooppunt verzonden of op een pull-service gedetecteerd. Als de configuratie van het doelknooppunt drifts uit het configuratiebestand, rapporten DSC daarna het verschil in Logboeken. Zie voor meer informatie over logboekregistratie van het DSC [met behulp van gebeurtenislogboeken fouten opsporen in Desired State Configuration](http://blogs.msdn.com/b/powershell/archive/2014/01/03/using-event-logs-to-diagnose-errors-in-desired-state-configuration.aspx).
  - **ApplyAndAutoCorrect**: met deze optie DSC van toepassing is een nieuwe configuraties of door u rechtstreeks naar het doelknooppunt verzonden of op een pull-service gedetecteerd. Daarna, als de configuratie van het doelknooppunt drifts uit het configuratiebestand, DSC rapporteert het verschil in Logboeken en probeert vervolgens de configuratie van het doel te brengen in overeenstemming met het configuratiebestand aanpassen.
- **ConfigurationModeFrequencyMins**: vertegenwoordigt de frequentie (in minuten) waarmee de achtergrondtoepassing van DSC probeert de huidige configuratie in het doelknooppunt te implementeren. De standaardwaarde is 15. Deze waarde kan worden ingesteld in combinatie met RefreshMode. Wanneer RefreshMode is ingesteld op PULL, wordt het doelknooppunt neemt contact op met de configuration-service op basis van een interval instellen door RefreshFrequencyMins en downloadt de huidige configuratie. Ongeacht de waarde RefreshMode geldt de engine voor consistentie met het interval dat is ingesteld door ConfigurationModeFrequencyMins, de meest recente configuratie die is gedownload naar het doelknooppunt. RefreshFrequencyMins moet worden ingesteld op een geheel getal veelvoud van ConfigurationModeFrequencyMins.
- **Referentie**: Hiermee wordt aangegeven referenties (zoals met Get-Credential) vereist voor toegang tot externe resources, zoals contact opnemen met de configuration-service.
- **DownloadManagerCustomData**: Hiermee geeft u een matrix met aangepaste gegevens die specifiek zijn voor het Downloadbeheer.
- **DownloadManagerName**: geeft de naam van de configuratie en de module Downloadbeheer.
- **RebootNodeIfNeeded**: bepaalde configuratiewijzigingen op een doelknooppunt mogelijk moet u deze opnieuw worden opgestart voordat de wijzigingen worden toegepast. Met de waarde **True**, wordt deze eigenschap opnieuw opstarten van het knooppunt zodra de configuratie is volledig van toepassing is, zonder verdere waarschuwing. Als **False** (de standaardwaarde), de configuratie wordt voltooid, maar het knooppunt moet handmatig opnieuw worden gestart om de wijzigingen van kracht te laten worden.
- **RefreshFrequencyMins**: gebruikt wanneer u een pull-service hebt ingesteld. Vertegenwoordigt de frequentie (in minuten) waarmee de lokale Configuration Manager contact moet een pull-service opnemen voor het downloaden van de huidige configuratie. Deze waarde kan worden ingesteld in combinatie met ConfigurationModeFrequencyMins. Wanneer RefreshMode is ingesteld op PULL, wordt het doelknooppunt neemt contact op met de pull-service op basis van een interval instellen door RefreshFrequencyMins en downloadt de huidige configuratie. De engine voor consistentie met het interval is ingesteld door ConfigurationModeFrequencyMins, wordt de meest recente configuratie die is gedownload naar het doelknooppunt toegepast. Als RefreshFrequencyMins niet is ingesteld op een geheel getal veelvoud van ConfigurationModeFrequencyMins, het systeem wordt het naar boven afronden. De standaardwaarde is 30.
- **RefreshMode**: mogelijke waarden zijn **Push** (de standaardinstelling) en **Pull**. In de configuratie van 'push', moet u een configuratiebestand op elk doelknooppunt plaatsen vanaf elke clientcomputer. In de modus 'pull', moet u een pull-service voor lokale Configuration Manager contact opnemen met en toegang tot de configuratiebestanden instellen.

### <a name="example-of-updating-local-configuration-manager-settings"></a>Voorbeeld van de lokale Configuration Manager-instellingen bijwerken

U kunt de lokale Configuration Manager-instellingen van een doelknooppunt bijwerken door een **LocalConfigurationManager** blokkeren binnen het blok knooppunt in een configuratiescript, zoals wordt weergegeven in het volgende voorbeeld.

```powershell
Configuration ExampleConfig
{
    Node “Server001”
    {
        LocalConfigurationManager
        {
            ConfigurationID = "646e48cb-3082-4a12-9fd9-f71b9a562d4e"
            ConfigurationModeFrequencyMins = 45
            ConfigurationMode = "ApplyAndAutocorrect"
            RefreshMode = "Pull"
            RefreshFrequencyMins = 90
            DownloadManagerName = "WebDownloadManager"
            DownloadManagerCustomData = (@{ServerUrl="https://$PullService/psdscpullserver.svc"})
            CertificateID = "71AA68562316FE3F73536F1096B85D66289ED60E"
            Credential = $cred
            RebootNodeIfNeeded = $true
            AllowModuleOverwrite = $false
        }
# One or more resource blocks can be added here
    }
}

# The following line invokes the configuration and creates a file called Server001.meta.mof at the specified path
ExampleConfig -OutputPath "c:\users\public\dsc"
```

Het script uitgevoerd in het vorige voorbeeld, genereert een MOF-bestand dat Hiermee geeft u en de gewenste instellingen worden opgeslagen.
Om de instellingen toepast, kunt u de **Set DscLocalConfigurationManager** cmdlet, zoals weergegeven in het volgende voorbeeld.

```powershell
Set-DscLocalConfigurationManager -Path "c:\users\public\dsc"
```

> **Opmerking**: voor de **pad** parameter, moet u hetzelfde pad dat u hebt opgegeven voor de **OutputPath** parameter bij het aanroepen van de configuratie in het vorige voorbeeld.

Overzicht van de huidige instellingen van de lokale Configuration Manager, kunt u de **Get-DscLocalConfigurationManager** cmdlet.
Als u deze cmdlet zonder parameters aanroept, krijgt het standaard maar de lokale Configuration Manager-instellingen voor het knooppunt waarop u het uitvoert.
Een ander knooppunt, gebruikt u de **CimSession** parameter met deze cmdlet.