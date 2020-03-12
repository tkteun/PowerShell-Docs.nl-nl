---
title: Hoe we problemen beheren
description: In dit artikel wordt uitgelegd hoe het Power shell-docs-team pull-aanvragen beheert.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: cd7aba83d42a6a2eba1ce73910fdd34096342c21
ms.sourcegitcommit: 18d832858a7b8ea094763afa753e0f48f01372e7
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/10/2020
ms.locfileid: "79078533"
---
# <a name="how-we-manage-issues"></a>Hoe we problemen beheren

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

|Beleids  | Beschrijving                                                         |
|------- | --------------------------------------------------------------------|
|Onderwerp    | Wordt gebruikt om aan te geven welk gedeelte van Power shell of welke docs het probleem ondervindt.<br>Deze optie is handig voor eigen aars om problemen voor hun functie te vinden.|
|Pri     | Wordt gebruikt om de prioriteit van het probleem aan te geven. Waarde bereik 0-4.        |
|Probleem   | Hiermee wordt het type feedback voor het probleem geclassificeerd                     |
|Beoordelen  | Gebruikt voor een probleem waarvoor verdere beoordeling door het team is vereist              |
|Status  | Wordt gebruikt om de status van het werk item aan te geven                        |
|Wachten | Wordt gebruikt om aan te geven dat wij wachten op iets                   |

#### <a name="milestones"></a>Mijl palen

Problemen en pull moeten worden gelabeld met de juiste mijl paal. Als het probleem niet is gericht op een specifieke versie, wordt er geen mijl paal gebruikt. Problemen voor docs pull die nog moeten worden samengevoegd met de Power shell-code basis, moeten worden toegewezen aan de **toekomstige** mijl paal. Nadat de code wijziging is samengevoegd, wijzigt u de mijl paal naar de juiste versie.

|    Mijlpalen     |                    Beschrijving                     |
| ---------------- | -------------------------------------------------- |
| 6.x              | Werk items met betrekking tot Power shell 6,0 t/m 6.2. x |
| 7.0.0            | Werk items met betrekking tot Power shell 7,0               |
| 7.1.0            | Werk items met betrekking tot Power shell 7,1               |
| toekomstig           | Werk items een toekomstige versie van Power shell          |
| PSReadline-vNext | Werk items een toekomstige versie van PSReadline          |

## <a name="triage-process"></a>Sorteren-proces

Het Power shell docs-team voldoet slechts één keer per week voor het bespreken van problemen die zijn toegevoegd sinds de laatste vergadering. Een probleem wordt beschouwd als ingedeeld wanneer er labels zijn toegewezen of als er een eigenaar is toegewezen. Team leden van Power shell-documenten worden aangemoedigd de problemen dagelijks te bekijken en nieuwe problemen op te lossen wanneer ze binnenkomen. De wekelijkse sorteren-vergadering kan vervolgens worden gebruikt om de nieuwe problemen zo nodig te bespreken.

### <a name="misplaced-product-feedback"></a>Verkeerd geplaatste product feedback

- Voer een opmerking in voor de klant die aangeeft dat het product feedback is en geef een koppeling naar het juiste feedback kanaal op.
- Optioneel: Kopieer het probleem naar de juiste locatie van de product feedback, voeg een koppeling naar het gekopieerde item toe en sluit het probleem. GEEN problemen naar UserVoice kopiëren.

  | DocSet    | URL van product feedback                                         |
  | --------- | ------------------------------------------------------------ |
  | Developer | https://github.com/PowerShell/PowerShell/issues/new/choose   |
  | dsc       | https://windowsserver.uservoice.com/forums/301869-powershell |
  | sjablonen   | https://github.com/powershell/powershellgallery/issues/new   |
  | JEA       | https://github.com/powershell/jea/issues/new                 |
  | Verwijzing | https://github.com/PowerShell/PowerShell/issues/new/choose   |
  | WMF       | https://windowsserver.uservoice.com/forums/301869-powershell |

### <a name="support-requests"></a>Ondersteunings aanvragen

- Als de vraag van de ondersteuning eenvoudig is, beantwoordt u deze en sluit u het probleem.
- Als de vraag gecompliceerder is, of als de indiener antwoordt met meer vragen, stuurt u deze om naar forums en ondersteunings kanalen. Voorgestelde tekst voor omleiding naar forums:

    > Dit is niet het juiste forum voor dit soort vragen. Probeer uw vraag te plaatsen in een forum Community-ondersteuning. Zie https://docs.microsoft.com/powershell/scripting/community/community-support voor een lijst met community-forums.

### <a name="code-of-conduct-violations"></a>Gedrags code schendingen

- Bewerk het probleem zo nodig om eventuele aanstootgevende inhoud te verwijderen.
- Voer een opmerking in om aan te geven dat het probleem spam is, sluit het probleem en vergrendel het vervolgens om verdere opmerkingen te voor komen.
- Elk exemplaar van dit moet worden besproken in de wekelijkse sorteren om te bepalen of verdere actie moet worden ondernomen (rapporteren aan GitHub of micro soft juridisch).
