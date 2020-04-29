---
title: Verwijzings artikelen bewerken
description: In dit artikel worden de specifieke vereisten beschreven voor het bewerken van cmdlet-verwijzingen en over onderwerpen in de Power shell-documentatie.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: e135f6cc81ba7537a535a08421e1ca9b2b2af573
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81624768"
---
# <a name="editing-reference-articles"></a>Verwijzings artikelen bewerken

Artikelen met naslaginformatie voor cmdlets hebben een specifieke structuur. Deze structuur wordt gedefinieerd door [PlatyPS][].
PlatyPS genereert de cmdlet-Help voor Power shell-modules in korting. Nadat de Markdown-bestanden zijn bewerkt, wordt PlatyPS gebruikt om de MAML-helpbestanden te maken die door de `Get-Help`-cmdlet worden gebruikt.

In PlatyPS is een in code vastgelegd schema voor cmdlet-naslaginformatie. Dit schema is in de code geschreven. In het document [platyPS. schema.md][] is deze structuur beschreven. Schendingen van het schema veroorzaken compilatiefouten die moeten worden opgelost voordat we uw bijdrage kunnen accepteren.

## <a name="general-guidelines"></a>Algemene richtlijnen

- Verwijder geen koptekststructuren. PlatyPS verwacht een specifieke reeks kopteksten.
- De kopteksten **Inputtype ** en **Outputtype ** moeten een type hebben. Als de cmdlet geen invoer heeft of een waarde retourneert, gebruikt u de waarde `None`.
- Afgebakende codeblokken zijn alleen toegestaan in de sectie [Voorbeelden](#structuring-examples).
- In elke alinea kunnen inline codereeksen worden gebruikt.

## <a name="formatting-about_-files"></a>About_-bestanden opmaken

`About_*`bestanden worden in korting geschreven, maar worden als tekst bestanden verzonden. We gebruiken [pandoc][] om de prijs verlaging te converteren naar platte tekst. `About_*`bestanden zijn ingedeeld voor de beste compatibiliteit tussen alle versies van Power shell en met de hulpprogram ma's voor publiceren.

Algemene richtlijnen voor het opmaken:

- Regels beperken tot 80 tekens. Met pandoc worden enkele prijsverlagings blokken Inge sprongen zodat dit blok moet worden aangepast.
  - Code blokken zijn beperkt tot 76 tekens
  - Tabellen zijn beperkt tot 76 tekens
  - Block Quotes (en waarschuwingen) zijn beperkt tot 78 tekens

- De speciale meta tekens `\`van pandoc gebruiken,`$`en`<`
  - In een koptekst-deze tekens moeten worden voorafgegaan door een voorloop `\` teken of worden inge sloten in code reeksen met behulp`` ` ``van accents graves ()
  - In een alinea moeten deze tekens in code reeksen worden geplaatst. Bijvoorbeeld:

    ~~~markdown
    ### The purpose of the \$foo variable

    The `$foo` variable is used to store ...
    ~~~

- Tabellen moeten binnen 76 tekens passen
  - Laat inhoud van cellen die over meerdere regels valt handmatig teruglopen
  - Gebruik op elke regel `|`-tekens voor openen en sluiten
  - In het volgende voor beeld ziet u hoe u een tabel op een juiste manier kunt samen stellen die informatie bevat die op meerdere regels in een cel inloopt.

    ~~~markdown
    ```
    |Operator|Description                |Example                          |
    |--------|---------------------------|---------------------------------|
    |`-is`   |Returns TRUE when the input|`(get-date) -is [DateTime]`      |
    |        |is an instance of the      |`True`                           |
    |        |specified .NET type.       |                                 |
    |`-isNot`|Returns TRUE when the input|`(get-date) -isNot [DateTime]`   |
    |        |not an instance of the     |`False`                          |
    |        |specified.NET type.        |                                 |
    |`-as`   |Converts the input to the  |`"5/7/07" -as [DateTime]`        |
    |        |specified .NET type.       |`Monday, May 7, 2007 12:00:00 AM`|
    ```
    ~~~

    > [!NOTE]
    > De limiet van 76 kolommen geldt alleen voor `About_*` onderwerpen. U kunt brede kolommen gebruiken in conceptuele of cmdlet-referentie artikelen.

## <a name="structuring-examples"></a>Voor beelden van structureren

In het PlatyPS-schema is de koptekst **VOORBEELDEN** een H2-kop en elk voorbeeld een H3-koptekst.

Het schema staat binnen een voorbeeld niet toe dat codeblokken worden gescheiden door alinea’s. Het ondersteunde schema is:

```
### Example #X title

0 or more paragraphs
1 or more code blocks
0 or more paragraphs.
```

Geef elk voorbeeld een nummer en voeg een korte titel toe.

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

[Redactionele controlelijst](editorial-checklist.md)

<!-- link references -->
[PlatyPS]: https://github.com/powershell/platyps
[platyPS.schema.md]: https://github.com/PowerShell/platyPS/blob/master/platyPS.schema.md
[issue1806]: https://github.com/MicrosoftDocs/PowerShell-Docs/issues/1806
[about-example]: /PowerShell/module/Microsoft.PowerShell.Core/About/about_Comparison_Operators
[Pandoc]: https://pandoc.org
