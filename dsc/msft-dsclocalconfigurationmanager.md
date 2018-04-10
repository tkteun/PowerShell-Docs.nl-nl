---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: MSFT_DSCLocalConfigurationManager-klasse
ms.openlocfilehash: 598bd7490043975d9d965c12a7337fb3475b3ded
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="msftdsclocalconfigurationmanager-class"></a>MSFT_DSCLocalConfigurationManager-klasse

De lokale Configuration Manager (LCM) die bepaalt de status van de configuratiebestanden en Configuration Agent gebruikt om de configuraties te passen.

De volgende syntaxis van Managed Object Format (MOF) code is vereenvoudigd en bevat alle overgenomen eigenschappen.

## <a name="syntax"></a>Syntaxis
------

``` syntax
[ClassVersion("1.0.0"), dynamic, provider("dsccore"), AMENDMENT]
class MSFT_DSCLocalConfigurationManager
{
};
```

## <a name="members"></a>Leden
-------

De **MSFT_DSCLocalConfigurationManager** klasse heeft de volgende leden:

-   [Methoden] []

### <a name="methods"></a>Methoden

De **MSFT_DSCLocalConfigurationManager** klasse heeft deze methoden.

|Methode |Beschrijving |
|:--- |:---|
| [ApplyConfiguration](msft-dsclocalconfigurationmanager-applyconfiguration.md)| Gebruik de Configuration-Agent voor de configuratie die in behandeling is.|
| [DisableDebugConfiguration](msft-dsclocalconfigurationmanager-disabledebugconfiguration.md)| Hiermee schakelt u foutopsporing van DSC-resource.|
| [EnableDebugConfiguration](msft-dsclocalconfigurationmanager-enabledebugconfiguration.md)| Hiermee schakelt u foutopsporing van DSC-resource.|
| [GetConfiguration](msft-dsclocalconfigurationmanager-getconfiguration.md)| Verzendt het configuratie-document naar het beheerde knooppunt en maakt gebruik van de **ophalen** methode van de configuratie-Agent de configuratie toepassen.|
| [GetConfigurationResultOutput](msft-dsclocalconfigurationmanager-getconfigurationresultoutput.md)| Hiermee wordt de uitvoer van de Configuration-Agent met betrekking tot een specifieke taak opgehaald.|
| [GetConfigurationStatus](msft-dsclocalconfigurationmanager-getconfigurationstatus.md)| Haal de geschiedenis van de configuratie-status.|
| [GetMetaConfiguration](msft-dsclocalconfigurationmanager-getmetaconfiguration.md)| Hiermee haalt u de LCM-instellingen die worden gebruikt voor het beheren van configuratie-Agent.|
| [PerformRequiredConfigurationChecks](msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks.md)| Start de consistentiecontrole.|
| [RemoveConfiguration](msft-dsclocalconfigurationmanager-removeconfiguration.md)| Hiermee verwijdert u de configuratiebestanden.|
| [ResourceGet](msft-dsclocalconfigurationmanager-resourceget.md)| Rechtstreeks roept de **ophalen** methode van een DSC-resource.|
| [ResourceSet](msft-dsclocalconfigurationmanager-resourceset.md)| Rechtstreeks roept de **ingesteld** methode van een DSC-resource.|
| [ResourceTest](msft-dsclocalconfigurationmanager-resourcetest.md)| Rechtstreeks roept de **Test** methode van een DSC-resource.|
| [RollBack](msft-dsclocalconfigurationmanager-rollback.md)| Hiermee wordt de terug naar een eerdere configuratie.|
| [SendConfiguration](msft-dsclocalconfigurationmanager-sendconfiguration.md)| Het configuratiebestand voor verzendt naar het beheerde knooppunt en wordt deze opgeslagen als een wijziging in behandeling.|
| [SendConfigurationApply](msft-dsclocalconfigurationmanager-sendconfigurationapply.md)| Het configuratiebestand voor het beheerde knooppunt verzendt en gebruik van de configuratie-Agent voor de configuratie.|
| [SendConfigurationApplyAsync](msft-dsclocalconfigurationmanager-sendconfigurationapplyasync.md)| Het configuratie-document verzenden naar het beheerde knooppunt en start met behulp van de configuratie-Agent de configuratie toepassen. Gebruik GetConfigurationResultOutput resultaat uitvoer ophalen.|
| [SendMetaConfigurationApply](msft-dsclocalconfigurationmanager-sendmetaconfigurationapply.md)| Hiermee stelt u de LCM-instellingen die worden gebruikt voor het beheren van de configuratie-Agent.|
| [StopConfiguration](msft-dsclocalconfigurationmanager-stopconfiguration.md)| Hiermee stopt de configuratie die wordt uitgevoerd.|
| [TestConfiguration](msft-dsclocalconfigurationmanager-testconfiguration.md)| Het configuratiebestand voor het beheerde knooppunt verzendt en controleert of de huidige configuratie op basis van het document.|





## <a name="requirements"></a>Vereisten
------------
>**MOF:** DscCore.mof

>**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration