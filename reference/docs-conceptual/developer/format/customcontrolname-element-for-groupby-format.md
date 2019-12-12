---
title: CustomControlName-element voor GroupBy (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 473d9b56-521b-479a-8010-67fe9f040063
caps.latest.revision: 8
ms.openlocfilehash: 3a386eff95044eae573c255a451c5c8b8f16714d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359034"
---
# <a name="customcontrolname-element-for-groupby-format"></a>Het element CustomControlName voor GroupBy (opmaak)

Hiermee geeft u de naam op van een aangepast besturings element dat wordt gebruikt om de nieuwe groep weer te geven. Dit element wordt gebruikt bij het definiëren van een tabel, lijst, brede of aangepaste beheer weergave.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) GroupBy-element voor weer gave (indeling) CustomControlName element van GroupBy (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<CustomControlName>ControlName</CustomControlName>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en bovenliggende elementen van het element `CustomControlName` beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Element GroupBy voor weer gave (indeling)](./groupby-element-for-view-format.md)|Definieert hoe een nieuwe groep objecten wordt weer gegeven in Windows Power shell.|

## <a name="text-value"></a>Tekstwaarde

Geef de naam op van het aangepaste besturings element dat wordt gebruikt om een nieuwe groep weer te geven.

## <a name="remarks"></a>Opmerkingen

U kunt algemene besturings elementen maken die kunnen worden gebruikt door alle weer gaven van een opmaak bestand, en u kunt weergave besturings elementen maken die kunnen worden gebruikt door een specifieke weer gave. In de volgende elementen worden de namen van deze aangepaste besturings elementen opgegeven:

- [Element naam voor besturings elementen voor configuratie (indeling)](./name-element-for-control-for-controls-for-configuration-format.md)

- [Element naam voor besturings elementen voor weer gave (indeling)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>Zie ook

[Element GroupBy voor weer gave (indeling)](./groupby-element-for-view-format.md)

[Element naam voor besturings elementen voor configuratie (indeling)](./name-element-for-control-for-controls-for-configuration-format.md)

[Element naam voor besturings elementen voor weer gave (indeling)](./name-element-for-control-for-controls-for-view-format.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
