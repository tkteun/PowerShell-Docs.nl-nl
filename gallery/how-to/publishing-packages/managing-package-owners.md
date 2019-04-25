---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galerie, powershell, cmdlet, psgallery
title: Pakket eigenaars beheren
ms.openlocfilehash: 5cf26a7195ac446177cbb7f3a055e8e0a78569cc
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084144"
---
# <a name="managing-package-owners"></a>Pakket eigenaars beheren

Eigendom van een pakket in de PowerShell Gallery wordt gedefinieerd door die het pakket gepubliceerd naar de galerie.
Soms moet deze metagegevens na het eerste pakket publiceren, wat betekent dat de metagegevens van de eigenaar moet veranderlijke dat terwijl het pakket zelf niet worden beheerd.

Alle pakket-eigenaren zijn peers.
Dit betekent dat de eigenaar van een pakket met een nieuwe versie van een pakket kunt publiceren. Het betekent ook dat de eigenaar van een pakket met een andere eigenaar van het pakket kan verwijderen.
Er is geen eigenaar heeft meer dan andere eigenaren-instantie.

## <a name="setting-a-packages-initial-owner"></a>Instellen van de oorspronkelijke eigenaar van een pakket

Wanneer een nieuw pakket is gepubliceerd naar de PowerShell Gallery, worden de eigenaar van de eerste wordt gedefinieerd door de gebruiker die het pakket hebt gepubliceerd. Dit wordt bepaald door waarvan API-sleutel in de cmdlet Publish-Module is gebruikt.

## <a name="adding-owners"></a>Eigenaren toevoegen

Nadat een pakket is gepubliceerd naar de PowerShell Gallery, is het eenvoudig extra gebruikers uitnodigen voor eigenaren van een pakket worden.

1. [Meld u bij](https://powershellgallery.com/users/account/LogOn) in PowerShell Gallery, met het account dat is de huidige eigenaar van een pakket.
2. Navigeer naar de pakketpagina van een met behulp van het tabblad 'Items', te zoeken of uw gebruikersnaam op te klikken en vervolgens [ **Mijn-pakketten beheren**](https://www.powershellgallery.com/account/Packages).
3. Wanneer u bent aangemeld op als de eigenaar van een pakket, wordt er een koppeling eigenaren beheren is aan de linkerkant te klikken.
4. Geef de gebruikersnaam van de persoon die als een eigenaar wilt toevoegen en klik op 'Toevoegen'.
5. Een e-mailbericht wordt verzonden naar de nieuwe mede-eigenaar, een uitnodiging om een eigenaar van een pakket.
6. Zodra de gebruiker klikt op de koppeling, zijn ze een volledige mede-eigenaar met volledig beheer over een pakket, inclusief de mogelijkheid om andere gebruikers als eigenaren te verwijderen.

**HOUD ER REKENING MEE**: Totdat de nieuwe eigenaar eigenaar te zijn aangeeft, ze *niet* worden vermeld als een eigenaar van een pakket.
Bij het weergeven van de **eigenaren beheren** pagina, ziet u een vermelding 'in afwachting van goedkeuring' in de huidige eigenaren.
Deze uitnodiging kan worden verwijderd; net zoals andere eigenaren kunnen worden verwijderd.
Dit proces van de uitnodigingen wordt voorkomen dat gebruikers om andere gebruikers toevoegen als eigenaren van hun pakketten.

Houd er rekening mee dat de metagegevens van de "Auteurs" puur vrije tekst is. alleen 'eigenaar' worden beheerd.


## <a name="removing-owners"></a>Eigenaars verwijderen

Wanneer een pakket meerdere eigenaren heeft en een moet worden verwijderd, is het proces is eenvoudig:

1. [Meld u bij](https://powershellgallery.com/users/account/LogOn) aan PowerShell Gallery met het account dat is de huidige eigenaar van een pakket.
2. Navigeer naar de pakketpagina van een met behulp van het tabblad pakketten, te zoeken of uw gebruikersnaam op te klikken en vervolgens [ **Mijn-pakketten beheren**](https://www.powershellgallery.com/account/Packages).
3. Wanneer u bent aangemeld op als de eigenaar van een pakket, is er een koppeling eigenaren beheren aan de linkerkant te klikken;
4. Klik op de koppeling 'verwijderen' naast de eigenaar moet worden verwijderd.



## <a name="transferring-package-ownership"></a>De overdracht van eigendom van pakket

Krijgen we soms ondersteuningsaanvragen voor het overbrengen van pakket eigendom van een gebruiker naar een andere, maar u kunt bijna altijd dit zelf doen.
De overdracht van eigendom van een gebruiker naar een andere is gewoon een combinatie van de bovenstaande twee functies.

1. De huidige eigenaar nodigt de nieuwe gebruiker om te worden van een mede-eigenaar en de nieuwe gebruiker accepteert de uitnodiging;
2. De nieuwe gebruiker verwijdert de oude gebruiker uit de lijst met eigenaren.

Deze aanvraag bij een aantal formulieren is geactiveerd, maar het proces werkt op dezelfde manier.

- Het eigendom van het pakket is gewijzigd van een ontwikkelaar naar een andere
- Het pakket is per ongeluk gepubliceerd met behulp van het verkeerde account


## <a name="orphaned-packages"></a>Zwevende pakketten

Een laatste scenario is opgetreden, maar niet vaak.
Pakketten zijn wezen geworden en de enige pakket met de eigenaar van account kan niet worden gebruikt nieuwe eigenaren toe te voegen.
Hier volgen enkele voorbeelden van dit scenario:

- Account van de eigenaar is gekoppeld aan een e-mailadres dat niet meer bestaat en de gebruiker is het wachtwoord vergeten
- De geregistreerde eigenaar heeft het bedrijf dat het pakket produceert en kan niet worden bereikt voor het bijwerken van het eigendom van het pakket verlaten
- Vanwege een fout die slechts een handvol pakketten heeft beïnvloed, is het pakket ownerless in de galerie

De PowerShell Gallery-beheerders hebben toegang tot de koppeling eigenaren beheren voor een pakket.
Als u de rechtmatige eigenaar van een pakket en tijdelijk niet bereikbaar voor de huidige eigenaar om eigendom machtiging te krijgen, gebruikt u de koppeling 'Misbruik melden' in de galerie bereiken van de PowerShell Gallery-beheerders.
We volgen een proces om te controleren of uw eigendom van het pakket vervolgens.
Als we ontdekken dat u moet een eigenaar van het pakket, wordt er gebruikt u de koppeling eigenaren beheren voor het pakket zelf en ontvangt u de uitnodiging aan voor een eigenaar.
We zullen dit alleen doen nadat u hebt gecontroleerd dat u een eigenaar moet en het proces voor deze is afhankelijk van de omstandigheden.
Vaak, gebruiken we de Project-URL van het pakket op een manier vinden om contact op met de projecteigenaar, maar we kunnen ook Twitter, E-mail of andere manier gebruiken voor het verbinden met de eigenaar van het project.
