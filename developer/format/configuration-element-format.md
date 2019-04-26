---
title: Configuratie-Element (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d46df0cb-50b7-4b81-82ba-37186a7b7a7f
caps.latest.revision: 28
ms.openlocfilehash: 296c63d0c774a0bf56e90dbaa32f2c221d4c3dbd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066818"
---
# <a name="configuration-element-format"></a>Het element Configuratie (opmaak)

Hiermee geeft u het element op het hoogste niveau van een bestand met opmaak.

Configuratie-Element

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

De volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van de `Configuration` element. Dit element moet het root-element voor elk bestand opmaak, en dit element moet ten minste één onderliggend element bevatten.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Description|
|-------------|-----------------|
|[Besturingselementen-Element voor configuratie (-indeling)](./controls-element-for-configuration-format.md)|Optioneel element.<br /><br /> Hiermee definieert u de algemene besturingselementen die kunnen worden gebruikt door alle weergaven van de opmaak-bestand.|
|[DefaultSettings-Element (indeling)](./defaultsettings-element-format.md)|Optioneel element.<br /><br /> Algemene instellingen die betrekking hebben op alle weergaven van de opmaak bestand definieert.|
|[SelectionSets Element opmaken](./selectionsets-element-format.md)|Optioneel element.<br /><br /> Hiermee definieert u de algemene sets met .NET-objecten die kunnen worden gebruikt door alle weergaven van de opmaak-bestand.|
|[ViewDefinitions-Element (indeling)](./viewdefinitions-element-format.md)|Optioneel element.<br /><br /> Definieert de weergaven die wordt gebruikt om objecten weer te geven.|

### <a name="parent-elements"></a>Bovenliggende elementen

Geen.

## <a name="remarks"></a>Opmerkingen

Opmaak bestanden definiëren hoe objecten worden weergegeven. In de meeste gevallen deze root-element bevat een [ViewDefinitions](./viewdefinitions-element-format.md) element dat de tabel, lijst en breed weergaven van de opmaak bestand definieert. Het opmaak-bestand kunt naast de weergavedefinities definiëren algemene selectiesets, instellingen en besturingselementen die deze weergaven kunnen gebruiken.

## <a name="see-also"></a>Zie ook

[Besturingselementen-Element voor configuratie (-indeling)](./controls-element-for-configuration-format.md)

[DefaultSettings-Element (indeling)](./defaultsettings-element-format.md)

[SelectionSets-Element (indeling)](./selectionsets-element-format.md)

[ViewDefinitions-Element (indeling)](./viewdefinitions-element-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
