---
title: Verwijzing naar schema-XML opmaken | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ac6f7aaa-d0cc-4c7b-a341-85e736174579
caps.latest.revision: 21
ms.openlocfilehash: 437b3d6bb62fdd3a74f3392ec71df360c01a1974
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72355025"
---
# <a name="format-schema-xml-reference"></a>Naslaginformatie over XML voor opmaakschema

De onderwerpen in deze sectie beschrijven de XML-elementen die worden gebruikt door het format teren van bestanden (ps1xml-bestanden). Indelings bestanden bepalen hoe het .NET-object wordt weer gegeven. het object zelf wordt niet gewijzigd.

## <a name="in-this-section"></a>In deze sectie

[Alignment-element voor TableColumnHeader voor TableControl (indeling)](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) Hiermee wordt gedefinieerd hoe de gegevens in een kolomkop worden weer gegeven.

[Alignment-element voor TableColumnItem voor TableControl (indeling)](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) Bepaalt hoe de gegevens in de rij worden weer gegeven.

Het [element AutoSize voor TableControl (Format)](./autosize-element-for-tablecontrol-format.md) Hiermee wordt aangegeven of de kolom grootte en het aantal kolommen worden aangepast op basis van de grootte van de gegevens.

Het [element AutoSize voor WideControl (Format)](./autosize-element-for-widecontrol-format.md) Hiermee wordt aangegeven of de kolom grootte en het aantal kolommen worden aangepast op basis van de grootte van de gegevens.

[ColumnNumber-element voor WideControl (indeling)](./columnnumber-element-for-widecontrol-format.md) Hiermee geeft u het aantal kolommen op dat wordt weer gegeven in de brede weer gave.

[Configuratie-element (indeling)](./configuration-element-format.md) Vertegenwoordigt het element op het hoogste niveau van het opmaak bestand.

[Control-element voor besturings elementen voor configuratie (indeling)](./control-element-for-controls-for-configuration-format.md) Hiermee wordt een algemeen besturings element gedefinieerd dat kan worden gebruikt door alle weer gaven van het opmaak bestand en de naam die wordt gebruikt om te verwijzen naar het besturings element.

[Besturings element voor besturings elementen voor weer gave (indeling)](./control-element-for-controls-for-view-format.md) Hiermee wordt een besturings element gedefinieerd dat kan worden gebruikt door de weer gave en de naam die wordt gebruikt om te verwijzen naar het besturings element.

[Controls-element voor configuratie (indeling)](./controls-element-for-configuration-format.md) Hiermee definieert u de algemene besturings elementen die kunnen worden gebruikt door alle weer gaven van het opmaak bestand.

[Element Controls voor weer gave (indeling)](./controls-element-for-view-format.md) Hiermee worden de weergave besturings elementen gedefinieerd die kunnen worden gebruikt door een specifieke weer gave.

[CustomControl-element voor besturings element voor configuratie (indeling)](./customcontrol-element-for-control-for-controls-for-configuration-format.md) Hiermee definieert u een besturings element. Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.

[CustomControl-element voor besturings elementen voor de weer gave (indeling)](./customcontrol-element-for-control-for-controls-for-view-format.md) Hiermee definieert u een besturings element dat wordt gebruikt door de weer gave.

[CustomControl-element voor GroupBy (indeling)](./customcontrol-element-for-groupby-format.md) Hiermee definieert u het aangepaste besturings element waarin de nieuwe groep wordt weer gegeven.

[CustomControl-element (indeling)](./customcontrol-element-for-groupby-format.md) Hiermee wordt een aangepaste besturings element-indeling gedefinieerd voor de weer gave.

[CustomControlName-element voor ExpressionBinding voor besturings elementen voor configuratie (indeling)](./customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format.md) Hiermee geeft u de naam van een gemeen schappelijk besturings element op. Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.

[CustomControlName-element voor ExpressionBindine voor besturings elementen voor weer gave (indeling)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md) Hiermee geeft u de naam op van een algemeen besturings element of een weergave besturings element. Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.

[CustomControlName element van GroupBy (indeling)](./customcontrolname-element-for-groupby-format.md) Hiermee geeft u de naam op van een aangepast besturings element dat wordt gebruikt om de nieuwe groep weer te geven. Dit element wordt gebruikt bij het definiëren van een tabel, lijst, brede of aangepaste beheer weergave.

[CustomEntry-element voor CustomControl voor besturings elementen voor configuratie (indeling)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md) Biedt een definitie van het algemene besturings element. Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.

[CustomEntry-element voor CustomEntries voor besturings elementen voor weer gave (indeling)](./customentry-element-for-customentries-for-controls-for-view-format.md) Biedt een definitie van het besturings element. Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.

[CustomEntry-element voor CustomEntries voor weer gave (indeling)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md) Biedt een definitie van de aangepaste beheer weergave.

[CustomEntry-element voor CustomControl voor GroupBy (indeling)](./customentry-element-for-customcontrol-for-groupby-format.md) Biedt een definitie van het besturings element. Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.

[CustomEntries-element voor CustomControl voor configuratie (indeling)](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md) Biedt de definities van een gemeen schappelijk besturings element. Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.

[CustomEntries-element voor CustomControl voor besturings elementen voor weer gave (indeling)](./customentries-element-for-customcontrol-for-controls-for-view-format.md) Bevat de definities voor het besturings element. Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.

[CustomEntries-element voor CustomControl voor GroupBy (indeling)](./customentries-element-for-customcontrol-for-groupby-format.md) Bevat de definities voor het besturings element. Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.

[CustomEntries-element voor CustomControl voor weer gave (indeling)](./customentries-element-for-customcontrol-for-view-format.md) Biedt de definities van de aangepaste beheer weergave. In de aangepaste beheer weergave moeten een of meer definities worden opgegeven.

[CustomItem-element voor CustomEntry voor besturings elementen voor configuratie](./customitem-element-for-customentry-for-controls-for-configuration-format.md) Hiermee definieert u welke gegevens worden weer gegeven door het besturings element en hoe deze worden weer gegeven. Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.

[CustomItem-element voor CustomEntry voor besturings elementen voor weer gave (indeling)](./customitem-element-for-customentry-for-controls-for-view-format.md) Hiermee definieert u welke gegevens worden weer gegeven door het besturings element en hoe deze worden weer gegeven. Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.

