---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: Galerie, powershell, cmdlet, psgallery
title: Beheer van eigenaren
ms.openlocfilehash: fcd538148f9ff1ac96324b567d54d643f1756c93
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2017
---
# <a name="managing-item-owners"></a>Beheer van eigenaren

Eigendom van een item in de PowerShell-galerie wordt gedefinieerd door die het item gepubliceerd naar de galerie.
Soms moet deze metagegevens afgezien van het eerste item publiceren, wat betekent dat de metagegevens van de eigenaar moet veranderlijke dat terwijl het item zelf kan niet worden beheerd.

Alle item eigenaars zijn peers. Dit betekent dat de eigenaar van elk item een nieuwe versie van een item kunt publiceren. Het betekent ook dat de eigenaar van elk item een andere eigenaar van het item kunt verwijderen. Er is geen eigenaar heeft meer dan andere eigenaars-instantie.  

## <a name="setting-an-items-initial-owner"></a>De eerste eigenaar van een Item instellen 

Wanneer een nieuw item is gepubliceerd naar de PowerShell-galerie, is de eigenaar van de eerste gedefinieerd door de gebruiker die het item wordt gepubliceerd. Dit wordt bepaald door waarvan API-sleutel in de cmdlet Publish-Module is gebruikt.

## <a name="adding-owners"></a>Eigenaars toevoegen

Nadat een item is gepubliceerd naar de PowerShell-galerie, is het eenvoudig om uit te nodigen extra gebruikers eigenaren van een item wordt omgezet.

1. [Meld u aan](https://powershellgallery.com/users/account/LogOn) naar de PowerShell-galerie met het account dat de huidige eigenaar van een item.
2. Navigeer naar de pagina van een item met behulp van het tabblad 'Items', zoeken of uw gebruikersnaam op te klikken en vervolgens [ **mijn Items beheren**](https://www.powershellgallery.com/account/Packages).
3. Wanneer aangemeld als eigenaar van een item, wordt er een koppeling eigenaren beheren is aan de linkerkant te klikken.
4. Geef de gebruikersnaam van de persoon die als een eigenaar wilt toevoegen en klik op 'Add'.
5. Een e-mailbericht wordt vervolgens naar de nieuwe mede-eigenaar verzonden als een uitnodiging voor een eigenaar van een item.
6. Als die gebruiker op de koppeling klikt, zijn ze een volledige mede-eigenaar met volledige controle over een item, inclusief de mogelijkheid om andere gebruikers als eigenaars te verwijderen.

**Opmerking**: totdat de nieuwe eigenaar eigendom bevestigt, ze *niet* worden vermeld als een eigenaar van een item.
Tijdens het weergeven van de **eigenaren beheren** pagina ziet u een vermelding 'in afwachting van goedkeuring' in de huidige eigenaren.
Deze uitnodiging kan worden verwijderd; Net als andere eigenaren kunnen worden verwijderd.
Dit proces van uitnodigingen wordt voorkomen dat gebruikers ten onrechte toevoegen van andere gebruikers als eigenaars van hun items.

Houd er rekening mee dat de metagegevens 'Auteurs' puur vrije tekst. alleen 'eigenaar' worden beheerd.


## <a name="removing-owners"></a>Eigenaars verwijderen
Wanneer een item meerdere eigenaars zijn en een moet worden verwijderd, is het proces is eenvoudig:

1. [Meld u aan](https://powershellgallery.com/users/account/LogOn) voor PowerShell Gallery met het account dat de huidige eigenaar van een item;
2. Navigeer naar de pagina van een item met behulp van het tabblad Items, zoeken of uw gebruikersnaam op te klikken en vervolgens [ **mijn Items beheren**](https://www.powershellgallery.com/account/Packages).
3. Wanneer aangemeld als eigenaar van een item, is er een koppeling eigenaren beheren aan de linkerkant te klikken;
4. Klik op de koppeling 'verwijderen' naast de eigenaar moet worden verwijderd.



## <a name="transferring-item-ownership"></a>Item eigendom overdragen
Soms krijgen we ondersteuningsaanvragen voor het item het eigendom overdraagt van een gebruiker naar een andere, maar u kunt bijna altijd dit zelf doen.
De overdracht van eigendom van de ene gebruiker naar de andere is gewoon een combinatie van de bovenstaande functies.

1. De huidige eigenaar nodigt de nieuwe gebruiker om te worden van een mede-eigenaar en de nieuwe gebruiker accepteert de uitnodiging;
2. De nieuwe gebruiker verwijdert de oude gebruiker uit de lijst met eigenaren.

Deze aanvraag heeft geleverd in onder een aantal formulieren, maar het proces werkt op dezelfde manier.

* Het item eigendom wordt van een ontwikkelaar gewijzigd naar een andere
* Het item is per ongeluk gepubliceerd met de verkeerde account


## <a name="orphaned-items"></a>Zwevende Items
Een laatste scenario heeft plaatsgevonden, maar niet vaak.
Items wezen zijn geworden en de enige item eigenaarsaccount kan niet worden gebruikt voor het toevoegen van nieuwe eigenaars.
Hier volgen enkele voorbeelden van dit scenario:

* Account van de eigenaar is gekoppeld aan een e-mailadres dat niet meer bestaat en de gebruiker het wachtwoord is vergeten
* De geregistreerde eigenaar heeft het bedrijf dat het item levert en kan niet worden bereikt voor het bijwerken van het item eigendom verlaten
* Vanwege een fout die is alleen van invloed op een aantal items, het item zich enigszins ownerless op de galerie

De PowerShell-galerie-beheerders hebben toegang tot de koppeling eigenaren beheren voor een item.
Als u de rechtmatige eigenaar van een item en geen toegang tot de huidige eigenaar om eigendom machtiging te krijgen, gebruikt u de koppeling 'Misbruik melden' in de galerie bereiken van de PowerShell-galerie-beheerders.
Er wordt een proces om te controleren of uw eigendom van het item volgt.
Als we moet u een eigenaar van het item bepalen, wordt de koppeling eigenaren beheren gebruiken voor het item onszelf en verzendt u de uitnodiging om te worden van een eigenaar.
We zullen dit alleen doen nadat u hebt gecontroleerd dat u een eigenaar moet en het proces voor dit af van de omstandigheden hangt.
Vaak het item Project URL zullen worden gebruikt voor het vinden van een manier om contact op met de eigenaar van het project, maar we kunnen ook Twitter, E-mail of andere wijze gebruikmaken voor communicatie met de eigenaar van het project.

