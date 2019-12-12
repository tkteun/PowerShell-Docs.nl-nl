---
title: Alignment-element voor TableColumnHeader voor TableControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff85e83a-c9c2-4c37-accc-e6a27c182f3c
caps.latest.revision: 19
ms.openlocfilehash: 16b41535109ca503e679a135f5ba30054e33de5b
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72355487"
---
# <a name="alignment-element-for-tablecolumnheader-for-tablecontrol-format"></a>Het element Uitlijning voor TableColumnHeader voor TableControl (opmaak)

Hiermee wordt gedefinieerd hoe de gegevens in een kolomkop worden weer gegeven.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) TableControl element (indeling) TableHeaders element (indeling) TableColumnHeader element (indeling) uitlijning element voor TableColumnHeader (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<Alignment>AlignmentType</Alignment>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het element `Alignment` beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[TableColumnHeader-element (indeling)](./tablecolumnheader-element-format.md)|Hiermee definieert u een label, de breedte en de uitlijning van de gegevens voor een kolom van de tabel.|

## <a name="text-value"></a>Tekstwaarde

Geef een van de volgende waarden op. Deze waarden zijn niet hoofdletter gevoelig.

Hiermee worden de gegevens links uitgelijnd die worden weer gegeven in de kolom links dit is de standaard waarde als dit element niet is opgegeven.

Hiermee worden de gegevens die worden weer gegeven in de kolom aan de rechter kant uitgelijnd.

Centreert de gegevens die in de kolom worden weer gegeven.

## <a name="remarks"></a>Opmerkingen

Zie [een tabel weergave maken](./creating-a-table-view.md)voor meer informatie over de onderdelen van een tabel weergave.

## <a name="example"></a>Voorbeeld

In dit voor beeld ziet u een `TableColumnHeader` element waarvan de gegevens aan de linkerkant worden uitgelijnd.

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
