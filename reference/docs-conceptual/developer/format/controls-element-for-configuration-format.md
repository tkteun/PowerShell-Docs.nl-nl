---
title: Controls-element voor configuratie (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4d4ef63d-5866-4319-ba00-7ed96de26821
caps.latest.revision: 18
ms.openlocfilehash: ac9f7ff08f6e87ef83b5a2fe23fc58ee2651566d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359096"
---
# <a name="controls-element-for-configuration-format"></a>Het element Besturingselementen voor Configuratie (opmaak)

Hiermee definieert u de algemene besturings elementen die kunnen worden gebruikt door alle weer gaven van het opmaak bestand.

Configuratie-element (Format) bepaalt element van de configuratie (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<Controls>
  <Control>...</Control>
</Controls>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het element `Controls` beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Control-element voor besturings elementen voor configuratie (indeling)](./control-element-for-controls-for-configuration-format.md)|Vereist element.<br /><br /> Hiermee wordt een algemeen besturings element gedefinieerd dat kan worden gebruikt door alle weer gaven van het opmaak bestand.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Configuratie-element (indeling)](./configuration-element-format.md)|Vertegenwoordigt het element op het hoogste niveau van een opmaak bestand.|

## <a name="remarks"></a>Opmerkingen

U kunt een wille keurig aantal algemene besturings elementen maken. Voor elk besturings element moet u de naam opgeven die wordt gebruikt om te verwijzen naar het besturings element en de onderdelen van het besturings element.

## <a name="see-also"></a>Zie ook

[Configuratie-element (indeling)](./configuration-element-format.md)

[Control-element voor besturings elementen voor configuratie (indeling)](./control-element-for-controls-for-configuration-format.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
