---
description: Hiermee worden gebruikers op de hoogte gesteld van het starten van Power shell dat er een nieuwe versie van Power shell is uitgebracht.
Locale: en-US
ms.date: 01/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_update_notifications?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Update_Notifications
ms.openlocfilehash: 1a9f8cfec15f83566fdb77175dcc1aed6d9e8c34
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705515"
---
# <a name="about-update-notifications"></a>Over update meldingen

## <a name="short-description"></a>KORTE BESCHRIJVING

Hiermee worden gebruikers op de hoogte gesteld van het starten van Power shell dat er een nieuwe versie van Power shell is uitgebracht.

## <a name="long-description"></a>LANGE BESCHRIJVING

Vanaf Power shell 7,0 worden er update meldingen gebruikt om gebruikers te waarschuwen dat er updates zijn voor Power shell. Eenmaal per dag vraagt Power shell een online service aan om te bepalen of er een nieuwere versie beschikbaar is.

> [!NOTE]
> Hoewel tijdens de eerste sessie van een bepaalde periode van 24 uur de update controle plaatsvindt, wordt de melding alleen weer gegeven aan het begin van volgende sessies. De controle kan ook om prestatie redenen niet worden gestart tot ten minste 3 seconden nadat de sessie is gestart.

Power shell abonneert standaard op een van twee verschillende meldings kanalen, afhankelijk van de versie/vertakking. Ondersteunde, algemeen beschik bare (GA) versies van Power shell retour neren alleen meldingen voor bijgewerkte GA-releases. Preview en release Candi date (RC) geven een melding van updates voor preview-, RC-en GA-releases.

Het gedrag van de update melding kan worden gewijzigd met behulp van de `POWERSHELL_UPDATECHECK` omgevings variabele. De volgende waarden worden ondersteund:

- `Off` Hiermee schakelt u de update meldings functie uit
- `Default` is hetzelfde als niet definiëren `POWERSHELL_UPDATECHECK` :
  - GA releases op de hoogte van updates voor GA releases
  - Preview/RC geeft melding van updates voor GA-en Preview-versies
- `LTS` alleen berichten met updates voor LTS-GA releases (Long-term-Servicing)

De volgende eind punten worden momenteel gebruikt voor het bepalen van de meest recente versie van elk kanaal:

- `LTS`: https://aka.ms/pwsh-buildinfo-lts
- `Stable`: https://aka.ms/pwsh-buildinfo-stable
- `Preview`: https://aka.ms/pwsh-buildinfo-preview

De update melding biedt geen manier om Power shell automatisch bij te werken. In de toekomst kunnen er meer instructies of mogelijkheden zijn om bij te werken vanuit Power shell, maar vandaag moet u hetzelfde installatie mechanisme gebruiken dat u hebt gebruikt om Power shell te installeren om het bij te werken.

