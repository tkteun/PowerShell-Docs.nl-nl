---
title: Element een label voor TableColumnHeader voor TableControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7196f039-2f6a-41fd-b252-5b1623ebb9f9
caps.latest.revision: 11
ms.openlocfilehash: 09183a538c179f19347c3f1ed45b4ad38c2ca451
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065747"
---
# <a name="label-element-for-tablecolumnheader-for-tablecontrol-format"></a>Het element Label voor TableColumnHeader voor TableControl (opmaak)

Hiermee definieert u het label dat wordt weergegeven aan de bovenkant van een kolom. Dit element wordt gebruikt bij het definiëren van een tabelweergave.

Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) TableControl-Element (indeling) TableHeaders Element voor TableControl (indeling) TableColumnHeader-Element voor TableHeaders voor TableControl (indeling) Label-Element voor TableColumnHeader voor TableControl (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<Label>DisplayedLabel</Label>

```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van de `Label` element. Slechts één label is toegestaan voor elke kolom.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[TableColumnHeader-Element voor TableHeaders voor TableControl (indeling)](./tablecolumnheader-element-format.md)|Een label, de breedte en de uitlijning van de gegevens voor een kolom van de tabel definieert.|

## <a name="text-value"></a>Tekstwaarde

Geef de tekst die wordt weergegeven aan de bovenkant van de kolom van de tabel. Er zijn geen tekens voor het label van de kolom.

## <a name="remarks"></a>Opmerkingen

Als u geen naam opgeeft, wordt de naam van de eigenschap waarvan de waarde wordt weergegeven in de rijen gebruikt.

Zie voor meer informatie over de onderdelen van een tabelweergave [het maken van een tabelweergave](./creating-a-table-view.md).

## <a name="example"></a>Voorbeeld

In dit voorbeeld ziet u een `TableColumnHeader` element waarvan het label 'Kolom 1' is.

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a>Zie ook

[Het maken van een tabelweergave](./creating-a-table-view.md)

[TableColumnHeader-Element (indeling)](./tablecolumnheader-element-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
