---
title: Naam element voor weer gave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3a31010d-1db9-44ae-a7f3-6ed32cb641cb
caps.latest.revision: 16
ms.openlocfilehash: 097d20cb6a04635124d1f96823248df6095ca1af
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72354269"
---
# <a name="name-element-for-view-format"></a>Het element Naam voor Weergave (opmaak)

Hiermee geeft u de naam op die wordt gebruikt om de weer gave te identificeren.

Configuratie-element (indeling) ViewDefinitions element (indeling) element (indeling) naam element (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<Name>ViewName</Name>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het element `Name` beschreven. Voor elke weer gave is slechts één `Name` element toegestaan.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Element weer geven (indeling)](./view-element-format.md)|Hiermee wordt een weer gave gedefinieerd die wordt gebruikt om de leden van een of meer .NET-objecten weer te geven.|

## <a name="text-value"></a>Tekstwaarde

Geef een unieke beschrijvende naam op voor de weer gave. Deze naam kan een verwijzing bevatten naar het type weer gave (zoals een tabel weergave of lijst weergave), welk object of welke verzameling objecten de weer gave gebruiken, welke opdracht de objecten retourneert of een combi natie hiervan.

## <a name="remarks"></a>Opmerkingen

Voor meer informatie over de verschillende typen weer gaven raadpleegt u de volgende onderwerpen: [tabel weergave](./creating-a-table-view.md), [lijst weergave](./creating-a-list-view.md), [brede weer](./creating-a-wide-view.md) [gave en aangepaste weer](./creating-custom-controls.md)gaven.

## <a name="example"></a>Voorbeeld

In het volgende voor beeld ziet u een `View`-element dat een tabel weergave definieert voor het object [System. ServiceProcess. servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) . De naam van de weer gave is ' service '.

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

[Een lijst weergave maken](./creating-a-list-view.md)

[Een tabel weergave maken](./creating-a-table-view.md)

[Een brede weer gave maken](./creating-a-wide-view.md)

[Aangepaste besturings elementen maken](./creating-custom-controls.md)

[Element weer geven (indeling)](./view-element-format.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
