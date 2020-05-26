---
title: Help-bestanden bijwerken | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 495869a6-080e-4401-9ddc-16edd2f86857
caps.latest.revision: 6
ms.openlocfilehash: 35b3fd696419d0135fd6f662223e6c8586df443a
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/23/2020
ms.locfileid: "83811154"
---
# <a name="how-to-update-help-files"></a>Help-bestanden bijwerken

In dit onderwerp wordt uitgelegd hoe u Help-bestanden bijwerkt voor een module die kan worden bijgewerkt met ondersteuning.

## <a name="updating-help-files"></a>Help-bestanden bijwerken

Er zijn veel redenen om Help-bestanden bij te werken, zoals het corrigeren van fouten, het verduidelijken van een concept, het beantwoorden van een veelgestelde vraag, het toevoegen van nieuwe bestanden of het toevoegen van nieuwe en betere voor beelden.

Een Help-bestand bijwerken:

1. Wijzig de bestanden.

2. De bestanden vertalen in andere GEBRUIKERSINTERFACE culturen.

3. Verzamel alle Help-bestanden (nieuw, gewijzigd en ongewijzigd) voor de module in elke GEBRUIKERSINTERFACE cultuur.

4. Valideer de bestanden op basis van het XML-schema.

5. Bouw de CAB-bestanden opnieuw op voor elke GEBRUIKERSINTERFACE cultuur.

6. In het XML-bestand HelpInfo verhoogt u de versie nummers van het CAB-bestand voor elke GEBRUIKERSINTERFACE cultuur.

7. Upload de nieuwe CAB-bestanden naar de locatie die is opgegeven door de waarde van het element **HelpContentUri** in het XML-bestand HelpInfo. Vervang de oudere CAB-bestanden door de nieuwe CAB-bestanden.

8. Upload het bijgewerkte XML-bestand HelpInfo naar de locatie die is opgegeven door de sleutel **HelpInfoUri** in het module manifest. Vervang het oudere HelpInfo XML-bestand door het nieuwe bestand.
