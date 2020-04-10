---
title: Controle lijst voor redactionele
description: Dit is een overzicht van de regels voor het bewerken van Power shell-documentatie.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 511e0c323e1a3256039e819d06f32f6e1ac42767
ms.sourcegitcommit: 18d832858a7b8ea094763afa753e0f48f01372e7
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/10/2020
ms.locfileid: "79078575"
---
# <a name="editors-checklist"></a>Controle lijst van de editor

Dit is een samen vatting van regels die moeten worden toegepast bij het schrijven van nieuwe of het bijwerken van bestaande artikelen. Zie andere artikelen in de hand leiding van de mede werker voor gedetailleerde uitleg en voor beelden van deze regels.

## <a name="metadata"></a>Metagegevens

- `ms.date`: moet de notatie **mm/dd/jjjj** hebben
  - De datum wijzigen wanneer er een belang rijke of feitelijke update is
    - Het artikel opnieuw ordenen
    - Feitelijke fouten oplossen
    - Nieuwe informatie toevoegen
  - Wijzig de datum niet als de update niet significant is
    - Typfouten en opmaak corrigeren
- `title`: een unieke teken reeks van 43-59 tekens inclusief spaties
  - Site-id niet toevoegen (deze wordt automatisch gegenereerd)
  - Gebruik een hoofd letter: alleen het eerste woord en eventuele eigen naam woorden
- `description`: 115-145 tekens inclusief spaties: deze abstract wordt weer gegeven in het Zoek resultaat

## <a name="formatting"></a>Opmaak

- Apostroffen-syntaxis elementen die worden weer gegeven, inline in een alinea
  - Cmdlet-namen `Verb-Noun`
  - Variabele `$counter`
  - Voor beelden van syntaxis `Verb-Noun -Parameter`
  - Bestands paden `C:\Program Files\PowerShell`, `/usr/bin/pwsh`
  - Url's die niet in het document kunnen worden geklikt
- Vet gebruiken voor eigenschapnamen, parameter waarden, parameter namen, klassen namen, module namen, namen van entiteiten, object-of type namen
  - Vet wordt gebruikt voor semantische opmaak, niet nadruk
  - Vet: sterretjes `**` gebruiken
- Cursief: onderstrepings `_` gebruiken
  - Alleen gebruikt voor nadruk, niet voor semantische opmaak
- Regel einden in 100 kolommen (of op 80 voor **about_Topics**)
- Geen harde tabbladen: alleen spaties gebruiken
- Geen Volg spaties op regels

### <a name="headers"></a>Headers

- H1 is in eerste instantie slechts één H1 per artikel
- Alleen [ATX-kopteksten](https://github.github.com/gfm/#atx-headings) gebruiken
- Gebruik een zin voor alle kopteksten
- Geen niveaus overs Laan: geen H3 zonder een H2
- Maximale diepte van H3 of H4
- Lege regel voor en na
- PlatyPS dwingt specifieke headers in het schema af-Voeg geen headers toe of verwijder deze

### <a name="code-blocks"></a>Code blokken

- Lege regel voor en na
- Gelabelde code Fences gebruiken- **Power shell**, **output**of een andere geschikte taal-id
- Niet-gecodeerde blokken met omheinings syntaxis of andere shells
- Plaats de **uitvoer** in een afzonderlijk code blok, met uitzonde ring van eenvoudige voor beelden waarin u niet van plan bent om de knop **kopiëren** te gebruiken voor de lezer
- Lijst met [ondersteunde talen](/contribute/code-in-docs#supported-languages) weer geven

### <a name="lists"></a>Lijsten

- Correct Inge sprongen
- Lege regel voor het eerste item en na het laatste item
- Bullet: use afbreek streepje (`-`) geen asterisk (`*`)-te eenvoudig te verwarren met nadruk
- Voor genummerde lijsten zijn alle cijfers ' 1 '.

## <a name="terminology"></a>Terminologie

- Power shell versus Windows Power shell versus Power shell core
- Zie [product terminologie](powershell-style-guide.md#product-terminology)

## <a name="cmdlet-reference-examples"></a>Naslag informatie voor cmdlets

- Er moet ten minste één voor beeld in de cmdlet-verwijzing zijn
- Voor beelden moeten net genoeg code zijn om het gebruik te demonstreren
- Power shell-syntaxis
  - Volledige namen van cmdlets en para meters gebruiken-geen aliassen
  - Splatting gebruiken voor para meters wanneer de opdracht regel te lang wordt
  - Vermijd het gebruik van regel voortzettings accents graves indien nodig
- De Power shell-prompt (`PS>`) verwijderen of vereenvoudigen, behalve wanneer dit nodig is voor het voor beeld
- Voor de cmdlet-referentie moet het volgende PlatyPS-schema worden gevolgd

  ~~~Markdown
  ### Example 1 - Descriptive title

  Zero or more short descriptive paragraphs explaining the context of the example followed by one or
  more code blocks. Recommend at least one and no more than two.

  ```powershell
  ... one or more PowerShell code statements ...
  ```

  ```Output
  Example output of the code above.
  ```

  Zero or more optional follow up paragraphs that explain the details of the code and output.
  ~~~

- Plaats geen alinea's tussen de code blokken. Alle beschrijvende inhoud moet vóór of na de code blokken komen.

## <a name="linking-to-other-documents"></a>Koppelen aan andere documenten

- Koppelen buiten de docset of tussen de cmdlet-verwijzing en de conceptuele
  - Relatieve Url's gebruiken bij het koppelen aan docs.microsoft.com (`https://docs.microsoft.com/en-us`verwijderen)
  - Land instellingen niet opnemen in Url's op Eigenschappen van micro soft (bijv. `/en-us` verwijderen uit URL)
  - Alle Url's naar externe websites moeten HTTPS gebruiken, tenzij dat niet geldig is voor de doel site
- Binnen docset
  - Koppeling naar bestandspad (bijvoorbeeld `../folder/file.md`)
  - Alle bestands paden gebruiken tekens voor voorwaartse slash (`/`)
- Afbeeldings koppelingen moeten unieke alternatieve tekst bevatten