[CustomItem-element voor CustomEntry voor weer gave (indeling)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md) Hiermee definieert u welke gegevens worden weer gegeven in de weer gave van het aangepaste besturings element en hoe deze worden weer gegeven. Dit element wordt gebruikt bij het definiëren van een aangepaste beheer weergave.

[CustomItem-element voor CustomEntry voor GroupBy (indeling)](./customitem-element-for-customentry-for-groupby-format.md) Hiermee definieert u welke gegevens worden weer gegeven in de weer gave van het aangepaste besturings element en hoe deze worden weer gegeven. Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.

[DefaultSettings-element (indeling)](./defaultsettings-element-format.md) Hiermee definieert u algemene instellingen die van toepassing zijn op alle weer gaven van het opmaak bestand. Algemene instellingen zijn onder meer het weer geven van fouten, tekst terugloop in tabellen, definiëren hoe verzamelingen worden uitgevouwen en meer.

[Display error-element (indeling)](./displayerror-element-format.md) Hiermee geeft u op dat de teken reeks #ERR wordt weer gegeven wanneer een fout optreedt bij het weer geven van een stukje gegevens.

[EntrySelectedBy-element voor CustomEntry voor besturings elementen voor configuratie (indeling)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md) Definieert de .NET-typen die gebruikmaken van de definitie van het algemene besturings element of de voor waarde die moet bestaan voor het gebruik van dit besturings element. Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.

[EntrySelectedBy-element voor CustomEntry voor besturings elementen voor weer gave (indeling)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md) Hiermee definieert u de .NET-typen die gebruikmaken van deze controle definitie of de voor waarde die voor deze definitie moet worden gebruikt. Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.

[EntrySelectedBy-element voor CustomEntry voor weer gave (indeling)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md) Hiermee definieert u de .NET-typen die gebruikmaken van deze aangepaste vermelding of de voor waarde die moet bestaan voor deze vermelding.

[EntrySelectedBy-element voor EnumerableExpansion (indeling)](./entryselectedby-element-for-enumerableexpansion-format.md) Hiermee definieert u de .NET-typen die gebruikmaken van deze definitie of de voor waarde die voor deze definitie moet worden gebruikt.

[EntrySelectedBy-element voor CustomEntry voor GroupBy (indeling)](./entryselectedby-element-for-customentry-for-groupby-format.md) Hiermee definieert u de .NET-typen die gebruikmaken van deze controle definitie of de voor waarde die voor deze definitie moet worden gebruikt. Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.

[EntrySelectedBy-element voor List entry voor ListControl (indeling)](./entryselectedby-element-for-listentry-for-listcontrol-format.md) Hiermee definieert u de .NET-typen die gebruikmaken van deze lijst weergave definitie of de voor waarde die voor deze definitie moet worden gebruikt. In de meeste gevallen is slechts één definitie nodig voor een lijst weergave. U kunt echter meerdere definities voor de lijst weergave opgeven als u dezelfde lijst weergave wilt gebruiken om verschillende gegevens voor verschillende objecten weer te geven.

[EntrySelectedBy-element voor TableRowEntry (indeling)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) Hiermee definieert u de .NET-typen waarvan de eigenschaps waarden worden weer gegeven in de rij.

[EntrySelectedBy-element voor WideEntry (indeling)](./entryselectedby-element-for-wideentry-format.md) Hiermee definieert u de .NET-typen die gebruikmaken van deze definitie van de brede weer gave of de voor waarde die voor deze definitie moet worden gebruikt.

[EnumerableExpansion-element (indeling)](./enumerableexpansion-element-format.md) Hiermee definieert u hoe specifieke .NET-verzamelings objecten worden uitgevouwen wanneer ze in een weer gave worden weer gegeven.

[EnumerableExpansions-element (indeling)](./enumerableexpansions-element-format.md) Hiermee definieert u hoe .NET-verzamelings objecten worden uitgevouwen wanneer ze worden weer gegeven in een weer gave.

[EnumerateCollection-element voor ExpressionBinding voor besturings elementen voor configuratie (indeling)](./enumeratecollection-element-for-expressionbinding-for-controls-for-configuration-format.md) Opgegeven dat de elementen van verzamelingen worden weer gegeven door het besturings element. Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.

[EnumerateCollection-element voor ExpressionBinding voor besturings elementen voor weer gave (indeling)](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md) Opgegeven dat de elementen van verzamelingen worden weer gegeven. Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.

[EnumerateCollection-element voor expressie binding voor CustomControl voor weer gave (indeling)](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md) Hiermee geeft u op dat de elementen van verzamelingen worden weer gegeven. Dit element wordt gebruikt bij het definiëren van een aangepaste beheer weergave.

[EnumerateCollection-element voor ExpressionBinding voor GroupBy (indeling)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md) Hiermee geeft u op dat de elementen van verzamelingen worden weer gegeven. Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.

[Element uitbreiden (indeling)](./expand-element-format.md) Hiermee geeft u op hoe het verzamelings object voor deze definitie moet worden uitgebreid.

[ExpressionBinding-element voor CustomItem voor besturings elementen voor configuratie (indeling)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md) Hiermee worden de gegevens gedefinieerd die door het besturings element worden weer gegeven. Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.

[ExpressionBinding-element voor CustomItem voor besturings elementen voor weer gave (indeling)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md) Hiermee worden de gegevens gedefinieerd die door het besturings element worden weer gegeven. Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.

[ExpressionBinding-element voor CustomItem voor CustomControl voor weer gave (indeling)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md) Hiermee worden de gegevens gedefinieerd die door het besturings element worden weer gegeven. Dit element wordt gebruikt bij het definiëren van een aangepaste beheer weergave.

[ExpressionBinding-element voor CustomItem voor GroupBy (indeling)](./expressionbinding-element-for-customitem-for-groupby-format.md) Hiermee worden de gegevens gedefinieerd die door het besturings element worden weer gegeven. Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.

[FirstLineHanging-element voor frame voor besturings elementen voor configuratie (indeling)](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) Geeft aan hoeveel tekens de eerste regel van de gegevens naar links verschuift. Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.

[FirstLineHanging-element van het frame van de besturings elementen van de weer gave (indeling)](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) Geeft aan hoeveel tekens de eerste regel van de gegevens naar links verschuift. Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.

