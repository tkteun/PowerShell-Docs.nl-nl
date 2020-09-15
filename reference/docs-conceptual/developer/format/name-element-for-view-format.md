---
title: Naam element voor weer gave (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 670b089f850fa4b39b7b100ca1e1ce45b05ea72d
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773229"
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
