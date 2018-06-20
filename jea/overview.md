---
ms.date: 06/12/2017
keywords: jea powershell beveiliging
title: Overzicht van Just Enough Administration
ms.openlocfilehash: 3dae8b31d4d13ff9033803035c870c02fc7c38ca
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34222085"
---
# <a name="just-enough-administration"></a>Just Enough Administration

Net genoeg Administration (JEA) is een technologie waarmee gedelegeerd beheer voor alles die kan worden beheerd met PowerShell.
Met JEA, kunt u het volgende doen:

- **Verminder het aantal beheerders op de machines** door gebruik van virtuele accounts of een groep beheerde serviceaccounts die bevoegde acties namens reguliere gebruikers uitvoeren.
- **Beperken wat gebruikers kunnen doen** door te geven welke cmdlets, functies en externe opdrachten kunnen ze worden uitgevoerd.
- **Beter te begrijpen wat gebruikers doen** met Logboeken en transcripties die ziet u precies die opdrachten uitgevoerd tijdens de sessie van een gebruiker.

**Waarom is dit belangrijk?**

Maximaal bevoorrechte accounts die worden gebruikt voor het beheren van uw servers vormen een ernstige beveiligingsrisico.
Een aanvaller moet inbreuk een van deze accounts, kan starten [aanvallen op lateral](http://aka.ms/pth) in uw organisatie.
Elk account die ze inbreuk kunt krijgen ze zelfs meer accounts en -bronnen, zodat ze een stap dichter in bedrijf geheimen, het starten van een denial of service-aanval en meer stelen.

Het is niet altijd eenvoudig beheerdersbevoegdheden, ofwel verwijderen.
Houd rekening met het algemene scenario waarbij de DNS-serverfunctie is geïnstalleerd op dezelfde computer als uw Active Directory-domeincontroller.
Uw DNS-administrators nodig lokale beheerdersbevoegdheden herstellen van problemen met de DNS-server, maar hiervoor hoeft u zodat ze leden van de bijzondere rechten 'Domeinadministrators' beveiligingsgroep.
Deze aanpak geeft effectief DNS-beheerders controle over het hele domein en de toegang tot alle resources op deze machine.

JEA helpt dit probleem oplossen door ondersteuning bij het vaststellen van het principe van *minimale bevoegdheden*.
U kunt een eindpunt met JEA configureren voor DNS-beheerders die hen toegang geeft tot alle PowerShell-opdrachten die ze nodig hebben om hun werk gedaan te krijgen, maar niets meer.
Dit betekent dat u kunt bieden de juiste toegang tot een verontreinigd DNS-cache herstellen of opnieuw opstarten van de DNS-server zonder onbedoeld door ze te machtigen voor Active Directory, of het bestandssysteem te bladeren of mogelijk schadelijke scripts uitvoeren.
Nog beter wanneer de sessie JEA is geconfigureerd voor gebruik van tijdelijke bevoorrechte virtuele accounts, uw DNS-beheerders kunnen verbinding maken met de server via *niet-beheerders* referenties en nog steeds uitvoeren van opdrachten die doorgaans vereisen beheerdersbevoegdheden.
Deze mogelijkheid kunt u gebruikers uit beheerdersrollen veel bevoegdheden lokaal/domein verwijderen en in plaats daarvan zorgvuldig bepalen wat ze kunnen uitvoeren op elke machine.

## <a name="get-started-with-jea"></a>Aan de slag met JEA

U kunt starten JEA vandaag gebruikt op elke computer waarop Windows Server 2016 of Windows 10 wordt uitgevoerd.
U kunt ook JEA uitvoeren op oudere besturingssystemen met een update voor Windows Management Framework.
Voor meer informatie over de vereisten voor gebruik van JEA en informatie over het maken, gebruiken, en een eindpunt JEA controleren, bekijk de volgende onderwerpen:

- [Vereisten](prerequisites.md) -wordt uitgelegd hoe u uw omgeving instellen JEA gebruiken.
- [Mogelijkheden van de rol](role-capabilities.md) -wordt uitgelegd hoe u de functies die bepalen wat een gebruiker mag doen in een sessie JEA maken.
- [Sessieconfiguraties](session-configurations.md) -wordt uitgelegd hoe u JEA-eindpunten die gebruikers rollen toewijzen en stel de identiteit JEA configureren
- [Registreren van JEA](register-jea.md) : Maak een eindpunt JEA en beschikbaar gesteld voor gebruikers verbinding maken met.
- [Met behulp van JEA](using-jea.md) -Ontdek op welke manieren u JEA kunt gebruiken.
- [Beveiligingsoverwegingen](security-considerations.md) -best practices voor beveiliging en implicaties van JEA configuratieopties te bekijken.
- [Controleren en te rapporteren over JEA](audit-and-report.md) -informatie over het controleren en te rapporteren over JEA eindpunten.

## <a name="samples-and-dsc-resource"></a>Voorbeelden en DSC-resource

Voorbeeld JEA configuraties en de JEA DSC-resource gevonden in de [JEA GitHub-opslagplaats](https://github.com/PowerShell/JEA).