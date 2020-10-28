---
ms.date: 03/27/2018
title: AVG-naleving van PowerShell Gallery
description: In dit artikel wordt uitgelegd hoe u persoonlijke gegevens uit het PowerShell Gallery verwijdert en hoe u deze kunt gebruiken om uw verplichtingen onder het AVG te ondersteunen.
ms.openlocfilehash: bd2537f48367a9b6ee3a9d70380b1f32d0a1a651
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92661145"
---
# <a name="powershell-gallery-gdpr-compliance"></a>AVG-naleving van PowerShell Gallery

## <a name="overview"></a>Overzicht

In mei 2018 heeft de Europese economische wetgeving de AVG (AVG) van kracht. De AVG legt nieuwe regels aan voor bedrijven, overheids instanties, non-profit organisaties en andere bedrijven die goederen en diensten aanbieden aan personen in de Europese Unie (EU) of die gegevens verzamelen en analyseren die zijn gekoppeld aan de inwoners van de EU. De AVG is van toepassing, ongeacht waar u zich bevindt.

> [!NOTE]
> Dit artikel bevat stappen voor het verwijderen van persoonlijke gegevens uit de PowerShell Gallery en kan worden gebruikt ter ondersteuning van uw verplichtingen onder het AVG. Zie de [AVG-sectie van Service Trust Portal](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted) voor algemene informatie over de AVG.

## <a name="personally-identifiable-data"></a>Persoons gegevens

De PowerShell Gallery slaat de volgende informatie op die mogelijk wordt verstrekt door gebruikers, die persoonlijke gegevens kunnen bevatten:

- PowerShell Gallery-account
- Pakketten die zijn gepubliceerd op de PowerShell Gallery
- E-mail correspondentie met het PowerShell Gallery-team

De meeste gebruikers maken geen PowerShell Gallery-account. U hoeft alleen een account op te geven als u een pakket wilt publiceren of de functie contact opnemen met eigenaar in de PowerShell Gallery wilt gebruiken. Met uitzonde ring van e-mail correspondentie die door de gebruiker is gestart, worden door de PowerShell Gallery geen persoonlijke gegevens opgeslagen voor gebruikers die geen account hebben gemaakt.

Gebruikers die een PowerShell Gallery account maken, kunnen pakketten publiceren naar de PowerShell Gallery. Deze pakketten worden naar verwachting Power shell-code, maar kunnen ook andere informatie bevatten, waaronder persoonlijke gegevens. In de onderstaande informatie ziet u hoe u alle pakketten kunt ophalen die u hebt gepubliceerd op de PowerShell Gallery.

## <a name="dsr-export-of-powershell-gallery-data"></a>DSR-export van PowerShell Gallery gegevens

In de volgende secties wordt beschreven hoe de PowerShell Gallery gegevens subject aanvragen (DSR) ondersteunt, door te uitleggen hoe u gegevens exporteert die in de PowerShell Gallery zijn opgeslagen, en hoe u het verwijderen van deze gegevens aanvraagt.

### <a name="email"></a>Email

E-mail correspondentie kan bestaan uit een van de volgende:

- E-mail bericht verzonden naar de eigen aren van PowerShell Gallery-pakketten als tijdens het scannen van de code analyse is vastgesteld dat er een probleem is met een pakket dat ze naar de PowerShell Gallery hebben gepubliceerd
- E-mail die door iemand naar het PowerShell Gallery-team is verzonden met behulp van het e-mail adres op de pagina contact opnemen [cgadmin@microsoft.com](mailto:cgadmin@microsoft.com)
- Geregistreerde gebruikers die gebruikmaken van de functie contact opnemen met de eigenaar van de PowerShell Gallery om e-mail te verzenden naar de eigenaar van een pakket in de PowerShell Gallery

