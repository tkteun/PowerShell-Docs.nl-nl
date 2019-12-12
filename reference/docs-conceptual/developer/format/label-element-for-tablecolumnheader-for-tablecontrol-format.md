---
title: Label element voor TableColumnHeader voor TableControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7196f039-2f6a-41fd-b252-5b1623ebb9f9
caps.latest.revision: 11
ms.openlocfilehash: 09183a538c179f19347c3f1ed45b4ad38c2ca451
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72356040"
---
# <a name="label-element-for-tablecolumnheader-for-tablecontrol-format"></a>Het element Label voor TableColumnHeader voor TableControl (opmaak)

Hiermee wordt het label gedefinieerd dat boven aan een kolom wordt weer gegeven. Dit element wordt gebruikt bij het definiëren van een tabel weergave.

Configuratie-element (indeling) ViewDefinitions element (indeling) element van weer gave (indeling) TableControl element (Format) TableHeaders element voor TableControl (Format) TableColumnHeader-element voor TableHeaders voor TableControl (Format) voor TableColumnHeader voor TableControl (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<Label>DisplayedLabel</Label>

```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het element `Label` beschreven. Voor elke kolom is slechts één label toegestaan.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[TableColumnHeader-element voor TableHeaders voor TableControl (indeling)](./tablecolumnheader-element-format.md)|Hiermee definieert u een label, de breedte en de uitlijning van de gegevens voor een kolom van de tabel.|

## <a name="text-value"></a>Tekstwaarde

Geef de tekst op die boven aan de kolom van de tabel wordt weer gegeven. Er zijn geen beperkte tekens voor het kolom Label.

## <a name="remarks"></a>Opmerkingen

Als er geen label is opgegeven, wordt de naam van de eigenschap waarvan de waarde wordt weer gegeven in de rijen gebruikt.

Zie [een tabel weergave maken](./creating-a-table-view.md)voor meer informatie over de onderdelen van een tabel weergave.

## <a name="example"></a>Voorbeeld

In dit voor beeld ziet u een `TableColumnHeader` element waarvan het label ' kolom 1 ' is.

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a>Zie ook

[Een tabel weergave maken](./creating-a-table-view.md)

[TableColumnHeader-element (indeling)](./tablecolumnheader-element-format.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
