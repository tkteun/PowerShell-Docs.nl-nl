---
title: Label element voor GroupBy (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3351d237-e8c2-4ec5-9500-4eceadb407c2
caps.latest.revision: 11
ms.openlocfilehash: e7158711c60d13c745bbdfab9b1b9fc7d98b34e2
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72356061"
---
# <a name="label-element-for-groupby-format"></a>Het element Label voor GroupBy (opmaak)

Hiermee geeft u een label op dat wordt weer gegeven wanneer een nieuwe groep wordt aangetroffen.

Configuratie-element (indeling) ViewDefinitions element (indeling) element weer geven (indeling) GroupBy-element voor weer gave (indeling) label element voor GroupBy (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<Label>DisplayedLabel</Label>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het element `Label` beschreven.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Element GroupBy voor weer gave (indeling)](./groupby-element-for-view-format.md)|Hiermee wordt gedefinieerd hoe een nieuwe groep objecten wordt weer gegeven.|

## <a name="text-value"></a>Tekstwaarde

Geef de tekst op die wordt weer gegeven wanneer in Windows Power shell een nieuwe eigenschap of script waarde wordt aangetroffen.

## <a name="remarks"></a>Opmerkingen

Naast de tekst die door dit element is opgegeven, wordt in Windows Power shell de nieuwe waarde weer gegeven waarmee de groep wordt gestart en wordt een lege regel voor en na de groep toegevoegd.

## <a name="example"></a>Voorbeeld

In het volgende voor beeld ziet u het label voor een nieuwe groep. Het weer gegeven label ziet er ongeveer als volgt uit: `Service Type: NewValueofProperty`

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

Zie [Wide View (GroupBy)](./wide-view-groupby.md)voor een voor beeld van een volledig indelings bestand dat dit element bevat.

## <a name="see-also"></a>Zie ook

[Element GroupBy voor weer gave (indeling)](./groupby-element-for-view-format.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
