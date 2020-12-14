---
title: Aan de slag met bijdragen aan Power shell-documentatie
description: Dit artikel bevat een overzicht van hoe u als inzender aan de slag kunt gaan met PowerShell-documentatie.
ms.date: 12/09/2020
ms.topic: conceptual
ms.openlocfilehash: ddcbf79de1ab05b901ce1abd67f65b2524ed164d
ms.sourcegitcommit: 61765d08321623743dc5db5367160f6982fe7857
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/12/2020
ms.locfileid: "97352699"
---
# <a name="get-started-contributing-to-powershell-documentation"></a>Aan de slag met bijdragen aan Power shell-documentatie

Dit artikel bevat een overzicht van hoe u als inzender aan de slag kunt gaan met PowerShell-documentatie.

## <a name="powershell-docs-structure"></a>PowerShell-Docs structuur

De [Power shell-docs-opslag plaats][psdocs] is onderverdeeld in twee groepen inhoud: Naslag informatie en conceptueel.

### <a name="reference-content"></a>Referentie-inhoud

De referentie-inhoud is de Power shell-cmdlet-verwijzing voor de cmdlets die in Power shell worden geleverd.
De [verwijzing][ref] wordt verzameld in versie mappen (5,1, 7,0, 7,1 en 7,2). Deze inhoud bevat alleen cmdlet-verwijzingen voor de modules die worden geleverd met Power shell. Deze inhoud wordt ook gebruikt voor het maken van de Help-informatie die door de cmdlet wordt weer gegeven `Get-Help` .

### <a name="conceptual-content"></a>Conceptuele inhoud

De conceptuele documentatie bevat de volgende inhoud:

- Releaseopmerkingen
- Installatie-instructies
- Voorbeeld scripts en procedure artikelen
- DSC-documentatie
- SDK-documentatie

De [conceptuele documentatie][conceptual] is niet ingedeeld op versie. Alle artikelen worden weer gegeven voor elke versie van Power shell. We werken aan het maken van versie-specifieke artikelen. Wanneer deze functie beschikbaar is in onze documentatie, wordt deze hand leiding bijgewerkt met de juiste informatie.

> [!NOTE]
> Telkens wanneer een conceptueel artikel wordt toegevoegd, verwijderd of de naam ervan wordt gewijzigd, moet de inhouds opgave worden bijgewerkt en opgenomen in de pull-aanvraag.

## <a name="creating-new-articles"></a>Nieuwe artikelen maken

Er moet een GitHub-probleem worden gemaakt voor elk nieuw document dat u wilt bijdragen. Controleer of er bestaande problemen zijn om er zeker van te zijn dat u geen dubbele taken uitvoert. Toegewezen problemen worden beschouwd als `in progress` . Als u wilt samen werken aan een probleem, neemt u contact op met de persoon die aan het probleem is toegewezen.

Net als bij het Power shell [RFC-proces][rfc]maakt u een probleem voordat u de inhoud schrijft. Het probleem zorgt ervoor dat u geen tijd en inspanningen op het werk verspilt dat door het PowerShell-Docs team wordt afgewezen. Met het probleem kunnen we met u overleg plegen over het bereik van de inhoud en waar deze in de Power shell-documentatie passen. Alle artikelen moeten worden opgenomen in de inhouds opgave (TOC). De voorgestelde locatie van de inhouds opgave moet worden opgenomen in de Issue-discussie.

> [!NOTE]
> De inhouds opgave voor referentie-inhoud wordt automatisch gegenereerd door het publicatie systeem. U hoeft de inhouds opgave niet bij te werken.

## <a name="updating-existing-articles"></a>Bestaande artikelen bijwerken

