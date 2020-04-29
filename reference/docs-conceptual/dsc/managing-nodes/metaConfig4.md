---
ms.date: 12/12/2018
keywords: DSC, Power shell, configuratie, installatie
title: De LCM configureren in PowerShell 4.0
ms.openlocfilehash: 747b15c483c79a7ecbb62214ef5a59f8dc137bd4
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "71941857"
---
# <a name="configuring-the-lcm-in-powershell-40"></a>De LCM configureren in PowerShell 4.0

>Van toepassing op: Windows Power Shell 4,0

**Zie [Configuring the Local Configuration Manager](metaConfig.md)(Engelstalig) voor informatie over Windows power shell 5,0 en hoger.**

Local Configuration Manager is de Windows Power shell-engine voor desired state Configuration (DSC).
Het wordt uitgevoerd op alle doel knooppunten en is verantwoordelijk voor het aanroepen van de configuratie resources die zijn opgenomen in een DSC-configuratie script.
In dit onderwerp vindt u de eigenschappen van lokale Configuration Manager en wordt beschreven hoe u de lokale Configuration Manager-instellingen op een doel knooppunt kunt wijzigen.

## <a name="local-configuration-manager-properties"></a>Eigenschappen van lokale Configuration Manager

Hieronder vindt u de lokale Configuration Manager eigenschappen die u kunt instellen of ophalen.