E-mail berichten die worden verzonden door of naar het PowerShell Gallery een Bewaar beleid van 90 dagen hebben om mogelijke beveiligings onderzoeken te ondersteunen, moeten schadelijke code worden gedetecteerd op de PowerShell Gallery. E-mail berichten worden na 90 dagen verwijderd door beleid.

U kunt een kopie aanvragen van alle e-mails die zijn verzonden naar of van uw e-mail adres en de PowerShell Gallery in de afgelopen 90 dagen. Als u deze correspondentie wilt aanvragen, stuurt u een e-mail bericht naar [cgadmin@microsoft.com](mailto:cgadmin@microsoft.com) met de titel: ' DSR-aanvraag voor e-mail berichten met betrekking tot dit account '. Geef in de hoofd tekst van het bericht aan welke gegevens u aanvraagt (bijvoorbeeld: verzend alle e-mails die zijn verzonden naar of ontvangen van dit e-mail adres.) Alle e-mail berichten met uw e-mail adres binnen 90 dagen na de aanvraag worden binnen 7 werk dagen verzonden.

### <a name="powershell-gallery-account-information"></a>PowerShell Gallery-account gegevens

Als u een PowerShell Gallery-account hebt gemaakt, kunt u alle persoonlijke gegevens die zijn opgeslagen in PowerShell Gallery vinden door de volgende stappen uit te voeren:

1. Meld u aan bij de PowerShell Gallery en klik op uw gebruikers naam
2. De volgende pagina die wordt weer gegeven, is de account pagina, waarin het e-mail adres wordt weer gegeven dat voor het PowerShell Gallery account wordt gebruikt

Als u meer dan één account hebt gemaakt in de PowerShell Gallery, moet u deze stappen voor elk account herhalen.

### <a name="packages-in-the-powershell-gallery"></a>Pakketten in de PowerShell Gallery

Om het exporteren van pakketten die naar het PowerShell Gallery zijn gepubliceerd te vergemakkelijken, hebben we het script ' GetPSGalleryItemsForAuthor ' gepubliceerd op de PowerShell Gallery. Met dit script wordt een kopie van elke versie van elk pakket dat wordt geplaatst in de PowerShell Gallery geëxporteerd op basis van de informatie in de auteur die in het pakket is opgeslagen.

> [!NOTE]
> De auteur wordt opgeslagen in het pakket manifest wanneer u het pakket publiceert. Er is geen garantie dat de auteur dezelfde identiteit heeft als het account dat u gebruikt in de PowerShell Gallery. Als u een andere waarde in het veld Auteur gebruikt, moet u die waarde opgeven wanneer u dit script gebruikt.

U kunt het script downloaden met behulp van de volgende Power shell-opdracht:

```powershell
Save-Script Get-repository psgallery
```

U kunt het script vervolgens rechtstreeks uitvoeren door de volgende Power shell-opdrachten uit te voeren:

```powershell
# cd <local folder location>
.\GetPSGalleryItemsForAuthor.ps1
```

U wordt gevraagd om de auteur en een map op het systeem op te geven waar u de pakketten wilt opslaan.

## <a name="deleting-personal-data-from-the-powershell-gallery"></a>Persoonlijke gegevens verwijderen uit de PowerShell Gallery

Als u uw PowerShell Gallery account of een pakket dat u in de PowerShell Gallery bezit wilt verwijderen, stuurt u een e-mail naar cgadmin@microsoft.com met de titel: ' AVG-aanvraag voor items met betrekking tot dit account '. In de hoofd tekst van de bericht status welke informatie u wilt verwijderen. Bijvoorbeeld:

- Verwijder versie x. y. z van mijn pakket "pakket naam"
- Verwijder alle versies van mijn pakket "pakket naam"
- Verwijder mijn PowerShell Gallery-account

De PowerShell Gallery-beheerders reageren binnen 7 werk dagen.
De opgegeven pakketten worden binnen 30 dagen nadat de aanvraag is verzonden, verwijderd.
