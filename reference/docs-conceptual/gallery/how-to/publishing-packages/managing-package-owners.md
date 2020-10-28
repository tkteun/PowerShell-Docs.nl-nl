---
ms.date: 06/12/2017
title: Pakket eigenaren beheren
description: Het eigendom van een pakket in de PowerShell Gallery wordt gedefinieerd door wie het pakket heeft gepubliceerd in de galerie.
ms.openlocfilehash: 96aa3a16156a226c9be23eca6599266b89a8423f
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92662527"
---
# <a name="managing-package-owners"></a>Pakket eigenaren beheren

Het eigendom van een pakket in de PowerShell Gallery wordt gedefinieerd door wie het pakket heeft gepubliceerd in de galerie. Soms moeten deze meta gegevens worden beheerd na de initiële pakket publicatie, wat betekent dat de meta gegevens van de eigenaar onveranderbaar moeten zijn terwijl het pakket zelf niet is.

Alle pakket eigenaren zijn peers. Dit betekent dat elke pakket eigenaar een nieuwe versie van een pakket kan publiceren.
Dit betekent ook dat elke eigenaar van het pakket alle andere pakket eigenaars kan verwijderen. Geen enkele eigenaar heeft meer bevoegdheden dan andere eigen aren.

## <a name="setting-a-packages-initial-owner"></a>De eerste eigenaar van een pakket instellen

Wanneer een nieuw pakket wordt gepubliceerd naar PowerShell Gallery, wordt de eerste eigenaar gedefinieerd door de gebruiker die het pakket heeft gepubliceerd. Dit wordt bepaald door de API-sleutel die is gebruikt in de cmdlet Publish-Module.

## <a name="adding-owners"></a>Eigen aren toevoegen

Wanneer een pakket is gepubliceerd naar de PowerShell Gallery, is het eenvoudig om extra gebruikers uit te nodigen om eigenaar te worden van een pakket.

1. [Meld](https://powershellgallery.com/users/account/LogOn) u aan bij de PowerShell Gallery met het account dat de huidige eigenaar is van een pakket.
1. Navigeer naar een pakket pagina met behulp van het tabblad ' items ', zoek of klik op uw gebruikers naam en vervolgens op [**mijn pakketten beheren**](https://www.powershellgallery.com/account/Packages).
1. Wanneer u bent aangemeld als eigenaar van een pakket, kunt u aan de linkerkant op de link eigen aren beheren klikken.
1. Voer de gebruikers naam in van de persoon die u wilt toevoegen als eigenaar en klik op toevoegen.
1. Er wordt een e-mail bericht verzonden naar de nieuwe mede-eigenaar, als een uitnodiging om eigenaar te worden van een pakket.
1. Zodra de gebruiker op de koppeling klikt, is deze een volledige mede-eigenaar met volledige controle over een pakket, inclusief de mogelijkheid om andere gebruikers als eigen aren te verwijderen.

> [!NOTE]
> Totdat de nieuwe eigenaar het eigendom bevestigt, *wordt deze niet* vermeld als een eigenaar van een pakket. Wanneer u de pagina **eigen aars beheren** bekijkt, ziet u de vermelding ' goed keuring in behandeling ' in de huidige eigen aars.
> Deze uitnodiging kan worden verwijderd. net zoals andere eigen aren kunnen worden verwijderd. Dit proces van uitnodigingen voor komt dat gebruikers onterecht andere gebruikers toevoegen als eigen aren van hun pakketten.

De meta gegevens van auteurs zijn niet-vrije tekst. alleen "eigen aren" worden beheerd.

## <a name="removing-owners"></a>Eigen aren verwijderen

Wanneer een pakket meerdere eigen aren heeft en één moet worden verwijderd, is het proces eenvoudig:

1. [Meld](https://powershellgallery.com/users/account/LogOn) u aan bij PowerShell Gallery met het account dat de huidige eigenaar is van een pakket.
1. Ga naar een pakket pagina met het tabblad pakketten, zoek of klik op uw gebruikers naam en vervolgens op [**mijn pakketten beheren**](https://www.powershellgallery.com/account/Packages).
1. Wanneer u bent aangemeld als eigenaar van een pakket, kunt u aan de linkerkant op de link eigen aren beheren klikken;
1. Klik op de koppeling verwijderen naast de eigenaar die moet worden verwijderd.

## <a name="transferring-package-ownership"></a>Eigendom van het pakket overdragen

Soms krijgen we ondersteunings aanvragen voor het overdragen van pakket eigendom van een gebruiker naar een andere, maar u kunt dit bijna altijd zelf doen. Het overdragen van het eigendom van de ene gebruiker naar een andere is slechts een combi natie van de bovenstaande functies.

1. De huidige eigenaar verzoekt de nieuwe gebruiker een mede-eigenaar te worden en de nieuwe gebruiker accepteert de uitnodiging.
1. De nieuwe gebruiker verwijdert de oude gebruiker uit de lijst met eigen aren.

Deze aanvraag is beschikbaar in een paar formulieren, maar het proces werkt op dezelfde manier.

- Het eigendom van het pakket verandert van de ene ontwikkelaar naar een andere
- Het pakket is per ongeluk gepubliceerd met het verkeerde account

## <a name="orphaned-packages"></a>Zwevende pakketten

Er is een laatste scenario opgetreden, maar dit is niet vaak. Pakketten zijn zwevend geworden en het enige pakket eigenaars account kan niet worden gebruikt om nieuwe eigen aren toe te voegen. Hier volgen enkele voor beelden van dit scenario:

- Het account van de eigenaar is gekoppeld aan een e-mail adres dat niet meer bestaat en de gebruiker is het wacht woord verg eten
- De geregistreerde eigenaar heeft het bedrijf verlaten dat het pakket produceert en kan niet worden bereikt om het eigendom van het pakket bij te werken
- Als gevolg van een bug die alleen een aantal pakketten heeft beïnvloed, is het pakket eigenaar van de galerie.

De PowerShell Gallery-beheerders hebben toegang tot de koppeling eigen aren beheren voor elk pakket. Als u de eigenaar van een pakket bent van de Rightful en de huidige eigenaar niet kan bereiken om eigendoms machtigingen te krijgen, gebruikt u de koppeling ' misbruik melden ' in de galerie om de PowerShell Gallery beheerders te bereiken. We gaan vervolgens een proces volgen om uw eigendom van het pakket te verifiëren. Als we bepalen dat u een eigenaar van het pakket moet zijn, gebruiken we de koppeling eigen aren beheren voor het pakket zelf en sturen we u de uitnodiging om eigenaar te worden. We zullen dit alleen doen nadat u hebt gecontroleerd of u een eigenaar moet zijn en het proces hiervoor afhankelijk is van omstandigheden. Vaak gebruiken we de project-URL van het pakket om een manier te vinden om contact op te nemen met de project eigenaar, maar we kunnen ook gebruikmaken van Twitter, E-mail of een andere manier om contact op te nemen met de project eigenaar.
