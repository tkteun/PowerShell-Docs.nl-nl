---
ms.date: 06/12/2017
keywords: jea, powershell, beveiliging
title: Overzicht van Just Enough Administration
ms.openlocfilehash: c097838fb25a63d42502eebf751c64c537bdd077
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084909"
---
# <a name="just-enough-administration"></a>Just Enough Administration

Alleen Enough Administration (JEA) is een beveiligingstechnologie waarmee gedelegeerd beheer voor alles wat die kan worden beheerd met PowerShell.
Met de JEA, kunt u het volgende doen:

- **Verminder het aantal administrators op de machines** door gebruik te maken van virtuele accounts of een groep beheerde serviceaccounts die beschermde acties namens normale gebruikers uitvoeren.
- **Beperken wat gebruikers kunnen doen** door op te geven welke cmdlets, functies en externe opdrachten kunnen ze worden uitgevoerd.
- **Beter te begrijpen wat gebruikers doen** met de uitgeschreven en logboeken die laten zien u precies welke opdrachten uitgevoerd tijdens de sessie van een gebruiker.

**Waarom is dit belangrijk?**

Maximaal bevoegde accounts die worden gebruikt voor het beheren van uw servers vormen een ernstige beveiligingsrisico.
Een aanvaller moet vormen een van deze accounts, kunnen ze starten [laterale aanvallen](http://aka.ms/pth) in uw organisatie.
Elk account dat ze in gevaar brengen zodat ze toegang te meer accounts en resources, zet ze nog een stapje dichter bij het stelen van bedrijf geheimen, starten van een denial-of-service-aanval en nog veel meer.

Het is niet altijd eenvoudig beheerdersbevoegdheden, ofwel verwijderen.
Houd rekening met de gangbare scenario waarbij de DNS-rol is geïnstalleerd op dezelfde computer als uw Active Directory-domeincontroller.
Uw DNS-beheerders vereisen dat lokale administrator-bevoegdheden voor het oplossen van problemen met de DNS-server, maar hiervoor hebben zodat ze leden van de groep met bijzondere rechten 'Domeinadministrators'.
Deze aanpak biedt effectief DNS-beheerders controle over uw hele domein en de toegang tot alle bronnen op die computer.

JEA helpt dit probleem oplossen door het helpt u vaststellen van het principe van *minimale bevoegdheden*.
Met de JEA, kunt u een eindpunt configureren voor DNS-beheerders die hen toegang geeft tot alle PowerShell-opdrachten die ze nodig hebben om hun werk gedaan te krijgen, maar niets meer.
Dit betekent dat u kunt de juiste toegang om te herstellen van een verontreinigd DNS-cache of de DNS-server opnieuw opstarten zonder het per ongeluk zodat ze rechten voor Active Directory, of om te bladeren van het bestandssysteem of mogelijk schadelijke scripts worden uitgevoerd.
Nog beter, wanneer de JEA-sessie is geconfigureerd voor gebruik van tijdelijke beschermde virtuele accounts, uw DNS-beheerders kunnen verbinding maken met de server met *niet-beheerders* referenties en nog steeds kunnen opdrachten uitvoeren die doorgaans vereist beheerdersbevoegdheden.
Deze mogelijkheid kunt u gebruikers verwijderen uit veel bevoegdheden lokaal/domein-beheerdersrollen en in plaats daarvan zorgvuldig bepalen wat ze zijn kunnen doen op elke computer.

## <a name="get-started-with-jea"></a>Aan de slag met JEA

U kunt starten met behulp van JEA vandaag nog op elke computer met Windows Server 2016 of Windows 10.
U kunt ook JEA uitvoeren op oudere besturingssystemen met een update voor Windows Management Framework.
Voor meer informatie over de vereisten om te gebruiken van JEA en voor informatie over het maken, gebruiken, en een JEA-eindpunt controleren, kunt u de volgende onderwerpen:

- [Vereisten](prerequisites.md) -wordt uitgelegd hoe u uw omgeving ingesteld voor het gebruik van JEA.
- [Rolmogelijkheden](role-capabilities.md) -wordt uitgelegd hoe u rollen bepalen wat een gebruiker mag doen in een JEA-sessie maken.
- [Sessieconfiguraties](session-configurations.md) -wordt uitgelegd hoe u JEA-eindpunten die gebruikers aan rollen toewijzen en stel de identiteit van de JEA configureren
- [JEA registreren](register-jea.md) : een JEA-eindpunt maken en het toegankelijk maken voor gebruikers verbinding maken met.
- [Met behulp van JEA](using-jea.md) -Ontdek op welke manieren u JEA kunt gebruiken.
- [Beveiligingsoverwegingen](security-considerations.md) -best practices voor beveiliging en implicaties van JEA-configuratie-opties bekijken.
- [Controle en rapportage van JEA](audit-and-report.md) -Leer hoe u controle en rapportage van JEA-eindpunten.

## <a name="samples-and-dsc-resource"></a>Voorbeelden en DSC-resource

Voorbeeld van JEA configuraties en de JEA-DSC-resource kunnen worden gevonden in de [JEA GitHub-opslagplaats](https://github.com/PowerShell/JEA).