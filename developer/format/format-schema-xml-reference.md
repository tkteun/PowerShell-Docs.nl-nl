---
title: XML-schemaverwijzing opmaken | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ac6f7aaa-d0cc-4c7b-a341-85e736174579
caps.latest.revision: 21
ms.openlocfilehash: 437b3d6bb62fdd3a74f3392ec71df360c01a1974
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056648"
---
# <a name="format-schema-xml-reference"></a>Naslaginformatie over XML voor opmaakschema

De onderwerpen in deze sectie beschrijven de XML-elementen die worden gebruikt door de opmaak van bestanden (Format.ps1xml). Opmaak bestanden definiëren hoe de .NET-object wordt weergegeven. het object zelf niet gewijzigd.

## <a name="in-this-section"></a>In deze sectie

[Uitlijning-Element voor TableColumnHeader voor TableControl (indeling)](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) definieert hoe de gegevens in een kolomkop wordt weergegeven.

[Uitlijning-Element voor TableColumnItem voor TableControl (indeling)](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) definieert hoe de gegevens in de rij worden weergegeven.

[AutoSize-Element voor TableControl (indeling)](./autosize-element-for-tablecontrol-format.md) geeft aan of de kolomgrootte en het aantal kolommen zijn aangepast op basis van de grootte van de gegevens.

[AutoSize-Element voor WideControl (indeling)](./autosize-element-for-widecontrol-format.md) geeft aan of de kolomgrootte en het aantal kolommen zijn aangepast op basis van de grootte van de gegevens.

[ColumnNumber-Element voor WideControl (indeling)](./columnnumber-element-for-widecontrol-format.md) geeft het aantal kolommen in de brede weergave.

[Configuratie-Element (indeling)](./configuration-element-format.md) het element op het hoogste niveau van de opmaak bestand vertegenwoordigt.

[Element voor besturingselementen voor de configuratie (-indeling) beheren](./control-element-for-controls-for-configuration-format.md) definieert een algemene besturingselement dat kan worden gebruikt door alle weergaven van de opmaak bestands- en de naam die wordt gebruikt om te verwijzen naar het besturingselement.

[Element voor besturingselementen voor weergave (indeling) beheren](./control-element-for-controls-for-view-format.md) definieert een besturingselement dat kan worden gebruikt door de weergave en de naam die wordt gebruikt om te verwijzen naar het besturingselement.

[Hiermee bepaalt u Element voor configuratie (-indeling)](./controls-element-for-configuration-format.md) de algemene besturingselementen die kunnen worden gebruikt door alle weergaven van de opmaak bestand definieert.

[Hiermee bepaalt u Element voor weergave (indeling)](./controls-element-for-view-format.md) definieert de weergave-besturingselementen die kunnen worden gebruikt door een specifieke weergave.

[CustomControl-Element voor controle voor de configuratie (-indeling)](./customcontrol-element-for-control-for-controls-for-configuration-format.md) definieert een besturingselement. Dit element wordt gebruikt bij het definiëren van een algemene besturingselement dat kan worden gebruikt door alle weergaven in de opmaak-bestand.

[CustomControl-Element voor het besturingselement voor besturingselementen voor weergave (indeling)](./customcontrol-element-for-control-for-controls-for-view-format.md) definieert een besturingselement dat wordt gebruikt door de weergave.

[CustomControl-Element voor GroupBy (indeling)](./customcontrol-element-for-groupby-format.md) definieert het aangepaste besturingselement weergegeven met de nieuwe groep.

[CustomControl Element (indeling)](./customcontrol-element-for-groupby-format.md) definieert een aangepast besturingselement-indeling voor de weergave.

[CustomControlName-Element voor ExpressionBinding voor besturingselementen voor de configuratie (-indeling)](./customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format.md) Hiermee geeft u de naam van een algemene besturingselement. Dit element wordt gebruikt bij het definiëren van een algemene besturingselement dat kan worden gebruikt door alle weergaven in de opmaak-bestand.

[CustomControlName-Element voor ExpressionBindine voor besturingselementen voor weergave (indeling)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md) Hiermee geeft u de naam van een algemene besturingselement of een besturingselement voor lijstweergave. Dit element wordt gebruikt bij het definiëren van besturingselementen die kunnen worden gebruikt door een weergave.

[CustomControlName-Element van GroupBy (indeling)](./customcontrolname-element-for-groupby-format.md) geeft de naam van een aangepast besturingselement dat wordt gebruikt om de nieuwe groep weer te geven. Dit element wordt gebruikt bij het definiëren van een tabel, lijst, breed of aangepast besturingselement weergeven.

[CustomEntry-Element voor CustomControl voor besturingselementen voor de configuratie (-indeling)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md) biedt een definitie van de algemene besturingselementen. Dit element wordt gebruikt bij het definiëren van een algemene besturingselement dat kan worden gebruikt door alle weergaven in de opmaak-bestand.

[CustomEntry-Element voor CustomEntries voor besturingselementen voor weergave (indeling)](./customentry-element-for-customentries-for-controls-for-view-format.md) biedt een definitie van het besturingselement. Dit element wordt gebruikt bij het definiëren van besturingselementen die kunnen worden gebruikt door een weergave.

[CustomEntry-Element voor CustomEntries voor weergave (indeling)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md) biedt een definitie van de weergave van het aangepaste besturingselement.

[CustomEntry-Element voor CustomControl voor GroupBy (indeling)](./customentry-element-for-customcontrol-for-groupby-format.md) biedt een definitie van het besturingselement. Dit element wordt gebruikt bij het definiëren van hoe een nieuwe groep objecten worden weergegeven.

[CustomEntries-Element voor CustomControl voor configuratie (-indeling)](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md) bevat de definities van een algemene besturingselementen. Dit element wordt gebruikt bij het definiëren van een algemene besturingselement dat kan worden gebruikt door alle weergaven in de opmaak-bestand.

[CustomEntries-Element voor CustomControl voor besturingselementen voor weergave (indeling)](./customentries-element-for-customcontrol-for-controls-for-view-format.md) bevat de definities voor het besturingselement. Dit element wordt gebruikt bij het definiëren van besturingselementen die kunnen worden gebruikt door een weergave.

[CustomEntries-Element voor CustomControl voor GroupBy (indeling)](./customentries-element-for-customcontrol-for-groupby-format.md) bevat de definities voor het besturingselement. Dit element wordt gebruikt bij het definiëren van hoe een nieuwe groep objecten worden weergegeven.

[CustomEntries-Element voor CustomControl voor weergave (indeling)](./customentries-element-for-customcontrol-for-view-format.md) bevat de definities van de weergave van het aangepaste besturingselement. De weergave van het aangepaste besturingselement moet een of meer netwerkdefinities opgeven.

[CustomItem-Element voor CustomEntry voor besturingselementen voor de configuratie van](./customitem-element-for-customentry-for-controls-for-configuration-format.md) bepaalt welke gegevens worden weergegeven door het besturingselement en hoe deze wordt weergegeven. Dit element wordt gebruikt bij het definiëren van een algemene besturingselement dat kan worden gebruikt door alle weergaven in de opmaak-bestand.

[CustomItem-Element voor CustomEntry voor besturingselementen voor weergave (indeling)](./customitem-element-for-customentry-for-controls-for-view-format.md) bepaalt welke gegevens worden weergegeven door het besturingselement en hoe deze wordt weergegeven. Dit element wordt gebruikt bij het definiëren van besturingselementen die kunnen worden gebruikt door een weergave.

