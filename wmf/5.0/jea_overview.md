---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installeren
ms.openlocfilehash: 847bd978b0a8ad8daf26d37ee8759f88fba67f31
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="just-enough-administration-jea"></a>Just Enough Administration (JEA)
Net genoeg Administration is een nieuwe functie in WMF 5.0 waarmee Rolgebaseerd beheer via PowerShell voor externe toegang.  Hiermee wordt de bestaande infrastructuur van beperkte eindpunt uitgebreid doordat niet-beheerders kunnen door specifieke opdrachten, scripts en uitvoerbare bestanden uitvoeren als beheerder.  Hierdoor kunt u Verminder het aantal volledige beheerders in uw omgeving en de beveiliging te verbeteren.  JEA is geschikt voor alles wat die u kunt via PowerShell beheren; Als u iets met PowerShell beheren kunt, kunt JEA u dus veiliger kunt doen.  Bekijk voor een gedetailleerde beschrijving net genoeg beheer, de [handleiding ervaren](http://aka.ms/JEA).

In tegenstelling tot oude beperkte eindpunten is JEA krachtige en eenvoudig te configureren.  Mogelijkheden van de gebruiker in JEA kunnen worden granulair beheerd, naar beneden beperken welke parametersets en -waarden kunnen worden geleverd aan een specifieke opdracht. Acties van de gebruiker worden uitgevoerd in de context van een eenmalige virtueel account met de rechten voor de beheerdersacties uitvoeren.  De opdrachten aangeroepen door de gebruiker kunnen worden geregistreerd voor beveiligingscontrole.

JEA werkt doordat u beperkte eindpunten speciaal geconfigureerde maken.  Deze eindpunten hebben een aantal belangrijke kenmerken:

1. Gebruikers verbinding maken met deze 'uitvoeren als' een virtueel Account met machtigingen die alleen voor de duur van deze externe sessie bestaat.  Standaard is deze virtueel Account lid is van de ingebouwde groep Administrators, evenals een domeinbeheerders op domeincontrollers (Opmerking: deze machtigingen worden geconfigureerd). Door verbinding te maken als een gebruiker uit te voeren als een gebruiker afwijken, bevoegdheden, kunt u onbevoegde gebruikers bepaalde beheertaken uitvoeren zonder dat zij beheerdersrechten heeft op uw systemen.
2. Het eindpunt is vergrendeld.  Dit betekent dat PowerShell wordt uitgevoerd in de modus Nee taal.  Alleen specifieke opdrachten, scripts en uitvoerbare bestanden zijn zichtbaar voor de gebruiker.
3. Andere gebruikers die verbinding maken worden met een andere set mogelijkheden op basis van groepslidmaatschap weergegeven.  U kunt verschillende rollen verschillende mogelijkheden op hetzelfde eindpunt opgeven.