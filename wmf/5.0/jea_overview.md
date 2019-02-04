---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 0bc085588190f134c4a687c952509aa256b5f840
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55687151"
---
# <a name="just-enough-administration-jea"></a>Just Enough Administration (JEA)
Just Enough Administration is een nieuwe functie in WMF 5.0 waarmee Rolgebaseerd beheer via externe communicatie van PowerShell.  Deze uitbreiding van de bestaande infrastructuur van beperkte eindpunt doordat niet-beheerders kunnen specifieke opdrachten, scripts en uitvoerbare bestanden uitvoeren als beheerder.  Hiermee kunt u Verminder het aantal volledige beheerders in uw omgeving en uw beveiliging te verbeteren.  JEA werkt voor alles wat die u via PowerShell beheren; Als u iets met PowerShell beheren kunt, kunt u dus veiliger door JEA helpen.  Bekijk voor een gedetailleerde Kijk op Just Enough Administration, de [gids voor gebruikerservaring](http://aka.ms/JEA).

JEA is in tegenstelling tot de oude beperkte eindpunten, krachtige en eenvoudig te configureren.  Gebruikersmogelijkheden in JEA kunnen worden granulair beheerd, naar het beperken van waarin parametersets en -waarden kunnen worden geleverd aan een specifieke opdracht. Acties van de gebruiker worden uitgevoerd in de context van een eenmalige virtueel account waarvoor de rechten voor het uitvoeren van de acties van de beheerder.  De opdrachten die wordt aangeroepen door de gebruiker kunnen worden geregistreerd voor beveiligingscontroles.

JEA werkt met de mogelijkheid om beperkte eindpunten speciaal geconfigureerd te maken.  Deze eindpunten hebben een aantal belangrijke kenmerken:

1. Gebruikers verbinding maken met deze 'uitvoeren als' een bevoegde virtueel Account die alleen voor de duur van deze externe sessie bestaat.  Deze virtuele-Account is standaard lid is van de ingebouwde groep Administrators, evenals de beheerders van een domein op domeincontrollers (Opmerking: deze machtigingen worden geconfigureerd). Door verbinding te maken als een gebruiker en die wordt uitgevoerd als een andere, bevoegde gebruiker, kunt u niet-gemachtigde gebruikers specifieke beheertaken uitvoeren zonder dat ze beheerdersrechten heeft op uw systemen.
2. Het eindpunt is vergrendeld.  Dit betekent dat PowerShell wordt uitgevoerd in de modus voor niet-taal.  Alleen specifieke opdrachten, scripts en uitvoerbare bestanden zijn zichtbaar voor de gebruiker.
3. Andere gebruikers die verbinding maken worden met een andere set mogelijkheden op basis van groepslidmaatschap weergegeven.  U kunt verschillende rollen bieden verschillende mogelijkheden op hetzelfde eindpunt.