[CustomItem-Element voor CustomEntry voor weergave (indeling)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md) bepaalt welke gegevens worden weergegeven in de weergave van het aangepaste besturingselement en hoe deze wordt weergegeven. Dit element wordt gebruikt bij het definiëren van een aangepast besturingselement-weergave.

[CustomItem-Element voor CustomEntry voor GroupBy (indeling)](./customitem-element-for-customentry-for-groupby-format.md) bepaalt welke gegevens worden weergegeven in de weergave van het aangepaste besturingselement en hoe deze wordt weergegeven. Dit element wordt gebruikt bij het definiëren van hoe een nieuwe groep objecten worden weergegeven.

[DefaultSettings-Element (indeling)](./defaultsettings-element-format.md) algemene instellingen die betrekking hebben op alle weergaven van de opmaak bestand definieert. Algemene instellingen omvatten weergeven van fouten, tekstterugloop in tabellen, definiëren hoe verzamelingen zijn uitgevouwen, en meer.

[DisplayError-Element (indeling)](./displayerror-element-format.md) geeft aan dat de tekenreeks #ERR wordt weergegeven wanneer er treedt een fout op bij het weergeven van een hoeveelheid gegevens.

[EntrySelectedBy-Element voor CustomEntry voor besturingselementen voor de configuratie (-indeling)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md) definieert de .NET-typen die gebruikmaken van de definitie van de algemene controle of de voorwaarde die moet bestaan voor dit besturingselement moet worden gebruikt. Dit element wordt gebruikt bij het definiëren van een algemene besturingselement dat kan worden gebruikt door alle weergaven in de opmaak-bestand.

[EntrySelectedBy-Element voor CustomEntry voor besturingselementen voor weergave (indeling)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md) definieert de .NET-typen die gebruikmaken van de besturingselementdefinitie van dit of de voorwaarde die moet bestaan voor deze definitie moet worden gebruikt. Dit element wordt gebruikt bij het definiëren van besturingselementen die kunnen worden gebruikt door een weergave.

[EntrySelectedBy-Element voor CustomEntry voor weergave (indeling)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md) definieert de .NET-typen die gebruikmaken van deze aangepaste vermelding of de voorwaarde die moet aanwezig zijn voor dit item moet worden gebruikt.

[EntrySelectedBy-Element voor EnumerableExpansion (indeling)](./entryselectedby-element-for-enumerableexpansion-format.md) definieert de .NET-typen die gebruikmaken van deze definitie of de voorwaarde die moet bestaan voor deze definitie moet worden gebruikt.

[EntrySelectedBy-Element voor CustomEntry voor GroupBy (indeling)](./entryselectedby-element-for-customentry-for-groupby-format.md) definieert de .NET-typen die gebruikmaken van de besturingselementdefinitie van dit of de voorwaarde die moet bestaan voor deze definitie moet worden gebruikt. Dit element wordt gebruikt bij het definiëren van hoe een nieuwe groep objecten worden weergegeven.

[EntrySelectedBy-Element voor ListEntry voor ListControl (indeling)](./entryselectedby-element-for-listentry-for-listcontrol-format.md) definieert de .NET-typen die gebruikmaken van de definitie van deze lijst weergeven of de voorwaarde die moet bestaan voor deze definitie moet worden gebruikt. In de meeste gevallen is slechts één definitie nodig voor een lijst weergeven. U kunt echter meerdere definities voor de lijstweergave opgeven als u wilt de dezelfde lijstweergave gebruiken om verschillende gegevens voor verschillende objecten weer te geven.

[EntrySelectedBy-Element voor TableRowEntry (indeling)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) definieert de .NET-typen waarvan de de eigenschapwaarden worden weergegeven in de rij.

[EntrySelectedBy-Element voor WideEntry (indeling)](./entryselectedby-element-for-wideentry-format.md) definieert de .NET-typen die gebruikmaken van deze definitie van de brede weergave of de voorwaarde die moet bestaan voor deze definitie moet worden gebruikt.

[EnumerableExpansion-Element (indeling)](./enumerableexpansion-element-format.md) definieert hoe specifieke .NET-verzameling objecten worden uitgevouwen wanneer ze worden weergegeven in een weergave.

[EnumerableExpansions-Element (indeling)](./enumerableexpansions-element-format.md) definieert hoe .NET-verzameling objecten worden uitgevouwen wanneer ze worden weergegeven in een weergave.

[EnumerateCollection-Element voor ExpressionBinding voor besturingselementen voor de configuratie (-indeling)](./enumeratecollection-element-for-expressionbinding-for-controls-for-configuration-format.md) opgegeven dat de elementen van verzamelingen worden weergegeven door het besturingselement. Dit element wordt gebruikt bij het definiëren van een algemene besturingselement dat kan worden gebruikt door alle weergaven in de opmaak-bestand.

[EnumerateCollection-Element voor ExpressionBinding voor besturingselementen voor weergave (indeling)](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md) opgegeven dat de elementen van verzamelingen worden weergegeven. Dit element wordt gebruikt bij het definiëren van besturingselementen die kunnen worden gebruikt door een weergave.

[EnumerateCollection-Element voor het binden van de expressie voor CustomControl voor weergave (indeling)](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md) geeft aan dat de elementen van verzamelingen worden weergegeven. Dit element wordt gebruikt bij het definiëren van een aangepast besturingselement-weergave.

[EnumerateCollection-Element voor ExpressionBinding voor GroupBy (indeling)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md) geeft aan dat de elementen van verzamelingen worden weergegeven. Dit element wordt gebruikt bij het definiëren van hoe een nieuwe groep objecten worden weergegeven.

[Vouw Element (indeling)](./expand-element-format.md) geeft aan hoe het verzamelingsobject voor deze definitie is uitgevouwen.

[ExpressionBinding-Element voor CustomItem voor besturingselementen voor de configuratie (-indeling)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md) definieert de gegevens die door het besturingselement wordt weergegeven. Dit element wordt gebruikt bij het definiëren van een algemene besturingselement dat kan worden gebruikt door alle weergaven in de opmaak-bestand.

[ExpressionBinding-Element voor CustomItem voor besturingselementen voor weergave (indeling)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md) definieert de gegevens die door het besturingselement wordt weergegeven. Dit element wordt gebruikt bij het definiëren van besturingselementen die kunnen worden gebruikt door een weergave.

[ExpressionBinding-Element voor CustomItem voor CustomControl voor weergave (indeling)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md) definieert de gegevens die door het besturingselement wordt weergegeven. Dit element wordt gebruikt bij het definiëren van een aangepast besturingselement-weergave.

[ExpressionBinding-Element voor CustomItem voor GroupBy (indeling)](./expressionbinding-element-for-customitem-for-groupby-format.md) definieert de gegevens die door het besturingselement wordt weergegeven. Dit element wordt gebruikt bij het definiëren van hoe een nieuwe groep objecten worden weergegeven.

[FirstLineHanging-Element voor kader voor controles voor configuratie (-indeling)](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) geeft aan hoeveel tekens de eerste regel van gegevens is verplaatst naar de linkerkant. Dit element wordt gebruikt bij het definiëren van een algemene besturingselement dat kan worden gebruikt door alle weergaven in de opmaak-bestand.

[FirstLineHanging-Element van het kader van de besturingselementen van weergave (indeling)](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) geeft aan hoeveel tekens de eerste regel van gegevens is verplaatst naar de linkerkant. Dit element wordt gebruikt bij het definiëren van besturingselementen die kunnen worden gebruikt door een weergave.

