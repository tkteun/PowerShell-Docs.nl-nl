---
ms.date: 10/16/2017
keywords: DSC, powershell, configuratie en installatie
title: Configuraties doorvoeren
ms.openlocfilehash: 2a40f2055dda78cc0cb6cb05a5e14dce48be9d00
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684176"
---
# <a name="enacting-configurations"></a>Configuraties doorvoeren

>Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0

Er zijn twee manieren op te nemen van PowerShell Desired State Configuration (DSC) configuraties: push- en pull-modus.

## <a name="push-mode"></a>Push-modus

![Push-modus](../images/pushModel.png "hoe push-modus werkt")

Push-modus verwijst naar het toepassen van een configuratie actief op een doelknooppunt door het aanroepen van een gebruiker de [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.

Na het maken en compileren van een configuratie, u kunt nemen deze in de pushmodus gebruikt door het aanroepen van de [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet, instellen van de parameter - Path van de cmdlet naar het pad waar de configuratie van de MOF zich bevindt.
Bijvoorbeeld, als de configuratie van de MOF bevindt zich in `C:\DSC\Configurations\localhost.mof`, zou u deze toepassen op de lokale computer met de volgende opdracht: `Start-DscConfiguration -Path 'C:\DSC\Configurations'`

> __Houd er rekening mee__: DSC wordt standaard uitgevoerd van een configuratie als achtergrondtaak. Als u wilt de configuratie van de interactief uitvoeren, aanroepen de [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) met de __-wacht__ parameter.

## <a name="pull-mode"></a>Pull-modus

![Pull-modus](../images/pullModel.png "hoe pull-modus werkt")

In de pull-modus, pull-clients geconfigureerd voor de configuraties van de gewenste status van een externe pull-service.
Evenzo, de pull-service is ingesteld op de host de DSC-service en is ingericht met de configuraties en resources die door de pull-clients vereist zijn.
Elk van de pull-clients heeft een geplande gebeurtenis waarmee een controle op periodieke naleving van de configuratie van het knooppunt worden uitgevoerd.
Wanneer de gebeurtenis wordt de eerste keer geactiveerd, maakt de lokale Configuration Manager (LCM) op de pull-client een aanvraag naar de pull-service om op te halen van de configuratie die is opgegeven in de LCM.
Als deze configuratie op de pull-service bestaat, en controleert op de eerste validatie wordt doorgegeven, wordt de configuratie gedownload naar de pull-client waarop deze wordt vervolgens uitgevoerd door de LCM.

De LCM wordt gecontroleerd of de client in overeenstemming met de configuratie met regelmatige intervallen die zijn opgegeven door de **ConfigurationModeFrequencyMins** eigenschap van de LCM.
De LCM gecontroleerd op bijgewerkte configuraties op de pull-service met regelmatige intervallen die zijn opgegeven door de **RefreshModeFrequency** eigenschap van de LCM.
Zie voor meer informatie over het configureren van de LCM [de Local Configuration Manager configureren](../managing-nodes/metaConfig.md).

De aanbevolen oplossing voor het hosten van een Pull-Service, is de DSC-cloudservice, [Azure Automation](https://azure.microsoft.com/services/automation/).
Dit wordt gehost oplossing biedt een grafische beheerprogramma, rapporten en gecentraliseerd beheer.

Zie voor meer informatie over het instellen van een Pull-Service op Windows Server [instellen van een DSC-pull-endwebserver](pullServer.md).
Begrijp echter dat deze implementatie heeft beperkte functionaliteit en sommige 'zelf'-integratie is vereist.

De volgende onderwerpen wordt uitgelegd voor pull-service en -clients:

- [Overzicht van Azure Automation DSC](https://docs.microsoft.com/azure/automation/automation-dsc-overview)
- [Instellen van een SMB-pull-server](pullServerSMB.md)
- [Een pull-client configureren](pullClientConfigID.md)
