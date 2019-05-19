---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
title: Registratie van software-inventaris (SIL)
ms.openlocfilehash: b12cfc4ae1e505bbc4d47596bed9352ce53a98f2
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856166"
---
# <a name="software-inventory-logging-sil"></a>Registratie van software-inventaris (SIL)

> [!IMPORTANT]
> Bij het installeren van WMF 5.x op een Windows Server 2012 R2-Server waarop SIL al wordt uitgevoerd, is het nodig om uit te voeren van de cmdlet Start-SilLogging eenmaal na de installatie van WMF, zoals het installatieproces foutievelijk met de functie logboekregistratie van Software-inventaris stopt.

Logboekregistratie van software-inventaris reduceert de operationele kosten van het verkrijgen van nauwkeurige informatie over de Microsoft-software die lokaal worden geïnstalleerd op een server, maar vooral voor grote aantallen servers in een IT-omgeving (ervan uitgaande dat de software is geïnstalleerd en uitgevoerd met de IT-omgeving). Voorwaarde die is ingesteld, kunt u doorsturen van deze gegevens naar een aggregatieserver en verzamelen van de logboekgegevens op één plek met behulp van een uniform, automatisch proces.

Terwijl u ook software-inventarisatiegegevens vastleggen kunt rechtstreeks een query uitgevoerd op elke computer, kunt logboekregistratie van Software-inventaris, met behulp van een architectuur doorsturen (via het netwerk) is gestart door elke server strijden tegen server discovery uitdagingen die gangbaar zijn voor een groot zijn software-inventarisatie en asset beheerscenario's. Logboekregistratie van software-inventaris maakt gebruik van SSL het beveiligen van gegevens die naar een aggregatieserver wordt doorgestuurd via HTTPS. Opslaan van gegevens op één plek, maakt de gegevens gemakkelijker te analyseren, bewerken en delen wanneer nodig.

Geen van deze gegevens is naar Microsoft als onderdeel van de functionaliteit verzonden. Gegevens en functionaliteit van Logboekregistratie voor software-inventaris zijn alleen bedoeld voor gebruik door de gelicentieerde eigenaar en beheerders van de serversoftware.

Zie voor meer informatie en documentatie over cmdlets van logboekregistratie van Software-inventaris, [beheren Sil in Windows Server 2012 R2](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn383584(v=ws.11)).