[FirstLineHanging-Element voor Frame voor CustomControl voor weergave (indeling)](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) geeft aan hoeveel tekens de eerste regel van gegevens is verplaatst naar de linkerkant. Dit element wordt gebruikt bij het definiëren van een aangepast besturingselement-weergave.

[FirstLineHanging-Element voor Frame voor GroupBy (indeling)](./firstlinehanging-element-for-frame-for-groupby-format.md) geeft aan hoeveel tekens de eerste regel van gegevens is verplaatst naar de linkerkant. Dit element wordt gebruikt bij het definiëren van hoe een nieuwe groep objecten worden weergegeven.

[FirstLineIndent-Element voor kader voor controles voor configuratie (-indeling)](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) geeft aan hoeveel tekens de eerste regel van gegevens is verplaatst naar de rechterkant. Dit element wordt gebruikt bij het definiëren van een algemene besturingselement dat kan worden gebruikt door alle weergaven in de opmaak-bestand.

[FirstLineIndent Element van het kader van de besturingselementen van weergave (indeling)](./firstlineindent-element-for-frame-for-controls-for-view-format.md) geeft aan hoeveel tekens de eerste regel van gegevens is verplaatst naar de rechterkant. Dit element wordt gebruikt bij het definiëren van besturingselementen die kunnen worden gebruikt door een weergave.

[FirstLineIndent Element](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) geeft aan hoeveel tekens de eerste regel van gegevens is verplaatst naar de rechterkant. Dit element wordt gebruikt bij het definiëren van een aangepast besturingselement-weergave.

[FirstLineIndent-Element voor Frame voor GroupBy (indeling)](./firstlineindent-element-for-frame-for-groupby-format.md) geeft aan hoeveel tekens de eerste regel van gegevens is verplaatst naar de rechterkant. Dit element wordt gebruikt bij het definiëren van hoe een nieuwe groep objecten worden weergegeven.

[FormatString-Element voor ListItem (indeling)](./formatstring-element-for-listitem-for-listcontrol-format.md) Hiermee geeft u een indeling patroon waarmee wordt gedefinieerd hoe de waarde voor eigenschap of het script wordt weergegeven.

[FormatString-Element voor TableColumnItem (indeling)](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md) Hiermee geeft u een indeling patroon waarmee wordt gedefinieerd hoe de waarde voor eigenschap of het script van de tabel wordt weergegeven.

[FormatString-Element voor WideItem voor WideControl (indeling)](./formatstring-element-for-wideitem-for-widecontrol-format.md) Hiermee geeft u een indeling patroon waarmee wordt gedefinieerd hoe de waarde voor eigenschap of het script wordt weergegeven in de weergave.

[Frame-Element voor CustomItem voor besturingselementen voor de configuratie (-indeling)](./frame-element-for-customitem-for-controls-for-configuration-format.md) definieert hoe de gegevens worden weergegeven, zoals de gegevens verschuiving naar links of rechts. Dit element wordt gebruikt bij het definiëren van een algemene besturingselement dat kan worden gebruikt door alle weergaven in de opmaak-bestand.

[Frame-Element voor CustomItem voor besturingselementen voor weergave (indeling)](./frame-element-for-customitem-for-controls-for-view-format.md) definieert hoe de gegevens worden weergegeven, zoals de gegevens verschuiving naar links of rechts. Dit element wordt gebruikt bij het definiëren van besturingselementen die kunnen worden gebruikt door een weergave.

[Frame-Element voor CustomItem voor CustomControl voor weergave (indeling)](./frame-element-for-customitem-for-customcontrol-for-view-format.md) definieert hoe de gegevens worden weergegeven, zoals de gegevens verschuiving naar links of rechts. Dit element wordt gebruikt bij het definiëren van een aangepast besturingselement-weergave.

[Frame-Element voor CustomItem voor GroupBy (indeling)](./frame-element-for-customitem-for-groupby-format.md) definieert hoe de gegevens worden weergegeven, zoals de gegevens verschuiving naar links of rechts. Dit element wordt gebruikt bij het definiëren van hoe een nieuwe groep objecten worden weergegeven.

[GroupBy-Element voor weergave (indeling)](./groupby-element-for-view-format.md) definieert hoe een nieuwe groep objecten worden weergegeven in Windows PowerShell.

[HideTableHeaders-Element (indeling)](./hidetableheaders-element-format.md) Hiermee geeft u de headers van de tabel worden niet weergegeven.

[ItemSelectionCondition-Element voor ExpressionBinding voor besturingselementen voor de configuratie (-indeling)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md) definieert de voorwaarde die moet bestaan voor dit besturingselement moet worden gebruikt. Dit element wordt gebruikt bij het definiëren van een algemene besturingselement dat kan worden gebruikt door alle weergaven in de opmaak-bestand.

[ItemSelectionCondition-Element van ExpressionBinding voor besturingselementen voor weergave (indeling)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md) definieert de voorwaarde die moet bestaan voor dit besturingselement moet worden gebruikt. Dit element wordt gebruikt bij het definiëren van besturingselementen die kunnen worden gebruikt door een weergave.

[ItemSelectionCondition-Element voor het binden van de expressie voor CustomControl voor weergave (indeling)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md) definieert de voorwaarde die moet bestaan voor dit besturingselement moet worden gebruikt. Er is geen limiet voor het aantal selectie voorwaarden die kan worden opgegeven voor een controle-item. Dit element wordt gebruikt bij het definiëren van een aangepast besturingselement-weergave.

[ItemSelectionCondition-Element voor ExpressionBinding voor GroupBy (indeling)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md) definieert de voorwaarde die moet bestaan voor dit besturingselement moet worden gebruikt. Er is geen limiet voor het aantal selectie voorwaarden die kan worden opgegeven voor een controle-item. Dit element wordt gebruikt bij het definiëren van hoe een nieuwe groep objecten worden weergegeven.

[ItemSelectionCondition-Element voor ListItem (indeling)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md) definieert de voorwaarde die moet bestaan voor dit item in de lijst moet worden gebruikt.

[Element een label voor ListItem voor ListControl(Format)](./label-element-for-listitem-for-listcontrol-format.md) Hiermee geeft u het label voor de waarde voor eigenschap of het script in de rij.

[Element een label voor GroupBy (indeling)](./label-element-for-groupby-format.md) Hiermee geeft u een label dat wordt weergegeven wanneer een nieuwe groep is opgetreden.

[Element een label voor TableColumnHeader (indeling)](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) definieert het label dat wordt weergegeven aan de bovenkant van een kolom.

[LeftIndent-Element voor kader voor controles voor configuratie (-indeling)](./leftindent-element-for-frame-for-controls-for-configuration-format.md) geeft aan hoeveel tekens de gegevens van de linkermarge is verplaatst. Dit element wordt gebruikt bij het definiëren van een algemene besturingselement dat kan worden gebruikt door alle weergaven in de opmaak-bestand.

[LeftIndent Element van het kader van de besturingselementen van weergave (indeling)](./leftindent-element-for-frame-for-controls-for-view-format.md) geeft aan hoeveel tekens de gegevens van de linkermarge is verplaatst. Dit element wordt gebruikt bij het definiëren van besturingselementen die kunnen worden gebruikt door een weergave.

[LeftIndent-Element voor Frame voor CustomControl voor weergave (indeling)](./leftindent-element-for-frame-for-customcontrol-for-view-format.md) geeft aan hoeveel tekens de gegevens van de linkermarge is verplaatst. Dit element wordt gebruikt bij het definiëren van een aangepast besturingselement-weergave.

