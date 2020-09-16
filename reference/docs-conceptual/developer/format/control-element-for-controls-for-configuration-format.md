---
title: Control-element voor besturings elementen voor configuratie (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 9447efac84cff3cc33468aeebc97a8bdd6137518
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783820"
---
# <a name="control-element-for-controls-for-configuration-format"></a>Het element Besturingselement voor Besturingselementen voor Configuratie (opmaak)

Hiermee wordt een algemeen besturings element gedefinieerd dat kan worden gebruikt door alle weer gaven van het opmaak bestand en de naam die wordt gebruikt om te verwijzen naar het besturings element.

Configuratie-element (Format) Controls element van configuratie-element (Format) voor besturings elementen voor configuratie (indeling)

## <a name="syntax"></a>Syntax

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `Control` element beschreven. U moet slechts één van beide onderliggende elementen opgeven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element CustomControl voor Besturingselement voor Besturingselementen voor Configuratie (opmaak)](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|Vereist element.<br /><br /> Hiermee wordt het besturings element gedefinieerd.|
|[Naam element voor besturings element voor configuratie (indeling)](./name-element-for-control-for-controls-for-configuration-format.md)|Vereist element.<br /><br /> Hiermee geeft u de naam op die wordt gebruikt om te verwijzen naar het besturings element.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Beheert element van configuratie (indeling)](./controls-element-for-configuration-format.md)|Hiermee definieert u de algemene besturings elementen die kunnen worden gebruikt door alle weer gaven van het opmaak bestand of door andere besturings elementen.|

## <a name="remarks"></a>Opmerkingen

In de volgende elementen kan worden verwezen naar de naam die aan dit besturings element wordt gegeven:

- [ExpressionBinding-element voor CustomItem (indeling)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- [Element GroupBy voor weer gave (indeling)](./groupby-element-for-view-format.md)

## <a name="see-also"></a>Zie ook

[Beheert element van configuratie (indeling)](./controls-element-for-configuration-format.md)

[CustomControl-element voor besturings element voor configuratie (indeling)](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[ExpressionBinding-element voor CustomItem (indeling)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[Element GroupBy voor weer gave (indeling)](./groupby-element-for-view-format.md)

[Het element Naam voor Besturingselement voor Besturingselementen voor Configuratie (opmaak)](./name-element-for-control-for-controls-for-configuration-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
