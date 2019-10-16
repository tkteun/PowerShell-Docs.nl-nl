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
ms.openlocfilehash: 2c1fbd70aab1f65f33ea206b7ab1e2bd3dfd8c7a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72357419"
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