[LeftIndent-Element voor Frame voor GroupBy (indeling)](./leftindent-element-for-frame-for-groupby-format.md) geeft aan hoeveel tekens de gegevens van de linkermarge is verplaatst. Dit element wordt gebruikt bij het definiëren van hoe een nieuwe groep objecten worden weergegeven.

[ListControl Element (indeling)](./listcontrol-element-format.md) definieert een lijst met indeling voor de weergave.

[ListEntry-Element (indeling)](./listentry-element-for-listcontrol-format.md) biedt een definitie van de lijstweergave.

[ListEntries-Element (indeling)](./listentries-element-for-listcontrol-format.md) definieert hoe de rijen van de lijstweergave worden weergegeven.

[Lijstitem-Element (indeling)](./listitem-element-for-listitems-for-listcontrol-format.md) definieert de eigenschap of het script waarvan de waarde wordt weergegeven in een rij in de lijstweergave.

[ListItems Element (indeling)](./listitems-element-for-listentry-for-listcontrol-format.md) definieert de eigenschappen en scripts die worden weergegeven in de lijstweergave.

[Element een naam voor het besturingselement voor besturingselementen voor de configuratie (-indeling)](./name-element-for-control-for-controls-for-configuration-format.md) Hiermee geeft u de naam van het besturingselement. Dit element wordt gebruikt bij het definiëren van een algemene besturingselement dat kan worden gebruikt door alle weergaven in de opmaak-bestand.

[Naam van Element voor SelectionSet (indeling)](./name-element-for-selectionset-format.md) Hiermee geeft u de naam die wordt gebruikt om te verwijzen naar de selectieset.

[Naam van Element voor weergave (indeling)](./name-element-for-view-format.md) Hiermee geeft u de naam die wordt gebruikt voor het identificeren van de weergave.

[Nieuwe regel-Element voor CustomItem voor besturingselementen voor de configuratie (-indeling)](./newline-element-for-customitem-for-controls-for-configuration-format.md) voegt een lege regel toe aan de weergave van het besturingselement. Dit element wordt gebruikt bij het definiëren van een algemene besturingselement dat kan worden gebruikt door alle weergaven in de opmaak-bestand.

[Nieuwe regel-Element voor CustomItem voor besturingselementen voor weergave (indeling)](./newline-element-for-customitem-for-controls-for-view-format.md) voegt een lege regel toe aan de weergave van het besturingselement. Dit element wordt gebruikt bij het definiëren van besturingselementen die kunnen worden gebruikt door een weergave.

[Nieuwe regel-Element voor CustomItem voor CustomControl voor weergave (indeling)](./newline-element-for-customitem-for-customcontrol-for-view-format.md) voegt een lege regel toe aan de weergave van het besturingselement. Dit element wordt gebruikt bij het definiëren van een aangepast besturingselement-weergave.

[Nieuwe regel-Element voor CustomItem voor GroupBy (indeling)](./newline-element-for-customitem-for-groupby-format.md) voegt een lege regel toe aan de weergave van het besturingselement. Dit element wordt gebruikt bij het definiëren van hoe een nieuwe groep objecten worden weergegeven.

[PropertyName-Element voor ExpressionBinding voor besturingselementen voor de configuratie (-indeling)](./propertyname-element-for-expressionbinding-for-controls-for-configuration-format.md) Hiermee geeft u de .NET-eigenschap waarvan de waarde van het algemene besturingselement wordt weergegeven. Dit element wordt gebruikt bij het definiëren van een algemene besturingselement dat kan worden gebruikt door alle weergaven in de opmaak-bestand.

[PropertyName-Element voor ExpressionBinding voor besturingselementen voor weergave (indeling)](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md) Hiermee geeft u de .NET-eigenschap waarvan de waarde van het besturingselement wordt weergegeven. Dit element wordt gebruikt bij het definiëren van besturingselementen die kunnen worden gebruikt door een weergave.

[PropertyName-Element voor ExpressionBinding voor CustomControl voor weergave (indeling)](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md) Hiermee geeft u de .NET-eigenschap waarvan de waarde van het besturingselement wordt weergegeven. Dit element wordt gebruikt bij het definiëren van een aangepast besturingselement weergeven

[PropertyName-Element voor ExpressionBinding voor GroupBy (indeling)](./propertyname-element-for-expressionbinding-for-groupby-format.md) Hiermee geeft u de .NET-eigenschap waarvan de waarde van het besturingselement wordt weergegeven. Dit element wordt gebruikt bij het definiëren van hoe een nieuwe groep objecten worden weergegeven.

[PropertyName-Element voor GroupBy (indeling)](./propertyname-element-for-groupby-format.md) Hiermee geeft u de .NET-eigenschap die een nieuwe groep wordt gestart wanneer de waarde ervan verandert.

[PropertyName-Element voor ItemSeclectionCondition voor besturingselementen voor de configuratie (-indeling)](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) Hiermee geeft u de .NET-eigenschap die de voorwaarde wordt geactiveerd. Als deze eigenschap is aanwezig, of wanneer deze wordt geëvalueerd naar `true`, de voorwaarde wordt voldaan, en wordt het besturingselement gebruikt. Dit element wordt gebruikt bij het definiëren van een algemene besturingselement dat kan worden gebruikt door alle weergaven in de opmaak-bestand.

[PropertyName-Element voor ItemSelectionCondition voor besturingselementen voor weergave (indeling)](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md) Hiermee geeft u de .NET-eigenschap die de voorwaarde wordt geactiveerd. Als deze eigenschap is aanwezig, of wanneer deze wordt geëvalueerd naar `true`, de voorwaarde wordt voldaan, en wordt het besturingselement gebruikt. Dit element wordt gebruikt bij het definiëren van besturingselementen die kunnen worden gebruikt door een weergave.

