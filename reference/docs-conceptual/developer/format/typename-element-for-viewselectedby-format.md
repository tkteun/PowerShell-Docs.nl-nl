---
title: TypeName-element voor ViewSelectedBy (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0ad807a9-d7d8-4e96-b799-9c6a7677cc2d
caps.latest.revision: 12
ms.openlocfilehash: e2028c479103cc414295dc24a0f9bb69190bfc66
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72353429"
---
# <a name="typename-element-for-viewselectedby-format"></a>Het element TypeName voor ViewSelectedBy (opmaak)

Hiermee geeft u een .NET-object op dat wordt weer gegeven in de weer gave.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) ViewSelectedBy element (Format) voor ViewSelectedBy (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<TypeName>FullyQualifiedTypeName</TypeName>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden kenmerken, onderliggende elementen en de bovenliggende elementen van het element `TypeName` beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[ViewSelectedBy-element (indeling)](./viewselectedby-element-format.md)|Hiermee worden de .NET-objecten gedefinieerd die worden weer gegeven in de weer gave.|

## <a name="text-value"></a>Tekst waarde

Geef de volledig gekwalificeerde naam van het .NET-type op, bijvoorbeeld `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Opmerkingen

Zie [een tabel weergave maken](./creating-a-table-view.md), een [lijst weergave](./creating-a-list-view.md)maken, [een brede weer gave](./creating-a-wide-view.md)en [aangepaste weergave onderdelen](./creating-custom-controls.md)maken voor meer informatie over hoe dit element wordt gebruikt in verschillende weer gaven.

## <a name="example"></a>Voorbeeld

In het volgende voor beeld ziet u hoe u het object [System. ServiceProcess. servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) opgeeft voor een lijst weergave. Hetzelfde schema wordt gebruikt voor tabel-, brede en aangepaste weer gaven.

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

[Een lijst weergave maken](./creating-a-list-view.md)

[Een tabel weergave maken](./creating-a-table-view.md)

[Een brede weer gave maken](./creating-a-wide-view.md)

[Aangepaste besturings elementen maken](./creating-custom-controls.md)

[ViewSelectedBy-element (indeling)](./viewselectedby-element-format.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
