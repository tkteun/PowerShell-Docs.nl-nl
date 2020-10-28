---
ms.date: 09/13/2016
ms.topic: reference
title: Het element Besturingselementen voor Configuratie (opmaak)
description: Het element Besturingselementen voor Configuratie (opmaak)
ms.openlocfilehash: 53f874ddccf3b4f1f0a23aad608e786524bde830
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92668096"
---
# <a name="controls-element-for-configuration-format"></a>Het element Besturingselementen voor Configuratie (opmaak)

Hiermee definieert u de algemene besturings elementen die kunnen worden gebruikt door alle weer gaven van het opmaak bestand.

Configuratie-element (Format) bepaalt element van de configuratie (indeling)

## <a name="syntax"></a>Syntax

```xml
<Controls>
  <Control>...</Control>
</Controls>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `Controls` element beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element Besturingselement voor Besturingselementen voor Configuratie (opmaak)](./control-element-for-controls-for-configuration-format.md)|Vereist element.<br /><br /> Hiermee wordt een algemeen besturings element gedefinieerd dat kan worden gebruikt door alle weer gaven van het opmaak bestand.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element Configuratie (opmaak)](./configuration-element-format.md)|Vertegenwoordigt het element op het hoogste niveau van een opmaak bestand.|

## <a name="remarks"></a>Opmerkingen

U kunt een wille keurig aantal algemene besturings elementen maken. Voor elk besturings element moet u de naam opgeven die wordt gebruikt om te verwijzen naar het besturings element en de onderdelen van het besturings element.

## <a name="see-also"></a>Zie ook

[Het element Configuratie (opmaak)](./configuration-element-format.md)

[Het element Besturingselement voor Besturingselementen voor Configuratie (opmaak)](./control-element-for-controls-for-configuration-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
