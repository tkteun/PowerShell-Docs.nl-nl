---
title: Pull-aanvragen verzenden
description: In dit artikel wordt uitgelegd hoe u pull-aanvragen verzendt naar de PowerShell-Docs opslag plaats.
ms.date: 12/09/2020
ms.topic: conceptual
ms.openlocfilehash: 1a21c25e19189aec4f48ad034147b02f4f804f9d
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "97090213"
---
# <a name="how-to-submit-pull-requests"></a>Pull-aanvragen verzenden

Als u inhoud wilt wijzigen, moet u een pull-aanvraag (PR) bij uw Fork indienen. Een pull-aanvraag moet worden gecontroleerd voordat deze kan worden samengevoegd. Voor de beste resultaten raadpleegt u de [controle lijst voor redactionele](editorial-checklist.md) voordat u uw pull-aanvraag indient.

## <a name="using-git-branches"></a>Git-vertakkingen gebruiken

De standaard vertakking voor PowerShell-Docs is de `staging` vertakking. Wijzigingen die zijn aangebracht in werk vertakkingen worden samengevoegd in de `staging` vertakking voordat ze worden gepubliceerd. De `staging` vertakking wordt `live` elke weekdag in de vertakking samengevoegd om 3:00 uur (Pacific Time). De `live` vertakking bevat de inhoud die wordt gepubliceerd op docs.Microsoft.com.

Voordat u wijzigingen start, maakt u een werk vertakking in uw lokale kopie van de PowerShell-Docs-opslag plaats. Als u lokaal werkt, moet u uw lokale opslag plaats synchroniseren voordat u uw werk vertakking maakt. De werk vertakking moet worden gemaakt op basis van een update-to-date kopie van de `staging` vertakking.

Alle pull-aanvragen moeten gericht zijn op de `staging` vertakking. Verzend de wijziging niet naar de `live` vertakking.
Wijzigingen die in de `staging` vertakking zijn aangebracht, worden samengevoegd in `live` , waarbij wijzigingen in worden overschreven `live` .

## <a name="make-the-pull-request-process-work-better-for-everyone"></a>Het proces voor pull-aanvragen voor iedereen beter laten werken

Het eenvoudiger en gerichter u kunt uw PR maken, des te sneller kan deze worden gecontroleerd en samengevoegd.

### <a name="avoid-pull-requests-that-update-large-numbers-of-files-or-contain-unrelated-changes"></a>Pull-aanvragen voor komen die een groot aantal bestanden bijwerken of niet-gerelateerde wijzigingen bevatten

Vermijd het maken van pull die niet-gerelateerde wijzigingen bevatten. Scheid kleine updates aan bestaande artikelen van nieuwe artikelen of artikelen die grotendeels zijn herschreven. Behandel deze wijzigingen in aparte werkstromen.

Bulk wijzigingen maken pull met een groot aantal gewijzigde bestanden. Beperk uw pull-aanvragen tot maximaal 50 gewijzigde bestanden. Grote pull-aanvragen zijn moeilijk te controleren en gevoeliger voor fouten.

### <a name="renaming-or-deleting-files"></a>Bestanden een andere naam geven of verwijderen

Bij het wijzigen van de naam of het verwijderen van bestanden moet er een probleem zijn dat is gekoppeld aan de PR. Dit probleem moet betrekking hebben op de nood zaak om de bestanden een andere naam te geven of te verwijderen.

Vermijd het combi neren van inhouds toevoegingen of wijziging van het wijzigen van de naam en het verwijderen van bestanden. Elk bestand waarvan de naam wordt gewijzigd of verwijderd, moet worden toegevoegd aan het globale omleidings bestand. Als dat mogelijk is, werkt u de bestanden bij die zijn gekoppeld aan de hernoemde of verwijderde inhoud, inclusief eventuele inhoudsopgave bestanden.

## <a name="docs-pr-validation-service"></a>Docs PR-validatieservice

De docs PR-validatie service is een GitHub-app waarmee validatie regels worden uitgevoerd op uw wijzigingen. U moet eventuele fouten of waarschuwingen die zijn gerapporteerd door de validatie service corrigeren.

U ziet het volgende gedrag:

1. U dient een PR in.
1. In de GitHub-opmerking die de status van uw PR aangeeft, ziet u de status ' controles ' die zijn ingeschakeld voor de opslag plaats. In dit voor beeld zijn er twee controles ingeschakeld, ' commit-validatie ' en ' openpublishing. build ':

   ![validatie status-sommige controles zijn mislukt](media/pull-requests/validation-failed.png)

   De build kan worden door gegeven, zelfs als de commit-validatie is mislukt.

1. Klik op **Details** voor meer informatie.
1. Op de pagina Details ziet u alle validatiecontroles die zijn mislukt, met informatie over wat u moet doen om de problemen op te lossen.
1. Als de validatie slaagt, wordt de volgende opmerking toegevoegd aan de pull-aanvraag:

   ![Validatie status: geslaagd](media/pull-requests/build-validation.png)

> [!NOTE]
> Als u een externe mede werker (niet een micro soft-mede werker) bent, hebt u geen toegang tot de gedetailleerde rapporten van de build of de preview-koppelingen.

Wanneer de PR wordt gecontroleerd, wordt u mogelijk gevraagd om wijzigingen aan te brengen of validatie waarschuwings berichten op te lossen. Het PowerShell-Docs-team kan u helpen bij het begrijpen van validatie fouten en redactionele vereisten.

## <a name="next-steps"></a>Volgende stappen

[Stijlgids voor PowerShell-documentatie](powershell-style-guide.md)

## <a name="additional-resources"></a>Aanvullende resources

[De manier waarop we pull-aanvragen beheren](managing-pull-requests.md)

<!--link refs-->
[fork]: /contribute/get-started-setup-local#fork-the-repository
