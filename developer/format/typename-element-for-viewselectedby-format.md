---
title: TypeName-Element voor ViewSelectedBy (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0ad807a9-d7d8-4e96-b799-9c6a7677cc2d
caps.latest.revision: 12
ms.openlocfilehash: e2028c479103cc414295dc24a0f9bb69190bfc66
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848137"
---
# <a name="typename-element-for-viewselectedby-format"></a>Het element TypeName voor ViewSelectedBy (opmaak)

Hiermee geeft u een .NET-object dat door de weergave wordt weergegeven.

Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) ViewSelectedBy-Element (indeling) TypeName Element voor ViewSelectedBy (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<TypeName>FullyQualifiedTypeName</TypeName>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties beschrijven kenmerken, onderliggende elementen en de bovenliggende elementen van de `TypeName` element.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[ViewSelectedBy-Element (indeling)](./viewselectedby-element-format.md)|Hiermee definieert u de .NET-objecten die worden weergegeven in de weergave.|

## <a name="text-value"></a>Tekstwaarde

Geef de volledig gekwalificeerde naam van het .NET-type, bijvoorbeeld `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Opmerkingen

Zie voor meer informatie over hoe dit element wordt gebruikt in verschillende weergaven, [het maken van een tabelweergave](./creating-a-table-view.md), [het maken van een lijstweergave](./creating-a-list-view.md), [het maken van een brede weergave](./creating-a-wide-view.md), en [ Onderdelen van de aangepaste weergave](./creating-custom-controls.md).

## <a name="example"></a>Voorbeeld

Het volgende voorbeeld ziet u hoe u de [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) -object voor een lijst weergeven. Hetzelfde schema wordt gebruikt voor de tabel, breed en aangepaste weergaven.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a>Zie ook

[Het maken van een lijst weergeven](./creating-a-list-view.md)

[Het maken van een tabelweergave](./creating-a-table-view.md)

[Het maken van een brede weergave](./creating-a-wide-view.md)

[Het maken van aangepaste besturingselementen](./creating-custom-controls.md)

[ViewSelectedBy-Element (indeling)](./viewselectedby-element-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
