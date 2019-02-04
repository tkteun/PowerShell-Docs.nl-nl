---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 7e87ed4bc9a86be52d4d06d3e87386a1111227c5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686934"
---
# <a name="software-inventory-logging-sil"></a>Registratie van software-inventaris (SIL)

**BELANGRIJK:** *Bij het installeren van WMF 5.0 op een Windows Server 2012 R2-Server waarop SIL al wordt uitgevoerd, is het nodig om de cmdlet Start-SilLogging één keer uitgevoerd nadat de WMF hebt geïnstalleerd, zoals het installatieproces foutievelijk met de functie logboekregistratie van Software-inventaris stopt.*

Logboekregistratie van software-inventaris reduceert de operationele kosten van het verkrijgen van nauwkeurige informatie over de Microsoft-software die lokaal worden geïnstalleerd op een server, maar vooral voor grote aantallen servers in een IT-omgeving (ervan uitgaande dat de software is geïnstalleerd en uitgevoerd met de IT-omgeving). Voorwaarde die is ingesteld, kunt u doorsturen van deze gegevens naar een aggregatieserver en verzamelen van de logboekgegevens op één plek met behulp van een uniform, automatisch proces.

Terwijl u ook software-inventarisatiegegevens vastleggen kunt rechtstreeks een query uitgevoerd op elke computer, kunt logboekregistratie van Software-inventaris, met behulp van een architectuur doorsturen (via het netwerk) is gestart door elke server strijden tegen server discovery uitdagingen die gangbaar zijn voor een groot zijn software-inventarisatie en asset beheerscenario's. Logboekregistratie van software-inventaris maakt gebruik van SSL het beveiligen van gegevens die naar een aggregatieserver wordt doorgestuurd via HTTPS. Opslaan van gegevens op één plek, maakt de gegevens gemakkelijker te analyseren, bewerken en delen wanneer nodig.

Geen van deze gegevens is naar Microsoft als onderdeel van de functionaliteit verzonden. Gegevens en functionaliteit van Logboekregistratie voor software-inventaris zijn alleen bedoeld voor gebruik door de gelicentieerde eigenaar en beheerders van de serversoftware.

Zie voor meer informatie en documentatie over cmdlets van logboekregistratie van Software-inventaris, Windows Server 2012 R2 online-bronnen op <http://technet.microsoft.com/library/dn383584.aspx>.