[FirstLineHanging-element voor frame voor CustomControl voor weer gave (indeling)](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) Geeft aan hoeveel tekens de eerste regel van de gegevens naar links verschuift. Dit element wordt gebruikt bij het definiëren van een aangepaste beheer weergave.

[FirstLineHanging-element voor frame voor GroupBy (indeling)](./firstlinehanging-element-for-frame-for-groupby-format.md) Geeft aan hoeveel tekens de eerste regel van de gegevens naar links verschuift. Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.

[FirstLineIndent-element voor frame voor besturings elementen voor configuratie (indeling)](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) Geeft aan hoeveel tekens de eerste regel van de gegevens naar rechts wordt geschoven. Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.

[FirstLineIndent-element van het frame van de besturings elementen van de weer gave (indeling)](./firstlineindent-element-for-frame-for-controls-for-view-format.md) Geeft aan hoeveel tekens de eerste regel van de gegevens naar rechts wordt geschoven. Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.

[FirstLineIndent-element](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) Geeft aan hoeveel tekens de eerste regel van de gegevens naar rechts wordt geschoven. Dit element wordt gebruikt bij het definiëren van een aangepaste beheer weergave.

[FirstLineIndent-element voor frame voor GroupBy (indeling)](./firstlineindent-element-for-frame-for-groupby-format.md) Geeft aan hoeveel tekens de eerste regel van de gegevens naar rechts wordt geschoven. Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.

[Element formats Tring voor lijst item (indeling)](./formatstring-element-for-listitem-for-listcontrol-format.md) Geeft een opmaak patroon aan dat definieert hoe de eigenschap of script waarde wordt weer gegeven.

[Element formats Tring voor TableColumnItem (indeling)](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md) Hiermee geeft u een indelings patroon op dat definieert hoe de eigenschap of script waarde van de tabel wordt weer gegeven.

[Element formats Tring voor WideItem voor WideControl (indeling)](./formatstring-element-for-wideitem-for-widecontrol-format.md) Geeft een indelings patroon aan dat definieert hoe de eigenschap of script waarde wordt weer gegeven in de weer gave.

[Frame-element voor CustomItem voor besturings elementen voor configuratie (indeling)](./frame-element-for-customitem-for-controls-for-configuration-format.md) Hiermee definieert u hoe de gegevens worden weer gegeven, zoals de gegevens naar links of rechts verplaatsen. Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.

[Frame-element voor CustomItem voor besturings elementen voor weer gave (indeling)](./frame-element-for-customitem-for-controls-for-view-format.md) Hiermee definieert u hoe de gegevens worden weer gegeven, zoals de gegevens naar links of rechts verplaatsen. Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.

[Frame-element voor CustomItem voor CustomControl voor weer gave (indeling)](./frame-element-for-customitem-for-customcontrol-for-view-format.md) Hiermee definieert u hoe de gegevens worden weer gegeven, zoals de gegevens naar links of rechts verplaatsen. Dit element wordt gebruikt bij het definiëren van een aangepaste beheer weergave.

[Frame-element voor CustomItem voor GroupBy (indeling)](./frame-element-for-customitem-for-groupby-format.md) Hiermee definieert u hoe de gegevens worden weer gegeven, zoals de gegevens naar links of rechts verplaatsen. Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.

[Element GroupBy voor weer gave (indeling)](./groupby-element-for-view-format.md) Definieert hoe een nieuwe groep objecten wordt weer gegeven in Windows Power shell.

[HideTableHeaders-element (indeling)](./hidetableheaders-element-format.md) Hiermee geeft u op dat de kopteksten van de tabel niet worden weer gegeven.

[ItemSelectionCondition-element voor ExpressionBinding voor besturings elementen voor configuratie (indeling)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md) Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit besturings element. Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.

[ItemSelectionCondition-element van ExpressionBinding voor besturings elementen voor weer gave (indeling)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md) Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit besturings element. Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.

[ItemSelectionCondition-element voor expressie binding voor CustomControl voor weer gave (indeling)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md) Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit besturings element. Er is geen limiet voor het aantal selectie omstandigheden dat kan worden opgegeven voor een besturings element. Dit element wordt gebruikt bij het definiëren van een aangepaste beheer weergave.

[ItemSelectionCondition-element voor ExpressionBinding voor GroupBy (indeling)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md) Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit besturings element. Er is geen limiet voor het aantal selectie omstandigheden dat kan worden opgegeven voor een besturings element. Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.

[ItemSelectionCondition-element voor lijst item (indeling)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md) Hiermee definieert u de voor waarde die moet bestaan voor het gebruik van dit lijst item.

[Element label voor lijst item voor ListControl (indeling)](./label-element-for-listitem-for-listcontrol-format.md) Hiermee geeft u het label voor de eigenschap of script waarde in de rij.

[Label element voor GroupBy (indeling)](./label-element-for-groupby-format.md) Hiermee geeft u een label op dat wordt weer gegeven wanneer een nieuwe groep wordt aangetroffen.

[Element label voor TableColumnHeader (indeling)](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) Hiermee wordt het label gedefinieerd dat boven aan een kolom wordt weer gegeven.

[LeftIndent-element voor frame voor besturings elementen voor configuratie (indeling)](./leftindent-element-for-frame-for-controls-for-configuration-format.md) Hiermee geeft u op hoeveel tekens de gegevens van de linkermarge worden verplaatst. Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.

[LeftIndent-element van het frame van de besturings elementen van de weer gave (indeling)](./leftindent-element-for-frame-for-controls-for-view-format.md) Hiermee geeft u op hoeveel tekens de gegevens van de linkermarge worden verplaatst. Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.

[LeftIndent-element voor frame voor CustomControl voor weer gave (indeling)](./leftindent-element-for-frame-for-customcontrol-for-view-format.md) Hiermee geeft u op hoeveel tekens de gegevens van de linkermarge worden verplaatst. Dit element wordt gebruikt bij het definiëren van een aangepaste beheer weergave.

[LeftIndent-element voor frame voor GroupBy (indeling)](./leftindent-element-for-frame-for-groupby-format.md) Hiermee geeft u op hoeveel tekens de gegevens van de linkermarge worden verplaatst. Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.

[ListControl-element (indeling)](./listcontrol-element-format.md) Hiermee definieert u een lijst indeling voor de weer gave.

[Element List entry (indeling)](./listentry-element-for-listcontrol-format.md) Geeft een definitie van de lijst weergave.

