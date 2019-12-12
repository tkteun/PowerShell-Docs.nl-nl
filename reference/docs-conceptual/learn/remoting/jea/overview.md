---
ms.date: 07/10/2019
keywords: JEA, Power shell, beveiliging
title: Overzicht van net voldoende beheer
ms.openlocfilehash: 4b74e5be9558810748a8844a325c8213e1b3ebc9
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "70017858"
---
# <a name="just-enough-administration"></a>Just Enough Administration

Net genoeg beheer (JEA) is een beveiligings technologie waarmee gedelegeerd beheer kan worden ingeschakeld voor alles dat wordt beheerd door Power shell. Met JEA kunt u het volgende doen:

- **Verminder het aantal beheerders op uw computers** door gebruik te maken van virtuele accounts of door groep beheerde service accounts om geprivilegieerde acties uit te voeren namens normale gebruikers.
- **Beperk wat gebruikers kunnen doen** door op te geven welke cmdlets, functies en externe opdrachten ze kunnen uitvoeren.
- **Beter inzicht in wat uw gebruikers doen** met transcripten en logboeken waarin u precies kunt zien welke opdrachten een gebruiker heeft uitgevoerd tijdens de sessie.

**Waarom is JEA belang rijk?**

Accounts met zeer privileges die worden gebruikt voor het beheer van uw servers vormen een ernstig beveiligings risico. Als een kwaadwillende persoon een van deze accounts zou misbruiken, kunnen ze [zijdelingse aanvallen](https://aka.ms/pth) in uw organisatie starten. Elk aangetast account geeft een aanvaller toegang tot nog meer accounts en resources, en plaatst ze één stap dichter om bedrijfs geheimen te stelen, een denial-of-service-aanval te starten, en meer.

Het is niet altijd eenvoudig om beheerders bevoegdheden te verwijderen. Houd rekening met het algemene scenario waarbij de DNS-rol is geïnstalleerd op dezelfde computer als uw Active Directory-domein controller. Uw DNS-beheerders hebben lokale beheerders bevoegdheden nodig om problemen met de DNS-server op te lossen. Maar hiervoor moet u de leden van de beveiligings groep **domein Administrators** met zeer privileged maken. Deze aanpak zorgt ervoor dat DNS-beheerders de controle over het hele domein en toegang tot alle resources op die computer hebben.

JEA lost dit probleem op door middel van het principe van **minimale bevoegdheden**. Met JEA kunt u een beheer eindpunt configureren voor DNS-beheerders waarmee ze toegang hebben tot de Power shell-opdrachten die ze nodig hebben om hun werk te doen. Dit betekent dat u de juiste toegang kunt bieden om een verontreinigde DNS-cache te herstellen of de DNS-server opnieuw op te starten zonder per ongeluk toestemming te geven aan Active Directory, of door het bestands systeem te bladeren of potentieel gevaarlijke scripts uit te voeren. Wanneer de JEA-sessie nog beter is geconfigureerd voor het gebruik van tijdelijke privileged Virtual accounts, kunnen uw DNS-beheerders verbinding maken met de server met behulp van **niet-beheerders** referenties en blijven opdrachten uitvoeren die doorgaans beheerders bevoegdheden nodig hebben. Met JEA kunt u gebruikers verwijderen uit beheerders rollen van algemeen privileged en zorgvuldig bepalen wat ze op elke computer kunnen doen.

## <a name="next-steps"></a>Volgende stappen

Meer informatie over de vereisten voor het gebruik van JEA vindt u [in het artikel vereisten.](prerequisites.md)

## <a name="samples-and-dsc-resource"></a>Voor beelden en DSC-resource

Voor beelden van JEA-configuraties en de DSC-resource van JEA vindt u in de [JEA github-opslag plaats](https://github.com/PowerShell/JEA).
