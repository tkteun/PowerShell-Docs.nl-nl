---
title: Verwijzings artikelen bewerken
description: In dit artikel worden de specifieke vereisten beschreven voor het bewerken van cmdlet-verwijzingen en over onderwerpen in de Power shell-documentatie.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 3c6f1b4fc27ca8ece7ec30317daf4ed2a6bc9228
ms.sourcegitcommit: 18d832858a7b8ea094763afa753e0f48f01372e7
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/10/2020
ms.locfileid: "79078568"
---
# <a name="editing-reference-articles"></a>Verwijzings artikelen bewerken

De cmdlet-referentie artikelen hebben een specifieke structuur. Deze structuur wordt gedefinieerd door [PlatyPS][].
PlatyPS genereert de cmdlet-Help voor Power shell-modules in korting. Nadat de bestanden voor de verlaging zijn bewerkt, wordt PlatyPS gebruikt om de MAML-Help bestanden te maken die worden gebruikt door de `Get-Help`-cmdlet.

PlatyPS heeft een in code vastgelegd schema voor cmdlet-verwijzingen die in de code zijn geschreven. Het [platyPS.schema.MD][] -document probeert deze structuur te beschrijven. Schema schendingen veroorzaken compilatie fouten die moeten worden opgelost voordat we uw bijdrage kunnen accepteren.

## <a name="general-guidelines"></a>Algemene richtlijnen

- Verwijder geen koptekst structuren. PlatyPS verwacht een specifieke set kopteksten.
- Het **invoer type** en de headers van het **uitvoer type** moeten een type hebben. Als de cmdlet geen invoer heeft of een waarde retourneert, gebruikt u de waarde `None`.
- Geomheiningde code blokken zijn alleen toegestaan in de sectie [voor beelden](#structuring-examples) .
- Inline code reeksen kunnen worden gebruikt in een wille keurige alinea.

## <a name="formatting-about_-files"></a>About_ bestanden Format teren

`About_*`-bestanden worden nu verwerkt door [pandoc][]in plaats van PlatyPS. `About_*` bestanden zijn ingedeeld voor de beste compatibiliteit tussen alle versies van Power shell en met de hulpprogram ma's voor publiceren.

Richt lijnen voor basis opmaak:

- Regels beperken tot 80 tekens
- Code blokken en tabellen zijn beperkt tot 76 tekens omdat pandoc deze met vier spaties inspringt tijdens de conversie naar tekst zonder opmaak
- Tabellen moeten binnen 76 tekens passen
  - Hand matig inhoud van cellen op meerdere regels laten teruglopen
  - `|` tekens openen en sluiten op elke regel gebruiken
  - Een werk voorbeeld in [about_Comparison_Operators][about-example] weer geven
- Pandoc speciale tekens gebruiken `\`,`$`en `<`
  - In een koptekst-deze tekens moeten worden voorafgegaan door een voorloop `\` teken of worden inge sloten in accents graves (`` ` ``)
  - In een alinea moeten deze tekens in code reeksen worden geplaatst. Bijvoorbeeld:

    ~~~markdown
    ### The purpose of the \$foo variable

    The `$foo` variable is used to store ...
    ~~~

## <a name="structuring-examples"></a>Voor beelden van structureren

In het PlatyPS-schema is de **voor** beeld-header een H2-kop en elk voor beeld is een H3-header.

Binnen een voor beeld staat het schema niet toe dat code blokken worden gescheiden door alinea's. Het ondersteunde schema is:

```
### Example #X title

0 or more paragraphs
1 or more code blocks
0 or more paragraphs.
```

Nummer elk voor beeld en voeg een korte titel toe.

Bijvoorbeeld:

### <a name="example-1-get-cmdlets-functions-and-aliases"></a>Voor beeld 1: cmdlets, functies en aliassen ophalen

Met deze opdracht worden de Power shell-cmdlets, functies en aliassen opgehaald die op de computer zijn geïnstalleerd.

```powershell
Get-Command
```

### <a name="example-2-get-commands-in-the-current-session"></a>Voor beeld 2: opdrachten in de huidige sessie ophalen

```powershell
Get-Command -ListImported
```

## <a name="next-steps"></a>Volgende stappen

[Controle lijst voor redactionele](editorial-checklist.md)

<!-- link references -->
[PlatyPS]: https://github.com/powershell/platyps
[platyPS.schema.md]: https://github.com/PowerShell/platyPS/blob/master/platyPS.schema.md
[issue1806]: https://github.com/MicrosoftDocs/PowerShell-Docs/issues/1806
[about-example]: https://github.com/MicrosoftDocs/PowerShell-Docs/reference/5.1/Microsoft.PowerShell.Core/About/about_Comparison_Operators.md
[Pandoc]: https://pandoc.org