[Element List Entries (indeling)](./listentries-element-for-listcontrol-format.md) Hiermee wordt gedefinieerd hoe de rijen van de lijst weergave worden weer gegeven.

[Lijst item-element (indeling)](./listitem-element-for-listitems-for-listcontrol-format.md) Hiermee wordt de eigenschap of het script gedefinieerd waarvan de waarde wordt weer gegeven in een rij van de lijst weergave.

[List items-element (indeling)](./listitems-element-for-listentry-for-listcontrol-format.md) Hiermee worden de eigenschappen en scripts gedefinieerd die worden weer gegeven in de lijst weergave.

[Element naam voor besturings elementen voor configuratie (indeling)](./name-element-for-control-for-controls-for-configuration-format.md) Hiermee geeft u de naam van het besturings element op. Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.

[Naam element voor selectieset (indeling)](./name-element-for-selectionset-format.md) Hiermee geeft u de naam op die wordt gebruikt om te verwijzen naar de selectieset.

[Naam element voor weer gave (indeling)](./name-element-for-view-format.md) Hiermee geeft u de naam op die wordt gebruikt om de weer gave te identificeren.

[Element nieuwe regel voor CustomItem voor besturings elementen voor configuratie (indeling)](./newline-element-for-customitem-for-controls-for-configuration-format.md) Hiermee voegt u een lege regel toe aan de weer gave van het besturings element. Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.

[Element nieuwe regel voor CustomItem voor besturings elementen voor weer gave (indeling)](./newline-element-for-customitem-for-controls-for-view-format.md) Hiermee voegt u een lege regel toe aan de weer gave van het besturings element. Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.

[Element nieuwe regel voor CustomItem voor CustomControl voor weer gave (indeling)](./newline-element-for-customitem-for-customcontrol-for-view-format.md) Hiermee voegt u een lege regel toe aan de weer gave van het besturings element. Dit element wordt gebruikt bij het definiëren van een aangepaste beheer weergave.

[Element nieuwe regel voor CustomItem voor GroupBy (indeling)](./newline-element-for-customitem-for-groupby-format.md) Hiermee voegt u een lege regel toe aan de weer gave van het besturings element. Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.

Het [element PropertyName voor ExpressionBinding voor besturings elementen voor configuratie (indeling)](./propertyname-element-for-expressionbinding-for-controls-for-configuration-format.md) Hiermee geeft u de .NET-eigenschap op waarvan de waarde wordt weer gegeven door het algemene besturings element. Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.

Het [element PropertyName voor ExpressionBinding voor besturings elementen voor weer gave (indeling)](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md) Hiermee geeft u de .NET-eigenschap op waarvan de waarde wordt weer gegeven door het besturings element. Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.

Het [element PropertyName voor ExpressionBinding voor CustomControl voor weer gave (indeling)](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md) Hiermee geeft u de .NET-eigenschap op waarvan de waarde wordt weer gegeven door het besturings element. Dit element wordt gebruikt bij het definiëren van een aangepaste besturings element weergave

Het [element PropertyName voor ExpressionBinding voor GroupBy (indeling)](./propertyname-element-for-expressionbinding-for-groupby-format.md) Hiermee geeft u de .NET-eigenschap op waarvan de waarde wordt weer gegeven door het besturings element. Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.

[PropertyName-element voor GroupBy (indeling)](./propertyname-element-for-groupby-format.md) Hiermee geeft u de .NET-eigenschap op waarmee een nieuwe groep wordt gestart wanneer de waarde ervan wordt gewijzigd.