- **AllowModuleOverwrite**: bepaalt of nieuwe configuraties die worden gedownload van de configuratie service, de oude kunnen overschrijven op het doel knooppunt. Mogelijke waarden zijn True en False.
- **CertificateID**: de vinger afdruk van een certificaat dat wordt gebruikt voor het beveiligen van referenties die in een configuratie zijn door gegeven. Zie voor meer informatie [referenties beveiligen in Windows Power shell desired state Configuration](https://blogs.msdn.microsoft.com/powershell/2014/01/31/want-to-secure-credentials-in-windows-powershell-desired-state-configuration/)(Engelstalig).
- **ConfigurationID**: geeft een GUID aan die wordt gebruikt om een bepaald configuratie bestand van een pull-service op te halen. De GUID zorgt ervoor dat het juiste configuratie bestand wordt geopend.
- **ConfigurationMode**: Hiermee geeft u op hoe de lokale Configuration Manager de configuratie werkelijk toepast op de doel knooppunten. Dit kan de volgende waarden hebben:
  - **ApplyOnly**: met deze optie wordt de configuratie door DSC toegepast en gebeurt er niets meer tenzij er een nieuwe configuratie wordt gedetecteerd, hetzij door u rechtstreeks een nieuwe configuratie naar het doel knooppunt te sturen of als u verbinding maakt met een pull-service en DSC een nieuwe configuratie detecteert wanneer deze de pull-service controleert. Als de configuratie drift van het doel knooppunt, wordt er geen actie ondernomen.
  - **ApplyAndMonitor**: met deze optie (dit is de standaard instelling), past DSC nieuwe configuraties toe, ongeacht of deze rechtstreeks naar het doel knooppunt zijn verzonden of op een pull-service zijn gevonden. Als de configuratie van het doel knooppunt van het configuratie bestand is, wordt de discrepantie in de logboeken door DSC gerapporteerd. Zie voor meer informatie over DSC-logboek registratie [gebeurtenis Logboeken gebruiken om fouten in de gewenste status configuratie te onderzoeken](https://blogs.msdn.com/b/powershell/archive/2014/01/03/using-event-logs-to-diagnose-errors-in-desired-state-configuration.aspx).
  - **ApplyAndAutoCorrect**: met deze optie past DSC nieuwe configuraties toe, ongeacht of deze rechtstreeks naar het doel knooppunt zijn verzonden of op een pull-service zijn gedetecteerd. Als de configuratie van het doel knooppunt van het configuratie bestand wordt opgehaald, wordt de discrepantie in Logboeken door DSC gerapporteerd en wordt vervolgens geprobeerd de configuratie van het doel knooppunt aan te passen om de compatibiliteit met het configuratie bestand te verg Roten.
- **ConfigurationModeFrequencyMins**: vertegenwoordigt de frequentie (in minuten) waarmee de achtergrond toepassing van DSC probeert de huidige configuratie op het doel knooppunt te implementeren. De standaard waarde is 15. Deze waarde kan worden ingesteld in combi natie met RefreshMode. Wanneer RefreshMode is ingesteld op PULL, neemt het doel knooppunt contact op met de configuratie service met een interval dat is ingesteld door RefreshFrequencyMins en downloadt de huidige configuratie. Ongeacht de waarde van RefreshMode, op basis van het interval dat door ConfigurationModeFrequencyMins is ingesteld, past de consistentie-engine de meest recente configuratie toe die is gedownload naar het doel knooppunt. RefreshFrequencyMins moet worden ingesteld op een veelvoud van een geheel getal van ConfigurationModeFrequencyMins.
- **Referentie**: geeft referenties aan (net als bij Get-Credential) die zijn vereist voor toegang tot externe bronnen, zoals om contact op te nemen met de configuratie service.
- **DownloadManagerCustomData**: vertegenwoordigt een matrix die aangepaste gegevens bevat die specifiek zijn voor het Download beheer.
- **DownloadManagerName**: geeft de naam aan van de configuratie-en module Download beheer.
- **RebootNodeIfNeeded**: Stel dit in `$true` op om resources toe te staan het knoop punt `$global:DSCMachineStatus` opnieuw op te starten met de vlag. Als dat niet het geval is, moet u het knoop punt hand matig opnieuw opstarten voor een configuratie waarvoor deze vereist is. De standaardwaarde is `$false`. Als u deze instelling wilt gebruiken wanneer een voor waarde voor opnieuw opstarten wordt aangenomen door iets anders dan DSC (zoals Windows Installer), moet u deze instelling combi neren met de module [xPendingReboot](https://github.com/powershell/xpendingreboot) .
- **RefreshFrequencyMins**: wordt gebruikt wanneer u een pull-service hebt ingesteld. Vertegenwoordigt de frequentie (in minuten) waarmee de lokale Configuration Manager contact opneemt met een pull-service om de huidige configuratie te downloaden. Deze waarde kan worden ingesteld in combi natie met ConfigurationModeFrequencyMins. Wanneer RefreshMode is ingesteld op PULL, neemt het doel knooppunt contact op met de pull-service met een interval dat is ingesteld door RefreshFrequencyMins en downloadt de huidige configuratie. Op basis van het interval dat is ingesteld door ConfigurationModeFrequencyMins, past de consistentie-engine de meest recente configuratie toe die is gedownload naar het doel knooppunt. Als RefreshFrequencyMins niet is ingesteld op een veelvoud van een geheel getal van ConfigurationModeFrequencyMins, wordt het door het systeem afgerond. De standaardwaarde is 30.
- **RefreshMode**: mogelijke waarden zijn **Push** (de standaard instelling) en **pull**. In de configuratie ' push ' moet u een configuratie bestand op elk doel knooppunt plaatsen met behulp van elke client computer. In de pull-modus moet u een pull-service voor lokale Configuration Manager instellen om contact op te nemen met de configuratie bestanden en deze te openen.

> [!NOTE]
> De LCM start de **ConfigurationModeFrequencyMins** -cyclus op basis van:
>
> - Er wordt een nieuwe-configuratie toegepast met behulp van`Set-DscLocalConfigurationManager`
> - Een computer opnieuw opstarten
>
> Voor elke voor waarde waarbij het timer proces vastloopt, wordt dit binnen 30 seconden gedetecteerd en wordt de cyclus opnieuw gestart.
> Een gelijktijdige bewerking kan ertoe leiden dat de cyclus wordt gestart. als de duur van deze bewerking de geconfigureerde cyclus frequentie overschrijdt, wordt de volgende timer niet gestart.
>
> Voor beeld: de configuratie van de instellingen van een pull-interval van vijf tien minuten en een pull vindt plaats in T1.  Het knoop punt is 16 minuten niet voltooid.  De eerste vijf tien minuten wordt genegeerd en de volgende pull-bewerking wordt uitgevoerd op T1 + 15 + 15.

### <a name="example-of-updating-local-configuration-manager-settings"></a>Voor beeld van het bijwerken van de instellingen van lokale Configuration Manager

U kunt de lokale Configuration Manager instellingen van een doel knooppunt bijwerken door een **LocalConfigurationManager** -blok in het knooppunt blok op te nemen in een configuratie script, zoals in het volgende voor beeld wordt weer gegeven.

```powershell
Configuration ExampleConfig
{
    Node "Server001"
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

Als u het script uitvoert in het vorige voor beeld, wordt een MOF-bestand gegenereerd dat de gewenste instellingen opgeeft en opslaat.
Als u de instellingen wilt Toep assen, kunt u de cmdlet **set-DscLocalConfigurationManager** gebruiken, zoals wordt weer gegeven in het volgende voor beeld.

```powershell
Set-DscLocalConfigurationManager -Path "c:\users\public\dsc"
```

> [!NOTE]
> Voor de para meter **Path** moet u hetzelfde pad opgeven dat u hebt opgegeven voor de para meter **OutputPath** wanneer u de configuratie in het vorige voor beeld aanroept.

Als u de huidige instellingen voor lokale Configuration Manager wilt zien, kunt u de cmdlet **Get-DscLocalConfigurationManager** gebruiken.
Als u deze cmdlet zonder para meters aanroept, worden standaard de lokale Configuration Manager-instellingen opgehaald voor het knoop punt waarop u het uitvoert.
Als u een ander knoop punt wilt opgeven, gebruikt u de para meter **CimSession** met deze cmdlet.
