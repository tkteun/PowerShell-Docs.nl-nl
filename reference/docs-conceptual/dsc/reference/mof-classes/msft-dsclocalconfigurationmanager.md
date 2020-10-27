---
ms.date: 07/14/2020
ms.topic: reference
title: MSFT_DSCLocalConfigurationManager-klasse
description: MSFT_DSCLocalConfigurationManager-klasse
ms.openlocfilehash: 31112c7d15884699171ec732ac20b6960b0858a9
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92644815"
---
# <a name="msft_dsclocalconfigurationmanager-class"></a>MSFT_DSCLocalConfigurationManager-klasse

De lokale Configuration Manager (LCM) die de statussen van configuratie bestanden beheert en configuratie-agent gebruikt om de configuraties toe te passen.

De volgende syntaxis is vereenvoudigd via de code van Managed Object Format (MOF) en bevat alle overgenomen eigenschappen.

## <a name="syntax"></a>Syntax

```
[ClassVersion("1.0.0"), dynamic, provider("dsccore"), AMENDMENT]
class MSFT_DSCLocalConfigurationManager
{
};
```

## <a name="members"></a>Leden

De klasse **MSFT_DSCLocalConfigurationManager** heeft de volgende leden:

- Technieken []

### <a name="methods"></a>Methoden

De klasse **MSFT_DSCLocalConfigurationManager** heeft deze methoden.

|Methoden |Beschrijving |
|:--- |:---|
| [ApplyConfiguration (Booleaans)](msft-dsclocalconfigurationmanager-applyconfiguration.md)| Maakt gebruik van de configuratie agent om de in behandeling zijnde configuratie toe te passen.|
| [De disabledebugconfiguration ()](msft-dsclocalconfigurationmanager-disabledebugconfiguration.md)| Hiermee schakelt u fout opsporing voor DSC-resources uit.|
| [De enabledebugconfiguration (Booleaans)](msft-dsclocalconfigurationmanager-enabledebugconfiguration.md)| Hiermee schakelt u fout opsporing voor DSC-resources in.|
| [De getconfiguration ()](msft-dsclocalconfigurationmanager-getconfiguration.md)| Hiermee wordt het configuratie document naar het beheerde knoop punt verzonden en wordt de **Get** -methode van de configuratie agent gebruikt om de configuratie toe te passen.|
| [De getconfigurationresultoutput](msft-dsclocalconfigurationmanager-getconfigurationresultoutput.md)| Hiermee wordt de uitvoer van de configuratie agent opgehaald die betrekking heeft op een specifieke taak.|
| [De getconfigurationstatus](msft-dsclocalconfigurationmanager-getconfigurationstatus.md)| De geschiedenis van de configuratie status ophalen.|
| [De getmetaconfiguration](msft-dsclocalconfigurationmanager-getmetaconfiguration.md)| Hiermee worden de instellingen van de LCM opgehaald die worden gebruikt voor het beheren van de configuratie agent.|
| [De performrequiredconfigurationchecks](msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks.md)| Hiermee wordt de consistentie controle gestart.|
| [De removeconfiguration](msft-dsclocalconfigurationmanager-removeconfiguration.md)| Hiermee verwijdert u de configuratie bestanden.|
| [De resourceget](msft-dsclocalconfigurationmanager-resourceget.md)| Roept rechtstreeks de **Get** -methode van een DSC-resource aan.|
| [ResourceSet](msft-dsclocalconfigurationmanager-resourceset.md)| Roept rechtstreeks de **ingestelde** methode van een DSC-resource aan.|
| [Resource Test](msft-dsclocalconfigurationmanager-resourcetest.md)| Roept rechtstreeks de **test** methode van een DSC-resource aan.|
| [Actie](msft-dsclocalconfigurationmanager-rollback.md)| Hiermee wordt teruggedraaid naar een eerdere configuratie.|
| [De sendconfiguration](msft-dsclocalconfigurationmanager-sendconfiguration.md)| Hiermee wordt het configuratie document naar het beheerde knoop punt verzonden en opgeslagen als een wijziging in behandeling.|
| [De sendconfigurationapply](msft-dsclocalconfigurationmanager-sendconfigurationapply.md)| Hiermee wordt het configuratie document naar het beheerde knoop punt verzonden en wordt de configuratie agent gebruikt om de configuratie toe te passen.|
| [De sendconfigurationapplyasync](msft-dsclocalconfigurationmanager-sendconfigurationapplyasync.md)| Stuur het configuratie document naar het beheerde knoop punt en start met behulp van de configuratie agent om de configuratie toe te passen. Gebruik de getconfigurationresultoutput om resultaat uitvoer op te halen.|
| [De sendmetaconfigurationapply](msft-dsclocalconfigurationmanager-sendmetaconfigurationapply.md)| Hiermee stelt u de instellingen voor de LCM die worden gebruikt voor het beheren van de configuratie agent.|
| [De stopconfiguration](msft-dsclocalconfigurationmanager-stopconfiguration.md)| Hiermee wordt de configuratie gestopt die momenteel wordt uitgevoerd.|
| [De testconfiguration](msft-dsclocalconfigurationmanager-testconfiguration.md)| Hiermee wordt het configuratie document naar het beheerde knoop punt verzonden en wordt de huidige configuratie gecontroleerd op basis van het document.|

## <a name="requirements"></a>Vereisten

**MOF:** DscCore. MOF

**Naam ruimte** : Root\Microsoft\Windows\DesiredStateConfiguration
