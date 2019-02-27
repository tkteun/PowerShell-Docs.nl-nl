---
title: Naam van Element voor weergave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3a31010d-1db9-44ae-a7f3-6ed32cb641cb
caps.latest.revision: 16
ms.openlocfilehash: 097d20cb6a04635124d1f96823248df6095ca1af
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849264"
---
# <a name="name-element-for-view-format"></a>Het element Naam voor Weergave (opmaak)

Hiermee geeft u de naam die wordt gebruikt voor het identificeren van de weergave.

Configuratie-Element (indeling) ViewDefinitions-Element (indeling) weergave-Element (indeling) naamelement (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<Name>ViewName</Name>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `Name` element. Slechts één `Name` element is toegestaan voor elke weergave.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[Weergave-Element (indeling)](./view-element-format.md)|Hiermee definieert u een weergave die wordt gebruikt om de leden van een of meer .NET-objecten weer te geven.|

## <a name="text-value"></a>Tekstwaarde

Geef een unieke beschrijvende naam voor de weergave. Deze naam kan een verwijzing naar het type van de weergave (zoals een tabel of lijstweergave), welke object of een set van objecten gebruikt u de weergave, welke opdracht retourneert de objecten of een combinatie hiervan bevatten.

## <a name="remarks"></a>Opmerkingen

Zie de volgende onderwerpen voor meer informatie over de verschillende typen weergaven: [Weergave tabel](./creating-a-table-view.md), [lijstweergave](./creating-a-list-view.md), [brede weergave](./creating-a-wide-view.md), en [aangepaste weergave](./creating-custom-controls.md).

## <a name="example"></a>Voorbeeld

Het volgende voorbeeld wordt een `View` element dat een tabelweergave voor definieert de [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object. De naam van de weergave is 'service'.

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>

```

## <a name="see-also"></a>Zie ook

[Het maken van een lijst weergeven](./creating-a-list-view.md)

[Het maken van een tabelweergave](./creating-a-table-view.md)

[Het maken van een brede weergave](./creating-a-wide-view.md)

[Het maken van aangepaste besturingselementen](./creating-custom-controls.md)

[Weergave-Element (indeling)](./view-element-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
