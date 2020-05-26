---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
title: Registratie van software-inventaris (SIL)
ms.openlocfilehash: b12cfc4ae1e505bbc4d47596bed9352ce53a98f2
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/23/2020
ms.locfileid: "83809943"
---
# <a name="software-inventory-logging-sil"></a>Registratie van software-inventaris (SIL)

> [!IMPORTANT]
> Bij de installatie van WMF 5. x op een Windows Server 2012 R2-server waarop SIL al wordt uitgevoerd, is het nodig om de cmdlet start-SilLogging uit te voeren na de installatie van de WMF, terwijl het installatie proces de functie voor logboek registratie van software-inventarisatie foutievelijk stoppen.

Met de logboek registratie van software-inventarisatie kunt u de operationele kosten verminderen van nauw keurige informatie over de micro soft-software die lokaal is geïnstalleerd op een server, maar met name op veel servers in een IT-omgeving (ervan uitgaande dat de software is geïnstalleerd en wordt uitgevoerd in de gehele IT-omgeving). Opgegeven, kunt u deze gegevens door sturen naar een aggregatie server en de logboek gegevens op één locatie verzamelen met een uniform, automatisch proces.

U kunt software-inventaris gegevens ook registreren door elke computer rechtstreeks te doorzoeken, logboek registratie van software-inventaris, door gebruik te maken van een doorstuur architectuur (via het netwerk) die door elke server wordt geïnitieerd. Dit kan leiden tot problemen met de server detectie die typisch zijn voor veel software-inventarisatie en Asset Management-scenario's. Logboek registratie van software-inventaris maakt gebruik van SSL om gegevens te beveiligen die via HTTPS naar een aggregatie server worden doorgestuurd. Als u de gegevens op één plek opslaat, kunnen de gegevens eenvoudiger worden geanalyseerd, gemanipuleerd en gedeeld wanneer dat nodig is.

Geen van deze gegevens wordt naar micro soft verzonden als onderdeel van de functie functionaliteit. Gegevens en functionaliteit van Logboekregistratie voor software-inventaris zijn alleen bedoeld voor gebruik door de gelicentieerde eigenaar en beheerders van de serversoftware.

Zie [logboek registratie van software-inventaris in Windows Server 2012 R2 beheren](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn383584(v=ws.11))voor meer informatie en documentatie over de cmdlets voor logboek registratie van software-inventaris.
