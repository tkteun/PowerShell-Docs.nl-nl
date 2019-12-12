---
title: WideItem-element voor WideControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17352fc4-ba83-4f04-86bc-f591765d85a8
caps.latest.revision: 18
ms.openlocfilehash: fa9eda3ea1028c27dbfb3eb04747af3b817c1a81
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72353401"
---
# <a name="wideitem-element-for-widecontrol-format"></a>Het element WideItem voor WideControl (opmaak)

Hiermee wordt de eigenschap of het script gedefinieerd waarvan de waarde wordt weer gegeven.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) WideControl element (indeling) WideEntries element (indeling) WideEntry element (indeling) WideItem element (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<WideItem>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <FormatString>FormatPattern</FormatString>
</WideItem>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het element `WideItem` beschreven. Het `FormatString`-element is optioneel. U moet echter een `PropertyName`-of `ScriptBlock`-element opgeven, maar u kunt niet beide opgeven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Element formats Tring voor WideItem voor WideControl (indeling)](./formatstring-element-for-wideitem-for-widecontrol-format.md)|Optioneel element.<br /><br /> Geeft een indelings patroon aan dat definieert hoe de eigenschap of script waarde wordt weer gegeven in de weer gave.|
|[Het element PropertyName voor WideItem (indeling)](./propertyname-element-for-wideitem-for-widecontrol-format.md)|Hiermee geeft u de eigenschap op van het object waarvan de waarde wordt weer gegeven in de brede weer gave.|
|[Script block-element voor WideItem (indeling)](./scriptblock-element-for-wideitem-for-widecontrol-format.md)|Hiermee geeft u het script op waarvan de waarde wordt weer gegeven in de brede weer gave.|

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[WideEntry-element (indeling)](./wideentry-element-for-widecontrol-format.md)|Biedt een definitie van de brede weer gave.|

## <a name="remarks"></a>Opmerkingen

Zie [brede weer gave](./creating-a-wide-view.md)voor meer informatie over de onderdelen van een brede weer gave.

## <a name="example"></a>Voorbeeld

In het volgende voor beeld ziet u een `WideEntry`-element waarmee één `WideItem` element wordt gedefinieerd. Het element `WideItem` definieert de eigenschap of het script waarvan de waarde wordt weer gegeven in de weer gave.

```xml
<WideEntry>
  <WideItem>
    <PropertyName>ProcessName</PropertyName>
  </WideItem>
</WideEntry>
```

Zie [Wide View (Basic)](./wide-view-basic.md)voor een volledig voor beeld van een brede weer gave.

## <a name="see-also"></a>Zie ook

[Element formats Tring voor WideItem voor WideControl (indeling)](./formatstring-element-for-wideitem-for-widecontrol-format.md)

[Het element PropertyName voor WideItem (indeling)](./propertyname-element-for-wideitem-for-widecontrol-format.md)

[Script block-element voor WideItem (indeling)](./scriptblock-element-for-wideitem-for-widecontrol-format.md)

[WideEntry-element (indeling)](./wideentry-element-for-widecontrol-format.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
