---
title: ExpressionBinding-Element voor CustomItem voor besturingselementen voor de configuratie (-indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6649d07-4762-4602-9b4b-d9e2e9e63312
caps.latest.revision: 13
ms.openlocfilehash: 531ff447f8407a737131a38351d7e4c6e7da90fb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065936"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-configuration-format"></a>Het element ExpressionBinding voor CustomItem voor Besturingselementen voor Configuratie (opmaak)

Definieert de gegevens die door het besturingselement wordt weergegeven. Dit element wordt gebruikt bij het definiëren van een algemene besturingselement dat kan worden gebruikt door alle weergaven in de opmaak-bestand.

Configuratie-Element (indeling) besturingselementen Element van configuratie (-indeling) besturingselement Element controles voor configuratie (-indeling) CustomControl-Element voor het besturingselement voor configuratie (-indeling) CustomEntries-Element voor CustomControl voor configuratie ( -Indeling) CustomEntry Element voor CustomControl controles voor configuratie (-indeling) CustomItem-Element voor CustomEntry voor besturingselementen voor ExpressionBinding, configuratie-Element voor CustomItem voor besturingselementen voor de configuratie (-indeling)

## <a name="syntax"></a>Syntaxis

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

De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `ExpressionBinding` element.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Description|
|-------------|-----------------|
|`CustomControl Element`|Optioneel element.<br /><br /> Hiermee definieert u een besturingselement dat wordt gebruikt door dit besturingselement.|
|[CustomControlName-Element voor ExpressionBinding voor besturingselementen voor de configuratie (-indeling)](./customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format.md)|Optioneel element.<br /><br /> Hiermee geeft u de naam van een algemene besturingselement of een besturingselement voor lijstweergave.|
|[EnumerateCollection-Element voor ExpressionBinding voor besturingselementen voor de configuratie (-indeling)](./enumeratecollection-element-for-expressionbinding-for-controls-for-configuration-format.md)|Optioneel element.<br /><br /> Opgegeven dat de elementen van verzamelingen worden weergegeven door het besturingselement.|
|[ItemSelectionCondition-Element voor ExpressionBinding voor besturingselementen voor de configuratie (-indeling)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|Optioneel element.<br /><br /> Hiermee definieert u de voorwaarde die moet bestaan voor dit algemene besturingselement moet worden gebruikt.|
|[PropertyName-Element voor ExpressionBinding voor besturingselementen voor de configuratie (-indeling)](./propertyname-element-for-expressionbinding-for-controls-for-configuration-format.md)|Optioneel element.<br /><br /> Hiermee geeft u de .NET-eigenschap waarvan de waarde van het algemene besturingselement wordt weergegeven.|
|[ScriptBlock-Element voor ExpressionBinding voor besturingselementen voor de configuratie (-indeling)](./scriptblock-element-for-expressionbinding-for-controls-for-configuration-format.md)|Optioneel element.<br /><br /> Hiermee geeft u het script waarvan de waarde van het algemene besturingselement wordt weergegeven.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[CustomItem-Element voor CustomEntry voor besturingselementen voor configuratie](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|Bepaalt welke gegevens worden weergegeven in de weergave van het aangepaste besturingselement en hoe deze wordt weergegeven.|

## <a name="remarks"></a>Opmerkingen

## <a name="see-also"></a>Zie ook

[CustomItem-Element voor CustomEntry voor besturingselementen voor configuratie](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