Waar van toepassing worden de cmdlet-referentie artikelen gedupliceerd in alle versies van Power shell die in deze opslag plaats worden onderhouden. Wanneer u een probleem met een cmdlet-verwijzing of een artikel rapporteert `About_` , moet u opgeven welke versies worden beïnvloed door het probleem. De uitgifte sjabloon in GitHub bevat een controle lijst met versies. Gebruik de selectie vakjes om op te geven welke versies van de inhoud worden beïnvloed.

Controleer alle versie van het artikel om te zien of dezelfde wijziging in de andere versies nodig is. Pas de relevante wijziging toe op elke versie van het bestand.

## <a name="localized-content"></a>Gelokaliseerde inhoud

De Power shell-documentatie is geschreven in het Engels en vertaald in 17 andere talen. De Engelse inhoud wordt opgeslagen in de GitHub-opslag plaats met de naam `MicrosoftDocs/PowerShell-Docs` . De gelokaliseerde inhoud wordt opgeslagen in een afzonderlijke opslag plaats voor elke taal. De opslag plaatsen gebruiken dezelfde basispad, maar voegen de naam van de land instelling toe aan het einde. `MicrosoftDocs/PowerShell-Docs.de-de`Bevat bijvoorbeeld de inhoud die naar Duits is vertaald.

Over het algemeen moeten problemen en wijzigingen worden verzonden naar de Engelse opslag plaats. Alle vertalingen beginnen eerst met de Engelse inhoud. We gebruiken zowel Human als machine vertalingen.

| Vertaal methode  |                              Talen                               |
| ------------------- | -------------------------------------------------------------------- |
| Menselijke vertaling   | de-DE, es-ES, fr-FR, it-IT, ja-JP, ko-KR, pt-BR, ru-RU, zh-CN, zh-TW |
| Automatische vertaling | CS-CZ, hu-HU, nl-NL, pl-PL, pt-PT, sv-SE, tr-TR                      |

De inhoud die wordt vertaald door automatische vertaling resulteert niet altijd in de juiste woord opties en grammatica. Als u een fout in de vertaling voor een wille keurige taal vindt, kunt u in plaats van de technische details van het artikel een probleem openen in de gelokaliseerde opslag plaats. Leg uit waarom u denkt dat de vertaling onjuist is. Onze lokalisatie team beoordelingen en reageert op deze problemen.

## <a name="next-steps"></a>Volgende stappen

Er zijn twee algemene manieren om wijzigingen in GitHub te verzenden. Beide methoden worden beschreven in de hand leiding van de centrale bijdrager:

1. U kunt [bestaande documenten snel bewerken](/contribute/#quick-edits-to-existing-documents) in de GitHub-webinterface.
1. Gebruik de [volledige github-werk stroom][making-changes] voor het toevoegen van nieuwe artikelen, het bijwerken van meerdere bestanden of andere grote wijzigingen.

Voordat u wijzigingen begint, moet u een Fork van de PowerShell-Docs-opslag plaats maken. De wijzigingen moeten worden aangebracht in een werk vertakking in het kopiëren van de Power shell-docs. Als u de methode voor **snel bewerken** gebruikt in github, worden deze stappen voor u afgehandeld. Als u de **volledige github-werk stroom** gebruikt, moet u worden ingesteld om [lokaal te werken][fork].

Beide methoden eindigen met het maken van een pull-aanvraag (PR). Zie [een pull-aanvraag indienen](pull-requests.md) voor meer informatie en aanbevolen procedures.

<!--link refs-->
[conceptual]: https://github.com/MicrosoftDocs/PowerShell-Docs/tree/staging/reference/docs-conceptual
[fork]: /contribute/get-started-setup-local#fork-the-repository
[making-changes]: /contribute/how-to-write-workflows-major#making-your-changes
[psdocs]: https://github.com/MicrosoftDocs/PowerShell-Docs
[ref]: https://github.com/MicrosoftDocs/PowerShell-Docs/tree/staging/reference
[rfc]: https://github.com/PowerShell/powershell-rfc/blob/master/RFC0000-RFC-Process.md
