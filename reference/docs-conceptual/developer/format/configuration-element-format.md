---
title: Configuratie-element (indeling) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 90be02f8e27c0bd391e01da1a08ecd8eeb29b84c
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783837"
---
# <a name="configuration-element-format"></a>Het element Configuratie (opmaak)

Vertegenwoordigt het element op het hoogste niveau van een opmaak bestand.

Configuratie-element

## <a name="syntax"></a>Syntax

```xml
<Configuration>
  <DefaultSettings>...</DefaultSettings>
  <SelectionSets>...</SelectionSets>
  <Controls>...</Controls>
  <ViewDefinitions>...</ViewDefinitions>
</Configuration>

```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

In de volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van het `Configuration` element beschreven. Dit element moet het hoofd element voor elk opmaak bestand zijn en dit element moet ten minste één onderliggend element bevatten.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

|Element|Beschrijving|
|-------------|-----------------|
|[Het element Besturingselementen voor Configuratie (opmaak)](./controls-element-for-configuration-format.md)|Optioneel element.<br /><br /> Hiermee definieert u de algemene besturings elementen die kunnen worden gebruikt door alle weer gaven van het opmaak bestand.|
|[Het element DefaultSettings (opmaak)](./defaultsettings-element-format.md)|Optioneel element.<br /><br /> Hiermee definieert u algemene instellingen die van toepassing zijn op alle weer gaven van het opmaak bestand.|
|[SelectionSets element indeling](./selectionsets-element-format.md)|Optioneel element.<br /><br /> Hiermee worden de algemene sets van .NET-objecten gedefinieerd die kunnen worden gebruikt door alle weer gaven van het opmaak bestand.|
|[Het element ViewDefinitions (opmaak)](./viewdefinitions-element-format.md)|Optioneel element.<br /><br /> Hiermee worden de weer gaven gedefinieerd waarmee objecten worden weer gegeven.|

### <a name="parent-elements"></a>Bovenliggende elementen

Geen.

## <a name="remarks"></a>Opmerkingen

Het format teren van bestanden bepaalt hoe objecten worden weer gegeven. In de meeste gevallen bevat dit hoofd element een [ViewDefinitions](./viewdefinitions-element-format.md) -element dat de tabel, lijst en brede weer gave van het opmaak bestand definieert. Naast de weergave definities kan het opmaak bestand algemene selectie sets, instellingen en besturings elementen definiëren die door die weer gaven kunnen worden gebruikt.

## <a name="see-also"></a>Zie ook

[Het element Besturingselementen voor Configuratie (opmaak)](./controls-element-for-configuration-format.md)

[Het element DefaultSettings (opmaak)](./defaultsettings-element-format.md)

[Het element SelectionSets (opmaak)](./selectionsets-element-format.md)

[Het element ViewDefinitions (opmaak)](./viewdefinitions-element-format.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
