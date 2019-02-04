---
ms.date: 12/12/2018
keywords: DSC, powershell, configuratie en installatie
title: De Local Configuration Manager configureren in eerdere versies van Windows PowerShell
ms.openlocfilehash: 945d2dc95304a347ec26f2f66f5a17bfefb90997
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688859"
---
# <a name="configuring-the-local-configuration-manager-in-previous-versions-of-windows-powershell"></a>De Local Configuration Manager configureren in eerdere versies van Windows PowerShell

>Van toepassing op: Windows PowerShell 4.0

**Zie voor informatie die betrekking hebben op de Windows PowerShell 5.0 en hoger [de Local Configuration Manager configureren](metaConfig.md).**

Local Configuration Manager is de Windows PowerShell Desired State Configuration (DSC)-engine.
Deze wordt uitgevoerd op alle doelknooppunten en is verantwoordelijk voor het aanroepen van de van configuratieresources die zijn opgenomen in een script voor DSC-configuratie.
In dit onderwerp worden de eigenschappen van de lokale Configuration Manager en wordt beschreven hoe u de Local Configuration Manager-instellingen op een doelknooppunt kunt wijzigen.

## <a name="local-configuration-manager-properties"></a>Eigenschappen van lokale Configuration Manager

Hieronder vindt u de Local Configuration Manager-eigenschappen die u kunt instellen of ophalen.

