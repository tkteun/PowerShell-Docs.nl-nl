---
ms.date: 10/16/2017
keywords: DSC, Power shell, configuratie, installatie
title: Configuraties doorvoeren
description: 'Er zijn twee manieren om Power shell DSC-configuraties te nemen: push-modus en pull-modus.'
ms.openlocfilehash: 466eb43cd266ceb4ae81cc997a7b338e041f8a15
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92661724"
---
# <a name="enacting-configurations"></a>Configuraties doorvoeren

> Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5,0

Er zijn twee manieren om de configuraties van desired state Configuration (DSC) van Power shell te nemen: push-modus en pull-modus.

## <a name="push-mode"></a>Push-modus

![Overzicht van de push-modus](media/enactingConfigurations/pushModel.png "De werking van de push modus")

De push modus verwijst naar een gebruiker die actief een configuratie toepast op een doel knooppunt door de cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) aan te roepen.

Nadat u een configuratie hebt gemaakt en gecompileerd, kunt u deze in de push-modus Toep assen door de cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) aan te roepen en de para meter-Path van de cmdlet in te stellen op het pad waar de configuratie-MOF zich bevindt. Als de configuratie-MOF zich bijvoorbeeld bevindt op `C:\DSC\Configurations\localhost.mof` , past u deze toe op de lokale computer met de volgende opdracht: `Start-DscConfiguration -Path 'C:\DSC\Configurations'`

> [!NOTE]
> DSC voert een configuratie standaard uit als achtergrond taak. Als u de configuratie interactief wilt uitvoeren, roept u [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) aan met de para meter **wait** .

## <a name="pull-mode"></a>Pull-modus

![Overzicht van de pull-modus](media/enactingConfigurations/pullModel.png "Hoe werkt de pull-modus?")

Pull-clients worden in de pull-modus geconfigureerd om de gewenste status configuraties te verkrijgen van een externe pull-service. Op dezelfde manier is de pull-service ingesteld voor het hosten van de DSC-service en is deze ingericht met de configuraties en resources die vereist zijn voor de pull-clients. Elk van de pull-clients heeft een geplande gebeurtenis die een periodieke controle op de naleving van de configuratie van het knoop punt uitvoert. Wanneer de gebeurtenis de eerste keer wordt geactiveerd, maakt de lokale Configuration Manager (LCM) op de pull-client een aanvraag voor de pull-service om de configuratie op te halen die is opgegeven in de LCM. Als deze configuratie bestaat in de pull-service en de initiële validatie controles worden door gegeven, wordt de configuratie gedownload naar de pull-client, waar deze wordt uitgevoerd door de LCM.

De LCM controleert of de client in overeenstemming is met de configuratie met regel matige tussen pozen die is opgegeven door de eigenschap **ConfigurationModeFrequencyMins** van de LCM. De LCM controleert met regel matige tussen pozen die zijn opgegeven door de eigenschap **RefreshModeFrequency** van de LCM op bijgewerkte configuraties van de pull-service. Zie [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md)(Engelstalig) voor meer informatie over het configureren van de LCM.

De aanbevolen oplossing voor het hosten van een pull-service is de DSC-Cloud service, [Azure Automation](https://azure.microsoft.com/services/automation/). Dit is een gehoste oplossing die grafische beheer, rapportage en gecentraliseerd beheer biedt.

Zie [een DSC Web-pull-server instellen](pullServer.md)voor meer informatie over het instellen van een pull-service op Windows Server. Meer informatie over deze implementatie heeft beperkte functies. hiervoor is wel een ' zelf-' zelf-integratie vereist.

In de volgende onderwerpen worden pull-Services en-clients beschreven:

- [Overzicht van Azure Automation DSC](/azure/automation/automation-dsc-overview)
- [Een SMB-pull-server instellen](pullServerSMB.md)
- [Een pull-client configureren](pullClientConfigID.md)
