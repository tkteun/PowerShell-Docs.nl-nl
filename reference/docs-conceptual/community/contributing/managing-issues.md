---
title: De manier waarop we problemen beheren
description: In dit artikel wordt uitgelegd hoe het PowerShell-Docs-team problemen beheert.
ms.date: 12/09/2020
ms.topic: conceptual
ms.openlocfilehash: c6cb38bc37260b14e2a7c728879e2fa2a036133f
ms.sourcegitcommit: f6cc3752463b254f6ba7fc14c1e4532ad33f06bb
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/08/2021
ms.locfileid: "107216910"
---
# <a name="how-we-manage-issues"></a>De manier waarop we problemen beheren

In dit artikel wordt beschreven hoe we problemen beheren in de PowerShell-Docs opslag plaats. Dit artikel is bedoeld als taak hulp voor leden van het PowerShell-Docs team. Het wordt hier gepubliceerd om proces transparantie te bieden voor de open bare mede werkers.

## <a name="sources-of-issues"></a>Bronnen van problemen

- Community-inzenders
- Interne inzenders
- Transcripties van opmerkingen van sociale-media kanalen
- Feedback via het formulier docs feedback

## <a name="response-time-targets"></a>Doelen voor reactie tijd

80% van de nieuwe problemen zijn binnen drie werk dagen gesloten.

- Ingedeeld-1 werk dagen
- Herstellen of wijzigen-10 werk dagen

### <a name="labeling--milestones"></a>Labels & mijl palen

#### <a name="label-types"></a>Label typen

|   Type   | Description                                                         |
| -------- | ------------------------------------------------------------------- |
| Gebied     | Wordt gebruikt om aan te geven welk gedeelte van Power shell of welke docs het probleem ondervindt.<br>Deze optie is handig voor eigen aars om problemen voor hun functie te vinden. |
| Probleem    | Hiermee wordt het type probleem aangegeven                                         |
| Prioriteit | Hiermee wordt de prioriteit van het probleem aangegeven. Waardebereik 0 (hoog)-4 (laag)  |
| Status   | Hiermee wordt de status van het werk item aangegeven of de reden waarom deze is gesloten          |
| Tag      | Labels die worden gebruikt voor extra classificatie                        |
| Wachten  | Hiermee wordt aangegeven dat er wordt gewacht op iemand of een andere gebeurtenis         |

#### <a name="milestones"></a>Mijlpalen

Problemen en pull moeten worden gelabeld met de juiste mijl paal. Als het probleem niet van toepassing is op een specifieke versie, wordt er geen mijl paal gebruikt. Pull en gerelateerde problemen voor wijzigingen die nog moeten worden samengevoegd met de Power shell-code basis, moeten worden toegewezen aan de **toekomstige** mijl paal. Nadat de code wijziging is samengevoegd, wijzigt u de mijl paal naar de juiste versie.

|    Mijlpalen     |                    Description                     |
| ---------------- | -------------------------------------------------- |
| 7.0.0            | Werk items met betrekking tot Power shell 7,0               |
| 7.1.0            | Werk items met betrekking tot Power shell 7,1               |
| 7.2.0            | Werk items met betrekking tot Power shell 7,2               |
| Toekomstig           | Werk items een toekomstige versie van Power shell          |

## <a name="triage-process"></a>Sorteren-proces

Team leden van Power shell-docs bekijken de problemen dagelijks en sorteren nieuwe problemen wanneer ze binnenkomen. Het team voldoet aan de wekelijkse voor het bespreken van problemen die sorteren of onopgelost moeten blijven.

### <a name="misplaced-product-feedback"></a>Verkeerd geplaatste product feedback

- Voer een opmerking in die de klant omleidt naar het juiste feedback kanaal.
- Optioneel: Kopieer het probleem naar de juiste locatie van de product feedback, voeg een koppeling naar het gekopieerde item toe en sluit het probleem. GEEN problemen naar UserVoice kopiëren.

  De standaard locatie voor Power Shell-problemen is [https://github.com/PowerShell/PowerShell/issues/new/choose](https://github.com/PowerShell/PowerShell/issues/new/choose) .

  De volgende onderwerpgebieden hebben verschillende locaties voor problemen:

  | Onderwerpen |                                                     URL van product feedback                                                     |
  | -------- | ---------------------------------------------------------------------------------------------------------------------------- |
  | dsc      | [https://windowsserver.uservoice.com/forums/301869-powershell](https://windowsserver.uservoice.com/forums/301869-powershell) |
  | galerie  | [https://github.com/powershell/powershellgallery/issues/new](https://github.com/powershell/powershellgallery/issues/new)     |
  | WMF      | [https://windowsserver.uservoice.com/forums/301869-powershell](https://windowsserver.uservoice.com/forums/301869-powershell) |

### <a name="support-requests"></a>Ondersteuningsaanvragen

- Als de vraag van de ondersteuning eenvoudig is, beantwoordt u deze en sluit u het probleem.
- Als de vraag gecompliceerder is, of als de indiener antwoordt met meer vragen, stuurt u deze om naar forums en ondersteunings kanalen. Voorgestelde tekst voor omleiding naar forums:

  ```Markdown
  > This is not the right forum for these kinds of questions. Try posting your question in a
  > community support forum. For a list of community forums see:
  > https://docs.microsoft.com/powershell/scripting/community/community-support
  ```

### <a name="code-of-conduct-violations"></a>Gedrags code schendingen

- Bewerk het probleem zo nodig om eventuele aanstootgevende inhoud te verwijderen.
- Voer een opmerking in om aan te geven dat het probleem spam is, sluit het probleem en vergrendel het vervolgens om verdere opmerkingen te voor komen.
- Elke schending moet worden besproken in de wekelijkse sorteren om te bepalen of verdere actie moet worden ondernomen (rapporteren aan GitHub of micro soft juridisch).
