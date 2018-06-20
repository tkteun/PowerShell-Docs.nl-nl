---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie, setup
title: De RollBack-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: d2f9b7025d611912e119800408e25fcb66bc0228
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219875"
---
# <a name="rollback-method-of-the-msftdsclocalconfigurationmanager-class"></a>De RollBack-methode van de klasse MSFT_DSCLocalConfigurationManager

De configuratie teruggedraaid naar een eerdere versie.

<a name="syntax"></a>Syntaxis
------

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

<a name="parameters"></a>Parameters
----------

*configurationNumber* \[in\] Hiermee geeft u de aangevraagde configuratie.

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