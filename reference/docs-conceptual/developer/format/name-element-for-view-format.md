---
ms.date: 09/13/2016
ms.topic: reference
title: Het element Naam voor Weergave (opmaak)
description: Het element Naam voor Weergave (opmaak)
ms.openlocfilehash: 5781bcdf7a0e1eb5e9c7e97bb6acc0a383dc0262
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92666451"
---
# <a name="name-element-for-view-format"></a>Het element Naam voor Weergave (opmaak)

Hiermee geeft u de naam op die wordt gebruikt om de weer gave te identificeren.

Configuratie-element (indeling) ViewDefinitions element (indeling) element (indeling) naam element (indeling)

## <a name="syntax"></a>Syntax

```xml
<Name>ViewName</Name>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en het bovenliggende element van het `Name` element beschreven. `Name`Voor elke weer gave is slechts één element toegestaan.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element Weergave (opmaak)](./view-element-format.md)|Hiermee wordt een weer gave gedefinieerd die wordt gebruikt om de leden van een of meer .NET-objecten weer te geven.|

## <a name="text-value"></a>Tekstwaarde

Geef een unieke beschrijvende naam op voor de weer gave. Deze naam kan een verwijzing bevatten naar het type weer gave (zoals een tabel weergave of lijst weergave), welk object of welke verzameling objecten de weer gave gebruiken, welke opdracht de objecten retourneert of een combi natie hiervan.

## <a name="remarks"></a>Opmerkingen

Voor meer informatie over de verschillende typen weer gaven raadpleegt u de volgende onderwerpen: [tabel weergave](./creating-a-table-view.md), [lijst weergave](./creating-a-list-view.md), [brede weer](./creating-a-wide-view.md) [gave en aangepaste weer](./creating-custom-controls.md)gaven.

## <a name="example"></a>Voorbeeld

In het volgende voor beeld ziet u een- `View` element dat een tabel weergave definieert voor het object [System. ServiceProcess. servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) . De naam van de weer gave is ' service '.

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

[Een lijstweergave maken](./creating-a-list-view.md)

[Een tabelweergave maken](./creating-a-table-view.md)

[Een brede weergave maken](./creating-a-wide-view.md)

[Aangepaste besturingselementen maken](./creating-custom-controls.md)

[Het element Weergave (opmaak)](./view-element-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
