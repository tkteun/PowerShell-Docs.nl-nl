---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installeren
ms.openlocfilehash: 4db2237678649c23729bd1f41bf88f1b9f8f0eef
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="software-inventory-logging-sil"></a>Registratie van software-inventaris (SIL)

** Belangrijk: ** *wanneer WMF 5.0 installeert op een Windows Server 2012 R2-Server waarop SIL al wordt uitgevoerd, is het nodig om uit te voeren van de cmdlet Start-SilLogging eenmaal na de installatie WMF als de installatie foutievelijk de Software stopt Inventaris-functie voor logboekregistratie.*

Logboekregistratie van software-inventaris vermindert het gebruik van de operationele kosten van het verkrijgen van nauwkeurige informatie over de Microsoft-software die lokaal wordt geïnstalleerd op een server, maar vooral voor grote aantallen servers in een IT-omgeving (ervan uitgaande dat de software is geïnstalleerd en uitgevoerd in de IT-omgeving). Voorwaarde die is ingesteld, kunt u het doorsturen van deze gegevens naar een aggregatieserver en de logboekgegevens op één plek verzamelen via een uniform, automatisch proces.

Terwijl u ook software-inventarisatiegegevens vastleggen kunt rechtstreeks een query uitgevoerd op elke computer, logboekregistratie van Software-inventaris, door middel van een doorstuurarchitectuur (via het netwerk) die door elke server wordt geïnitieerd, kunnen ondervangen server discovery uitdagingen die kenmerkend voor veel zijn software-inventarisatie en asset management scenario's. Logboekregistratie van software-inventaris maakt gebruik van SSL beveiligen van gegevens die via HTTPS wordt doorgestuurd naar een aggregatieserver. Opslaan van de gegevens op één plek kan de gegevens eenvoudiger worden geanalyseerd, bewerkt en delen indien nodig.

Geen van deze gegevens als onderdeel van de functionaliteit naar Microsoft verzonden. Gegevens en functionaliteit van Logboekregistratie voor software-inventaris zijn alleen bedoeld voor gebruik door de gelicentieerde eigenaar en beheerders van de serversoftware.

Zie voor meer informatie en documentatie over cmdlets van logboekregistratie van Software-inventaris, Windows Server 2012 R2 online bronnen op <http://technet.microsoft.com/library/dn383584.aspx>.