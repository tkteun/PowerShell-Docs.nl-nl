---
title: De manier waarop we problemen beheren
description: In dit artikel wordt uitgelegd hoe het Power shell-docs-team pull-aanvragen beheert.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 018200f1a9384f1ea956c9b27a7605db21f2da9e
ms.sourcegitcommit: 17d798a041851382b406ed789097843faf37692d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83692528"
---
# <a name="how-we-manage-issues"></a>De manier waarop we problemen beheren

In dit artikel wordt beschreven hoe we problemen beheren in de Power shell-docs opslag plaats. Dit artikel is bedoeld als taak hulp voor leden van het Power shell-docs-team. Dit wordt hier gepubliceerd om proces transparantie te bieden voor de open bare mede werkers.

## <a name="sources-of-issues"></a>Bronnen van problemen

- Community-inzenders
- Interne inzenders
- Transcripties van opmerkingen van sociale-media kanalen
- Feedback via het formulier docs feedback

## <a name="response-time-targets"></a>Doelen voor reactie tijd

- Ingedeeld-5 werk dagen
- Repareren of wijzigen-geen specifieke doel stelling alleen beste

### <a name="labeling--milestones"></a>Labels & mijl palen

#### <a name="label-types"></a>Label typen

|Voorvoegsel  | Beschrijving                                                         |
|------- | --------------------------------------------------------------------|
|Gebied    | Wordt gebruikt om aan te geven welk gedeelte van Power shell of welke docs het probleem ondervindt.<br>Deze optie is handig voor eigen aars om problemen voor hun functie te vinden.|
|Pri     | Wordt gebruikt om de prioriteit van het probleem aan te geven. Waarde bereik 0-4.        |
|Probleem   | Hiermee wordt het type feedback voor het probleem geclassificeerd                     |
|Beoordelen  | Gebruikt voor een probleem waarvoor verdere beoordeling door het team is vereist              |
|Status  | Wordt gebruikt om de status van het werk item aan te geven                        |
|Wachten | Wordt gebruikt om aan te geven dat wij wachten op iets                   |

#### <a name="milestones"></a>Milestones

Problemen en pull moeten worden gelabeld met de juiste mijl paal. Als het probleem niet is gericht op een specifieke versie, wordt er geen mijl paal gebruikt. Problemen voor docs pull die nog moeten worden samengevoegd met de Power shell-code basis, moeten worden toegewezen aan de **toekomstige** mijl paal. Nadat de code wijziging is samengevoegd, wijzigt u de mijl paal naar de juiste versie.

|    Mijlpalen     |                    Beschrijving                     |
| ---------------- | -------------------------------------------------- |
| 6.x              | Werk items met betrekking tot Power shell 6,0 t/m 6.2. x |
| 7.0.0            | Werk items met betrekking tot Power shell 7,0               |
| 7.1.0            | Werk items met betrekking tot Power shell 7,1               |
| Toekomstig           | Werk items een toekomstige versie van Power shell          |
| PSReadline-vNext | Werk items een toekomstige versie van PSReadline          |

## <a name="triage-process"></a>Sorteren-proces

Het Power shell docs-team voldoet slechts één keer per week voor het bespreken van problemen die zijn toegevoegd sinds de laatste vergadering. Een probleem wordt beschouwd als ingedeeld wanneer er labels zijn toegewezen of als er een eigenaar is toegewezen. Team leden van Power shell-documenten worden aangemoedigd de problemen dagelijks te bekijken en nieuwe problemen op te lossen wanneer ze binnenkomen. De wekelijkse sorteren-vergadering kan vervolgens worden gebruikt om de nieuwe problemen zo nodig te bespreken.

### <a name="misplaced-product-feedback"></a>Verkeerd geplaatste product feedback

- Voer een opmerking in voor de klant die aangeeft dat het product feedback is en geef een koppeling naar het juiste feedback kanaal op.
- Optioneel: Kopieer het probleem naar de juiste locatie van de product feedback, voeg een koppeling naar het gekopieerde item toe en sluit het probleem. GEEN problemen naar UserVoice kopiëren.

  | DocSet    | URL van product feedback                                           |
  | --------- | -------------------------------------------------------------- |
  | ontwikkelaar | `https://github.com/PowerShell/PowerShell/issues/new/choose`   |
  | DSC       | `https://windowsserver.uservoice.com/forums/301869-powershell` |
  | galerie   | `https://github.com/powershell/powershellgallery/issues/new`   |
  | JEA       | `https://github.com/powershell/jea/issues/new`                 |
  | referentielaag | `https://github.com/PowerShell/PowerShell/issues/new/choose`   |
  | WMF       | `https://windowsserver.uservoice.com/forums/301869-powershell` |

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
- Elk exemplaar van dit moet worden besproken in de wekelijkse sorteren om te bepalen of verdere actie moet worden ondernomen (rapporteren aan GitHub of micro soft juridisch).