Het [element PropertyName voor ItemSeclectionCondition voor besturings elementen voor configuratie (indeling)](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd. Wanneer deze eigenschap aanwezig is of wordt geëvalueerd als `true`, wordt aan de voor waarde voldaan en wordt het besturings element gebruikt. Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.

Het [element PropertyName voor ItemSelectionCondition voor besturings elementen voor weer gave (indeling)](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md) Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd. Wanneer deze eigenschap aanwezig is of wordt geëvalueerd als `true`, wordt aan de voor waarde voldaan en wordt het besturings element gebruikt. Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.

Het [element PropertyName voor ItemSelectionCondition voor CustomControl voor weer gave (indeling](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) specificeert de .net-eigenschap waarmee de voor waarde wordt geactiveerd. Wanneer deze eigenschap aanwezig is of wordt geëvalueerd als `true`, wordt aan de voor waarde voldaan en wordt het besturings element gebruikt. Dit element wordt gebruikt bij het definiëren van een aangepaste beheer weergave.

Het [element PropertyName voor ItemSelectionCondition voor GroupBy (indeling)](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd. Wanneer deze eigenschap aanwezig is of wordt geëvalueerd als `true`, wordt aan de voor waarde voldaan en wordt het besturings element gebruikt. Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.

Het [element PropertyName voor ItemSelectionCondition voor lijst item (indeling)](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md) Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd. Wanneer deze eigenschap aanwezig is of wordt geëvalueerd als `true`, wordt aan de voor waarde voldaan en wordt de weer gave gebruikt. Dit element wordt gebruikt bij het definiëren van een lijst weergave.

[PropertyName-element voor lijst item voor ListControl (indeling)](./propertyname-element-for-listitem-for-listcontrol-format.md) Hiermee geeft u de .NET-eigenschap op waarvan de waarde wordt weer gegeven in de lijst.

Het [element PropertyName voor SelectionCondition voor EntrySelectedBy voor List entry (indeling)](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md) Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd. Wanneer deze eigenschap aanwezig is of wordt geëvalueerd als `true`, wordt aan de voor waarde voldaan en wordt de vermelding gebruikt. Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.

Het [element PropertyName voor SelectionCondition voor besturings elementen voor weer gave (indeling)](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md) Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd. Wanneer deze eigenschap aanwezig is of wordt geëvalueerd als `true`, wordt aan de voor waarde voldaan en wordt de vermelding gebruikt. Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.

Het [element PropertyName voor SelectionCondition voor CustomControl voor weer gave (indeling)](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md) Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd. Wanneer deze eigenschap aanwezig is of wordt geëvalueerd als `true`, wordt aan de voor waarde voldaan en wordt de definitie gebruikt. Dit element wordt gebruikt bij het definiëren van een aangepaste beheer weergave.

Het [element PropertyName voor SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (indeling)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md) Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd. Wanneer deze eigenschap aanwezig is of wordt geëvalueerd als `true`, wordt aan de voor waarde voldaan en wordt de definitie gebruikt.

Het [element PropertyName voor SelectionCondition voor GroupBy (indeling)](./propertyname-element-for-selectioncondition-for-groupby-format.md) Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd. Wanneer deze eigenschap aanwezig is of wordt geëvalueerd als `true`, wordt aan de voor waarde voldaan en wordt de definitie gebruikt. Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.

Het [element PropertyName voor SelectionCondition voor EntrySelectedBy voor List entry (indeling)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md) Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd. Wanneer deze eigenschap aanwezig is of wordt geëvalueerd als `true`, wordt aan de voor waarde voldaan en wordt de vermelding in de lijst gebruikt.

Het [element PropertyName voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (indeling)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md) Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd. Als deze eigenschap aanwezig is of als deze wordt geëvalueerd als `true`, wordt aan de voor waarde voldaan en wordt het tabel item gebruikt.

Het [element PropertyName voor SelectionCondition voor EntrySelectedBy voor WideEntry (indeling)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md) Hiermee geeft u de .NET-eigenschap op waarmee de voor waarde wordt geactiveerd. Wanneer deze eigenschap aanwezig is of wordt geëvalueerd als `true`, wordt aan de voor waarde voldaan en wordt de definitie gebruikt.

Het [element PropertyName voor TableColumnItem (indeling)](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) Hiermee geeft u de eigenschap op waarvan de waarde wordt weer gegeven in de kolom van de rij.

Het [element PropertyName voor WideItem (indeling)](./propertyname-element-for-wideitem-for-widecontrol-format.md) Hiermee geeft u de eigenschap op van het object waarvan de waarde wordt weer gegeven in de brede weer gave.

[RightIndent-element voor frame voor besturings elementen voor configuratie (indeling)](./rightindent-element-for-frame-for-controls-for-configuration-format.md) Hiermee geeft u op hoeveel tekens de gegevens van de rechter marge worden verplaatst. Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.

[RightIndent-element van het frame van de besturings elementen van de weer gave (indeling)](./rightindent-element-for-frame-for-controls-for-view-format.md) Hiermee geeft u op hoeveel tekens de gegevens van de rechter marge worden verplaatst. Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.

[RightIndent-element](./rightindent-element-for-frame-for-customcontrol-for-view-format.md) Hiermee geeft u op hoeveel tekens de gegevens van de rechter marge worden verplaatst. Dit element wordt gebruikt bij het definiëren van een aangepaste beheer weergave.

[RightIndent-element voor frame voor GroupBy (indeling)](./rightindent-element-for-frame-for-groupby-format.md) Hiermee geeft u op hoeveel tekens de gegevens van de rechter marge worden verplaatst. Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.

[Script block-element voor ExpressionBinding voor besturings elementen voor configuratie (indeling)](./scriptblock-element-for-expressionbinding-for-controls-for-configuration-format.md) Hiermee geeft u het script op waarvan de waarde wordt weer gegeven door het algemene besturings element. Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.

[Script block-element voor ExpressionBinding voor besturings elementen voor weer gave (indeling)](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md) Hiermee geeft u het script op waarvan de waarde wordt weer gegeven door het besturings element. Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.

[Script block-element voor ExpressionBinding voor CustomCustomControl voor weer gave (indeling)](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md) Hiermee geeft u het script op waarvan de waarde wordt weer gegeven door het besturings element. Dit element wordt gebruikt bij het definiëren van een aangepaste beheer weergave.

[Script block-element voor ExpressionBinding voor GroupBy (indeling)](./scriptblock-element-for-expressionbinding-for-groupby-format.md) Hiermee geeft u het script op waarvan de waarde wordt weer gegeven door het besturings element. Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.

[Script block-element voor GroupBy (indeling)](./scriptblock-element-for-groupby-format.md) Hiermee geeft u het script op waarmee een nieuwe groep wordt gestart wanneer de waarde ervan wordt gewijzigd.

[Script block-element voor ItemSelectionCondition voor besturings elementen voor configuratie (indeling)](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd. Wanneer dit script wordt geëvalueerd om `true`, wordt aan de voor waarde voldaan en wordt het besturings element gebruikt. Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.

[Script block-element voor ItemSelectionCondition voor besturings elementen voor weer gave (indeling)](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md) Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd. Wanneer dit script wordt geëvalueerd om `true`, wordt aan de voor waarde voldaan en wordt het besturings element gebruikt. Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.

[Script block-element voor ItemSelectionCondition voor CustomControl voor weer gave (indeling)](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd. Wanneer dit script wordt geëvalueerd om `true`, wordt aan de voor waarde voldaan en wordt het besturings element gebruikt. Dit element wordt gebruikt bij het definiëren van een aangepaste beheer weergave.

[Script block-element voor ItemSelectionCondition voor GroupBy (indeling)](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md) Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd. Wanneer dit script wordt geëvalueerd om `true`, wordt aan de voor waarde voldaan en wordt het besturings element gebruikt. Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.

[Script block-element voor ItemSelectionCondition voor ListControl (indeling)](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd. Wanneer dit script wordt geëvalueerd om `true`, wordt aan de voor waarde voldaan en wordt het lijst item gebruikt. Dit element wordt gebruikt bij het definiëren van een lijst weergave.

[Script block-element voor lijst item (indeling)](./scriptblock-element-for-listitem-for-listcontrol-format.md) Hiermee geeft u het script op waarvan de waarde wordt weer gegeven in de rij van de lijst.

[Script block-element voor SelectionCondition voor besturings elementen voor configuratie (indeling)](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md) Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd. Wanneer dit script wordt geëvalueerd om `true`, wordt aan de voor waarde voldaan en wordt de definitie gebruikt. Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.

[Script block-element voor SelectionCondition voor besturings elementen voor weer gave (indeling)](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md) Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd. Wanneer dit script wordt geëvalueerd om `true`, wordt aan de voor waarde voldaan en wordt de definitie gebruikt. Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.

[Script block-element voor SelectionCondition voor CustomControl voor weer gave (indeling)](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md) Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd. Wanneer dit script wordt geëvalueerd om `true`, wordt aan de voor waarde voldaan en wordt de definitie gebruikt. Dit element wordt gebruikt bij het definiëren van een aangepaste beheer weergave.

[Script block-element voor SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (indeling)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md) Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd.

[Script block-element voor SelectionCondition voor GroupBy (indeling)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format.md) Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd. Wanneer dit script wordt geëvalueerd om `true`, wordt aan de voor waarde voldaan en wordt de definitie gebruikt. Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.

[Script block-element voor SelectionCondition voor EntrySelectedBy voor List entry (indeling)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md) Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd. Wanneer dit script wordt geëvalueerd om `true`, wordt aan de voor waarde voldaan en wordt de vermelding in de lijst gebruikt.

[Script block-element voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (indeling)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md) Hiermee geeft u het script blok op waarmee de voor waarde wordt geactiveerd. Wanneer dit script wordt geëvalueerd om `true`, wordt aan de voor waarde voldaan en wordt het tabel item gebruikt.

[Script block-element voor SelectionCondition voor EntrySelectedBy voor WideEntry (indeling)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md) Hiermee geeft u het script op waarmee de voor waarde wordt geactiveerd. Wanneer dit script wordt geëvalueerd om `true`, wordt aan de voor waarde voldaan en wordt de definitie van het grote item gebruikt.

[Script block-element voor TableColumnItem (indeling)](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) Hiermee geeft u het script op waarvan de waarde wordt weer gegeven in de kolom van de rij.

[Script block-element voor WideItem (indeling)](./scriptblock-element-for-wideitem-for-widecontrol-format.md) Hiermee geeft u het script op waarvan de waarde wordt weer gegeven in de brede weer gave.

[SelectionCondition-element voor EntrySelectedBy voor CustomEntry voor configuratie (indeling)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md) Hiermee definieert u een voor waarde die moet bestaan voor het gebruik van een algemene definitie van het besturings element. Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.

[SelectionCondition-element voor EntrySelectedBy voor besturings elementen voor weer gave (indeling)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md) Hiermee definieert u een voor waarde die moet bestaan voor het gebruik van de controle definitie. Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.

[SelectionCondition-element voor EntrySelectedBy voor CustomControl voor weer gave (indeling)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md) Hiermee definieert u een voor waarde die moet bestaan voor het gebruik van een definitie van een besturings element. Dit element wordt gebruikt bij het definiëren van een aangepaste beheer weergave.

[SelectionCondition-element voor EntrySelectedBy voor EnumerableExpansion (indeling)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md) Hiermee definieert u de voor waarde die moet bestaan om de verzamelings objecten van deze definitie uit te breiden.

[SelectionCondition-element voor EntrySelectedBy voor GroupBy (indeling)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md) Hiermee definieert u een voor waarde die moet bestaan voor het gebruik van een definitie van een besturings element. Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.

[SelectionCondition-element voor EntrySelectedBy voor List entry (indeling)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) Hiermee definieert u de voor waarde die moet bestaan om deze definitie van de lijst weergave te gebruiken. Er is geen limiet voor het aantal selectie omstandigheden dat kan worden opgegeven voor een lijst definitie.

[SelectionCondition-element voor EntrySelectedBy voor TableRowEntry (indeling)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md) Hiermee definieert u de voor waarde die moet bestaan om te gebruiken voor deze definitie van de tabel weergave. Er is geen limiet voor het aantal selectie omstandigheden dat kan worden opgegeven voor een tabel definitie.

[SelectionCondition-element voor EntrySelectedBy voor WideEntry (indeling)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) Hiermee definieert u de voor waarde die voor deze definitie moet worden gebruikt. Er is geen limiet voor het aantal selectie omstandigheden dat kan worden opgegeven voor een definitie van een brede vermelding.

[Selectie verzamelings element (indeling)](./selectionset-element-format.md) Hiermee wordt een set .NET-objecten gedefinieerd waarnaar kan worden verwezen door de naam van de set.

[SelectionSetName-element voor EntrySelectedBy voor besturings elementen voor configuratie (indeling)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md) Hiermee geeft u een set .NET-typen op die gebruikmaken van deze definitie van het besturings element. Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.

[SelectionSetName-element voor EntrySelectedBy voor besturings elementen voor weer gave (indeling)](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md) Hiermee geeft u een set .NET-typen op die gebruikmaken van deze definitie van het besturings element. Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.

[SelectionSetName-element voor EntrySelectedBy voor CustomEntry (indeling)](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md) Hiermee geeft u een set .NET-objecten voor de lijst vermelding op. Er is geen limiet voor het aantal selectie sets dat voor een vermelding kan worden opgegeven.

[SelectionSetName-element voor EntrySelectedBy voor EnumerableExpansion (indeling)](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md) Hiermee geeft u de set .NET-typen op die door deze definitie worden uitgebreid.

[SelectionSetName-element voor EntrySelectedBy voor GroupBy (indeling)](./selectionsetname-element-for-entryselectedby-for-groupby-format.md) Hiermee geeft u een set .NET-objecten voor de lijst vermelding op. Er is geen limiet voor het aantal selectie sets dat voor een vermelding kan worden opgegeven. Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.

[SelectionSetName-element voor EntrySelectedBy voor List entry (indeling)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) Hiermee geeft u een set .NET-objecten voor de lijst vermelding op. Er is geen limiet voor het aantal selectie sets dat voor een vermelding kan worden opgegeven.

[SelectionSetName-element voor EntrySelectedBy voor TableRowEntry (indeling)](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md) Hiermee geeft u een set .NET-typen op die gebruikmaken van dit item van de tabel weergave. Er is geen limiet voor het aantal selectie sets dat voor een vermelding kan worden opgegeven.

[SelectionSetName-element voor EntrySelectedBy voor WideEntry (indeling)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md) Hiermee geeft u een set .NET-objecten voor de definitie op. De definitie wordt gebruikt wanneer een van deze objecten wordt weer gegeven.

[SelectionSetName-element voor SelectionCondition voor besturings elementen voor configuratie (indeling)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md) Hiermee geeft u de set .NET-typen op waarmee de voor waarde wordt geactiveerd. Wanneer een van de typen in deze set aanwezig is, wordt aan de voor waarde voldaan en wordt het object weer gegeven met behulp van dit besturings element. Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.

[SelectionSetName-element voor SelectionCondition voor besturings elementen voor weer gave (indeling)](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md) Hiermee geeft u de set .NET-typen op waarmee de voor waarde wordt geactiveerd. Wanneer een van de typen in deze set aanwezig is, wordt aan de voor waarde voldaan en wordt het object met dit besturings element weer gegeven. Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.

[EntrySelectedBy-element voor CustomEntry voor weer gave (indeling)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md) Hiermee geeft u de set .NET-typen op waarmee de voor waarde wordt geactiveerd. Wanneer een van de typen in deze set aanwezig is, wordt aan de voor waarde voldaan en wordt het object met dit besturings element weer gegeven. Dit element wordt gebruikt bij het definiëren van een aangepaste beheer weergave.

[SelectionSetName-element voor SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (indeling)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md) Hiermee geeft u de set .NET-typen op waarmee de voor waarde wordt geactiveerd. Wanneer een van de typen in deze set aanwezig is, wordt voldaan aan de voor waarde.

[SelectionSetName-element voor SelectionCondition voor GroupBy (indeling)](./selectionsetname-element-for-selectioncondition-for-groupby-format.md) Hiermee geeft u de set .NET-typen op waarmee de voor waarde wordt geactiveerd. Wanneer een van de typen in deze set aanwezig is, wordt aan de voor waarde voldaan en wordt het object weer gegeven met behulp van dit besturings element. Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.

[SelectionSetName-element voor SelectionCondition voor EntrySelectedBy voor List entry (indeling)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md) Hiermee geeft u de set .NET-typen op waarmee de voor waarde wordt geactiveerd. Wanneer een van de typen in deze set aanwezig is, wordt aan de voor waarde voldaan en wordt het object weer gegeven met behulp van deze definitie van de lijst weergave.

[SelectionSetName-element voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (indeling)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md) Hiermee geeft u de set .NET-typen op waarmee de voor waarde wordt geactiveerd. Wanneer een van de typen in deze set aanwezig is, wordt aan de voor waarde voldaan en wordt het object weer gegeven met behulp van deze definitie van de tabel weergave.

[SelectionSetName-element voor SelectionCondition voor EntrySelectedBy voor WideEntry (indeling)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md) Hiermee geeft u de set .NET-typen op waarmee de voor waarde wordt geactiveerd. Wanneer een van de typen in deze set aanwezig is, wordt aan de voor waarde voldaan en wordt het object weer gegeven met behulp van deze definitie van de brede weer gave.

[SelectionSetName-element voor ViewSelectedBy (indeling)](./selectionsetname-element-for-viewselectedby-format.md) Hiermee geeft u een set .NET-objecten op die worden weer gegeven in de weer gave.

[SelectionSets-element (indeling)](./selectionsets-element-format.md) Hiermee worden de sets .NET-objecten gedefinieerd die kunnen worden gebruikt door afzonderlijke opmaak weergaven.

[Show error-element (indeling)](./showerror-element-format.md) Hiermee geeft u op dat de volledige fout record wordt weer gegeven als er een fout optreedt bij het weer geven van een stukje gegevens.

[TableColumnHeader-element voor TableHeaders voor TableControl (indeling)](./tablecolumnheader-element-format.md) Hiermee definieert u het label, de breedte van de kolom en de uitlijning van het label voor een kolom van de tabel.

[TableColumnItem-element (indeling)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) Hiermee wordt de eigenschap of het script gedefinieerd waarvan de waarde wordt weer gegeven in de kolom van de rij.

[TableColumnItems-element (indeling)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) Hiermee worden de eigenschappen of scripts gedefinieerd waarvan de waarden worden weer gegeven in de rij.

[TableControl-element (indeling)](./tablecontrol-element-format.md) Definieert een tabel indeling voor een weer gave.

[TableHeaders-element (indeling)](./tableheaders-element-format.md) Hiermee worden de kopteksten van de kolommen van een tabel gedefinieerd.

[TableRowEntries-element (indeling)](./tablerowentries-element-for-tablecontrol-format.md) Hiermee worden de rijen van de tabel gedefinieerd.

[TableRowEntry-element (indeling)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md) Hiermee worden de gegevens gedefinieerd die worden weer gegeven in een rij van de tabel.

[Tekst element voor CustomItem voor besturings elementen voor configuratie (indeling)](./text-element-for-customitem-for-controls-for-configuration-format.md) Hiermee geeft u tekst op die wordt toegevoegd aan de gegevens die worden weer gegeven door het besturings element, zoals een label, haakjes om de gegevens op te nemen en spaties om de gegevens te laten inspringen. Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.

[Tekst element voor CustomItem voor besturings elementen voor weer gave (indeling)](./text-element-for-customitem-for-controls-for-view-format.md) Hiermee geeft u tekst op die wordt toegevoegd aan de gegevens die worden weer gegeven door het besturings element, zoals een label, haakjes om de gegevens op te nemen en spaties om de gegevens te laten inspringen. Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.

[Tekst element voor CustomItem (indeling)](./text-element-for-customitem-for-customview-for-view-format.md) Hiermee geeft u tekst op die wordt toegevoegd aan de gegevens die worden weer gegeven door het besturings element, zoals een label, haakjes om de gegevens op te nemen en spaties om de gegevens te laten inspringen. Dit element wordt gebruikt bij het definiëren van een aangepaste beheer weergave.

[Tekst element voor CustomItem voor GroupBy (indeling)](./text-element-for-customitem-for-groupby-format.md) Hiermee geeft u tekst op die wordt toegevoegd aan de gegevens die worden weer gegeven door het besturings element, zoals een label, haakjes om de gegevens op te nemen en spaties om de gegevens te laten inspringen. Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.

[TypeName-element voor EntrySelectedBy voor besturings elementen voor configuratie (indeling)](./typename-element-for-entryselectedby-for-controls-for-configuration-format.md) Hiermee geeft u een .NET-type op dat gebruikmaakt van deze definitie van het besturings element. Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.

[TypeName-element voor EntrySelectedBy voor besturings elementen voor weer gave (indeling)](./typename-element-for-entryselectedby-for-controls-for-view-format.md) Hiermee geeft u een .NET-type op dat gebruikmaakt van deze definitie van het besturings element. Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.

[TypeName-element voor EntrySelectedBy voor CustomEntry voor weer gave (indeling)](./typename-element-for-entryselectedby-for-customentry-for-view-format.md) Hiermee geeft u een .NET-type op dat gebruikmaakt van deze definitie van de aangepaste beheer weergave. Er is geen limiet voor het aantal typen dat voor een definitie kan worden opgegeven.

[TypeName-element voor EntrySelectedBy voor EnumerableExpansion (indeling)](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md) Hiermee geeft u een .NET-type op dat is uitgevouwen door deze definitie. Dit element wordt gebruikt bij het definiëren van een standaard instelling.

[TypeName-element voor EntrySelectedBy voor GroupBy (indeling)](./typename-element-for-entryselectedby-for-groupby-format.md) Hiermee geeft u een .NET-type op dat gebruikmaakt van deze definitie van het aangepaste besturings element. Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.

[TypeName-element voor EntrySelectedBy voor ListControl (indeling)](./typename-element-for-entryselectedby-for-listcontrol-format.md) Hiermee geeft u een .NET-type op dat gebruikmaakt van dit item van de lijst weergave. Er is geen limiet voor het aantal typen dat kan worden opgegeven voor een vermelding in de lijst.

[TypeName-element voor EntrySelectedBy voor TableRowEntry (indeling)](./typename-element-for-entryselectedby-for-tablecontrol-format.md) Hiermee geeft u een .NET-type op dat gebruikmaakt van dit item van de tabel weergave. Er is geen limiet voor het aantal typen dat voor een tabel vermelding kan worden opgegeven.

[TypeName-element voor EntrySelectedBy voor WideEntry (indeling)](./typename-element-for-entryselectedby-for-wideentry-format.md) Hiermee geeft u een .NET-type voor de definitie op. De definitie wordt gebruikt wanneer dit object wordt weer gegeven.

[TypeName-element voor SelectionCondition voor besturings elementen voor configuratie (indeling)](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md) Hiermee geeft u een .NET-type op waarmee de voor waarde wordt geactiveerd. Dit element wordt gebruikt bij het definiëren van een algemeen besturings element dat kan worden gebruikt door alle weer gaven in het opmaak bestand.

[TypeName-element voor SelectionCondition voor besturings elementen voor weer gave (indeling)](./typename-element-for-selectioncondition-for-controls-for-view-format.md) Hiermee geeft u een .NET-type op waarmee de voor waarde wordt geactiveerd. Dit element wordt gebruikt bij het definiëren van besturings elementen die kunnen worden gebruikt door een weer gave.

[TypeName-element voor SelectionCondition voor CustomControl voor weer gave (indeling)](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md) Hiermee geeft u een .NET-type op waarmee de voor waarde wordt geactiveerd. Dit element wordt gebruikt bij het definiëren van een aangepaste beheer weergave.

[TypeName-element voor SelectionCondition voor EntrySelectedBy voor EnumerableExpansion (indeling)](./typename-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md) Hiermee geeft u een .NET-type op waarmee de voor waarde wordt geactiveerd.

[TypeName-element voor SelectionCondition voor GroupBy (indeling)](./typename-element-for-selectioncondition-for-groupby-format.md) Hiermee geeft u een .NET-type op waarmee de voor waarde wordt geactiveerd. Dit element wordt gebruikt bij het definiëren van de manier waarop een nieuwe groep objecten wordt weer gegeven.

[TypeName-element voor SelectionCondition voor EntrySelectedBy voor ListControl (indeling)](./typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md) Hiermee geeft u een .NET-type op waarmee de voor waarde wordt geactiveerd. Wanneer dit type aanwezig is, wordt de vermelding in de lijst gebruikt.

[TypeName-element voor SelectionCondition voor EntrySelectedBy voor TableRowEntry (indeling)](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md) Hiermee geeft u een .NET-type op waarmee de voor waarde wordt geactiveerd. Wanneer dit type aanwezig is, wordt voldaan aan de voor waarde en wordt de tabelrij gebruikt.

[TypeName-element voor SelectionCondition voor EntrySelectedBy voor WideEntry (indeling)](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md) Hiermee geeft u een .NET-type op waarmee de voor waarde wordt geactiveerd. Wanneer dit type aanwezig is, wordt de definitie gebruikt.

[TypeName-element voor typen (indeling)](./typename-element-for-types-format.md) Hiermee geeft u het .NET-type op van een object dat tot de selectieset behoort.

[TypeName-element voor ViewSelectedBy (indeling)](./typename-element-for-viewselectedby-format.md) Hiermee geeft u een .NET-object op dat wordt weer gegeven in de weer gave.

[Type-element (indeling)](./types-element-for-selectionset-format.md) Hiermee definieert u de .NET-objecten die zich in de selectieset bevinden.

[Element weer geven (indeling)](./view-element-format.md) Hiermee wordt een weer gave gedefinieerd die wordt gebruikt om een of meer .NET-objecten weer te geven.

[ViewDefinitions-element (indeling)](./viewdefinitions-element-format.md) Hiermee worden de weer gaven gedefinieerd waarmee objecten worden weer gegeven.

[ViewSelectedBy-element (indeling)](./viewselectedby-element-format.md) Hiermee worden de .NET-objecten gedefinieerd die worden weer gegeven in de weer gave.

[WideControl-element (indeling)](./widecontrol-element-format.md) Hiermee wordt een brede lijst indeling (enkelvoudige waarde) gedefinieerd voor de weer gave. In deze weer gave wordt één eigenschaps waarde of script waarde voor elk object weer gegeven.

[WideEntries-element (indeling)](./wideentries-element-for-widecontrol-format.md) Biedt de definities van de brede weer gave. In de brede weer gave moeten een of meer definities worden opgegeven.

[WideEntry-element (indeling)](./wideentry-element-for-widecontrol-format.md) Biedt een definitie van de brede weer gave.

[WideItem-element (indeling)](./wideitem-element-for-widecontrol-format.md) Hiermee wordt de eigenschap of het script gedefinieerd waarvan de waarde wordt weer gegeven.

[Width-element (indeling)](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) Hiermee wordt de breedte (in tekens) van een kolom gedefinieerd.

[Omloop element (indeling)](./wrap-element-for-tablerowentry-for-tablecontrol-format.md) Geeft aan dat de tekst die de kolom breedte overschrijdt wordt weer gegeven op de volgende regel.

[WrapTables-element (indeling)](./wraptables-element-format.md) Geeft aan dat de gegevens in een tabelcel worden verplaatst naar de volgende regel als de gegevens langer zijn dan de kolom breedte.

## <a name="see-also"></a>Zie ook

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