[PropertyName-Element voor ItemSelectionCondition voor CustomControl voor weergave (indeling](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) Hiermee geeft u de .NET-eigenschap die de voorwaarde wordt geactiveerd. Als deze eigenschap is aanwezig, of wanneer deze wordt geëvalueerd naar `true`, de voorwaarde wordt voldaan, en wordt het besturingselement gebruikt. Dit element wordt gebruikt bij het definiëren van een aangepast besturingselement-weergave.

[PropertyName-Element voor ItemSelectionCondition voor GroupBy (indeling)](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) Hiermee geeft u de .NET-eigenschap die de voorwaarde wordt geactiveerd. Als deze eigenschap is aanwezig, of wanneer deze wordt geëvalueerd naar `true`, de voorwaarde wordt voldaan, en wordt het besturingselement gebruikt. Dit element wordt gebruikt bij het definiëren van hoe een nieuwe groep objecten worden weergegeven.

[PropertyName-Element voor ItemSelectionCondition voor ListItem (indeling)](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md) Hiermee geeft u de .NET-eigenschap die de voorwaarde wordt geactiveerd. Als deze eigenschap is aanwezig, of wanneer deze wordt geëvalueerd naar `true`, de voorwaarde wordt voldaan en de weergave wordt gebruikt. Dit element wordt gebruikt bij het definiëren van een lijst weergeven.

[PropertyName-Element voor ListItem voor ListControl (indeling)](./propertyname-element-for-listitem-for-listcontrol-format.md) Hiermee geeft u de .NET-eigenschap waarvan de waarde wordt weergegeven in de lijst.

[PropertyName-Element voor SelectionCondition voor EntrySelectedBy voor ListEntry (indeling)](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md) Hiermee geeft u de .NET-eigenschap die de voorwaarde wordt geactiveerd. Als deze eigenschap is aanwezig, of wanneer deze wordt geëvalueerd naar `true`, de voorwaarde wordt voldaan en de vermelding wordt gebruikt. Dit element wordt gebruikt bij het definiëren van een algemene besturingselement dat kan worden gebruikt door alle weergaven in de opmaak-bestand.

[PropertyName-Element voor SelectionCondition voor besturingselementen voor weergave (indeling)](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md) Hiermee geeft u de .NET-eigenschap die de voorwaarde wordt geactiveerd. Als deze eigenschap is aanwezig, of wanneer deze wordt geëvalueerd naar `true`, de voorwaarde wordt voldaan en de vermelding wordt gebruikt. Dit element wordt gebruikt bij het definiëren van besturingselementen die kunnen worden gebruikt door een weergave.

[PropertyName-Element voor SelectionCondition voor CustomControl voor weergave (indeling)](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md) Hiermee geeft u de .NET-eigenschap die de voorwaarde wordt geactiveerd. Als deze eigenschap is aanwezig, of wanneer deze wordt geëvalueerd naar `true`, de voorwaarde wordt voldaan en de definitie wordt gebruikt. Dit element wordt gebruikt bij het definiëren van een aangepast besturingselement-weergave.

[PropertyName-Element voor SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (indeling)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md) Hiermee geeft u de .NET-eigenschap die de voorwaarde wordt geactiveerd. Als deze eigenschap is aanwezig, of wanneer deze wordt geëvalueerd naar `true`, de voorwaarde wordt voldaan en de definitie wordt gebruikt.

[PropertyName-Element voor SelectionCondition voor GroupBy (indeling)](./propertyname-element-for-selectioncondition-for-groupby-format.md) Hiermee geeft u de .NET-eigenschap die de voorwaarde wordt geactiveerd. Als deze eigenschap is aanwezig, of wanneer deze wordt geëvalueerd naar `true`, de voorwaarde wordt voldaan en de definitie wordt gebruikt. Dit element wordt gebruikt bij het definiëren van hoe een nieuwe groep objecten worden weergegeven.

[PropertyName-Element voor SelectionCondition voor EntrySelectedBy voor ListEntry (indeling)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md) Hiermee geeft u de .NET-eigenschap die de voorwaarde wordt geactiveerd. Als deze eigenschap is aanwezig, of wanneer deze wordt geëvalueerd naar `true`, de voorwaarde wordt voldaan en vermelding in de lijst wordt gebruikt.

[PropertyName-Element voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (indeling)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md) Hiermee geeft u de .NET-eigenschap die de voorwaarde wordt geactiveerd. Als deze eigenschap is aanwezig, of wanneer deze wordt geëvalueerd naar `true`, de voorwaarde wordt voldaan en de vermelding in de tabel wordt gebruikt.

[PropertyName-Element voor SelectionCondition voor EntrySelectedBy voor WideEntry (indeling)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md) Hiermee geeft u de .NET-eigenschap die de voorwaarde wordt geactiveerd. Als deze eigenschap is aanwezig, of wanneer deze wordt geëvalueerd naar `true`, de voorwaarde wordt voldaan en de definitie wordt gebruikt.

[PropertyName-Element voor TableColumnItem (indeling)](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) Hiermee geeft u de eigenschap waarvan de waarde wordt weergegeven in de kolom van de rij.

[PropertyName-Element voor WideItem (indeling)](./propertyname-element-for-wideitem-for-widecontrol-format.md) Hiermee geeft u de eigenschap van het object waarvan de waarde wordt weergegeven in de brede weergave.

[RightIndent-Element voor kader voor controles voor configuratie (-indeling)](./rightindent-element-for-frame-for-controls-for-configuration-format.md) geeft aan hoeveel tekens de gegevens van de rechtermarge is verplaatst. Dit element wordt gebruikt bij het definiëren van een algemene besturingselement dat kan worden gebruikt door alle weergaven in de opmaak-bestand.

[RightIndent Element van het kader van de besturingselementen van weergave (indeling)](./rightindent-element-for-frame-for-controls-for-view-format.md) geeft aan hoeveel tekens de gegevens van de rechtermarge is verplaatst. Dit element wordt gebruikt bij het definiëren van besturingselementen die kunnen worden gebruikt door een weergave.

[RightIndent Element](./rightindent-element-for-frame-for-customcontrol-for-view-format.md) geeft aan hoeveel tekens de gegevens van de rechtermarge is verplaatst. Dit element wordt gebruikt bij het definiëren van een aangepast besturingselement-weergave.

[RightIndent-Element voor Frame voor GroupBy (indeling)](./rightindent-element-for-frame-for-groupby-format.md) geeft aan hoeveel tekens de gegevens van de rechtermarge is verplaatst. Dit element wordt gebruikt bij het definiëren van hoe een nieuwe groep objecten worden weergegeven.

[ScriptBlock-Element voor ExpressionBinding voor besturingselementen voor de configuratie (-indeling)](./scriptblock-element-for-expressionbinding-for-controls-for-configuration-format.md) Hiermee geeft u het script waarvan de waarde van het algemene besturingselement wordt weergegeven. Dit element wordt gebruikt bij het definiëren van een algemene besturingselement dat kan worden gebruikt door alle weergaven in de opmaak-bestand.

[ScriptBlock-Element voor ExpressionBinding voor besturingselementen voor weergave (indeling)](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md) Hiermee geeft u het script waarvan de waarde van het besturingselement wordt weergegeven. Dit element wordt gebruikt bij het definiëren van besturingselementen die kunnen worden gebruikt door een weergave.

[ScriptBlock-Element voor ExpressionBinding voor CustomCustomControl voor weergave (indeling)](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md) Hiermee geeft u het script waarvan de waarde van het besturingselement wordt weergegeven. Dit element wordt gebruikt bij het definiëren van een aangepast besturingselement-weergave.

[ScriptBlock-Element voor ExpressionBinding voor GroupBy (indeling)](./scriptblock-element-for-expressionbinding-for-groupby-format.md) Hiermee geeft u het script waarvan de waarde van het besturingselement wordt weergegeven. Dit element wordt gebruikt bij het definiëren van hoe een nieuwe groep objecten worden weergegeven.

[ScriptBlock-Element voor GroupBy (indeling)](./scriptblock-element-for-groupby-format.md) Hiermee geeft u het script dat een nieuwe groep wordt gestart wanneer de waarde ervan verandert.

[ScriptBlock-Element voor ItemSelectionCondition voor besturingselementen voor de configuratie (-indeling)](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) Hiermee geeft u het script dat de voorwaarde wordt geactiveerd. Wanneer dit script wordt geëvalueerd naar `true`, de voorwaarde wordt voldaan, en wordt het besturingselement gebruikt. Dit element wordt gebruikt bij het definiëren van een algemene besturingselement dat kan worden gebruikt door alle weergaven in de opmaak-bestand.

[ScriptBlock-Element voor ItemSelectionCondition voor besturingselementen voor weergave (indeling)](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md) Hiermee geeft u het script dat de voorwaarde wordt geactiveerd. Wanneer dit script wordt geëvalueerd naar `true`, de voorwaarde wordt voldaan, en wordt het besturingselement gebruikt. Dit element wordt gebruikt bij het definiëren van besturingselementen die kunnen worden gebruikt door een weergave.

[ScriptBlock-Element voor ItemSelectionCondition voor CustomControl voor weergave (indeling)](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) Hiermee geeft u het script dat de voorwaarde wordt geactiveerd. Wanneer dit script wordt geëvalueerd naar `true`, de voorwaarde wordt voldaan, en wordt het besturingselement gebruikt. Dit element wordt gebruikt bij het definiëren van een aangepast besturingselement-weergave.

[ScriptBlock-Element voor ItemSelectionCondition voor GroupBy (indeling)](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md) Hiermee geeft u het script dat de voorwaarde wordt geactiveerd. Wanneer dit script wordt geëvalueerd naar `true`, de voorwaarde wordt voldaan, en wordt het besturingselement gebruikt. Dit element wordt gebruikt bij het definiëren van hoe een nieuwe groep objecten worden weergegeven.

[ScriptBlock-Element voor ItemSelectionCondition voor ListControl (indeling)](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) Hiermee geeft u het script dat de voorwaarde wordt geactiveerd. Wanneer dit script wordt geëvalueerd naar `true`, de voorwaarde wordt voldaan en dat het item wordt gebruikt. Dit element wordt gebruikt bij het definiëren van een lijst weergeven.

[ScriptBlock-Element voor ListItem (indeling)](./scriptblock-element-for-listitem-for-listcontrol-format.md) Hiermee geeft u het script waarvan de waarde wordt weergegeven in de rij van de lijst.

[ScriptBlock-Element voor SelectionCondition voor besturingselementen voor de configuratie (-indeling)](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md) Hiermee geeft u het script dat de voorwaarde wordt geactiveerd. Wanneer dit script wordt geëvalueerd naar `true`, de voorwaarde wordt voldaan en de definitie wordt gebruikt. Dit element wordt gebruikt bij het definiëren van een algemene besturingselement dat kan worden gebruikt door alle weergaven in de opmaak-bestand.

[ScriptBlock-Element voor SelectionCondition voor besturingselementen voor weergave (indeling)](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md) Hiermee geeft u het script dat de voorwaarde wordt geactiveerd. Wanneer dit script wordt geëvalueerd naar `true`, de voorwaarde wordt voldaan en de definitie wordt gebruikt. Dit element wordt gebruikt bij het definiëren van besturingselementen die kunnen worden gebruikt door een weergave.

[ScriptBlock-Element voor SelectionCondition voor CustomControl voor weergave (indeling)](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md) Hiermee geeft u het script dat de voorwaarde wordt geactiveerd. Wanneer dit script wordt geëvalueerd naar `true`, de voorwaarde wordt voldaan en de definitie wordt gebruikt. Dit element wordt gebruikt bij het definiëren van een aangepast besturingselement-weergave.

[ScriptBlock-Element voor SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (indeling)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md) Hiermee geeft u het script dat de voorwaarde wordt geactiveerd.

[ScriptBlock-Element voor SelectionCondition voor GroupBy (indeling)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format.md) Hiermee geeft u het script dat de voorwaarde wordt geactiveerd. Wanneer dit script wordt geëvalueerd naar `true`, de voorwaarde wordt voldaan en de definitie wordt gebruikt. Dit element wordt gebruikt bij het definiëren van hoe een nieuwe groep objecten worden weergegeven.

[ScriptBlock-Element voor SelectionCondition voor EntrySelectedBy voor ListEntry (indeling)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md) Hiermee geeft u het script dat de voorwaarde wordt geactiveerd. Wanneer dit script wordt geëvalueerd naar `true`, de voorwaarde wordt voldaan en vermelding in de lijst wordt gebruikt.

[ScriptBlock-Element voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (indeling)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md) Hiermee geeft u het scriptblok waarmee de voorwaarde wordt geactiveerd. Wanneer dit script wordt geëvalueerd naar `true`, de voorwaarde wordt voldaan en de vermelding in de tabel wordt gebruikt.

[ScriptBlock-Element voor SelectionCondition voor EntrySelectedBy voor WideEntry (indeling)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md) Hiermee geeft u het script dat de voorwaarde wordt geactiveerd. Wanneer dit script wordt geëvalueerd naar `true`, de voorwaarde wordt voldaan en de definitie van de brede vermelding wordt gebruikt.

[ScriptBlock-Element voor TableColumnItem (indeling)](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) Hiermee geeft u het script waarvan de waarde wordt weergegeven in de kolom van de rij.

[ScriptBlock-Element voor WideItem (indeling)](./scriptblock-element-for-wideitem-for-widecontrol-format.md) Hiermee geeft u het script waarvan de waarde wordt weergegeven in de brede weergave.

[SelectionCondition-Element voor EntrySelectedBy voor CustomEntry voor configuratie (-indeling)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md) definieert een voorwaarde die moet aanwezig zijn voor de besturingselementdefinitie van een algemene moet worden gebruikt. Dit element wordt gebruikt bij het definiëren van een algemene besturingselement dat kan worden gebruikt door alle weergaven in de opmaak-bestand.

[SelectionCondition-Element voor EntrySelectedBy voor besturingselementen voor weergave (indeling)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md) definieert een voorwaarde die moet aanwezig zijn voor de besturingselementdefinitie van het moet worden gebruikt. Dit element wordt gebruikt bij het definiëren van besturingselementen die kunnen worden gebruikt door een weergave.

[SelectionCondition-Element voor EntrySelectedBy voor CustomControl voor weergave (indeling)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md) definieert een voorwaarde die moet aanwezig zijn voor de besturingselementdefinitie van een moet worden gebruikt. Dit element wordt gebruikt bij het definiëren van een aangepast besturingselement-weergave.

[SelectionCondition-Element voor EntrySelectedBy voor EnumerableExpansion (indeling)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md) de voorwaarde die moet aanwezig zijn om uit te breiden, de verzameling objecten van deze definitie wordt gedefinieerd.

[SelectionCondition-Element voor EntrySelectedBy voor GroupBy (indeling)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md) definieert een voorwaarde die moet aanwezig zijn voor de besturingselementdefinitie van een moet worden gebruikt. Dit element wordt gebruikt bij het definiëren van hoe een nieuwe groep objecten worden weergegeven.

[SelectionCondition-Element voor EntrySelectedBy voor ListEntry (indeling)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) definieert de voorwaarde die moet bestaan voor het gebruik van deze definitie van de lijstweergave. Er is geen limiet voor het aantal selectie voorwaarden die kan worden opgegeven voor de Lijstdefinitie van een.

[SelectionCondition-Element voor EntrySelectedBy voor TableRowEntry (indeling)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md) definieert de voorwaarde die moet aanwezig zijn als u wilt gebruiken voor deze definitie van de tabelweergave. Er is geen limiet voor het aantal selectie voorwaarden die kan worden opgegeven voor de tabeldefinitie van een.

[SelectionCondition-Element voor EntrySelectedBy voor WideEntry (indeling)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) definieert de voorwaarde die moet bestaan voor deze definitie moet worden gebruikt. Er is geen limiet voor het aantal selectie voorwaarden die kan worden opgegeven voor de definitie van een breed vermelding.

[SelectionSet-Element (indeling)](./selectionset-element-format.md) definieert een set van .NET-objecten die kan worden verwezen door de naam van de set.

[SelectionSetName-Element voor EntrySelectedBy voor besturingselementen voor de configuratie (-indeling)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md) geeft een reeks van .NET-typen die gebruikmaken van deze definitie van het besturingselement. Dit element wordt gebruikt bij het definiëren van een algemene besturingselement dat kan worden gebruikt door alle weergaven in de opmaak-bestand.

[SelectionSetName-Element voor EntrySelectedBy voor besturingselementen voor weergave (indeling)](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md) geeft een reeks van .NET-typen die gebruikmaken van deze definitie van het besturingselement. Dit element wordt gebruikt bij het definiëren van besturingselementen die kunnen worden gebruikt door een weergave.

[SelectionSetName-Element voor EntrySelectedBy voor CustomEntry (indeling)](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md) geeft een reeks van .NET-objecten voor de vermelding in de lijst. Er is geen limiet voor het aantal selectiesets die kan worden opgegeven voor een vermelding.

[SelectionSetName-Element voor EntrySelectedBy voor EnumerableExpansion (indeling)](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md) geeft de set van .NET-typen die door deze definitie zijn uitgebreid.

[SelectionSetName-Element voor EntrySelectedBy voor GroupBy (indeling)](./selectionsetname-element-for-entryselectedby-for-groupby-format.md) geeft een reeks van .NET-objecten voor de vermelding in de lijst. Er is geen limiet voor het aantal selectiesets die kan worden opgegeven voor een vermelding. Dit element wordt gebruikt bij het definiëren van hoe een nieuwe groep objecten worden weergegeven.

[SelectionSetName-Element voor EntrySelectedBy voor ListEntry (indeling)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) geeft een reeks van .NET-objecten voor de vermelding in de lijst. Er is geen limiet voor het aantal selectiesets die kan worden opgegeven voor een vermelding.

[SelectionSetName-Element voor EntrySelectedBy voor TableRowEntry (indeling)](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md) Hiermee geeft u een set met .NET typen het gebruik van deze vermelding van de tabelweergave. Er is geen limiet voor het aantal selectiesets die kan worden opgegeven voor een vermelding.

[SelectionSetName-Element voor EntrySelectedBy voor WideEntry (indeling)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md) geeft een reeks van .NET-objecten voor de definitie. De definitie wordt gebruikt als een van deze objecten wordt weergegeven.

[SelectionSetName-Element voor SelectionCondition voor besturingselementen voor de configuratie (-indeling)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md) geeft de set van .NET-typen waarvoor de voorwaarde is geactiveerd. Wanneer een van de typen in deze set aanwezig zijn, de voorwaarde wordt voldaan en het object met behulp van dit besturingselement wordt weergegeven. Dit element wordt gebruikt bij het definiëren van een algemene besturingselement dat kan worden gebruikt door alle weergaven in de opmaak-bestand.

[SelectionSetName-Element voor SelectionCondition voor besturingselementen voor weergave (indeling)](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md) geeft de set van .NET-typen waarvoor de voorwaarde is geactiveerd. Wanneer een van de typen in deze set aanwezig zijn, de voorwaarde wordt voldaan en het object wordt weergegeven met behulp van dit besturingselement. Dit element wordt gebruikt bij het definiëren van besturingselementen die kunnen worden gebruikt door een weergave.

[EntrySelectedBy-Element voor CustomEntry voor weergave (indeling)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md) geeft de set van .NET-typen waarvoor de voorwaarde is geactiveerd. Wanneer een van de typen in deze set aanwezig zijn, de voorwaarde wordt voldaan en het object wordt weergegeven met behulp van dit besturingselement. Dit element wordt gebruikt bij het definiëren van een aangepast besturingselement-weergave.

[SelectionSetName-Element voor SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (indeling)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md) geeft de set van .NET-typen waarvoor de voorwaarde is geactiveerd. Wanneer een van de typen in deze set aanwezig zijn, wordt de voorwaarde wordt voldaan.

[SelectionSetName-Element voor SelectionCondition voor GroupBy (indeling)](./selectionsetname-element-for-selectioncondition-for-groupby-format.md) geeft de set van .NET-typen waarvoor de voorwaarde is geactiveerd. Wanneer een van de typen in deze set aanwezig zijn, de voorwaarde wordt voldaan en het object met behulp van dit besturingselement wordt weergegeven. Dit element wordt gebruikt bij het definiëren van hoe een nieuwe groep objecten worden weergegeven.

[SelectionSetName-Element voor SelectionCondition voor EntrySelectedBy voor ListEntry (indeling)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md) geeft de set van .NET-typen waarvoor de voorwaarde is geactiveerd. Wanneer een van de typen in deze set aanwezig zijn, de voorwaarde wordt voldaan en het object wordt weergegeven met behulp van deze definitie van de lijstweergave.

[SelectionSetName-Element voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (indeling)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md) geeft de set van .NET-typen waarvoor de voorwaarde is geactiveerd. Wanneer een van de typen in deze set aanwezig zijn, de voorwaarde wordt voldaan en het object wordt weergegeven met behulp van deze definitie van de tabelweergave.

[SelectionSetName-Element voor SelectionCondition voor EntrySelectedBy voor WideEntry (indeling)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md) geeft de set van .NET-typen waarvoor de voorwaarde is geactiveerd. Wanneer een van de typen in deze set aanwezig zijn, de voorwaarde wordt voldaan en het object met behulp van deze definitie van de brede weergave wordt weergegeven.

[SelectionSetName-Element voor ViewSelectedBy (indeling)](./selectionsetname-element-for-viewselectedby-format.md) geeft een reeks van .NET-objecten die worden weergegeven in de weergave.

[SelectionSets-Element (indeling)](./selectionsets-element-format.md) definieert de sets met .NET-objecten die kunnen worden gebruikt door weergaven van de afzonderlijke indeling.

[ShowError Element (indeling)](./showerror-element-format.md) geeft aan dat de volledige foutrecord wordt weergegeven wanneer een fout optreedt bij het weergeven van een hoeveelheid gegevens.

[TableColumnHeader-Element voor TableHeaders voor TableControl (indeling)](./tablecolumnheader-element-format.md) definieert het label, de breedte van de kolom en de uitlijning van het label voor een kolom van de tabel.

[TableColumnItem-Element (indeling)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) definieert de eigenschap of het script waarvan de waarde wordt weergegeven in de kolom van de rij.

[TableColumnItems-Element (indeling)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) definieert de eigenschappen of scripts waarvan de waarden worden weergegeven in de rij.

[TableControl-Element (indeling)](./tablecontrol-element-format.md) definieert een tabelindeling voor een weergave.

[TableHeaders-Element (indeling)](./tableheaders-element-format.md) definieert de headers voor de kolommen van een tabel.

[TableRowEntries-Element (indeling)](./tablerowentries-element-for-tablecontrol-format.md) definieert de rijen van de tabel.

[TableRowEntry-Element (indeling)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md) definieert de gegevens die worden weergegeven in een rij van de tabel.

[Tekstelement voor CustomItem voor besturingselementen voor de configuratie (-indeling)](./text-element-for-customitem-for-controls-for-configuration-format.md) geeft tekst die wordt toegevoegd aan de gegevens die worden weergegeven door het besturingselement, zoals een label, vierkante haken om de gegevens en spaties laten inspringen van de gegevens. Dit element wordt gebruikt bij het definiëren van een algemene besturingselement dat kan worden gebruikt door alle weergaven in de opmaak-bestand.

[Tekstelement voor CustomItem voor besturingselementen voor weergave (indeling)](./text-element-for-customitem-for-controls-for-view-format.md) geeft tekst die wordt toegevoegd aan de gegevens die worden weergegeven door het besturingselement, zoals een label, vierkante haken om de gegevens en spaties laten inspringen van de gegevens. Dit element wordt gebruikt bij het definiëren van besturingselementen die kunnen worden gebruikt door een weergave.

[Tekstelement voor CustomItem (indeling)](./text-element-for-customitem-for-customview-for-view-format.md) geeft tekst die wordt toegevoegd aan de gegevens die worden weergegeven door het besturingselement, zoals een label, vierkante haken om de gegevens en spaties laten inspringen van de gegevens. Dit element wordt gebruikt bij het definiëren van een aangepast besturingselement-weergave.

[Tekstelement voor CustomItem voor GroupBy (indeling)](./text-element-for-customitem-for-groupby-format.md) geeft tekst die wordt toegevoegd aan de gegevens die worden weergegeven door het besturingselement, zoals een label, vierkante haken om de gegevens en spaties laten inspringen van de gegevens. Dit element wordt gebruikt bij het definiëren van hoe een nieuwe groep objecten worden weergegeven.

[TypeName-Element voor EntrySelectedBy voor besturingselementen voor de configuratie (-indeling)](./typename-element-for-entryselectedby-for-controls-for-configuration-format.md) Hiermee geeft u een .NET-type dat gebruikmaakt van deze definitie van het besturingselement. Dit element wordt gebruikt bij het definiëren van een algemene besturingselement dat kan worden gebruikt door alle weergaven in de opmaak-bestand.

[TypeName-Element voor EntrySelectedBy voor besturingselementen voor weergave (indeling)](./typename-element-for-entryselectedby-for-controls-for-view-format.md) Hiermee geeft u een .NET-type dat gebruikmaakt van deze definitie van het besturingselement. Dit element wordt gebruikt bij het definiëren van besturingselementen die kunnen worden gebruikt door een weergave.

[TypeName-Element voor EntrySelectedBy voor CustomEntry voor weergave (indeling)](./typename-element-for-entryselectedby-for-customentry-for-view-format.md) Hiermee geeft u een .NET-type dat gebruikmaakt van deze definitie van de weergave van het aangepaste besturingselement. Er is geen limiet voor het aantal typen die kunnen worden opgegeven voor een definitie.

[TypeName-Element voor EntrySelectedBy voor EnumerableExpansion (indeling)](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md) Hiermee geeft u een .NET-type dat door deze definitie is uitgevouwen. Dit element wordt gebruikt bij het definiëren van een standaard-instellingen.

[TypeName-Element voor EntrySelectedBy voor GroupBy (indeling)](./typename-element-for-entryselectedby-for-groupby-format.md) Hiermee geeft u een .NET-type dat gebruikmaakt van deze definitie van het aangepaste besturingselement. Dit element wordt gebruikt bij het definiëren van hoe een nieuwe groep objecten worden weergegeven.

[TypeName-Element voor EntrySelectedBy voor ListControl (indeling)](./typename-element-for-entryselectedby-for-listcontrol-format.md) Hiermee geeft u een .NET-type dat deze vermelding van de lijstweergave gebruikt. Er is geen limiet voor het aantal typen die kunnen worden opgegeven voor een lijstitem.

[TypeName-Element voor EntrySelectedBy voor TableRowEntry (indeling)](./typename-element-for-entryselectedby-for-tablecontrol-format.md) Hiermee geeft u een .NET-type dat deze vermelding van de tabelweergave gebruikt. Er is geen limiet voor het aantal typen die kunnen worden opgegeven voor de vermelding in een tabel.

[TypeName-Element voor EntrySelectedBy voor WideEntry (indeling)](./typename-element-for-entryselectedby-for-wideentry-format.md) Hiermee geeft u een .NET-type voor de definitie. De definitie wordt gebruikt wanneer dit object wordt weergegeven.

[TypeName-Element voor SelectionCondition voor besturingselementen voor de configuratie (-indeling)](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md) Hiermee geeft u een .NET-type dat de voorwaarde wordt geactiveerd. Dit element wordt gebruikt bij het definiëren van een algemene besturingselement dat kan worden gebruikt door alle weergaven in de opmaak-bestand.

[TypeName-Element voor SelectionCondition voor besturingselementen voor weergave (indeling)](./typename-element-for-selectioncondition-for-controls-for-view-format.md) Hiermee geeft u een .NET-type dat de voorwaarde wordt geactiveerd. Dit element wordt gebruikt bij het definiëren van besturingselementen die kunnen worden gebruikt door een weergave.

[TypeName-Element voor SelectionCondition voor CustomControl voor weergave (indeling)](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md) Hiermee geeft u een .NET-type dat de voorwaarde wordt geactiveerd. Dit element wordt gebruikt bij het definiëren van een aangepast besturingselement-weergave.

[TypeName-Element voor SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (indeling)](./typename-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md) Hiermee geeft u een .NET-type dat de voorwaarde wordt geactiveerd.

[TypeName-Element voor SelectionCondition voor GroupBy (indeling)](./typename-element-for-selectioncondition-for-groupby-format.md) Hiermee geeft u een .NET-type dat de voorwaarde wordt geactiveerd. Dit element wordt gebruikt bij het definiëren van hoe een nieuwe groep objecten worden weergegeven.

[TypeName-Element voor SelectionCondition voor EntrySelectedBy voor ListControl (indeling)](./typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md) Hiermee geeft u een .NET-type dat de voorwaarde wordt geactiveerd. Wanneer dit type aanwezig is, wordt de vermelding in de lijst gebruikt.

[TypeName-Element voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (indeling)](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md) Hiermee geeft u een .NET-type dat de voorwaarde wordt geactiveerd. Wanneer dit type aanwezig is, wordt de voorwaarde wordt voldaan en wordt een rij in de tabel wordt gebruikt.

[TypeName-Element voor SelectionCondition voor EntrySelectedBy voor WideEntry (indeling)](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md) Hiermee geeft u een .NET-type dat de voorwaarde wordt geactiveerd. Wanneer dit type aanwezig is, wordt de definitie wordt gebruikt.

[TypeName-Element voor typen die zijn (indeling)](./typename-element-for-types-format.md) Hiermee geeft u de .NET-type van een object dat bij de selectieset hoort.

[TypeName-Element voor ViewSelectedBy (indeling)](./typename-element-for-viewselectedby-format.md) Hiermee geeft u een .NET-object dat door de weergave wordt weergegeven.

[Element (indeling) van het type](./types-element-for-selectionset-format.md) definieert de .NET-objecten die in de selectie.

[Element (indeling) weergeven](./view-element-format.md) definieert een weergave die wordt gebruikt om een of meer .NET-objecten weer te geven.

[ViewDefinitions-Element (indeling)](./viewdefinitions-element-format.md) definieert de weergaven die wordt gebruikt om objecten weer te geven.

[ViewSelectedBy-Element (indeling)](./viewselectedby-element-format.md) definieert de .NET-objecten die worden weergegeven in de weergave.

[WideControl-Element (indeling)](./widecontrol-element-format.md) definieert een lijst van de hele (één waarde)-indeling voor de weergave. Deze weergave bevat een waarde van één eigenschap of een Scriptwaarde voor elk object.

[WideEntries-Element (indeling)](./wideentries-element-for-widecontrol-format.md) bevat de definities van de brede weergave. De brede weergave moet een of meer netwerkdefinities opgeven.

[WideEntry-Element (indeling)](./wideentry-element-for-widecontrol-format.md) biedt een definitie van de brede weergave.

[WideItem-Element (indeling)](./wideitem-element-for-widecontrol-format.md) definieert de eigenschap of het script waarvan de waarde wordt weergegeven.

[Breedte van Element (indeling)](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) bepaalt de breedte (in tekens) van een kolom.

[Inpakken van Element (indeling)](./wrap-element-for-tablerowentry-for-tablecontrol-format.md) geeft aan dat de tekst die langer is dan de breedte van de kolom wordt weergegeven op de volgende regel.

[WrapTables-Element (indeling)](./wraptables-element-format.md) geeft aan dat de gegevens in een cel in de tabel is verplaatst naar de volgende regel wanneer de gegevens langer dan de breedte van de kolom is.

## <a name="see-also"></a>Zie ook

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
