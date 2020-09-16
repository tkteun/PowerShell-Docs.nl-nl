---
title: CustomControlName-element voor GroupBy (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 4e3102f12cd37fa72a2de1bf1db5d1f82db31222
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783735"
---
# <a name="customcontrolname-element-for-groupby-format"></a>Het element CustomControlName voor GroupBy (opmaak)

Hiermee geeft u de naam op van een aangepast besturings element dat wordt gebruikt om de nieuwe groep weer te geven. Dit element wordt gebruikt bij het definiëren van een tabel, lijst, brede of aangepaste beheer weergave.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) GroupBy-element voor weer gave (indeling) CustomControlName element van GroupBy (indeling)

## <a name="syntax"></a>Syntax

```xml
<CustomControlName>ControlName</CustomControlName>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en bovenliggende elementen van het `CustomControlName` element beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element GroupBy voor Weergave (opmaak)](./groupby-element-for-view-format.md)|Definieert hoe een nieuwe groep objecten wordt weer gegeven in Windows Power shell.|

## <a name="text-value"></a>Tekstwaarde

Geef de naam op van het aangepaste besturings element dat wordt gebruikt om een nieuwe groep weer te geven.

## <a name="remarks"></a>Opmerkingen

U kunt algemene besturings elementen maken die kunnen worden gebruikt door alle weer gaven van een opmaak bestand, en u kunt weergave besturings elementen maken die kunnen worden gebruikt door een specifieke weer gave. In de volgende elementen worden de namen van deze aangepaste besturings elementen opgegeven:

- [Het element Naam voor Besturingselement voor Besturingselementen voor Configuratie (opmaak)](./name-element-for-control-for-controls-for-configuration-format.md)

- [Het element Naam voor Besturingselement voor Besturingselementen voor Weergave (opmaak)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>Zie ook

[Het element GroupBy voor Weergave (opmaak)](./groupby-element-for-view-format.md)

[Het element Naam voor Besturingselement voor Besturingselementen voor Configuratie (opmaak)](./name-element-for-control-for-controls-for-configuration-format.md)

[Het element Naam voor Besturingselement voor Besturingselementen voor Weergave (opmaak)](./name-element-for-control-for-controls-for-view-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
