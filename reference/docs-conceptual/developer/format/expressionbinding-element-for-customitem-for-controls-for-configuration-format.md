---
ms.date: 09/13/2016
ms.topic: reference
title: Het element ExpressionBinding voor CustomItem voor Besturingselementen voor Configuratie (opmaak)
description: Het element ExpressionBinding voor CustomItem voor Besturingselementen voor Configuratie (opmaak)
ms.openlocfilehash: 1abcf2173e18d45839161b4c7e59f1ad238f81a1
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92655335"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-configuration-format"></a>Het element ExpressionBinding voor CustomItem voor Besturingselementen voor Configuratie (opmaak)

Hiermee worden de gegevens gedefinieerd die door het besturings element worden weer gegeven. Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.

Configuratie-element (Format) Controls element van configuratie (indeling) Control element voor besturings elementen voor configuratie (Format) CustomControl-element voor besturings element voor configuratie (indeling) CustomEntries element voor CustomControl voor configuratie (indeling) CustomEntry element voor CustomControl voor besturings elementen voor configuratie-ExpressionBinding element voor CustomItem voor besturings elementen voor configuratie (indeling)

## <a name="syntax"></a>Syntax

```xml
<ExpressionBinding>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameofCommonCustomControl</CustomControlName>
  <EnumerateCollection/>
  <ItemSelectionCondition>...</ItemSelectionCondition>
  <PropertyName>Nameof.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate></ScriptBlock>
</ExpressionBinding>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `ExpressionBinding` element beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|`CustomControl Element`|Optioneel element.<br /><br /> Hiermee wordt een besturings element gedefinieerd dat door dit besturings element wordt gebruikt.|
|[Het element CustomControlName voor ExpressionBinding voor Besturingselementen voor Configuratie (opmaak)](./customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format.md)|Optioneel element.<br /><br /> Hiermee geeft u de naam op van een algemeen besturings element of een weergave besturings element.|
|[Het element EnumerateCollection voor ExpressionBinding voor Besturingselementen voor Configuratie (opmaak)](./enumeratecollection-element-for-expressionbinding-for-controls-for-configuration-format.md)|Optioneel element.<br /><br /> Opgegeven dat de elementen van verzamelingen worden weer gegeven door het besturings element.|
|[Het element ItemSelectionCondition voor ExpressionBinding voor Besturingselementen voor Configuratie (opmaak)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|Optioneel element.<br /><br /> Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit algemene besturings element.|
|[Het element PropertyName voor ExpressionBinding voor Besturingselementen voor Configuratie (opmaak)](./propertyname-element-for-expressionbinding-for-controls-for-configuration-format.md)|Optioneel element.<br /><br /> Hiermee geeft u de .NET-eigenschap op waarvan de waarde wordt weer gegeven door het algemene besturings element.|
|[Het element ScriptBlock voor ExpressionBinding voor Besturingselementen voor Configuratie (opmaak)](./scriptblock-element-for-expressionbinding-for-controls-for-configuration-format.md)|Optioneel element.<br /><br /> Hiermee geeft u het script op waarvan de waarde wordt weer gegeven door het algemene besturings element.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[CustomItem-element voor CustomEntry voor besturings elementen voor configuratie](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|Hiermee definieert u welke gegevens worden weer gegeven in de weer gave van het aangepaste besturings element en hoe deze worden weer gegeven.|

## <a name="remarks"></a>Opmerkingen

## <a name="see-also"></a>Zie ook

[CustomItem-element voor CustomEntry voor besturings elementen voor configuratie](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
