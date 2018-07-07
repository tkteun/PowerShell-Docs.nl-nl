---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: MSFT_DSCLocalConfigurationManager-klasse
ms.openlocfilehash: 7f6aaf209601e99b0120407eb301d32fcfda9eb8
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892270"
---
# <a name="msftdsclocalconfigurationmanager-class"></a>MSFT_DSCLocalConfigurationManager-klasse

De lokale Configuration Manager (LCM) die bepaalt de status van de configuratiebestanden en Configuration-Agent gebruikt om de configuraties te passen.

De volgende syntaxis van Managed Object Format (MOF)-code is vereenvoudigd en bevat alle overgenomen eigenschappen.

## <a name="syntax"></a>Syntaxis

```
[ClassVersion("1.0.0"), dynamic, provider("dsccore"), AMENDMENT]
class MSFT_DSCLocalConfigurationManager
{
};
```

## <a name="members"></a>Leden

De **MSFT_DSCLocalConfigurationManager** klasse heeft de volgende leden:

- [Methoden] []

### <a name="methods"></a>Methoden

De **MSFT_DSCLocalConfigurationManager** klasse heeft deze methoden.

|Methode |Beschrijving |
|:--- |:---|
| [De ApplyConfiguration](msft-dsclocalconfigurationmanager-applyconfiguration.md)| Gebruik de configuratie van Agent voor de configuratie die in behandeling is.|
| [De DisableDebugConfiguration](msft-dsclocalconfigurationmanager-disabledebugconfiguration.md)| Hiermee schakelt u foutopsporing van DSC-resource.|
| [De EnableDebugConfiguration](msft-dsclocalconfigurationmanager-enabledebugconfiguration.md)| U kunt foutopsporing van DSC-resource.|
| [De GetConfiguration](msft-dsclocalconfigurationmanager-getconfiguration.md)| Het configuratiebestand voor verzendt naar de beheerd knooppunt en maakt gebruik van de **ophalen** methode van de Agent configureren om toe te passen van de configuratie.|
| [De GetConfigurationResultOutput](msft-dsclocalconfigurationmanager-getconfigurationresultoutput.md)| Hiermee haalt u de configuratie van Agent-uitvoer met betrekking tot een specifieke taak.|
| [De GetConfigurationStatus](msft-dsclocalconfigurationmanager-getconfigurationstatus.md)| De geschiedenis van de configuratie-status ophalen.|
| [De GetMetaConfiguration](msft-dsclocalconfigurationmanager-getmetaconfiguration.md)| De LCM-instellingen die worden gebruikt voor het beheren van configuratie-Agent worden opgehaald.|
| [De PerformRequiredConfigurationChecks](msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks.md)| De consistentiecontrole starten.|
| [De RemoveConfiguration](msft-dsclocalconfigurationmanager-removeconfiguration.md)| Hiermee verwijdert u de configuratiebestanden.|
| [De ResourceGet](msft-dsclocalconfigurationmanager-resourceget.md)| Rechtstreeks roept de **ophalen** methode van een DSC-resource.|
| [De ResourceSet](msft-dsclocalconfigurationmanager-resourceset.md)| Rechtstreeks roept de **ingesteld** methode van een DSC-resource.|
| [De ResourceTest](msft-dsclocalconfigurationmanager-resourcetest.md)| Rechtstreeks roept de **Test** methode van een DSC-resource.|
| [Ongedaan maken](msft-dsclocalconfigurationmanager-rollback.md)| Hiermee wordt de terug naar een vorige configuratie.|
| [De SendConfiguration](msft-dsclocalconfigurationmanager-sendconfiguration.md)| Het configuratiebestand voor verzendt naar de beheerd knooppunt en wordt deze opgeslagen als een wijziging in behandeling.|
| [De SendConfigurationApply](msft-dsclocalconfigurationmanager-sendconfigurationapply.md)| Het configuratiebestand voor verzendt naar de beheerd knooppunt en maakt gebruik van de Agent configureren om toe te passen van de configuratie.|
| [De SendConfigurationApplyAsync](msft-dsclocalconfigurationmanager-sendconfigurationapplyasync.md)| De configuratiedocument verzenden naar de beheerde knooppunten en start met behulp van de Agent configureren om toe te passen van de configuratie. De GetConfigurationResultOutput gebruiken om op te halen resultaat uitvoer.|
| [De SendMetaConfigurationApply](msft-dsclocalconfigurationmanager-sendmetaconfigurationapply.md)| Hiermee stelt de LCM-instellingen die worden gebruikt voor het beheren van de configuratie van Agent.|
| [De StopConfiguration](msft-dsclocalconfigurationmanager-stopconfiguration.md)| Hiermee stopt u de configuratie die wordt uitgevoerd.|
| [De TestConfiguration](msft-dsclocalconfigurationmanager-testconfiguration.md)| Het configuratiebestand voor verzendt naar de beheerd knooppunt en controleert of de huidige configuratie op basis van het document.|

## <a name="requirements"></a>Vereisten

**MOF:** DscCore.mof

**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration