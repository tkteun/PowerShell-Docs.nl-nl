---
ms.date: 09/12/2016
ms.topic: reference
title: Help-bestanden bijwerken
description: Help-bestanden bijwerken
ms.openlocfilehash: 19bf501cf91b1eb5dabb334c2179953590b40232
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649587"
---
# <a name="how-to-update-help-files"></a>Help-bestanden bijwerken

In dit onderwerp wordt uitgelegd hoe u Help-bestanden bijwerkt voor een module die kan worden bijgewerkt met ondersteuning.

## <a name="updating-help-files"></a>Help-bestanden bijwerken

Er zijn veel redenen om Help-bestanden bij te werken, zoals het corrigeren van fouten, het verduidelijken van een concept, het beantwoorden van een veelgestelde vraag, het toevoegen van nieuwe bestanden of het toevoegen van nieuwe en betere voor beelden.

Een Help-bestand bijwerken:

1. Wijzig de bestanden.
1. De bestanden vertalen in andere GEBRUIKERSINTERFACE culturen.
1. Verzamel alle Help-bestanden (nieuw, gewijzigd en ongewijzigd) voor de module in elke GEBRUIKERSINTERFACE cultuur.
1. Valideer de bestanden op basis van het XML-schema.
1. Bouw de CAB-bestanden opnieuw op voor elke GEBRUIKERSINTERFACE cultuur.
1. In het XML-bestand HelpInfo verhoogt u de versie nummers van het CAB-bestand voor elke GEBRUIKERSINTERFACE cultuur.
1. Upload de nieuwe CAB-bestanden naar de locatie die is opgegeven door de waarde van het element **HelpContentUri** in het XML-bestand HelpInfo. Vervang de oudere CAB-bestanden door de nieuwe CAB-bestanden.
1. Upload het bijgewerkte XML-bestand HelpInfo naar de locatie die is opgegeven door de sleutel **HelpInfoUri** in het module manifest. Vervang het oudere HelpInfo XML-bestand door het nieuwe bestand.
