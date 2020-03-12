---
title: Aan de slag met bijdragen aan Power shell-documentatie
description: Dit artikel bevat een overzicht van hoe u aan de slag kunt gaan als bijdrager aan de Power shell-documentatie.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 95eb2c3157a99fcb6560914da8464022e1b64fad
ms.sourcegitcommit: 18d832858a7b8ea094763afa753e0f48f01372e7
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/10/2020
ms.locfileid: "79078554"
---
# <a name="get-started-contributing-to-powershell-documentation"></a>Aan de slag met bijdragen aan Power shell-documentatie

Dit artikel bevat een overzicht van hoe u aan de slag kunt gaan als bijdrager aan de Power shell-documentatie.

## <a name="powershell-docs-structure"></a>Power shell-docs-structuur

De [Power shell-docs-opslag plaats][psdocs] is onderverdeeld in twee inhouds groepen. Git-vertakkingen worden gebruikt om te beheren hoe en wanneer documentatie wordt gepubliceerd.

### <a name="reference-content"></a>Referentie-inhoud

De referentie-inhoud is de Power shell-cmdlet-verwijzing voor de cmdlets die in Power shell worden geleverd.
De [verwijzing][ref] wordt verzameld in versie mappen (5,1, 6, 7,0 en 7,1). Deze inhoud bevat alleen cmdlet-verwijzingen voor de modules die worden geleverd met Power shell. Deze inhoud wordt ook gebruikt voor het maken van de Help-informatie die wordt weer gegeven door de `Get-Help`-cmdlet.

> [!NOTE]
> De inhouds opgave (TOC) voor referentie-inhoud wordt automatisch gegenereerd door het publicatie systeem. U hoeft de inhouds opgave niet bij te werken.

### <a name="conceptual-content"></a>Conceptuele inhoud

De conceptuele documentatie bevat de volgende inhoud:

- Releaseopmerkingen
- Installatie-instructies
- Voorbeeld scripts en procedure artikelen
- DSC-documentatie
- SDK-documentatie

De [conceptuele documentatie][conceptual] is niet ingedeeld op versie. Alle artikelen worden weer gegeven voor elke versie van Power shell. We werken eraan om versie-specifieke artikelen te maken. Wanneer deze functie beschikbaar is in onze documentatie, wordt deze hand leiding bijgewerkt met de juiste informatie.

> [!NOTE]
> Telkens wanneer een conceptueel artikel wordt toegevoegd, verwijderd of de naam ervan wordt gewijzigd, moet de inhouds opgave worden bijgewerkt en opgenomen in de pull-aanvraag.

## <a name="using-git-branches"></a>Git-vertakkingen gebruiken

De standaard vertakking voor Power shell-docs is de vertakking `staging`. Wijzigingen die zijn aangebracht in werk vertakkingen worden samengevoegd in de `staging` vertakking vóór de publicatie. Ongeveer eenmaal per week wordt de `staging` vertakking samengevoegd in de `live` vertakking. De `live` vertakking bevat de inhoud die wordt gepubliceerd op docs.microsoft.com. Wijzigingen mogen nooit rechtstreeks in de `live` vertakking worden aangebracht.

Als u een wijziging in de documentatie indient die alleen van toepassing is op een niet-uitgebrachte versie van Power shell, controleert u of er een release vertakking voor die versie is. Alle wijzigingen die van toepassing zijn op een specifieke, toekomstige versie, moeten zijn gericht op de release vertakking. Release vertakkingen hebben het volgende naam patroon: `release-<version>`.

Voordat u wijzigingen start, maakt u een werk vertakking in uw lokale kopie van de Power shell-docs-opslag plaats. Dit moet een [kloon van uw Fork][fork]zijn. Zorg ervoor dat u uw lokale opslag plaats synchroniseert voordat u uw werk vertakking maakt. De werk vertakking moet worden gemaakt op basis van een update naar datum-kopie van de `staging` of `release` vertakking.

Breng de wijzigingen aan die u wilt verzenden na het proces in het gedeelte [uw wijziging door voeren][making-changes] in de hand leiding voor centrale mede werkers.

### <a name="creating-new-articles"></a>Nieuwe artikelen maken

Er moet een GitHub-probleem worden gemaakt voor elk nieuw document dat u wilt bijdragen. Controleer of er bestaande problemen zijn om er zeker van te zijn dat u geen dubbele taken uitvoert. Problemen die aan iemand worden toegewezen, worden beschouwd als in uitvoering. Als u wilt samen werken aan een probleem, neemt u contact op met de persoon die aan het probleem is toegewezen.

Net als bij het Power shell [RFC-proces][rfc], het maken van een probleem voordat de inhoud wordt geschreven, zorgt u ervoor dat u niet veel tijd en moeite besteedt aan iets dat wordt afgewezen door het Power shell-docs-team. Op deze manier kunnen we ook contact met u opnemen over het bereik van de inhoud en waar deze in de Power shell-documentatie moeten passen.

### <a name="updating-existing-articles"></a>Bestaande artikelen bijwerken

Waar van toepassing, worden het cmdlet-referentie artikel gedupliceerd in alle versies van Power shell. Bij het rapporteren van een probleem met betrekking tot een cmdlet-verwijzing of een `About_` artikel, moet u opgeven welke versies worden beïnvloed door het probleem. De uitgifte sjabloon in GitHub bevat een controle lijst met versies. Gebruik de selectie vakjes om op te geven welke versies van de inhoud worden beïnvloed. Wanneer u een wijziging in een artikel indient voor een probleem dat van invloed is op meerdere versies van de inhoud, moet u de juiste wijziging Toep assen op elke versie van het bestand.

## <a name="next-steps"></a>Volgende stappen

Zie [een pull-aanvraag verzenden](pull-requests.md)

<!--link refs-->
[conceptual]: https://github.com/MicrosoftDocs/PowerShell-Docs/tree/staging/reference/docs-conceptual
[fork]: /contribute/get-started-setup-local#fork-the-repository
[making-changes]: /contribute/how-to-write-workflows-major#making-your-changes
[psdocs]: https://github.com/MicrosoftDocs/PowerShell-Docs
[ref]: https://github.com/MicrosoftDocs/PowerShell-Docs/tree/staging/reference
[rfc]: https://github.com/PowerShell/powershell-rfc/blob/master/RFC0000-RFC-Process.md