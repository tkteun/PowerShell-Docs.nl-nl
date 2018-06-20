---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie, setup
title: De GetConfigurationResultOutput-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 73d10a8b44e5056e3fce1598518630a84aff6ceb
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34186803"
---
# <a name="getconfigurationresultoutput-method-of-the-msftdsclocalconfigurationmanager-class"></a>De GetConfigurationResultOutput-methode van de klasse MSFT_DSCLocalConfigurationManager

Hiermee wordt de uitvoer van de Configuration-Agent die is gekoppeld aan een specifieke taak opgehaald.

<a name="syntax"></a>Syntaxis
------

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

<a name="parameters"></a>Parameters
----------

*jobId* \[in\] de ID van de taak voor die uitvoergegevens ophalen.

*resumeOutputBookmark* \[in\] Hiermee geeft u de uitvoer moet een vervolg van een vorige bladwijzer.

*uitvoer* \[uit\] de uitvoer voor de opgegeven taak.

## <a name="return-value"></a>Retourwaarde
------------

Retourneert nul geslaagd; Anders retourneert een foutcode.

## <a name="remarks"></a>Opmerkingen

Dit is een statische methode.

## <a name="requirements"></a>Vereisten
------------
>**MOF:** DscCore.mof

>**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration


## <a name="see-also"></a>Zie ook


[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)