- **AllowModuleOverwrite**: Hiermee wordt bepaald of door nieuwe configuraties van de configuration-service wordt gedownload naar de oude overschrijven op het doelknooppunt zijn toegestaan. Mogelijke waarden zijn True en False.
- **CertificateID**: De vingerafdruk van een certificaat dat wordt gebruikt voor het beveiligen van referenties die zijn doorgegeven in een configuratie. Zie voor meer informatie [wilt voor het beveiligen van referenties in Windows PowerShell Desired State Configuration?](https://blogs.msdn.microsoft.com/powershell/2014/01/31/want-to-secure-credentials-in-windows-powershell-desired-state-configuration/).
- **ConfigurationID**: Geeft een GUID die wordt gebruikt voor het ophalen van een specifieke configuratie-bestand van een pull-service. De GUID zorgt ervoor dat de juiste configuratie-bestand wordt geopend.
- **ConfigurationMode**: Hiermee geeft u op hoe de Local Configuration Manager daadwerkelijk geldt de configuratie voor de doelknooppunten. Het kan duren voordat de volgende waarden:
  - **ApplyOnly**: Met deze optie DSC geldt de configuratie en doet niets meer, tenzij er een nieuwe configuratie wordt gedetecteerd, ofwel door uzelf verzenden van een nieuwe configuratie rechtstreeks naar de doel-knooppunt of als u verbinding met een pull-service en de DSC maakt een nieuwe configuratie detecteert wanneer Er wordt gecontroleerd met de pull-service. Als het doelknooppunt configuratie drifts, wordt geen actie ondernomen.
  - **ApplyAndMonitor**: Met deze optie (dit is de standaardinstelling), DSC van toepassing is een nieuwe configuraties of door u rechtstreeks naar het doelknooppunt verzonden of gedetecteerd op een pull-service. Als de configuratie van het doelknooppunt drifts uit het configuratiebestand, rapporteert DSC daarna het verschil in Logboeken. Zie voor meer informatie over DSC-logboekregistratie, [gebeurtenislogboeken met behulp van fouten opsporen in Desired State Configuration](http://blogs.msdn.com/b/powershell/archive/2014/01/03/using-event-logs-to-diagnose-errors-in-desired-state-configuration.aspx).
  - **ApplyAndAutoCorrect**: Met deze optie geldt DSC eventuele nieuwe configuraties of door u rechtstreeks naar het doelknooppunt verzonden of gedetecteerd op een pull-service. Daarna, als de configuratie van het doelknooppunt drifts uit het configuratiebestand, DSC rapporteert het verschil in Logboeken en vervolgens wordt geprobeerd om aan te passen van de doel-knooppuntconfiguratie te brengen in overeenstemming met het configuratiebestand.
- **ConfigurationModeFrequencyMins**: Hiermee geeft u de frequentie (in minuten) waarbinnen de toepassing van de achtergrond van DSC probeert voor het implementeren van de huidige configuratie op het doelknooppunt. De standaardwaarde is 15. Deze waarde kan worden ingesteld in combinatie met RefreshMode. Wanneer RefreshMode is ingesteld op PULL, wordt het doelknooppunt neemt contact op met de configuration-service op basis van een interval dat is ingesteld door RefreshFrequencyMins en downloadt de huidige configuratie. Ongeacht de waarde RefreshMode geldt de engine voor consistentie op basis van het interval instellen door ConfigurationModeFrequencyMins, de meest recente configuratie die is gedownload naar het doelknooppunt. RefreshFrequencyMins moet worden ingesteld op een geheel getal meervoud van ConfigurationModeFrequencyMins.
- **Referentie**: Geeft aan dat referenties (net als bij Get-Credential) vereist voor toegang tot externe resources, zoals contact opnemen met de configuration-service.
- **DownloadManagerCustomData**: Hiermee geeft u een matrix met aangepaste gegevens die specifiek zijn voor het Downloadbeheer.
- **DownloadManagerName**: Geeft de naam van de configuratie en de module Downloadbeheer.
- **RebootNodeIfNeeded**: Stel dit in op `$true` om toe te staan van bronnen op te starten op het knooppunt met behulp van de `$global:DSCMachineStatus` vlag. Anders moet u handmatig het knooppunt voor de configuratie die vereist dat het opnieuw opstarten. De standaardwaarde is `$false`. Voor het gebruik van deze instelling als de voorwaarde van een opnieuw opstarten wordt gepubliceerd door iets anders dan DSC (zoals Windows-installatieprogramma), combineert u deze instelling met de [xPendingReboot](https://github.com/powershell/xpendingreboot) module.
- **RefreshFrequencyMins**: Gebruikt wanneer u een pull-service hebt ingesteld. Hiermee geeft u de frequentie (in minuten) waarbinnen de Local Configuration Manager neemt contact op met een pull-service voor het downloaden van de huidige configuratie. Deze waarde kan worden ingesteld in combinatie met ConfigurationModeFrequencyMins. Wanneer RefreshMode is ingesteld op PULL, wordt het doelknooppunt neemt contact op met de pull-service op basis van een interval dat is ingesteld door RefreshFrequencyMins en downloadt de huidige configuratie. Volgens het interval dat is ingesteld door ConfigurationModeFrequencyMins, geldt de consistentie-engine klikt u vervolgens de meest recente configuratie die is gedownload naar het doelknooppunt. Als RefreshFrequencyMins niet is ingesteld op een geheel getal meervoud van ConfigurationModeFrequencyMins, het systeem wordt deze naar boven afronden. De standaardwaarde is 30.
- **RefreshMode**: Mogelijke waarden zijn **Push** (de standaardinstelling) en **Pull**. In de pushconfiguratie van '', moet u een configuratiebestand op elk doelknooppunt plaatsen met behulp van een clientcomputer. In de modus 'pull', moet u een pull-service voor Local Configuration Manager en neem contact op met toegang tot de configuratiebestanden instellen.

> [!NOTE]
> De LCM begint de **ConfigurationModeFrequencyMins** cyclus op basis van:
>
> - Een nieuwe metaconfig wordt toegepast met behulp van `Set-DscLocalConfigurationManager`
> - Een machine opnieuw opstarten
>
> Voor een voorwaarde waar de timer tijdens de uitvoering van een crash die binnen 30 seconden worden gedetecteerd en de cyclus wordt opnieuw gestart.
> Een gelijktijdige bewerking kan vertragen de cyclus wordt gestart, als de duur van deze bewerking de geconfigureerde cyclus frequentie overschrijdt, de volgende timer niet gestart.
>
> Bijvoorbeeld: de metaconfig is geconfigureerd met een pull-frequentie van 15 minuten en een pull-wordt uitgevoerd op T1.  Het knooppunt voor 16 minuten niet is voltooid.  De eerste 15 minuten cyclus wordt genegeerd en volgende pull bij T1 + 15 + 15 wordt uitgevoerd.

### <a name="example-of-updating-local-configuration-manager-settings"></a>Voorbeeld van de lokale Configuration Manager-instellingen bijwerken

U kunt de Local Configuration Manager-instellingen van een doelknooppunt bijwerken door op te nemen een **LocalConfigurationManager** blokkeren in het knooppunt blok in een configuratiescript, zoals wordt weergegeven in het volgende voorbeeld.

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

Het script is uitgevoerd in het vorige voorbeeld, genereert een MOF-bestand dat Hiermee geeft u en de gewenste instellingen worden opgeslagen.
Als u wilt de instellingen toepast, kunt u de **Set-DscLocalConfigurationManager** cmdlet, zoals weergegeven in het volgende voorbeeld.

```powershell
Set-DscLocalConfigurationManager -Path "c:\users\public\dsc"
```

> **Houd er rekening mee**: Voor de **pad** parameter, moet u hetzelfde pad dat u hebt opgegeven voor de **OutputPath** parameter wanneer u de configuratie in het vorige voorbeeld aangeroepen.

Als u wilt zien van de huidige instellingen van de lokale Configuration Manager, kunt u de **Get-DscLocalConfigurationManager** cmdlet.
Als u deze cmdlet zonder parameters aanroepen, krijgt het standaard maar de Local Configuration Manager-instellingen voor het knooppunt waarop u deze uitvoeren.
Als u een ander knooppunt, gebruikt u de **CimSession** parameter met deze cmdlet.
