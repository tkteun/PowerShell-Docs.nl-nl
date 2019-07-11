---
ms.date: 07/10/2019
keywords: jea, powershell, beveiliging
title: Overzicht van Just Enough Administration
ms.openlocfilehash: 4b74e5be9558810748a8844a325c8213e1b3ebc9
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726645"
---
# <a name="just-enough-administration"></a>Just Enough Administration

Alleen Enough Administration (JEA) is een beveiligingstechnologie waarmee gedelegeerd beheer voor alles wat beheerd door PowerShell. Met de JEA, kunt u het volgende doen:

- **Verminder het aantal administrators op de machines** met behulp van virtuele accounts of -groep beheerde serviceaccounts bevoegde acties namens normale gebruikers uit te voeren.
- **Beperken wat gebruikers kunnen doen** door op te geven welke cmdlets, functies en externe opdrachten kunnen ze worden uitgevoerd.
- **Beter te begrijpen wat gebruikers doen** met de uitgeschreven en logboeken die laten zien u precies welke opdrachten uitgevoerd tijdens de sessie van een gebruiker.

**Waarom is JEA belangrijk?**

Maximaal bevoegde accounts die worden gebruikt voor het beheren van uw servers vormen een ernstige beveiligingsrisico. Een aanvaller moet vormen een van deze accounts, kunnen ze starten [laterale aanvallen](https://aka.ms/pth) in uw organisatie. Elk account waarmee is geknoeid biedt een aanvaller toegang tot het zelfs meer accounts en resources en worden de tegels één stap dichter naar het stelen van bedrijf geheimen, starten van een denial-of-service-aanval en nog veel meer.

Het is niet altijd eenvoudig beheerdersbevoegdheden, ofwel verwijderen. Houd rekening met de gangbare scenario waarbij de DNS-rol is geïnstalleerd op dezelfde computer als uw Active Directory-domeincontroller. Uw DNS-beheerders vereisen dat lokale beheerrechten nodig voor het oplossen van problemen met de DNS-server. Maar om dit te doen, moet u ze leden van de maximaal bevoegde **Domeinadministrators** beveiligingsgroep. Deze aanpak biedt effectief DNS-beheerders controle over uw hele domein en de toegang tot alle bronnen op die computer.

JEA lost dit probleem via het principe van **minimale bevoegdheden**. Met JEA, kunt u een eindpunt configureren voor DNS-beheerders dat hen toegang geeft tot de PowerShell-opdrachten die ze nodig hebben om hun werk gedaan te krijgen. Dit betekent dat u kunt de juiste toegang om te herstellen van een verontreinigd DNS-cache of de DNS-server opnieuw opstarten zonder het per ongeluk zodat ze rechten voor Active Directory, of om te bladeren van het bestandssysteem of mogelijk schadelijke scripts worden uitgevoerd. Nog beter, wanneer de JEA-sessie is geconfigureerd voor gebruik van tijdelijke beschermde virtuele accounts, uw DNS-beheerders kunnen verbinding maken met de server met **niet-beheerders** referenties en opdrachten nog steeds uitvoeren waarvoor doorgaans admin bevoegdheden. JEA kunt u gebruikers verwijderen uit een breed beschermde lokale/domein-beheerdersrollen en zorgvuldig bepalen wat ze kunnen doen op elke computer.

## <a name="next-steps"></a>Volgende stappen

Zie voor meer informatie over de vereisten voor het gebruik van JEA, de [vereisten](prerequisites.md) artikel.

## <a name="samples-and-dsc-resource"></a>Voorbeelden en DSC-resource

Voorbeeld van JEA configuraties en de JEA-DSC-resource kunnen worden gevonden in de [JEA GitHub-opslagplaats](https://github.com/PowerShell/JEA).
