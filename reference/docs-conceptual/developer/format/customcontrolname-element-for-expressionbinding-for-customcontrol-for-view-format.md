---
title: CustomControlName-element voor ExpressionBinding voor CustomControl voor weer gave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ea821e8b-4d65-4263-b7e4-6aeca9f534c2
caps.latest.revision: 9
ms.openlocfilehash: b44ced75bbaac7c0744f347bdc97f87365b8fe39
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72355298"
---
# <a name="customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format"></a>Het element CustomControlName voor ExpressionBinding voor CustomControl voor Weergave (opmaak)

Hiermee geeft u de naam op van een algemeen besturings element of een weergave besturings element. Dit element wordt gebruikt bij het definiëren van een aangepaste beheer weergave.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) CustomControl-element voor weer gave (indeling) CustomEntries element voor CustomControl voor weer gave (Format) CustomEntry-element voor CustomEntries voor weer gave (indeling) CustomItem Element voor CustomEntry voor View (Format) ExpressionBinding element voor CustomItem (Format) CustomControlName element voor expressie binding voor CustomItem (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `CustomControlName` beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[ExpressionBinding-element voor CustomItem (indeling)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|Hiermee worden de gegevens gedefinieerd die door het besturings element worden weer gegeven.|

## <a name="text-value"></a>Tekstwaarde

Geef de naam van het besturings element op.

## <a name="remarks"></a>Opmerkingen

U kunt algemene besturings elementen maken die kunnen worden gebruikt door alle weer gaven van een opmaak bestand en u kunt weergave besturings elementen maken die kunnen worden gebruikt door een specifieke weer gave. De namen van deze besturings elementen worden aangegeven door de volgende elementen.

- [Element naam voor besturings elementen voor configuratie (indeling)](./name-element-for-control-for-controls-for-configuration-format.md)

- [Element naam voor besturings elementen voor weer gave (indeling)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>Zie ook

[Element naam voor besturings elementen voor configuratie (indeling)](./name-element-for-control-for-controls-for-configuration-format.md)

[Element naam voor besturings elementen voor weer gave (indeling)](./name-element-for-control-for-controls-for-view-format.md)

[ExpressionBinding-element voor CustomItem (indeling)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
