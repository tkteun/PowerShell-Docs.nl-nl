---
title: PropertyName-Element voor WideItem voor WideControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3d91d0e6-bf18-4587-b651-db66849e5df5
caps.latest.revision: 6
ms.openlocfilehash: 326880834cd82ab826aadc409cd7a8f21cd36824
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064642"
---
# <a name="propertyname-element-for-wideitem-for-widecontrol-format"></a>Het element PropertyName voor WideItem voor WideControl (opmaak)

Hiermee geeft u de eigenschap van het object waarvan de waarde wordt weergegeven in de brede weergave.

Configuratie Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) WideControl-Element (indeling) WideEntries-Element (indeling) WideEntry Element (indeling) WideItem-Element (indeling) PropertyName-Element voor WideItem (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties worden de kenmerken, de onderliggende elementen en het bovenliggende element van de `PropertyName` element.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[WideItem-Element (indeling)](./wideitem-element-for-widecontrol-format.md)|De eigenschap of het script waarvan de waarde wordt weergegeven in de brede weergave definieert.|

## <a name="text-value"></a>Tekstwaarde

Geef de naam van de eigenschap waarvan de waarde wordt weergegeven.

## <a name="remarks"></a>Opmerkingen

Zie voor meer informatie over de onderdelen van een brede weergave [het maken van een brede weergave](./creating-a-wide-view.md).

## <a name="example"></a>Voorbeeld

In dit voorbeeld ziet u een breed overzicht waarin de waarde van de procesnaam-eigenschap van de [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.

```xml
View>
  <Name>process</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>
    <WideEntries>
      <WideEntry>
        <WideItem>
          <PropertyName>ProcessName</PropertyName>
        </WideItem>
      </WideEntry>
    </WideEntries>
  </WideControl>
</View>

```

## <a name="see-also"></a>Zie ook

[WideItem-Element (indeling)](./wideitem-element-for-widecontrol-format.md)

[Het maken van een brede weergave](./creating-a-wide-view.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
