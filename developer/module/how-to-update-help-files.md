---
title: Het bijwerken van Help-bestanden | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 495869a6-080e-4401-9ddc-16edd2f86857
caps.latest.revision: 6
ms.openlocfilehash: 2c1fbd70aab1f65f33ea206b7ab1e2bd3dfd8c7a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846478"
---
# <a name="how-to-update-help-files"></a>Help-bestanden bijwerken

In dit onderwerp wordt uitgelegd hoe u help-bestanden voor een module die ondersteuning biedt voor bij te werken Help bijwerken.

## <a name="updating-help-files"></a>Help-bestanden bijwerken

Er zijn diverse redenen om bij te werken help-bestanden, zoals het corrigeren van fouten, een concept te verduidelijken, een veelgestelde vraag beantwoorden, nieuwe bestanden toe te voegen of toevoegen van nieuwe en betere voorbeelden.

Bijwerken van een help-bestand:

1. De bestanden wijzigen.

2. De bestanden vertalen in andere culturen gebruikersinterface.

3. Alle help-bestanden (nieuwe, gewijzigde en ongewijzigd) voor de module in elke gebruikersinterfacecultuur verzamelen.

4. De bestanden op basis van de XML-schema te valideren.

5. De CAB-bestanden voor elke gebruikersinterfacecultuur opnieuw.

6. In de HelpInfo XML-bestand, verhoog het versienummer van het CAB-bestand voor elke gebruikersinterfacecultuur.

7. De nieuwe CAB-bestanden uploaden naar de locatie die is opgegeven door de waarde van de **HelpContentUri** -element in het HelpInfo XML-bestand. De oudere CAB-bestanden vervangen door de nieuwe CAB-bestanden.

8. Het bijgewerkte HelpInfo XML-bestand uploaden naar de locatie die is opgegeven door de **HelpInfoUri** sleutel in de module-manifest. Vervang het oudere HelpInfo XML-bestand door het nieuwe bestand.