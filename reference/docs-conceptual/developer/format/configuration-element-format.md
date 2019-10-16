---
title: Configuratie-element (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d46df0cb-50b7-4b81-82ba-37186a7b7a7f
caps.latest.revision: 28
ms.openlocfilehash: 296c63d0c774a0bf56e90dbaa32f2c221d4c3dbd
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72354871"
---
# <a name="configuration-element-format"></a>Het element Configuratie (opmaak)

Vertegenwoordigt het element op het hoogste niveau van een opmaak bestand.

Configuratie-element

## <a name="syntax"></a>Syntaxis

```xml
<Configuration>
  <DefaultSettings>...</DefaultSettings>
  <SelectionSets>...</SelectionSets>
  <Controls>...</Controls>
  <ViewDefinitions>...</ViewDefinitions>
</Configuration>

```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het element `Configuration` beschreven. Dit element moet het hoofd element voor elk opmaak bestand zijn en dit element moet ten minste één onderliggend element bevatten.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Controls-element voor configuratie (indeling)](./controls-element-for-configuration-format.md)|Optioneel element.<br /><br /> Hiermee definieert u de algemene besturings elementen die kunnen worden gebruikt door alle weer gaven van het opmaak bestand.|
|[DefaultSettings-element (indeling)](./defaultsettings-element-format.md)|Optioneel element.<br /><br /> Hiermee definieert u algemene instellingen die van toepassing zijn op alle weer gaven van het opmaak bestand.|
|[SelectionSets element indeling](./selectionsets-element-format.md)|Optioneel element.<br /><br /> Hiermee worden de algemene sets van .NET-objecten gedefinieerd die kunnen worden gebruikt door alle weer gaven van het opmaak bestand.|
|[ViewDefinitions-element (indeling)](./viewdefinitions-element-format.md)|Optioneel element.<br /><br /> Hiermee worden de weer gaven gedefinieerd waarmee objecten worden weer gegeven.|

### <a name="parent-elements"></a>Bovenliggende elementen

Geen.

## <a name="remarks"></a>Opmerkingen

Het format teren van bestanden bepaalt hoe objecten worden weer gegeven. In de meeste gevallen bevat dit hoofd element een [ViewDefinitions](./viewdefinitions-element-format.md) -element dat de tabel, lijst en brede weer gave van het opmaak bestand definieert. Naast de weergave definities kan het opmaak bestand algemene selectie sets, instellingen en besturings elementen definiëren die door die weer gaven kunnen worden gebruikt.

## <a name="see-also"></a>Zie ook

[Controls-element voor configuratie (indeling)](./controls-element-for-configuration-format.md)

[DefaultSettings-element (indeling)](./defaultsettings-element-format.md)

[SelectionSets-element (indeling)](./selectionsets-element-format.md)

[ViewDefinitions-element (indeling)](./viewdefinitions-element-format.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
