---
title: Uitlijning-Element voor TableColumnHeader voor TableControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff85e83a-c9c2-4c37-accc-e6a27c182f3c
caps.latest.revision: 19
ms.openlocfilehash: 16b41535109ca503e679a135f5ba30054e33de5b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067005"
---
# <a name="alignment-element-for-tablecolumnheader-for-tablecontrol-format"></a>Het element Uitlijning voor TableColumnHeader voor TableControl (opmaak)

Hiermee definieert u hoe de gegevens in een kolomkop wordt weergegeven.

Configuratie-Element (indeling) ViewDefinitions-Element (indeling) weergave-Element (indeling) TableControl-Element (indeling) TableHeaders-Element (indeling) TableColumnHeader Element (indeling) uitlijning Element voor TableColumnHeader (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<Alignment>AlignmentType</Alignment>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties worden de kenmerken, de onderliggende elementen en het bovenliggende element van de `Alignment` element.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[TableColumnHeader-Element (indeling)](./tablecolumnheader-element-format.md)|Een label, de breedte en de uitlijning van de gegevens voor een kolom van de tabel definieert.|

## <a name="text-value"></a>Tekstwaarde

Een van de volgende waarden opgeven. Deze waarden zijn niet hoofdlettergevoelig.

Links uitgelijnd met de gegevens in de kolom aan de linkerkant weergegeven dit is op de standaardwaarde als dit element is niet opgegeven.

Rechts uitgelijnd de gegevens in de kolom aan de rechterkant weergegeven.

Center datacenters, de gegevens die worden weergegeven in de kolom.

## <a name="remarks"></a>Opmerkingen

Zie voor meer informatie over de onderdelen van een tabelweergave [het maken van een tabelweergave](./creating-a-table-view.md).

## <a name="example"></a>Voorbeeld

In dit voorbeeld ziet u een `TableColumnHeader` element waarvan de gegevens aan de linkerkant is uitgelijnd.

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
