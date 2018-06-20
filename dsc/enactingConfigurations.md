---
ms.date: 10/16/2017
keywords: DSC, powershell, configuratie, setup
title: Configuraties doorvoeren
ms.openlocfilehash: 3d938d14a4da645bbea7ba30ab41e0af72c4b94e
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188465"
---
# <a name="enacting-configurations"></a>Configuraties doorvoeren

>Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0

Er zijn twee manieren op te nemen PowerShell Desired State Configuration (DSC) configuraties: push- en pull-modus.

## <a name="push-mode"></a>Push-modus

![Push-modus](images/pushModel.png "hoe push-modus werkt")

Push-modus verwijst naar een gebruiker een configuratie naar een target-knooppunt actief zijn toegepast door het aanroepen van de [Start DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) cmdlet.

Na het maken en een configuratie compileren, u kunt nemen deze in de modus push door het aanroepen van de [Start DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) cmdlet, instellen van de parameter - Path van het pad naar MOF van de configuratie van de cmdlet.
Bijvoorbeeld, als de configuratie van de MOF bevindt zich op `C:\DSC\Configurations\localhost.mof`, zou u deze toepassen op de lokale computer met de volgende opdracht: `Start-DscConfiguration -Path 'C:\DSC\Configurations'`

> __Opmerking__: DSC wordt standaard een configuratie uitgevoerd als achtergrondtaak. Roep de configuratie interactief wordt uitgevoerd, de [Start DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) met de __-wacht__ parameter.

## <a name="pull-mode"></a>Pull-modus

![Pull-modus](images/pullModel.png "hoe pull-modus werkt")

In de pull-modus zijn pull-clients geconfigureerd voor de gewenste status configuraties ophalen uit een externe pull-service.
Op dezelfde manier de pull-service is ingesteld op de host de DSC-service en is ingericht met de configuraties en resources die door de pull-clients vereist zijn.
Elk van de pull-clients heeft een geplande gebeurtenis die een periodieke nalevingscontrole van de configuratie van het knooppunt uitvoert.
Wanneer de gebeurtenis wordt geactiveerd voor het eerst, doet de lokale Configuration Manager (LCM) op de pull-client een aanvraag naar de pull-service om op te halen van de configuratie die is opgegeven in de LCM.
Als deze configuratie op de pull-service bestaat en het eerste validatiecontroles wordt doorgegeven, wordt de configuratie gedownload naar de pull-client, waarbij vervolgens uitgevoerd door de LCM.

De LCM controleert of de client in overeenstemming met de configuratie met regelmatige tussenpozen opgegeven door de **ConfigurationModeFrequencyMins** eigenschap van de LCM.
De LCM gecontroleerd op bijgewerkte configuraties op de pull-service met regelmatige tussenpozen opgegeven door de **RefreshModeFrequency** eigenschap van de LCM.
Zie voor meer informatie over het configureren van de LCM [configureren van de lokale Configuration Manager](metaConfig.md).

De aanbevolen oplossing voor het hosten van een Pull-Service, is de DSC-cloudservice, [Azure Automation](https://azure.microsoft.com/services/automation/).
Dit wordt gehost oplossing biedt grafische beheerprogramma, rapportage en gecentraliseerd beheer.

Zie voor meer informatie over het instellen van een Pull-Service op Windows Server [instellen van een DSC-webserver pull](pullServer.md).
Lees echter dat deze implementatie heeft beperkte onderdelen en sommige 'zelf'-integratie is vereist.

De volgende onderwerpen wordt uitgelegd pull-service en -clients:

- [Overzicht van Azure Automation DSC](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview)
- [Instellen van een SMB-pull-server](pullServerSMB.md)
- [Een pull-client configureren](pullClientConfigID.md)